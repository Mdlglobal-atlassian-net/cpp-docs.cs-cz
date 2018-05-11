---
title: Průvodce pro vývojáře C++ pro kanály straně spekulativní provádění | Microsoft Docs
ms.custom: ''
ms.date: 05/03/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
author: mamillmsft
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0a7e7ddb51f07f7fe6be1da017d8feae9cc4919e
ms.sourcegitcommit: 96cdc2da0d8c3783cc2ce03bd280a5430e1ac01d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Průvodce pro vývojáře C++ pro kanály straně spekulativní provádění

Tento článek obsahuje pokyny pro vývojáře, které pomáhají při identifikaci a zmírnění spekulativní provádění straně kanál hardwaru slabá místa zabezpečení v C++ softwaru. Tyto chyby můžete prozrazeny citlivé informace napříč hranicemi vztahů důvěryhodnosti a může ovlivnit software, který běží na procesorů, které podporují spekulativní, se na pořadí provádění pokyny. Tato třída chyb byla první popsané v lednu, 2018 a další informace a pokyny najdete v [informační zpravodaj zabezpečení společnosti Microsoft](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002).

V pokynech v tomto článku se vztahuje k třídě reprezentována CVE-2017-5753, také známé jako spektrum variant 1 ohrožení zabezpečení. Tato třída hardwaru ohrožení zabezpečení se týká straně kanály, které mohou nastat z důvodu spekulativní provádění, k níž dojde v důsledku misprediction podmíněného větev. Kompilátor Visual C++ v aplikaci Visual Studio 2017 (počínaje verzí 15.5.5) zahrnuje podporu pro `/Qspectre` přepínač poskytuje zmírnění kompilace pro omezenou sadu potenciálně citlivé kódování vzorky související s CVE. 2017 5753. V dokumentaci [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) příznak poskytuje další informace o jeho dopady a využití. 

Přístupné Úvod k ohrožení zabezpečení kanálu straně spekulativní provádění lze nalézt v prezentaci s názvem [případ spektrum a Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) pomocí jedné z research týmy, které zjištěny tyto problémy.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Jaké jsou ohrožení zabezpečení hardwaru Speculative provádění straně Channel?

Moderní procesory poskytují vyšší stupňů výkonu tím, že použití spekulativní a na více systémů pořadí provádění pokyny. Například to často provádí predikci cíle větví (podmíněného a indrect), která umožňuje procesoru zahájí speculatively pokyny v cílovém předpokládaných větve, tedy není zpomalován místo dokud cílový skutečné větve je rozpoznat. V případě, že procesoru později zjistí, že došlo k chybě misprediction, všechny stav počítače, který se spočítala speculatively se zahodí. To zajistí, že neexistují žádné z pohledu architektury viditelné důsledky mispredicted spekulativní.

Při provádění spekulativní nemá vliv na stav viditelnosti architecturaly, ho můžete nechat zbytkové trasování v jiných architektury stavu, jako je například různé mezipaměti, které jsou používány procesoru. Je toto zbytkové trasování spekulativní spuštění, který může vést k ohrožení zabezpečení kanálu straně. Abyste lépe pochopili, to, vezměte v úvahu následující fragment kódu, který poskytuje příklad CVE 5753 2017 (hranice zkontrolujte obcházení):

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

V tomto příkladu `ReadByte` je zadaný index, vyrovnávací paměť a velikost vyrovnávací paměti do vyrovnávací paměti. Parametr index podle specifikace `untrusted_index`, poskytl méně privilegované kontextu, jako je například procesu bez oprávnění správce. Pokud `untrusted_index` je menší než `buffer_size`, pak znak, od tohoto indexu je pro čtení z `buffer` a slouží jako index do byla sdílená oblast paměti odkazuje `shared_buffer`.

Z architektury perspektivy, je toto pořadí kód perfektně bezpečné, protože bylo zaručeno, že `untrusted_index` bude vždy menší než `buffer_size`. Případě spekulativní spuštění, je však možné, že bude procesoru mispredict podmíněného větve a provést text Pokud příkaz i v případě `untrusted_index` je větší než nebo rovno `buffer_size`. V důsledku toho může procesoru speculatively číst bajt from beyond hranice `buffer` (které můžou být tajný klíč) a pak použít tuto hodnotu bajtu k výpočtu adresu následné zatížení prostřednictvím `shared_buffer`. 

Při této misprediction nakonec detekuje, procesoru, se může stát zbytkové vedlejší účinky zůstane v mezipaměti procesoru, které odhalit informace o bajtovou hodnotu, která byla načtena mimo rozsah od `buffer`. Tyto vedlejší účinky může rozpoznat méně privilegované kontextu službou v systému a jak rychle zjišťování každá mezipaměť řádek v `shared_buffer` přistupuje. Kroky, které můžete provést k tomu jsou:

1. **Vyvolání `ReadByte` vícekrát s `untrusted_index` je menší než `buffer_size`** . Kontext útočící může způsobit postižené kontext, který má vyvolat `ReadByte` (např. přes RPC) tak, aby se předpověď větve je cvičení nebyly použity jako `untrusted_index` je menší než `buffer_size`.

2. **Vyprázdnit všechny řádky mezipaměti v `shared_buffer`** . Kontext útočící musí vyprázdnit všechny řádky mezipaměti ve sdílené oblasti paměti odkazuje `shared_buffer`. Vzhledem k tomu, že je sdílená oblast paměti, to je jednoduchá a dá dosáhnout pomocí vnitřní funkce, jako `_mm_clflush`.

3. **Vyvolání `ReadByte` s `untrusted_index` větším než `buffer_size`** . Kontext útočící způsobí, že postižené kontext, který má vyvolat `ReadByte` tak, aby nesprávně předpovídá, nesmí být použito větvení. Tato příčiny procesoru speculatively provést text Pokud blokovat s `untrusted_index` větším než `buffer_size`, proto tečka na začátku k out-of-bounds čtení z `buffer`. V důsledku toho `shared_buffer` je indexovaný pomocí potenciálně tajná hodnota, která byla načtena out-of-bounds, což způsobuje příslušných mezipaměti řádku mají být načteny procesoru.

4. **Přečtěte si každý řádek mezipaměti v `shared_buffer` zobrazíte, který je přístupný nejvíce rychle**. Kontext útočící může číst každý řádek mezipaměti v `shared_buffer` a zjistit řádek mezipaměti, který načte výrazně rychlejší než jiné. Toto je řádek mezipaměti, která by mohla znovu kroku 3. Vzhledem k tomu, že je relace 1:1 mezi bajtů hodnota a mezipaměti řádku v tomto příkladu, díky útočník odvodit se skutečnou hodnotou bajtů, která byla načtena out-of-bounds.

Výše uvedené kroky uveďte příklad použití techniku známou jako VYPRÁZDNĚNÍ + NAČTĚTE ve spojení s zneužitím instanci CVE. 2017 5753.

## <a name="what-software-scenarios-can-be-impacted"></a>Ovlivněné můžou být jaké scénáře softwaru?

Vývoj zabezpečené softwaru pomocí procesu, jako [Security Development Lifecycle](https://www.microsoft.com/en-us/sdl/) (SDL) zpravidla vyžaduje, aby vývojáři k identifikaci hranice vztahu důvěryhodnosti, které existují ve svých aplikacích. Hranice vztahu důvěryhodnosti v místech, kde aplikace může komunikovat s daty poskytované kontextu méně důvěryhodný, jako je například jiný proces na serveru nebo proces režimu uživatele bez oprávnění správce v případě ovladač režimu jádra zařízení existuje. Nová třída ohrožení zabezpečení zahrnující spekulativní provádění straně kanály se hodí pro řadu hranicemi důvěryhodnosti v existující modely zabezpečení softwaru, které izolovat kód a data na zařízení.

Následující tabulka obsahuje souhrn modely zabezpečení softwaru, kde mohou vývojáři musí starat o těchto chybách, ke kterým dochází:

|Hranice vztahu důvěryhodnosti|Popis|
|----------------|----------------|
|Virtuální počítač hranic|Aplikace, které izolují úlohy v samostatných virtuálních počítačů, které přijímat nedůvěryhodné data z jiného virtuálního počítače může být ohrožena.|
|Hranice jádra|Ovladač zařízení v režimu jádra, která přijímá nedůvěryhodné data z procesu režimu uživatele bez oprávnění správce může být ohrožena.|
|Hranice procesu|Aplikace, která přijímá nedůvěryhodné data z jiný proces, který běží v místním systému, například prostřednictvím vzdálené volání procedur (RPC), sdílené paměti nebo jiných mezi proces komunikace (IPC) mechanismy může být ohrožena.|
|Enclave hranic|Aplikace, která se spouští v rámci zabezpečeného enclave (například Intel SGX), která recieves nedůvěryhodná, že data z mimo enclave může být ohrožena.|
|Jazyk hranic|Aplikace, který interpretuje nebo JIT (JIT) kompiluje a provede nedůvěryhodné kód napsaný v jazyce vyšší úrovně může být ohrožena.|

Aplikace, které mají prostor pro útoky zveřejněné žádnému z výše uvedených důvěřovat, že hranice by si měli projít kódu na prostor pro útoky na zjišťovat a zmírňovat možných výskytů spekulativní provádění straně kanál ohrožení zabezpečení. Je potřeba poznamenat, že hranice vztahů důvěryhodnosti vystavený povrchy vzdáleného útoku, jako je vzdálené síťových protokolech, nebyly prokázal jako hrozí na spekulativní provádění straně kanál slabá místa zabezpečení.

## <a name="potentially-vulnerable-coding-patterns"></a>Potenciálně citlivé kódování vzory

Ohrožení zabezpečení kanálu straně spekulativní provádění mohou nastat v důsledku více kódování vzorů. Tato část popisuje potenciálně citlivé kódování vzory a obsahuje příklady pro každou, ale by měly být rozpoznány, že může existovat varianty těchto motivů. Jako takový vývojáři doporučujeme provést tyto vzory jako příklady a ne jako vyčerpávající seznam všech potenciálně citlivé kódování vzory.

Obecně platí spekulativní provádění straně kanály související s podmíněného větve misprediction mohou nastat při podmíněným výrazem pracuje s daty, která se dá řídit nebo ovlivněné kontextu méně důvěryhodný. Například to může zahrnovat podmíněné výrazy použité v `if`, `for`, `while`, `switch`, nebo Ternární příkazy. Pro každou z těchto příkazů kompilátor může generovat struktura, která procesoru může pak předpovědi větve cíle pro za běhu.

Každý například je vložit komentář s frázi "SPEKULATIVNÍ bariéry" vývojář, kde může zanést bariéry jako omezení rizik. To je podrobněji popsána v části na způsoby zmírnění rizik.

### <a name="speculative-out-of-bounds-load"></a>Out-of-bounds spekulativní zatížení

Z kódování vzory této kategorie zahrnuje misprediction podmíněného větve, který vede k spekulativní out-of-bounds přístup do paměti.

#### <a name="array-out-of-bounds-load-feeding-a-load"></a>Pole out-of-bounds načíst napájení zatížení

Tento vzor kódování je původně popsané citlivé kódování vzor pro CVE 5753 2017 (hranice zkontrolujte obcházení). Tento vzor podrobně vysvětluje, pozadí části tohoto článku.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

Podobně pole out-of-bounds zatížení může dojít ve spojení s smyčku, která překračuje jeho ukončení podmínky kvůli misprediction. V tomto příkladu podmíněného větev přidružené `x < buffer_size` výraz může mispredict a speculatively provést text `for` cykly při `x` je větší než nebo rovno `buffer_size`, proto spekulativní což Out-of-Bounds načtěte.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

#### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Pole out-of-bounds načíst napájení nepřímých firemní pobočky

Tento vzor kódování zahrnuje tento případ, kdy misprediction větve podmíněného může vést k out-of-bounds přístup k pole ukazatelé funkcí, které pak vede k větev nepřímých do cílové adresy, které byla načtena out-of-bounds. Následující fragment kódu poskytuje příklad, který ukazuje to. 

V tomto příkladu je zadán identifikátor nedůvěryhodné zpráva pro DispatchMessage prostřednictvím `untrusted_message_id` parametr. Pokud `untrusted_message_id` je menší než `MAX_MESSAGE_ID`, bude použit k indexování do pole ukazatelů na funkce a větvení do odpovídající cílové firemní pobočky. Tento kód je z pohledu architektury bezpečné, ale pokud procesoru mispredicts podmíněného větev, to může způsobit `DispatchTable` se indexovat pomocí `untrusted_message_id` při jeho hodnota může být větší než nebo rovna hodnotě `MAX_MESSAGE_ID`, proto tečka na začátku k out-of-bounds přístup. To může vést ke spekulativní spuštění z cílová adresa firemní pobočky, který je odvozený za hranice pole, které by mohly způsobit zpřístupnění informací v závislosti na kód, který je proveden speculatively.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

Jako v případě pole out-of-bounds zatížení napájení jiný zatížení, tento stav může také způsobit ve spojení s smyčku, která překračuje jeho ukončující stavu z důvodu misprediction.

### <a name="speculative-type-confusion"></a>Nejasnostem spekulativní typu

Z kódování vzory této kategorie zahrnuje misprediction podmíněného větve, který vede k záměně spekulativní typu. Následující příklad kódu budou vztahovat kódování vzory v této části.

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

#### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Vedoucí k záměně spekulativní typ out-of-bounds načíst.

Tento vzor kódování zahrnuje tento případ, kde může způsobit nejasnosti spekulativní typ out-of-bounds nebo nerozumíte typ pole přístupu, kde načíst hodnotu kanály adresu dalších zatížení. To se podobá se vzorem out-of-bounds kódování pole ale označované prostřednictvím alternativu kódování pořadí jako v příkladu nahoře. V tomto příkladu by mohlo způsobit kontextu útočící kontext postižené provést `ProcessType` vícekrát s objektem typu `CType1` (`type` pole rovná `Type1`). To bude mít za následek skutečnost podmíněného větve pro první `if` příkaz k předvídání není přijatá. Kontext útočící pak může způsobit kontext postižené provést `ProcessType` s objektem typu `CType2`. To může způsobit nejasnosti spekulativní typ Pokud větev zásad správy pro první `if` příkaz mispredicts a provede text `if` prohlášení, proto přetypování objekt typu `CType2` k `CType1`. Vzhledem k tomu `CType2` je menší než `CType1`, přístup k paměti `CType1::field2` vést spekulativní out-of-bounds načte dat, která může být tajný. Tato hodnota se pak používá v zatížení z `shard_buffer` pozorovatelné vedlejší účinky, které můžete vytvořit stejně jako u pole out-of-bounds příklad popsané.

#### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Spekulativní typ nedorozuměním vedoucí k nepřímé firemní pobočky

Toto kódování vzory zahrnuje tento případ, kde můžete nedorozuměním spekulativní typ výsledkem unsafe nepřímých firemní pobočky během spekulativní provádění. V tomto příkladu by mohlo způsobit kontextu útočící kontext postižené provést `ProcessType` vícekrát s objektem typu `CType2` (`type` pole rovná `Type2`). To bude mít za následek skutečnost podmíněného větve pro první `if` příkaz mají být provedeny a `else if` příkaz nelze provést. Kontext útočící pak může způsobit kontext postižené provést `ProcessType` s objektem typu `CType1`. To může způsobit nejasnosti spekulativní typ Pokud větev zásad správy pro první `if` příkaz předpovídá prováděné a `else if` příkaz předpovídá není přijatá proto provádění text `else if` a objekt typu přetypování`CType1` k `CType2`. Vzhledem k tomu `CType2::dispatch_routine` pole se překrývá s `char` pole `CType1::field1`, výsledkem by mohlo spekulativní nepřímých větev cíl nezamýšleným větev. Pokud kontext útočící můžete řídit bajtových hodnot v `CType1::field1` pole, které mohou být schopné řídit cílová adresa firemní pobočky.

## <a name="mitigation-options"></a>Zmírnění dopadů možnosti

Spekulativní provádění straně kanál ohrožení zabezpečení můžete zmírnit tím, že změny ke zdrojovému kódu. Tyto změny mohou zahrnovat zmírnění určité instance ohrožení zabezpečení, například přidáním *spekulativní bariéry*, nebo po provedení změn v návrhu aplikace, aby citlivé informace nepřístupný pro spekulativní provádění.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Barrier spekulativní prostřednictvím ruční instrumentace

A *spekulativní bariéry* může ručně vložit vývojáře, aby se zabránilo vykonání spekulativní z pokračováním podél-architektury cesty. Například vývojář bariéry spekulativní před nebezpečná kódování vzor vložit do těla podmíněného blok, buď na začátku bloku (po podmíněného větev) nebo před první zatížení, která bude se jednat o problém. To zabrání misprediction větve podmíněného spuštění nebezpečného kódu-architektury cestou serializací provádění. Pořadí bariéry spekulativní se liší podle hardwarovou architekturou, jak je popsáno v následující tabulce:

|Architektura|Spekulativní bariéry|
|----------------|----------------|
|x86/x64|_mm_lfence()|
|ARM|Není aktuálně k dispozici|
|ARM64|Není aktuálně k dispozici|


Například následující kód vzor můžete zmírnit použitím `_mm_lfence` vnitřní, jak je uvedeno níže.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Barrier spekulativní prostřednictvím kompilaci instrumentace

Kompilátor Visual C++ v aplikaci Visual Studio 2017 (počínaje verzí 15.5.5) zahrnuje podporu pro `/Qspectre` přepínač, který automaticky vloží bariéry spekulativní pro omezenou sadu potenciálně citlivé kódování vzory související s CVE. 2017 5753. V dokumentaci [/Qspectre](https://docs.microsoft.com/en-us/cpp/build/reference/qspectre) příznak poskytuje další informace o jeho dopady a využití. Je důležité si uvědomit, že tento příznak nepopisuje všechny vzoru potenciálně citlivé kódování a jako takový vývojáři neměli spoléhat na jako komplexní zmírnění dopadů pro tuto třídu ohrožení zabezpečení.

### <a name="removing-sensitive-information-from-memory"></a>Odebrání citlivých informací z paměti

Další postup, který slouží ke zmírnění ohrožení zabezpečení kanálu spekulativní provádění straně je odebrání citlivých informací z paměti. Vývojáři softwaru můžete vyhledat příležitosti Refaktorovat jejich aplikace tak, aby citlivé informace není přístupné během spekulativní zpracování. To můžete udělat refaktoring návrhu aplikace izolovat citlivé informace do samostatné procesy. Aplikace webového prohlížeče může například pokusit izolovat data související s každou původu webového do samostatné procesy, proto nebudete mít přístup k mezi zdroji dat prostřednictvím spekulativní spuštění brání jeden proces.

## <a name="see-also"></a>Viz také

[Pokyny ke zmírnění spekulativní provádění straně kanál ohrožení zabezpečení](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002)

[Zmírnění spekulativní provádění straně kanál hardwaru ohrožení zabezpečení](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
