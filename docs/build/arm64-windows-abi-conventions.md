---
title: Přehled konvencí ARM64 ABI
ms.date: 03/27/2019
ms.openlocfilehash: 07d58bbd64795235ad63a7b26b6f18fcffdcd1d2
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303271"
---
# <a name="overview-of-arm64-abi-conventions"></a>Přehled konvencí ARM64 ABI

Základní binární rozhraní aplikace (ABI) pro systém Windows při kompilování a spuštění na procesorech ARM v 64ovém režimu (ARMv8 nebo novější architektury), a to z toho důvodu, že následuje Standard AArch64 EABI úrovně Standard pro ARM. Tento článek popisuje některé klíčové předpoklady a změny, které jsou popsané v EABI. Informace o 32-bit ABI najdete v tématu [Přehled konvencí ABI pro ARM](overview-of-arm-abi-conventions.md). Další informace o standardu ARM EABI naleznete v tématu [Application Binary Interface (ABI) pro architekturu ARM](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.subset.swdev.abi/index.html) (externí odkaz).

## <a name="definitions"></a>Definice

Díky zavedení podpory 64 bitů definoval ARM několik podmínek:

- **AArch32** – 32bitová verze 32 sady instrukcí (ISA) definovaná v ARM, včetně spuštění režimu pořizování.
- **AArch64** – nová 64á architektura sady instrukcí (ISA) definovaná ARM.
- **ARMv7** – specifikace hardwaru ARM "7. generace", který zahrnuje pouze podporu pro AArch32. Tato verze hardwaru ARM je první podporovanou verzí Windows pro ARM.
- **ARMv8** – specifikace hardwaru ARM "8. generace", který zahrnuje podporu pro AArch32 i AArch64.

Systém Windows používá také tyto výrazy:

- **ARM** – odkazuje na architekturu ARM 32 (AArch32), někdy označovanou jako WOA (Windows on ARM).
- **ARM32** – totéž jako ARM, nahoře; používá se v tomto dokumentu k přehlednost.
- **ARM64** – odkazuje na architekturu ARM 64 (AArch64). Neexistují žádné takové věci jako WoA64.

Nakonec při odkazování na datové typy jsou odkazovány následující definice z ARM:

- **Krátký vektor** – datový typ přímo reprezentovatelné v SIMD, vektor s 8 bajty nebo 16 bajty pro prvky. Je zarovnána na velikost, buď 8 bajtů, nebo 16 bajtů, kde každý prvek může mít 1, 2, 4 nebo 8 bajtů.
- **HFA (homogenní agregace s plovoucí desetinnou** čárkou) – datový typ, který má 2 až 4 stejné členy s plovoucí desetinnou čárkou, buď float, nebo Double.
- **HVA (homogenní Krátká vektorová agregace)** – datový typ s 2 až 4 identickými členy krátkého vektoru.

## <a name="base-requirements"></a>Základní požadavky

Verze ARM64 systému Windows předchází, že je v současné době spuštěná v architektuře ARMv8 nebo novějším. V hardwaru se předpokládá, že jsou k dispozici obě podpory s plovoucí desetinnou čárkou a NEON.

Specifikace ARMv8 popisuje nové volitelné kryptografie a pomocné operační kódy CRC pro AArch32 a AArch64. Podpora pro ně je aktuálně volitelná, ale doporučuje se. Aby bylo možné využít tyto operační kódy, aplikace by nejdřív měly provádět kontroly za běhu pro jejich existenci.

## <a name="endianness"></a>Endianitou

Stejně jako u ARM32 verze Windows se v ARM64 Windows spouští v režimu Little endian. Přepínání na endian je obtížné dosáhnout bez podpory režimu jádra v AArch64, takže je snazší je vymáhat.

## <a name="alignment"></a>Zarovnání

Systém Windows spuštěný v ARM64 umožňuje hardwaru procesoru zpracovávat nesprávně zarovnaný přístup transparentně. V vylepšení od AArch32 tato podpora teď funguje taky pro všechna přístup k celému číslu (včetně přístupů do více slov) a pro přístup k plovoucí desetinné čárce.

Přístup k paměti bez mezipaměti (zařízení) je však stále nutné zarovnávat. Pokud by kód mohl číst nebo zapisovat nesprávně zarovnaná data z paměti, která není v mezipaměti, je nutné zajistit, aby všechny přístupy byly zarovnány.

Výchozí zarovnání rozložení pro národní prostředí:

| Velikost v bajtech | Zarovnání v bajtech |
| - | - |
| 1 | 1 |
| 2 | 2 |
| 3, 4 | 4 |
| > 4 | 8 |

Výchozí zarovnání rozložení pro globální a statické prvky:

| Velikost v bajtech | Zarovnání v bajtech |
| - | - |
| 1 | 1 |
| 2 - 7 | 4 |
| 8 - 63 | 8 |
| >= 64 | 16 |

## <a name="integer-registers"></a>Celočíselné registry

Architektura AArch64 podporuje Registry typu Integer 32:

| Registr | Permanentní? | Role |
| - | - | - |
| x0 | Permanentní | Parametr/Scrat registr 1, výsledný registr |
| x1-x7 | Permanentní | Parametr/Scrat registr 2-8 |
| x8-x15 | Permanentní | Odkládací Registry |
| x16-x17 | Permanentní | Odkládací Registry uvnitř procedury – volání |
| x18 | Bez volatile | Registr platformy: v režimu jádra odkazuje na KPCR pro aktuální procesor; v uživatelském režimu odkazuje na TEB |
| x19-x28 | Bez volatile | Odkládací Registry |
| x29/FP | Bez volatile | Ukazatel na rámec |
| X30/LR | Bez volatile | Registry odkazů |

Ke každému registru může být přistup jako k úplné 64ové hodnotě (přes x0-X30) nebo jako 32 hodnota (prostřednictvím W0-W30). 32 bitové operace nulové – rozšíří své výsledky až do 64 bitů.

Podrobnosti o použití registrů parametrů naleznete v části předání parametru.

Na rozdíl od AArch32 nejsou indexy programu (PC) a ukazatel zásobníku (SP) indexované Registry. Jsou omezené na to, jak k nim mají přistup. Všimněte si také, že není k dispozici žádný x31 registr. Toto kódování se používá pro speciální účely.

Pro zajištění kompatibility s rychlým procházením pomocí trasování událostí pro Windows a dalšími službami se vyžaduje ukazatel na rámec (x29). Musí odkazovat na předchozí dvojici {x29, X30} v zásobníku.

## <a name="floating-pointsimd-registers"></a>Registry s plovoucí desetinnou čárkou/SIMD

Architektura AArch64 podporuje taky 32 Registry s plovoucí desetinnou čárkou nebo SIMD, které jsou shrnuté níže:

| Registr | Permanentní? | Role |
| - | - | - |
| v0 | Permanentní | Parametr/Scrat registr 1, výsledný registr |
| v1-v7 | Permanentní | Parametry/pomocné Registry 2-8 |
| v8-v15 | Bez volatile | Odkládací Registry (pouze nízké 64 bity jsou nestálé) |
| v16-v31 | Permanentní | Odkládací Registry |

Ke každému registru může být přistup jako k úplné 128ové hodnotě (přes v0-V31 nebo Q0-Q31). Je možné, že je k ní přistupovaná hodnota 64 (přes D31), jako 32 hodnota (prostřednictvím S0-S31), jako 16bitová hodnota (prostřednictvím H0-H31) nebo jako 8bitové hodnoty (prostřednictvím B0-B31). Přístup k menšímu počtu než 128 bitů přistupuje pouze k dolním bitům plného 128 bitového registru. Zbývající bity zůstanou beze změny, pokud není uvedeno jinak. (AArch64 se liší od AArch32, kde menší registry byly zabaleny nad většími Registry.)

Registr ovládacího prvku s plovoucí desetinnou čárkou (FPCR) má určité požadavky na různé bitová pole v rámci něj:

| Bity | Význam | Permanentní? | Role |
| - | - | - | - |
| 26 | AHP | Bez volatile | Alternativní ovládací prvek s poloviční přesností |
| 25 | ROZLIŠUJÍCÍ NÁZEV | Bez volatile | Výchozí ovládací prvek režimu NaN. |
| 24 | FZ | Bez volatile | Řízení režimu vyprázdnění na nulu. |
| 23-22 | RMode | Bez volatile | Ovládací prvek režimu zaokrouhlování |
| 15,12-8 | IDE/IXE/atd. | Bez volatile | Depeše výjimky povolit bity, musí být vždy 0. |

## <a name="system-registers"></a>Systémové Registry

Podobně jako AArch32 poskytuje specifikace AArch64 tři Registry "ID vlákna řízené systémem":

| Registr | Role |
| - | - |
| TPIDR_EL0 | Rezervovaný. |
| TPIDRRO_EL0 | Obsahuje číslo procesoru pro aktuální procesor. |
| TPIDR_EL1 | Odkazuje na KPCR strukturu pro aktuální procesor. |

## <a name="floating-point-exceptions"></a>Výjimky s plovoucí desetinnou čárkou

Podpora výjimek s plovoucí desetinnou čárkou IEEE je volitelná v systémech AArch64. V případě variant procesoru, které mají hardwarové výjimky s plovoucí desetinnou čárkou, jádro systému Windows tiše tyto výjimky zachytí a implicitně je zakáže v registru FPCR. Tato depeše zajišťuje normalizované chování napříč variantami procesoru. V opačném případě kód vyvinutý na platformě bez podpory výjimek může při spuštění na platformě s podporou najít neočekávané výjimky.

## <a name="parameter-passing"></a>Předávání parametrů

Pro funkce, které nejsou variadické, se v systému Windows ABI za předáváním parametrů řídí pravidla určená ARM. Tato pravidla jsou výňatkem přímo ze standardního volání procedury pro architekturu AArch64:

### <a name="stage-a--initialization"></a>Fáze A – inicializace

Tato fáze se provádí přesně jednou a před tím, než začne zpracování argumentů.

1. Další číslo registračního čísla (NGRN) pro obecné účely je nastaveno na hodnotu nula.

1. Další SIMD a číslo registru s plovoucí desetinnou čárkou (NSRN) je nastaveno na hodnotu nula.

1. Další adresa skládaného argumentu (NSAA) je nastavená na aktuální hodnotu ukazatele na zásobník (SP).

### <a name="stage-b--pre-padding-and-extension-of-arguments"></a>Fáze B – předběžné vyplnění a rozšíření argumentů

Pro každý argument v seznamu se použije první pravidlo pro porovnání z následujícího seznamu. Pokud se neshodují žádné pravidlo, argument se použije jako nezměněný.

1. Je-li typ argumentu složený typ, jehož velikost nelze staticky určit volajícím i volaným, je argument zkopírován do paměti a argument je nahrazen ukazatelem na kopii. (Žádné takové typy nejsou v jazyce C/C++ , ale existují v jiných jazycích nebo v jazykových rozšířeních).

1. Je-li typ argumentu HFA nebo HVA, pak je argument použit jako nezměněný.

1. Je-li typ argumentu složený typ větší než 16 bajtů, pak je argument zkopírován do paměti přidělené volajícím a argument je nahrazen ukazatelem na kopii.

1. Pokud je typ argumentu složený typ, pak se velikost argumentu zaokrouhlí na nejbližší násobek 8 bajtů.

### <a name="stage-c--assignment-of-arguments-to-registers-and-stack"></a>Fáze C – přiřazení argumentů k registrům a zásobníku

U každého argumentu v seznamu jsou následující pravidla aplikována postupně, dokud není argument přidělen. Při přiřazení argumentu k registru mají všechny nepoužívané bity v registru nespecifikovanou hodnotu. Pokud je argument přiřazen k slotu zásobníku, nepoužité Bajty odsazení mají nespecifikovanou hodnotu.

1. Pokud je argumentem poloviční, jednoduchá, dvojitá nebo typ krátkého vektoru s plovoucí desetinnou čárkou nebo typem krátkého vektoru a NSRN je menší než 8, pak je argument přidělen nejméně významnému počtu bitů registru v\[NSRN]. NSRN se zvyšuje o jednu. Argument byl nyní přidělen.

1. Pokud je argumentem HFA nebo HVA a existuje dostatečný počet nepřidělených SIMDů a registrů s plovoucí desetinnou čárkou (NSRN + počet členů ≤ 8), pak je argument přidělen SIMD a registru s plovoucí desetinnou čárkou, jeden registr na člena HFA nebo HVA. NSRN se zvyšuje podle počtu využitých registrů. Argument byl nyní přidělen.

1. Pokud je argumentem HFA nebo HVA, pak je NSRN nastaven na 8 a velikost argumentu se zaokrouhlí na nejbližší násobek 8 bajtů.

1. Pokud je argumentem HFA, HVA, typ s plovoucí desetinnou čárkou nebo krátkým vektorem, pak je NSAA zaokrouhlena na větší než 8 nebo přirozené zarovnání typu argumentu.

1. Pokud je argumentem Typ s plovoucí desetinnou čárkou typu poloviční nebo s jednoduchou přesností, pak je velikost argumentu nastavená na 8 bajtů. Efekt je takový, jak byl argument zkopírován do nejméně významných bitů 64 registru a zbývající bity vyplní neurčenými hodnotami.

1. Je-li argumentem HFA, HVA, typ s plovoucí desetinnou čárkou nebo krátkým vektorem, který je typu Double nebo quad, pak je argument zkopírován do paměti v upraveném NSAA. NSAA se zvyšuje o velikost argumentu. Argument byl nyní přidělen.

1. Pokud je argumentem integrální typ nebo typ ukazatele, velikost argumentu je menší nebo rovna 8 bajtů a hodnota NGRN je menší než 8, argument je zkopírován do nejméně významných bitů v x\[NGRN]. NGRN se zvyšuje o jednu. Argument byl nyní přidělen.

1. Pokud má argument zarovnání 16, pak se NGRN zaokrouhlí nahoru na další sudé číslo.

1. Pokud je argumentem integrální typ, je velikost argumentu rovna 16 a hodnota NGRN je menší než 7, je argument zkopírován do x\[NGRN] a x\[NGRN + 1]. x\[NGRN] obsahuje méně adresované dvojité slovo reprezentace argumentu. NGRN se zvyšuje o dva. Argument byl nyní přidělen.

1. Je-li argumentem složený typ a velikost v dvojitých slovech argumentu není více než 8 minus NGRN, pak je argument zkopírován do po sobě jdoucích registrů pro obecné účely, počínaje hodnotou x\[NGRN]. Argument je předán, jako by byl načten do registrů z adresy zarovnané na dvě slova s odpovídající posloupností instrukcí LDR, které načítají po sobě jdoucí Registry z paměti. Obsah žádné nepoužívané části registrů není specifikován tímto standardem. NGRN se zvyšuje podle počtu využitých registrů. Argument byl nyní přidělen.

1. NGRN je nastavená na 8.

1. NSAA se zaokrouhluje na větší než 8 nebo přirozené zarovnání typu argumentu.

1. Je-li argumentem složený typ, je argument zkopírován do paměti upravenou NSAA. NSAA se zvyšuje o velikost argumentu. Argument byl nyní přidělen.

1. Pokud je velikost argumentu menší než 8 bajtů, pak je velikost argumentu nastavená na 8 bajtů. Efekt je, jako by byl argument zkopírován do nejméně významných bitů 64 registru a zbývající bity byly vyplněny nezadanými hodnotami.

1. Argument je zkopírován do paměti ve upraveném NSAA. NSAA se zvyšuje o velikost argumentu. Argument byl nyní přidělen.

### <a name="addendum-variadic-functions"></a>Dodatek: funkce variadické

Funkce, které přijímají proměnlivý počet argumentů, jsou zpracovávány jinak než výše, následovně:

1. Všechny složené barvy jsou ošetřeny podobně; žádné zvláštní zacházení s HFAs ani HVAs.

1. SIMD a nepoužívají se Registry s plovoucí desetinnou čárkou.

Efektivně je stejný jako u následujících pravidel C. 12 – C. 15 pro přidělení argumentů do imaginárního zásobníku, kde první 64 bajtů zásobníku je načteno do x0-120 a všechny zbývající argumenty zásobníku jsou obvykle umístěny.

## <a name="return-values"></a>Vrácené hodnoty

Celočíselné hodnoty jsou vraceny v x0.

Hodnoty s plovoucí desetinnou čárkou jsou v případě potřeby vráceny v S0, d0 nebo v0.

Hodnoty HFA a HVA se v případě potřeby vrátí v S0-S3, d0-D3 nebo v0-v3.

Typy vrácené hodnotou jsou zpracovávány různě v závislosti na tom, zda mají určité vlastnosti. Typy, které mají všechny tyto vlastnosti,

- jsou *agregovány* podle standardní definice c++ 14, to znamená, že nemají žádné uživatelem zadané konstruktory, žádné soukromé nebo chráněné nestatické datové členy, žádné základní třídy ani žádné virtuální funkce a
- mají operátor přiřazení triviálního kopírování a
- mají triviální destruktor,

použijte následující návratový styl:

- V x0 jsou vraceny typy menší nebo rovny 8 bajtů.
- Typy menší nebo rovny 16 bajtů jsou vraceny v x0 a x1 s x0, které obsahují nižší pořadí 8 bajtů.
- Pro typy větší než 16 bajtů volající vyhradí blok paměti dostatečné velikosti a zarovnání pro uchování výsledku. Adresa bloku paměti musí být předána do funkce v x8 jako další argument. Volaný může změnit blok paměti výsledku v jakémkoli okamžiku během provádění podprocesu. Volaný není vyžadován k zachování hodnoty uložené v x8.

Všechny ostatní typy používají tuto konvenci:

- Volající musí vyhradit blok paměti dostatečné velikosti a zarovnání pro uložení výsledku. Adresa bloku paměti musí být předána jako další argument funkci v x0 nebo x1, pokud je předáno $this v x0. Volaný může změnit blok paměti výsledku v jakémkoli okamžiku během provádění podprocesu. Volaný vrátí adresu bloku paměti v x0.

## <a name="stack"></a>Rámec

Za běhu, které jsou uvedeny v ARM, zásobník musí zůstat zarovnaný po dobu 16 bajtů. AArch64 obsahuje funkci hardwaru, která generuje chyby zarovnání zásobníku pokaždé, když se nerovná 16 bajtů, a v případě, že je provedeno navýšení nebo uložení v poměru SP. Systém Windows běží vždy, když je tato funkce povolená.

Funkce, které přidělují 4k nebo většímu množství zásobníku, musí zajistit, aby se všechny stránky před poslední stránkou dotýkaly v daném pořadí. Tato akce zajistí, že žádný kód nemůže přesměrovat na stránku Guard, kterou systém Windows používá k rozšíření zásobníku. Dodávání se obvykle provádí pomocí pomocné rutiny `__chkstk`, která má vlastní konvenci volání, která předá celkové přidělení zásobníku dělené 16 v X15.

## <a name="red-zone"></a>Červená zóna

16bitová oblast, která je bezprostředně pod aktuálním ukazatelem zásobníku, je vyhrazena pro použití v rámci analýz a scénářů dynamické opravy. Tato oblast umožňuje vložit pečlivě generovaný kód, který ukládá dva Registry na [SP, #-16] a dočasně je používá pro libovolný účel. Jádro systému Windows zaručuje, že tyto 16 bajtů nebudou přepsány, pokud dojde k výjimce nebo přerušení v režimu uživatele i režimu jádra.

## <a name="kernel-stack"></a>Zásobník jádra

Výchozí zásobník režimu jádra ve Windows je šest stránek (24k). Věnujte mimořádnou pozornost funkcím s velkými vyrovnávacími paměťmi zásobníku v režimu jádra. Chybná přerušení by mohla přijít s malým omezením a vytvořit nouzovou kontrolu chyb v zásobníku.

## <a name="stack-walking"></a>Procházení zásobníku

Kód v rámci Windows je kompilován s povolenými ukazateli snímků ([parametr/Oy-](reference/oy-frame-pointer-omission.md)), aby bylo možné rychlé procházení zásobníku. Obecně platí, že x29 (FP) odkazuje na další odkaz v řetězci, což je dvojice {FP, LR}, která označuje ukazatel na předchozí snímek v zásobníku a návratovou adresu. Kód třetí strany doporučujeme povolit i ukazatele na rámec, aby bylo možné zlepšit profilování a trasování.

## <a name="exception-unwinding"></a>Vrácení výjimky zpět

Odvíjení během zpracování výjimek je prostřednictvím použití unwind kódů k diskrok. Unwind kódy jsou posloupnosti bajtů uložených v oddílu. xdata spustitelného souboru. Popisují operaci prologu a epilogu abstraktním způsobem tak, aby se účinky prologu funkce mohly vrátit zpět v přípravě pro zálohování do rámce zásobníku volajícího. Další informace o unwind kódy naleznete v tématu [ARM64ing Exception rebavování](arm64-exception-handling.md).

EABI ARM také určuje model unwind pro výjimku, který používá unwind kódy. Uvedená specifikace však není dostatečná pro odvíjení v systému Windows, která musí zpracovávat případy, kdy je počítač uprostřed funkce prologu nebo epilogu.

Kód, který je dynamicky generován, by měl být popsán s dynamickými tabulkami funkcí prostřednictvím `RtlAddFunctionTable` a přidružených funkcí, aby generovaný kód mohl být součástí zpracování výjimek.

## <a name="cycle-counter"></a>Čítač cyklů

Všechny procesory ARMv8 jsou vyžadovány pro podporu registru čítače cyklu, což je 64 registrů, které systém Windows nakonfiguruje tak, aby byl čitelný na jakékoli úrovni výjimky, včetně uživatelského režimu. Lze k němu přistupovat prostřednictvím zvláštního PMCCNTR_EL0 registraci, pomocí operačního systému MSR v kódu sestavení nebo `_ReadStatusReg` vnitřní v C/C++ Code.

Čítač cyklu je tady skutečný počítadlo, ne nástěnné hodiny. Frekvence počítání se bude lišit podle frekvence procesoru. Pokud se domníváte, že je nutné znát frekvenci počítadla cyklu, neměli byste používat čítač cyklu. Místo toho je třeba změřit čas hodin, pro který byste měli použít `QueryPerformanceCounter`.

## <a name="see-also"></a>Viz také:

[Běžné problémy s migrací ARM v prostředí Visual C++](common-visual-cpp-arm-migration-issues.md)<br/>
[Zpracování výjimek ARM64](arm64-exception-handling.md)
