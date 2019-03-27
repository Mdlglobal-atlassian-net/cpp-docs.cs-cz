---
title: Přehled konvencí ARM64 ABI
ms.date: 03/27/2019
ms.openlocfilehash: 2695ba69c642b2100ec041d1f85debb4ad7041c8
ms.sourcegitcommit: 06fc71a46e3c4f6202a1c0bc604aa40611f50d36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58508855"
---
# <a name="overview-of-arm64-abi-conventions"></a>Přehled konvencí ARM64 ABI

Binární rozhraní základní aplikace (ABI) pro Windows při kompilaci a spuštění na procesorech ARM v režimu 64-bit (ARMv8 nebo novější architektury), většinou se řídí standardní EABI AArch64 na ARM. Tento článek popisuje některé z klíčových předpokladů a změny z je uvedeno v EABI. Informace o ABI 32-bit, naleznete v tématu [přehled ARM ABI konvence](overview-of-arm-abi-conventions.md). Další informace o standardní EABI ARM naleznete v tématu [aplikace binární rozhraní ABI () pro architekturu ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externí odkaz).

## <a name="definitions"></a>Definice

Se zavedením 64bitová podpora ARM definoval několika podmínek:

- **AArch32** – starší verze instrukce 32-bit nastaven architektury (ISA) určené ARM, včetně spuštění režimu Thumb.
- **AArch64** – architektura (ISA) určené ARM nastavit nové 64bitové instrukce.
- **ARMv7** – specifikace "7 generování" hardwaru ARM, která bude obsahovat pouze podporu pro AArch32. Tato verze hardwaru ARM je první verze Windows pro ARM nepodporuje.
- **ARMv8** – specifikace "8 generování" hardwaru ARM, která zahrnuje podporu pro AArch32 i AArch64.

Windows také používá tyto podmínky:

- **ARM** – odkazuje na 32bitová architektura ARM (AArch32), někdy označovány jako WoA (Windows na ARM).
- **ARM32** – je to stejné jako ARM, výše; použité v tomto dokumentu pro přehlednost.
- **ARM64** – odkazuje na 64bitová architektura ARM (AArch64). Není k dispozici i WoA64.

A konečně k odkazování na typy dat, jsou odkazovány následující definice z ARM:

- **Krátký vektor** – datový typ, který je přímo reprezentovat SIMD, vektor bajtů 8 nebo 16 bajtů za elementy. Prvek je zarovnán na její velikost, 8 bajtů nebo 16 bajtů, kde každý prvek může být 1, 2, 4 nebo 8 bajtů.
- **HFA (homogenní plovoucí desetinné čárky agregace)** – datový typ s identickými členy s plovoucí desetinnou čárkou 2 až 4 čísel s plovoucí čárkou nebo zdvojnásobí.
- **HVA (homogenní krátkého vektoru agregace)** – datový typ s identickými členy krátkého vektoru 2 až 4.

## <a name="base-requirements"></a>Základní požadavky

Verzi Windows pro ARM64 se předpokládá, že je spuštěn na ARMv8 nebo novější architekturu neustále. Obě s plovoucí desetinnou čárkou a podporu NEON se předpokládá, že bude k dispozici v hardwaru.

Specifikace ARMv8 umožňuje plnou podporu AArch32 aplikací. Podporu pro existující aplikace ARM32 na verzi Windows pro ARM64 se však neplánuje. (To znamená, že jsou žádné plány pro WOW64). Tato podpora se může v budoucnu opakované vyhodnocení, ale je aktuální pracovní předpokladů.

Specifikace ARMv8 popisuje nový volitelný crypto a operační kódy CRC pomocné rutiny pro AArch32 a AArch64. Podpora pro ně je momentálně volitelné, ale doporučený. Abyste mohli využívat tyto operační kódy, aplikace by měla nejdříve kontroly za běhu pro jejich existence.

## <a name="endianness"></a>Ukládání významných bajtů

Jako s ARM32 verze Windows na ARM64 Windows spustí v režimu little endian. Přepínání ukládání významných bajtů je obtížné dosáhnout bez podpory režimu jádra v AArch64, aby bylo snazší vynutit.

## <a name="alignment"></a>Zarovnání

Windows běží na ARM64 umožňuje procesoru hardwarem pro zpracování nezarovnané přístupy transparentně. V zlepšení z AArch32 tato podpora teď také funguje pro všechny přístupy celé číslo (včetně přístupy více slov) a přístupy s plovoucí desetinnou čárkou.

Ale přístupy k paměti bez vyrovnávací paměti (zařízení) stále musí vždycky být zarovnány. Pokud kód může potenciálně čtení nebo zápisu nesprávně zarovnaná data z paměti bez mezipaměti, musí nezapomeňte zarovnat všechny přístupy.

## <a name="integer-registers"></a>Celočíselné registry

Architektura AArch64 podporuje 32 registrů pro celé číslo:

| Registr | Volatile? | Role |
| - | - | - |
| x0 | Volatile | Parametr/začátku registrace 1, výsledek registrace |
| x1-x7 | Volatile | Parametr/začátku registrace 2 až 8 |
| x8-x15 | Volatile | Pomocné registrů |
| x16-x17 | Volatile | Volání procedury uvnitř pomocné registrů |
| x18 | Non-volatile | Platforma registrace: v režimu jádra, odkazuje na KPCR aktuální procesoru; v uživatelském režimu odkazuje na TEB |
| x19-x28 | Non-volatile | Pomocné registrů |
| x29/fp | Non-volatile | Ukazatel na rámec |
| x30/lr | Non-volatile | Zaregistruje odkaz |

Každý registr přístupná jako hodnota úplného 64-bit (prostřednictvím x0 x30) nebo jako hodnotu 32-bit (prostřednictvím w0 – w30). operace 32-bit nulové rozšíření jejich výsledky až 64 bitů.

Podívejte se předávání podrobné informace týkající se použití parametru registrů parametrů.

Na rozdíl od AArch32 nejsou indexované registrů čítač programu (PC) a ukazatel zásobníku (SP). Že vás omezuje v tom, jak k nim může přistupovat. Všimněte si, že neexistuje žádná x31 také zaregistrovat. Kódování se používá pro zvláštní účely.

Ukazatel na rámec (x29) je nutná pro kompatibilitu s procházení rychlé zásobníku používá trasování událostí pro Windows a dalších služeb. Musí odkazovat předchozí {x29, × 30} dvojice v zásobníku.

## <a name="floating-pointsimd-registers"></a>Zaregistruje desetinnou plovoucí, SIMD

Architektura AArch64 také podporuje 32 registrů plovoucí desetinnou/SIMD shrnuté dole:

| Registr | Volatile? | Role |
| - | - | - |
| v0 | Volatile | Parametr/začátku registrace 1, výsledek registrace |
| v1-v7 | Volatile | Parametr/začátku zaregistruje 2 až 8 |
| v8-v15 | Non-volatile | Pomocný registrů (pouze s nízkou 64 bity není typu volatile) |
| v16-v31 | Volatile | Pomocné registrů |

Každý registr přístupná jako hodnota úplného 128-bit (prostřednictvím v0-v31 nebo q0-Dotaz č. 31). Mohly být přístupné jako hodnotu 64-bit (prostřednictvím d0-d31), jako hodnotu 32-bit (prostřednictvím s0-s31), jako hodnotu 16 bitů (prostřednictvím h0 h31) nebo jako hodnota 8 bitů (prostřednictvím b0 b31). Přístupy menší než 128 bitů přístup jenom k nižší bity úplné 128bitové registru. Opuštění zbývající bity beze změny není uvedeno jinak. (AArch64 se liší od AArch32, ve kterém byly menší registrů zabaleny nad větší registrů.)

Registr s plovoucí desetinnou čárkou ovládacího prvku (FPCR) má několik požadavků na různé bitová pole v rámci něj:

| Bity | Význam | Volatile? | Role |
| - | - | - | - |
| 26 | AHP | Není typu Volatile. | Alternativní ovládací prvek poloviční přesností. |
| 25 | ROZLIŠUJÍCÍ NÁZEV | Není typu Volatile. | Výchozí režim řízení NaN. |
| 24 | FZ | Non-volatile | Vyprázdnění nula režim ovládacího prvku. |
| 23-22 | RMode | Non-volatile | Ovládací prvek režim zaokrouhlení. |
| 15,12-8 | IDE/IXE/etc | Není typu Volatile. | Výjimku zachytit povolit bits, musí být vždy 0. |

## <a name="system-registers"></a>Registrů systému

Stejně jako AArch32 specifikace AArch64 poskytuje tři systém řídí "ID vlákna" registrů:

| Registr | Role |
| - | - |
| TPIDR_EL0 | Vyhrazená. |
| TPIDRRO_EL0 | Obsahuje číslo procesoru pro aktuální procesoru. |
| TPIDR_EL1 | Odkazuje na strukturu KPCR pro aktuální procesoru. |

## <a name="floating-point-exceptions"></a>Výjimky s plovoucí desetinnou čárkou

Podpora pro výjimky s plovoucí desetinnou čárkou IEEE je volitelné na AArch64 systémy. Pro varianty procesoru, které nemají hardwarové výjimky s plovoucí desetinnou čárkou jádra Windows tiše zachytí výjimky a implicitně zakazuje je do registru FPCR. Tuto depeši. zajišťuje normalizované chování napříč varianty procesoru. V opačném případě kód vyvinuli na platformě bez podpory výjimka zjistit samotné trvá neočekávané výjimky, když se používá platformy s podporou.

## <a name="parameter-passing"></a>Předávání parametrů

Pro jiné variadické funkce Windows ABI následuje pravidla určená ARM pro předávání parametrů. Tato pravidla jsou výňatkem přímo z postup volání standardní architektuře AArch64:

### <a name="stage-a--initialization"></a>Fáze A – inicializace

Této fázi se provádí pouze jednou, před zahájením zpracování argumentů.

1. Na další General-purpose zaregistrovat číslo (NGRN) je nastavena na hodnotu nula.

1. Další SIMD a plovoucí desetinné čárky zaregistrovat číslo (NSRN) je nastaven na hodnotu nula.

1. Adresa dalšího skládaný argument (NSAA) je nastavena na hodnotu aktuální ukazatel zásobníku (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Fáze B – před odsazení a rozšíření argumentů

Pro každý argument v seznamu je použito první vyhovující pravidlo z následujícího seznamu. Pokud žádné pravidlo shody, argument se používá bez jakýchkoli úprav.

1. Pokud typ argumentu je složený typ, jehož velikost nelze určit staticky tak, že volající a volaného, argument se zkopíruje do paměti a argument je nahrazena ukazatel na kopii. (Nejsou žádné takové typy v jazyce C/C++ však existují v jiných jazycích nebo jazyková rozšíření).

1. Pokud je typ argumentu HFA nebo HVA, pak tento argument se používá bez úprav.

1. Pokud typ argumentu je větší než 16 bajtů složený typ, pak se argument zkopíruje na paměť přidělenou volajícím a argument je nahrazena ukazatel na kopii.

1. Pokud typ argumentu je složený typ, velikost argumentu je zaokrouhlí nahoru na nejbližší násobek 8 bajtů.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Fáze C – přiřazení argumentů, které mají registry a zásobníku

Pro každý argument v seznamu následující pravidla se použijí pak dokud argument byl přidělen. Pokud argument je přiřazena k registru, všechny nepoužívané bity v registru mít tento parametr nezadáte hodnotu. Pokud argument je přiřazen k datová oblast zásobníku, všechny nepoužívané odsazení bajtů mít tento parametr nezadáte hodnotu.

1. Argument je částečně-, Single - dvojité nebo Quad přesnost s plovoucí desetinnou čárkou nebo typu Short Vector a NSRN je menší než 8, pak argument je přidělená k nejméně významných bitů v registru\[NSRN]. NSRN se zvýší o jedna. Argument teď byl přidělen.

1. Pokud argument je HFA nebo HVA a je dostatek volné SIMD a zaregistruje se s plovoucí desetinnou čárkou (NSRN + počet členů ≤ 8), je přidělena argument SIMD a registruje plovoucí desetinné čárky, jeden registr na člen HFA nebo HVA. NSRN se zvýší počet registrů použít. Argument teď byl přidělen.

1. Pokud je argumentem HFA nebo HVA, pak NSRN nastavená na 8 a velikost argumentu se zaokrouhluje na nejbližší násobek 8 bajtů.

1. Pokud argument je HFA, HVA, typu Quad přesnost s plovoucí desetinnou čárkou nebo krátký vektor, pak NSAA se zaokrouhlí na větší z 8 nebo přirozeného zarovnání typ argumentu.

1. Pokud je argumentem Typ polovině nebo jednoduchou přesnost s plovoucí desetinnou čárkou, velikost argumentu nastavená na 8 bajtů. Efekt je jako by měl argument byl zkopírován do nejméně významných bitů registru 64bitovým kompilátorem a zbývajících bitů vyplněny neurčené hodnoty.

1. Pokud je argumentem HFA, HVA, polovině-, Single-, Double- nebo Quad přesnost s plovoucí desetinnou čárkou nebo typu Short Vector a argument je zkopírován do paměti na upravené NSAA. NSAA je zvýšen o velikost argumentu. Argument teď byl přidělen.

1. Pokud argument je celočíselný typ nebo typ ukazatele, velikost argumentu je menší než 8 bajtů a NGRN je menší než 8, argument je zkopírován do nejméně významných bitů v x\[NGRN]. NGRN se zvýší o jedna. Argument teď byl přidělen.

1. Pokud má argument zarovnání 16, pak NGRN se zaokrouhluje na nejbližší sudé číslo.

1. Pokud argument je Integrálový typ, velikost argumentu je rovno 16 a NGRN je kratší než 7, argument je zkopírován do x\[NGRN] a x\[NGRN + 1]. x\[NGRN] musí obsahovat nižší adresovaný double slovo vyjádření paměti argumentu. NGRN je zvýšen o dvou. Argument teď byl přidělen.

1. Pokud argument je složený typ a velikost v dvojslova argumentu je více než 8 minus NGRN pak argument je zkopírována do po sobě jdoucích registrů pro obecné účely, začínající na x\[NGRN]. Argument je předán jako by měl byla načtena do registrů z adresy double word souladu s příslušnou posloupnost omezeně distribuovatelných oprav pokyny, které zatížení po sobě jdoucích registry z paměti. Podle této normy tento parametr zadán obsah libovolné nevyužité části registrů. NGRN se zvýší počet registrů použít. Argument teď byl přidělen.

1. NGRN byla nastavená na 8.

1. NSAA se zaokrouhlí na větší z 8 nebo přirozeného zarovnání typ argumentu.

1. Pokud argument je složený typ, argument je zkopírován do paměti na upravené NSAA. NSAA je zvýšen o velikost argumentu. Argument teď byl přidělen.

1. Pokud velikost argumentu je menší než 8 bajtů, velikost argumentu nastavená na 8 bajtů. Efekt je jako argument byl zkopírován do nejméně významných bitů 64-bit registru a zbývající bity bylo vyplněno neurčené hodnoty.

1. Argument je zkopírován do paměti na upravené NSAA. NSAA je zvýšen o velikost argumentu. Argument teď byl přidělen.

### <a name="addendum-variadic-functions"></a>Dodatek: Variadické funkce

Funkce vyžadující proměnný počet argumentů jsou zpracovány jinak než výše, následujícím způsobem:

1. Všechny složené zachází stejně; žádná zvláštní zacházení HFAs nebo HVAs.

1. Nejsou použity SIMD a zaregistruje plovoucí desetinné čárky.

Efektivně je stejný jako následující pravidla C.12–C.15 přidělit argumenty, které mají imaginární zásobníku, kde první 64 bajtů zásobníku se načtou do x0 x7 a všechny zbývající argumenty zásobníku jsou obvykle umístěny.

## <a name="return-values"></a>Vrácené hodnoty

Integrální hodnoty jsou vráceny v x0.

Hodnoty s plovoucí desetinnou čárkou jsou vráceny v s0/d0/v0 podle potřeby.

Typy vrácené hodnoty jsou zpracovány jinak v závislosti na tom, zda mají určité vlastnosti.

Typy jsou uvedena v každém vrácení styl "C" Pokud se agregovaná C ++ 14 standardní definice. To je

- nemají žádné uživatelem zadané konstruktory, žádné soukromé nebo chráněné nestatické datové členy, žádné základní třídy a žádné virtuální funkce
- mají triviální kopírovací konstruktor, a
- mají triviální destruktor.

Všechny ostatní typy jsou uvedeny návratový styl "C++".

### <a name="c-return-style"></a>Návratový stylu C

Menší než 8 bajtů se vrátí v x0 typy.

Typy menší než nebo rovno 16 bajtů se vrátí v x0 a x1 s x0 obsahující 8 bajtů nižšího řádu.

U typů větší než 16 bajtů se volající rezervovat blok paměti dostatečnou velikost a zarovnání pro uchování výsledku. Adresa bloku paměti se jako další argument předána funkci v x8. Volaný může změnit výsledek blok paměti v libovolném bodě během spuštění podprogramu. Volaný vyžadovat zachovávaní hodnotu uloženou v x8.

### <a name="c-return-style"></a>Návratový stylu C++

Volající musí rezervovat blok paměti dostatečnou velikost a zarovnání pro uchování výsledku. Adresa bloku paměti se předat jako další argument funkce v x0 nebo x1 Pokud $ předá se x0. Volaný může změnit výsledek blok paměti v libovolném bodě během spuštění podprogramu. Volaný vrátí adresu blok paměti v x0.

## <a name="stack"></a>Rámec

Následující Komisí iaasb ARM ABI musí zásobníku zůstat 16 bajtů zarovnána za všech okolností. AArch64 obsahuje funkce hardwaru, který generuje chyby zarovnání zásobníku pokaždé, když SP není zarovnána 16 bajtů a je proveden k vláknům SP zatížení nebo úložiště. Tato funkce povolena po celou dobu spuštění Windows.

Funkce, které přidělují 4 kB nebo více vhodné zásobníku musíte zajistit, že je v pořadí dotčená každou stránku před poslední stránky. Tím zajistíte žádný kód můžete "leap přes" ochranné stránky, které Windows používá rozšíření zásobníku. Obvykle dotýká se provádí `__chkstk` pomocné rutiny, která má vlastní konvence volání, které předává celkové přidělení zásobníku dělený 16 v x15.

## <a name="red-zone"></a>Červené zóny

16 bajtů oblast bezprostředně pod aktuální ukazatel zásobníku je vyhrazuje pro účely analýzy a dynamické opravy scénáře. Tato oblast povoluje pečlivě generovaného kódu má být vložen, která ukládá dvě registrů na [sp, #-16] a používá je dočasně libovolného důvodů. Jádra Windows zaručuje, že tyto 16 bajtů nejsou přepsány, pokud výjimku nebo přerušení je převzata, a v režimu jádra i uživatele.

## <a name="kernel-stack"></a>Jádra zásobníku

Výchozím zásobníku režimu jádra ve Windows je šest stránek (24 kb). Třeba věnujte zvláštní pozornost funkce s velké zásobníku vyrovnávací paměti v režimu jádra. Ill-timed přerušení může pocházet pomocí malé velkou rezervu a vytvoření tísňový chyby kontroly zásobníku.

## <a name="stack-walking"></a>Procházení zásobníku

Kód v rámci Windows je zkompilován pomocí ukazatele na rámce povolené ([/Oy-](reference/oy-frame-pointer-omission.md)) k povolení procházení zásobníku rychlé. Obecně platí, x29 (fp) odkazuje na další článek v řetězci, tedy {fp, lr} pár označující ukazatel na předchozí rámec v zásobníku a zpáteční adresu. Kód třetích stran je doporučujeme povolit, ukazatele na rámce umožňující lepší profilace a trasování.

## <a name="exception-unwinding"></a>Uvolňování výjimek

Uvolnění během zpracování výjimek je pomoc prostřednictvím kódy unwind. Kódy unwind je posloupnost bajtů, které jsou uložené v části .xdata spustitelného souboru. Popisují operace prologu a epilogu abstraktní způsobem tak, aby efekty prologu funkce může vrátit zpět, během přípravy na zálohování rámce zásobníku volajícího. Další informace o kódy unwind najdete v tématu [zpracování výjimek ARM64](arm64-exception-handling.md).

ARM EABI také určuje odvíjení model výjimek, který používá parsovat kódy unwind. Specifikace uvedenou ale nepostačuje pro uvolnění ve Windows, které musí zpracovat případech, kdy je počítač uprostřed funkce prologu nebo epilogu.

Kód, který generuje dynamicky by měl být popsán s tabulkami dynamické funkce prostřednictvím `RtlAddFunctionTable` a související funkce, tak, aby vygenerovaného kódu mohl podílet na zpracování výjimek.

## <a name="cycle-counter"></a>Čítač cyklu

Všechny procesory ARMv8 jsou vyžadovány pro podporu cyklu čítač zaregistrovat, 64-bit registru, který konfiguruje Windows, aby byly čitelné na libovolné úrovni výjimky, včetně uživatelského režimu. Je přístupný prostřednictvím speciální PMCCNTR_EL0 zaregistrovat, pomocí operačního kódu MSR v kódu sestavení nebo `_ReadStatusReg` vnitřní v kódu C/C++.

Čítač cyklus je čítač true cyklu, není skutečný hodiny. Počítání frekvence se bude lišit při frekvenci procesoru. Pokud se domníváte, že musíte znát četnost cyklu čítače, neměli byste používat čítač cyklu. Místo toho chcete měřit skutečný čas, pro kterou byste měli použít `QueryPerformanceCounter`.

## <a name="see-also"></a>Viz také:

[Běžné problémy s migrací ARM v prostředí Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Zpracování výjimek ARM64](arm64-exception-handling.md)
