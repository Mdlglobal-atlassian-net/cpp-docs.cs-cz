---
title: Historie změn Visual C++ 2003–2015
ms.date: 10/21/2019
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: b7a18354257333bb71fff6aedb3cf623c47c2d5c
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821802"
---
# <a name="visual-c-change-history-2003---2015"></a>Historie změn Visual C++ 2003–2015

Tento článek popisuje všechny zásadní změny ze sady Visual Studio 2015, které se vrátí do sady Visual Studio 2003 a v tomto článku "nové chování" nebo "teď" odkazují na Visual Studio 2015 a novější. Pojem "staré chování" a "před" odkazují na Visual Studio 2013 a starší verze.

Informace o nejnovější verzi sady Visual Studio naleznete v tématu [co je nového pro vizuál C++ v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) a [vylepšení shody v aplikaci C++ Visual Studio](../overview/cpp-conformance-improvements.md).

> [!NOTE]
> Mezi Visual Studio 2015 a Visual Studio 2017 neexistují žádné binární změny.

Při upgradu na novou verzi sady Visual Studio může dojít k chybám kompilace a/nebo za běhu v kódu, který byl dříve kompilován a spuštěn správně. Změny v nové verzi, které způsobují takové problémy, se označují jako zásadní *změny*a obvykle jsou vyžadovány změnami ve standardním C++ jazyku, signaturách funkcí nebo rozložení objektů v paměti.

Aby nedocházelo k chybám za běhu, které je obtížné rozpoznat a diagnostikovat, doporučujeme, abyste nikdy nepoužili staticky odkaz na binární soubory kompilovány pomocí jiné verze kompilátoru. Když upgradujete projekt EXE nebo DLL, nezapomeňte také provést upgrade knihoven, na které odkazuje. Neprovádějte typy CRT (C Runtime) C++ nebo standardní knihovnaC++ (standardní knihovna) mezi binárními soubory, včetně knihoven DLL, kompilovány pomocí různých verzí kompilátoru. Další informace najdete v tématu [možné chyby při předávání objektů CRT napříč hranicemi knihoven DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Nikdy byste neměli psát kód, který závisí na konkrétním rozložení objektu, který není rozhraním COM nebo objektem POD. Pokud takový kód napíšete, musíte zajistit, aby po upgradu fungoval. Další informace najdete v tématu [přenositelnost na hranicích ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Navíc průběžná vylepšení shody kompilátoru mohou někdy změnit způsob, jakým kompilátor rozumí vašemu existujícímu zdrojovému kódu. Například můžete najít nové nebo jiné chyby během sestavení nebo dokonce i rozdíly v kódu, které dříve vytvořili a zdály se pracovat správně. I když tato vylepšení nejsou zásadními změnami, jako jsou popsané v tomto dokumentu, možná budete muset provést změny ve zdrojovém kódu pro vyřešení těchto problémů:

- [Přerušující se změny knihovny C runtime (CRT)](#BK_CRT)

- [Nenejnovější změny standardní C++ a C++ standardní knihovny](#BK_STL)

- [Přerušující změny MFC a ATL](#BK_MFC)

- [Concurrency Runtime přerušující změny](#BK_ConcRT)

## <a name="VC_2015"></a>Změny shody sady Visual Studio 2015

###  <a name="BK_CRT"></a>Běhová knihovna jazyka C (CRT)

#### <a name="general-changes"></a>Obecné změny

- **Refaktorované binární soubory**

   Knihovna CRT byla refaktorovaná do dvou různých binárních souborů: Universal CRT (ucrtbase), který obsahuje většinu standardních funkcí a knihovnu runtime VC (vcruntime). Knihovna vcruntime obsahuje funkce související s kompilátorem, jako je zpracování výjimek, a vnitřní objekty. Pokud používáte výchozí nastavení projektu, pak tato změna nemá vliv na to, že linker bude automaticky používat nové výchozí knihovny. Pokud jste nastavili vlastnost **linkeru** projektu **Ignorovat všechny výchozí knihovny** na **hodnotu Ano** nebo na příkazovém řádku používáte možnost linker `/NODEFAULTLIB`, je nutné aktualizovat seznam knihoven (ve vlastnosti **Další závislosti** ) tak, aby zahrnovaly nové, refaktoringované knihovny. Nahraďte starou knihovnu CRT (Libcmt. lib, LIBCMTD. lib, Msvcrt. lib, msvcrtd. lib) ekvivalentními refaktoring knihovny. Pro každou ze dvou předaných knihoven existují statické verze (. lib) a dynamické (. dll) a verze (bez přípony) a ladicí verze (s příponou "d"). Dynamické verze obsahují knihovnu importu, se kterou propojíte. Dvě refaktorované knihovny jsou Universal CRT, konkrétně ucrtbase. dll nebo ucrtbase. lib, ucrtbased. dll nebo ucrtbased. lib a knihovny runtime VC, libvcruntime. lib, vcruntime*Version*. dll, libvcruntimed. lib a vcruntimed*Version*. dll. *Verze* v aplikaci visual Studio 2015 a visual Studio 2017 je 140. Viz [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

#### <a name="localeh"></a>\<locale. h >

- **localeconv**

   Funkce [localeconv](../c-runtime-library/reference/localeconv.md) deklarovaná v locale. h teď funguje správně i v případě, že je povoleno [národní prostředí pro vlákno](../parallel/multithreading-and-locales.md) . V předchozích verzích knihovny vrátila Tato funkce data `lconv` pro globální národní prostředí, nikoli národní prostředí vlákna.

   Pokud používáte národní prostředí pro vlákno, měli byste kontrolovat použití `localeconv`. Pokud váš kód předpokládá, že vracená data `lconv` jsou pro globální národní prostředí, měli byste je opravit.

#### <a name="mathh"></a>\<Math. h >

- **C++přetížení funkcí matematické knihovny**

   V předchozích verzích \<Math. h > definovali některé, ale ne všechny, z C++ přetížení pro funkce matematické knihovny. Zbytek přetížení byl v hlavičce \<cmath >. Kód, který je zahrnutý pouze \<Math. h > by mohl mít problémy s řešením přetížení funkce. C++ Přetížení se teď odebrala z \<Math. h > a najdete je jenom v \<cmath >.

   Chcete-li vyřešit chyby, zahrňte \<cmath > a získejte deklarace funkcí, které byly odebrány z \<Math. h >. Tyto funkce byly přesunuty:

  - `double abs(double)` a `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - `float` a `long double` verze funkcí s plovoucí desetinnou čárkou `acos`, `acosh`, `asin`, `asinh`, `atan`, `atanh`, `atan2`, `cbrt`, `ceil`, `copysign`, `cos`, `cosh`, `erf`, `erfc`, `exp`, `exp2``expm1``fabs``fdim``floor``fma``fmax``fmin``fmod``frexp``hypot`, `ldexp`, `lgamma`, `llrint`, `llround`, `log`, `log10`, `log1p`, `log2`, `lrint`, `lround`, `modf`, `nearbyint`, `nextafter`, `nexttoward`, `remainder`, `remquo`, `rint`, `round``scalbln``scalbn``sin`

  Pokud máte kód, který používá `abs` s typem s plovoucí desetinnou čárkou, který obsahuje pouze hlavičku \<Math. h >, verze s plovoucí desetinnou čárkou již nebudou k dispozici. Volání nyní překládá na `abs(int)`, a to i v argumentu s plovoucí desetinnou čárkou, což způsobí chybu:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Oprava tohoto upozornění je nahrazení volání `abs` s použitím verze `abs`s plovoucí desetinnou čárkou, jako je například `fabs` pro dvojitý argument nebo `fabsf` pro argument typu float, nebo zahrnutí hlavičky \<cmath > a pokračování v používání `abs`.

- **Shoda s plovoucí desetinnou čárkou**

   Bylo provedeno mnoho změn v knihovně Math pro zlepšení dodržování specifikace IEEE-754 a přílohy F specifikací C11 s ohledem na vstupy zvláštních případů, jako je hodnoty NaN a nekonečno. Například tiché vstupy NaN, které byly často zpracovány jako chyby v předchozích verzích knihovny, již nejsou považovány za chyby. Viz standard [IEEE 754](https://standards.ieee.org/standard/754-2008.html) a Příloha F [standardu C11](http://www.iso-9899.info/wiki/The_Standard).

   Tyto změny nezpůsobí chyby při kompilaci, ale mohou způsobit, že se programy chovají jinak a správně podle standardu.

- **FLT_ROUNDS**

   V Visual Studio 2013 se makro FLT_ROUNDS rozšířilo na konstantní výraz, který byl nesprávný, protože režim zaokrouhlení lze konfigurovat za běhu, například voláním fesetround. Makro FLT_ROUNDS je teď dynamické a správně odráží aktuální režim zaokrouhlení.

#### <a name="new-and-newh"></a>\<nové > a \<New. h >

- **nové a odstranit**

   V předchozích verzích knihovny byly vyexportovány funkce operátora New a DELETE definované implementací z knihovny DLL běhové knihovny (například msvcr120. dll). Tyto funkce operátora jsou nyní vždy staticky propojeny do vašich binárních souborů i při použití knihoven DLL knihoven modulu runtime.

   Nejedná se o zásadní změnu pro nativní nebo smíšený kód (`/clr`), ale pro kód kompilovaný jako [/clr: Pure](../build/reference/clr-common-language-runtime-compilation.md)může tato změna způsobit selhání kompilace kódu. Pokud kompilujete kód jako `/clr:pure`, může být nutné přidat `#include <new>` nebo `#include <new.h>` pro řešení chyb sestavení z důvodu této změny. Možnost`/clr:pure` je zastaralá v aplikaci Visual Studio 2015 a nepodporovaná v aplikaci Visual Studio 2017. Kód, který musí být "Pure", by měl být na C#port.

#### <a name="processh"></a>\<Process. h >

- **_beginthread a _beginthreadex**

   Funkce [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) a [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) nyní obsahují odkaz na modul, ve kterém je procedura vlákna definována pro dobu trvání vlákna. To pomáhá zajistit, že moduly nebudou uvolněny, dokud vlákno nebude dokončeno.

#### <a name="stdargh"></a>\<stdarg.h>

- **va_start a odkazové typy**

   Při kompilování C++ kódu [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) nyní ověřuje v době kompilace, že argument předaný do něj není odkazový typ. Argumenty typu odkazu jsou zakázané C++ standardem.

#### <a name="stdio_and_conio"></a>\<stdio. h > a \<CONIO. h >

- **Rodina funkcí printf a scanf je teď definovaná jako inline.**

   Definice všech funkcí `printf` a `scanf` byly přesunuty do \<stdio. h >, \<CONIO. h > a dalších hlaviček CRT. Tato zásadní změna vede k chybě linkeru (LINKERŮ LNK2019, nerozpoznaný externí symbol) pro všechny programy, které tyto funkce deklarovaly místně bez zahrnutí odpovídajících hlaviček CRT. Pokud je to možné, měli byste kód aktualizovat tak, aby zahrnoval hlavičky CRT (tj. přidat `#include <stdio.h>`) a vložené funkce, ale pokud nechcete upravovat kód pro zahrnutí těchto hlavičkových souborů, alternativním řešením je přidat další knihovnu do vstupu linkeru, legacy_stdio_definitions. lib.

   Chcete-li přidat tuto knihovnu do vstupu linkeru v integrovaném vývojovém prostředí, otevřete kontextovou nabídku uzlu projektu, zvolte možnost **vlastnosti**, poté v dialogovém okně **Vlastnosti projektu** zvolte možnost **linker**a upravte **vstup linkeru** tak, aby byly přidány `legacy_stdio_definitions.lib` do seznamu odděleného středníkem.

   Pokud projekt odkazuje na statické knihovny, které byly zkompilovány s vydáním sady Visual Studio starší než 2015, linker může hlásit nevyřešený externí symbol. Tyto chyby mohou odkazovat na interní definice pro `_iob`, `_iob_func`nebo související importy pro určité \<> funkcí ve formě\*_IMP_ . Společnost Microsoft doporučuje při upgradu projektu překompilovat všechny statické knihovny s nejnovější verzí C++ kompilátoru a knihoven. Pokud je knihovna knihovnou třetí strany, pro kterou není k dispozici zdroj, měli byste buď požádat o aktualizovaný binární soubor od třetí strany, nebo zapouzdřit použití této knihovny do samostatné knihovny DLL, která kompilujete pomocí starší verze kompilátoru a knihoven. .

    > [!WARNING]
    > Pokud propojujete s Windows SDK 8,1 nebo starším, můžete se setkat s těmito nevyřešenými chybami externích symbolů. V takovém případě byste tuto chybu měli vyřešit přidáním legacy_stdio_definitions. lib do vstupu linkeru, jak je popsáno výše.

   K řešení chyb nevyřešených symbolů můžete zkusit použít nástroj [DUMPBIN. exe](../build/reference/dumpbin-reference.md) k prohlédnutí symbolů definovaných v binárním souboru. Zkuste zobrazit symboly definované v knihovně pomocí následujícího příkazového řádku.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **Získá a _getws**

   Funkce [Get](../c-runtime-library/gets-getws.md) a [_getws](../c-runtime-library/gets-getws.md) byly odebrány. Funkce Get byla ze standardní knihovny jazyka C v C11 odebrána, protože ji nelze bezpečně použít. _Getws funkce byla rozšíření společnosti Microsoft, které bylo ekvivalentní k získání, ale pro velké řetězce. Jako alternativy k těmto funkcím zvažte použití [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md)a [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets a _cgetws**

   Byly odebrány funkce [_cgets](../c-runtime-library/cgets-cgetws.md) a [_cgetws](../c-runtime-library/cgets-cgetws.md) . Jako alternativy k těmto funkcím zvažte použití [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) a [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Formátování nekonečno a NaN**

   V předchozích verzích se nekonečny a hodnoty NaN naformátují pomocí sady ověřovacích řetězců specifických pro MSVC.

  - Nekonečno: 1. #INF

  - Tiché NaN: 1. #QNAN

  - Signalizace: 1. #SNAN

  - Nekonečný NaN: 1. #IND

  Některý z těchto formátů může být předponou a mohl by být zformátován mírně různě v závislosti na šířce a přesnosti pole (v některých případech se jedná o neobvyklé účinky, například `printf("%.2f\n", INFINITY)` by měl tisknout 1. #J, protože #INF "zaokrouhlit" na 2 číslice přesnost). C99 zavedl nové požadavky na to, jak mají být naformátovány nekonečny a hodnoty NaN. Implementace MSVC nyní splňuje tyto požadavky. Nové řetězce jsou následující:

  - Nekonečno: INF

  - Tiché NaN: NaN

  - Signalizace: NaN (Snan)

  - Nekonečná hodnota NaN: NaN (DIS-ajít)

  Jakékoli z nich může být předponou. Pokud se používá specifikátor formátu s velkými písmeny (% F namísto% F), pak se řetězce tisknou velkými písmeny (`INF` místo `inf`), jak je potřeba.

  Funkce [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) byly upraveny tak, aby se tyto nové řetězce analyzovaly, takže tyto řetězce se nyní budou cyklicky předávat `printf` a `scanf`.

- **Formátování a analýza plovoucí desetinné čárky**

   Byly zavedeny nové formátování a algoritmy pro analýzu plovoucí desetinné čárky, aby se zlepšila správnost. Tato změna má vliv na řady funkcí [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) a také na funkce jako [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Staré algoritmy formátování by vygenerovaly jenom omezený počet číslic a pak zbývající desetinná místa vyplní nula. Obvykle by generovaly řetězce, které by se převedly zpět na původní hodnotu s plovoucí desetinnou čárkou, ale nebyly Skvělé, pokud jste chtěli přesnou hodnotu (nebo nejbližší desítkovou reprezentaci). Nové algoritmy formátování generují tolik číslic, kolik je potřeba k reprezentaci hodnoty (nebo k vyplnění zadané přesnosti). Jako příklad zlepšení; Vezměte v úvahu výsledky při tisku velkých mocnin dvou:

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   Starý výstup:

    ```Output
    1208925819614629200000000
    ```

   Nový výstup:

    ```Output
    1208925819614629174706176
    ```

   Staré algoritmy analýzy by zvážily pouze až 17 platných číslic ze vstupního řetězce a zahodí zbytek číslic. Tento přístup je dostačující pro vygenerování přibližného aproximace hodnoty reprezentované řetězcem a výsledek je obvykle velmi blízko pro správný zaoblený výsledek. Nová implementace považuje všechny aktuální číslice a vytvoří správně zaoblený výsledek pro všechny vstupy (až 768 číslic po délce). Kromě toho tyto funkce nyní respektují režim zaokrouhlení (ovladatelné přes fesetround).  To je potenciálně pravděpodobné změny chování, protože tyto funkce mohou mít za následek výstup různých výsledků. Nové výsledky jsou vždy častěji správné než staré výsledky.

- **Šestnáctková a nekonečná nebo NaN analýza plovoucí desetinné čárky**

   Algoritmy analýzy plovoucí desetinné čárky nyní analyzují šestnáctkové řetězce s plovoucí desetinnou čárkou (například ty generované specifikátory formátu% a a% A printf) a všechny nekonečno a NaN řetězce, které jsou vygenerovány funkcemi `printf`, jak je popsáno výše.

- **% A a% nulového odsazení**

   Specifikátory formátu% a a% formátuje číslo s plovoucí desetinnou čárkou jako hexadecimální mantisu a binární exponent. V předchozích verzích `printf` funkce nesprávně odblokované řetězce. `printf("%07.0a\n", 1.0)` by například měl tisknout 00x1p + 0, kde by měl tisknout 0x01p + 0. Tato chyba byla opravena.

- **% A a% – přesnost**

   Výchozí přesnost specifikátorů formátu% A a% byla 6 v předchozích verzích knihovny. Výchozí přesnost je nyní 13 pro shodu s standardem C.

   Toto je změna chování za běhu ve výstupu jakékoli funkce, která používá formátovací řetězec s% A nebo% a. Ve starém chování může být výstup pomocí% specifikátoru "1.1 A2B3Cp + 111". Nyní je výstup pro stejnou hodnotu "1.1 A2B3C4D5E6F7p + 111". Chcete-li získat staré chování, můžete zadat přesnost, například%. 6A. Viz [specifikace přesnosti](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **Specifikátor% F**

   Specifikátor formátu nebo převodu% F se teď podporuje. Je funkčně ekvivalentní specifikátoru formátu% f s tím rozdílem, že nekonečná a hodnoty NaN jsou formátována pomocí velkých písmen.

   V předchozích verzích byla implementace použita k analýze F a N jako modifikátorů délky. Toto chování bylo vráceno zpět do stáří segmentů segmentů adres: Tyto modifikátory délky byly použity k označení daleko a blízko ukazatelů v uvedeném pořadí, jako v% FP nebo% NS. Toto chování bylo odebráno. Pokud dojde k% F, je nyní zpracován jako specifikátor formátu% F; je-li zjištěno% N, je nyní zpracován jako neplatný parametr.

- **Formátování exponentu**

   Specifikátory formátu% e a% E naformátují číslo s plovoucí desetinnou čárkou jako Desítková mantisa a exponent. Specifikátory formátu% g a% G také formátuje čísla v tomto formuláři v některých případech. V předchozích verzích by CRT vždy generovala řetězce se třemi číslicemi exponentů. `printf("%e\n", 1.0)` například 1.000000 tisk e + 000, což nebylo správné. Jazyk C vyžaduje, aby se exponent reprezentovat jenom s jedním nebo dvěma číslicemi, takže se vytisknou jenom dvě číslice.

   V aplikaci Visual Studio 2005 byl přidán globální přepínač pro shodu: [_set_output_format](../c-runtime-library/set-output-format.md). Program by mohl zavolat tuto funkci s argumentem _TWO_DIGIT_EXPONENT, aby bylo možné povolit vyhovující vytisknutí exponentu. Výchozí chování bylo změněno do režimu tisku exponentu vyhovujícího standardům.

- **Ověřování řetězce formátu**

   V předchozích verzích funkce `printf` a `scanf` tiše přijímají mnoho neplatných formátovacích řetězců, někdy s neobvyklými účinky. Například% hlhlhld by měl být považován za% d. Všechny neplatné řetězce formátu se teď považují za neplatné parametry.

- **ověřování řetězců v režimu fopen**

   V předchozích verzích `fopen` rodina funkcí tiše přijala některé neplatné řetězce režimu, jako je například `r+b+`. Nyní jsou zjištěny neplatné řetězce režimu a zpracovány jako neplatné parametry.

- **_O_U8TEXT režim**

   Funkce [_setmode](../c-runtime-library/reference/setmode.md) nyní správně hlásí režim pro datové proudy otevřené v režimu in_O_U8TEXT. V předchozích verzích knihovny by se takové datové proudy nahlásily jako otevřené v _O_WTEXT.

   Toto je zásadní změna, pokud váš kód interpretuje _O_WTEXT režim pro datové proudy, kde kódování je UTF-8. Pokud vaše aplikace nepodporuje UTF_8, zvažte přidání podpory pro toto stále běžné kódování.

- **snprintf a vsnprintf**

   Funkce [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) a [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) jsou nyní implementovány. Starší kód často poskytuje definice verze makra těchto funkcí, protože nebyly implementovány knihovnou CRT, ale již nejsou potřeba v novějších verzích. Pokud je [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) nebo [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) definováno jako makro před zahrnutím \<stdio. h >, kompilace nyní selhává s chybou, která indikuje, kde bylo makro definováno.

   Běžným řešením tohoto problému je odstranit jakékoliv deklarace `snprintf` nebo `vsnprintf` v uživatelském kódu.

- **tmpnam generuje použitelné názvy souborů.**

   V předchozích verzích funkce `tmpnam` a `tmpnam_s` vygenerovaly názvy souborů v kořenovém adresáři jednotky (například \sd3c.). Tyto funkce teď v dočasném adresáři generují použitelné cesty k názvům souborů.

- **Zapouzdření souborů**

   V předchozích verzích byl kompletní typ souboru definován veřejně v \<stdio. h >, takže bylo možné, aby uživatelský kód dosáhl do souboru a upravil jeho vnitřní části. Knihovna byla změněna tak, aby se skryly podrobnosti implementace. V rámci této změny soubor, jak je definováno v \<stdio. h > je nyní neprůhledný typ a jeho členové jsou nepřístupní mimo samotný CRT.

- **_outp a _inp**

   Funkce [_outp](../c-runtime-library/outp-outpw-outpd.md), [_outpw](../c-runtime-library/outp-outpw-outpd.md), [_outpd](../c-runtime-library/outp-outpw-outpd.md), [_inp](../c-runtime-library/inp-inpw-inpd.md), [_inpw](../c-runtime-library/inp-inpw-inpd.md)a [_inpd](../c-runtime-library/inp-inpw-inpd.md) byly odebrány.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<Stdlib. h >, \<\. h > a \<sys/stat. h >

- **strtof a wcstof**

   Funkce `strtof` a `wcstof` se nepovedlo nastavit `errno` na ERANGE, když se hodnota nedá reprezentovat jako float. Tato chyba byla specifická pro tyto dvě funkce; funkce `strtod`, `wcstod`, `strtold`a `wcstold` nebyly nijak ovlivněny. Tento problém byl opraven a je zásadní změnou v modulu runtime.

- **Funkce zarovnaného přidělení**

   V předchozích verzích funkce zarovnané alokace (`_aligned_malloc`, `_aligned_offset_malloc`atd.) by v tichosti přijímaly požadavky na blok s zarovnáním 0. Požadované zarovnání musí být mocninou hodnoty 2, která nemá hodnotu true nula. Požadované zarovnání 0 se teď považuje za neplatný parametr. Tento problém byl opraven a je zásadní změnou v modulu runtime.

- **Funkce haldy**

   Byly odebrány funkce `_heapadd`, `_heapset`a `_heapused`. Tyto funkce nebyly funkční, protože CRT byla aktualizována, aby používala haldu systému Windows.

- **smallheap**

   Možnost odkazu `smallheap` byla odebrána. Viz [Možnosti odkazů](../c-runtime-library/link-options.md).

#### <a name="stringh"></a>\<String. h >

- **wcstok**

   Signatura funkce `wcstok` se změnila tak, aby odpovídala hodnotám, které vyžaduje standard jazyka C. V předchozích verzích knihovny byl podpis této funkce:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Používá interní kontext pro vlákno ke sledování stavu napříč voláními, jak je to pro `strtok`provedeno. Funkce má nyní signaturu `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)`a vyžaduje volajícímu předat kontext jako třetí argument funkce.

   Byla přidána nová funkce `_wcstok` se starým podpisem pro usnadnění přenosu. Při kompilování C++ kódu existuje také vložené přetížení `wcstok`, které má starý podpis. Toto přetížení je deklarováno jako zastaralé. V kódu jazyka C můžete define_CRT_NON_CONFORMING_WCSTOK, že `_wcstok` použít místo `wcstok`.

#### <a name="timeh"></a>\<time.h>

- **clock**

   V předchozích verzích byla funkce [Clock](../c-runtime-library/reference/clock.md) implementována pomocí rozhraní API systému Windows [GetSystemTimeAsFileTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime). V této implementaci byla funkce hodin citlivá na systémový čas, a proto nebyla nutně monotónní. Funkce Clock se znovu implementovala z podmínek [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) a teď je monotónní.

- **fstat a _utime**

   V předchozích verzích funkce [_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)a [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) zpracovávají letní čas nesprávně. Před Visual Studio 2013 všechny tyto funkce nesprávně upravily standardní časové časy, jako kdyby byly v letním čase.

   V Visual Studio 2013 byl problém vyřešen v **_stat** rodině funkcí, ale podobné problémy v **fstat** **_utime** a rodinám funkcí nebyly opraveny. Tato částečná oprava vedla k problémům z důvodu nekonzistence mezi funkcemi. **Fstat** a **_utime** řady funkcí byly nyní opraveny, takže všechny tyto funkce nyní zpracovávají letní čas správně a konzistentně.

- **asctime**

   V předchozích verzích [asctime](../c-runtime-library/reference/asctime-wasctime.md) funkce odvolala jednociferné číslo dnů s úvodní nulou, například: `Fri Jun 06 08:00:00 2014`. Specifikace vyžaduje, aby tyto dny byly doplněny na počáteční místo, jak je uvedeno v `Fri Jun  6 08:00:00 2014`. Tento problém byl opraven.

- **strftime a wcsftime**

   Funkce `strftime` a `wcsftime` nyní podporují specifikátory formátu% C,% D,% e,% F,% g,% G,% h,% n,% r,% R,% t,% T,% u a% V. Kromě toho modifikátory E a O jsou analyzovány, ale ignorovány.

   Specifikátor formátu% c je zadán jako označení "vhodné reprezentace data a času" pro aktuální národní prostředí. V národním prostředí jazyka C musí být tato reprezentace stejná jako `%a %b %e %T %Y`, což je stejný tvar, který je vytvořen pomocí `asctime`. V předchozích verzích specifikátor formátu% c nesprávně formátované časy pomocí `MM/DD/YY HH:MM:SS` reprezentace. Tento problém byl opraven.

- **timespec a TIME_UTC**

   Hlavička \<Time. h > nyní definuje typ `timespec` a `timespec_get` funkce ze standardu C11. Kromě toho je nyní definováno makro TIME_UTC pro použití s funkcí `timespec_get`. Tato aktualizace je zásadní změnou kódu, který má konfliktní definici pro některý z těchto identifikátorů.

- **CLOCKS_PER_SEC**

   CLOCKS_PER_SEC makro se nyní rozbalí na celé číslo typu `clock_t`, jak to vyžaduje jazyk C.

####  <a name="BK_STL"></a>C++ Standardní knihovna

Pokud byte chtěli povolit nové optimalizace a kontroly ladění, implementace standardní knihovny C++ záměrně neumožňuje binární kompatibilitu mezi verzemi. Proto při použití standardní knihovny C++ nelze objektové soubory a statické knihovny, které jsou kompilovány pomocí různých verzí, směšovat v jednom binárním souboru (EXE nebo DLL) a objekty standardní knihovny C++ nelze předávat mezi binárními soubory, které jsou kompilovány pomocí různých verzí. Takovéto směšování objektů vyvolává chyby linkeru týkající se neshod _MSC_VER. (_MSC_VER je makro, které obsahuje hlavní verzi kompilátoru, například 1800 pro Visual Studio 2013.) Tato kontrola nedokáže detekovat kombinování knihoven DLL a nemůže detekovat kombinování, které zahrnuje Visual Studio 2008 nebo starší.

- **C++Soubory zahrnuté do standardní knihovny**

   V hlavičkách C++ standardní knihovny byly provedeny některé změny ve struktuře include. C++Standardní hlavičky knihovny můžou zahrnovat jiné neurčené způsoby. Obecně byste měli napsat kód tak, aby pečlivě zahrnoval všechny hlavičky, které potřebuje podle C++ standardu, a nespoléhá se na to, které C++ standardní hlavičky knihovny obsahují další C++ standardní hlavičky knihovny. Díky tomu je kód přenosný napříč různými verzemi a platformami. Alespoň dvě změny hlaviček v aplikaci Visual Studio 2015 ovlivňují uživatelský kód. První \<řetězec > již nezahrnuje \<iterátor >. Za druhé \<řazené kolekce členů > nyní deklaruje `std::array` bez zahrnutí všech \<pole >, který může přerušit kód prostřednictvím následující kombinace konstrukcí kódu: váš kód má proměnnou s názvem Array a máte pomocí oboru názvů std; použitou direktivu C++ Standard, a zahrnete standardní hlavičku knihovny (například \<funkční >), která obsahuje \<řazené kolekce členů >, který nyní deklaruje `std::array`.

- **steady_clock**

   \<Chrono > implementace [steady_clock](../standard-library/steady-clock-struct.md) se změnila tak, aby splňovala C++ standardní požadavky pro Steadiness a monotonicity. `steady_clock` je nyní založen na [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) a `high_resolution_clock` je nyní definicí pro `steady_clock`. V důsledku toho je v sadě Visual Studio `steady_clock::time_point` nyní definice typu pro `chrono::time_point<steady_clock>`; to však není nutně případ pro jiné implementace.

- **přidělování a const**

   Pro přijetí argumentů const na obou stranách teď vyžadujeme porovnání rovnosti a nerovnosti přidělování. Pokud vaše přidělování definují tyto operátory jako toto,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   pak byste je měli aktualizovat a deklarovat jako členy const:

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **elementy const**

   C++ Standard má vždycky zakázané kontejnery elementů const (například Vector\<const t > nebo nastavte\<const t >). Visual Studio 2013 a dříve přijaly takové kontejnery. V aktuální verzi nelze tyto kontejnery zkompilovat.

- **std:: přidělování::d eallocate**

   V Visual Studio 2013 a dřívějších `std::allocator::deallocate(p, n)` ignorován argument předaný pro *n*.  C++ Standard vždy vyžadoval, aby hodnota *n* musela být rovna hodnotě předané jako první argument vyvolání `allocate`, která vrátila hodnotu *p*. V aktuální verzi je však zkontrolována hodnota *n* . Kód, který předává argumenty pro *n* , které se liší od toho, co vyžaduje standard, může za běhu selhat.

- **hash_map a hash_set**

   Soubory hlaviček, které nejsou standardní \<hash_map > a \<hash_set > jsou v rámci sady Visual Studio 2015 zastaralé a v budoucí verzi budou odebrány. Místo toho použijte \<unordered_map > a \<unordered_set.

- **komparátorů a – operátor ()**

   Asociativní kontejnery (\<mapa > Rodina) nyní vyžadují, aby jejich komparátorů měly operátory volání funkce, které lze volat jako const. Následující kód v deklaraci třídy komparátor nyní nemůže kompilovat:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Chcete-li tuto chybu vyřešit, změňte deklaraci funkce na:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **vlastnosti typu**

   Odebraly se staré názvy vlastností typu z dřívější verze C++ konceptu Standard. Tyto změny byly změněny v C++ 11 a byly aktualizovány na hodnoty C++ 11 v aplikaci Visual Studio 2015. V následující tabulce jsou uvedeny staré a nové názvy.

   |Starý název|Nový název|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **spustit:: Any a Launch:: Sync – zásady**

   Nestandardní `launch::any` a zásady `launch::sync` se odebraly. Místo toho použijte pro `launch::any``launch:async | launch:deferred`. Pro `launch::sync`použijte `launch::deferred`. Viz [Spustit výčet](../standard-library/future-enums.md#launch).

####  <a name="BK_MFC"></a>MFC a ATL

- **Knihovna MFC (Microsoft Foundation Classes)**

   už není zahrnutý v typické instalaci Visual studia z důvodu jeho velké velikosti. Chcete-li nainstalovat knihovnu MFC, zvolte možnost **vlastní** instalace v instalačním programu sady Visual Studio 2015. Pokud již máte nainstalovánu aplikaci Visual Studio 2015, můžete znovu nainstalovat knihovnu MFC spuštěním instalačního programu sady **Visual Studio** . Zvolte možnost **vlastní** instalace a pak zvolte položku **Microsoft Foundation Classes**. Instalaci sady **Visual Studio** můžete spustit z ovládacích **panelů** ovládací panely **programy a funkce**nebo z instalačního média nástroje.

   Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.

####  <a name="BK_ConcRT"></a>Concurrency Runtime

- **Dej makro z Windows. h v konfliktu s concurrency:: Context:: yield**

   Concurrency Runtime dřív používal `#undef` k zrušení definice makra yield, aby nedocházelo ke konfliktům mezi makrem yield definovaným v systému Windows. h h a funkcí `concurrency::Context::Yield`. Tato `#undef` byla odebrána a bylo přidáno nové Nekolidující ekvivalentní volání rozhraní API [:: Context:: YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) . Chcete-li vyřešit konflikty s výsledkem, můžete buď aktualizovat kód pro volání funkce `YieldExecution`, nebo obklopit název `Yield` funkce závorkami na webech volání, jako v následujícím příkladu:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Vylepšení shody kompilátoru v aplikaci Visual Studio 2015

Při upgradu kódu z předchozích verzí může dojít také k chybám kompilátoru, které jsou způsobeny vylepšeními shody provedenými v aplikaci Visual Studio 2015. Tato vylepšení neruší binární kompatibilitu z dřívějších verzí sady Visual Studio, ale mohou způsobit chyby kompilátoru, kde žádná nebyla vygenerována dříve. Další informace najdete v tématu [ C++ co je nového 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

V rámci sady Visual Studio 2015 může někdy změna způsobu, jakým je v souladu s kompilátorem, někdy změnit způsob, jakým kompilátor rozumí vašemu existujícímu zdrojovému kódu. V důsledku toho může dojít k výskytu nových nebo různých chyb během sestavení nebo dokonce i rozdílů v kódu, které dříve sestavily a zdály se pracovat správně.

Naštěstí tyto rozdíly mají malý nebo žádný vliv na většinu vašeho zdrojového kódu. V případě, že je pro vyřešení těchto rozdílů nutný zdrojový kód nebo jiné změny, jsou opravy velmi malé a musí být přímo předávány. Zahrnuli jsme spoustu příkladů dříve přijatelného zdrojového kódu, který může být potřeba změnit *(před)* , a opravy, které je třeba opravit *(po)* .

I když tyto rozdíly mohou ovlivnit váš zdrojový kód nebo jiné artefakty sestavení, nemají vliv na binární kompatibilitu mezi aktualizacemi verzí sady Visual Studio. Zásadní *Změna* je mnohem závažná a může mít vliv na binární kompatibilitu, ale u těchto typů binárních rozdílů se vyskytuje pouze mezi hlavními verzemi sady Visual Studio, například mezi Visual Studio 2013 a Visual Studio 2015. Informace o nejnovějších změnách, ke kterým došlo mezi Visual Studio 2013 a Visual Studio 2015, najdete v článku [změny shody sady Visual studio 2015](#VC_2015).

- [Vylepšení shody v aplikaci Visual Studio 2015](#VS_RTM)

- [Vylepšení shody v aktualizaci Update 1](#VS_Update1)

- [Vylepšení shody v aktualizaci Update 2](#VS_Update2)

- [Vylepšení shody v aktualizaci Update 3](#VS_Update3)

###  <a name="VS_RTM"></a>Vylepšení shody v aplikaci Visual Studio 2015

- /Zc: forScope-Option

   Možnost kompilátoru `/Zc:forScope-` je zastaralá a v budoucí verzi se odebere.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Obvykle se tato možnost použila, aby povolovala nestandardní kód, který používá proměnné smyčky za bodem, kde, podle standardu, by měl být mimo rozsah. Bylo nutné pouze při kompilaci s možností `/Za`, od bez `/Za`, použití proměnné for Loop po konci smyčky je vždy povoleno. Pokud nezáleží na dodržování standardů (například pokud váš kód není určen pro přenos do jiných kompilátorů), můžete vypnout možnost `/Za` (nebo nastavit vlastnost **Zakázat jazykové rozšíření** na hodnotu **ne**). Pokud se zajímáte o zápis přenosného kódu kompatibilního s normami, měli byste přepsat kód tak, aby odpovídal standardu přesunutím deklarace těchto proměnných do bodu mimo smyčku.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg` – možnost kompilátoru

   Možnost kompilátoru `/Zg` (generovat prototypy funkcí) už není dostupná. Tato možnost kompilátoru byla dřív zastaralá.

- Pomocí příkazu/CLI z příkazového řádku s C++MSTest. exe už nemůžete spouštět testy jednotek s/CLI. Místo toho použijte VSTest. Console. exe. Viz [Možnosti příkazového řádku VSTest. Console. exe](/visualstudio/test/vstest-console-options).

- **mutable – klíčové slovo**

   Specifikátor třídy **měnitelného** úložiště již není povolen v místech, kde byla dříve zkompilována bez chyby. Nyní kompilátor poskytuje chybu C2071 (neplatná třída úložiště). Podle standardu může být **proměnlivý** specifikátor použit pouze pro názvy datových členů třídy a nelze jej použít pro názvy deklarované jako const nebo static a nelze jej použít pro členy odkazu.

   Zvažte například následující kód:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Předchozí verze kompilátoru to přijaly, ale teď kompilátor poskytuje tuto chybu:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Chybu opravíte tak, že odeberete redundantní klíčové slovo **mutable** .

- **char_16_t a char32_t**

   Už nemůžete používat `char16_t` ani `char32_t` jako aliasy ve **typedef**, protože tyto typy se teď považují za předdefinované. Pro uživatele a autory knihovny bylo běžné definovat `char16_t` a `char32_t` jako aliasy `uint16_t` a `uint32_t`v uvedeném pořadí.

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   Chcete-li aktualizovat kód, odeberte deklarace **typedef** a přejmenujte všechny ostatní identifikátory, které s těmito názvy kolidují.

- **Parametry šablony bez typu**

   Určitý kód, který zahrnuje parametry šablony bez typu, je nyní správně zkontrolován na kompatibilitu typu při zadání explicitních argumentů šablony. Například následující kód byl zkompilován bez chyb v předchozích verzích sady Visual Studio.

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   Aktuální kompilátor správně poskytuje chybu, protože typ parametru šablony neodpovídá argumentu šablony (parametr je ukazatel na konstantní člen, ale funkce f není const):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Chcete-li vyřešit tuto chybu ve vašem kódu, ujistěte se, že typ argumentu šablony, který použijete, odpovídá deklarovanému typu parametru šablony.

- **__declspec(align)**

   Kompilátor už nepřijímá `__declspec(align)` na funkcích. Tento konstruktor se vždycky ignoruje, ale teď vytvoří chybu kompilátoru.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Chcete-li tento problém vyřešit, odeberte `__declspec(align)` z deklarace funkce. Vzhledem k tomu, že nedošlo k žádnému vlivu, odebrání nemění nic.

- **Zpracování výjimek**

   Zpracovávání výjimek je několik změn. Nejprve objekty výjimky musí být buď kopírovací, nebo pohyblivý. Následující kód byl zkompilován v Visual Studio 2013, ale není zkompilován v aplikaci Visual Studio 2015:

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Problémem je, že kopírovací konstruktor je privátní, takže objekt nelze zkopírovat, protože se stane v normálním průběhu zpracování výjimky. Totéž platí, pokud je kopírovací konstruktor deklarovaný jako **explicitní**.

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Chcete-li aktualizovat kód, ujistěte se, že kopírovací konstruktor pro objekt výjimky je **veřejný** a není označen jako **explicitní**.

   Zachycení výjimky podle hodnoty také vyžaduje zkopírování objektu výjimky. Následující kód byl zkompilován v Visual Studio 2013, ale není zkompilován v aplikaci Visual Studio 2015:

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   Tento problém můžete vyřešit tak, že změníte typ parametru pro **catch** na odkaz.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Řetězcové literály následované makry**

   Kompilátor teď podporuje uživatelsky definované literály. V důsledku toho jsou řetězcové literály následované makry bez použití mezer interpretovány jako uživatelsky definované literály, což může způsobit chyby nebo neočekávané výsledky. Například v předchozích kompilátorech byl následující kód úspěšně zkompilován:

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   Kompilátor interpretuje tento kód jako řetězcový literál "Hello" následovaný makrem, které je rozbaleno do "a", poté dva řetězcové literály byly zřetězeny do jednoho. V aplikaci Visual Studio 2015 Kompilátor interpretuje tuto sekvenci jako literál definovaný uživatelem, ale vzhledem k tomu, že není definována žádná vyhovující uživatelsky definovaná Literálová `_x` definovaná, obsahuje chybu.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi řetězcový literál a makro.

- **Sousedící řetězcové literály**

   Podobně jako v předchozím případě v důsledku souvisejících změn v analýze řetězců, sousedících řetězcových literálů (buď pro řetězce s velkým nebo úzkým znakem ") bez mezer byly interpretovány jako jeden zřetězený řetězec v C++předchozích verzích Visaul. V aplikaci Visual Studio 2015 je nyní nutné přidat prázdné znaky mezi dva řetězce. Například následující kód musí být změněn:

    ```cpp
    char * str = "abc""def";
    ```

   Chcete-li tento problém vyřešit, přidejte mezi tyto dva řetězce mezeru:

    ```cpp
    char * str = "abc" "def";
    ```

- **Umístění – nové a odstranit**

   Byl proveden pokus o změnu operátoru **Delete** , aby byl do souladu s c++ 14 standardem. Podrobnosti o změně standardů najdete v [ C++ podrobnostech o navracení velikosti](https://isocpp.org/files/papers/n3778.html). Změny přidají formu globálního operátoru **Delete** , který přijímá parametr velikosti. Zásadní změna znamená, že pokud jste předtím používali operátor **Delete** se stejnou signaturou (aby odpovídala **umístění New** operator), obdržíte chybu kompilátoru (C2956, ke které dojde v místě, kde se používá umístění New), protože to je pozice v kódu, kde se kompilátor pokusí identifikovat příslušný odpovídající operátor **Delete** .

   Funkce `void operator delete(void *, size_t)`a umístění operátoru **Delete** , který odpovídá **umístění New** Function `void * operator new(size_t, size_t)` v c++ 11. Při dealokaci velikosti C++ 14 je tato funkce odstranění nyní *běžnou funkcí zrušení přidělení* (globální operátor **Delete** ). Standardně se vyžaduje, aby při použití umístění nový vyhledala odpovídající funkci DELETE a vyhledala obvyklou funkci zrušení přidělení, program je nesprávně vytvořen.

   Předpokládejme například, že váš kód definuje **umístění nové** a **odstranění umístění**:

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   K tomuto problému dochází z důvodu shody v signaturách funkcí mezi uživatelem definovaným operátorem pro **odstranění umístění** a novým operátorem **odstranění** globální velikosti. Zvažte, zda můžete použít jiný typ než `size_t` pro všechny operátory **New** a **Delete** . Typ `size_t` **typedef** je závislý na kompilátoru; je to **definice** typu **unsigned int** v MSVC. Dobrým řešením je použít Výčtový typ, jako je například tento:

    ```cpp
    enum class my_type : size_t {};
    ```

   Pak změňte definici **umístění New** a **Delete** , aby se tento typ používal jako druhý argument místo `size_t`. Budete také muset aktualizovat volání do umístění New pro předání nového typu (například pomocí `static_cast<my_type>` pro převod z celočíselné hodnoty) a aktualizace definice **New** a **Delete** pro přetypování zpět na celočíselný typ. Pro tuto chybu nemusíte používat **výčet** . může fungovat i typ třídy s `size_t`ovým členem.

   Alternativním řešením je, že možná budete moct zcela úplně odstranit **nové umístění** . Pokud váš kód používá **nové umístění** k implementaci fondu paměti, kde argument umístění je velikost objektu, který je přidělen nebo odstraněn, může být funkce navrácení prostředků vhodná k nahrazení vlastního kódu vlastního fondu paměti a můžete se zbavit funkcí umístění a stačí použít vlastní operátor **Delete** dvou argumentů namísto funkcí umístění.

   Pokud nechcete kód hned aktualizovat, můžete se vrátit k původnímu chování pomocí možnosti kompilátoru `/Zc:sizedDealloc-`. Použijete-li tuto možnost, funkce odstranění dvou argumentů neexistují a nezpůsobí konflikt s operátorem **odstranění umístění** .

- **Sjednocení datových členů**

   Datové členy sjednocení již nemohou mít odkazové typy. Následující kód byl úspěšně zkompilován v Visual Studio 2013, ale vyvolá chybu v aplikaci Visual Studio 2015.

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   Předchozí kód vytvoří následující chyby:

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   Chcete-li tento problém vyřešit, změňte typ odkazu buď na ukazatel, nebo na hodnotu. Změna typu na ukazatel vyžaduje změny v kódu, který používá pole Union. Změna kódu na hodnotu by změnila data uložená ve sjednocení, která mají vliv na ostatní pole, protože pole v typech sjednocení sdílejí stejnou paměť. V závislosti na velikosti hodnoty může také dojít ke změně velikosti sjednocení.

- Anonymní sjednocení jsou nyní více vyhovující standardu. Předchozí verze kompilátoru vygenerovala explicitní konstruktor a destruktor pro anonymní sjednocení. Tyto funkce vygenerované kompilátorem jsou v aplikaci Visual Studio 2015 odstraněny.

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   Předchozí kód generuje následující chybu v aplikaci Visual Studio 2015:

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   Chcete-li vyřešit tento problém, zadejte vlastní definice konstruktoru nebo destruktoru.

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **Sjednocení s anonymními strukturami**

   Aby bylo možné v souladu se standardem, bylo chování modulu runtime změněno pro členy anonymních struktur ve sjednoceních. Konstruktor pro členy anonymní struktury ve sjednocení již není implicitně volán při vytvoření takového sjednocení. Také destruktor pro členy anonymní struktury ve sjednocení již není implicitně volán, když se sjednocení dostanou mimo rozsah. Vezměte v úvahu následující kód, ve kterém sjednocení U obsahuje anonymní strukturu, která obsahuje pojmenovanou strukturu členů S destruktorem.

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   V Visual Studio 2013 konstruktor pro S je volán při vytvoření sjednocení a destruktor pro S je volán, když je vyčištěn zásobník funkce f. Ale v aplikaci Visual Studio 2015 nejsou volány konstruktor a destruktor. Kompilátor poskytuje upozornění na tuto změnu chování.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Chcete-li obnovit původní chování, zadejte název anonymní struktury. Běhové chování neanonymních struktur je stejné, bez ohledu na verzi kompilátoru.

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Případně můžete zkusit přesunout konstruktor a kód destruktoru do nových funkcí a přidat volání těchto funkcí z konstruktoru a destruktoru pro sjednocení.

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **Řešení šablony**

   Byly provedeny změny překladu názvů pro šablony. V C++systému se při zvažování kandidátů na rozlišení názvu může jednat o případ, že jeden nebo více názvů, které se považují za potenciální shody, vytvoří neplatnou instanci šablony. Tyto neplatné instance obvykle nezpůsobují chyby kompilátoru, princip známý jako SFINAE (Chyba při nahrazování není chyba).

   Pokud nyní SFINAE vyžaduje, aby kompilátor vytvořil instanci specializace šablony třídy, pak všechny chyby, ke kterým dojde během tohoto procesu, jsou chyby kompilátoru. V předchozích verzích kompilátor by tyto chyby ignoroval. Zvažte například následující kód:

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   Pokud kompilujete s aktuálním kompilátorem, zobrazí se následující chyba:

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   Důvodem je, že v bodě prvního vyvolání is_base_of třída `D` ještě nebyla definována.

   V takovém případě oprava nepoužívá takové typové vlastnosti, dokud není definována třída. Pokud přesunete definice `B` a `D` na začátek souboru kódu, dojde k vyřešení chyby. Pokud jsou definice v hlavičkových souborech, zkontrolujte pořadí příkazů include pro hlavičkové soubory, abyste se ujistili, že všechny definice tříd jsou kompilovány před použitím problematických šablon.

- **Kopírovací konstruktory**

   V Visual Studio 2013 i Visual Studio 2015 kompilátor generuje kopírovací konstruktor pro třídu, pokud tato třída má uživatelsky definovaný konstruktor přesunu, ale neexistuje uživatelsky definovaný kopírovací konstruktor. V Dev14 je tento implicitně vygenerovaný kopírovací konstruktor označený také "= Delete".

<!--From here to VS_Update1 added 04/21/2017-->

- **hlavní deklarovaný jako extern "C" nyní vyžaduje návratový typ.**

   Následující kód teď vytvoří C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Chcete-li chybu opravit, přidejte návratový typ:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **TypeName není povolený v inicializátoru členu.**

   Následující kód teď vytvoří C2059:

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   Chcete-li chybu opravit, odeberte `typename` z inicializátoru:

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **Třída úložiště v explicitních specializacích je ignorována.**

   V následujícím kódu se specifikátor třídy statického úložiště ignoruje.

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **Konstanta použitá v static_assert uvnitř šablony třídy bude vždy neúspěšná.**

   Následující kód způsobí, že `static_assert` vždy selže:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Pokud chcete tento problém obejít, zabalte hodnotu ve **struktuře**:

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **Pravidla jsou vydaná pro dopředné deklarace. (Platí jenom pro C.)**

   Následující kód teď vytvoří C2065:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Chcete-li tento problém vyřešit, přidejte správné deklarace dopředné:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Jednotnější vynucování typů ukazatelů na funkce**

   Následující kód teď vytvoří C2197:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Nejednoznačné volání přetížených funkcí**

   Následující kód teď vytvoří C266: ' N:: bind ': dvojznačné volání funkce přetížení

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   Chcete-li chybu opravit, můžete plně kvalifikovat volání `bind: N::bind(...)`. Nicméně pokud je tato změna v manifestu prostřednictvím nedeklarovaného identifikátoru (C2065), může být vhodné ji opravit **pomocí deklarace using** místo toho.

   Tento vzor probíhá často s ComPtr a dalšími typy v oboru názvů `Microsoft::WRL`.

- **Opravit nesprávnou adresu**

   Následující kód nyní vytváří C2440: ' = ': nelze převést z ' type * ' na ' type '. Chcete-li chybu opravit, změňte & (typ) na (typ) a (& f ()) na (f ()).

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **Řetězcový literál je konstantní pole.**

   Následující kód nyní vytváří upozornění C2664: ' void f (void *) ': argument 1 nelze převést z ' const char (* ) [2] ' na ' void * '

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Chcete-li chybu opravit, změňte typ parametru funkce na `const void*`nebo jinak změňte tělo `h` tak, aby vypadalo jako v tomto příkladu:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **Řetězce UDL v c++ 11**

   Následující kód teď vytvoří chybu C3688: Neplatná přípona literálu L; operátor literálu nebo šablona operátoru literálu operator "" L "se nenašly.

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Chcete-li chybu opravit, změňte kód tak, aby přidal mezeru:

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they aren't needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   V příkladu výše `MACRO` již není analyzován jako dvě tokeny (řetězec následovaný makrem). Teď se analyzuje jako UDL s jedním tokenem. Totéž platí pro L "" L ", který byl dříve analyzován jako L" "a L" "a je nyní analyzován jako L" "L a" ".

   Pravidla zřetězení řetězců byla také uvedena v souladu se standardem, což znamená, že L "a" b "je ekvivalentem L" AB ". Předchozí edice sady Visual Studio nepřijaly zřetězení řetězců s jinou šířkou znaků.

- **Odebraný prázdný znak c++ 11**

   Následující kód teď vytvoří chybu C2137: prázdná znaková konstanta

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Chcete-li chybu opravit, změňte kód tak, aby explicitně vytvářely hodnotu null:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **Výjimky knihovny MFC nelze zachytit podle hodnoty, protože nejsou zkopírovány.**

   Následující kód v aplikaci knihovny MFC nyní způsobuje chybu C2316: 'D ': nelze zachytit, protože destruktor nebo kopírovací konstruktor jsou nedostupné nebo odstraněné.

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   Chcete-li opravit kód, můžete změnit blok catch na `catch (const D &)`, ale lepší řešení obvykle používá makra TRY/CATCH knihovny MFC.

- **alignof je nyní klíčové slovo**

   Následující kód teď vytvoří chybu C2332: Class: chybí název značky. Chcete-li opravit kód, musíte přejmenovat třídu nebo, pokud třída provádí stejnou práci jako **alignof**, stačí nahradit třídu klíčovým slovem New.

    ```cpp
    class alignof{}
    ```

- **constexpr je nyní klíčové slovo.**

   Následující kód nyní vytvoří chybu C2059: Chyba syntaxe: ') '. Chcete-li opravit kód, je nutné přejmenovat všechny funkce nebo názvy proměnných, které se nazývají constexpr.

    ```cpp
    int constexpr() {return 1;}
    ```

- **Pohyblivé typy nemůžou být const.**

   Když funkce vrátí typ, který je určen k přesunu, jeho návratový typ by neměl být **const**.

- **Odstraněné kopírovací konstruktory**

   Následující kód nyní vytvoří C2280:: S (S & &) ': Probíhá pokus o odkaz na odstraněnou funkci:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Chcete-li chybu opravit, použijte přímou inicializaci pro `S2`:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Převod na ukazatel funkce se vygeneroval jenom v případě, že není zachytávání lambda.**

   Následující kód vytvoří upozornění C2664 v aplikaci Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Chcete-li chybu opravit, odeberte `=` ze seznamu zachycení.

- **Dvojznačná volání zahrnující operátory převodu**

   Následující kód teď vytvoří chybu C2440: přetypování typu: nejde převést z 2 na 1:

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   Chcete-li chybu opravit, explicitně zavolejte operátor převodu:

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   Následující kód nyní vytvoří chybu C2593: ' operator = ' je dvojznačný:

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   Chcete-li chybu opravit, explicitně zavolejte operátor převodu:

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Opravit neplatnou inicializaci kopírování při inicializaci nestatických datových členů (NSDMI)**

   Následující kód nyní vytvoří chybu upozornění C2664:1:: S1 (S1 & &): nelze převést Argument 1 z ' bool ' na ' const S1 & ':

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Chcete-li chybu opravit, použijte přímou inicializaci:

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Přístup k konstruktorům uvnitř příkazů decltype**

   Následující kód teď vytvoří C2248::: S: nejde získat přístup k soukromému členu deklarovanému ve třídě:

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   Chcete-li chybu opravit, přidejte do `S`deklaraci typu Friend za `S2`:

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Výchozí ctor konstruktoru lambda se implicitně odstraní.**

   Následující kód nyní vytvoří chybu C3497: nelze vytvořit instanci výrazu lambda:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Chcete-li chybu opravit, odeberte nutnost vyvolání výchozího konstruktoru. Pokud lambda nezachycuje cokoli, může být převeden na ukazatel na funkci.

- **Výrazy lambda s odstraněným operátorem přiřazení**

   Následující kód teď vytvoří chybu C2280:

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   Chcete-li chybu opravit, nahraďte lambda třídou funktor nebo odeberte nutnost použití operátoru přiřazení.

- **Pokus o přesunutí objektu s odstraněným kopírovacím konstruktorem**

   Následující kód teď vytvoří chybu C2280: "mobilní:: mobilní" (const &): pokus o odkaz na odstraněnou funkci

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   K opravě chyby použijte `std::move` místo toho:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **Lokální třída nemůže odkazovat na jinou místní třídu definovanou dále ve stejné funkci.**

   Následující kód teď vytvoří chybu C2079: ' používá nedefinovanou strukturu ' Main:: S2 '

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   Chcete-li chybu opravit, přesuňte definici `S2`:

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **V těle odvozeného konstruktoru ctor nelze volat chráněný základní ctor.**

   Následující kód teď vytvoří chybu C2248:1:: S1: nejde získat přístup k chráněnému členu deklarovanému ve třídě 1.

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   Chcete-li chybu opravit, v `S2` odeberte volání `S1()` z konstruktoru a v případě potřeby jej vložte do jiné funkce.

- **{} brání konverzi na ukazatel**

   Následující kód teď vytvoří C2439::p ': člen se nedal inicializovat.

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Chcete-li chybu opravit, odeberte závorky z okolí `0` nebo jinak místo toho použijte **nullptr** , jak je znázorněno v následujícím příkladu:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Nesprávná definice a použití makra pomocí závorek**

   Následující příklad nyní vytvoří chybu C2008: '; ': neočekáváno v definici makra

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Chcete-li tento problém vyřešit, změňte horní řádek na `#define A();`

   Následující kód vytvoří chybu C2059: Chyba syntaxe: ') '

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Chcete-li opravit kód, odeberte prostor mezi a a ().

   Následující kód vytvoří chybu c2091: funkce vrací funkci:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Chcete-li chybu opravit, odeberte závorky po DEKLARaci v S: `DECLARE;`.

   Následující kód vytvoří chybu C2062: typ int se neočekával.

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Pokud chcete problém vyřešit, definujte `A` takto:

    ```cpp
    #define A int
    ```

- **Další Parens v deklaracích**

   Následující kód vytvoří chybu C2062: typ int se neočekával.

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Chcete-li chybu opravit, odeberte závorky kolem `j`. Pokud jsou závorky potřeba pro přehlednost, pak použijte **typedef**.

- **Konstruktory a __declspec generované kompilátorem (-vtable)**

   V aplikaci Visual Studio 2015 existuje větší pravděpodobnost, že vložené konstruktory, které jsou generovány kompilátorem, s virtuálními základními třídami, mohou vystavovat nesprávné použití `__declspec(novtable)` při použití v kombinaci s `__declspec(dllimport)`.

- **Automatický vyžaduje jeden výraz v inicializaci Direct-list.**

   Následující kód teď vytvoří chybu C3518: ' testPositions ': v kontextu Direct-list-inicializace typ pro ' auto ' se dá odvodit jenom z výrazu s jedním inicializátorem.

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Chcete-li chybu opravit, jednu z možností je inicializovat `testPositions` následujícím způsobem:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Kontrola typů vs. ukazatele na typy pro is_convertible**

   Následující kód nyní způsobí selhání statického kontrolního výrazu.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Chcete-li chybu opravit, změňte `static_assert` tak, aby porovnávána odkazy na `D` a `B2`:

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **deklarace __declspec (-vtable) musí být konzistentní.**

   deklarace `__declspec` musí být konzistentní napříč všemi knihovnami. Následující kód nyní vytvoří porušení pravidla s jednou definicí (ODR):

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

###  <a name="VS_Update1"></a>Vylepšení shody v aktualizaci Update 1

- **Soukromé virtuální základní třídy a nepřímá dědičnost**

   Předchozí verze kompilátoru povolily odvozenou třídu pro volání členských funkcí své nepřímo odvozené `private virtual` základní třídy. Toto staré chování nebylo správné a neodpovídá C++ standardu. Kompilátor již nepřijímá kód napsaný tímto způsobem a v důsledku toho vydává chybu kompilátoru C2280.

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   Příklad (před)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   Příklad (po)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   \- nebo –

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Přetížený operátor New a operátor delete**

   Předchozí verze kompilátoru povolují nečlenský **operátor New** a nečlenský **operátor delete** , aby byly deklarované jako statické a deklarované v oborech názvů kromě globálního oboru názvů.  Toto staré chování vytvořilo riziko, že by program nevolal implementaci operátoru **New** nebo **Delete** , kterou programátor zamýšlel, a výsledkem je tiché chybné chování za běhu. Kompilátor již nepřijímá kód napsaný tímto způsobem a namísto toho vydá chybu kompilátoru C2323.

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   Příklad (před)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   Příklad (po)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   Kromě toho, i když kompilátor neposkytuje konkrétní diagnostiku, je vložený operátor **New** považován za nesprávně vytvořený.

- **Volání operátoru ' *Type*() ' (uživatelsky definovaný převod) na typy bez třídy**

   Předchozí verze povoleného kompilátoru ' operator *Type*() ', které mají být volány na typy bez třídy, zatímco jsou tiše ignorovány. Toto staré chování vytvořilo riziko tichého chybného generování kódu, což vede k nepředvídatelnému chování za běhu. Kompilátor již nepřijímá kód napsaný tímto způsobem a namísto toho vydá chybu kompilátoru C2228.

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   Příklad (před)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   Příklad (po)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **Redundantní TypeName v propracované specifikátorech typu**

   Předchozí verze kompilátoru povolily **TypeName** ve vypracovaném specifikátoru typu, ale kód psaný tímto způsobem je sémanticky nesprávným. Kompilátor již nepřijímá kód napsaný tímto způsobem a namísto toho vydá chybu kompilátoru C3406.

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   Příklad (před)

    ```cpp
    template <typename class T>
    class container;
    ```

   Příklad (po)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **Typ srážek polí ze seznamu inicializátorů**

   Předchozí verze kompilátoru nepodporovaly typ srážek polí ze seznamu inicializátorů. Kompilátor teď podporuje tento typ odvození typu, a proto volání šablon funkcí pomocí seznamů inicializátorů teď může být dvojznačné nebo jiné přetížení může být zvolené než v předchozích verzích kompilátoru. Aby bylo možné tyto problémy vyřešit, musí nyní program explicitně určit přetížení, které programátor zamýšlel.

   V případě, že toto nové chování způsobí, že řešení přetížení považuje další kandidáty, které jsou stejně vhodné jako historické kandidáty, volání se nejednoznační a kompilátor vyvolá chybu kompilátoru C2668 v důsledku.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   Příklad 1: dvojznačné volání funkce přetížení (před)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   Příklad 1: nejednoznačné volání přetížené funkce (po)

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   Když toto nové chování způsobí, že řešení přetížení považuje další kandidáta, který je lepší, než historická kandidát, volání se jednoznačně vyřeší na novém kandidáta, což způsobí změnu v chování programu, která se pravděpodobně liší od zamýšlený programátor.

   Příklad 2: Změna v řešení přetížení (před)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   Příklad 2: Změna v řešení přetížení (po)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **Obnovení upozornění příkazu switch**

   Předchozí verze kompilátoru odebrala některá upozornění související s příkazy **Switch** ; Tato upozornění se teď obnovila. Kompilátor nyní vydá obnovená upozornění a upozornění související s konkrétními případy (včetně výchozího případu) jsou nyní vydány na řádku obsahujícím problematický případ, nikoli na posledním řádku příkazu switch. V důsledku toho, že se tato upozornění vydávají na různých řádcích než v minulosti, upozornění, která byla dříve potlačena pomocí `#pragma warning(disable:####)`, již nemusí být potlačena jako zamýšlená. Chcete-li potlačit tato upozornění jako zamýšlená, může být nutné přesunout direktivu `#pragma warning(disable:####)` na řádek nad první problematický případ. Obnoví se následující upozornění:

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   Příklad C4063 (před)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   Příklad C4063 (za)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   Příklady dalších obnovených upozornění jsou uvedeny v dokumentaci.

- **#include: použití specifikátoru nadřazeného adresáře '.. ' v cestě** (týká se pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nerozpoznaly použití specifikátoru nadřazeného adresáře... v cestě `#include` direktiv. Kód psaný tímto způsobem je obvykle určen pro zahrnutí hlaviček, které existují mimo projekt, pomocí nesprávného použití relativních cest projektu. Toto staré chování vytvořilo riziko, že program může být zkompilován zahrnutím jiného zdrojového souboru, než je programátor zamýšlen, nebo zda tyto relativní cesty nebudou přenosné do jiných prostředí pro sestavení. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné C4464 upozornění kompilátoru, pokud je povoleno.

    ```Output
    warning C4464: relative include path contains '..'
    ```

   Příklad (před)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   Příklad (po)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   I když kompilátor neposkytuje konkrétní diagnostiku, doporučujeme také, aby specifikátor nadřazeného adresáře ".." neměl být použit k určení adresáře include projektu.

- **#pragma optimize () rozšiřuje poslední konec souboru hlaviček** (týká se pouze `/Wall` `/WX`).

   Předchozí verze kompilátoru nerozpoznaly změny nastavení příznaku optimalizace, které řídí hlavičkový soubor zahrnutý do jednotky překladu. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné upozornění kompilátoru C4426 v umístění problematické `#include`, pokud je povoleno. Toto upozornění je vystaveno pouze v případě, že změny jsou v konfliktu s příznaky optimalizace nastavenými argumenty příkazového řádku pro kompilátor.

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   Příklad (před)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   Příklad (po)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **Neshoda #pragma upozornění (push)** a **upozornění #pragma (pop)** (týká se pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nerozpoznaly změny stavu `#pragma warning(push)` spárované se změnami stavu `#pragma warning(pop)` v jiném zdrojovém souboru, což je zřídka zamýšlené. Toto staré chování vytvořilo riziko, že program bude zkompilován s jinou sadou upozornění, než je zamýšlený programátor, což může vést k tichému chybnému chování za běhu. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné C5031 upozornění kompilátoru v umístění odpovídajícího `#pragma warning(pop)`, pokud je povoleno. Toto upozornění obsahuje poznámku odkazující na umístění odpovídajícího #pragma upozornění (push).

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   Příklad (před)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   Příklad (po)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   I když je neobvyklá, kód napsaný tímto způsobem je někdy úmyslné. Kód psaný tímto způsobem je citlivý na změny v pořadí `#include`; Pokud je to možné, doporučujeme, aby soubory zdrojového kódu spravovaly stav upozornění v samostatném způsobu.

- **Nespárované upozornění na #pragma (push)** (týká se pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistily na konci jednotky překladu neshodné změny stavu `#pragma warning(push)`. Kompilátor nyní detekuje a upozorňuje programátora kódu napsaného tímto způsobem a vydá volitelné C5032 upozornění kompilátoru v umístění neodpovídajícího `#pragma warning(push)`, pokud je povoleno. Toto upozornění je vystaveno pouze v případě, že v jednotce překladu nejsou žádné chyby kompilace.

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   Příklad (před)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   Příklad (po)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **Další upozornění můžou být vystavena v důsledku vylepšení sledování stavu upozornění #pragma**

   Předchozí verze kompilátoru sledovány #pragma změny stavu upozornění nedostatečně dobře vydávají všechna zamýšlená upozornění. Toto chování vytvořilo riziko, že určitá upozornění budou efektivně potlačena v jiných případech, než je programátor zamýšlen. Kompilátor nyní sleduje `#pragma warning` stav robustnější – obzvláště související se změnami stavu `#pragma warning` v rámci šablon – a volitelně vydá nová upozornění C5031 a C5032, která mají za cíl pomáhat programátorovi najít nezamýšlené použití `#pragma warning(push)` a `#pragma warning(pop)`.

   V důsledku vylepšení sledování změn stavu `#pragma warning` se teď můžou vystavovat upozornění, která se dřív nesprávně potlačila, nebo upozornění související s dříve nezjištěnými problémy.

- **Vylepšená identifikace nedosažitelného kódu**

   C++Změny knihovny Standard a vylepšená možnost volání vložených funkcí v předchozích verzích kompilátoru může povolit, aby kompilátor prokázal, že určitý kód je nyní nedosažitelný. Toto nové chování může mít za následek nové a více často vydaných instancí upozornění C4720.

    ```Output
    warning C4720: unreachable code
    ```

   V mnoha případech může být toto upozornění vystaveno pouze při kompilaci s povolenými optimalizacemi, protože optimalizace mohou vložit více volání funkce, eliminovat redundantní kód nebo jinak určit, že určitý kód je nedosažitelný. Zjistili jsme, že v blocích **try/catch** se často objevily nové instance varovných C4720, zejména ve vztahu k použití [std:: Find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

   Příklad (před)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   Příklad (po)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

###  <a name="VS_Update2"></a>Vylepšení shody v aktualizaci Update 2

- **Další upozornění a chyby mohou být vydány v důsledku částečné podpory pro Expression SFINAE**

   Předchozí verze kompilátoru neanalyzovaly některé druhy výrazů uvnitř specifikátorů **decltype** z důvodu nedostatku podpory pro Expression SFINAE. Toto staré chování nebylo správné a neodpovídá C++ standardu. Kompilátor nyní analyzuje tyto výrazy a má částečnou podporu pro Expression SFINAE z důvodu probíhajících vylepšení dodržování shody. V důsledku toho kompilátor nyní vydá upozornění a chyby nalezené ve výrazech, které předchozí verze kompilátoru neanalyzovaly.

   Když toto nové chování analyzuje výraz **decltype** , který obsahuje typ, který dosud nebyl deklarován, kompilátor vyvolá chybu kompilátoru C2039 v důsledku.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Příklad 1: použití nedeklarovaného typu (před)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   Příklad 1 (za)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   Když toto nové chování analyzuje výraz **decltype** , u kterého chybí nezbytné použití klíčového slova **TypeName** k určení, že název závislého typu je typ, kompilátor vydává upozornění kompilátoru C4346 spolu s chybou kompilátoru C2923.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Příklad 2: závislý název není typu (před)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   Příklad 2 (po)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- `volatile` **proměnné členů zabraňují implicitně definovaným konstruktorům a operátorům přiřazení** .

   Předchozí verze kompilátoru povolily třídu, která má **nestálé** členské proměnné, aby měly výchozí konstruktory Copy/Move a automaticky vygenerovaly výchozí operátory kopírování a přesunu. Toto staré chování nebylo správné a neodpovídá C++ standardu. Kompilátor nyní považuje třídu, která má **nestálé** členské proměnné pro konstruktory konstrukce a přiřazení, což brání automatickému generování výchozích implementací těchto operátorů. Když je taková třída členem sjednocení (nebo anonymního sjednocení uvnitř třídy), konstruktory Copy/Move a operátory přiřazení kopírování a přesunu (nebo třídy obsahující anonymní sjednocení) se implicitně definují jako odstraněné. Pokus o sestavení nebo zkopírování sjednocení (nebo třídy obsahující anonymní sjednocení) bez explicitního definování je chyba a kompilátor vyvolá chybu kompilátoru C2280, která je výsledkem.

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   Příklad (před)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   Příklad (po)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **Statické členské funkce nepodporují kvalifikátory cv.**

   Předchozí verze sady Visual Studio 2015 povolily statickým členským funkcí kvalifikátory cv. K tomuto chování dochází z důvodu regrese v rámci sady Visual Studio 2015 a Visual Studio 2015 Update 1; Visual Studio 2013 a předchozí verze kompilátoru zamítají kód zapsaný tímto způsobem. Chování sady Visual Studio 2015 a sady Visual Studio 2015 Update 1 je nesprávné a neodpovídá C++ standardu.  Visual Studio 2015 Update 2 odmítne kód napsaný tímto způsobem a místo toho vydá chybu kompilátoru C2511.

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   Příklad (před)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   Příklad (po)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **Dopředná deklarace výčtu není v kódu WinRT povolená** (týká se jenom `/ZW`).

   Kód kompilovaný pro prostředí Windows Runtime (WinRT) neumožňuje dopředně deklarovat **výčtové** typy, podobně jako při kompilaci C++ spravovaného kódu pro rozhraní .NET Framework pomocí přepínače kompilátoru `/clr`. Toto chování zajistí, že velikost výčtu je vždy známá a lze jej správně promítnout do systému typů WinRT. Kompilátor odmítne kód napsaný tímto způsobem a vydá chybu kompilátoru C2599 spolu s chybou kompilátoru C3197.

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   Příklad (před)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   Příklad (po)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **Přetížený operátor New a operátor delete se nedá deklarovat jako inline** (úroveň 1 (`/W1`) ve výchozím nastavení.)

   Předchozí verze kompilátoru nevydá upozornění, když je nečlenský operátor New a funkce Delete operátora jsou deklarovány jako inline. Kód napsaný tímto způsobem je nesprávně vytvořen (bez diagnostiky není vyžadován) a může způsobit problémy s pamětí způsobenými neodpovídajícími operátory New a Delete (zejména při použití společně s velikostí dealokace), které mohou být obtížné diagnostikovat. Kompilátor nyní vydává upozornění kompilátoru C4595, aby mohl identifikovat kód napsaný tímto způsobem.

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   Příklad (před)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   Příklad (po)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   Oprava kódu, který je napsán tímto způsobem, může vyžadovat, aby definice operátora byly přesunuty ze souboru hlaviček a do odpovídajícího zdrojového souboru.

###  <a name="VS_Update3"></a>Vylepšení shody v aktualizaci Update 3

- **std:: is_convertable nyní detekuje samostatné přiřazení** (standardní knihovna)

   Předchozí verze `std::is_convertable` typu-vlastnost nerozpoznaly správně vlastní přiřazení typu třídy, pokud je jeho kopírovací konstruktor odstraněný nebo soukromý. Nyní je `std::is_convertable<>::value` správně nastaveno na **hodnotu false** při použití na typ třídy s odstraněným nebo soukromým kopírovacím konstruktorem.

   K této změně není přidružená žádná Diagnostika kompilátoru.

   Příklad

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   V předchozích verzích kompilátoru byly statické kontrolní výrazy ve spodní části tohoto příkladu passované, protože `std::is_convertable<>::value` nebylo nesprávně nastaveno na **hodnotu true**. Nyní je `std::is_convertable<>::value` správně nastaven na **hodnotu false**, což způsobí selhání statických kontrolních výrazů.

- **Přednastavené nebo odstraněné konstruktory triviálního kopírování a přesunu respektují specifikátory přístupu.**

   Předchozí verze kompilátoru nekontrolovaly specifikátor přístupu u výchozích nebo odstraněných konstruktorů triviální kopie a přemístění, než je povolí volání. Toto staré chování nebylo správné a neodpovídá C++ standardu. V některých případech toto staré chování vytvořilo riziko tichého chybného generování kódu, což vede k nepředvídatelnému chování za běhu. Kompilátor nyní kontroluje specifikátor přístupu u výchozích nebo odstraněných konstruktorů triviální kopie a přesunutí, aby bylo možné určit, zda je lze volat, a pokud ne, vystaví se v důsledku upozornění kompilátoru C2248.

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   Příklad (před)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   Příklad (po)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- Vyřazení **podpory kódu ATL s atributy** (ve výchozím nastavení úroveň 1 (`/W1`))

   Předchozí verze kompilátoru podporovaly atribut ATL kódu. Jako další fáze odebrání podpory pro kód ATL s atributy, který [začala v aplikaci Visual Studio 2008](../porting/visual-cpp-what-s-new-2003-through-2015.md#whats-new-for-c-in-visual-studio-2008), je kód ATL s atributy zastaralý. Kompilátor nyní vydává upozornění kompilátoru C4467, aby mohl identifikovat tento druh zastaralého kódu.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Pokud chcete pokračovat v používání kódu ATL s atributy, dokud není podpora odebrána z kompilátoru, můžete toto upozornění zakázat předáním `/Wv:18` nebo `/wd:4467` argumentů příkazového řádku kompilátoru nebo přidáním `#pragma warning(disable:4467)` do zdrojového kódu.

   Příklad 1 (před)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Příklad 1 (za)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Někdy možná budete potřebovat nebo chcete vytvořit soubor IDL, abyste se vyhnuli použití zastaralých atributů ATL, jako v následujícím příkladu kódu.

   Příklad 2 (před)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   Nejprve vytvořte soubor \*.idl; vc140\*.idl vygeneruje soubor lze použít k získání obsahující rozhraní a poznámky souboru IDL.

   Dále přidejte do sestavení krok MIDL, abyste se ujistili, že jsou C++ vygenerovány definice rozhraní.

   Příklad 2 IDL (po)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   Pak použijte ATL přímo v implementačním souboru, jako v následujícím příkladu kódu.

   Příklad 2 implementace (za)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **Soubory předkompilovaných hlaviček (PCH) a neodpovídající direktivy #include** (týká se pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru přijaly neshodné direktivy `#include` ve zdrojových souborech mezi `-Yc` a `-Yu` kompilací při použití souborů předkompilované hlavičky (PCH). Kód napsaný tímto způsobem již není kompilátorem přijat.   Kompilátor nyní vydává upozornění kompilátoru CC4598, aby při použití souborů PCH mohla identifikovat neshodné direktivy `#include`.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   Příklad (před):

   X. cpp (-YCC. h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z. cpp (-Yuc. h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   Příklad (po)

   X. cpp (-YCC. h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z. cpp (-Yuc. h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **Soubory předkompilovaných hlaviček (PCH) a neodpovídající adresáře zahrnutí** (týká se pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru přijaly neodpovídající argumenty příkazového řádku Directory (`-I`) pro kompilátor mezi `-Yc` a `-Yu` kompilací při použití souborů předkompilované hlavičky (PCH). Kód napsaný tímto způsobem již není kompilátorem přijat. Kompilátor nyní vystavuje upozornění kompilátoru CC4599, aby při použití souborů PCH mohla identifikovat neodpovídající argumenty příkazového řádku pro zahrnutí (`-I`).

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   Příklad (před)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   Příklad (po)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 změny shody

### <a name="compiler"></a>Přepínač

- **Konečné** klíčové slovo nyní vygeneruje nevyřešenou chybu symbolu, kde by předtím byla zkompilována:

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   V dřívějších verzích nebyla chyba vyvolána, protože volání bylo **virtuální** volání; program by však při běhu znamenal chybu. Nyní je přiřazena chyba linkeru, protože třída je nyní označena jako konečná. V tomto příkladu, chcete-li opravit chybu, byste propojíte s obj, který obsahuje definici `S2::f`.

- Pokud používáte funkce Friend v oborech názvů, musíte znovu deklarovat funkci Friend předtím, než na ni kliknete, nebo se zobrazí chyba, protože kompilátor nyní odpovídá standardu ISO C++ . Například tento příklad již není zkompilován:

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   Chcete-li tento kód opravit, Deklarujte funkci **Friend** :

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- C++ Standard nepovoluje explicitní specializaci ve třídě. I když v C++ některých případech kompilátor společnosti Microsoft to umožňuje, v případech, jako je následující příklad, je nyní generována chyba, protože kompilátor nebere v úvahu druhou funkci jako specializaci první.

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   Chcete-li tento kód opravit, upravte druhou funkci:

    ```cpp
    template <> void f(char& val);
    ```

- Kompilátor se již nesnaží odstranit tyto dvě funkce v následujícím příkladu a nyní generuje chybu:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   Chcete-li tento kód opravit, upřesněte volání:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- Předtím, než byl kompilátor kompatibilní s ISO C++ 11, byl zkompilován následující kód a způsobil, že `x` přeložit na typ **int**:

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Tento kód nyní překládá `x` na typ `std::initializer_list<int>` a způsobí chybu na dalším řádku, který se pokusí přiřadit `x` k typu **int**. (Ve výchozím nastavení neexistuje žádný převod.) Chcete-li tento kód opravit, použijte **int** k nahrazení hodnoty **auto**:

    ```cpp
    int x = {0};
    int y = x;
    ```

- Inicializace agregace již není povolena, když typ pravé hodnoty neodpovídá typu levé hodnoty, která je inicializována, a dojde k chybě, protože Standard ISO C++ 11 vyžaduje jednotnou inicializaci pro práci bez zužující převody. Pokud byl dříve k dispozici zužující převod, upozornění [kompilátoru (úroveň 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) bylo vydáno namísto chyby C4242.

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   Chcete-li tento kód opravit, přidejte explicitní zužující převod:

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- Následující inicializace již není povolena:

    ```cpp
    void *p = {{0}};
    ```

   Chcete-li tento kód opravit, použijte některou z těchto forem:

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- Vyhledávání názvu bylo změněno. Následující kód je vyřešen odlišně v C++ kompilátoru v aplikaci Visual Studio 2012 a Visual Studio 2013:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   V aplikaci Visual Studio 2012 se `E1` ve výrazu `E1::b` přeložila na `::E1` v globálním oboru. V Visual Studio 2013 `E1` ve výrazu `E1::b` překládá na definici `typedef E2` v `main()` a má typ `::E2`.

- Rozložení objektů se změnilo. Na platformě x 64 se může v porovnání z předchozími verzemi změnit rozložení objektů třídy. Pokud má **virtuální** funkci, ale nemá základní třídu, která má **virtuální** funkci, objektový model kompilátoru vloží ukazatel na tabulku **virtuální** funkce za rozložení datového člena. To znamená, že rozložení nemusí být ve všech případech optimální. V předchozích verzích se optimalizace pro platformu x64 snaží vylepšit rozložení za vás, ale vzhledem k tomu, že se nezdařilo správně pracovat v situacích složitých kódů, byla odebrána v Visual Studio 2013. Podívejte se například na tento kód:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- V Visual Studio 2013 výsledek `sizeof(S2)` na platformě x64 je 48, ale v předchozích verzích se vyhodnocuje na 32. Chcete-li tuto hodnotu vyhodnotit na C++ 32 v kompilátoru Visual Studio 2013 pro platformu x64, přidejte fiktivní základní třídu, která má **virtuální** funkci:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Chcete-li najít místa v kódu, který se pokusil o optimalizaci dříve, použijte kompilátor z této verze společně s možností kompilátoru `/W3` a zapněte upozornění 4370. Příklad:

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Před Visual Studio 2013 tento kód obsahuje tuto zprávu: "upozornění C4370:2": rozložení třídy se od předchozí verze kompilátoru změnilo kvůli lepšímu balení ".

   Kompilátor x86 má stejný problém s podideálním rozložením ve všech verzích kompilátoru. Pokud je například tento kód je zkompilován pro platformu x86:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Výsledek `sizeof(S)` je 24. Dá se ale snížit na 16, pokud použijete alternativní řešení uvedené pro x64:

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>Standardní knihovna

C++ Kompilátor v Visual Studio 2013 zjistí neshody v _ITERATOR_DEBUG_LEVEL, které byly implementovány v aplikaci Visual Studio 2010, a RuntimeLibrary neshody. K těmto neshodě dojde, pokud možnosti kompilátoru `/MT` (statická verze), `/MTd` (statické ladění), `/MD` (dynamická verze) a `/MDd` (dynamický ladění) jsou smíšené.

- Pokud váš kód potvrdí šablony simulovaného aliasu předchozí verze, je nutné ji změnit. Například místo `allocator_traits<A>::rebind_alloc<U>::other`, nyní musíte vyslovit `allocator_traits<A>::rebind_alloc<U>`. I když `ratio_add<R1, R2>::type` již není nutné a teď doporučujeme, abyste si vyřekli `ratio_add<R1, R2>`, předchozí kompilace bude stále zkompilována, protože `ratio<N, D>` je nutné, aby měl "Type" typedef pro snížený poměr, který bude stejný typ, pokud již byl zmenšen.

- Při volání `std::min()` nebo `std::max()`je nutné použít `#include <algorithm>`.

- Pokud váš stávající kód používá simulované rozsahy v předchozím vydání – tradiční výčty bez oboru, které jsou zabaleny v oborech názvů – je třeba je změnit. Pokud jste například odkazovali na typ `std::future_status::future_status`, nyní musíte vyslovit `std::future_status`. Většina kódu však není ovlivněna, například `std::future_status::ready` stále kompiluje.

- `explicit operator bool()` je přísnější než nespecifikovaný operátor-bool-Type (). `explicit operator bool()` povoluje explicitní převod na logickou hodnotu, například v případě, že se jedná o `shared_ptr<X> sp`, `static_cast<bool>(sp)` i `bool b(sp)` jsou platné – a Boolean-testovatelné "kontextové převody" na bool, například `if (sp)`, `!sp``sp &&` jakékoli. `explicit operator bool()` však zakáže implicitní převod na bool, takže nemůžete vyslovit `bool b = sp;` a s ohledem na návratový typ bool nemůžete vyslovit `return sp`.

- Nyní jsou implementovány reálné šablony variadické, _VARIADIC_MAX a související makra nemají žádný vliv. Pokud stále definujete _VARIADIC_MAX, ignoruje se. Je-li potvrzen náš nástroj maker určený k podpoře simulovaných variadic šablon jiným způsobem, je nutné změnit váš kód.

- Kromě běžných klíčových slov hlavičky C++ standardní knihovny teď neumožňují nahradit makro přepsání kontextově závislého klíčového slova **override** a **Final**.

- `reference_wrapper`, `ref()`a `cref()` nyní zakazují vytvoření vazby na dočasné objekty.

- \<náhodný > nyní striktně vynutila podmínky při kompilaci.

- U C++ různých vlastností typu standardní knihovny je předběžná podmínka "T" úplným typem ". I když kompilátor nyní vynutil tuto předběžnou podmínku striktně, nemusí ji vyhovět ve všech situacích. (Protože C++ porušení předběžných podmínek standardní knihovny spustí nedefinované chování, Standard nezaručuje vynucení.)

- C++ Standardní knihovna nepodporuje `/clr:oldSyntax`.

- Specifikace C++ 11 pro common_type < > měla neočekávané a nežádoucí následky; Konkrétně to dělá common_type\<int, int >:: Type Return int & &. Proto kompilátor implementuje navrhované řešení problému pracovní skupiny knihovny 2141, který umožňuje common_type\<int, int = "" >:: Type Return int.

   Vzhledem k tomu, že se jedná o vedlejší účinky této změny, nebude mít případ identity nadále fungovat (common_type\<T > nevede vždy jako typ T). Toto chování vyhovuje navrženému řešení, ale přerušuje jakýkoliv kód, který se spoléhal na předchozí chování.

   Pokud požadujete vlastnost typu identita, nepoužívejte nestandardní `std::identity` definované v \<type_traits >, protože nebude fungovat pro \<void >. Místo toho implementujte vlastní typovou vlastnost identity tak, aby vyhovovala vašim potřebám. Tady je příklad:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

- **Pouze Visual Studio 2013**: knihovna MFC MBCS není obsažena v sadě Visual Studio, protože kódování Unicode je oblíbené a používání znakové sady MBCS bylo významně odmítnuto. Tato změna také udržuje MFC lépe zarovnané s Windows SDK, protože mnoho ovládacích prvků a zpráv má pouze kódování Unicode. Pokud však musíte nadále používat knihovnu MFC MBCS, můžete ji stáhnout z webu MSDN Download Center na [vícebajtové knihovně MFC pro Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770). Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.  (Poznámka: knihovna DLL znakové sady MBCS je obsažena v součástech pro C++ instalaci v aplikaci Visual Studio 2015 a novější).

- Přístupnost pásu karet MFC se změnila.  Místo architektury s jednou úrovní je teď Hierarchická architektura. Staré chování můžete i nadále používat voláním `CRibbonBar::EnableSingleLevelAccessibilityMode()`.

- Metoda `CDatabase::GetConnect` je odebrána. Pro zlepšení zabezpečení je připojovací řetězec nyní uložen zašifrovaný a je dešifrován pouze v případě potřeby; nedá se vrátit jako prostý text.  Řetězec lze získat pomocí metody `CDatabase::Dump`.

- Podpis `CWnd::OnPowerBroadcast` se změnil. Podpis tohoto popisovače zprávy se změní na LPARAM jako druhý parametr.

- Signatury se mění tak, aby vyhovovaly obslužným rutinám zpráv. Seznamy parametrů u následujících funkcí se změnily a používají nově přidané popisovače zpráv ON_WM_ *:

   - `CWnd::OnDisplayChange` změněno na (UINT, int, int) namísto (WPARAM, LPARAM), aby bylo možné použít nové makro ON_WM_DISPLAYCHANGE v mapě zpráv.

   - `CFrameWnd::OnDDEInitiate` změněno na (CWnd *, UINT, UNIT) namísto (WPARAM, LPARAM), aby bylo možné použít nové makro ON_WM_DDE_INITIATE v mapě zpráv.

   - `CFrameWnd::OnDDEExecute` změnit na (CWnd *, HANDLE) místo (WPARAM, LPARAM), aby bylo možné použít nové makro ON_WM_DDE_EXECUTE v mapě zpráv.

   - `CFrameWnd::OnDDETerminate` změnit na (CWnd *) jako parametr namísto (WPARAM, LPARAM), aby bylo možné použít nové makro ON_WM_DDE_TERMINATE v mapě zpráv.

   - místo (WPARAM, LPARAM) se nezmění `CMFCMaskedEdit::OnCut`, aby bylo možné použít nové makro ON_WM_CUT v mapě zpráv.

   - místo (WPARAM, LPARAM) se nezmění `CMFCMaskedEdit::OnClear`, aby bylo možné použít nové makro ON_WM_CLEAR v mapě zpráv.

   - místo (WPARAM, LPARAM) se nezmění `CMFCMaskedEdit::OnPaste`, aby bylo možné použít nové makro ON_WM_PASTE v mapě zpráv.

- direktivy `#ifdef` v hlavičkových souborech knihovny MFC jsou odebrány. V hlavičkových souborech knihovny MFC, které souvisejí s nepodporovanými verzemi Windows (WINVER &lt; 0x0501), se odebralo mnoho direktiv `#ifdef`.

- Knihovna ATL DLL (atl120. dll) je odebrána. Knihovna ATL je nyní poskytována jako záhlaví a statická knihovna (atls.lib).

- Knihovny Atlsd. lib, atlsn. lib a atlsnd. lib se odeberou. Knihovna Atls.lib již nemá závislosti na znakové sadě ani kód specifický pro ladění/vydání. Protože princip funkce je stejný pro Unicode/ANSI i ladění/vydání, je vyžadována pouze jedna verze knihovny.

- Trasovací nástroj ATL nebo MFC je odebrán společně s knihovnou ATL DLL a mechanismus trasování je zjednodušen. Konstruktor `CTraceCategory` nyní přijímá jeden parametr (název kategorie) a makra trasování volají funkce vytváření sestav ladění CRT.

## <a name="visual-studio-2012-breaking-changes"></a>Nejnovější změny sady Visual Studio 2012

### <a name="compiler"></a>Přepínač

- Možnost kompilátoru `/Yl` se změnila. Ve výchozím nastavení kompilátor používá tuto možnost, což může vést k LINKERŮ LNK2011 chyb za určitých podmínek. Další informace naleznete v tématu [/yl (vložení referenčního souboru PCH pro knihovnu ladění)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- V kódu, který je kompilován pomocí `/clr`, klíčové slovo class **výčtu** definuje výčet c++ 11, nikoli výčet modulu CLR (Common Language Runtime). Chcete-li definovat výčet CLR, musíte být explicitní o jeho přístupnost.

- Pomocí klíčového slova Template můžete explicitně určit závislý název (C++ standardní dodržování předpisů v jazyce). V následujícím příkladu je zvýrazněné klíčové slovo šablony povinno vyřešit nejednoznačnost. Další informace najdete v tématu [překlad názvů pro závislé typy](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Konstantní výraz typu float již není povolen jako argument šablony, jak je znázorněno v následujícím příkladu.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Kód, který je zkompilován pomocí možnosti příkazového řádku `/GS` a který má ohrožení zabezpečení po jedné, může vést k ukončení zpracování za běhu, jak je znázorněno v následujícím příkladu pseudokódu.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- Výchozí architektura pro sestavení x86 se změní na SSE2; Kompilátor proto může vygenerovat instrukce SSE a použije registry XMM k provádění výpočtů s plovoucí desetinnou čárkou. Pokud se chcete vrátit k předchozímu chování, použijte příznak kompilátoru `/arch:IA32` k určení architektury jako IA32.

- Kompilátor může vystavit [Upozornění kompilátoru upozornění (úroveň 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) a C4701, kde dříve to nevedlo. Kompilátor aplikuje silnější kontroly pro použití neinicializovaných lokálních proměnných typu ukazatele.

- Je-li zadán nový příznak linkeru `/HIGHENTROPYVA`, systém Windows 8 obvykle způsobí, že přidělení paměti vrátí 64 bitovou adresu. (Před Windows 8 takové přidělení častěji vrací adresy, které byly méně než 2 GB.) Tato změna může vystavit chyby zkrácení ukazatele v existujícím kódu. Ve výchozím nastavení je tento přepínač zapnutý. Chcete-li toto chování zakázat, zadejte `/HIGHENTROPYVA:NO`.

- Spravovaný kompilátor (Visual Basic/C#) také podporuje `/HIGHENTROPYVA` pro spravovaná sestavení.  V tomto případě je však `/HIGHENTROPYVAswitch` ve výchozím nastavení vypnutá.

### <a name="ide"></a>IDE – integrované vývojové prostředí

- I když doporučujeme, abyste v C++/CLI nevytvořili model Windows Formsé aplikace, bude se C++podporovat údržba stávajících aplikací uživatelského rozhraní/CLI. Pokud je nutné vytvořit aplikaci model Windows Forms nebo jinou aplikaci uživatelského rozhraní .NET, použijte C# nebo Visual Basic. Použijte C++/CLI jenom pro účely interoperability.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Knihovna paralelních vzorů a knihovna Concurrency Runtime

`SchedulerType` výčet `UmsThreadDefault` je zastaralý. Specifikace `UmsThreadDefault` vytváří zastaralé upozornění a interně se mapuje zpět na `ThreadScheduler`.

### <a name="standard-library"></a>Standardní knihovna

- Po zásadní změně mezi standardy C++ 98/03 a C++ 11 pomocí explicitních argumentů šablony pro volání `make_pair()` – jako v `make_pair<int, int>(x, y)` – obvykle není kompilována v vizuálu C++ v aplikaci visual Studio 2012. Řešením je vždy volat `make_pair() `bez explicitních argumentů šablony – jako v `make_pair(x, y)`. Zadání explicitních argumentů šablony zaruší účel funkce. Pokud potřebujete přesnou kontrolu nad výsledným typem, použijte místo `make_pair` `pair`, jako v `pair<short, short>(int1, int2)`.

- Další zásadní změna mezi standardy C++ 98/03 a C++ 11: Pokud je implicitně převoditelná na B a B, implicitně převoditelné na C, ale není implicitně převoditelná na C, C++ 98/03 a Visual Studio `pair<A, X>` 2010, aby bylo možné `pair<C, X>`převést (implicitně nebo explicitně). (Druhý typ, X, není zde důležité a není specifický pro první typ v páru.) C++ Kompilátor v aplikaci Visual Studio 2012 detekuje, že není možné implicitně převést na jazyk C a odebírá dvojici převodů z řešení přetížení. Tato změna je pro mnoho scénářů pozitivní. Například přetížení `func(const pair<int, int>&)` a `func(const pair<string, string>&)`a volání `func()` s `pair<const char *, const char *>` budou kompilována s touto změnou. Tato změna však přerušuje kód, který se opírá o agresivní převody párů. Takový kód může být obvykle vyřešen prováděním jedné části převodu explicitně – například předáním `make_pair(static_cast<B>(a), x)` funkci, která očekává `pair<C, X>`.

- Sady Visual Studio 2010 simulované variadické šablony – například `make_shared<T>(arg1, arg2, argN)`– až do limitu 10 argumentů, pomocí razítka přetížení a specializace s využitím strojového stroje preprocesoru. V aplikaci Visual Studio 2012 se toto omezení omezuje na pět argumentů, aby se zlepšila doba kompilace a spotřeba paměti kompilátoru pro většinu uživatelů. Předchozí limit však můžete nastavit tak, že explicitně definujete _VARIADIC_MAX jako 10, projektově v rámci.

- C++ 11 17.6.4.3.1 [makro. Names]/2 zakazuje nahrazení klíčových slov makrem C++ při zahrnutí standardních hlaviček knihovny. Hlavičky nyní generují chyby kompilátoru, pokud zjišťují klíčová slova nahrazená makrem. (Definování _ALLOW_KEYWORD_MACROS umožňuje zkompilovat tento kód, ale důrazně na něj nemůžeme.) Jako výjimka je ve výchozím nastavení povolená forma `new` makra, protože hlavičky se samyně chrání pomocí `#pragma push_macro("new")`/`#undef new`/`#pragma pop_macro("new")`. Definování _ENFORCE_BAN_OF_MACRO_NEW přesně s tím, co jeho název implikuje.

- Chcete-li implementovat různé optimalizace a kontroly ladění, C++ implementace standardní knihovny úmyslně přerušuje binární kompatibilitu mezi verzemi sady Visual Studio (2005, 2008, 2010, 2012). Při použití C++ standardní knihovny zakazuje kombinování souborů objektů a statických knihoven, které jsou kompilovány pomocí různých verzí do jednoho binárního souboru (exe nebo DLL), a zakazuje předávání objektů C++ standardních knihoven mezi binárními soubory, které jsou kompilovány pomocí různých verzí. Kombinování souborů objektů a statických knihoven (pomocí C++ standardní knihovny, které byly zkompilovány pomocí sady visual Studio 2010 s těmi, které byly zkompilovány C++ pomocí kompilátoru v aplikaci Visual Studio 2012, generuje chyby linkeru o neshodu _MSC_VER, kde _MSC_VER je makro, které obsahuje hlavní verzi kompilátoru ( C++ 1700 pro vizuál v aplikaci Visual Studio 2012). Tato kontrola nedokáže detekovat kombinování knihoven DLL a nemůže detekovat kombinování, které zahrnuje Visual Studio 2008 nebo starší.

- Kromě zjištění _ITERATOR_DEBUG_LEVEL neshody, které byly implementovány v aplikaci Visual Studio 2010, C++ kompilátor v aplikaci visual Studio 2012 detekuje neshody běhové knihovny. K těmto neshoděm dochází, když jsou možnosti kompilátoru `/MT` (statická verze), `/MTd` (statický ladicí program), `/MD` (dynamická verze) a `/MDd` (dynamický ladění), jsou smíšené.

- `operator<()`, `operator>()`, `operator<=()`a `operator>=()` byly dříve k dispozici pro `std::unordered_map` a `stdext::hash_map` řady kontejnerů, i když jejich implementace nejsou užitečné. Tyto nestandardní operátory byly odebrány v jazyce Visual C++ Studio 2012. Kromě toho byla rozšířená implementace `operator==()` a `operator!=()` pro rodinu `std::unordered_map` rozšířena tak, aby kryla `stdext::hash_map` rodinu. (Doporučujeme, abyste se vyhnuli použití `stdext::hash_map` řady v novém kódu.)

- C++ 11 22.4.1.4 [locale. codecvt] Určuje, že `codecvt::length()` a `codecvt::do_length()` by měly mít upravitelný `stateT&` parametr, ale Visual Studio 2010 převzal `const stateT&`. C++ Kompilátor v aplikaci Visual Studio 2012 přebírá `stateT&` pověřením standardem. Tento rozdíl je důležitý pro všechny uživatele, kteří se snaží přepsat virtuální funkci `do_length()`.

### <a name="crt"></a>CRT

- Halda jazyka C runtime (CRT), která se používá pro New a hodnotu (), již není soukromá. CRT nyní používá haldu procesu. To znamená, že halda není zničena při uvolnění knihovny DLL, takže knihovny DLL, které jsou staticky propojeny s CRT, musí zajistit, aby paměť, která je přidělena kódem knihovny DLL, byla vyčištěna před uvolněním.

- Funkce `iscsymf()` vyhodnotí záporné hodnoty.

- Struktura `threadlocaleinfostruct` se změnila tak, aby odpovídala změnám funkcí národního prostředí.

- Funkce CRT, které mají odpovídající vnitřní prvky jako `memxxx()`, `strxxx()` jsou odebrány z intrin. h. Pokud jste zahrnuli intrin. h jenom pro tyto funkce, musíte teď zahrnout odpovídající hlavičky CRT.

### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

- Odebrala se podpora fúze (afxcomctl32. h); Proto byly odebrány všechny metody definované v \<afxcomctl32. h >. Hlavičkové soubory \<afxcomctl32. h > a \<afxcomctl32. inl > byly odstraněny.

- Změnili jste název `CDockablePane::RemoveFromDefaultPaneDividier` na `CDockablePane::RemoveFromDefaultPaneDivider`.

- Změnili jste podpis `CFileDialog::SetDefExt` pro použití LPCTSTR; Proto jsou sestavení v kódování Unicode ovlivněna.

- Byly odebrány zastaralé kategorie trasování knihovny ATL.

- Byl změněn podpis `CBasePane::MoveWindow`, aby bylo možné provést `const CRect`.

- Změnili jste podpis `CMFCEditBrowseCtrl::EnableBrowseButton`.

- Odebrání `m_fntTabs` a `m_fntTabsBold` z `CMFCBaseTabCtrl`.

- Byl přidán parametr do konstruktorů `CMFCRibbonStatusBarPane`. (Jedná se o výchozí parametr, a proto se nejedná o derozdělení do zdrojového kódu.)

- Byl přidán parametr do konstruktoru `CMFCRibbonCommandsListBox`. (Jedná se o výchozí parametr, a proto se nejedná o derozdělení do zdrojového kódu.)

- Odebrali jsme rozhraní `AFXTrackMouse` API (a související procedura časovače). Místo toho použijte rozhraní Win32 `TrackMouseEvent` API.

- Byl přidán parametr do konstruktoru `CFolderPickerDialog`. (Jedná se o výchozí parametr, a proto se nejedná o derozdělení do zdrojového kódu.)

- změnila se velikost `CFileStatus` struktury: člen `m_attribute` se změnil z hodnoty BYTE na DWORD (tak, aby odpovídal hodnotě vrácené z `GetFileAttributes`).

- `CRichEditCtrl` a `CRichEditView` použít MSFTEDIT_CLASS (RichEdit 4,1 Control) místo RICHEDIT_CLASS (RichEdit 3,0 Control) v sestaveních Unicode.

- Odebrané `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground`, protože je vždycky TRUE v systémech Windows Vista, Windows 7 a Windows 8.

- Odebrané `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable`, protože je vždycky TRUE v systémech Windows Vista, Windows 7 a Windows 8.

- Odebrání `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`. Rozhraní API systému Windows volejte přímo v systémech Windows Vista, Windows 7 a Windows 8.

- Odebrání `AFX_GLOBAL_DATA::DwmDefWindowProc`. Rozhraní API systému Windows volejte přímo v systémech Windows Vista, Windows 7 a Windows 8.

- Přejmenování `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` na `IsDwmCompositionEnabled`, aby se vyloučila kolize názvů.

- Změněné identifikátory pro určitý počet interních časovačů MFC a přesunuly definice na AFXRES. h (AFX_TIMER_ID_ *).

- Změnila se signatura `OnExitSizeMove` metody tak, aby souhlasila s ON_WM_EXITSIZEMOVEm makrem:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Změnil se název a podpis `OnDWMCompositionChanged` k vyjádření souhlasu s ON_WM_DWMCOMPOSITIONCHANGEDm makrem:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Změnila se signatura `OnMouseLeave` metody tak, aby souhlasila s ON_WM_MOUSELEAVEm makrem:

   - `CMFCCaptionBar`

   - `CMFCColorBar`

   - `CMFCHeaderCtrl`

   - `CMFCProperySheetListBox`

   - `CMFCRibbonBar`

   - `CMFCRibbonPanelMenuBar`

   - `CMFCRibbonRichEditCtrl`

   - `CMFCSpinButtonCtrl`

   - `CMFCToolBar` ReplaceThisText

   - `CMFCToolBarComboBoxEdit`

   - `CMFCToolBarEditCtrl`

   - `CMFCAutoHideBar`

- Byl změněn podpis `OnPowerBroadcast` k vyjádření souhlasu s ON_WM_POWERBROADCASTm makrem:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

- Byl změněn podpis `OnStyleChanged` k vyjádření souhlasu s ON_WM_STYLECHANGEDm makrem:

   - `CMFCListCtrl`

   - `CMFCStatusBar`

- Přejmenujte `FontFamalyProcFonts` interní metody na `FontFamilyProcFonts`.

- Bylo odebráno množství globálních statických `CString` objektů, které eliminují nevracení paměti v některých situacích (nahrazeno #defines), a následující proměnné členů třídy:

   - `CKeyBoardManager::m_strDelimiter`

   - `CMFCPropertyGridProperty::m_strFormatChar`

   - `CMFCPropertyGridProperty::m_strFormatShort`

   - `CMFCPropertyGridProperty::m_strFormatLong`

   - `CMFCPropertyGridProperty::m_strFormatUShort`

   - `CMFCPropertyGridProperty::m_strFormatULong`

   - `CMFCPropertyGridProperty::m_strFormatFloat`

   - `CMFCPropertyGridProperty::m_strFormatDouble`

   - `CMFCToolBarImages::m_strPngResType`

   - `CMFCPropertyGridProperty::m_strFormat`

- Změnili jste podpis `CKeyboardManager::ShowAllAccelerators` a odebrali jste parametr oddělovače akcelerátoru.

- Přidejte `CPropertyPage::GetParentSheet`a ve třídě `CPropertyPage` zavolejte místo `GetParent`, abyste získali správné okno nadřazeného okna, což může být nadřazené nebo při`CPropertyPage`okno. Je možné, že budete muset změnit kód pro volání `GetParentSheet` místo `GetParent`.

- Opravené nevyrovnané #pragma upozornění (push) v ATLBASE. H, což způsobilo nesprávné zakázání upozornění Tato upozornění jsou teď po ATLBASE povolená správně. H byla analyzována.

- Přesunuly se metody související s D2D z AFX_GLOBAL_DATA do _AFX_D2D_STATE:

   - `GetDirectD2dFactory`

   - `GetWriteFactory`

   - `GetWICFactory`

   - `InitD2D`

   - `ReleaseD2DRefs`

   - `IsD2DInitialized`

   - `D2D1MakeRotateMatrix`

   - Místo volání, například `afxGlobalData.IsD2DInitialized`, volejte `AfxGetD2DState->IsD2DInitialized`.

- Odebrala se zastaralá knihovna ATL *. Soubory CPP ze složky \atlmfc\include

- Pro splnění `DLLMain` požadavků byla přesunuta `afxGlobalData` inicializace na vyžádání místo v čase inicializace CRT.

- Do `CMFCOutlookBarPane` třídy byla přidána metoda `RemoveButtonByIndex`.

- Oprava `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` k `IsFrequentlyUsedCmd`.

- Pro `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`byla opravena několik instancí `RestoreOriginalstate`.

- Nepoužívané metody se odebraly z `CDockablePane`: `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, `GetRecentSiblingPaneInfo`a `CanAdjustLayout`.

- Byly odebrány `CDockablePane` statické členské proměnné `m_bCaptionText` a `m_bHideDisabledButtons`.

- Do `CMFCFontComboBox`se přidala metoda override `DeleteString`.

- Z `CPane`se odebraly nepoužívané metody: `GetMinLength` a `IsLastPaneOnLastRow`.

- Přejmenování `CPane::GetDockSiteRow(CDockingPanesRow *)` na `CPane::SetDockSiteRow`.

## <a name="visual-studio-2010-breaking-changes"></a>Nejnovější změny sady Visual Studio 2010

### <a name="compiler"></a>Přepínač

- Klíčové slovo **auto** má nový výchozí význam. Vzhledem k tomu, že použití starého významu je vzácné, většina aplikací nebude touto změnou ovlivněná.

- Nové klíčové slovo **static_assert** je zavedeno, což způsobí konflikt názvů, pokud v kódu již existuje identifikátor s tímto názvem.

- Podpora pro nový zápis lambda vylučuje podporu pro kódování identifikátoru GUID bez uvozovek v atributu UUID IDL.

- .NET Framework 4 zavádí koncept poškozených výjimek stavu, což jsou výjimky, které ponechávají proces v neopravitelném poškozeném stavu. Ve výchozím nastavení nemůžete zachytit poškozenou výjimku stavu, a to ani pomocí možnosti kompilátoru/EHa, která zachycuje všechny ostatní výjimky.                 Chcete-li explicitně zachytit výjimku poškozeného stavu, použijte příkazy __try-\__except. Nebo použijte atribut [HandledProcessCorruptedStateExceptions], aby funkce mohla zachytit poškozené výjimky stavu.  Tato změna ovlivňuje hlavně systémové programátory, kteří by museli zachytit výjimku poškozeného stavu. Osm výjimek je STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION EXCEPTION_NONCONTINUABLE_EXCEPTION EXCEPTION_PRIV_INSTRUCTION STATUS_ UNWIND_CONSOLIDATE.                 Další informace o těchto výjimkách naleznete v makru [GetExceptionCode](/windows/win32/Debug/getexceptioncode) .

- Revidovaná možnost kompilátoru `/GS` chrání proti přetečení vyrovnávací paměti před více komplexními verzemi než v předchozích verzích. Tato verze může do zásobníku vložit další kontroly zabezpečení, které by mohly snížit výkon. Pomocí nového klíčového slova `__declspec(safebuffers)` instruujte kompilátor, že nevloží kontroly zabezpečení pro konkrétní funkci.

- Pokud kompilujete s možnostmi kompilátoru `/GL` (celková optimalizace programu) a `/clr` (kompilace modulu Common Language Runtime), možnost `/GL` je ignorována. Tato změna byla provedena, protože kombinace možností kompilátoru poskytuje málo výhod. V důsledku této změny dojde k vylepšení výkonu sestavení.

- Ve výchozím nastavení je podpora pro trigraphs ve Visual Studiu 2010 zakázaná. Pokud chcete povolit podporu trigraphs, použijte možnost kompilátoru `/Zc:trigraphs`. Trigraph se skládá ze dvou po sobě jdoucích otazníků ("??") následovaný jedinečným třetím znakem. Kompilátor nahradí trigraph odpovídajícím znakem interpunkce. Kompilátor například nahradí `??=` trigraph znakem "#". Použijte trigraphs ve zdrojových souborech jazyka C, které používají znakovou sadu, která neobsahuje vhodné grafické reprezentace pro některé znaky interpunkce.

- Linker již nepodporuje optimalizaci pro systém Windows 98. Pokud zadáte `/OPT:WIN98` nebo `/OPT:NOWIN98`, možnost `/OPT` (optimalizace) vytvoří chybu při kompilaci.

- Výchozí možnosti kompilátoru, které jsou určeny vlastnostmi systému sestavení RuntimeLibrary a DebugInformationFormat, byly změněny. Ve výchozím nastavení jsou tyto vlastnosti sestavení určeny v projektech, které jsou vytvořeny pomocí C++ sady Visual Release 7,0 až 10,0. Pokud migrujete projekt, který byl vytvořen pomocí sady C++ Visual 6,0, zvažte, zda chcete zadat hodnotu pro tyto vlastnosti.

- V aplikaci Visual Studio 2010, RuntimeLibrary = vícevláknové (`/MD`) a DebugInformationFormat = ProgramDatabase (`/Zi`). V jazyce C++ Visual 9,0 RuntimeLibrary = vícevláknové (`/MT`) a DebugInformationFormat = Disabled.

### <a name="clr"></a>CLR

- Kompilátory C# Microsoft a Visual Basic teď můžou vytvořit primární spolupracující sestavení (no-PIA). Sestavení bez PIA může používat typy COM bez nasazení příslušného primárního definičního sestavení (PIA). Při využívání sestavení bez PIA vytvořených pomocí jazyka Visual C# nebo Visual Basic musíte odkazovat na sestavení PIA v příkazu Compile předtím, než budete odkazovat na jakékoli sestavení bez PIA, které používá knihovnu.

### <a name="visual-studio-c-projects-and-msbuild"></a>Projekty a C++ MSBuild sady Visual Studio

- Projekty sady C++ Visual Studio jsou nyní založeny na nástroji MSBuild. V důsledku toho soubory projektu používají nový formát souboru XML a příponu. vcxproj. Visual Studio 2010 automaticky převede soubory projektu z dřívějších verzí sady Visual Studio do nového formátu souboru. Existující projekt je ovlivněn, pokud závisí na předchozím nástroji pro sestavení, VCBUILD. exe nebo příponě souboru projektu,. vcproj.

- V dřívějších verzích vizuál C++ podporoval pozdní vyhodnocení seznamů vlastností. Nadřazený seznam vlastností může například importovat podřízený seznam vlastností a nadřízený může použít proměnnou definovanou v podřízeném prvku k definování dalších proměnných. Pozdní vyhodnocení povoluje nadřazenému objektu používat podřízenou proměnnou, a to i před importem podřízeného seznamu vlastností. V aplikaci Visual Studio 2010 nelze použít proměnnou listu projektu předtím, než je definována, protože nástroj MSBuild podporuje pouze prvotní vyhodnocení.

### <a name="ide"></a>IDE – integrované vývojové prostředí

- Dialogové okno ukončení aplikace již nekončí aplikací. V předchozích verzích, když funkce `abort()` nebo `terminate()` zavřela maloobchodní sestavení aplikace, knihovna run-time jazyka C zobrazila zprávu ukončení aplikace v okně konzoly nebo dialogovém okně. Zpráva uvedená v části "Tato aplikace požádala modul runtime o jeho ukončení neobvyklým způsobem. Další informace získáte od týmu podpory aplikace. " Zpráva ukončení aplikace byla redundantní, protože v systému Windows se následně zobrazila aktuální obslužná rutina ukončení, což byl obvykle dialogové okno Zasílání zpráv o chybách systému Windows (Dr. Watson) nebo ladicí program sady Visual Studio. Počínaje verzí Visual Studio 2010 se v knihovně run-time jazyka C nezobrazí zpráva. Kromě toho modul runtime zabraňuje aplikaci v ukončení před spuštěním ladicího programu. Toto je zásadní změna pouze v případě, že závisíte na předchozím chování zprávy ukončení aplikace.

- Konkrétně pro Visual Studio 2010, IntelliSense nefunguje pro C++kód nebo atributy/CLI, **Najít všechny odkazy** nefungují pro lokální proměnné a model kódu nenačte názvy typů z importovaných sestavení nebo vyhodnotí typy na jejich plně kvalifikované názvy.

### <a name="libraries"></a>Knihovny

- Třída SafeInt je obsažena ve vizuálu C++ a již není v samostatném stažení. Toto je zásadní změna pouze v případě, že jste vytvořili třídu, která je také pojmenována "SafeInt".

- Model nasazení knihoven již nepoužívá manifesty k nalezení konkrétní verze dynamické knihovny. Místo toho název každé knihovny DLL obsahuje číslo verze a vy použijete tento název k vyhledání knihovny.

- V předchozích verzích sady Visual Studio bylo možné znovu sestavit knihovny run time. Visual Studio 2010 již nepodporuje vytváření vlastních kopií souborů běhové knihovny jazyka C.

### <a name="standard-library"></a>Standardní knihovna

- Hlavička \<iterátoru > již není automaticky obsažena v mnoha dalších hlavičkových souborech. Místo toho zahrňte tuto hlavičku explicitně, pokud požadujete podporu pro samostatné iterátory definované v hlavičce. Existující projekt je ovlivněn, pokud závisí na předchozím nástroji pro sestavení, souboru VCBUILD. exe nebo příponě souboru projektu,. vcproj. iterátor.

- V hlavičce \<algoritmu > jsou odebrány checked_ * a unchecked_\* funkce. A v hlavičce \<iterátoru > > je třída `checked_iterator` odebrána a přidala se třída `unchecked_array_iterator`.

- Byl odebrán konstruktor `CComPtr::CComPtr(int)`. Tento konstruktor povolil objekt `CComPtr`, který se má vytvořit z makra NULL, ale byl zbytečný a povolený nesmyslná konstrukce z nenulových celých čísel.

   `CComPtr` lze stále vytvořit z hodnoty NULL, která je definována jako 0, ale selže, pokud je vytvořena z celého čísla jiného než literál 0. Místo toho použijte **nullptr** .

- Odebraly se následující `ctype` členské funkce: `ctype::_Do_narrow_s`, `ctype::_Do_widen_s`, `ctype::_narrow_s`, `ctype::_widen_s`. Pokud aplikace používá jednu z těchto členských funkcí, je nutné ji nahradit odpovídající nezabezpečenou verzí: `ctype::do_narrow`, `ctype::do_widen`, `ctype::narrow`, `ctype::widen`.

### <a name="crt-mfc-and-atl-libraries"></a>Knihovny CRT, MFC a ATL

- Byla odebrána podpora pro uživatele, aby mohli vytvářet knihovny CRT, MFC a ATL. Například není k dispozici žádný odpovídající soubor NMAKE. Uživatelé však stále mají přístup ke zdrojovému kódu pro tyto knihovny. Dokument, který popisuje možnosti nástroje MSBuild, které Microsoft používá k vytváření těchto knihoven, bude pravděpodobně zveřejněn na blogu Visual C++ týmu.

- Byla odebrána podpora knihovny MFC pro IA64. Nicméně podpora pro CRT a ATL na IA64 je stále k dispozici.

- Řadové číslovky již nejsou znovu používány v souborech definice modulu MFC (. def). Tato změna znamená, že pořadí se nebude lišit mezi podverzemi a binární kompatibilita pro aktualizace Service Pack a rychlé opravy technických vydání se zlepší.

- Do třídy `CDocTemplate` byla přidána nová virtuální funkce. Tato nová virtuální funkce je [třídou CDocTemplate –](../mfc/reference/cdoctemplate-class.md). Předchozí verze `OpenDocumentFile` obsahovala dva parametry. Nová verze má tři parametry. Pro podporu správce restartování musí jakákoli třída odvozená z `CDocTemplate` implementovat verzi, která má tři parametry. Nový parametr je `bAddToMRU`.

### <a name="macros-and-environment-variables"></a>Makra a proměnné prostředí

- Proměnná prostředí __MSVCRT_HEAP_SELECT už není podporovaná. Tato proměnná prostředí je odebrána a neexistuje žádná náhrada.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční informace

- Z referenčního kompilátoru Microsoft Macro assembleru bylo odebráno několik direktiv. Odebrané direktivy jsou `.186`, `.286`, `.286P`, `.287`, `.8086`, `.8087`a `.NO87`.

## <a name="visual-studio-2008-breaking-changes"></a>Nejnovější změny sady Visual Studio 2008

### <a name="compiler"></a>Přepínač

- Platformy Windows 95, Windows 98, Windows MILLENNIUM a Windows NT již nejsou podporovány. Tyto operační systémy byly ze seznamu cílových platforem odebrány.

- Kompilátor již nepodporuje více atributů, které byly přímo přidruženy k serveru ATL. Následující atributy již nejsou podporovány:

   - perf_counter

   - perf_object

   - Perfmon

   - request_handler

   - soap_handler

   - soap_header

   - soap_method

   - tag_name

### <a name="visual-studio-c-projects"></a>Projekty sady C++ Visual Studio

- Při upgradu projektů z předchozích verzí sady Visual Studio může být nutné upravit makra WINVER a _WIN32_WINNT tak, aby byla větší než nebo rovna 0x0500.

- Počínaje sadou Visual Studio 2008, Průvodce vytvořením nového projektu nemá možnost vytvořit projekt C++ SQL Server. SQL Server projekty vytvořené pomocí starší verze sady Visual Studio budou i nadále kompilovány a fungovat správně.

- Odebral se soubor hlaviček rozhraní Windows API Winable. h. Místo toho použijte Winuser. h.

- Knihovna rozhraní API systému Windows Rpcndr. lib byla odebrána. Místo toho připojte pomocí rpcrt4. lib.

### <a name="crt"></a>CRT

- Odebrala se podpora pro Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4,0.

- Byly odebrány následující globální proměnné:

   - _osplatform

   - _osver

   - _winmajor

   - _winminor

   - _winver

- Následující funkce byly odebrány. Místo toho použijte `GetVersion` nebo `GetVersionEx` funkce rozhraní API systému Windows:

   - _get_osplatform

   - _get_osver

   - _get_winmajor

   - _get_winminor

   - _get_winver

- Syntaxe poznámek SAL se změnila. Další informace najdete v tématu [poznámky SAL](../c-runtime-library/sal-annotations.md).

- Filtr IEEE teď podporuje instrukční sady SSE 4,1. Další informace najdete v tématu [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Běhové knihovny jazyka C, dodávané se sadou Visual Studio, již nejsou závislé na systémové knihovně DLL Msvcrt. dll.

### <a name="standard-library"></a>Standardní knihovna

- Odebrala se podpora pro Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4,0.

- Když kompilujete v režimu ladění s definovaným _HAS_ITERATOR_DEBUGGING (nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studiu 2010), aplikace nyní vyhodnotí, kdy se iterátor pokusí zvýšit nebo snížit hodnoty za hranicemi podkladového kontejneru.

- Členská proměnná c třídy zásobníku je teď deklarovaná jako chráněná. Dříve byla tato proměnná členů deklarována jako veřejná.

- Chování `money_get::do_get` se změnilo. Dříve při analýze peněžních částek s více číslicemi zlomků, než jsou volány `frac_digits``do_get` použity pro jejich spotřebování. Nyní `do_get` zastaví analýzu po obnově `frac_digits` znaků.

### <a name="atl"></a>ATL

- Knihovnu ATL nelze sestavit bez závislosti na CRT. V dřívějších verzích sady Visual Studio můžete použít #define ATL_MIN_CRT a vytvořit tak projekt ATL na základě minima na CRT. V aplikaci Visual Studio 2008 jsou všechny projekty ATL na CRT závislé, bez ohledu na to, zda je definována ATL_MIN_CRT.

- Základ kódu ATL serveru byl vydán jako sdílený zdrojový projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio. Třídy kódování a dekódování dat z atlenc. h a funkce nástrojů a třídy z atlutil. h a atlpath. h jsou zachované a teď jsou součástí knihovny ATL. Několik souborů přidružených k serveru ATL již nejsou součástí sady Visual Studio.

- Některé funkce již nejsou zahrnuty v knihovně DLL. Pořád se nacházejí v knihovně importů. Nebude to mít vliv na kód, který funkce používá staticky. Bude mít vliv pouze na kód, který tyto funkce používá dynamicky.

- Makra PROP_ENTRY a PROP_ENTRY_EX jsou zastaralá a v případech zabezpečení nahrazena makry PROP_ENTRY_TYPE a PROP_ENTRY_TYPE_EX.

### <a name="atlmfc-shared-classes"></a>Sdílené třídy ATL/MFC

- Knihovnu ATL nelze sestavit bez závislosti na CRT. V dřívějších verzích sady Visual Studio můžete použít `#define ATL_MIN_CRT`, aby projekt knihovny ATL byl na CRT závislý. V aplikaci Visual Studio 2008 jsou všechny projekty ATL na CRT závislé, bez ohledu na to, zda je definována ATL_MIN_CRT.

- Základ kódu ATL serveru byl vydán jako sdílený zdrojový projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio. Třídy kódování a dekódování dat z atlenc. h a funkce nástrojů a třídy z atlutil. h a atlpath. h jsou zachované a teď jsou součástí knihovny ATL. Několik souborů přidružených k serveru ATL již nejsou součástí sady Visual Studio.

- Některé funkce již nejsou zahrnuty v knihovně DLL. Pořád se nacházejí v knihovně importů. Nebude to mít vliv na kód, který funkce používá staticky. Bude mít vliv pouze na kód, který tyto funkce používá dynamicky.

### <a name="mfc"></a>MFC

- `CTime` třída: třída `CTime` nyní přijímá data začínající od 1/1/1900 0001 místo 1/1/1970 0001

- Pořadí ovládacích prvků v dialogových oknech knihovny MFC: správné pořadí tabulátoru více ovládacích prvků v dialogovém okně knihovny MFC je narušeno, pokud je ovládací prvek ActiveX knihovny MFC vložen do pořadí prvků. Tato změna opravuje tento problém.

   Například vytvořte dialog knihovny MFC, který obsahuje ovládací prvek ActiveX a několik ovládacích prvků pro úpravy. Umístěte ovládací prvek ActiveX uprostřed pořadí ovládacích prvků pro úpravy. Spusťte aplikaci, klikněte na ovládací prvek pro úpravy, jehož pořadí karet je za ovládacím prvkem ActiveX a pak tabulátor. před touto změnou se fokus přistoupí k ovládacímu prvku pro úpravy, který následuje po ovládacím prvku ActiveX, a ne na následujícím ovládacím prvku pro úpravy v pořadí prvků.

- `CFileDialog` třída: vlastní šablony pro `CFileDialog` třídu nelze automaticky přenést do systému Windows Vista. Jsou pořád použitelné, ale nebudou mít další funkce ani vzhled dialogových oken ve stylu Windows Vista.

- `CWnd` třídy a `CFrameWnd` třídy: metoda `CWnd::GetMenuBarInfo` byla odebrána.

   Metoda `CFrameWnd::GetMenuBarInfo` je nyní nevirtuální metodou. Další informace naleznete v tématu **funkce GetMenuBarInfo** v Windows SDK.

- Podpora MFC ISAPI: knihovna MFC již nepodporuje vytváření aplikací s rozhraním ISAPI (Internet Server Application Programming Interface). Pokud chcete sestavit aplikaci ISAPI, zavolejte rozšíření ISAPI přímo.

- Zastaralá rozhraní API ANSI: verze ANSI několika metod MFC jsou zastaralé. Ve svých budoucích aplikacích použijte verze Unicode těchto metod. Další informace najdete v tématu **požadavky na sestavení pro běžné ovládací prvky systému Windows Vista**.

## <a name="visual-studio-2005-breaking-changes"></a>Nejnovější změny sady Visual Studio 2005

### <a name="crt"></a>CRT

- Mnoho funkcí se už nepoužívá. Viz **zastaralé funkce CRT**.

- Mnoho funkcí nyní ověřuje jejich parametry a zastavuje provádění, pokud byly zadány neplatné parametry. Toto ověření může přerušit kód, který předává neplatné parametry a spoléhá na to, že je funkce ignoruje, nebo pouze vracet kód chyby. Viz **ověření parametru**.

- Hodnota popisovače souboru – 2 se nyní používá k označení toho, že `stdout` a `stderr` nejsou k dispozici pro výstup, například v aplikaci systému Windows, která nemá žádné okno konzoly. Použila se předchozí hodnota-1. Další informace najdete v tématu [_fileno](../c-runtime-library/reference/fileno.md).

- Byly odebrány knihovny CRT s jedním vláknem (LIBC. lib a LIBCD. lib). Používejte vícevláknové knihovny CRT. Příznak kompilátoru `/ML` již není podporován. Neuzamykání verzí některých funkcí byly přidány v případech, kdy rozdíl výkonu mezi vícevláknovým kódem a kódem s jedním vláknem je potenciálně významný.

- Bylo odebráno přetížení metody POW, Double POW (int, int), aby bylo lépe v souladu se standardem.

- Specifikátor formátu% n již není ve výchozím nastavení podporován v žádné printf rodině funkcí, protože je podstatou nezabezpečený. Pokud dojde k% n, výchozí chování je vyvolat neplatnou obslužnou rutinu parametru. Pokud chcete povolit podporu% n, použijte `_set_printf_count_output` (viz také `_get_printf_count_output`).

- `sprintf` nyní vytiskne záporné znaménko nuly se znaménkem.

- `swprintf` byl změněn tak, aby odpovídal standardu; nyní vyžaduje parametr velikosti. Forma `swprintf` bez parametru size je zastaralá.

- `_set_security_error_handler` byla odebrána. Odeberte všechna volání této funkce; výchozí obslužná rutina je mnohem bezpečnější způsob, jak řešit chyby zabezpečení.

- `time_t` je teď 64 hodnota (Pokud není definovaná _USE_32BIT_TIME_T).

- `_spawn``_wspawn` Functions nyní opouští `errno` bez dotyku, jak je určeno standardem C.

- RTC teď ve výchozím nastavení používá velké znaky.

- Funkce podpory řídicího slova s plovoucí desetinnou čárkou jsou pro aplikace zkompilované pomocí `/CLR` nebo `/CLR:PURE`zastaralé. Zasažené funkce jsou `_clear87`, `_clearfp`, `_control87``_controlfp`, `_fpreset``_status87``_statusfp`. Upozornění na vyřazení můžete zakázat definováním _CRT_MANAGED_FP_NO_DEPRECATE, ale použití těchto funkcí ve spravovaném kódu je nepředvídatelné a nepodporované.

- Některé funkce nyní vracejí ukazatele const. Staré chování, které neconst, lze obnovit definováním _CONST_RETURN. Ovlivněné funkce jsou

   - memchr, wmemchr

   - strchr, wcschr, _mbschr, _mbschr_l

   - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

   - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

   - strstr, wcsstr, _mbsstr, _mbsstr_l

- Při propojování s setargv. obj nebo wsetargv. obj již není možné potlačit rozšíření zástupného znaku na příkazovém řádku jeho uzavřením do dvojitých uvozovek. Další informace najdete v tématu [rozšíření argumentů zástupného znaku](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Standardní knihovna (2005)

- Třída výjimky (umístěná v hlavičce \<výjimky >) byla přesunuta do oboru názvů `std`. V předchozích verzích byla tato třída v globálním oboru názvů. Chcete-li vyřešit všechny chyby, které signalizují, že třídu výjimky nelze nalézt, přidejte následující příkaz using do kódu: `using namespace std;`

- Při volání `valarray::resize()`bude obsah `valarray` ztracen a bude nahrazen výchozími hodnotami. Metoda `resize()` je určena k opětovné inicializaci `valarray` místo toho, aby se dynamicky narůsta jako vektor.

- Vyladit iterátory: aplikace sestavené pomocí ladicí verze knihovny C-Runtime, které používají iterátory nesprávně, mohou začít zobrazit výrazy Assert za běhu. Chcete-li zakázat tyto kontrolní výrazy, je nutné definovat _HAS_ITERATOR_DEBUGGING (nahrazeno [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po aplikaci Visual Studio 2010) na hodnotu 0. Další informace najdete v tématu [Podpora ladění iterátoru](../standard-library/debug-iterator-support.md) .

## <a name="visual-c-net-2003-breaking-changes"></a>Nejnovější C++ změny v jazyce Visual .NET 2003

### <a name="compiler"></a>Přepínač

- Pravé kulaté závorky se teď vyžadují pro definovanou direktivu preprocesoru (c2004).

- Explicitní specializace již nenaleznou parametry šablony z primární šablony ([Chyba kompilátoru C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- K chráněnému členu (n) lze přistupovat pouze prostřednictvím členské funkce třídy (B), která dědí z třídy (A), z níž je (n) členem ([Chyba kompilátoru C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Vylepšené kontroly dostupnosti v kompilátoru teď zjišťují nepřístupné základní třídy ([Chyba kompilátoru C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- Výjimka nemůže být zachycena v případě, že destruktor nebo kopírovací konstruktor je nepřístupný (C2316).

- Výchozí argumenty u ukazatelů na funkce už nejsou povolené ([Chyba kompilátoru C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Statický datový člen nejde inicializovat prostřednictvím odvozené třídy ([Chyba kompilátoru C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- Inicializace **typedef** není povolená standardem a teď generuje chybu kompilátoru ([Chyba kompilátoru C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- hodnota **bool** je nyní správného typu ([Chyba kompilátoru C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- UDC teď může vytvořit nejednoznačnost pomocí přetížených operátorů ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Další výrazy se teď považují za platné konstanty ukazatele s hodnotou null ([Chyba kompilátoru C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- Šablona < > nyní vyžaduje umístění, kde by ji kompilátor dřív znamenal ([Chyba kompilátoru C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- Explicitní specializace členské funkce mimo třídu není platná, pokud již byla funkce explicitně specializovaná prostřednictvím specializace třídy šablony ([Chyba kompilátoru C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Parametry šablony bez typu s plovoucí desetinnou čárkou již nejsou povoleny ([Chyba kompilátoru C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- Šablony třídy nejsou povoleny jako argumenty typu šablony (C3206).

- Názvy funkcí Friend již nejsou zavedeny do obsahujícího oboru názvů ([Chyba kompilátoru C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Kompilátor již nebude v makru (C4002) přijímat nadbytečné čárky.

- Objekt POD typu konstruovaný s inicializátorem formuláře () bude inicializován jako výchozí (C4345).

- TypeName se nyní vyžaduje, pokud je závislý název považován za typ ([Upozornění kompilátoru (úroveň 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Funkce, které byly nesprávně považovány za specializace šablon, již nejsou považovány za (C4347).

- Statické datové členy nelze inicializovat prostřednictvím odvozené třídy (C4356).

- Specializace šablony třídy musí být definovaná dřív, než se použije v návratovém typu ([Upozornění kompilátoru (úroveň 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Kompilátor nyní hlásí nedosažitelný kód (C4702).

## <a name="see-also"></a>Viz také:

[Novinky pro vizuál C++ v aplikaci Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
