---
title: Historie změn Visual C++ 2003–2015
ms.date: 10/21/2019
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: a045b04e5a57e9963b2ad374fbdfdd533bde0a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374166"
---
# <a name="visual-c-change-history-2003---2015"></a>Historie změn Visual C++ 2003–2015

Tento článek popisuje všechny nejnovější změny z Visual Studio 2015 vrací do Visual Studio 2003 a v tomto článku termíny "nové chování" nebo "nyní" naleznete Visual Studio 2015 a novější. Termíny "staré chování" a "před" odkazují na Visual Studio 2013 a dřívější verze.

Informace o nejnovější verzi sady Visual Studio najdete v tématu [Co je nového pro Visual C++ v sadě Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) a vylepšení [shody v jazyce Visual C++ v sadě Visual Studio](../overview/cpp-conformance-improvements.md).

> [!NOTE]
> Mezi Visual Studio 2015 a Visual Studio 2017 nejsou žádné binární změny.

Při upgradu na novou verzi sady Visual Studio může dojít kompilace nebo runtime chyby v kódu, který dříve zkompiloval a správně spuštěn. Změny v nové verzi, které způsobují tyto problémy jsou označovány jako *narušující změny*a obvykle jsou vyžadovány změnami ve standardu jazyka C++, podpisy funkcí nebo rozložení objektů v paměti.

Chcete-li se vyhnout chybám za běhu, které je obtížné zjistit a diagnostikovat, doporučujeme nikdy staticky propojit binární soubory zkompilované pomocí jiné verze kompilátoru. Když upgradujete projekt EXE nebo DLL, nezapomeňte také provést upgrade knihoven, na které odkazuje. Nepředávají CRT (C Runtime) nebo C++ Standardní knihovna (C++ Standardní knihovna) typy mezi binárními soubory, včetně Knihovny DLL, zkompilované pomocí různých verzí kompilátoru. Další informace naleznete [v tématu Potenciální chyby předávání crt objekty přes hranice dll](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Nikdy byste neměli psát kód, který závisí na konkrétním rozložení pro objekt, který není rozhraní com nebo objekt POD. Pokud takový kód napíšete, musíte zajistit, aby po upgradu fungoval. Další informace naleznete v tématu [Přenositelnost na hranicích ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Kromě toho probíhající vylepšení shody kompilátoru může někdy změnit způsob, jakým kompilátor chápe váš existující zdrojový kód. Můžete například najít nové nebo různé chyby během sestavení nebo dokonce behaviorální rozdíly v kódu, který byl dříve sestaven a zdálo se, že běží správně. Přestože tato vylepšení nejsou porušení změny, jako jsou popsány v tomto dokumentu, budete muset provést změny ve zdrojovém kódu k vyřešení těchto problémů:

- [C Runtime (CRT) Změny rozdělení knihovny](#BK_CRT)

- [Standardní změny rozdělení standardní knihovny c++ a c++](#BK_STL)

- [Změny rozdělení knihovny MFC a knihovny ATL](#BK_MFC)

- [Změny přelomení za běhu souběžnosti](#BK_ConcRT)

## <a name="visual-studio-2015-conformance-changes"></a><a name="VC_2015"></a>Změny shody sady Visual Studio 2015

### <a name="c-runtime-library-crt"></a><a name="BK_CRT"></a>C Runtime knihovna (CRT)

#### <a name="general-changes"></a>Obecné změny

- **Refaktorované binární soubory**

   Knihovna CRT byla refaktorována do dvou různých binárních souborů: Univerzální CRT (ucrtbase), který obsahuje většinu standardních funkcí, a Knihovna běhu VC (vcruntime). Knihovna vcruntime obsahuje funkce související s kompilátorem, jako je například zpracování výjimek a vnitřní objekty. Pokud používáte výchozí nastavení projektu, pak tato změna nemá vliv na vás, protože propojovací aplikace bude automaticky používat nové výchozí knihovny. Pokud jste nastavili vlastnost **Propojovací** služba projektu Ignorovat všechny výchozí `/NODEFAULTLIB` **knihovny** na **Ano** nebo používáte možnost propojovacího programu na příkazovém řádku, je nutné aktualizovat seznam knihoven (ve **vlastnosti Další závislosti)** tak, aby zahrnovala nové refaktorované knihovny. Nahraďte starou knihovnu CRT (libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib) ekvivalentními refaktorovanými knihovnami. Pro každou ze dvou refaktorovaných knihoven existují statické (.lib) a dynamické (.dll) verze a verze (bez přípony) a ladicí verze (s příponou "d"). Dynamické verze mají knihovnu importu, se kterou je propojen. Dvě refaktorované knihovny jsou Universal CRT, konkrétně ucrtbase.dll nebo ucrtbase.lib, ucrtbased.dll nebo ucrtbased.lib a knihovna Runtime VC, libvcruntime.lib, vcruntime*verze*.dll, libvcruntimed.lib a*verze*vcruntimed .dll. *Verze* v sadě Visual Studio 2015 a Visual Studio 2017 je 140. Viz [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

#### <a name="localeh"></a>\<locale.h>

- **localeconv**

   Funkce [localeconv](../c-runtime-library/reference/localeconv.md) deklarovaná v souboru locale.h nyní funguje správně, pokud je povoleno [národní prostředí pro vlákno.](../parallel/multithreading-and-locales.md) V předchozích verzích knihovny by `lconv` tato funkce vrátit data pro globální národní prostředí, nikoli národní prostředí vlákna.

   Pokud používáte národní prostředí pro vlastní vlákno, `localeconv`měli byste zkontrolovat použití aplikace . Pokud váš kód předpokládá, že `lconv` vrácená data jsou pro globální národní prostředí, měli byste je opravit.

#### <a name="mathh"></a>\<math.h>

- **C++ přetížení funkcí matematické knihovny**

   V předchozích \<verzích math.h> definovány některé, ale ne všechny přetížení Jazyka C++ pro funkce matematické knihovny. Zbytek přetížení byly v \<cmath> záhlaví. Kód, který \<zahrnoval pouze math.h> může mít problémy s řešením přetížení funkce. Nyní c++ přetížení byly odebrány z \<math.h> \<a jsou nalezeny pouze v cmath>.

   Chcete-li vyřešit chyby, zahrňte \<cmath> \<získat deklarace funkcí, které byly odebrány z math.h>. Tyto funkce byly přesunuty:

  - `double abs(double)` a `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - `float`a `long double` `acos`verze funkcí s `acosh`pohyblivou desetinnou tál `erfc` `exp`, `exp2` `expm1` `fabs` `fdim` `floor` `fma` `fmax` `fmin` `fmod` `frexp` `hypot` `ilogb` `ldexp` `lgamma` `llrint` `llround` `log` `log10` `log1p` `log2` `lrint` `sin` `sinh` `sqrt` `tan` `tanh` `tgamma` `round` `scalbln` `scalbn`, , , , `ceil` `copysign` `cos` `cosh` `erf` `atan` `atanh` `atan2` `cbrt`, , , `lround` `modf` `nearbyint` `nexttoward`, , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , `remainder` `remquo` `rint` `nextafter` `asin` `asinh``trunc`

  Pokud máte kód, `abs` který používá s plovoucí \<desetinnou čárkou typu, který obsahuje pouze math.h> záhlaví, verze s plovoucí desetinnou čárkou již nebude k dispozici. Volání nyní překládá `abs(int)`na , i s argumentem s plovoucí desetinnou tázkou, který způsobuje chybu:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Oprava tohoto upozornění je nahradit volání `abs` `abs`s plovoucí desetinnou `fabs` tácek `fabsf` em , například pro \<dvojitý argument nebo pro `abs`argument float nebo zahrnout cmath> záhlaví a nadále používat .

- **Shody s plovoucí desetinnou táhovostí**

   Mnoho změn v matematické knihovně bylo provedeno s cílem zlepšit shodu se specifikacemi přílohy F IEEE-754 a C11 s ohledem na zvláštní vstupy případů, jako jsou NANs a nekonečna. Například tiché vstupy NaN, které byly často považovány za chyby v předchozích verzích knihovny, již nejsou považovány za chyby. Viz [norma IEEE 754](https://standards.ieee.org/standard/754-2008.html) a příloha F [normy C11](https://www.iso.org/standard/57853.html).

   Tyto změny nezpůsobí chyby v době kompilace, ale mohou způsobit, že se programy budou chovat odlišně a správněji podle standardu.

- **FLT_ROUNDS**

   V sadě Visual Studio 2013 FLT_ROUNDS makro rozbalené na konstantní výraz, který byl nesprávný, protože režim zaokrouhlení lze konfigurovat za běhu, například voláním fesetround. Makro FLT_ROUNDS je nyní dynamické a správně odráží aktuální režim zaokrouhlení.

#### <a name="new-and-newh"></a>\<nové> \<a new.h>

- **nové a odstranit**

   V předchozích verzích knihovny byly nové a funkce odstranění definované implementací exportovány z knihovny DLL knihovny runtime (například msvcr120.dll). Tyto funkce operátoru jsou nyní vždy staticky propojeny do binárních souborů, a to i při použití knihoven DLL knihovny runtime.

   Toto není narušující změna pro nativní nebo smíšený kód (`/clr`), ale pro kód kompilovaný jako [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md), tato změna může způsobit selhání kompilace kódu. Pokud kompilujete kód `/clr:pure`jako `#include <new>` `#include <new.h>` , budete muset přidat nebo obejít chyby sestavení z důvodu této změny. Tato`/clr:pure` možnost je v sadě Visual Studio 2015 již zastaralá a v sadě Visual Studio 2017 není podporována. Kód, který musí být "čistý" by měl být portován do jazyka C#.

#### <a name="processh"></a>\<process.h>

- **_beginthread a _beginthreadex**

   Funkce [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) a [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) nyní obsahuje odkaz na modul, ve kterém je definován postup podprocesu po dobu trvání vlákna. To pomáhá zajistit, že moduly nejsou uvolněny, dokud vlákno bude spuštěno až do dokončení.

#### <a name="stdargh"></a>\<stdarg.h>

- **va_start a referenční typy**

   Při kompilaci kódu Jazyka C++ [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) nyní ověřuje v době kompilace, že argument předán není typu odkazu. Argumenty referenčního typu jsou zakázány standardem C++.

#### <a name="stdioh-and-conioh"></a><a name="stdio_and_conio"></a>\<stdio.h> \<a conio.h>

- **Řada funkcí printf a scanf jsou nyní definovány jako vzaúšátkové.**

   Definice všech funkcí `printf` a `scanf` byly přesunuty do \<> stdio.h, \<conio.h> a dalších hlavičkách CRT. Tato změna přerušení vede k chybě propojovacího programu (LNK2019, nevyřešený externí symbol) pro všechny programy, které deklarovaly tyto funkce místně bez zahrnutí příslušných záhlaví CRT. Pokud je to možné, měli byste aktualizovat kód tak, `#include <stdio.h>`aby zahrnoval hlavičky CRT (to znamená přidat) a vložené funkce, ale pokud nechcete upravit kód tak, aby zahrnoval tyto soubory záhlaví, alternativním řešením je přidat další knihovnu do vstupu propojovacího programu, legacy_stdio_definitions.lib.

   Chcete-li přidat tuto knihovnu do vstupu propojovacího aplikace v rozhraní IDE, otevřete kontextovou nabídku pro uzel projektu, `legacy_stdio_definitions.lib` zvolte **Vlastnosti** **projektu** , zvolte **Propojovací systém**a upravte vstup **propojovacího prostředí,** který chcete přidat do seznamu oddělených středníkem.

   Pokud váš projekt propojení se statickými knihovnami, které byly zkompilovány s verzí sady Visual Studio dříve než 2015, propojovací aplikace může hlásit nevyřešený externí symbol. Tyto chyby mohou odkazovat `_iob_func`na vnitřní definice \<pro `_iob`, nebo související dovozy pro některé stdio.h> funkce ve formě _imp_\*. Společnost Microsoft doporučuje překompilovat všechny statické knihovny s nejnovější verzí kompilátoru jazyka C++ a knihoven při upgradu projektu. Pokud je knihovna knihovnou jiného výrobce, pro kterou není k dispozici zdroj, měli byste požádat třetí stranu o aktualizovaný binární soubor nebo zapouzdřit použití této knihovny do samostatné knihovny DLL, kterou zkompilujete se starší verzí kompilátoru a knihoven.

    > [!WARNING]
    > Pokud se připojujete k sada Windows SDK 8.1 nebo starší, může dojít k těmto nevyřešeným chybám externích symbolů. V takovém případě byste měli chybu vyřešit přidáním legacy_stdio_definitions.lib do vstupu linkeru, jak je popsáno výše.

   Chcete-li odstranit nevyřešené chyby symbolů, můžete zkusit pomocí [dumpbin.exe](../build/reference/dumpbin-reference.md) prozkoumat symboly definované v binárním souboru. Chcete-li zobrazit symboly definované v knihovně, vyzkoušejte následující příkazový řádek.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **dostane a _getws**

   Funkce [gets](../c-runtime-library/gets-getws.md) a [_getws](../c-runtime-library/gets-getws.md) byly odebrány. Funkce gets byla odebrána z c standardní knihovny v C11, protože ji nelze bezpečně použít. Funkce _getws byla rozšíření společnosti Microsoft, které bylo ekvivalentní gets, ale pro široké řetězce. Jako alternativy k těmto funkcím zvažte použití [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md)a [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets a _cgetws**

   Funkce [_cgets](../c-runtime-library/cgets-cgetws.md) a [_cgetws](../c-runtime-library/cgets-cgetws.md) byly odebrány. Jako alternativy k těmto funkcím zvažte použití [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) a [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Formátování Nekonečna a NaN**

   V předchozích verzích by byly nekonečna a nany formátovány pomocí sady ověřovacích řetězců specifických pro MSVC.

  - Nekonečno: 1,#INF

  - Tichá NaN: 1,#QNAN

  - Signalizace NaN: 1.#SNAN

  - Neurčitý NaN: 1,#IND

  Některý z těchto formátů může být předponou znaménkem a může být formátován mírně odlišně v závislosti na šířce a přesnosti pole (někdy s neobvyklými efekty, například `printf("%.2f\n", INFINITY)` by tisk 1.#J, protože #INF by byl "zaokrouhlen" na dvoumístnou přesnost). C99 zavedla nové požadavky na to, jak mají být nekonečna a NaN formátovány. Implementace MSVC nyní splňuje tyto požadavky. Nové řetězce jsou následující:

  - Nekonečno: inf

  - Quiet NaN: nan

  - Signalizace NaN: nan(snan)

  - Neurčitý NaN: nan(ind)

  Kterákoli z nich může být předponou značkou. Pokud je použit specifikátor formátu s velkými písmeny (%F místo %f),`INF` jsou `inf`řetězce vytištěny velkými písmeny ( místo ), jak je požadováno.

  Funkce [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) byly upraveny tak, aby analyzovat tyto nové řetězce, `printf` takže `scanf`tyto řetězce nyní round-trip through a .

- **Formátování a analýza plovoucích bodů**

   Byly zavedeny nové algoritmy formátování a analýzy plovoucí chod, aby se zlepšila správnost. Tato změna ovlivňuje [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) rodiny funkcí, stejně jako funkce jako [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Staré formátovací algoritmy by generovaly pouze omezený počet číslic a pak by vyplnily zbývající desetinná místa nulou. Obvykle mohou generovat řetězce, které by round-trip zpět na původní hodnotu s plovoucí desetinnou čárkou, ale nebyly skvělé, pokud jste chtěli přesnou hodnotu (nebo nejbližší desítkové reprezentace). Nové formátovací algoritmy generují tolik číslic, kolik je potřeba k reprezentaci hodnoty (nebo k vyplnění zadané přesnosti). Jako příklad zlepšení; zvažte výsledky při tisku velkého výkonu dvou:

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

   Staré algoritmy analýzy by zvážit pouze až 17 významné číslice ze vstupního řetězce a by zahodit zbytek číslic. Tento přístup je dostatečná k vytvoření blízké aproximace hodnoty reprezentované řetězcem a výsledek je obvykle velmi blízko správně zaoblený výsledek. Nová implementace bere v úvahu všechny přítomné číslice a vytváří správně zaokrouhlený výsledek pro všechny vstupy (až 768 číslic na délku). Kromě toho tyto funkce nyní respektují režim zaokrouhlení (kontrolovatelné pomocí fesetround).  Toto je potenciálně narušující změny chování, protože tyto funkce mohou výstup různých výsledků. Nové výsledky jsou vždy správnější než staré výsledky.

- **Šestnáctkové a nekonečno/NaN analýza plovoucí desetinné čárky**

   Algoritmy analýzy plovoucí desetinné čárky budou nyní analyzovat šestnáctkové řetězce s plovoucí desetinnou čárkou (například řetězce generované specifikátory formátu %a a a `printf` %A) a všechny řetězce infinity a NaN, které jsou generovány funkcemi, jak je popsáno výše.

- **%A a %nulové odsazení**

   Specifikátory formátu %a a %A formátují číslo s plovoucí desetinnou čárkou jako šestnáctkovou mantisu a binární exponent. V předchozích verzích by `printf` funkce nesprávně nula pad řetězce. Například `printf("%07.0a\n", 1.0)` by tisk 00x1p +0, kde by měl tisknout 0x01p +0. Tato chyba byla opravena.

- **Přesnost %A a %a**

   Výchozí přesnost specifikátorů formátu %A a %a byla v předchozích verzích knihovny 6. Výchozí přesnost je nyní 13 pro shodu s c standard.

   Jedná se o změnu chování za běhu ve výstupu libovolné funkce, která používá formátovací řetězec s %A nebo %a. Ve starém chování může být výstup pomocí specifikátoru %A "1.1A2B3Cp+111". Nyní je výstup pro stejnou hodnotu "1.1A2B3C4D5E6F7p+111". Chcete-li získat staré chování, můžete zadat přesnost, například %. 6A. Viz [Specifikace přesnosti](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **%F specifikátor**

   Specifikátor formátu /převodu %F je nyní podporován. Je funkčně ekvivalentní specifikátoru formátu %f s tím rozdílem, že nekonečna a nans jsou formátovány velkými písmeny.

   V předchozích verzích implementace slouží k analyzovat F a N jako modifikátory délky. Toto chování pochází z doby segmentovaných adresních prostorů: tyto modifikátory délky byly použity k označení ukazatelů vzdálených a blízkých, jako v %Fp nebo %Ns. Toto chování bylo odebráno. Pokud je %F zjištěn, je nyní považován za specifikátor formátu %F. Pokud je zjištěn %N, je nyní považován za neplatný parametr.

- **Exponent formátování**

   The %e and %E format specifiers format a floating point number as a decimal mantissa and exponent. Specifikatory formátu %g a %G také v některých případech formátují čísla v tomto formuláři. V předchozích verzích crt by vždy generovat řetězce s třímístné exponenty. Například `printf("%e\n", 1.0)` by vytisknout 1.000000e+000, což bylo nesprávné. C vyžaduje, aby pokud exponent je reprezentovat pouze jednu nebo dvě číslice, pak pouze dvě číslice mají být vytištěny.

   V sadě Visual Studio 2005 byl přidán přepínač globální shody: [_set_output_format](../c-runtime-library/set-output-format.md). Program může tuto funkci volat s argumentem _TWO_DIGIT_EXPONENT, aby umožnil odpovídající exponentní tisk. Výchozí chování bylo změněno na exponentní režim standardy.

- **Ověření formátovacího řetězce**

   V předchozích `printf` verzích `scanf` a funkce by tiše přijmout mnoho neplatný formát řetězce, někdy s neobvyklé efekty. Například %hlhlhld by bylo považováno za %d. Všechny neplatné formátovací řetězce jsou nyní považovány za neplatné parametry.

- **ověření řetězce režimu fopen**

   V předchozích verzích `fopen` rodina funkcí tiše přijala některé řetězce `r+b+`neplatného režimu, například . Řetězce neplatného režimu jsou nyní rozpoznány a považovány za neplatné parametry.

- **_O_U8TEXT režim**

   Funkce [_setmode](../c-runtime-library/reference/setmode.md) nyní správně hlásí režim pro datové proudy otevřené in_O_U8TEXT režimu. V předchozích verzích knihovny by hlásit takové datové proudy jako otevření v _O_WTEXT.

   Toto je narušující změna, pokud váš kód interpretuje _O_WTEXT režim pro datové proudy, kde kódování je UTF-8. Pokud vaše aplikace nepodporuje UTF_8, zvažte přidání podpory pro toto stále běžnější kódování.

- **snprintf a vsnprintf**

   Funkce [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) a [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) jsou nyní implementovány. Starší kód často za předpokladu, definice makro verze těchto funkcí, protože nebyly implementovány knihovnou CRT, ale již nejsou potřebné v novějších verzích. Pokud [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) nebo [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) je definován \<jako makro před zahrnutím stdio.h>, kompilace nyní selže s chybou, která označuje, kde bylo makro definováno.

   Za normálních okolností je oprava tohoto `snprintf` problému `vsnprintf` odstranit všechny deklarace nebo v uživatelském kódu.

- **tmpnam generuje použitelné názvy souborů**

   V předchozích `tmpnam` verzích `tmpnam_s` a funkce generované názvy souborů v kořenovém adresáři jednotky (například \sd3c.). Tyto funkce nyní generují použitelné cesty názvů souborů v dočasném adresáři.

- **Zapouzdření souboru**

   V předchozích verzích byl celý typ \<SOUBORu veřejně definován v stdio.h>, takže bylo možné, aby se uživatelský kód dostal do SOUBORU a upravil jeho vnitřní. Knihovna byla změněna tak, aby skryla podrobnosti implementace. Jako součást této změny FILE, \<jak je definováno v stdio.h> je nyní neprůhledný typ a jeho členy jsou nepřístupné z mimo CRT sám.

- **_outp a _inp**

   Funkce [_outp](../c-runtime-library/outp-outpw-outpd.md), [_outpw](../c-runtime-library/outp-outpw-outpd.md), [_outpd](../c-runtime-library/outp-outpw-outpd.md), [_inp](../c-runtime-library/inp-inpw-inpd.md), [_inpw](../c-runtime-library/inp-inpw-inpd.md)a [_inpd](../c-runtime-library/inp-inpw-inpd.md) byly odebrány.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>, \<malloc.h \<> a sys/stat.h>

- **strtof a wcstof**

   Funkce `strtof` `wcstof` a se `errno` nepodařilo nastavit eRANGE, když hodnota nebyla rezivovatelná jako float. Tato chyba byla specifická pro tyto dvě funkce; `strtod` `wcstod`nebyly `strtold` `wcstold` ovlivněny . Tento problém byl opraven a je změna za běhu přerušení.

- **Zarovnané alokační funkce**

   V předchozích verzích by zarovnány alokační funkce (`_aligned_malloc`, `_aligned_offset_malloc`, atd.) tiše přijímaly požadavky na blok se zarovnáním 0. Požadované zarovnání musí být mocninu dvou, což neplatí pro nulu. Požadované zarovnání 0 je nyní považováno za neplatný parametr. Tento problém byl opraven a je změna za běhu přerušení.

- **Funkce haldy**

   Funkce `_heapadd` `_heapset`, `_heapused` a byly odebrány. Tyto funkce byly nefunkční od CRT byl aktualizován na haldu systému Windows.

- **malá halda**

   Možnost `smallheap` propojení byla odebrána. Viz [Možnosti propojení](../c-runtime-library/link-options.md).

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   Podpis funkce `wcstok` byl změněn tak, aby odpovídal tomu, co je požadováno standardem C. V předchozích verzích knihovny byl podpis této funkce:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Používá interní kontext pro vlákno ke sledování stavu mezi voláními, jak je tomu u . `strtok` Funkce má nyní `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)`podpis a vyžaduje, aby volající předat kontext jako třetí argument funkce.

   Byla `_wcstok` přidána nová funkce se starým podpisem pro usnadnění přenosu. Při kompilaci kódu Jazyka C++ je také `wcstok` vřádkové přetížení, které má starý podpis. Toto přetížení je deklarováno jako zastaralé. V kódu C, můžete `_wcstok` define_CRT_NON_CONFORMING_WCSTOK způsobit použití `wcstok`místo .

#### <a name="timeh"></a>\<time.h>

- **clock**

   V předchozích verzích byla funkce [hodiny](../c-runtime-library/reference/clock.md) implementována pomocí rozhraní API systému Windows [GetSystemTimeAsFileTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime). S touto implementací byla funkce hodin citlivá na systémový čas, a proto nebyla nutně monotónní. Funkce hodiny byla znovu implementována z hlediska [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) a je nyní monotónní.

- **fstat a _utime**

   V předchozích verzích [_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)a [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) funkce nesprávně zpracovávají letní čas. Před Visual Studio 2013 všechny tyto funkce nesprávně upraveny standardní čas, jako by byly v letním čase.

   V sadě Visual Studio 2013 byl problém vyřešen v **_stat** rodiny funkcí, ale podobné problémy v **fstat** a **_utime** rodiny funkcí nebyly opraveny. Tato částečná oprava vedla k problémům kvůli nekonzistenci mezi funkcemi. **Fstat** a **_utime** rodiny funkcí byly nyní opraveny, takže všechny tyto funkce nyní zpracovávají letní čas správně a konzistentně.

- **asctime**

   V předchozích verzích by funkce [asctime](../c-runtime-library/reference/asctime-wasctime.md) vymezila jednociferné dny s počáteční nulou, například: `Fri Jun 06 08:00:00 2014`. Specifikace vyžaduje, aby tyto dny byly doplněny `Fri Jun  6 08:00:00 2014`úvodním prostorem, jako v . Tento problém byl opraven.

- **strftime a wcsftime**

   Funkce `strftime` `wcsftime` a nyní podporují specifikátory formátu %C, %D, %e, %F, %g, %G, %h, %n, %r, %r, %t, %T, %u a %V. Modifikátory E a O jsou navíc analyzovány, ale ignorovány.

   Specifikátor formátu %c je určen jako vytvoření "vhodné reprezentace data a času" pro aktuální národní prostředí. V národním prostředí C musí být toto `%a %b %e %T %Y`znázornění stejné jako ve `asctime`stejném formuláři, který vytváří . V předchozích verzích specifikátor formátu %c nesprávně `MM/DD/YY HH:MM:SS` formátoval časy pomocí reprezentace. Tento problém byl opraven.

- **timespec a TIME_UTC**

   Hlavička \<time.h> nyní `timespec` definuje `timespec_get` typ a funkci ze standardu C11. Kromě toho je nyní definováno `timespec_get` TIME_UTC makro pro použití s funkcí. Tato aktualizace je narušující změna pro kód, který má konfliktní definici pro některý z těchto identifikátorů.

- **CLOCKS_PER_SEC**

   Makro CLOCKS_PER_SEC se nyní rozbalí na `clock_t`celé číslo typu , jak to vyžaduje jazyk C.

#### <a name="c-standard-library"></a><a name="BK_STL"></a>Standardní knihovna C++

Pokud byte chtěli povolit nové optimalizace a kontroly ladění, implementace standardní knihovny C++ záměrně neumožňuje binární kompatibilitu mezi verzemi. Proto při použití standardní knihovny C++ nelze objektové soubory a statické knihovny, které jsou kompilovány pomocí různých verzí, směšovat v jednom binárním souboru (EXE nebo DLL) a objekty standardní knihovny C++ nelze předávat mezi binárními soubory, které jsou kompilovány pomocí různých verzí. Takovéto směšování objektů vyvolává chyby linkeru týkající se neshod _MSC_VER. (_MSC_VER je makro, které obsahuje hlavní verzi kompilátoru – například 1800 pro Visual Studio 2013.) Tato kontrola nemůže rozpoznat míchání dll a nelze zjistit míchání, které zahrnuje Visual Studio 2008 nebo starší.

- **Standardní knihovna c++ obsahuje soubory**

   Některé změny byly provedeny do struktury zahrnutí v záhlaví standardní knihovny C++. Záhlaví standardní knihovny jazyka C++ se mohou vzájemně začleňovat nespecifikovanými způsoby. Obecně byste měli napsat kód tak, aby pečlivě zahrnuje všechny hlavičky, které potřebuje podle standardu C++ a nespoléhá na které hlavičky standardní knihovny C++ obsahují další hlavičky standardní knihovny C++. Díky tomu je kód přenosný napříč verzemi a platformami. Alespoň dvě změny záhlaví ve Visual Studiu 2015 ovlivní uživatelský kód. Za \<prvé, řetězec \<> již neobsahuje> iterátoru. Za \<druhé, n-tice> nyní deklaruje `std::array` bez \<zahrnutí všech> pole, které mohou přerušit kód prostřednictvím následující kombinace konstrukce kódu: váš kód má proměnnou s názvem "pole" a máte using-direktivu "pomocí oboru názvů std;" a zahrnout hlavičku standardní knihovny Jazyka C++ (například \<funkční>), která zahrnuje \<> n-tice, která nyní deklaruje `std::array`.

- **steady_clock**

   Chrono \<> implementace [steady_clock](../standard-library/steady-clock-struct.md) se změnila tak, aby splňovala požadavky standardu C++ na stálost a monotónnost. `steady_clock`Je nyní založen na [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) a `high_resolution_clock` `steady_clock`je nyní typedef pro . V důsledku toho v `steady_clock::time_point` sadě Visual Studio `chrono::time_point<steady_clock>`je nyní typedef pro ; to však nemusí být nutně případ pro jiné implementace.

- **alokátory a const**

   Nyní požadujeme, aby srovnání rovnosti a nerovnosti alokátorů akceptovně akceptovalo konstituční argumenty na obou stranách. Pokud alokátory definují tyto operátory takto,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   pak byste je měli aktualizovat a prohlásit je za členy const:

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **const prvky**

   Standard C++ má vždy zakázané kontejnery const\<prvků (například\<vector const T> nebo set const T>). Visual Studio 2013 a dříve přijal takové kontejnery. V aktuální verzi tyto kontejnery nepodaří zkompilovat.

- **std::alokátor::deallocate**

   V sadě Visual Studio 2013 a starší `std::allocator::deallocate(p, n)` ignoroval argument předaný pro *n*.  Standard Jazyka C++ vždy vyžadoval, aby *se n* rovnalo hodnotě předané jako první argument `allocate` vyvolání, které bylo vráceno. *p* V aktuální verzi je však zkontrolována hodnota *n.* Kód, který předává argumenty pro *n,* které se liší od toho, co vyžaduje standard, může za běhu chybět.

- **hash_map a hash_set**

   Nestandardní soubory \<hlaviček \<hash_map> a hash_set> se v sadě Visual Studio 2015 zastaraly a budou odebrány v budoucí verzi. Místo \<toho \<použijte unordered_map> a unordered_set>.

- **komparátory a operátor()**

   Asociativní kontejnery \<(mapa> rodiny) nyní vyžadují, aby jejich komparátory měly operátory volání funkce const callable. Následující kód v deklaraci třídy komparátoru se nyní nepodaří zkompilovat:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Chcete-li tuto chybu vyřešit, změňte deklaraci funkce na:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **vlastnosti typu**

   Staré názvy vlastností typu ze starší verze konceptu c++ standardu byly odebrány. Tyto byly změněny v Jazyce C ++ 11 a byly aktualizovány na hodnoty C++ 11 v sadě Visual Studio 2015. V následující tabulce jsou uvedeny staré a nové názvy.

   |Starý název|Nové jméno|
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

- **spuštění::any a launch::zásady synchronizace**

   Nestandardní `launch::any` a `launch::sync` zásady byly odstraněny. Místo toho `launch::any`pro `launch:async | launch:deferred`, použijte . Pro `launch::sync`použití `launch::deferred`. Viz [spuštění výčtu](../standard-library/future-enums.md#launch).

#### <a name="mfc-and-atl"></a><a name="BK_MFC"></a>Knihovny MFC a knihovny ATL

- **Knihovna MFC (Microsoft Foundation Classes)**

   již není součástí "Typické" instalace sady Visual Studio z důvodu jeho velké velikosti. Chcete-li nainstalovat knihovnu MFC, zvolte možnost **Vlastní** instalace v nastavení Visual Studia 2015. Pokud už máte nainstalovanou Visual Studio 2015, můžete nainstalovat knihovnu MFC dalším spuštěním nastavení **sady Visual Studio.** Zvolte možnost **Vlastní** instalace a pak zvolte **Třídy microsoft foundation**. Nastavení **sady Visual Studio** můžete spustit v ovládacím **panelu** **Programy a funkce**nebo z instalačního média.

   Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.

#### <a name="concurrency-runtime"></a><a name="BK_ConcRT"></a>Doba runtime souběžnosti

- **Výnosové makro ze systému Windows.h v konfliktu s souběžnou měnou::Kontext::Výnos**

   Souběžnost Runtime dříve `#undef` používá k nedefinování yield makro, aby se zabránilo konfliktům `concurrency::Context::Yield` mezi yield makro definované v Windows.h h a funkce. Tato `#undef` byla odebrána a byl přidán nový nekonfliktní ekvivalentní volání rozhraní API [souběžnosti::Context::YieldExecution.](../parallel/concrt/reference/context-class.md#yieldexecution) Chcete-li obejít konflikty s Yield, můžete `YieldExecution` buď aktualizovat kód `Yield` pro volání funkce místo, nebo obklopit název funkce s závorky na místech volání, jako v následujícím příkladu:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Vylepšení shody kompilátoru v sadě Visual Studio 2015

Při upgradu kódu z předchozích verzí může dojít také k chybám kompilátoru, které jsou z důvodu zlepšení shody provedené v sadě Visual Studio 2015. Tato vylepšení neporušují binární kompatibilitu z dřívějších verzí sady Visual Studio, ale mohou vytvářet chyby kompilátoru, kde žádné byly emitovány dříve. Další informace naleznete v [tématu Visual C++ What's New 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

V sadě Visual Studio 2015 probíhající vylepšení shody kompilátoru může někdy změnit způsob, jakým kompilátor chápe váš existující zdrojový kód. V důsledku toho může dojít k nové nebo různé chyby během sestavení nebo dokonce behaviorální rozdíly v kódu, který dříve sestavené a zdálo se, že správně spustit.

Naštěstí tyto rozdíly mají malý nebo žádný vliv na většinu zdrojového kódu. Pokud zdrojový kód nebo jiné změny jsou potřebné k řešení těchto rozdílů, opravy mají tendenci být malé a přímočaré. Zahrnuli jsme mnoho příkladů dříve přijatelného zdrojového kódu, který může být nutné změnit *(před)* a opravy, které je opravují *(po)*.

Přestože tyto rozdíly mohou ovlivnit zdrojový kód nebo jiné artefakty sestavení, nemají vliv na binární kompatibilitu mezi aktualizacemi verzí sady Visual Studio. *Narušující změna* je závažnější a může ovlivnit binární kompatibilitu, ale tyto druhy binární kompatibility přestávky dojít pouze mezi hlavní verze sady Visual Studio, například mezi Visual Studio 2013 a Visual Studio 2015. Informace o narušujících změnách, ke kterým došlo mezi Visual Studio 2013 a Visual Studio 2015, naleznete v [tématu Visual Studio 2015 Změny shody](#VC_2015).

- [Vylepšení shody v sadě Visual Studio 2015](#VS_RTM)

- [Vylepšení shody v aktualizaci 1](#VS_Update1)

- [Vylepšení shody v aktualizaci 2](#VS_Update2)

- [Vylepšení shody v aktualizaci 3](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a>Vylepšení shody v sadě Visual Studio 2015

- /Zc:forScope- volba

   Možnost `/Zc:forScope-` kompilátoru je zastaralé a budou odebrány v budoucí verzi.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Obvykle tato možnost byla použita k povolení nestandardní kód, který používá proměnné smyčky po bodu, kde podle standardu, měly být mimo rozsah. Bylo to nutné pouze tehdy, když jste zkompilovali s `/Za` možností, protože bez `/Za`, použití proměnné smyčky for po skončení smyčky je vždy povoleno. Pokud se nestaráte o shodu standardů (například pokud váš kód není určen k `/Za` přenositelnosti na jiné kompilátory), můžete tuto možnost vypnout (nebo nastavit vlastnost **Zakázat rozšíření jazyka** na **ne).** Pokud vám záleží na psaní přenosný, standardy kompatibilní kód, měli byste přepsat kód tak, aby odpovídalstandard přesunutím deklarace těchto proměnných do bodu mimo smyčky.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg`možnost kompilátoru

   Možnost `/Zg` kompilátoru (Generovat prototypy funkcí) již není k dispozici. Tato možnost kompilátoru byla dříve zastaralá.

- Již nelze spustit testy částí s C++/CLI z příkazového řádku s mstest.exe. Místo toho použijte vstest.console.exe. Viz [možnosti příkazového řádku VSTest.Console.exe](/visualstudio/test/vstest-console-options).

- **proměnlivé klíčové slovo**

   Specifikátor třídy **proměnlivé** úložiště již není povolen v místech, kde dříve zkompiloval bez chyby. Nyní kompilátor poskytuje chybu C2071 (třída neplatné úložiště). Podle standardu lze **proměnlivý** specifikátor použít pouze na názvy datových členů třídy a nelze jej použít na názvy deklarované jako const nebo statické a nelze je použít na referenční členy.

   Zvažte například následující kód:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Předchozí verze kompilátoru přijal to, ale nyní kompilátor dává následující chybu:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Chcete-li chybu opravit, odeberte redundantní **proměnlivé** klíčové slovo.

- **char_16_t a char32_t**

   Již nelze použít `char16_t` `char32_t` nebo jako aliasy v **typedef**, protože tyto typy jsou nyní považovány za předdefinované. Bylo běžné, že uživatelé `char16_t` a `char32_t` autoři knihovny definovali a jako aliasy `uint16_t` a `uint32_t`, resp.

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

   Chcete-li aktualizovat kód, odeberte deklarace **typedef** a přejmenujte všechny ostatní identifikátory, které se srazí s těmito názvy.

- **Parametry šablony bez typu**

   Určitý kód, který zahrnuje parametry šablony bez typu, je nyní správně zkontrolován na kompatibilitu typů, když zadáte explicitní argumenty šablony. Například následující kód zkompilován bez chyby v předchozích verzích sady Visual Studio.

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

   Aktuální kompilátor správně poskytuje chybu, protože typ parametru šablony neodpovídá argumentu šablony (parametr je ukazatel na člen const, ale funkce f není const):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Chcete-li tuto chybu vyřešit v kódu, ujistěte se, že typ argumentu šablony, který používáte, odpovídá deklarovanému typu parametru šablony.

- **__declspec(zarovnat)**

   Kompilátor již přijímá `__declspec(align)` funkce. Tato konstrukce byla vždy ignorována, ale nyní vytváří chybu kompilátoru.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Chcete-li tento `__declspec(align)` problém vyřešit, odeberte z deklarace funkce. Vzhledem k tomu, že to nemělo žádný účinek, jeho odstranění nic nemění.

- **Zpracování výjimek**

   Existuje několik změn zpracování výjimek. Za prvé, objekty výjimky musí být kopírovatelné nebo pohyblivé. Následující kód zkompilován ve Visual Studiu 2013, ale nekompiluje se v Sadě Visual Studio 2015:

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

   Problém je, že konstruktor kopie je soukromý, takže objekt nelze zkopírovat, jak se stane v normálním průběhu zpracování výjimky. Totéž platí, když je konstruktor kopie **deklarován explicitní**.

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

   Chcete-li aktualizovat kód, ujistěte se, že konstruktor kopie pro objekt výjimky je **veřejný** a není označen **explicitní**.

   Zachycení výjimky podle hodnoty také vyžaduje, aby objekt výjimky byl kopírovatelný. Následující kód zkompilován ve Visual Studiu 2013, ale nekompiluje se v Sadě Visual Studio 2015:

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

   Tento problém můžete vyřešit změnou typu parametru pro **catch** na odkaz.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Řetězcové literály následované makry**

   Kompilátor nyní podporuje literály definované uživatelem. V důsledku toho řetězcové literály následované makry bez jakýchkoli zasahujících mezer jsou interpretovány jako literály definované uživatelem, které mohou způsobit chyby nebo neočekávané výsledky. Například v předchozích kompilátorech byl úspěšně zkompilován následující kód:

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

   Kompilátor interpretoval tento kód jako literál řetězce "hello" následovaný makry, které je rozbaleno do "tam", a pak byly dva literály řetězce zřetězeny do jednoho. V sadě Visual Studio 2015 kompilátor interpretuje tuto sekvenci jako literál `_x` definovaný uživatelem, ale protože neexistuje žádná odpovídající uživatelem definovaná literál defined, poskytuje chybu.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi literál řetězce a makro.

- **Sousední řetězcové literály**

   Podobně jako předchozí, z důvodu souvisejících změn v analýzě řetězců, sousední řetězcové literály (literály řetězce široký nebo úzký znak) bez jakýchkoli mezer byly interpretovány jako jeden zřetězený řetězec v předchozích verzích Visaul C++. V sadě Visual Studio 2015 je nyní nutné přidat mezery mezi dva řetězce. Například následující kód musí být změněn:

    ```cpp
    char * str = "abc""def";
    ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi dva řetězce:

    ```cpp
    char * str = "abc" "def";
    ```

- **Umístění nové a odstranit**

   Byla provedena změna operátoru **delete,** aby byl shodou se standardem C++ 14. Podrobnosti o změně standardů lze nalézt na [C ++ velikosti Deallocation](https://isocpp.org/files/papers/n3778.html). Změny přidat formu globální **delete** operátor, který má parametr velikosti. Narušující změna je, že pokud jste dříve používali operátor **odstranit** se stejným podpisem (aby **odpovídaly umístění nového** operátoru), obdržíte chybu kompilátoru (C2956, ke kterému dochází v místě, kde se používá umístění nové, protože to je pozice v kódu, kde kompilátor se pokusí identifikovat odpovídající **operátor delete).**

   Funkce `void operator delete(void *, size_t)` byla operátor **odstranění umístění** odpovídající umístění **nové** funkce `void * operator new(size_t, size_t)` v C ++ 11. S C ++ 14 velikosti deallocation, tato funkce odstranění je nyní *obvyklé funkce mezera umístění* (globální operátor **odstranění).** Standard vyžaduje, aby v případě, že použití umístění nové vyhledá odpovídající odstranit funkci a najde obvyklou funkci deallocation, program je špatně-tvořil.

   Předpokládejme například, že váš kód definuje **nové umístění** a **odstranění umístění**:

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   K problému dochází z důvodu shody v podpisech funkce mezi operátorem **odstranění umístění,** který jste definovali, a novým operátorem **odstranění** globální velikosti. Zvažte, zda můžete použít `size_t` jiný typ než pro **jakékoli umístění nové** a **odstranit** operátory. Typ `size_t` **typedef** je závislý na kompilátoru; je to **typedef** pro **nepodepsané int** v MSVC. Dobrým řešením je použít výčtový typ, jako je tento:

    ```cpp
    enum class my_type : size_t {};
    ```

   Potom změňte definici **umístění nové** a **odstranit** použít tento `size_t`typ jako druhý argument namísto . Budete také muset aktualizovat volání umístění nové předat nový typ (například `static_cast<my_type>` pomocí převést z celé číslo hodnoty) a aktualizovat definici **nové** a **odstranit** přetypování zpět na typ celé ho. Není nutné použít **výčtu** pro toto; typ třídy `size_t` s členem bude také fungovat.

   Alternativním řešením je, že byste mohli být schopni odstranit **umístění nové** úplně. Pokud váš kód používá **nové umístění** k implementaci fondu paměti, kde argument umístění je velikost objektu, který je přidělen nebo odstraněn, pak velikost imlokační funkce může být vhodné nahradit vlastní kód fondu paměti a můžete se zbavit umístění funkce a stačí použít vlastní dva **argumenty odstranit** operátor místo umístění funkce.

   Pokud nechcete aktualizovat kód okamžitě, můžete se vrátit ke starému chování pomocí `/Zc:sizedDealloc-`možnosti kompilátoru . Pokud použijete tuto možnost, funkce odstranění dvěma argumenty neexistují a nezpůsobí konflikt s operátorem **odstranění umístění.**

- **Členové dat Unie**

   Datové členy sjednocení již nemohou mít typy odkazů. Následující kód byl úspěšně zkompilován v sadě Visual Studio 2013, ale v sadě Visual Studio 2015 vytvoří chybu.

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

   Předchozí kód vytváří následující chyby:

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   Chcete-li tento problém vyřešit, změňte typy odkazů na ukazatel nebo hodnotu. Změna typu na ukazatel vyžaduje změny v kódu, který používá pole sjednocení. Změna kódu na hodnotu by změnila data uložená v unii, což má vliv na jiná pole, protože pole v typech sjednocení sdílejí stejnou paměť. V závislosti na velikosti hodnoty může také změnit velikost unie.

- Anonymní odbory jsou nyní více v souladu se standardem. Předchozí verze kompilátoru vygenerovaly explicitní konstruktor a destruktor pro anonymní sjednocení. Tyto funkce generované kompilátorem jsou odstraněny v sadě Visual Studio 2015.

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

   Předchozí kód generuje následující chybu v sadě Visual Studio 2015:

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   Chcete-li tento problém vyřešit, zadejte vlastní definice konstruktoru nebo destruktoru.

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

- **Odbory s anonymními strukturami**

   Aby bylo možné v souladu se standardem, chování za běhu se změnilo pro členy anonymnístruktury v sjednocení. Konstruktor pro členy anonymní struktury v unii již není implicitně volána při vytvoření takového sjednocení. Destruktor pro členy anonymní struktury v unii již není implicitně volána, když unie přejde mimo rozsah. Vezměme si následující kód, ve kterém unie U obsahuje anonymní strukturu, která obsahuje strukturu pojmenovaný člen S, který má destruktor.

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

   V sadě Visual Studio 2013 je při vytvoření sjednocení volán konstruktor pro S a destruktor pro S je volán při vyčištění zásobníku pro funkci f. Ale v Sadě Visual Studio 2015 konstruktor a destruktor se nenazývají. Kompilátor poskytuje upozornění o této změně chování.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Chcete-li obnovit původní chování, pojmenujte anonymní strukturu. Chování runtime neanonymních struktur je stejné, bez ohledu na verzi kompilátoru.

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

   Případně zkuste přesunout kód konstruktoru a destruktoru do nových funkcí a přidat volání těchto funkcí z konstruktoru a destruktoru pro sjednocení.

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

- **Rozlišení šablony**

   Byly provedeny změny překladu názvů šablon. V jazyce C++ při zvažování kandidátů pro rozlišení názvu může být případ, že jeden nebo více názvů v úvahu jako potenciální shody vytvoří neplatný vytvoření instance šablony. Tyto neplatné instance obvykle nezpůsobují chyby kompilátoru, což je princip známý jako SFINAE (Selhání nahrazení není chyba).

   Nyní pokud SFINAE vyžaduje kompilátor k vytvoření instance specializace šablony třídy, pak všechny chyby, ke kterým dojde během tohoto procesu jsou chyby kompilátoru. V předchozích verzích by kompilátor tyto chyby ignoroval. Zvažte například následující kód:

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

   Pokud kompilujete s aktuálníkompilátor, zobrazí se následující chyba:

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

   Důvodem je, že v okamžiku první vyvolání `D` is_base_of třída nebyla dosud definována.

   V tomto případě je oprava není používat tyto vlastnosti typu, dokud třída byla definována. Pokud přesunete definice `B` a `D` na začátek souboru kódu, chyba je vyřešena. Pokud jsou definice v souborech hlaviček, zkontrolujte pořadí příkazů include pro soubory hlaviček a ujistěte se, že všechny definice tříd jsou zkompilovány před použitím problematických šablon.

- **Kopírovat konstruktory**

   V obou Visual Studio 2013 a Visual Studio 2015 kompilátor generuje konstruktor kopie pro třídu, pokud tato třída má uživatelem definovaný konstruktor přesunutí, ale žádný uživatelem definovaný konstruktor kopírování. V Dev14 je tento implicitně generovaný konstruktor kopie také označen "= delete".

<!--From here to VS_Update1 added 04/21/2017-->

- **main deklarované jako extern "C" nyní vyžaduje návratový typ.**

   Následující kód nyní vytváří C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Chcete-li chybu opravit, přidejte návratový typ:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **typename není v inicializátoru člena povolen**

   Následující kód nyní vytváří C2059:

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

   Chcete-li chybu `typename` opravit, odeberte z inicializátoru:

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **Třída úložiště na explicitní specializace je ignorována.**

   V následujícím kódu je specifikátor třídy statického úložiště ignorován.

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

- **Konstanta použitá v static_assert uvnitř šablony třídy se vždy nezdaří.**

   Následující kód způsobí, `static_assert` že se vždy nezdaří:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Chcete-li tento problém vyřešit, zalomte hodnotu **do struktury**:

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

- **Pravidla vynucená pro předávací prohlášení. (Platí pouze pro C.)**

   Následující kód nyní vytváří C2065:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Chcete-li tento problém vyřešit, přidejte správné dopředné deklarace:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Konzistentnější vynucení typů ukazatelů funkcí**

   Následující kód nyní vytváří C2197:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Nejednoznačná volání přetížených funkcí**

   Následující kód nyní vytváří C266: 'N::bind': nejednoznačné volání přetížené funkce

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

   Chcete-li chybu opravit, můžete plně `bind: N::bind(...)`kvalifikovat volání . Pokud je však tato změna manifestprostředu nedeklarované identifikátor (C2065), pak může být vhodné opravit pomocí **pomocí** deklarace místo.

   Tento vzor se stává často s ComPtr a další typy v oboru `Microsoft::WRL` názvů.

- **Opravit nesprávnou adresu**

   Následující kód nyní vytváří C2440: '=': nelze převést z 'type *' na 'type'. Chcete-li chybu opravit, změňte &(typ) na (typ) a (&f()) na (f()).

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

- **Literál řetězce je konstantní pole**

   Následující kód nyní vytváří C2664: 'void f(void *)': nelze převést argument 1 z 'const char (*)[2]' na 'void *'

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Chcete-li chybu opravit, změňte `const void*`typ parametru funkce `h` na , nebo změňte tělo aplikace tak, aby vypadalo takto:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **Řetězce UDL c++11**

   Následující kód nyní vytváří chybu C3688: neplatná literálová přípona "L"; Literál operátor nebo literál operátor šablony "operátor "L" nebyl nalezen

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Chcete-li chybu opravit, změňte kód a přidejte mezeru:

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

   Ve výše uvedeném příkladu `MACRO` již není analyzovánjako dva tokeny (řetězec následovaný makra). Nyní je analyzován jako jeden token UDL. Totéž platí pro L""L"", který byl analyzován dříve jako L"" a L"", a je nyní analyzován jako L""L a "".

   Pravidla zřetězení řetězců byla rovněž uvedena do souladu s normou, což znamená, že L"a" "b" je ekvivalentní L"ab". Předchozí edice sady Visual Studio nepřijaly zřetězení řetězců s různou šířkou znaků.

- **Prázdný znak c++11 byl odebrán.**

   Následující kód nyní vytváří chybu C2137: konstanta prázdného znaku

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Chcete-li chybu opravit, změňte kód tak, aby byl null explicitní:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **Výjimky knihovny MFC nemohou být zachyceny hodnotou, protože nejsou kopírovatelné**

   Následující kód v aplikaci knihovny MFC nyní způsobuje chybu C2316: 'D': nelze zachytit jako destruktor a/nebo konstruktor kopie jsou nepřístupné nebo odstraněné

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

   Chcete-li opravit kód, můžete změnit `catch (const D &)` blok catch na, ale lepším řešením je obvykle použít makra MFC TRY/CATCH.

- **alignof je nyní klíčové slovo**

   Následující kód nyní vytváří chybu C2332: 'class': chybějící název značky. Chcete-li opravit kód, musíte přejmenovat třídu nebo, pokud třída provádí stejnou práci jako **alignof**, stačí nahradit třídu novým klíčovým slovem.

    ```cpp
    class alignof{}
    ```

- **constexpr je nyní klíčové slovo**

   Následující kód nyní vytváří chybu C2059: syntaktická chyba: ')'. Chcete-li opravit kód, je nutné přejmenovat všechny funkce nebo názvy proměnných, které se nazývají "constexpr".

    ```cpp
    int constexpr() {return 1;}
    ```

- **Pohyblivé typy nemohou být const**

   Pokud funkce vrátí typ, který je určen k přesunutí, jeho návratový typ by neměl být **const**.

- **Odstraněné konstruktory kopírování**

   Následující kód nyní vytváří C2280 'S:S(S &&)': pokus o odkaz na odstraněnou funkci:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Chcete-li chybu opravit, použijte `S2`přímou inicializaci pro :

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Převod na ukazatel funkce je generován pouze v případě, že nezachycuje lambda**

   Následující kód vytváří C2664 v sadě Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Chcete-li chybu opravit, odeberte `=` ji ze seznamu zachycení.

- **Nejednoznačná volání zahrnující operátory převodu**

   Následující kód nyní vytváří chybu C2440: 'typ přetypované': nelze převést z 'S2' na 'S1':

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

   Následující kód nyní vytváří chybu C2593: 'operátor =' je nejednoznačný:

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

- **Oprava neplatné inicializace kopírování v nestatické inicializaci datového prvku (NSDMI)**

   Následující kód nyní vytváří chybu C2664: 'S1::S1(S1 &&)': nelze převést argument 1 z 'bool' na 'const S1 &':

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

   Následující kód nyní vytváří C2248: 'S::S': nemůže získat přístup k soukromému členu deklarovanému ve třídě 'S':

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

   Chcete-li chybu opravit, přidejte deklaraci přítele do `S2` : `S`

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Výchozí ctor lambda je implicitně odstraněn**

   Následující kód nyní vytváří chybu C3497: nelze vytvořit instanci lambda:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Chcete-li chybu opravit, odeberte potřebu volání výchozího konstruktoru. Pokud lambda nezachytí nic, pak může být přetypována na ukazatel funkce.

- **Lambdas s odstraněným operátorem přiřazení**

   Následující kód nyní vytváří chybu C2280:

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

   Chcete-li chybu opravit, nahraďte lambda třídou functor nebo odeberte potřebu použít operátor přiřazení.

- **Pokus o přesunutí objektu pomocí odstraněného konstruktoru kopie**

   Následující kód nyní vytváří chybu C2280: 'pohyblivý::moveable(const movité &)': pokus o odkaz na odstraněnou funkci

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

   Chcete-li chybu `std::move` opravit, použijte místo toho:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **Místní třída nemůže odkazovat na jinou místní třídu definovanou později ve stejné funkci.**

   Následující kód nyní vytváří chybu C2079: 's' používá nedefinovanou strukturu 'main::S2'

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

- **Nelze volat chráněné základny ctor v těle odvozené ctor.**

   Následující kód nyní vytváří chybu C2248: 'S1::S1': nelze získat přístup k chráněnému členu deklarovanému ve třídě S1.

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

   Chcete-li opravit `S2` chybu, v `S1()` odebrat volání z konstruktoru a v případě potřeby umístit do jiné funkce.

- **{}zabraňuje převodu na ukazatel**

   Následující kód nyní vytváří C2439 'S::p': člen nelze inicializovat

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Chcete-li chybu opravit, odeberte `0` závorky z okolí nebo použijte **nullptr** místo, jak je znázorněno v tomto příkladu:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Nesprávné definice maker a použití s závorky**

   Následující příklad nyní vytváří chybu C2008: ';': neočekávané v definici makra

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Chcete-li problém vyřešit, změňte horní řádek na`#define A();`

   Následující kód vytváří chybu C2059: syntaktická chyba: ')'

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Chcete-li kód opravit, odeberte mezeru mezi a ().

   Následující kód vytváří chybu C2091: funkce vrátí funkci:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Chcete-li chybu opravit, odeberte závorky po příkazu DECLARE v s: `DECLARE;`.

   Následující kód vytváří chybu C2062: zadejte 'int' neočekávané

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Chcete-li problém `A` vyřešit, definujte takto:

    ```cpp
    #define A int
    ```

- **Extra parens v prohlášeních**

   Následující kód vytváří chybu C2062: zadejte 'int' neočekávané

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Chcete-li chybu opravit, odeberte `j`závorky kolem . Pokud jsou závorky potřebné pro přehlednost, použijte **typedef**.

- **Konstruktory generované kompilátorem a __declspec(novtable)**

   V sadě Visual Studio 2015 je zvýšená pravděpodobnost, že kompilátor generované vložkové konstruktory abstraktní třídy s virtuální základní třídy může vystavit nesprávné použití `__declspec(novtable)` při použití v kombinaci s `__declspec(dllimport)`.

- **auto vyžaduje jeden výraz v přímé inicializaci seznamu**

   Následující kód nyní vytváří chybu C3518: 'testPositions': v kontextu přímé inicializace seznamu typ pro 'auto' lze odvodit pouze z jednoho výrazu inicializátoru

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Chcete-li chybu opravit, jednou z `testPositions` možností je inicializovat následujícím způsobem:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Kontrola typů vs. odkazy na typy pro is_convertible**

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

   Chcete-li chybu opravit, změňte `static_assert` tak, `D` aby `B2`porovnávala ukazatele a :

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **__declspec (novtable) prohlášení musí být konzistentní**

   `__declspec`deklarace musí být konzistentní ve všech knihovnách. Následující kód nyní vytvoří pravidlo jedné definice (ODR) porušení:

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

### <a name="conformance-improvements-in-update-1"></a><a name="VS_Update1"></a>Vylepšení shody v aktualizaci 1

- **Soukromé virtuální základní třídy a nepřímá dědičnost**

   Předchozí verze kompilátoru povoleno odvozené třídy volat členské funkce `private virtual` jeho nepřímo odvozené základní třídy. Toto staré chování bylo nesprávné a neodpovídá standardu C++. Kompilátor již přijímá kód napsaný tímto způsobem a v důsledku toho vydává chybu kompilátoru C2280.

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

   \-nebo -

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Přetížený operátor nový a odstranit operátor**

   Předchozí verze kompilátoru povoleno nečlen **operátor nový** a nečlen operátor **odstranit deklarovat** statické a deklarovat v oborech názvů než globální obor názvů.  Toto staré chování vytvořilo riziko, že program nebude volat **novou** nebo **odstranit** implementaci operátoru, kterou programátor zamýšlel, což vedlo k tichému chybnému chování za běhu. Kompilátor již přijímá kód napsaný tímto způsobem a místo toho vydává chybu kompilátoru C2323.

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

   Navíc i když kompilátor neposkytuje konkrétní diagnostiku, inline operátor **new** je považován za neutvářený.

- **Volání typu *operátoru*()" (uživatelem definovaný převod) u typů mimo třídu**

   Předchozí verze kompilátoru povoleno *'typ*operátoru ()' být volána na typy mimo třídu, zatímco tiše ignoruje. Toto staré chování vytvořilo riziko tichého generování chybného kódu, což vedlo k nepředvídatelnému chování za běhu. Kompilátor již přijímá kód napsaný tímto způsobem a místo toho vydává chybu kompilátoru C2228.

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

- **Redundantní název typu v propracovaných specifikátorech typu**

   Předchozí verze kompilátoru povolené **typename** v propracované matyonu typu, ale kód napsaný tímto způsobem je sémanticky nesprávné. Kompilátor již přijímá kód napsaný tímto způsobem a místo toho vydává chybu kompilátoru C3406.

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

- **Zadejte odpočet polí ze seznamu inicializačních zařízení**

   Předchozí verze kompilátoru nepodporovaly typ odpočtu polí ze seznamu inicializátoru. Kompilátor nyní podporuje tento formulář odpočtu typu a v důsledku toho volání šablon funkcí pomocí seznamů inicializátoru může být nyní nejednoznačné nebo může být vybráno jiné přetížení než v předchozích verzích kompilátoru. Chcete-li tyto problémy vyřešit, program musí nyní explicitně určit přetížení, které programátor zamýšlel.

   Když toto nové chování způsobí, že řešení přetížení zvážit další kandidát, který je stejně dobrý jako historický kandidát, volání se stane nejednoznačný a kompilátor problémy chyba kompilátoru C2668 jako výsledek.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   Příklad 1: Nejednoznačné volání přetížené funkce (před)

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

   Když toto nové chování způsobí přetížení řešení zvážit další kandidát, který je lepší shoda než historický kandidát, volání jednoznačně řeší nového kandidáta, což způsobuje změnu chování programu, který je pravděpodobně jiný, než programátor zamýšlel.

   Příklad 2: změna rozlišení přetížení (před)

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

   Příklad 2: změna rozlišení přetížení (po)

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

   Předchozí verze kompilátoru odebrala některá upozornění týkající se **příkazy switch;** tato varování byla nyní obnovena. Kompilátor nyní vydává obnovená upozornění a upozornění týkající se konkrétních případů (včetně výchozího případu) jsou nyní vydávána na řádku obsahujícím problematický případ, nikoli na posledním řádku příkazu switch. V důsledku nyní vydávání těchto varování na různých řádcích než v `#pragma warning(disable:####)` minulosti, varování dříve potlačena pomocí již nemusí být potlačeny tak, jak bylo zamýšleno. Chcete-li potlačit tato varování, jak bylo `#pragma warning(disable:####)` zamýšleno, může být nutné přesunout směrnice na řádek nad první případ problematický. Následují obnovená upozornění:

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

   Příklad C4063 (po)

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

   Příklady dalších obnovených upozornění jsou uvedeny v jejich dokumentaci.

- **#include: použití specifikátoru nadřazeného adresáře '..' v cestě (ovlivňuje** pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistily použití nadřazeného specifikátoru adresáře ... v názvu směrnic. `#include` Kód napsaný tímto způsobem je obvykle určen k zahrnutí záhlaví, které existují mimo projekt nesprávně pomocí cest relativní chod projektu. Toto staré chování vytvořilo riziko, že by program mohl být zkompilován zahrnutím jiného zdrojového souboru, než programátor zamýšlel, nebo že tyto relativní cesty nebudou přenosné do jiných prostředí sestavení. Kompilátor nyní detekuje a upozorní programátora napsaný takto a vydá volitelné upozornění kompilátoru C4464, pokud je povoleno.

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

   Navíc i když kompilátor neposkytuje konkrétní diagnostiku, doporučujeme také, aby nadřazený specifikátor adresáře ".." by neměl být používán k určení adresářů zahrnutí projektu.

- **#pragma optimize() rozšiřuje za konec souboru záhlaví** (týká se `/Wall` `/WX`pouze)

   Předchozí verze kompilátoru nezjistily změny nastavení příznaku optimalizace, které unikly souboru záhlaví obsaženému v jednotce překladu. Kompilátor nyní detekuje a upozorní programátora na kód napsaný tímto způsobem a vydá volitelné upozornění kompilátoru C4426 v umístění problematicky `#include`, pokud je povoleno. Toto upozornění je vydáno pouze v případě, že změny v konfliktu s příznaky optimalizace nastavit argumenty příkazového řádku kompilátoru.

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

- **Neshoda #pragma varování (push)** a **#pragma warning(pop)** (týká se `/Wall` `/WX`pouze)

   Předchozí verze kompilátoru nezjistily `#pragma warning(push)` změny `#pragma warning(pop)` stavu spárované se změnami stavu v jiném zdrojovém souboru, který je zřídka určen. Toto staré chování vytvořilo riziko, že program bude kompilován s jinou sadou upozornění povolenou, než programátor zamýšlel, což by mohlo vést k tichému špatnému chování za běhu. Kompilátor nyní detekuje a upozorní programátora napsaný takto a vydá volitelné upozornění kompilátoru C5031 v umístění odpovídající `#pragma warning(pop)`, pokud je povoleno. Toto upozornění zahrnuje poznámku odkazující na umístění odpovídajícího #pragma upozornění(push).

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

   Ačkoli neobvyklé, kód napsaný tímto způsobem je někdy úmyslné. Takto napsaný kód je `#include` citlivý na změny v pořadí; pokud je to možné, doporučujeme, aby soubory zdrojového kódu spravovaly stav upozornění samostatným způsobem.

- **Bezkonkurenční #pragma varování (push)** (týká se `/Wall` `/WX`pouze )

   Předchozí verze kompilátoru nezjistily `#pragma warning(push)` neodpovídající změny stavu na konci jednotky překladu. Kompilátor nyní detekuje a upozorní programátora kódu napsaného tímto způsobem a vydá volitelné upozornění kompilátoru `#pragma warning(push)`C5032 v umístění neodpovídající , pokud je povoleno. Toto upozornění je vydáno pouze v případě, že v jednotce překladu nejsou žádné chyby kompilace.

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

- **Další upozornění mohou být vydána v důsledku vylepšeného sledování stavu #pragma varování**

   Předchozí verze kompilátoru sledovány #pragma změny stavu upozornění nedostatečně dobře vydat všechna zamýšlená upozornění. Toto chování vytvořilo riziko, že některá upozornění budou účinně potlačena za jiných okolností, než programátor zamýšlel. Kompilátor nyní `#pragma warning` sleduje stav robustněji `#pragma warning` – zejména v souvislosti se změnami stavu uvnitř šablon – a volitelně vydává nová upozornění C5031 a C5032, která mají programátorovi pomoci najít nezamýšlené použití `#pragma warning(push)` a `#pragma warning(pop)`.

   V důsledku vylepšeného `#pragma warning` sledování změn stavu mohou být nyní vydána upozornění dříve nesprávně potlačená nebo upozornění týkající se problémů, které byly dříve chybně diagnostikovány.

- **Vylepšená identifikace nedostupného kódu**

   Změny standardní knihovny jazyka C++ a vylepšená možnost vsazených volání funkcí přes předchozí verze kompilátoru mohou kompilátoru umožnit, aby dokázal, že určitý kód je nyní nedostupný. Toto nové chování může mít za následek nové a častěji vydané instance upozornění C4720.

    ```Output
    warning C4720: unreachable code
    ```

   V mnoha případech toto upozornění může být vydáno pouze při kompilaci s povolené optimalizace, protože optimalizace může vložit více volání funkce, eliminovat redundantní kód nebo jinak umožnit určit, že určitý kód je nedostupný. Zjistili jsme, že nové instance varování C4720 se často vyskytují v **try/catch** bloky, zejména ve vztahu k použití [std::find](../standard-library/algorithm-functions.md#find).

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

### <a name="conformance-improvements-in-update-2"></a><a name="VS_Update2"></a>Vylepšení shody v aktualizaci 2

- **Další varování a chyby mohou být vydány v důsledku částečné podpory výrazu SFINAE**

   Předchozí verze kompilátoru neanalyzují určité druhy výrazů uvnitř specifikátorů **decltype** z důvodu nedostatečné podpory výrazu SFINAE. Toto staré chování bylo nesprávné a neodpovídá standardu C++. Kompilátor nyní analyzuje tyto výrazy a má částečnou podporu výrazu SFINAE z důvodu průběžné zlepšení shody. V důsledku toho kompilátor nyní vydává upozornění a chyby nalezené ve výrazech, které předchozí verze kompilátoru nebyly analyzovat.

   Když toto nové chování analyzuje **decltype** výraz, který obsahuje typ, který ještě nebyl deklarován, kompilátor problémy chyba kompilátoru C2039 jako výsledek.

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

   Příklad 1 (po)

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

   Když toto nové chování analyzuje **decltype** výraz, který chybí nezbytné použití klíčového slova **typename** k určení, že závislý název je typ, kompilátor vydá upozornění kompilátoru C4346 spolu s chybou kompilátoru C2923.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Příklad 2: závislý název není typ (před)

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

- `volatile`**členské proměnné brání implicitně definovaným konstruktorům a operátorům přiřazení**

   Předchozí verze kompilátoru umožnily třídě, která má **nestálé** členské proměnné, aby byly automaticky generovány výchozí konstruktory kopírování/přesunutí a výchozí operátory přiřazení kopírování/přesunutí. Toto staré chování bylo nesprávné a neodpovídá standardu C++. Kompilátor nyní považuje třídu, která má **nestálé** členské proměnné, za netriviální operátory konstrukce a přiřazení, což zabraňuje automatickému generování výchozích implementací těchto operátorů. Pokud je taková třída členem unie (nebo anonymní unie uvnitř třídy), konstruktory copy/move a operátory přiřazení copy/move unie (nebo třídy obsahující anonymní sjednocení) budou implicitně definovány jako odstraněné. Pokus o vytvoření nebo zkopírování sjednocení (nebo třídy obsahující anonymní sjednocení) bez jejich explicitního definování je chyba a kompilátor vystaví chybu kompilátoru C2280 jako výsledek.

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

- **Statické členské funkce nepodporují cv-qualifiers.**

   Předchozí verze Visual Studia 2015 povoleno statické členské funkce mít cv kvalifikátory. Toto chování je způsobeno regrese v Sadě Visual Studio 2015 a Visual Studio 2015 Update 1; Visual Studio 2013 a předchozí verze kompilátoru odmítnout kód napsaný tímto způsobem. Chování Visual Studio 2015 a Visual Studio 2015 Update 1 je nesprávné a neodpovídá standardu C++.  Visual Studio 2015 Update 2 odmítne kód napsaný tímto způsobem a problémy chyba kompilátoru C2511 místo.

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

   Příklad(po)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **Dopředné prohlášení výčtu není v kódu WinRT povoleno** (týká se `/ZW`pouze)

   Kód zkompilovaný pro prostředí Windows Runtime (WinRT) neumožňuje **předsunout typy výčtu** deklarované, podobně jako `/clr` při kompilaci spravovaného kódu Jazyka C++ pro rozhraní .Net Framework pomocí přepínače kompilátoru. Toto chování zajišťuje, že velikost výčtu je vždy známa a může být správně promítána do systému typu WinRT. Kompilátor odmítne kód napsaný tímto způsobem a vydá chybu kompilátoru C2599 spolu s chybou kompilátoru C3197.

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

- **Přetížený operátor bez členů new a delete operátoru nemusí být deklarovány jako inline** (Úroveň 1 (`/W1`) ve výchozím nastavení)

   Předchozí verze kompilátoru nevydávají upozornění, když jsou funkce odstranění operátoru, které nejsou členy, deklarovány jako vepříné. Kód napsaný tímto způsobem je špatně tvarované (není vyžadována žádná diagnostika) a může způsobit problémy s pamětí vyplývající z neshody nové a odstranit operátory (zejména při použití společně s velikosti deallocation), které může být obtížné diagnostikovat. Kompilátor nyní vydává upozornění kompilátoru C4595, který pomáhá identifikovat kód napsaný tímto způsobem.

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

   Oprava kódu, který je napsán tímto způsobem může vyžadovat, aby definice operátoru byly přesunuty ze souboru záhlaví do odpovídajícího zdrojového souboru.

### <a name="conformance-improvements-in-update-3"></a><a name="VS_Update3"></a>Vylepšení shody v aktualizaci 3

- **std::is_convertable nyní detekuje vlastní přiřazení** (standardní knihovna)

   Předchozí verze vlastnosti `std::is_convertable` typu nezjistily správně vlastní přiřazení typu třídy při odstranění jeho konstruktoru kopie nebo soukromé. Nyní `std::is_convertable<>::value` je správně nastavena na **false** při použití na typ třídy s odstraněné nebo soukromé kopie konstruktoru.

   K této změně není přidružena žádná diagnostika kompilátoru.

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

   V předchozích verzích kompilátoru statické kontrolní výrazy v `std::is_convertable<>::value` dolní části tohoto příkladu předat, protože byla nesprávně nastavena na **hodnotu true**. Nyní `std::is_convertable<>::value` je správně nastavena na **false**, což způsobuje statické kontrolní výrazy nezdaří.

- **Výchozí nebo odstraněné triviální kopírování a přesouvání konstruktorů respektuje specifikátory přístupu**

   Předchozí verze kompilátoru nezkontrolovaly specifikátor přístupu výchozí nebo odstraněné triviální kopie a přesunout konstruktory před jejich voláním. Toto staré chování bylo nesprávné a neodpovídá standardu C++. V některých případech toto staré chování vytvořilo riziko tichého generování chybného kódu, což vedlo k nepředvídatelnému chování za běhu. Kompilátor nyní zkontroluje specifikátor přístupu výchozí nebo odstraněné triviální kopie a přesunout konstruktory k určení, zda může být volána, a pokud ne, vydá upozornění kompilátoru C2248 jako výsledek.

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

- **Vyřazení podpory přiřazeného kódu KNIHOVNY ATL** (úroveň 1 (`/W1`) ve výchozím nastavení)

   Předchozí verze kompilátoru podporované přiřazený kód KNIHOVNY ATL. Jako další fáze odebrání podpory pro přiřazený kód KNIHOVNY ATL, který [začal v sadě Visual Studio 2008](../porting/visual-cpp-what-s-new-2003-through-2015.md#whats-new-for-c-in-visual-studio-2008), byl přiřazen kód KNIHOVNY ATL zastaral. Kompilátor nyní vydává upozornění kompilátoru C4467, který pomáhá identifikovat tento druh zastaralého kódu.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Pokud chcete pokračovat v používání přiřazeného kódu KNIHOVNY ATL, dokud nebude podpora `/Wv:18` odebrána z kompilátoru, můžete toto upozornění zakázat předáním argumentů nebo `/wd:4467` příkazového řádku kompilátoru nebo přidáním `#pragma warning(disable:4467)` zdrojového kódu.

   Příklad 1 (před)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Příklad 1 (po)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Někdy můžete potřebovat nebo chcete vytvořit soubor IDL, abyste se vyhnuli použití zastaralých atributů KNIHOVNY ATL, jako v příkladu níže

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

   Nejprve vytvořte soubor *.idl; generovaný soubor vc140.idl lze použít \*k získání souboru .idl obsahujícího rozhraní a poznámky.

   Dále přidejte krok MIDL do sestavení a ujistěte se, že jsou generovány definice rozhraní Jazyka C++.

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

   Potom použijte ATL přímo v souboru implementace, jako v příkladu kódu níže.

   Příklad implementace 2 (po)

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

- **Předkompilované soubory záhlaví (PCH) a neodpovídající #include direktivy** (týká se `/Wall` `/WX`pouze)

   Předchozí verze kompilátoru přijaly `#include` neodpovídající direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilacemi při použití předkompilovaných souborů záhlaví (PCH). Kód napsaný tímto způsobem již není kompilátorem akceptován.   Kompilátor nyní vydává upozornění kompilátoru CC4598, aby pomohl identifikovat neodpovídající `#include` direktivy při použití souborů PCH.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   Příklad (před):

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   Příklad (po)

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **Předkompilované soubory záhlaví (PCH) a neodpovídající zahrnují adresáře** (týká se `/Wall` `/WX`pouze)

   Předchozí verze přijatého kompilátoru neodpovídající`-I`zahrnují argumenty příkazového řádku adresáře ( ) do kompilátoru mezi `-Yc` a `-Yu` kompilace při použití předkompilovaných souborů záhlaví (PCH). Kód napsaný tímto způsobem již není kompilátorem akceptován. Kompilátor nyní vydává upozornění kompilátoru CC4599, aby`-I`pomohl identifikovat neodpovídající argumenty příkazového řádku zahrnutí adresáře ( ) při použití souborů PCH.

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

## <a name="visual-studio-2013-conformance-changes"></a>Změny shody sady Visual Studio 2013

### <a name="compiler"></a>Kompilátoru

- **Konečné** klíčové slovo nyní generuje nevyřešenou chybu symbolu, kde by bylo dříve zkompilován:

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

   V dřívějších verzích nebyla vydána chyba, protože volání bylo **virtuální** volání; nicméně, program by se zhroutí za běhu. Nyní je přiřazena chyba linkeru, protože třída je nyní označena jako konečná. V tomto příkladu chcete-li opravit chybu, by odkaz proti `S2::f`obj, který obsahuje definici .

- Při použití friend funkce v oborech názvů, je nutné znovu deklarovat přítele funkce před odkazovat na něj nebo se zobrazí chyba, protože kompilátor nyní odpovídá ISO C ++ Standard. Například tento příklad již nekompiluje:

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

   Chcete-li opravit tento kód, deklarujte funkci **friend:**

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

- Standard Jazyka C++ neumožňuje explicitní specializaci ve třídě. Přestože kompilátor Microsoft C++ umožňuje v některých případech, v případech, jako je například v následujícím příkladu, je nyní generována chyba, protože kompilátor nepovažuje druhou funkci za specializaci první.

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

- Kompilátor se již nepokouší rozptýlit dvě funkce v následujícím příkladu a nyní vydává chybu:

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

- Před kompilátor byl proveden v souladu s ISO C ++ 11, následující kód by zkompiloval a způsobil `x` přeložit zadejte **int**:

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Tento kód nyní `x` překládá `std::initializer_list<int>` na typ a způsobí chybu na `x` dalším řádku, který se pokusí přiřadit k typu **int**. (Ve výchozím nastavení neexistuje žádný převod.) Chcete-li tento kód opravit, použijte **int** nahradit **auto**:

    ```cpp
    int x = {0};
    int y = x;
    ```

- Agregace inicializace již není povolena, pokud typ hodnoty na pravé straně neodpovídá typu levé hodnoty, která je inicializována, a je vydána chyba, protože standard ISO C ++ 11 vyžaduje jednotnou inicializaci, aby fungovalbez zúžení převodů. Dříve, pokud zužující převod byl k dispozici, [upozornění kompilátoru (úroveň 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) by byly vydány namísto chyby.

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

- Vyhledávání názvů bylo změněno. Následující kód je vyřešen odlišně v kompilátoru C++ v Sadě Visual Studio 2012 a Visual Studio 2013:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   V sadě Visual Studio 2012 výraz `E1` `E1::b` in vyřešen `::E1` v globálním oboru. V sadě Visual Studio `E1` 2013 `E1::b` ve `typedef E2` výrazu překládá na definici v `main()` a má typ `::E2`.

- Rozložení objektu se změnilo. Na platformě x 64 se může v porovnání z předchozími verzemi změnit rozložení objektů třídy. Pokud má **virtuální** funkci, ale nemá základní třídu, která má **virtuální** funkci, objektový model kompilátoru vloží ukazatel do tabulky **virtuálních** funkcí za rozložení datového člena. To znamená, že rozložení nemusí být ve všech případech optimální. V předchozích verzích optimalizace pro x64 by se pokusí zlepšit rozložení pro vás, ale protože se nepodařilo pracovat správně v situacích složitého kódu, byl odebrán v sadě Visual Studio 2013. Podívejte se například na tento kód:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- V Sadě Visual Studio 2013 výsledek `sizeof(S2)` na x64 je 48, ale v předchozích verzích se vyhodnotí na 32. Chcete-li to vyhodnotit na 32 v kompilátoru Visual Studio 2013 C++ pro x64, přidejte fiktivní základní třídu, která má **virtuální** funkci:

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

   Chcete-li najít místa v kódu, které dřívější verze by se pokusili `/W3` optimalizovat, použijte kompilátor z této verze spolu s možností kompilátoru a zapněte upozornění C4370. Příklad:

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

   Před Visual Studio 2013 tento kód výstupy tuto zprávu: "upozornění C4370: 'S2' : rozložení třídy se změnila z předchozí verze kompilátoru z důvodu lepší balení".

   Kompilátor x86 má stejný problém s neoptimálním rozložením ve všech verzích kompilátoru. Pokud je například tento kód je zkompilován pro platformu x86:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Výsledkem `sizeof(S)` je 24. Pokud však použijete řešení uvedené pro x64, může být snížena na 16:

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

Kompilátor Jazyka C++ ve Visual Studiu 2013 detekuje neshody v _ITERATOR_DEBUG_LEVEL, který byl implementován v sadě Visual Studio 2010 a neshody runtimelibrary. K těmto neshodám dochází, `/MT` když jsou `/MTd` smíšené možnosti `/MD` kompilátoru `/MDd` (statické vydání), (statické ladění), (dynamické vydání) a (dynamické ladění).

- Pokud váš kód potvrdí simulované aliasšablony předchozí verze, musíte je změnit. Například místo `allocator_traits<A>::rebind_alloc<U>::other`, nyní musíte `allocator_traits<A>::rebind_alloc<U>`říct . I `ratio_add<R1, R2>::type` když již není nutné a `ratio_add<R1, R2>`nyní doporučujeme, abyste `ratio<N, D>` řekli , první bude stále kompilovat, protože je nutné mít "typ" typedef pro snížený poměr, který bude stejný typ, pokud je již snížena.

- Musíte použít `#include <algorithm>` při `std::min()` volání `std::max()`nebo .

- Pokud váš existující kód používá předchozí verze simulované rozsahové výčty – tradiční unscoped výčty zabalené v oborech názvů – musíte změnit. Například pokud jste odkazoval `std::future_status::future_status`se na typ `std::future_status`, nyní musíte říct . Většina kódu však není ovlivněna – například `std::future_status::ready` stále zkompiluje.

- `explicit operator bool()`je přísnější než operátor nespecifikovaný-bool type(). `explicit operator bool()`umožňuje explicitní převody bool – `shared_ptr<X> sp`například `static_cast<bool>(sp)` `bool b(sp)` dané , a jsou platné – a boolean-testable "kontextové `if (sp)` `!sp`převody" bool –například , , , `sp &&` cokoliv. Nicméně, `explicit operator bool()` zakazuje implicitní převody bool, takže nemůžete `bool b = sp;` říct, a vzhledem k bool `return sp`návratový typ, nemůžete říct .

- Nyní, když jsou implementovány skutečné variadické šablony, _VARIADIC_MAX a související makra nemají žádný vliv. Pokud stále definujete _VARIADIC_MAX, je ignorována. Je-li potvrzen náš nástroj maker určený k podpoře simulovaných variadic šablon jiným způsobem, je nutné změnit váš kód.

- Kromě běžných klíčových slov nyní záhlaví standardní knihovny jazyka C++ zakazují nahrazení maker kontextově **citlivými** klíčovými slovy a **konečná**.

- `reference_wrapper`, `ref()`a `cref()` nyní zakázat vazbu na dočasné objekty.

- \<random> nyní přísně vynucuje své předpoklady kompilace.

- Různé znaky typu standardní knihovny c++ mají předpoklad "T musí být úplný typ". Přestože kompilátor nyní vynucuje tuto podmínku přísněji, nemusí vynutit ve všech situacích. (Vzhledem k tomu, že porušení podmínky standardní knihovny jazyka C++ aktivuje nedefinované chování, standard nezaručuje vynucení.)

- Standardní knihovna jazyka C++ `/clr:oldSyntax`nepodporuje .

- Specifikace C++11 pro common_type<> měla neočekávané a nežádoucí důsledky; zejména provede common_type\<int, int>::type return int&&. Proto kompilátor implementuje navrhované řešení pro knihovnu pracovní skupiny\<problém 2141, který umožňuje common_type int= """>::type return int.

   Jako vedlejší účinek této změny případ identity již\<nefunguje (common_type T> nemusí vždy mít za následek typ T). Toto chování je v souladu s navrhované řešení, ale přeruší jakýkoli kód, který spoléhal na předchozí chování.

   Pokud požadujete znak typu identity, nepoužívejte nestandardní, `std::identity` který je \<definován v type_traits> \<protože to nebude fungovat pro prázdné>. Místo toho implementujte vlastní typovou vlastnost identity tak, aby vyhovovala vašim potřebám. Tady je příklad:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

- **Pouze Visual Studio 2013**: Knihovna mbcs knihovny mfc není součástí sady Visual Studio, protože Unicode je tak populární a použití MBCS výrazně snížila. Tato změna také udržuje MFC lépe zarovnané s Windows SDK, protože mnoho ovládacích prvků a zpráv má pouze kódování Unicode. Pokud však musíte pokračovat v používání knihovny mbcs knihovny knihovny MFC, můžete ji stáhnout ze služby Stažení softwaru MSDN v [knihovně Knihovny mfc multibyte pro sadu Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770). Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.  (Poznámka: Knihovna DLL mbcs je součástí součástí nastavení c++ v sadě Visual Studio 2015 a novější).

- Usnadnění přístupu na pás u pásu karet knihovny MFC se změní.  Namísto jednoúrovňové architektury je nyní hierarchická architektura. Staré chování můžete stále používat `CRibbonBar::EnableSingleLevelAccessibilityMode()`voláním .

- `CDatabase::GetConnect`metoda je odstraněna. Pro zlepšení zabezpečení je připojovací řetězec nyní uložen zašifrován a dešifrován pouze podle potřeby. nelze jej vrátit jako prostý text.  Řetězec lze získat pomocí `CDatabase::Dump` metody.

- Podpis `CWnd::OnPowerBroadcast` společnosti se změní. Podpis tohoto popisovače zprávy se změní na LPARAM jako druhý parametr.

- Podpisy jsou změněny tak, aby vyhovovaly obslužné rutiny zpráv. Seznamy parametrů u následujících funkcí se změnily a používají nově přidané popisovače zpráv ON_WM_ *:

  - `CWnd::OnDisplayChange`změněnna (UINT, int, int) namísto (WPARAM, LPARAM) tak, aby nové ON_WM_DISPLAYCHANGE makro lze použít v mapě zpráv.

  - `CFrameWnd::OnDDEInitiate`změněnna (CWnd*, UINT, UNIT) namísto (WPARAM, LPARAM) tak, aby bylo možné nové ON_WM_DDE_INITIATE makro použít v mapě zpráv.

  - `CFrameWnd::OnDDEExecute`změněnna (CWnd*, HANDLE) namísto (WPARAM, LPARAM) tak, aby bylo možné použít nové makro ON_WM_DDE_EXECUTE v mapě zpráv.

  - `CFrameWnd::OnDDETerminate`změněnna (CWnd*) jako parametr namísto (WPARAM, LPARAM) tak, aby nové makro ON_WM_DDE_TERMINATE bylo možné použít v mapě zpráv.

  - `CMFCMaskedEdit::OnCut`změněnna žádné parametry namísto (WPARAM, LPARAM), takže nové makro ON_WM_CUT lze použít v mapě zpráv.

  - `CMFCMaskedEdit::OnClear`změněnna žádné parametry namísto (WPARAM, LPARAM), takže nové ON_WM_CLEAR makro lze použít v mapě zpráv.

  - `CMFCMaskedEdit::OnPaste`změněnna žádné parametry namísto (WPARAM, LPARAM), takže nové makro ON_WM_PASTE lze použít v mapě zpráv.

- `#ifdef`direktivy v hlavičkových souborech knihovny MFC jsou odebrány. Mnoho `#ifdef` direktiv v souborech hlaviček knihovny MFC související s nepodporovanými verzemi systému Windows (WINVER &lt; 0x0501) jsou odebrány.

- Atl DLL (atl120.dll) je odebrána. Knihovna ATL je nyní poskytována jako záhlaví a statická knihovna (atls.lib).

- Atlsd.lib, atlsn.lib a atlsnd.lib jsou odebrány. Knihovna Atls.lib již nemá závislosti na znakové sadě ani kód specifický pro ladění/vydání. Protože princip funkce je stejný pro Unicode/ANSI i ladění/vydání, je vyžadována pouze jedna verze knihovny.

- Nástroj trasování KNIHOVNY ATL/MFC je odebrán společně s knihovnou DLL knihovny ATL a mechanismus trasování je zjednodušen. Konstruktor `CTraceCategory` nyní přebírá jeden parametr (název kategorie) a makra TRACE volání funkce zasílání ladicích protokolů CRT.

## <a name="visual-studio-2012-breaking-changes"></a>Visual Studio 2012 Nejnovější změny

### <a name="compiler"></a>Kompilátoru

- Možnost `/Yl` kompilátoru byla změněna. Ve výchozím nastavení používá kompilátor tuto možnost, což může za určitých podmínek vést k chybám LNK2011. Další informace naleznete v tématu [/Yl (Inject PCH Reference for Debug Library).](../build/reference/yl-inject-pch-reference-for-debug-library.md)

- V kódu, který je `/clr`kompilován pomocí , **výčtu** třídy klíčové slovo definuje C ++ 11 výčtu, nikoli běžný jazyk runtime (CLR) výčtu. Chcete-li definovat výčtu CLR, musíte být explicitní o jeho usnadnění přístupu.

- Pomocí klíčového slova šablony explicitně rozptýlá tezávislí název závislý (dodržování předpisů jazyka C++). V následujícím příkladu je zvýrazněné klíčové slovo šablony povinné k vyřešení nejednoznačnosti. Další informace naleznete v [tématu Překlad názvů pro závislé typy](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Konstantní výraz typu float již není povolen jako argument šablony, jak je znázorněno v následujícím příkladu.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Kód, který je kompilován pomocí možnosti `/GS` příkazového řádku a který má chybu zabezpečení mimo jednu, může vést k ukončení procesu za běhu, jak je znázorněno v následujícím příkladu pseudokódu.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- Výchozí architektura pro sestavení x86 se změní na SSE2; proto kompilátor může vyzařovat sa pokyny a bude používat xmm registry k provádění výpočtů s plovoucí desetinnou desetinnou desetinnou desetinnou tálicí. Pokud se chcete vrátit k předchozímu `/arch:IA32` chování, použijte příznak kompilátoru k určení architektury jako IA32.

- Kompilátor může vydávat upozornění [Compiler Warning (úroveň 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) a C4701, kde dříve nebyl. Kompilátor použije silnější kontroly pro použití neinicializovaných místních proměnných typu ukazatele.

- Když je zadán `/HIGHENTROPYVA` nový příznak propojovacího programu, systém Windows 8 obvykle způsobí, že přidělení paměti vrátí 64bitovou adresu. (Před Windows 8, tyto přidělení častěji vráceny adresy, které byly menší než 2 GB.) Tato změna může vystavit chyby zkrácení ukazatele v existujícím kódu. Ve výchozím nastavení je tento přepínač zapnutý. Chcete-li toto `/HIGHENTROPYVA:NO`chování zakázat, zadejte .

- Spravovaný kompilátor (Visual Basic/C#) také podporuje `/HIGHENTROPYVA` pro spravované sestavení.  V tomto případě je `/HIGHENTROPYVAswitch` však vypnuto ve výchozím nastavení.

### <a name="ide"></a>IDE – integrované vývojové prostředí

- Přestože doporučujeme nevytvářet aplikace windows forms v jazyce C++/CLI, je podporována údržba existujících aplikací ui jazyka C++/CLI. Pokud máte k vytvoření aplikace Windows Forms nebo jiné aplikace rozhraní .NET, použijte C# nebo Visual Basic. C++/CLI používejte pouze pro účely interoperability.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Knihovna paralelních vzorů a souběžná doba běhu

Výčet `SchedulerType` `UmsThreadDefault` je zastaralé. Specifikace `UmsThreadDefault` vytvoří zastaralé varování a interně mapuje zpět `ThreadScheduler`na rozhraní .

### <a name="standard-library"></a>Standardní knihovna

- Po přerušení změny mezi Standardy C ++ 98/03 a C++ 11 pomocí explicitní šablony argumenty volat `make_pair()` – jako v `make_pair<int, int>(x, y)` – obvykle nekompiluje v jazyce Visual C++ v sadě Visual Studio 2012. Řešením je vždy `make_pair()` volat bez explicitní šablony `make_pair(x, y)`argumenty – jako v . Poskytnutí argumentů explicitní šablony poráží účel funkce. Pokud požadujete přesnou kontrolu nad `pair` výsledným `make_pair` typem, použijte místo – jako v `pair<short, short>(int1, int2)`.

- Další zlomová změna mezi standardy C++98/03 a C++11: Pokud je A implicitně převoditelná na B a B, je implicitně převoditelná na C, `pair<A, X>` a není implicitně převoditelná `pair<C, X>`na C, C ++ 98/03 a Visual Studio 2010 povoleno převést (implicitně nebo explicitně) na . (Jiný typ, X, není zajímavé zde a není specifické pro první typ v páru.) Kompilátor Jazyka C++ v sadě Visual Studio 2012 zjistí, že A není implicitně konvertibilní na C a odebere převod dvojice z rozlišení přetížení. Tato změna je pozitivní pro mnoho scénářů. Například přetížení `func(const pair<int, int>&)` a `func(const pair<string, string>&)`, `func()` a `pair<const char *, const char *>` volání s bude zkompilovat s touto změnou. Tato změna však přeruší kód, který se spoléhal na agresivní převody párů. Takový kód lze obvykle opravit provedením jedné části převodu explicitně `make_pair(static_cast<B>(a), x)` – například `pair<C, X>`předáním funkce, která očekává .

- Visual Studio 2010 simulované variadické `make_shared<T>(arg1, arg2, argN)`šablony – například – až do limitu 10 argumentů, potlačením přetížení a specializací s preprocesorové stroje. V sadě Visual Studio 2012 je tento limit snížen na pět argumentů pro zlepšení doby kompilace a spotřeby paměti kompilátoru pro většinu uživatelů. Předchozí limit však můžete nastavit explicitním definováním _VARIADIC_MAX jako 10 celoprojektových.

- C++ 11 17.6.4.3.1 [macro.names]/2 zakazuje nahrazení maker klíčových slov, pokud jsou zahrnuty hlavičky standardní knihovny jazyka C++. Záhlaví nyní vyzařují chyby kompilátoru, pokud zjistí klíčová slova nahrazená makry. (Definování _ALLOW_KEYWORD_MACROS umožňuje takový kód ke kompilaci, ale důrazně nedoporučujeme, že použití.) `new` Jako výjimku je ve výchozím nastavení povolena forma makra, protože `#pragma push_macro("new")` / `#undef new` /záhlaví se komplexně brání pomocí `#pragma pop_macro("new")`. Definování _ENFORCE_BAN_OF_MACRO_NEW dělá přesně to, co jeho název napovídá.

- Chcete-li implementovat různé optimalizace a kontroly ladění, implementace standardní knihovny jazyka C++záměrně přeruší binární kompatibilitu mezi verzemi sady Visual Studio (2005, 2008, 2010, 2012). Při použití standardní knihovny Jazyka C++ zakazuje míchání objektových souborů a statických knihoven, které jsou kompilovány pomocí různých verzí do jednoho binárního souboru (EXE nebo DLL), a zakazuje předávání objektů standardní knihovny jazyka C++ mezi binárními soubory, které jsou kompilovány pomocí různých verzí. Míchání objektových souborů a statických knihoven (pomocí standardní knihovny Jazyka C++, které byly zkompilovány pomocí sady Visual Studio 2010 s těmi, které byly zkompilovány pomocí kompilátoru Jazyka C++ v sadě Visual Studio 2012, vydává chyby propojovacího programu o neshodě _MSC_VER, kde _MSC_VER je makro, které obsahuje hlavní verzi kompilátoru (1700 pro Visual C++ v sadě Visual Studio 2012). Tato kontrola nemůže rozpoznat míchání dll a nelze zjistit míchání, které zahrnuje Visual Studio 2008 nebo starší.

- Kromě zjišťování neshod _ITERATOR_DEBUG_LEVEL, který byl implementován v sadě Visual Studio 2010, kompilátor jazyka C++ v sadě Visual Studio 2012 detekuje neshody knihovny runtime. K těmto neshodám dochází, `/MT` když jsou `/MTd` smíšené možnosti `/MD` kompilátoru `/MDd` (statické vydání), (statické ladění), (dynamické vydání) a (dynamické ladění).

- `operator<()`, `operator>()` `operator<=()`, `operator>=()` a byly dříve `std::unordered_map` `stdext::hash_map` k dispozici pro a rodiny kontejnerů, i když jejich implementace nebyly užitečné. Tyto nestandardní operátory byly odebrány v jazyce Visual C++ v sadě Visual Studio 2012. Kromě toho, provádění `operator==()` `operator!=()` a `std::unordered_map` pro rodinu byla rozšířena na `stdext::hash_map` rodinu. (Doporučujeme, abyste se vyhýbali použití rodiny `stdext::hash_map` v novém kódu.)

- C++ 11 22.4.1.4 [locale.codecvt] `codecvt::length()` `codecvt::do_length()` určuje, že `stateT&` a měl by mít upravitelné `const stateT&`parametry, ale Visual Studio 2010 trvalo . Kompilátor Jazyka C++ v sadě `stateT&` Visual Studio 2012 trvá podle pověření standardu. Tento rozdíl je významný pro každého, kdo se `do_length()`pokouší přepsat virtuální funkci .

### <a name="crt"></a>CRT

- Halda C Runtime (CRT), která se používá pro nové a malloc(), již není soukromá. CRT nyní používá haldy procesu. To znamená, že halda není zničena při uvolnění knihovny DLL, takže knihovny DLL, které se staticky propojují s CRT, musí zajistit, aby paměť přidělená kódem Knihovny DLL byla vyčištěna před jeho uvolněním.

- Funkce `iscsymf()` uplatňuje se zápornými hodnotami.

- Struktura `threadlocaleinfostruct` byla změněna tak, aby vyhovovala změnám funkcí národního prostředí.

- Crt funkce, které mají odpovídající vnitřní, jako `memxxx()`je například , `strxxx()` jsou odebrány z intrin.h. Pokud jste zahrnuli intrin.h pouze pro tyto funkce, musíte nyní zahrnout odpovídající crt záhlaví.

### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

- Odebrána podpora Fusion (afxcomctl32.h); proto všechny metody, které \<jsou definovány v afxcomctl32.h> byly odebrány. Soubory \<hlaviček afxcomctl32.h> a \<afxcomctl32.inl> byly odstraněny.

- Název byl `CDockablePane::RemoveFromDefaultPaneDividier` změněn `CDockablePane::RemoveFromDefaultPaneDivider`na .

- Byl změněn `CFileDialog::SetDefExt` podpis pro použití lPCTSTR; proto jsou ovlivněny sestavení Unicode.

- Byly odebrány zastaralé kategorie trasování seznamu ATL.

- Změněn podpis `CBasePane::MoveWindow` na soubor `const CRect`.

- Byl změněn `CMFCEditBrowseCtrl::EnableBrowseButton`podpis souboru .

- Byly odebrány vlastnosti `m_fntTabs` a `m_fntTabsBold` ze třídy `CMFCBaseTabCtrl`.

- Byl přidán parametr `CMFCRibbonStatusBarPane` do konstruktorů. (Je to výchozí parametr, a proto není zdroj-lámání.)

- Do konstruktoru `CMFCRibbonCommandsListBox` byl přidán parametr. (Je to výchozí parametr, a proto není zdroj-lámání.)

- Odebráno `AFXTrackMouse` rozhraní API (a související časovač proc). Místo toho použijte `TrackMouseEvent` rozhraní API Win32.

- Do konstruktoru `CFolderPickerDialog` byl přidán parametr. (Je to výchozí parametr, a proto není zdroj-lámání.)

- `CFileStatus`velikost struktury změněna: Člen `m_attribute` se změnil z BYTE na DWORD `GetFileAttributes`(tak, aby odpovídal hodnotě vrácené z ).

- `CRichEditCtrl`a `CRichEditView` používat MSFTEDIT_CLASS (RichEdit 4.1 řízení) namísto RICHEDIT_CLASS (RichEdit 3.0 řízení) v sestavení unicode.

- Odstraněno, `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` protože je vždy TRUE v systémech Windows Vista, Windows 7 a Windows 8.

- Odstraněno, `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` protože je vždy TRUE v systémech Windows Vista, Windows 7 a Windows 8.

- Odebráno `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`. Volejte rozhraní Windows API přímo ve Windows Vista, Windows 7 a Windows 8.

- Odebráno `AFX_GLOBAL_DATA::DwmDefWindowProc`. Volejte rozhraní Windows API přímo ve Windows Vista, Windows 7 a Windows 8.

- `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` Přejmenována `IsDwmCompositionEnabled` tak, aby eliminovala kolizi názvů.

- Změněny identifikátory pro řadu interních časovačů knihovny MFC a přesunuly definice na soubor afxres.h (AFX_TIMER_ID_*).

- Změněn podpis `OnExitSizeMove` metody tak, aby souhlasil s ON_WM_EXITSIZEMOVE makro:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Změněn název a `OnDWMCompositionChanged` podpis, aby bylo ON_WM_DWMCOMPOSITIONCHANGED makro:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Změněn podpis `OnMouseLeave` metody tak, aby souhlasil s ON_WM_MOUSELEAVE makro:

  - `CMFCCaptionBar`

  - `CMFCColorBar`

  - `CMFCHeaderCtrl`

  - `CMFCProperySheetListBox`

  - `CMFCRibbonBar`

  - `CMFCRibbonPanelMenuBar`

  - `CMFCRibbonRichEditCtrl`

  - `CMFCSpinButtonCtrl`

  - `CMFCToolBar`NahraditTento text

  - `CMFCToolBarComboBoxEdit`

  - `CMFCToolBarEditCtrl`

  - `CMFCAutoHideBar`

- Byl změněn `OnPowerBroadcast` podpis ON_WM_POWERBROADCAST:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

- Byl změněn `OnStyleChanged` podpis ON_WM_STYLECHANGED:

  - `CMFCListCtrl`

  - `CMFCStatusBar`

- Interní metodu `FontFamalyProcFonts` bylo `FontFamilyProcFonts`přejmenováno na .

- Byly odebrány `CString` četné globální statické objekty, aby se v některých situacích eliminovaly nevracení paměti (nahrazeny #defines) a následující proměnné členů třídy:

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

- Byl změněn `CKeyboardManager::ShowAllAccelerators` podpis a byl odebrán parametr oddělovače akcelerátoru.

- Přidáno `CPropertyPage::GetParentSheet`, `CPropertyPage` a ve třídě, `GetParent` volání namísto získat správné okno nadřazeného listu, které může být nadřazené nebo prarodiče okno `CPropertyPage`. Možná budete muset změnit kód `GetParentSheet` pro `GetParent`volání namísto .

- Opravena nevyvážená #pragma varování(push) v ATLBASE. H, který způsobil, že upozornění byla nesprávně zakázána. Tato upozornění jsou nyní správně povolena po ATLBASE. H byl analyzován.

- Metody související s D2D byly přesunuty z AFX_GLOBAL_DATA na _AFX_D2D_STATE:

  - `GetDirectD2dFactory`

  - `GetWriteFactory`

  - `GetWICFactory`

  - `InitD2D`

  - `ReleaseD2DRefs`

  - `IsD2DInitialized`

  - `D2D1MakeRotateMatrix`

  - Místo volání, například `afxGlobalData.IsD2DInitialized`, `AfxGetD2DState->IsD2DInitialized`volejte .

- Odstraněno zastaralé ATL*. Soubory CPP ze složky \atlmfc\include\.

- Přesunul `afxGlobalData` inicializace na on-demand namísto v `DLLMain` době inicializace CRT, aby byly splněny požadavky.

- Byla `RemoveButtonByIndex` přidána `CMFCOutlookBarPane` metoda do třídy.

- Opraveno `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` `IsFrequentlyUsedCmd`na .

- Opraveno několik instancí na `RestoreOriginalstate` . `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`

- Byly odebrány `CDockablePane`nepoužívané metody `GetRecentSiblingPaneInfo`z `CanAdjustLayout`: `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, a .

- Byly `CDockablePane` odebrány `m_bCaptionText` statické `m_bHideDisabledButtons`členské proměnné a .

- Do aplikace `DeleteString` byla `CMFCFontComboBox`přidána metoda přepsání.

- Byly z `CPane`: `GetMinLength` a `IsLastPaneOnLastRow`.

- `CPane::GetDockSiteRow(CDockingPanesRow *)` Přejmenováno `CPane::SetDockSiteRow`na .

## <a name="visual-studio-2010-breaking-changes"></a>Visual Studio 2010 Nejnovější změny

### <a name="compiler"></a>Kompilátoru

- Klíčové slovo **auto** má nový výchozí význam. Vzhledem k tomu, že použití starého významu je vzácné, většina aplikací nebude touto změnou ovlivněna.

- Nové **klíčové** slovo static_assert je zavedeno, což způsobí konflikt názvů, pokud již v kódu existuje identifikátor s tímto názvem.

- Podpora pro nový zápis lambda vylučuje podporu pro kódování nekotovanéguid v atributu IDL uuid.

- Rozhraní .NET Framework 4 zavádí koncept výjimky poškozeného stavu, které jsou výjimky, které ponechávají proces v neopravitelném poškozeném stavu. Ve výchozím nastavení nelze zachytit výjimku poškozeného stavu, a to ani s možností kompilátoru /EHa, která zachycuje všechny ostatní výjimky.                 Chcete-li explicitně zachytit výjimku\_poškozeného stavu, použijte příkazy __try- _except. Nebo použijte atribut [HandledProcessCorruptedStateExceptions], abyste umožnili funkci zachytit výjimky poškozeného stavu.  Tato změna se týká především programátorů systému, kteří mohou mít zachytit výjimku poškozeného stavu. Osm výjimek je STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION STATUS_UNWIND_CONSOLIDATE.                 Další informace o těchto výjimkách naleznete v makru [GetExceptionCode.](/windows/win32/Debug/getexceptioncode)

- Revidovaná `/GS` možnost kompilátoru chrání proti přetečení vyrovnávací paměti komplexněji než v předchozích verzích. Tato verze může vložit další kontroly zabezpečení v zásobníku, které mohou snížit výkon. Pomocí nového `__declspec(safebuffers)` klíčového slova můžete kompilátoru dát pokyn, aby nevkládal bezpečnostní kontroly pro určitou funkci.

- Pokud kompilujete s možnostmi kompilátoru (Optimalizace celého `/GL` programu) a `/clr` (Kompilace běžného jazykového prostředí), `/GL` bude tato možnost ignorována. Tato změna byla provedena, protože kombinace možností kompilátoru poskytla malou výhodu. V důsledku této změny je lepší výkon sestavení.

- Ve výchozím nastavení je v sadě Visual Studio 2010 zakázána podpora trigrafů. Pomocí `/Zc:trigraphs` možnosti kompilátoru povolte podporu trigrafů. Trigraph se skládá ze dvou po sobě jdoucích otazníků ("??") následovaných jedinečným třetím znakem. Kompilátor nahradí trigraph odpovídajícím interpunkčním znakem. Například kompilátor nahradí `??=` trigraph znakem #. Použijte trigrafy ve zdrojových souborech Jazyka C, které používají znakovou sadu, která neobsahuje pohodlné grafické znázornění některých interpunkčních znaků.

- Propojovací program již nepodporuje optimalizaci pro systém Windows 98. Možnost `/OPT` (Optimalizace) vytvoří chybu času kompilace, pokud zadáte `/OPT:WIN98` nebo `/OPT:NOWIN98`.

- Výchozí možnosti kompilátoru, které jsou určeny vlastnostmi systému sestavení RuntimeLibrary a DebugInformationFormat, byly změněny. Ve výchozím nastavení jsou tyto vlastnosti sestavení určeny v projektech, které jsou vytvořeny visual c++ verze 7.0 až 10.0. Pokud migrujete projekt, který byl vytvořen visual c++ 6.0, zvažte, zda určit hodnotu pro tyto vlastnosti.

- V sadě Visual Studio 2010 RuntimeLibrary`/MD`= MultiThreaded ( )`/Zi`a DebugInformationFormat = ProgramDatabase ( ). V jazyce Visual C++ 9.0 je`/MT`runtimelibrary = MultiThreaded ( ) a DebugInformationFormat = Zakázáno.

### <a name="clr"></a>CLR

- Kompilátory Jazyka Microsoft C# a Visual Basic nyní mohou vytvořit žádné primární sestavení interop (no-PIA). Sestavení no-PIA můžete použít typy COM bez nasazení příslušné ho primárního sestavení interop (PIA). Při spotřebě sestavení bez PIA vytvořených jazykem Visual C# nebo Visual Basic musíte odkazovat na sestavení PIA na příkazu kompilace, než na něj odkazujete na sestavení no-PIA, které používá knihovnu.

### <a name="visual-studio-c-projects-and-msbuild"></a>Projekty Visual Studio C++ a MSBuild

- Projekty Visual Studio C++ jsou teď založené na nástroji MSBuild. V důsledku toho soubory projektu používají nový formát souboru XML a příponu souboru .vcxproj. Visual Studio 2010 automaticky převede soubory projektu z dřívějších verzí sady Visual Studio do nového formátu souboru. Existující projekt je ovlivněna, pokud závisí na předchozí nástroj sestavení, VCBUILD.exe nebo příponu souboru projektu.

- V dřívějších verzích visual c++ podporoval pozdní vyhodnocení seznamů vlastností. Nadřazený seznam vlastností může například importovat podřízený seznam vlastností a nadřazený objekt může použít proměnnou definovanou v podřízeném objektu k definování dalších proměnných. Pozdní vyhodnocení umožnilo nadřazené mu použít podřízenou proměnnou ještě před importem podřízeného seznamu vlastností. V sadě Visual Studio 2010 nelze použít proměnnou listu projektu před definovanou, protože MSBuild podporuje pouze včasné vyhodnocení.

### <a name="ide"></a>IDE – integrované vývojové prostředí

- Dialogové okno ukončení aplikace již nekončí aplikaci. V předchozích verzích, když funkce `abort()` nebo `terminate()` zavřela maloobchodní sestavení aplikace, knihovna run-time c zobrazí zprávu o ukončení aplikace v okně konzoly nebo dialogovém okně. Zpráva částečně říká: "Tato aplikace požádala runtime, aby ji ukončil neobvyklým způsobem. Další informace získáte od týmu podpory aplikace." Zpráva o ukončení aplikace byla nadbytečná, protože systém Windows následně zobrazil aktuální obslužnou rutinu ukončení, což bylo obvykle dialogové okno Zasílání zpráv o chybách systému Windows (Dr. Watson) nebo ladicí program sady Visual Studio. Počínaje Visual Studio 2010, C Run-Time Library nezobrazí zprávu. Kromě toho zaběhu zabrání ukončení aplikace před spuštěním ladicího programu. Toto je narušující změna pouze v případě, že závisí na předchozí chování zprávy o ukončení aplikace.

- Konkrétně pro Visual Studio 2010, IntelliSense nefunguje pro kód C++/CLI kód nebo atributy, **najít všechny odkazy** nefunguje pro místní proměnné a model kódu nenačítá názvy typů z importovaných sestavení nebo přeložit typy jejich plně kvalifikované názvy.

### <a name="libraries"></a>Knihovny

- Třída SafeInt je součástí visual c++ a již není v samostatném stahování. Toto je narušující změna pouze v případě, že jste vyvinuli třídu, která je také s názvem "SafeInt".

- Model nasazení knihoven již nepoužívá manifesty k nalezení konkrétní verze knihovny dynamických odkazů. Místo toho název každé knihovny dynamických odkazů obsahuje číslo verze a tento název použijete k vyhledání knihovny.

- V předchozích verzích sady Visual Studio můžete znovu sestavit knihovny běhu. Visual Studio 2010 již nepodporuje vytváření vlastních kopií souborů knihovny běhu Jazyka C.

### <a name="standard-library"></a>Standardní knihovna

- Hlavička \<> iterátoru již není automaticky zahrnuta mnoha dalšími soubory hlaviček. Místo toho zahrnout toto záhlaví explicitně, pokud potřebujete podporu pro samostatné iterátory definované v záhlaví. Existující projekt je ovlivněna, pokud závisí na předchozí nástroj sestavení, VCBUILD.exe nebo příponu souboru projektu, .vcproj.iterator.

- V \<záhlaví> algoritmu jsou odebrány funkce checked_* a unchecked_.\* A v \<záhlaví iterátoru `checked_iterator`>> je třída `unchecked_array_iterator` odebrána a třída byla přidána.

- Konstruktor `CComPtr::CComPtr(int)` je odebrán. Tento konstruktor `CComPtr` povolil vytvoření objektu z makra NULL, ale byl zbytečný a umožňoval nesmyslné konstrukce z nenulových celočísel.

   A `CComPtr` může být stále vytvořena z NULL, která je definována jako 0, ale nezdaří, pokud je vytvořena z celé hozinu než literál 0. Místo toho použijte **nullptr.**

- Byly `ctype` odebrány následující `ctype::_Do_narrow_s`členské `ctype::_Do_widen_s` `ctype::_narrow_s`funkce: , , . `ctype::_widen_s`. Pokud aplikace používá některou z těchto členských funkcí, je nutné `ctype::do_narrow`ji `ctype::do_widen` `ctype::narrow`nahradit `ctype::widen`odpovídající nezabezpečenou verzí: , , .

### <a name="crt-mfc-and-atl-libraries"></a>Knihovny CRT, MFC a ATL

- Podpora byla odebrána pro uživatele k vytvoření knihoven CRT, MFC a ATL. Například není k dispozici žádný vhodný soubor NMAKE. Uživatelé však stále mají přístup ke zdrojovému kódu pro tyto knihovny. A dokument, který popisuje možnosti MSBuild, které společnost Microsoft používá k vytvoření těchto knihoven, bude pravděpodobně publikován v blogu týmu Visual C++.

- Podpora knihovny MFC pro IA64 byla odebrána. Podpora pro CRT a ATL na IA64 je však stále k dispozici.

- Počet néřů se již znovu nepoužije v souborech definice modulu knihovny MFC (.def). Tato změna znamená, že se ordinální verze nebudou lišit mezi dílčími verzemi a zlepší se binární kompatibilita aktualizací Service Pack a technických verzí rychlé opravy.

- Do třídy byla přidána `CDocTemplate` nová virtuální funkce. Tato nová virtuální funkce je [CDocTemplate Class](../mfc/reference/cdoctemplate-class.md). Předchozí verze `OpenDocumentFile` měla dva parametry. Nová verze má tři parametry. Pro podporu správce restartování musí každá `CDocTemplate` třída odvozená z implementovat verzi, která má tři parametry. Nový parametr `bAddToMRU`je .

### <a name="macros-and-environment-variables"></a>Makra a proměnné prostředí

- Proměnná prostředí __MSVCRT_HEAP_SELECT již není podporována. Tato proměnná prostředí je odebrána a neexistuje žádná náhrada.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční dokumentace

- Z kompilátoru Microsoft Macro Assembler Reference bylo odebráno několik direktiv. Odebrané směrnice `.186`jsou `.286` `.286P`, `.287` `.8086`, `.8087`, `.NO87`, , a .

## <a name="visual-studio-2008-breaking-changes"></a>Visual Studio 2008 Nejnovější změny

### <a name="compiler"></a>Kompilátoru

- Platformy Windows 95, Windows 98, Windows ME a Windows NT již nejsou podporovány. Tyto operační systémy byly odebrány ze seznamu cílových platforem.

- Kompilátor již nepodporuje více atributů, které byly přímo spojeny se serverem ATL. Následující atributy již nejsou podporovány:

  - perf_counter

  - perf_object

  - Perfmon

  - request_handler

  - soap_handler

  - soap_header

  - soap_method

  - tag_name

### <a name="visual-studio-c-projects"></a>Projekty Visual Studia C++

- Při inovaci projektů z předchozích verzí sady Visual Studio bude pravděpodobně nutné upravit makra WINVER a _WIN32_WINNT tak, aby byla větší nebo rovna 0x0500.

- Počínaje Visual Studio 2008, nový průvodce projektu nemá možnost vytvořit projekt C++ SQL Server. Sql Server projekty vytvořené pomocí starší verze sady Visual Studio bude stále kompilovat a pracovat správně.

- Soubor záhlaví rozhraní API systému Windows Winable.h byl odebrán. Místo toho zahrňte soubor Winuser.h.

- Knihovna rozhraní API systému Windows Rpcndr.lib byla odebrána. Místo toho spojte s rpcrt4.lib.

### <a name="crt"></a>CRT

- Byla odebrána podpora pro systémy Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4.0.

- Byly odebrány následující globální proměnné:

  - _osplatform

  - _osver

  - _winmajor

  - _winminor

  - _winver

- Následující funkce byly odebrány. Použijte funkce `GetVersion` rozhraní `GetVersionEx` API systému Windows nebo místo toho:

  - _get_osplatform

  - _get_osver

  - _get_winmajor

  - _get_winminor

  - _get_winver

- Syntaxe poznámky SAL se změnila. Další informace naleznete [v tématu Poznámky SAL](../c-runtime-library/sal-annotations.md).

- Filtr IEEE nyní podporuje instrukční sadu SSE 4.1. Další informace naleznete [v tématu _fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Knihovny C Run-Time, které jsou dodávány s visual studio již nejsou závislé na systémové knihovně DLL msvcrt.dll.

### <a name="standard-library"></a>Standardní knihovna

- Byla odebrána podpora pro systémy Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4.0.

- Při kompilaci v režimu ladění s _HAS_ITERATOR_DEBUGGING definován [(nahrazen_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010), aplikace bude nyní uplatnit, když iterátor pokusí o zvýšení nebo snížení za hranice podkladového kontejneru.

- Členská proměnná c třídy zásobníku je nyní deklarována jako chráněná. Dříve byla tato členská proměnná deklarována jako veřejná.

- Chování `money_get::do_get` se změnilo. Dříve při analýzě peněžní částky s více zlomkových `frac_digits` `do_get` číslic, než je požadováno , slouží ke spotřebě je všechny. Nyní `do_get` přestane analyzovat po konzumaci `frac_digits` na většině znaků.

### <a name="atl"></a>ATL

- Atl nelze sestavit bez závislosti na CRT. V dřívějších verzích sady Visual Studio můžete použít #define ATL_MIN_CRT k tomu, aby projekt ATL byl minimálně závislý na CRT. V sadě Visual Studio 2008 jsou všechny projekty ATL minimálně závislé na CRT bez ohledu na to, zda je definovánATL_MIN_CRT

- Atl Server codebase byl vydán jako sdílený zdrojový projekt na CodePlex a není nainstalován jako součást sady Visual Studio. Třídy kódování a dekódování dat z atlenc.h a užitné funkce a třídy z atlutil.h a atlpath.h byly zachovány a jsou nyní součástí knihovny ATL. Několik souborů přidružených ke serveru ATL již není součástí sady Visual Studio.

- Některé funkce již nejsou součástí dll. Jsou stále umístěny v knihovně importu. To nebude mít vliv na kód, který používá funkce staticky. Bude mít vliv pouze na kód, který používá tyto funkce dynamicky.

- Makra PROP_ENTRY a PROP_ENTRY_EX byla z bezpečnostních důvodů zastaralá a nahrazena makrami PROP_ENTRY_TYPE a PROP_ENTRY_TYPE_EX.

### <a name="atlmfc-shared-classes"></a>Sdílené třídy ATL/MFC

- Atl nelze sestavit bez závislosti na CRT. V dřívějších verzích sady Visual `#define ATL_MIN_CRT` Studio můžete použít k tomu, aby projekt ATL byl minimálně závislý na CRT. V sadě Visual Studio 2008 jsou všechny projekty ATL minimálně závislé na CRT bez ohledu na to, zda je definovánATL_MIN_CRT

- Atl Server codebase byl vydán jako sdílený zdrojový projekt na CodePlex a není nainstalován jako součást sady Visual Studio. Třídy kódování a dekódování dat z atlenc.h a užitné funkce a třídy z atlutil.h a atlpath.h byly zachovány a jsou nyní součástí knihovny ATL. Několik souborů přidružených ke serveru ATL již není součástí sady Visual Studio.

- Některé funkce již nejsou součástí dll. Jsou stále umístěny v knihovně importu. To nebude mít vliv na kód, který používá funkce staticky. Bude mít vliv pouze na kód, který používá tyto funkce dynamicky.

### <a name="mfc"></a>MFC

- `CTime`Třída: `CTime` Třída nyní přijímá data od 1/1/1900 CE místo 1/1/1970 CE

- Pořadí ovládacích prvků v dialogových oknech knihovny MFC: Správné pořadí polí více ovládacích prvků v dialogovém okně knihovny MFC je narušeno, pokud je v pořadí polí vložen ovládací prvek ActiveX knihovny MFC. Tato změna tento problém opraví.

   Můžete například vytvořit aplikaci dialogového okna knihovny MFC, která má ovládací prvek ActiveX a několik ovládacích prvků pro úpravy. Umístěte ovládací prvek ActiveX doprostřed pořadí ovládacích prvků úprav. Spusťte aplikaci, klepněte na ovládací prvek pro úpravy, jehož pořadí polí je za ovládacím prvkem ActiveX, a potom na kartě.

- `CFileDialog`Třída: Vlastní šablony `CFileDialog` pro třídu nelze automaticky přenést do systému Windows Vista. Jsou stále použitelné, ale nebudou mít další funkce nebo vzhled dialogových oken stylu systému Windows Vista.

- `CWnd`Třída `CFrameWnd` a třída: Metoda `CWnd::GetMenuBarInfo` byla odebrána.

   Metoda `CFrameWnd::GetMenuBarInfo` je nyní nevirtuální metoda. Další informace naleznete v **tématu GetMenuBarInfo Function** v sadě Windows SDK.

- Podpora rozhraní MFC ISAPI: Knihovna MFC již nepodporuje vytváření aplikací pomocí rozhraní ISAPI (Internet Server Application Programming Interface). Pokud chcete vytvořit aplikaci ISAPI, zavolejte přímo rozšíření ISAPI.

- Zastaralá api ANSI: Verze ANSI několika metod knihovny MFC jsou zastaralé. Použijte unicode verze těchto metod v budoucích aplikacích. Další informace naleznete v **tématu Build Requirements for Windows Vista Common Controls**.

## <a name="visual-studio-2005-breaking-changes"></a>Visual Studio 2005 Nejnovější změny

### <a name="crt"></a>CRT

- Mnoho funkcí bylo zastaralé. Viz **Zastaralé funkce CRT**.

- Mnoho funkcí nyní ověřuje jejich parametry a zastavuje provádění, pokud jsou dány neplatné parametry. Toto ověření může přerušit kód, který předává neplatné parametry a spoléhá na funkci, která je ignoruje nebo pouze vrací kód chyby. Viz **Ověření parametru**.

- Hodnota popisovače souboru -2 se nyní `stdout` `stderr` používá k označení, že a nejsou k dispozici pro výstup, například v aplikaci systému Windows, která nemá žádné okno konzoly. Předchozí použitá hodnota byla -1. Další informace naleznete [v tématu _fileno](../c-runtime-library/reference/fileno.md).

- Knihovny CRT s jedním podprocesem (libc.lib a libcd.lib) byly odebrány. Použijte vícevláknové knihovny CRT. Příznak `/ML` kompilátoru již není podporován. Non-locking verze některých funkcí byly přidány v případech, kdy rozdíl výkonu mezi vícevláknový kód a jednovláknový kód je potenciálně významné.

- Přetížení pow, double pow (int, int), bylo odstraněno, aby lépe odpovídalo standardu.

- Specifikátor formátu %n již není ve výchozím nastavení podporován v žádné z řady funkcí printf, protože je ze své podstaty nezabezpečený. Pokud je zjištěn %n, výchozí chování je vyvolat neplatnou obslužnou rutinu parametru. Chcete-li povolit `_set_printf_count_output` %n `_get_printf_count_output`podporu, použijte (viz také).

- `sprintf`nyní vytiskne záporné znaménko podepsané nuly.

- `swprintf`byla změněna tak, aby odpovídala normě; nyní vyžaduje parametr velikosti. Forma `swprintf` bez parametru velikosti byla zastaralá.

- `_set_security_error_handler`byla odebrána. Odeberte všechna volání této funkce; výchozí obslužná rutina je mnohem bezpečnější způsob, jak řešit chyby zabezpečení.

- `time_t`je nyní 64bitová hodnota (pokud není definován_USE_32BIT_TIME_T).

- `_spawn`Funkce `_wspawn` , funkce `errno` nyní ponechat nedotčené na úspěch, jak je uvedeno standardu C.

- RTC nyní používá široké znaky ve výchozím nastavení.

- Funkce podpory slov s plovoucí desetinnou desetinnou `/CLR` desetinnou táhou byly zastaralé pro aplikace kompilované pomocí aplikace nebo `/CLR:PURE`. Ovlivněné funkce `_clear87` `_clearfp`jsou `_control87` `_controlfp`, `_fpreset` `_status87`, `_statusfp`, , , . . Upozornění na vyřazení můžete zakázat definováním _CRT_MANAGED_FP_NO_DEPRECATE, ale použití těchto funkcí ve spravovaném kódu je nepředvídatelné a nepodporované.

- Některé funkce nyní vrátí const ukazatele. Staré, non-const chování může být obnovena definováním _CONST_RETURN. Ovlivněné funkce jsou

  - memchr, wmemchr

  - strchr, wcschr, _mbschr, _mbschr_l

  - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

  - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

  - strstr, wcsstr, _mbsstr, _mbsstr_l

- Při propojení s Setargv.obj nebo Wsetargv.obj již není možné potlačit rozšíření zástupného znaku na příkazovém řádku jeho uzavřením v uvozovkách. Další informace naleznete v [tématu Rozbalení zástupných argumentů](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Standardní knihovna (2005)

- Třída výjimky (umístěná v záhlaví výjimky \< `std`>) byla přesunuta do oboru názvů. V předchozích verzích byla tato třída v globálním oboru názvů. Chcete-li vyřešit všechny chyby označující, že třída výjimky nebyla nalezena, přidejte do kódu následující příkaz using:`using namespace std;`

- Při `valarray::resize()`volání `valarray` bude obsah tohoto dokumentu ztracen a bude nahrazen výchozími hodnotami. Metoda `resize()` je určena k reinicializaci `valarray` spíše než růst dynamicky jako vektor.

- Ladění iterátorů: Aplikace vytvořené s ladicí verzí knihovny C-Runtime a které používají iterátory nesprávně může začít vidět nepodmíněných výrazů za běhu. Chcete-li zakázat tyto nepodmíněných výrazů, musíte definovat _HAS_ITERATOR_DEBUGGING (nahrazen_ITERATOR_DEBUG_LEVEL [po](../standard-library/iterator-debug-level.md) Visual Studio 2010) na 0. Další informace naleznete v tématu [Debug Iterator Support](../standard-library/debug-iterator-support.md)

## <a name="visual-c-net-2003-breaking-changes"></a>Vizuální c++ .NET 2003 Nejnovější změny

### <a name="compiler"></a>Kompilátoru

- Uzavírací závorky, které jsou nyní vyžadovány pro definovanou direktivu preprocesoru (C2004).

- Explicitní specializace již nenaleznou parametry šablony z primární šablony ([Chyba kompilátoru C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Chráněný člen (n) lze přistupovat pouze prostřednictvím členské funkce třídy (B), která dědí z třídy (A), z nichž (n) je členem ([Chyba kompilátoru C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Vylepšené kontroly usnadnění v kompilátoru nyní zjišťují nepřístupné základní třídy[(Chyba kompilátoru C2248).](../error-messages/compiler-errors-1/compiler-error-c2248.md)

- Výjimku nelze zachytit, pokud je destruktor nebo konstruktor kopie nepřístupný (C2316).

- Výchozí argumenty na odkazy na funkce již nejsou povoleny ([Chyba kompilátoru C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Statický datový člen nelze inicializovat prostřednictvím odvozené třídy[(Chyba kompilátoru C2477).](../error-messages/compiler-errors-1/compiler-error-c2477.md)

- Inicializace **typedef** není povolena standardem a nyní generuje chybu kompilátoru ([Chyba kompilátoru C2513).](../error-messages/compiler-errors-2/compiler-error-c2513.md)

- **bool** je nyní správný typ ([Chyba kompilátoru C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- UDC nyní může vytvářet nejednoznačnost s přetíženými operátory ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Další výrazy jsou nyní považovány za platné konstanty ukazatele null ([Chyba kompilátoru C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- šablona<> je nyní vyžadována v místech, kde by to kompilátor dříve naznačoval ([Chyba kompilátoru C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- Explicitní specializace členské funkce mimo třídu není platná, pokud již byla funkce explicitně specializována prostřednictvím specializace třídy šablony ([Chyba kompilátoru C2910).](../error-messages/compiler-errors-2/compiler-error-c2910.md)

- Parametry netextové šablony s plovoucí desetinnou tázkem již nejsou povoleny[(Chyba kompilátoru C2993).](../error-messages/compiler-errors-2/compiler-error-c2993.md)

- Šablony tříd nejsou povoleny jako argumenty typu šablony (C3206).

- Názvy funkcí Friend již nejsou zavedeny do obsahujícího oboru názvů ([Chyba kompilátoru C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Kompilátor již nebude přijímat další čárky v makru (C4002).

- Objekt typu POD vytvořený s inicializátorem formuláře () bude výchozí inicializován (C4345).

- typename je nyní vyžadován, pokud má být závislý název považován za typ ([Upozornění kompilátoru (úroveň 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Funkce, které byly nesprávně považovány za specializace šablony již nejsou považovány za tak (C4347).

- Statické datové členy nelze inicializovat prostřednictvím odvozené třídy (C4356).

- Specializace šablony třídy musí být definována před použitím v návratovém typu[(Upozornění kompilátoru (úroveň 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Kompilátor nyní hlásí nedostupný kód (C4702).

## <a name="see-also"></a>Viz také

[Co je nového pro Visual C++ v Visual Studiu](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
