---
title: Doprovodné materiály pro vývojáře v C++ pro kanály na straně spekulativního spouštění
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: 20e6d45c088fe92fa736539e485d6807802b368a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179316"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>Doprovodné materiály pro vývojáře v C++ pro kanály na straně spekulativního spouštění

Tento článek obsahuje pokyny pro vývojáře, které pomáhají při identifikaci a omezení spekulativního spouštění na straně kanálu hardwaru chyby v softwaru C++. Tyto chyby zabezpečení může odhalit citlivé informace napříč hranicemi vztahů důvěryhodnosti a může mít vliv na software, který běží na procesorech podporujících spekulativního, mimo pořadí provádění instrukcí. Tato třída ohrožení zabezpečení byl první je popsáno v lednu 2018 a další informace a pokyny najdete v [informační zpravodaj zabezpečení společnosti Microsoft](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002).

Pokynů, které jste v tomto článku se vztahuje na třídy reprezentována ohrožení zabezpečení:

1. CVE-2017-5753, označované také jako chyby zabezpečení Spectre variant 1. Tuto třídu hardwaru ohrožení zabezpečení se týká kanály na straně, které mohou vzniknout z důvodu spekulativního spouštění, ke které dojde v důsledku misprediction podmíněná větev. Kompilátor Visual C++ v sadě Visual Studio 2017 (od verze 15.5.5) zahrnuje podporu pro `/Qspectre` přepínač, který poskytuje zmírnění kompilace pro omezenou sadu potenciálně ohrožená vzorce kódování související s CVE-2017-5753. `/Qspectre` Přepínač je také k dispozici v sadě Visual Studio 2015 Update 3 prostřednictvím [KB 4338871](https://support.microsoft.com/help/4338871). V dokumentaci [/qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) příznak poskytuje další informace o jeho dopady a využití.

2. CVE-2018-3639, označované také jako [spekulativního jednorázové přihlášení pro Store (SSB)](https://aka.ms/sescsrdssb). Tuto třídu hardwaru ohrožení zabezpečení se týká kanály na straně, které mohou vzniknout z důvodu spekulativního spouštění zatížení náskok před závislé úložiště jako výsledek misprediction přístupu k paměti.

Přístupné Úvod k ohrožení zabezpečení spekulativního spouštění na straně kanálu lze nalézt v prezentaci s názvem [případ Spectre a Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4) pomocí jedné z research týmy, které zjišťují tyto problémy.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>Co jsou spekulativní provádění na straně kanálu hardwarové ohrožení zabezpečení?

Moderní procesory poskytují vyšší stupeň výkon tím, že použití spekulativního a mimo pořadí spouštění instrukcí. Například to je často proveden predikce cíl větve (podmíněné a nepřímé), který umožňuje procesoru zahájí speculatively pokyny v cíli předpokládané větev, tedy není zpomalován pozastavení provádění získání, dokud je cíl skutečné větve vyřešené. V případě, že procesoru později zjistí, že došlo k chybě misprediction, se zahodí všechny vypočítaná speculatively stav počítače. Tím se zajistí, že neexistují žádné architektonicky viditelné účinky mispredicted spekulace o.

Při spekulativního spouštění nemá vliv na stav architektonicky viditelnosti, ho můžete nechat plyne ze zbytkových trasování ve stavu architektury, jako je například různé mezipaměti, které jsou používány procesoru. Je toto plyne ze zbytkových trasování spekulativního spouštění, který může mít za následek ohrožení zabezpečení na straně kanálu. Chcete-li lépe pochopit, zvažte následující fragment kódu, který poskytuje příklad CVE-2017-5753. (zkontrolujte nepoužívat hranice):

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

V tomto příkladu `ReadByte` je zadané vyrovnávací paměti, velikost vyrovnávací paměti a indexu do vyrovnávací paměti. Index parametru, jak jsou určené `untrusted_index`, získáte ho od méně privilegovaným kontextu, například bez oprávnění správce procesu. Pokud `untrusted_index` je menší než `buffer_size`, znak na pozici indexu je přečten z `buffer` a slouží jako index do oblasti sdílené paměti, na které odkazuje `shared_buffer`.

Z architektonického hlediska, toto pořadí kód je zcela bezpečné, protože je zaručeno, že `untrusted_index` bude vždy menší než `buffer_size`. Za přítomnosti spekulativního spouštění, je však možné, že procesor bude nevyplněné předpovědi podmíněná větev a spustit tělo příkazu if – příkaz i v případě `untrusted_index` je větší než nebo rovna hodnotě `buffer_size`. Následkem toho může procesor speculatively číst bajt from beyond hranice `buffer` (která může být tajný klíč) a pak použít tuto hodnotu bajtu pro výpočet adresy následné zatížení prostřednictvím `shared_buffer`.

Zatímco procesoru nakonec zjistí tento misprediction, plyne ze zbytkových vedlejší účinky, může zůstat v mezipaměti procesoru, který zjistí informace o hodnotě bajtů, který byl načten mimo rozsah od `buffer`. Můžete rozpoznat tyto vedlejší účinky less privileged kontext spuštěné v systému, jak rychle zjišťováním každá mezipaměť řádku v `shared_buffer` přistupuje. Kroky, které můžete k tomu jsou:

1. **Vyvolání `ReadByte` vícekrát s `untrusted_index` je menší než `buffer_size`** . Útočící kontextu může způsobit victim kontextu vyvolat `ReadByte` (například prostřednictvím vzdáleného volání Procedur) tak, že je větev prediktivní vyškolit tak, aby se není provedena jako `untrusted_index` je menší než `buffer_size`.

2. **Vyprázdnit všechny řádky mezipaměti v `shared_buffer`** . Kontext útočící musí vyprázdnění všech řádků mezipaměti v oblasti sdílené paměti, na které odkazuje `shared_buffer`. Protože je sdílený paměťové oblasti, to je jednoduché a můžete to provést pomocí vnitřní objekty, jako `_mm_clflush`.

3. **Vyvolání `ReadByte` s `untrusted_index` větším než `buffer_size`** . Kontext útočící způsobí, že victim kontextu vyvolat `ReadByte` tak, aby nesprávně předpovídá, nesmí být použito větvení. To způsobí procesoru speculatively provádět tělo příkazu if blokovat s `untrusted_index` větším než `buffer_size`, tedy přední na celočíselných čtení z `buffer`. V důsledku toho `shared_buffer` indexován pomocí potenciálně tajná hodnota, která byla načtena celočíselných, což způsobuje příslušných mezipaměti řádku mají být načteny procesoru.

4. **Přečtěte si každý řádek mezipaměti v `shared_buffer` zobrazíte, která je nejvíc rychlý přístup**. Útočící kontextu můžou číst každý řádek mezipaměti v `shared_buffer` a zjistit řádek mezipaměti, který načítá výrazně rychlejší než ostatní. Toto je řádek mezipaměti, která by mohla dali kroku 3. Protože vztah 1:1 mezi bajtové hodnoty a mezipaměti řádku v tomto příkladu, ta umožňuje útočníkovi odvodit skutečnou hodnotu, která byla načtena celočíselných bajtu.

Výše uvedené kroky uveďte příklad pomocí techniky označované jako VYPRÁZDNĚNÍ + RELOAD ve spojení s využívajícím instance CVE-2017-5753.

## <a name="what-software-scenarios-can-be-impacted"></a>Může mít dopad na jakých situacích softwaru?

Vývoj pomocí procesu, jako je zabezpečení softwaru [Security Development Lifecycle](https://www.microsoft.com/sdl/) (SDL) obvykle vyžaduje, aby vývojáři k identifikaci hranice vztahu důvěryhodnosti, které existují ve svých aplikacích. Hranice vztahů důvěryhodnosti existuje na místech, kde můžou aplikace pracovat s daty poskytuje kontext, méně důvěryhodnému, například jiný proces v systému nebo proces režimu uživatele bez oprávnění správce v případě ovladač zařízení režimu jádra. Nová třída zahrnující kanály na straně spekulativního spouštění ohrožení zabezpečení je relevantní pro řadu hranicemi vztahů důvěryhodnosti v existujících modelech zabezpečení softwaru, které izolovat kódu a dat na zařízení.

Následující tabulka obsahuje souhrn modely zabezpečení softwaru, kde vývojáři muset mít obavy o těchto chyb, ke kterým došlo:

|Hranice vztahu důvěryhodnosti|Popis|
|----------------|----------------|
|Virtuální počítač hranice|Aplikace, které izolování úloh v samostatných virtuálních počítačů, které přijímají nedůvěryhodná data z jiného virtuálního počítače může být ohrožena.|
|Hranice jádra|Ovladač zařízení režimu jádra, která přijímá nedůvěryhodná data z procesu režimu bez oprávnění správce uživatele může být ohrožena.|
|Hranice procesu|Aplikace, která přijímá nedůvěryhodná data z jiného procesu spuštění v místním systému, jako je prostřednictvím vzdálené volání procedur (RPC), sdílené paměti nebo jiných mezi proces komunikace (IPC) mechanismy může být ohrožena.|
|Enklávě hranic|Aplikace, která se spustí v rámci zabezpečeného enklávy (například Intel SGX), která přijímá nedůvěryhodná data z mimo enklávy může být ohrožena.|
|Jazyky|Aplikace, který interpretuje nebo za běhu (JIT) zkompiluje a spustí nedůvěryhodný kód napsaný v jazyce vyšší úrovně může být ohrožena.|

Aplikace, které mají potenciální oblast útoku zveřejněná ke kterékoli z výše uvedených důvěřovat, že hranice byste si přečíst kód na rovině útoku pro identifikaci a zmírnění možných výskytů spekulativního spouštění na straně kanálu ohrožení zabezpečení. Je třeba poznamenat, že hranicemi vztahů důvěryhodnosti vystaveni rovin útoku vzdálené, jako je vzdálené síťové protokoly, nebyly se prokáže, že být ohrožena na spekulativního spouštění na straně kanálu slabá místa zabezpečení.

## <a name="potentially-vulnerable-coding-patterns"></a>Potenciálně ohrožená a vzorů psaní kódu

Spekulativního spouštění na straně kanálu ohrožení zabezpečení můžou nastat v důsledku více vzorce kódování. Tato část popisuje potenciálně ohrožená vzorce kódování a příklady pro každý, ale by měly být rozpoznán, mohou existovat varianty těchto motivů. Vývojáři v důsledku toho doporučujeme provést tyto modely jako příklady a ne jako vyčerpávající seznam všech potenciálně ohrožená vzorce kódování. Stejné třídy ohrožení zabezpečení bezpečný přístup z více paměti, které mohou existovat v softwaru ještě dnes mohou také existovat společně spekulativního a cesty mimo pořadí spuštění, včetně, ale nikoli výhradně přetečení vyrovnávací paměti, pole celočíselných přístupy, použití neinicializované paměti typu nejasnosti a tak dále. Stejné primitivních elementů, které zneužívají ohrožení zabezpečení bezpečnost paměti podél cest architektury použít útočníci se můžou vztahovat taky spekulativního cesty.

Obecně platí misprediction týkajících se podmíněné větvi kanály na straně spekulativního spouštění mohou vzniknout při podmíněný výraz pracuje s daty, která můžete řídit nebo ovlivněno méně důvěryhodnému kontextu. Například to může zahrnovat podmíněné výrazy použité v `if`, `for`, `while`, `switch`, nebo Ternární příkazy. Pro každou z těchto příkazů může kompilátor generovat podmíněná větev, která procesor může předpovídat pak cíl větve pro za běhu.

Pro každý příklad je vložen komentář pomocí fráze "SPEKULAČNÍ bariéru", kde vývojáři by mohla zanést barrier jako omezení rizik. Toto je podrobněji v oddílu na zmírnění rizik.

## <a name="speculative-out-of-bounds-load"></a>Načíst spekulativní celočíselných

Tato kategorie pravidel psaní kódu zahrnuje misprediction podmíněná větev, který vede k spekulativního celočíselných přístup do paměti.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>Pole celočíselných načtení, tak zatížení

Tento vzor kódování je původně popsané zranitelné kódování vzor pro CVE-2017-5753. (zkontrolujte nepoužívat hranice). Tento model podrobně vysvětluje, pozadí části tohoto článku.

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

Obdobně podmínky pole celočíselných zatížení může dojít ve spojení s smyčku, která překračuje jeho ukončení z důvodu misprediction. V tomto příkladu přidružené podmíněná větev `x < buffer_size` může nevyplněné předpovědi a speculatively spusťte tělo výrazu `for` smyčky, kdy `x` je větší než nebo rovna hodnotě `buffer_size`tedy výsledkem spekulativního celočíselných načtěte.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>Pole celočíselných načíst předáte nepřímé větve

Tento model kódování zahrnuje tento případ, kdy misprediction podmíněná větev může vést k celočíselných přístup k poli z ukazatele funkcí, které pak vede k nepřímé větev do cílové adresy, která byla načtena celočíselných. Následující fragment kódu poskytuje příklad, který ukazuje to.

V tomto příkladu identifikátor nedůvěryhodné zprávu dostane DispatchMessage prostřednictvím `untrusted_message_id` parametru. Pokud `untrusted_message_id` je menší než `MAX_MESSAGE_ID`, pak se používá k Indexujte pole ukazatelů na funkce a větvit do odpovídající cílové větve. Tento kód je bezpečné architektonicky, ale pokud procesor nevyplněných předpovědí rozvětvení podmíněná větev, může vést `DispatchTable` indexované podle `untrusted_message_id` když její hodnota je větší než nebo rovna hodnotě `MAX_MESSAGE_ID`, tedy vedoucí k celočíselných přístup. To může způsobit spekulativního spouštění z adresy cílové větve, která je odvozena za hranice pole, které by mohlo vést k informacím v závislosti na kód, který je proveden speculatively.

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

Jako v případě pole celočíselných načtení, tak další zatížení, k tomuto stavu může také nastat ve spojení s smyčku, která překračuje jeho ukončující stav kvůli misprediction.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>Pole celočíselných ukládat tak nepřímé větve

Při předchozí příklad ukázal jak spekulativního celočíselných zatížení mohou mít vliv na cíl nepřímé větve, je také možné, ukládání celočíselných změnit cíl nepřímé větev, například ukazatele na funkci nebo zpáteční adresu. To může potenciálně vést k spekulativního spouštění z útočník zadané adresy.

V tomto příkladu se předává nedůvěryhodné indexu `untrusted_index` parametru. Pokud `untrusted_index` je menší než počet prvků `pointers` pole (256 prvky), pak hodnota poskytnutý ukazatel v `ptr` se zapisují do `pointers` pole. Tento kód je bezpečné architektonicky, ale pokud procesor nevyplněných předpovědí rozvětvení podmíněná větev, může vést `ptr` speculatively zapisovaných za hranice zásobníku přidělený `pointers` pole. To může vést k spekulativního poškození zpáteční adresu pro `WriteSlot`. Pokud útočník můžete určit hodnotu `ptr`, mohou být schopni způsobit spekulativního spouštění z libovolnou adresu při `WriteSlot` vrátí spekulativního cestě.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

Podobně pokud funkce ukazatele místní proměnné s názvem `func` byly přiděleny v zásobníku, pak je možné speculatively upravit adresu, která `func` odkazuje na, když dojde k misprediction podmíněná větev. To může vést k spekulativního spouštění z libovolné adresy při ukazatel funkce volané prostřednictvím.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

Je třeba poznamenat, že oba tyto příklady zahrnují spekulativního úpravy přidělený na zásobník nepřímé větev ukazatelů. Je možné, že spekulativního úpravy by se mohl vyskytnout pro globální proměnné, paměť přidělenou haldě a dokonce i paměti jen pro čtení na některých procesorech. Přidělený na zásobník paměti kompilátor Visual C++ již trvá v zájmu postup znesnadňují speculatively upravit přidělený na zásobník nepřímé větvi cíle, například opětovným uspořádáním lokální proměnné tak, že soubor cookie zabezpečení jako jsou umístěna vyrovnávací paměti součástí [/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check) kompilátoru bezpečnostní funkce.

## <a name="speculative-type-confusion"></a>Typu spekulativním záměny

Tato kategorie se zabývá vzorů, které můžou vést k záměně typu spekulativním psaní kódu. Vyvolá se při přístupu k paměti pomocí nesprávného typu – architektury cestě během spekulativního spouštění. Misprediction podmíněná větev a obejít spekulativního úložiště může potenciálně vést k typu spekulativním nejasnosti.

Pro jednorázové přihlášení spekulativního úložiště tato situace může nastat ve scénářích, kde kompilátor opětovně používá umístění zásobníku pro proměnné více typů. Důvodem je, že architektury úložiště proměnné typu `A` může obejít, což umožní načíst typ `A` speculatively běžet, než proměnná přiřazená. Pokud dříve uložené proměnné jiného typu, toto můžete vytvořit podmínky typu spekulativním nejasnostem.

Pro misprediction podmíněná větev se použije následující fragment kódu k popisu různých podmínek, které můžete poskytnout typu spekulativním záměně vzrůst.

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

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>Což vede k záměně typu spekulativním celočíselných načíst

Tento model kódování zahrnuje tento případ, ve kterém může způsobit zmatení typu spekulativním celočíselných nebo kde načtená hodnota kanály adresu následné zatížení přístup zaměňovat typ pole. To se podobá celočíselných kódování vzor pole, ale označované prostřednictvím alternativu kódování pořadí, jak je znázorněno výše. V tomto příkladu by mohlo způsobit útočící kontextu kontextu victim ke spuštění `ProcessType` vícekrát s objektem typu `CType1` (`type` pole je rovna `Type1`). To bude mít vliv školení podmíněná větev pro první `if` příkaz k předpovědi není přijatá. Útočící kontextu může způsobit pak victim kontext pro spouštění `ProcessType` s objektem typu `CType2`. To může způsobit zmatení typu spekulativním Pokud podmíněnou větev v první `if` příkaz nevyplněných předpovědí větvení a provádí tělo `if` prohlášení, tedy přetypováním objektu typu `CType2` k `CType1`. Protože `CType2` je menší než `CType1`, přístup k paměti k `CType1::field2` bude výsledkem spekulativního celočíselných načtení dat, která může být tajný. Tato hodnota se pak použije v rámci zátěžového z `shared_buffer` pozorovatelný vedlejší účinky, které můžete vytvořit stejně jako u pole celočíselných příklad je popsáno výše.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>Typu spekulativním nejasnosti, což vede k nepřímé větve

Tento model kódování zahrnuje tento případ, kde záměny typu spekulativním může způsobit unsafe nepřímé větve během spekulativního spouštění. V tomto příkladu by mohlo způsobit útočící kontextu kontextu victim ke spuštění `ProcessType` vícekrát s objektem typu `CType2` (`type` pole je rovna `Type2`). To bude mít vliv školení podmíněná větev pro první `if` příkaz mají být provedeny a `else if` příkaz nelze provést. Útočící kontextu může způsobit pak victim kontext pro spouštění `ProcessType` s objektem typu `CType1`. To může způsobit zmatení typu spekulativním Pokud podmíněnou větev v první `if` předpovídá příkaz přijata a `else if` příkaz předpovídá není přijatá, tedy provádění těla `else if` a přetypováním objektu typu `CType1` k `CType2`. Protože `CType2::dispatch_routine` pole se překrývá s `char` pole `CType1::field1`, to mohlo způsobit spekulativního nepřímé větve k cíli neúmyslnému větve. Pokud útočící kontextu určit hodnoty bajt `CType1::field1` pole, mohou být schopni řídit adresu cílové větve.

## <a name="speculative-uninitialized-use"></a>Spekulativní neinicializované použití

Tato kategorie pravidel psaní kódu zahrnuje scénáře, kde může spekulativního spouštění přístup k neinicializované paměti a použít ho ke kanálu zatížení následné nebo nepřímé větev. Útočník pro jehož zneužití tyto vzorce kódování, musí být schopný řídit nebo smysluplně ovlivnit obsah, který se používá bez během inicializace podle kontextu, který se používá v paměti.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>Spekulativní neinicializované použití, což vede k celočíselných načíst.

Spekulativní použití neinicializovaného může potenciálně vést k celočíselných načtení pomocí hodnotu útočník řídit. V příkladu níže hodnotu `index` je přiřazena `trusted_index` ve všech cestách architektury a `trusted_index` je považován za menší než nebo rovno `buffer_size`. V závislosti na kód vytvořený kompilátorem, je však možné jednorázové přihlášení spekulativního úložiště může dojít, který umožňuje načtení z `buffer[index]` a závislé výrazy k provedení před přiřazení `index`. Pokud k tomu dojde, neincializované hodnoty pro `index` se použije jako posun do `buffer` která by mohla útočníkovi umožnit čtení celočíselných citlivé informace a sdělit to přes kanál na straně prostřednictvím závislé zatížení `shared_buffer` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>Spekulativní neinicializované použít počáteční nepřímé větví

Spekulativní použití neinicializovaného může vést k nepřímé větve ve kterém je řízen cíl větve ze strany útočníka. V následujícím příkladu `routine` přiřazen buď `DefaultMessageRoutine1` nebo `DefaultMessageRoutine` závisí na hodnotě `mode`. Na cestě pro architektury, výsledkem bude `routine` vždy inicializovat náskok před nepřímé větve. Ale v závislosti na kód vytvořený kompilátorem, jednorázové přihlášení spekulativního úložiště může dojít k umožňující nepřímé větev prostřednictvím `routine` speculatively provádět náskok před přiřazení `routine`. V tomto případě útočník může být možné spustit dotaz speculatively z libovolné adresy, za předpokladu, že útočník může ovlivnit nebo řídit neincializované hodnoty z `routine`.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>Možnosti omezení rizik

Ohrožení zabezpečení spekulativního spouštění na straně kanálu je možné zmírnit tím, že změny zdrojového kódu. Tyto změny mohou zahrnovat snížení rizik souvisejících s konkrétní instance ohrožení zabezpečení, jako například přidávání *spekulační bariéru*, nebo tím, že změny v návrhu aplikace provádět citlivé informace do nedostupný spekulativního pro spuštění.

### <a name="speculation-barrier-via-manual-instrumentation"></a>Spekulační bariéru prostřednictvím ručního instrumentace

A *spekulační bariéru* lze ručně vložit vývojářem, aby se zabránilo spekulativního spouštění z budete pokračovat bez architektury cestě. Například může vývojář vloží spekulační bariéru před vzoru nebezpečné psaní kódu v těle podmíněný blok, buď na začátku bloku (po podmíněná větev) nebo před prvním načtením, která má problém. To zabrání misprediction podmíněná větev z provádění nebezpečného kódu na cestě architektury pomocí serializace spuštění. Pořadí spekulační bariéru se liší podle architektury hardwaru, jak je popsáno v následující tabulce:

|Architektura|Spekulační bariéru vnitřní pro CVE-2017-5753|Vnitřní pro CVE-2018-3639 spekulační bariéru|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence()|_mm_lfence()|
|ARM|není aktuálně k dispozici|__dsb(0)|
|ARM64|není aktuálně k dispozici|__dsb(0)|

Například následující vzorek kódu lze zmírnit použitím `_mm_lfence` vnitřní, jak je znázorněno níže.

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

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>Spekulační bariéru prostřednictvím kompilaci instrumentace

Kompilátor Visual C++ v sadě Visual Studio 2017 (od verze 15.5.5) zahrnuje podporu pro `/Qspectre` přepínač, který automaticky vloží spekulační bariéru pro omezenou sadu potenciálně ohrožená vzorce kódování související s CVE-2017-5753. V dokumentaci [/qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre) příznak poskytuje další informace o jeho dopady a využití. Je důležité si uvědomit, že tento příznak nepopisuje všechny potenciálně ohrožená vzorce kódování a jako takový vývojáři by neměl spoléhat jako komplexní omezení rizik pro tuto třídu ohrožení zabezpečení.

### <a name="masking-array-indices"></a>Indexy pole maskování

V případech, kde spekulativního celočíselných zatížení může dojít, index pole může být důrazně ohraničené v cestě architektury a jiné architektury přidávání logiky explicitně vázaný index pole. Například pokud pole mohou být přiděleny velikostí, která je umístěno na mocninou čísla 2, pak jednoduché maska je možné vytvářet. To je znázorněno v následující ukázce, ve kterém se předpokládá, který `buffer_size` zarovnán mocninou čísla 2. To zajistí, že `untrusted_index` je vždy menší než `buffer_size`i v případě, že dojde k misprediction podmíněná větev a `untrusted_index` byl předán pomocí hodnotu větší než nebo rovna hodnotě `buffer_size`.

Je třeba poznamenat, že maskování indexu tady provádět může být v souladu s obejít spekulativního úložiště v závislosti na kód, který je generovaný kompilátorem.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>Odebrání citlivých informací z paměti

Další technikou, který slouží k omezení spekulativního spouštění na straně kanálu ohrožení zabezpečení je odebrání citlivých informací z paměti. Vývojáři softwaru můžete vyhledat příležitosti k refaktorování své aplikace tak, aby citlivých informací není přístupné během spekulativního spouštění. To lze provést refaktoring návrhu aplikace izolovat citlivé informace do samostatné procesy. Například aplikace webového prohlížeče může pokusit o izolovat data související s každou původu webového do samostatné procesy zamezuje tak nebudou mít přístup k datům nepůvodního prostřednictvím spekulativního spouštění jeden proces.

## <a name="see-also"></a>Viz také:

[Pokyny ke zmírnění chyby zabezpečení na straně kanálu spekulativního spouštění](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[Omezení spekulativního spouštění na straně kanálu hardwarové ohrožení zabezpečení](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
