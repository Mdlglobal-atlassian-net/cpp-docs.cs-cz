---
title: Přehled konvencí ARM64 ABI
ms.date: 07/11/2018
ms.openlocfilehash: c5c928dcb77729f5b79433d3be1b552664a0d211
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599781"
---
# <a name="overview-of-arm64-abi-conventions"></a>Přehled konvencí ARM64 ABI

Základní ABI pro Windows, při kompilaci a spuštění na procesorech ARM v režimu 64-bit (ARMv8 nebo novější architektury), většinou se řídí standardní EABI AArch64 na ARM. Tento článek popisuje některé z klíčových předpokladů a změny z je uvedeno v EABI. Informace o ABI 32-bit, naleznete v tématu [přehled ARM ABI konvence](overview-of-arm-abi-conventions.md). Další informace o standardní EABI ARM naleznete v tématu [aplikace binární rozhraní ABI () pro architekturu ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externí odkaz).

## <a name="definitions"></a>Definice

Se zavedením 64bitová podpora ARM definoval několika podmínek:

- **AArch32** – starší verze instrukce 32-bit nastaven architektury (ISA) určené ARM, včetně spuštění režimu Thumb.
- **AArch64** – architektura (ISA) určené ARM nastavit nové 64bitové instrukce.
- **ARMv7** – specifikace "7 generování" hardwaru ARM, která bude obsahovat pouze podporu pro AArch32. Toto je verze ARM hardware, který je první verze nástroje Windows pro ARM není podporovaná.
- **ARMv8** – specifikace "8 generování" hardwaru ARM, která zahrnuje podporu pro AArch32 i AArch64.

Kromě těchto definic v Windows používáme tyto podmínky:

- **ARM** – odkazuje na 32bitová architektura ARM (AArch32). To se někdy označuje jako WoA (Windows na ARM).
- **ARM32** – je to stejné jako ARM, výše; použité v tomto dokumentu pro přehlednost.
- **ARM64** – odkazuje na 64bitová architektura ARM (AArch64). Není k dispozici i WoA64.

A konečně k odkazování na typy dat, jsou odkazovány následující definice z ARM:

- **Krátký vektor** – Toto je datový typ, který je přímo reprezentovat SIMD, například vektor 8 nebo 16 bajtů za prvky zarovnané velikosti (8 nebo 16 bajtů), kde každý prvek může být 1, 2, 4 nebo 8 bajtů
- **HFA (homogenní plovoucí desetinné čárky agregace)** – jedná se o typ dat se 2 až 4 identické s plovoucí desetinnou čárkou členy (float nebo Double)
- **HVA (homogenní krátkého vektoru agregace)** – Toto je datový typ s identickými členy krátkého vektoru 2 až 4

## <a name="base-requirements"></a>Základní požadavky

Verzi Windows pro ARM64 se předpokládá, že je spuštěn na ARMv8 nebo novější architekturu neustále. Obě s plovoucí desetinnou čárkou a podporu NEON se předpokládá, že bude k dispozici v hardwaru.

I když specifikaci ARMv8 umožňuje plnou podporu AArch32 aplikací, nejsou momentálně žádné plány pro podporu spouštíte existující aplikace ARM32 na ARM64 verzi Windows (například žádné plány pro WOW64). To se řídí opětovného hodnocení v budoucnu, ale je aktuální pracovní předpokladů.

Specifikace ARMv8 popisuje nový volitelný crypto a operační kódy CRC pomocné rutiny pro AArch32 a AArch64. Podpora pro tyto je momentálně volitelné, ale doporučený. Kód, které chtějí využívat tyto operační kódy by měl provádět kontroly za běhu pro jejich existence.

## <a name="endianness"></a>Ukládání významných bajtů

Jako s ARM32 verze Windows na ARM64 Windows spustí v režimu little endian. Přepínání ukládání významných bajtů je obtížné dosáhnout bez podpory režimu jádra v AArch64, aby bylo snazší vynutit.

## <a name="alignment"></a>Zarovnání

Windows běží na ARM64 umožňuje procesoru hardwarem pro zpracování nezarovnané přístupy transparentně. V zlepšení z AArch32 tato podpora teď také funguje pro všechny přístupy celé číslo (včetně přístupy více slov) a přístupy s plovoucí desetinnou čárkou.

Ale přístupy k paměti bez vyrovnávací paměti (zařízení) stále musí vždycky být zarovnány. To znamená, že pokud je kód, který může být volána po pro čtení a zápis nesprávně zarovnaná data z paměti bez mezipaměti, musí přehrávání akcí bezpečné a ujistěte se, že jsou všechny přístupy do souladu.

## <a name="integer-registers"></a>Celočíselné registry

Architektura AArch64 podporuje 32 registrů pro celé číslo, shrnuté dole:

|Registr|Volatile?|Role|
|-|-|-|
x0|Volatile|Parametr/začátku registrace 1, výsledek registrace
x1 x7|Volatile|Parametr/začátku registrace 2 až 8
x8 x15|Volatile|Pomocné registrů
x16 x17|Volatile|Volání procedury uvnitř pomocné registrů
x18|Non-volatile|Platforma registrace: v režimu jádra, odkazuje na KPCR aktuální procesoru; v uživatelském režimu odkazuje na TEB
x19 x28|Non-volatile|Pomocné registrů
x29/fp|Non-volatile|Ukazatel na rámec
x30/lr|Non-volatile|Zaregistruje odkaz

Každý registr přístupná jako hodnota úplného 64-bit (prostřednictvím x0 x30) nebo jako hodnotu 32-bit (prostřednictvím w0 – w30). operace 32-bit nulové rozšíření jejich výsledky až 64 bitů.

Podívejte se předávání podrobné informace týkající se použití parametru registrů parametrů.

Všimněte si, že na rozdíl od AArch32, počítač a této uložené Procedury nejsou indexované registrů a proto jsou omezeny v tom, jak k nim může přistupovat. Všimněte si, že neexistuje žádná x31 také zaregistrovat (který se používá kódování pro zvláštní účely).

Použití ukazatel na rámec (x29) je nutná pro kompatibilitu s rychlé procházení zásobníku používá trasování událostí pro Windows a dalších služeb. Musí odkazovat předchozí {x29, × 30} dvojice v zásobníku.

## <a name="floating-pointsimd-registers"></a>Zaregistruje desetinnou plovoucí, SIMD

Architektura AArch64 také podporuje 32 registrů plovoucí desetinnou/SIMD shrnuté dole:

Registr|Volatile?|Role
|-|-|-|
V0|Volatile|Parametr/začátku registrace 1, výsledek registrace
V1 v7|Volatile|Parametr/začátku zaregistruje 2 až 8
v8 v15|Non-volatile|Pomocný registrů (Všimněte si, že pouze s nízkou 64 bity není typu volatile)
V16 v31|Volatile|Pomocné registrů

Každý registr přístupná jako úplné hodnotu 128-bit (prostřednictvím v0-v31 nebo q0-Dotaz č. 31), jako hodnotu 64-bit (prostřednictvím d0-d31), jako hodnotu 32-bit (prostřednictvím s0-s31), jako hodnotu 16 bitů (prostřednictvím h0 h31) nebo jako hodnota 8 bitů (prostřednictvím b0 b31). Přístupy menší než 128 bitů přístup k nižší bity register úplné 128 bitů a ponechte zbývající bity beze změny, pokud není uvedeno jinak. (Všimněte si, že tím se značně liší od AArch32, ve kterém byly menší registrů zabaleny nad větší registrů.)

Kromě datových registrů registrace ovládacího prvku s plovoucí desetinnou čárkou (FPCR) má několik požadavků na různé bitová pole v rámci něj:

Bity|Význam|Volatile?|Role
|-|-|-|-|
26|AHP|Není typu Volatile.|Alternativní ovládací prvek poloviční přesností
25|ROZLIŠUJÍCÍ NÁZEV|Není typu Volatile.|Výchozí NaN režimu ovládací prvek
24|FZ|Non-volatile|Vyprázdnění nula režim ovládacího prvku
23-22|RMode|Non-volatile|Ovládací prvek režimu zaokrouhlení
15,12-8|Integrované vývojové prostředí/IXE/atd.|Není typu Volatile.|Výjimku zachytit povolit bits, musí být vždy 0.

## <a name="system-registers"></a>Registrů systému

Stejně jako AArch32 specifikace AArch64 poskytuje tři systém řídí "ID vlákna" registrů běžícím použít/přidělené následujícím způsobem:

Registr|Role
|-|-|
TPIDR_EL0|Rezervováno
TPIDRRO_EL0|Obsahuje číslo procesoru pro aktuální procesoru
TPIDR_EL1|Odkazuje na strukturu KPCR pro aktuální procesoru

## <a name="floating-point-exceptions"></a>Výjimky s plovoucí desetinnou čárkou

Podpora pro výjimky s plovoucí desetinnou čárkou IEEE je volitelné na AArch64 systémy. Pro varianty procesoru, které nemají hardwarové výjimky s plovoucí desetinnou čárkou jádra Windows tiše zachytí výjimky a implicitně zakazuje je do registru FPCR. Tím je zajištěno normalizované chování napříč varianty procesoru (v opačném případě kód vyvinuli na platformě bez samotné trvá neočekávané výjimky, když se používá platformy s podporou zjistit podpora výjimek).

## <a name="parameter-passing"></a>Předávání parametrů

Pro jiné variadické funkce Windows ABI následuje pravidla určená ARM pro předávání parametrů. Tato pravidla jsou výňatkem přímo z postup volání standardní architektuře AArch64:

### <a name="stage-a--initialization"></a>Fáze A – inicializace

Této fázi se provádí pouze jednou, před zahájením zpracování argumentů.

1. Na další General-purpose zaregistrovat číslo (NGRN) je nastavena na hodnotu nula.

1. Další SIMD a plovoucí desetinné čárky zaregistrovat číslo (NSRN) je nastaven na hodnotu nula.

1. Adresa dalšího skládaný argument (NSAA) je nastavena na hodnotu aktuální ukazatel zásobníku (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Fáze B – před odsazení a rozšíření argumentů

Pro každý argument v seznamu je použito první vyhovující pravidlo z následujícího seznamu. Pokud žádné pravidlo shody argument se používá bez jakýchkoli úprav.

1. Pokud typ argumentu je složený typ, jehož velikost nelze určit staticky tak, že volající a volaného, argument se zkopíruje do paměti a argument je nahrazena ukazatel na kopii. (Nejsou žádné takové typy v jazyce C/C++ však existují v jiných jazycích nebo jazyková rozšíření).

1. Pokud je typ argumentu HFA nebo HVA, pak tento argument se používá bez úprav.

1. Pokud typ argumentu je složený typ, který je větší než 16 bajtů, argument se zkopíruje na paměť přidělenou volajícím a argument je nahrazena ukazatel na kopii.

1. Pokud typ argumentu je složený typ velikost argumentu je zaokrouhlí nahoru na nejbližší násobek 8 bajtů.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Fáze C – přiřazení argumentů, které mají registry a zásobníku

Pro každý argument v seznamu následující pravidla se použijí pak dokud argument byl přidělen. Pokud argument je přiřazena k registru všechny nepoužívané bity v registru mít tento parametr nezadáte hodnotu. Pokud argument je přiřazená datová oblast zásobníku všechny nepoužívané odsazení bajtů mít tento parametr zadán hodnotu.

1. Pokud je argumentem polovině-, Single-, Double - nebo Quad přesnost s plovoucí desetinnou čárkou nebo typu Short Vector a NSRN je menší než 8, pak argument je přidělená k nejméně významných bitů v rejstříku [NSRN]. NSRN se zvýší o jedna. Argument teď byl přidělen.

1. Pokud je argument HFA nebo HVA a nejsou dostatečné volné SIMD a zaregistruje se s plovoucí desetinnou čárkou (NSRN + počet členů ≤ 8), je přidělena argument SIMD a zaregistruje plovoucí desetinné čárky (u jeden registr na člen HFA nebo HVA). NSRN se zvýší počet registrů použít. Argument teď byl přidělen.

1. Pokud je argumentem HFA nebo HVA NSRN nastavená na 8 a velikost argumentu se zaokrouhluje na nejbližší násobek 8 bajtů.

1. Pokud je argumentem HFA, HVA, zadejte Quad přesnost s plovoucí desetinnou čárkou nebo krátkého vektoru se zaokrouhlí NSAA až větší z 8 nebo přirozeného zarovnání typ argumentu.

1. Pokud je argumentem Typ polovině nebo jednoduchou přesnost s plovoucí desetinnou čárkou, velikost argumentu nastavená na 8 bajtů. Účinek jako by měl argument byl zkopírován do nejméně významných bitů 64-bit registru a zbývající bitů vyplněny neurčené hodnoty.

1. Pokud je argumentem HFA, HVA, polovině-, Single-, Double - nebo Quad přesnost s plovoucí desetinnou čárkou nebo typu Short Vector a argument je zkopírován do paměti na upravené NSAA. NSAA je zvýšen o velikost argumentu. Argument teď byl přidělen.

1. Pokud argument je celočíselný typ nebo typ ukazatele, velikost argumentu je menší než nebo rovna hodnotě 8 bajtů a NGRN je menší než 8, argument je zkopírován do nejméně významných bitů v x [NGRN]. NGRN se zvýší o jedna. Argument teď byl přidělen.

1. Pokud má argument zarovnání 16 NGRN se zaokrouhlí nahoru na nejbližší sudé číslo.

1. Pokud argument je Integrálový typ, velikost argumentu je rovno 16 a NGRN je kratší než 7, argument je zkopírován do x [NGRN] x [NGRN + 1]. x [NGRN] musí obsahovat nižší adresovaný double slovo vyjádření paměti argumentu. NGRN je zvýšen o dvou. Argument teď byl přidělen.

1. Pokud argument je složený typ a velikost v dvojslova argument není větší než 8 minus NGRN pak argument je zkopírována do registrů po sobě jdoucích pro obecné účely, začínající hodnotou x [NGRN]. Argument je předán jako by měl byla načtena do registrů z adresy double word souladu s pokyny omezeně distribuovatelných oprav načítání po sobě jdoucích registry z paměti (obsah libovolné nevyužité části registrů nejsou specifikována příslušné pořadí podle této normy). NGRN se zvýší počet registrů použít. Argument teď byl přidělen.

1. NGRN byla nastavená na 8.

1. NSAA se zaokrouhlí na větší z 8 nebo přirozené zarovnání typu argumentu...

1. Pokud argument je složený typ argumentu je zkopírován do paměti na upravené NSAA. NSAA je zvýšen o velikost argumentu. Argument teď byl přidělen.

1. Pokud velikost argumentu je menší než 8 bajtů. velikost argumentu nastavená na 8 bajtů. Efekt je jako argument byl zkopírován do nejméně významných bitů 64-bit registru a zbývající bitů vyplněny neurčené hodnoty.

1. Argument je zkopírován do paměti na upravené NSAA. NSAA je zvýšen o velikost argumentu. Argument teď byl přidělen.

### <a name="addendum-variadic-functions"></a>Dodatek: Variadické funkce

Funkce vyžadující proměnný počet argumentů jsou zpracovány jinak než výše, následujícím způsobem:

1. Všechny složené zachází stejně; žádná zvláštní zacházení HFAs nebo HVAs.

1. Nejsou použity SIMD a zaregistruje plovoucí desetinné čárky.

Efektivně to odpovídá následujícím pravidlům C.12–C.15 přidělit argumenty, které mají imaginární zásobníku, kde první 64 bajtů zásobníku se načtou do x0 x7 a všechny zbývající argumenty zásobníku jsou obvykle umístěny.

## <a name="return-values"></a>Vrácené hodnoty

Integrální hodnoty jsou vráceny v x0. Hodnoty s plovoucí desetinnou čárkou jsou vráceny v s0/d0/v0 podle potřeby.

Pro návrat podle hodnot, který nemůže být předány prostřednictvím registrů volající vyhrazuje blok paměti dostatečnou velikost a zarovnání pro uchování výsledku. Adresu bloku paměti se předají jako další argument funkce x8 pro typ POD, nebo v x0 (nebo pokud $ předá se x0 x1) pro typ bez POD. Volaný může změnit výsledek blok paměti v libovolném bodě během spuštění podprogramu (neexistuje žádný požadavek pro volaných zachovat hodnotu uloženou v x8, ale pro jiné než POD, adresu této vyrovnávací paměti musí být také vrácen v x0 volaným).

## <a name="stack"></a>Rámec

Následující Komisí iaasb ARM ABI musí zásobníku zůstat 16 bajtů zarovnána za všech okolností. AArch64 obsahuje funkce hardwaru, který generuje zarovnání zásobník chyb pokaždé, když se provádí relativní SP load nebo store a SP není 16 bajtů zarovnána. Tato funkce povolena po celou dobu spuštění Windows.

Funkce, které přidělit 4 kB nebo více vhodné zásobníku musí zajistit, aby každá stránka před poslední stránky je dotčená v pořadí, zajistila žádný kód můžete "leap přes" ochranné stránky, které Windows používá rozšíření zásobníku. Obvykle se to provádí `__chkstk` pomocné rutiny, která má vlastní konvence volání, které předává celkové přidělení zásobníku dělený 16 v x8.

## <a name="red-zone"></a>Červené zóny

16 bajtů oblast bezprostředně pod aktuální ukazatel zásobníku je vyhrazuje pro účely analýzy a dynamické opravy scénáře. To umožňuje kód pečlivě vygeneruje, má být vložen, který ukládá 2 registrů na [sp, #-16] a používá je dočasně libovolného důvodů. Jádra Windows zaručuje, že tyto 16 bajtů nedojde k přepsání Pokud nedojde k výjimce nebo přerušení, v režimu jádra i uživatele.

## <a name="kernel-stack"></a>Jádra zásobníku

Výchozím zásobníku režimu jádra ve Windows je šest stránek (24 kb). Třeba věnujte zvláštní pozornost funkce s velké zásobníku vyrovnávací paměti v režimu jádra. Ill-timed přerušení může pocházet pomocí velmi málo velkou rezervu a vytvoření zásobníku tísňový kontroly chyb.

## <a name="stack-walking"></a>Procházení zásobníku

Kód v rámci Windows je zkompilován pomocí ukazatele na rámce povolené ([/Oy-](../build/reference/oy-frame-pointer-omission.md)) k povolení procházení zásobníku rychlé. Upshot tohoto je, že x29 (fp) obecně odkazuje na další článek v řetězci, tedy {fp, lr} pár označující ukazatel na předchozí rámec v zásobníku a zpáteční adresu. Kód třetích stran je doporučujeme povolit ukazatele na rámce a aby bylo možné povolit pro zlepšení profilování a trasování.

## <a name="exception-unwinding"></a>Uvolňování výjimek

Uvolnění během zpracování výjimek je pomoc prostřednictvím kódy unwind. Kódy unwind je posloupnost bajtů uložené v části .xdata spustitelného souboru, které popisují operace prologu a epilogu abstraktní způsobem tak, aby efekty prologu funkce může vrátit zpět, během přípravy na zálohování rámce zásobníku volajícího. Další informace o kódy unwind najdete v tématu [zpracování výjimek ARM64](arm64-exception-handling.md).

ARM EABI také určuje model odvíjení výjimky, že se parsovat kódy unwind využívá. Specifikace uvedenou však není dostatečná pro uvolnění ve Windows, které musí zpracovat případech, kdy je počítač uprostřed prologu nebo epilogu funkce.

Kód, který generuje dynamicky by měl být popsán s tabulkami dynamické funkce prostřednictvím `RtlAddFunctionTable` a související funkce, tak, aby vygenerovaného kódu mohl podílet na zpracování výjimek.

## <a name="cycle-counter"></a>Čítač cyklu

Všechny procesory ARMv8 jsou vyžadovány pro podporu cyklus čítače registrace. Toto je 64-bit registru, který konfiguruje Windows, aby byly čitelné na libovolné úrovni výjimky (včetně režim). Je přístupný prostřednictvím speciální PMCCNTR_EL0 zaregistrovat, pomocí operačního kódu MSR v kódu sestavení nebo `_ReadStatusReg` vnitřní v kódu C/C++.

Nezapomeňte ale, že čítač cyklus je true cyklu čítače, není wall hodinami a proto počítání frekvence se bude lišit podle frekvence procesoru. Pokud se domníváte, že musíte znát četnost cyklu čítače, neměli byste používat čítač cyklu. Místo toho chcete měřit skutečný čas, pro kterou byste měli použít `QueryPerformanceCounter`.

## <a name="see-also"></a>Viz také:

[Běžné problémy s migrací ARM v prostředí Visual C++](../build/common-visual-cpp-arm-migration-issues.md)<br/>
[Zpracování výjimek ARM64](../build/arm64-exception-handling.md)
