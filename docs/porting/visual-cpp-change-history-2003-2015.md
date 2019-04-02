---
title: 2003 – 2015 historie změn Visual C++
ms.date: 08/30/2017
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: 9be4db9e0f7c50054dc6e6ca498b1c9d49715a8d
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58775410"
---
# <a name="visual-c-change-history-2003---2015"></a>2003 – 2015 historie změn Visual C++

Tento článek popisuje zásadní změny z Visual Studia 2015, když se vrátíme k Visual Studio 2003 a v tomto článku podmínky "nové chování" nebo "teď" odkazovat do sady Visual Studio 2015 a novější. Podmínky "staré chování" a "před" odkazovat na Visual Studio 2013 a dřívějších verzích.

Informace o sadě Visual Studio 2017 najdete v tématu [co je nového v aplikaci Visual C++ v sadě Visual Studio 2017](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) a [vylepšení v aplikaci Visual C++ v sadě Visual Studio 2017](../overview/cpp-conformance-improvements-2017.md).

> [!NOTE]
> Neexistují žádná binární rozbíjející změny mezi Visual Studio 2015 a Visual Studio 2017.

Při upgradu na novou verzi sady Visual Studio se můžete setkat s kompilačním nebo běhovým chybám v kódu, který dříve kompiloval a běžel správně. Změny v nové verzi, které způsobují tyto problémy jsou označovány jako *rozbíjející změny v*, a obvykle vyžadovány na základě změn ve standardu jazyka C++, podpisech funkcí nebo rozložení objektů v paměti.

Aby nedocházelo k chybám za běhu, které se těžko najít a diagnostikovat, doporučujeme vám nikdy nevytvářet statická propojení na binární soubory zkompilovány pomocí jinou verzi kompilátoru. Když upgradujete projekt EXE nebo DLL, nezapomeňte také provést upgrade knihoven, na které odkazuje. Nemáte předat CRT (C Runtime) nebo typy standardní knihovny C++ (standardní knihovna C++) mezi binárními soubory, včetně knihoven DLL, zkompilovány pomocí jiných verzí kompilátoru. Další informace najdete v tématu [potenciální chyby předávání CRT objekty přes hranice knihovny DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Nikdy byste psát kód, který závisí na konkrétním rozložení pro objekt, který není rozhraním modelu COM nebo objektem POD. Pokud takový kód napíšete, musíte zajistit, aby po upgradu fungoval. Další informace najdete v tématu [přenositelnost na ABI hranice](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Kromě toho probíhající vylepšení shoda s kompilátorem prostředí můžete někdy změnit jak kompilátor rozpozná existující zdrojový kód. Můžete například zjistit nové nebo jiné chyby během sestavování nebo dokonce behaviorální rozdíly v kódu, který dříve vytvořené a vypadal jako správně spustit. I když tato vylepšení nejsou rozbíjející změny, jako jsou popsané v tomto dokumentu, budete muset provést změny ke zdrojovému kódu. Chcete-li vyřešit tyto problémy:

- [Knihovny jazyka C Runtime (CRT) Rozbíjející změny v](#BK_CRT)

- [Standard jazyka C++ a standardní knihovna C++ Rozbíjející změny v](#BK_STL)

- [Knihovna MFC a ATL Rozbíjející změny v](#BK_MFC)

- [Změny způsobující chyby modulu Runtime souběžnosti](#BK_ConcRT)

## <a name="VC_2015"></a> Visual C++ 2015 nejnovějšími změnami

###  <a name="BK_CRT"></a> Běhové knihovny jazyka C (CRT)

#### <a name="general-changes"></a>Obecné změny

- **Refaktorovaný binárních souborů**

   Knihovna CRT byla refaktorována, do dvou různých binárních souborů: Universal CRT (ucrtbase), který obsahuje většinu standardních funkcí a knihovny modulu Runtime VC (vcruntime). Knihovna vcruntime obsahuje týkající se kompilátoru funkce jako je zpracování výjimek a vnitřní funkce. Pokud použijete výchozí nastavení projektu, pak tato změna nebude mít vliv na vás od propojovacího programu bude automaticky používat nový výchozí knihovny. Pokud jste nastavili v projektu **Linkeru** vlastnost **ignorovat všechny výchozí knihovny** k **Ano** nebo používáte `/NODEFAULTLIB` na příkazovém řádku, pak jste – možnost linkeru musíte aktualizovat seznam knihoven (v **Další závislosti** vlastnost) zahrnout nové, refaktorovaný knihovny. Nahraďte původní Knihovna CRT (libcmt.lib libcmtd.lib, msvcrt.lib, msvcrtd.lib) ekvivalentní refaktorovaný knihovny. U každé dvě refaktorovaný knihovny jsou statické (.lib) a verze dynamické (knihovny DLL) a vydané verzi (bez přípony) a ladicí verze (s příponou "d"). Dynamické verze mají knihovnu importu, který můžete propojit s. Dvě refaktorovaný knihovny jsou Universal CRT, konkrétně ucrtbase.dll nebo ucrtbase.lib, ucrtbased.dll nebo ucrtbased.lib a knihovna prostředí runtime VC, libvcruntime.lib vcruntime*verze*.dll, libvcruntimed.lib, a vcruntimed*verze*.dll. *Verze* v sadě Visual Studio 2015 a Visual Studio 2017 je 140. Zobrazit [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).

#### <a name="localeh"></a>\<Locale.h >

- **localeconv**

   [Localeconv](../c-runtime-library/reference/localeconv.md) funkce deklarovaná v locale.h nyní funguje správně při [národního prostředí pro vlákno](../parallel/multithreading-and-locales.md) je povolená. V předchozích verzích knihovny, vrátí tato funkce `lconv` dat pro globální národní prostředí, nikoli národní prostředí vlákna.

   Pokud používáte národní prostředí pro vlákno, měli byste zkontrolovat vaše užívání `localeconv`. Pokud váš kód předpokládá, že `lconv` vrácená data pro globální národní prostředí, měli byste opravit.

#### <a name="mathh"></a>\<math.h>

- **Přetížení C++ matematických knihovních funkcí**

   V předchozích verzích \<math.h > definované některé, ale ne všechna přetížení C++ pro matematických knihovních funkcí. Zbývající část přetížení byly v \<cmath > záhlaví. Kód, který zahrnuty pouze \<math.h > může mít problémy s řešení přetížení funkce. Nyní přetížení C++ byly odebrány z \<math.h > se nacházejí pouze v \<cmath >.

   Pro vyřešení chyb, zahrnují \<cmath > Chcete-li získat deklarace funkce, které byly odebrány z \<math.h >. Tyto funkce se přesunuly:

  - `double abs(double)` a `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - `float` a `long double` verze s plovoucí desetinnou čárkou bodu funkce `acos`, `acosh`, `asin`, `asinh`, `atan`, `atanh`, `atan2`, `cbrt`, `ceil`, `copysign`, `cos`, `cosh`, `erf`, `erfc`, `exp`, `exp2`, `expm1`, `fabs`, `fdim`, `floor`, `fma`, `fmax`, `fmin` , `fmod`, `frexp`, `hypot`, `ilogb`, `ldexp`, `lgamma`, `llrint`, `llround`, `log`, `log10`, `log1p`, `log2`, `lrint`, `lround`, `modf`, `nearbyint`, `nextafter`, `nexttoward`, `remainder`, `remquo`, `rint`, `round`, `scalbln`, `scalbn`, `sin`, `sinh`, `sqrt`, `tan`, `tanh`, `tgamma`, a `trunc`

  Pokud máte kód, který používá `abs` s plovoucí bodu typ, který obsahuje jenom \<math.h > hlavičky, s plovoucí desetinnou čárkou verzích již nebude k dispozici. Volání nyní přeloží na `abs(int)`, i s plovoucí bodu argument, který generuje chybu:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Oprava pro toto upozornění je nahraďte volání `abs` s plovoucí verze bodu `abs`, jako `fabs` double argument nebo `fabsf` pro argument typu float, nebo zahrnout \<cmath > záhlaví a pokračovat v používání `abs`.

- **Shoda s plovoucí desetinnou čárkou bodu**

   Mnoho změn do knihovny math mít cíl vylepšit celkovou shodu IEEE 754 a specifikace C11 přílohy F s ohledem na zvláštní případ vstupů, například hodnoty NaN a nekonečno. Tichý NaN vstupy, které byly často považována za chyby v předchozích verzích knihovny, jsou již považovány za chyby. V tématu [IEEE 754 standardní](https://standards.ieee.org/standard/754-2008.html) a přílohy F [C11 Standard](http://www.iso-9899.info/wiki/The_Standard).

   Tyto změny nebude způsobovat chyby v době kompilace, ale může způsobit, že programy, které se chovají jinak než a větší správně podle standardu.

- **FLT_ROUNDS**

   V sadě Visual Studio 2013 FLT_ROUNDS – makro rozšířit na konstantní výraz, který byl nesprávná, protože je možné konfigurovat za běhu, například pomocí volání fesetround režimu zaokrouhlování. FLT_ROUNDS – makro je teď dynamická a správně odráží aktuální režim zaokrouhlení.

#### <a name="new-and-newh"></a>\<Nový > a \<new.h >

- **nové a odstranění**

   V předchozích verzích knihovny definované implementací operátor new a delete funkcí exportovaných z knihovny runtime DLL (například msvcr120.dll). Tyto funkce operátoru jsou teď vždy staticky propojené do vašich binárních souborů, i když se používá knihovnu runtime knihovny DLL.

   To není zásadní změny pro nativní nebo smíšený kód (`/clr`), ale pro kód zkompilovaný jako [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), tato změna může způsobit selhání kompilace vašeho kódu. Pokud při kompilaci kódu jako `/clr:pure`, budete muset přidat `#include <new>` nebo `#include <new.h>` obejít chyby sestavení z důvodu této změny. `/clr:pure` Možnost je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017. Kód, který musí být "čistě" by měl být přenést do jazyka C#.

#### <a name="processh"></a>\<process.h>

- **_beginthread a _beginthreadex**

   [_Beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) a [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) functions nyní uložení odkazu na modul, ve kterém je definována procedura vlákna po dobu trvání vlákna. To pomáhá zajistit, že nejsou moduly uvolněna až do konce bylo spuštěno vlákno.

#### <a name="stdargh"></a>\<stdarg.h>

- **va_start a referenční typy**

   Při kompilaci kódu jazyka C++ [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) nyní ověří v době kompilace, které do něho předaný argument není typu odkazu. Argumenty typu odkazu jsou zakázány podle standardu jazyka C++.

#### <a name="stdioh-and-conioh"></a>\<stdio.h > a \<conio.h >

- **Nyní jsou definovány printf a scanf rodinu funkcí vložené.**

   Definice všech `printf` a `scanf` funkce byly přesunuté vložené do \<stdio.h >, \<conio.h > a dalších hlaviček CRT. Tato zásadní změna vede k chybě propojovacího programu (LNK2019, nerozpoznaný externí symbol) pro všechny programy, které tyto funkce deklarovaná místně bez zahrnutí příslušné záhlaví CRT. Pokud je to možné, měli byste aktualizovat kód přikazující zahrnutí záhlaví CRT (to znamená přidat `#include <stdio.h>`) a vložené funkce, ale pokud nechcete změnit váš kód přikazující zahrnutí tyto soubory hlaviček, alternativní řešení Chcete-li přidat další knihovny vaše linkeru Vstupní, legacy_stdio_definitions.lib.

   Chcete-li přidat tuto knihovnu pro váš vstup linkeru v integrovaném vývojovém prostředí, otevřete kontextovou nabídku pro uzel projektu, zvolte **vlastnosti**, pak v **vlastnosti projektu** dialogového okna zvolte **Linkeru**a upravit **vstup Linkeru** přidat `legacy_stdio_definitions.lib` do seznamu středníkem-colon oddělených čárkami.

   Pokud váš projekt odkazuje statických knihoven, které byly zkompilovány pomocí verze sady Visual Studio starší než 2015, linker hlásit nevyřešené externí symbol. K těmto chybám může odkazovat na interní definice pro `_iob`, `_iob_func`, nebo pro určité související importy \<stdio.h > funkce ve formě _imp_\*. Společnost Microsoft doporučuje, když upgradujete projekt překompilovat všechny statické knihovny se zmírněními hrozeb nejnovější verzi kompilátoru jazyka C++ a knihoven. Pokud je knihovna knihovny třetích stran pro zdroj, který není k dispozici, by měla buď vyžádat aktualizované binární od třetích stran nebo zapouzdření využití této knihovny do samostatných knihovny DLL, které při kompilaci s starší verzi kompilátoru a knihovny .

    > [!WARNING]
    > Pokud vytváříte propojení s Windows SDK 8.1 nebo starší, může dojít k těmto chybám nerozpoznaný externí symbol. V takovém případě by měla vyřešit chybu tak, že přidáte legacy_stdio_definitions.lib linkeru, zadejte, jak je popsáno výše.

   Řešení potíží s chybami nevyřešeného symbolu, můžete zkusit použít [dumpbin.exe](../build/reference/dumpbin-reference.md) prozkoumat symboly definované v binární soubor. Vyzkoušejte následující příkazový řádek pro zobrazení symbolů definovaných v knihovně.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **klíče GET a _getws**

   [Získá](../c-runtime-library/gets-getws.md) a [_getws](../c-runtime-library/gets-getws.md) funkce byly odebrány. Získá funkce byla odebrána ze standardní knihovny jazyka C v C11, protože nelze bezpečně použít. _Getws – funkce je rozšířením společnosti Microsoft, která je ekvivalentní získá jenom pro široké řetězce. Jako alternativa pro tyto funkce, zvažte použití [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws –](../c-runtime-library/reference/fgets-fgetws.md), [gets_s –](../c-runtime-library/reference/gets-s-getws-s.md), a [_getws_s –](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets a _cgetws –**

   [_Cgets](../c-runtime-library/cgets-cgetws.md) a [_cgetws –](../c-runtime-library/cgets-cgetws.md) funkce byly odebrány. Jako alternativa pro tyto funkce, zvažte použití [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) a [_cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Nekonečno a NaN formátování**

   V předchozích verzích nekonečno a hodnoty NaN by být formátována pomocí sadu řetězců sentinel konkrétní MSVC.

  - Nekonečno: 1.#INF

  - Tichý NaN: 1.#QNAN

  - Signalizace NaN: 1.#SNAN

  - Neomezené NaN: 1. #IND

  Některé z těchto formátů mohou mít předponu znakem a může formátována mírně liší v závislosti na šířku pole a přesnosti (někdy se neobvyklé účinky, například `printf("%.2f\n", INFINITY)` vytiskne 1. #J vzhledem k tomu, #INF by "zaokrouhlí" 2 číslice přesnost). C99 zavedeny nové požadavky toho, jak se má být formátováno nekonečno a hodnoty NaN. Implementace MSVC nyní splňuje tyto požadavky. Nové řetězce jsou následující:

  - Nekonečno: inf

  - Quiet NaN: nan

  - Signalizace NaN: nan(snan)

  - Neomezené NaN: nan(ind)

  Některé z těchto může začínat znakem. Pokud je specifikátor formátu velkými písmeny používali (%F místo %f), řetězce jsou vypsány velkými písmeny (`INF` místo `inf`), jako je povinný.

  [Scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkce se upravila tak analyzovat tyto nové řetězce, proto tyto řetězce nyní round-trip prostřednictvím `printf` a `scanf`.

- **Plovoucí desetinná čárka, formátování a analýzu**

   K vylepšení správnosti byly zavedeny nové plovoucí desetinná čárka, formátování a analýzu algoritmy. Tato změna ovlivňuje [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) rodinách funkcí, stejně jako funkce, jako jsou [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Staré formátování algoritmy vygeneruje jenom omezený počet číslic a pak by vyplnění zbývající desetinných míst s nulou. Která by obvykle generují řetězce, které by operace round-trip zpět původní hodnotu s plovoucí desetinnou, ale nebyly oceníte, pokud chcete získat přesné hodnoty (nebo jejich nejbližší desítkový zápis). Nový algoritmus formátování vygenerovat, protože mnoho číslic, které jsou nutné k reprezentaci hodnoty (nebo tak, aby vyplnil zadané přesnosti). Jako příklad vylepšení; Při tisku velké mocninou čísla 2 vezměte v úvahu výsledky:

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   Staré výstup:

    ```Output
    1208925819614629200000000
    ```

   Nový výstup:

    ```Output
    1208925819614629174706176
    ```

   Staré analýzy algoritmy byste měli považovat jenom až 17 platných číslic ze vstupního řetězce a by zrušit zbývající číslice. Tento přístup je dostatečné pro generovat aproximace Hodnota reprezentovaná tímto řetězcem a výsledkem je obvykle velmi blízko správně zakulacený výsledek. Novou implementaci bere v úvahu všechny číslice k dispozici a správně zakulacený výsledek pro všechny vstupy (až 768 číslic). Kromě toho tyto funkce nyní respektují režim (dát řídit přes fesetround).  Totiž potenciálně rozbíjející změny chování těchto funkcí může být výstup odlišné výsledky. Nové výsledky jsou vždy více než starých výsledků.

- **Šestnáctkové číslo a číslo s plovoucí čárkou nekonečno a NaN bod analýza kódu**

   Plovoucí desetinnou čárkou parsování algoritmy bude nyní analýzy hexadecimální s plovoucí desetinnou řetězce (jako jsou ty generovaných %a a specifikátory formátu printf %A) a všechny nekonečno a NaN řetězce, které jsou generovány `printf` funguje, jak je popsáno výše.

- **%A a %a nula odsazení**

   %A a %A formát specifikátorů formátu plovoucí číslo bodu jako šestnáctkové mantisy a exponentu binární. V předchozích verzích `printf` funkce by řetězců nesprávně panel nula. Například `printf("%07.0a\n", 1.0)` vytiskne 00x1p + 0, ve kterém by měl vytisknout 0x01p + 0. Tato chyba byla opravena.

- **%A a %a přesnosti**

   Výchozí přesnost specifikátorů formátu %A a %a byl 6 v předchozích verzích knihovny. Přesnost je nyní 13 pro soulad s standardu C.

   Jedná se o změnu chování modulu runtime ve výstupu jakékoli funkce používající formátovací řetězec s %A nebo %. V původní chování může být výstup jde pomocí specifikátoru %A "1.1A2B3Cp + 111". Výstup pro stejnou hodnotu je nyní "1.1A2B3C4D5E6F7p + 111". Chcete-li získat staré chování, můžete určit přesnost, například %.6A. Zobrazit [specifikace přesnosti](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **Specifikátor %F**

   Nově se podporuje specifikátor formátu nebo převodu %F. Je funkčně ekvivalentní specifikátoru formátu %f, s tím rozdílem, že nekonečno a hodnoty NaN jsou formátovány pomocí velká písmena.

   V předchozích verzích použitá k analýze F a N jako délka modifikátory implementace. Toto chování ze zpět stáří segmentovaným adresních prostorů: tyto modifikátory délka byly použity k označení daleko a téměř ukazatele, hodnoty, stejně jako v % Fp nebo %Ns. Toto chování se odebrala. Pokud je nalezen %F, je nyní považován za specifikátor formátu %F; v případě %N je nyní považován za neplatný parametr.

- **Exponent, formátování**

   %E a %E formát specifikátorů formátu plovoucí číslo bodu jako desítkové mantisy a exponentu. Specifikátory formátu %G a %g také formátování čísel v tomto formuláři v některých případech. V předchozích verzích by CRT vždy generovat řetězce s trojmístný exponenty. Například `printf("%e\n", 1.0)` vytiskněte 1.000000e + 000, což bylo nesprávné. Jazyk C vyžaduje, je-li exponent reprezentovat pomocí jednoho nebo dvou číslic, pak pouze dvě číslice se mají vytisknout.

   V sadě Visual Studio 2005 byl přidán globální shoda přepínač: [_set_output_format –](../c-runtime-library/set-output-format.md). Program lze volat tuto funkci s argumentem _TWO_DIGIT_EXPONENT, povolení vyhovující exponentu tisku. Výchozí chování se změnil na vyhovující standardům exponentu tisk režimu.

- **Ověření řetězce formátu**

   V předchozích verzích `printf` a `scanf` funkce bude přijímat tiše mnoho neplatné formátovací řetězce, někdy s neobvyklou účinky. Třeba % hlhlhld budou považované za %d. Všechny neplatné formátovací řetězce jsou nyní považovány za neplatné parametry.

- **fopen – režim řetězec ověření**

   V předchozích verzích `fopen` řadu funkcí, jako tiše přijmout některé řetězce neplatný režim `r+b+`. Neplatný režim řetězce jsou nyní zjištěn a považovány za neplatné parametry.

- **Režim _O_U8TEXT**

   [_Setmode](../c-runtime-library/reference/setmode.md) funkce nyní správně hlásí režim pro datové proudy otevřené in_O_U8TEXT režimu. V předchozích verzích knihovny ho zasílat zprávy tyto proudy jako otevírané v _O_WTEXT.

   Toto je zásadní změnu, pokud váš kód interpretuje _O_WTEXT režim pro datové proudy, kde kódování je UTF-8. Pokud aplikace nepodporuje UTF_8, zvažte přidání podpory pro toto stále běžnější kódování.

- **snprintf – a vsnprintf –**

   [Snprintf –](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) a [vsnprintf –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) functions je nyní implementována. Starší kód často najdete definice makra verze těchto funkcí nejsou implementované knihovny CRT, protože se už je nepotřebujete v novější verzi. Pokud [snprintf –](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) nebo [vsnprintf –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) je definován jako makra před zahrnutím \<stdio.h >, nyní kompilace se nezdaří s chybou, která určuje, kde byl definován makra.

   Za normálních okolností opravu tohoto problému je odstranit všechny deklarace `snprintf` nebo `vsnprintf` v uživatelském kódu.

- **tmpnam – vygeneruje použitelné názvy souborů**

   V předchozích verzích `tmpnam` a `tmpnam_s` funkce generované názvy souborů v kořenové složce jednotky (například \sd3c.). Tyto funkce generují nyní cesty k souborům použitelný název v dočasném adresáři.

- **Zapouzdření souboru**

   V předchozích verzích, úplný typ souboru byl definován veřejně v \<stdio.h >, aby bylo možné pro uživatelský kód pro získání přístupu do souboru a upravte její vnitřní součásti. Knihovny se změnil na skrýt podrobnosti implementace. Jako součást této změny souboru, jak jsou definovány v \<stdio.h > je nyní neprůhledné typem a její členy jsou nebyla přístupná z mimo samotný CRT.

- **_outp – a _inp –**

   Funkce [_outp –](../c-runtime-library/outp-outpw-outpd.md), [_outpw –](../c-runtime-library/outp-outpw-outpd.md), [_outpd –](../c-runtime-library/outp-outpw-outpd.md), [_inp –](../c-runtime-library/inp-inpw-inpd.md), [_inpw –](../c-runtime-library/inp-inpw-inpd.md), a [_inpd – ](../c-runtime-library/inp-inpw-inpd.md) byly odebrány.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h >, \<malloc.h >, a \<sys/stat.h >

- **strtof a wcstof**

   `strtof` a `wcstof` funkce se nepodařilo nastavit `errno` k ERANGE při hodnota se nedá prezentovat jako s float. Tato chyba byla specifická pro tyto dvě funkce. `strtod`, `wcstod`, `strtold`, a `wcstold` funkce bylo to neovlivní. Tento problém byl opraven a k zásadní změně modulu runtime.

- **Funkce přidělení**

   V předchozích verzích, funkce přidělení (`_aligned_malloc`, `_aligned_offset_malloc`atd) by tiše přijímat žádosti o blok s zarovnání 0. Požadované zarovnání musí být mocninou čísla 2, který není true nula. Požadovaným zarovnáním 0 je nyní považován za neplatný parametr. Tento problém byl opraven a k zásadní změně modulu runtime.

- **Funkce haldy**

   `_heapadd`, `_heapset`, A `_heapused` funkce byly odebrány. Tyto funkce někdo funkční CRT byl aktualizován na použití Windows haldy.

- **smallheap**

   `smallheap` Možnost propojení se odebrala. Zobrazit [propojit možnosti](../c-runtime-library/link-options.md).

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   Podpis metody `wcstok` funkce byl změněn tak, aby odpovídaly toho, co vyžaduje C Standard. V předchozích verzích knihovny se signatura této funkce:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Interní kontext vlákno používá ke sledování stavu mezi volání, což se děje u `strtok`. Funkce teď má podpis `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)`a vyžaduje volajícího k předání kontextu jako třetí argument funkce.

   Nový `_wcstok` funkce byla přidána s starý podpis k usnadnění přenos. Při kompilaci kódu jazyka C++, k dispozici je také přetížení vložené `wcstok` , který má starý podpis. Toto přetížení je deklarován jako zastaralé. V kódu jazyka C, může způsobit define_CRT_NON_CONFORMING_WCSTOK `_wcstok` má být použit místo `wcstok`.

#### <a name="timeh"></a>\<time.h>

- **clock**

   V předchozích verzích [hodiny](../c-runtime-library/reference/clock.md) funkce bylo implementováno pomocí rozhraní Windows API [GetSystemTimeAsFileTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime). S touto implementací clock – funkce záleželo na systémový čas a nebyla proto nemusí být monotónní. Clock – funkce má byla reimplemented z hlediska [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) a je nyní monotónní.

- **fstat – a _utime**

   V předchozích verzích [_stat](../c-runtime-library/reference/stat-functions.md), [fstat –](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), a [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) funkce zpracování letní čas nesprávně. Před Visual Studio 2013 všechny tyto funkce nesprávně upravena časy (běžný čas) jako by byly v letní čas.

   V sadě Visual Studio 2013 byl opraven problém v **_stat** řadu funkcí, ale s podobnými problémy v **fstat –** a **_utime** nebyly oprava rodinách funkcí. Tato částečná oprava vedlo k problémům kvůli nekonzistencí mezi funkcemi. **Fstat –** a **_utime** rodinách funkcí teď jsme opravili, takže všechny tyto funkce nyní zpracovávají letní čas správnou a konzistentní.

- **asctime**

   V předchozích verzích [asctime –](../c-runtime-library/reference/asctime-wasctime.md) funkce by vyplnění řádu dnů s počáteční nulou, například: `Fri Jun 06 08:00:00 2014`. Specifikace vyžaduje, aby těchto dnů bude doplněn s přední místa, stejně jako v `Fri Jun  6 08:00:00 2014`. Tento problém byl opraven.

- **STRFTIME a wcsftime**

   `strftime` a `wcsftime` functions nyní podporují %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u a %V specifikátory formátu. Kromě toho modifikátory E a O jsou analyzovány, ale ignoruje.

   Specifikátor formátu %c je zadán jako vytváření "příslušné datum a čas reprezentace" pro aktuální národní prostředí. V národním prostředí C tento zápis musí být stejný jako `%a %b %e %T %Y`, stejný formulář, protože se vytvářejí pomocí `asctime`. V předchozích verzích se nesprávně naformátováno specifikátor formátu %c dobu používání `MM/DD/YY HH:MM:SS` reprezentace. Tento problém byl opraven.

- **timespec a TIME_UTC**

   \<Time.h > teď definuje záhlaví `timespec` typ a `timespec_get` C11 standardní funkci. Kromě toho makra TIME_UTC pro použití se službou `timespec_get` fungovat, je teď definovaný. Tato aktualizace je zásadní změny pro kód, který má konfliktní definice pro některý z těchto identifikátorů.

- **CLOCKS_PER_SEC**

   Makro CLOCKS_PER_SEC teď rozšíří na celé číslo typu `clock_t`, jak je požadováno v jazyce C.

####  <a name="BK_STL"></a> Standardní knihovna C++

Pokud byte chtěli povolit nové optimalizace a kontroly ladění, implementace standardní knihovny C++ záměrně neumožňuje binární kompatibilitu mezi verzemi. Proto při použití standardní knihovny C++ nelze objektové soubory a statické knihovny, které jsou kompilovány pomocí různých verzí, směšovat v jednom binárním souboru (EXE nebo DLL) a objekty standardní knihovny C++ nelze předávat mezi binárními soubory, které jsou kompilovány pomocí různých verzí. Takovéto směšování objektů vyvolává chyby linkeru týkající se neshod _MSC_VER. (_MSC_VER je makro, které obsahuje hlavní verzi kompilátoru, například 1800 pro Visual Studio 2013.) Tato kontrola nezjistí směšování knihoven DLL a nelze zjišťovat kombinace, která zahrnuje sady Visual Studio 2008 nebo dřívější.

- **Soubory k zahrnutí standardní knihovny C++**

   Byly provedeny některé změny do struktury zahrnout v záhlaví standardní knihovny C++. Patří mezi sebou neurčené způsoby mohou hlavičky standardní knihovny C++. Obecně platí by měl napište svůj kód tak, aby pečlivě zahrnuje všechny hlavičky, která potřebuje podle standardu jazyka C++ a nemusí spoléhat na které hlavičky standardní knihovny C++ zahrnují které dalších hlaviček standardní knihovny C++. Díky tomu je kód přenosný napříč platformy a verze. Alespoň dvě záhlaví změny v sadě Visual Studio 2015 vliv uživatelského kódu. Nejprve je potřeba \<řetězec > už obsahuje \<iterátor >. Druhý, \<řazené kolekce členů > teď deklaruje `std::array` bez zahrnutí všech \<pole >, což může přerušit kódu pomocí následující kombinace konstrukce kódu: váš kód obsahuje proměnnou s názvem "pole" a vy musíte pomocí směrnice " s použitím oboru názvů std; ", a zahrnout hlavičku standardní knihovny C++ (jako \<funkční >), který obsahuje \<řazené kolekce členů >, které je teď deklaruje `std::array`.

- **steady_clock**

   \<Chrono > provádění [steady_clock](../standard-library/steady-clock-struct.md) došlo ke změně pro splnění požadavků standardu C++ steadiness a monotonicity. `steady_clock` je teď na základě [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) a `high_resolution_clock` je nyní definice typu `steady_clock`. V důsledku toho v sadě Visual Studio `steady_clock::time_point` je nyní definice typu `chrono::time_point<steady_clock>`; však není nutně případ v jiných implementacích.

- **alokátorů a const**

   Teď vyžadujeme porovnání rovnosti nebo nerovnosti allocator tak, aby přijímal konstantní argumenty na obou stranách. Pokud vaše alokátorů definovat tyto operátory tímto způsobem

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   potom byste je aktualizovat a deklarovat jako const členy:

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **Const elementy**

   Standard jazyka C++ vždy zakázal kontejnery prvků const (jako jsou vektorové\<const T >, nebo nastavte\<const T >). Visual Studio 2013 a starší přijetí těchto kontejnerů. V aktuální verzi takových kontejnerů kompilace selže.

- **std::Allocator:: uvolnění**

   V sadě Visual Studio 2013 a dřívějších verzí `std::allocator::deallocate(p, n)` ignoruje argument předaný pro *n*.  Standard jazyka C++, která vždy vyžaduje *n* musí být rovna hodnotě předané jako první argument k vyvolání `allocate` který vrácen *p*. Ale v aktuální verzi, hodnota *n* je prozkoumat. Kód, který se předá argumenty pro *n* , která se liší od co standard vyžaduje, může dojít k chybě za běhu.

- **hash_map – a hash_set –**

   Nestandardní hlavičky souborů \<hash_map > a \<hash_set > jsou zastaralé v sadě Visual Studio 2015 a bude v budoucí verzi odebrána. Použití \<unordered_map > a \<unordered_set > místo toho.

- **komparátorů a operator()**

   Asociativní kontejnery ( \<mapy > rodina) nyní vyžadovat, aby jejich komparátorů, aby volání operátory const-callable funkce. Následující kód v deklaraci třídy Komparátor nyní selže při kompilaci:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Chcete-li vyřešit tuto chybu, změňte za deklarací funkce:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **typové vlastnosti**

   Byly odebrány staré názvy pro typové vlastnosti ze starší verze standard C++ konceptu. Tyto byly změněny v C ++ 11 a byl aktualizován na C ++ 11. hodnoty v sadě Visual Studio 2015. V následující tabulce jsou uvedeny staré i nové názvy.

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
   |has_trivial_copy|is_trivially_copy_constructible –|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible –|

- **Launch::Any a launch::sync zásady**

   Nestandardní `launch::any` a `launch::sync` zásady byly odstraněny. Namísto toho `launch::any`, použijte `launch:async | launch:deferred`. Pro `launch::sync`, použijte `launch::deferred`. Zobrazit [launch – výčet](../standard-library/future-enums.md#launch).

####  <a name="BK_MFC"></a> Knihovna MFC a ATL

- **Knihovna MFC (Microsoft Foundation Classes)**

   je již součástí "Typické" instalací sady Visual Studio z důvodu jeho velikost. Chcete-li nainstalovat knihovny MFC, zvolte **vlastní** možnost instalace v instalačním programu sady Visual Studio 2015. Pokud už máte nainstalovanou sadu Visual Studio 2015, můžete nainstalovat MFC spuštěním **sady Visual Studio** znovu instalační program. Zvolte **vlastní** možnost instalace a klikněte na tlačítko **Microsoft Foundation Classes**. Můžete spustit **sady Visual Studio** nastavení z **ovládací panely** ovládací prvek **programy a funkce**, nebo z instalačního média.

   Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.

####  <a name="BK_ConcRT"></a> Concurrency Runtime

- **YIELD – makro v konfliktu s concurrency::Context::Yield Windows.h**

   Modulu Runtime souběžnosti, který dřív používal `#undef` definice makra Yield jak zamezit konfliktům mezi Yield makro definované v Windows.h h a `concurrency::Context::Yield` funkce. To `#undef` se odebral a nové nekonfliktní ekvivalentní rozhraní API volání [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) byla přidána. Je v konfliktu s Yield obejít, můžete buď aktualizovat váš kód volat `YieldExecution` namísto toho funkci nebo před a za `Yield` název funkce pomocí závorek ve volání servery, jako v následujícím příkladu:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Vylepšení kompilátoru v sadě Visual Studio 2015

Při upgradu z předchozí verze kódu, může také dojít chyb kompilátoru, které jsou z důvodu vylepšení v sadě Visual Studio 2015. Těmto vylepšením nedojde k narušení binární kompatibilitu z předchozích verzí sady Visual Studio, ale může vést k chybám kompilátoru kde žádný byly generované před. Další informace najdete v tématu [Visual C++ co na nový 2003 – 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

V sadě Visual Studio 2015 probíhající vylepšení shoda s kompilátorem prostředí můžete někdy změnit, jak kompilátor rozpozná existující zdrojový kód. Nové nebo jiné chyby v důsledku toho může dojít během sestavování nebo dokonce behaviorální rozdíly v kódu, který dříve vytvořené a vypadal jako správně spustit.

Tyto rozdíly naštěstí mít žádné nebo téměř žádné dopad na většinu zdrojového kódu. Pokud zdrojový kód nebo jiné změny jsou potřeba k vyřešení těchto rozdílů, opravy jsou obvykle malé a přímočaré. Přidali jsme mnoho příkladů dříve přijatelné zdrojový kód, který může být nutné změnit *(před)* a opravy je opravit *(po)*.

I když váš zdrojový kód nebo jiných artefaktů sestavení, můžete tyto rozdíly ovlivňují, neovlivňují binární kompatibilitu mezi aktualizace verze sady Visual Studio. A *narušující změna* je přísnější a může ovlivnit binární kompatibilitu, ale tyto druhy binární kompatibilitu konce vyskytovat jenom mezi hlavními verzemi sady Visual Studio, například mezi Visual Studio 2013 a Visual Studio 2015. Informace o nejnovější změny, ke kterým došlo mezi Visual Studio 2013 a Visual Studio 2015, najdete v části [Visual Studio 2015 nejnovějšími změnami](#VC_2015).

- [Vylepšení v sadě Visual Studio 2015](#VS_RTM)

- [Vylepšení shody aktualizace 1](#VS_Update1)

- [Vylepšení ve verzi Update 2](#VS_Update2)

- [Vylepšení shody aktualizací Update 3](#VS_Update3)

###  <a name="VS_RTM"></a> Vylepšení v sadě Visual Studio 2015

- Možnost /Zc:forScope-

   Možnost kompilátoru `/Zc:forScope-` je zastaralá a bude v budoucí verzi odebrána.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Tuto možnost obvykle použil aby nestandardní kód, který používá smyčku proměnné od chvíle, kdy podle standardu, že by měl nepřejdou mimo rozsah. Byla pouze nezbytné při kompilaci s `/Za` možnost, neboť bez `/Za`, použití pro proměnnou smyčky po konci smyčky je vždycky povolená. Pokud vám nezáleží shoda se standardy (například, pokud není určena pro přenositelnost na jiné kompilátory kódu), může vypnout `/Za` možnost (nebo nastavit **zakázat jazyková rozšíření** vlastnost **ne** ). Pokud vás zajímají psaní kódu, přenosná, který vyhovuje standardům, byste měli přepsat váš kód, který vyhovuje standardu přesunutím deklaraci těchto proměnných do bodu mimo smyčku.

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

   `/Zg` – Možnost kompilátoru (Generovat prototypy funkcí) už nejsou k dispozici. Tato možnost kompilátoru dříve byla zrušena.

- Jednotkové testy můžete spustit již s C + +/ CLI z příkazového řádku pomocí mstest.exe. Místo toho používejte vstest.console.exe. Zobrazit [možnosti příkazového řádku VSTest.Console.exe](/visualstudio/test/vstest-console-options).

- **Mutable – klíčové slovo**

   **Proměnlivé** specifikátor třídy úložiště již není povolena na místech, kde dříve ho zkompilovány bez chyb. Nyní, kompilátor dochází k chybě C2071 (neplatná třída úložiště). Podle standardu **proměnlivé** specifikátor lze použít pouze u názvů datové členy třídy a nejde použít u názvů deklarovaný jako const nebo statické a nedá se použít k odkazování členů.

   Zvažte například následující kód:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Předchozí verze kompilátoru přijímají toto, ale teď kompilátor poskytuje následující chybu:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Chcete-li chybu opravit, odeberte redundantní **proměnlivé** – klíčové slovo.

- **char_16_t a char32_t**

   Kterou již nebudete používat `char16_t` nebo `char32_t` jako aliasů v **typedef**, protože tyto typy jsou nyní považovány za předdefinované. Je běžné, že uživatelé a autoři knihovny k definování `char16_t` a `char32_t` jako aliasy `uint16_t` a `uint32_t`v uvedeném pořadí.

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

   Chcete-li aktualizovat váš kód, odeberte **– typedef** deklarace a přejmenujte další identifikátory, které kolidují s těmito názvy.

- **Parametry šablony bez typu**

   Určitý kód, který zahrnuje parametry šablony bez typu je nyní správně kontroluje kompatibilita typů při poskytování explicitní argumenty šablony. Například následující kód zkompilován bez chyby v předchozích verzích sady Visual Studio.

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

   Aktuální kompilátor správně vrátí chybu, protože typ parametru šablony neodpovídá argument šablony (parametru je ukazatel na člena const, ale funkce f je nekonstantní):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Chcete-li vyřešit tuto chybu v kódu, ujistěte se, že typ argumentu šablony používáte odpovídá deklarovaného typu parametru šablony.

- **__declspec(align)**

   Kompilátor už přijímá `__declspec(align)` na funkce. Tento konstruktor vždy ignorovalo se, ale nyní způsobí chybu kompilátoru.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Chcete-li tento problém vyřešit, odeberte `__declspec(align)` z deklarace funkce. Protože to nemělo žádný vliv, jeho odebrání nic nezmění.

- **Zpracování výjimek**

   Existuje několik změn pro zpracování výjimek. Nejprve objekty výjimky musí být kopírovatelné nebo přesouvatelný. Následující kód zkompilován v sadě Visual Studio 2013, ale nebude kompilovat v sadě Visual Studio 2015:

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

   Problém je, že je kopírovací konstuktor je soukromé, tak, aby objekt nelze zkopírovat, protože dochází v běžném zpracování výjimky. To samé platí při deklaraci konstruktoru kopie **explicitní**.

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

   A aktualizujte svůj kód, ujistěte se, že je kopírovací konstruktor pro svůj objekt výjimky **veřejné** a není označena jako **explicitní**.

   Zachycování výjimky podle hodnoty vyžaduje také kopírovatelné objekt výjimky. Následující kód zkompilován v sadě Visual Studio 2013, ale nebude kompilovat v sadě Visual Studio 2015:

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

   Tento problém můžete opravit tak, že změníte typ parametru pro položku **catch** na odkaz.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Řetězcové literály, za nímž následuje makra**

   Kompilátor nyní podporuje uživateli definované literály. Řetězcové literály, za nímž následuje makra bez žádné prázdné znaky použité v důsledku toho jsou interpretovány jako uživateli definované literály, které by mohla vést k chybám nebo neočekávané výsledky. Například v předchozím kompilátory následující kód zkompilován úspěšně:

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

   Kompilátor interpretuje tento kód jako řetězcový literál "hello" následované makro, které se rozbalí do "zde", a potom byly spojeny dva řetězcové literály do jedné. V sadě Visual Studio 2015, kompilátor interpretuje toto pořadí jako uživatelem definovaného literálu, ale protože neexistuje žádný odpovídající uživatelem definovaného literálu `_x` definovaný, vrátí chybu.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Chcete-li tento problém vyřešit, přidejte mezeru mezi řetězcový literal a makro.

- **Sousední řetězcové literály**

   Podobně jako na předchozí, z důvodu související změny v analýze řetězce byly sousedních textových literálů (buď široký nebo úzký znak řetězcových literálů) bez žádné prázdné znaky interpretován jako jeden řetězec zřetězených v předchozích verzích Visaul C++. V sadě Visual Studio 2015 teď musíte přidat prázdné znaky mezi dva řetězce. Například musíte změnit následující kód:

    ```cpp
    char * str = "abc""def";
    ```

   Chcete-li vyřešit tento problém, přidejte mezeru mezi dva řetězce:

    ```cpp
    char * str = "abc" "def";
    ```

- **Nové umístění a delete**

   Byla provedena změna **odstranit** operátor pamětí souladu s C ++ 14, standardní. Podrobnosti o změně standardy najdete v [C++ velikostí Dealokace](http://isocpp.org/files/papers/n3778.html). Změny přidejte formulář globálního **odstranit** operátor, který přijímá parametr velikosti. Rozbíjející změnu je, že pokud jste dříve používali operátor **odstranit** se stejným podpisem (tak, aby odpovídaly s **nové umístění** operátor), obdržíte chybu kompilátoru (C2956, to se stává v okamžiku, kdy se používá nové umístění, protože to je pozice v kódu, kde kompilátor se pokusí identifikovat příslušné odpovídající **odstranit** operátor).

   Funkce `void operator delete(void *, size_t)` byla **umístění operátoru delete** odpovídající operátor **umístění nového** funkce `void * operator new(size_t, size_t)` v C ++ 11. Pomocí C ++ 14 velikostí dealokace, tato funkce delete je teď *funkce zrušení přidělení obvykle* (globální **odstranit** operátor). Standardní vyžaduje, pokud použijte nové umístění vyhledá odpovídající funkce delete a vyhledá funkce zrušení přidělení obvyklé, program chybně vytvořený.

   Předpokládejme například, že váš kód definuje, jak **umístění nového** a **umístění operátoru delete**:

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   K problému dochází kvůli shodu v podpisech funkcí mezi **umístění operátoru delete** operátoru, které jste definovali a nové globální velikosti **odstranit** operátor. Zvažte, jestli můžete použít jiný typ než `size_t` libovolné **umístění nového** a **odstranit** operátory. Typ `size_t` **– typedef** závisí na kompilátoru; je **typedef** pro **unsigned int** v MSVC. Dobrým řešením je použití Výčtový typ jako je například tento:

    ```cpp
    enum class my_type : size_t {};
    ```

   Změňte definicí **umístění nového** a **odstranit** použít tento typ, jako druhý argument místo `size_t`. Také budete muset aktualizovat volání do nového umístění předejte nový typ (například pomocí `static_cast<my_type>` pro převod z celočíselnou hodnotu) a aktualizace definice **nové** a **odstranit** přetypovat zpět typ celého čísla. Není nutné používat **výčtu** pro tento účel; typ třídy s `size_t` člen by také fungovat.

   Alternativním řešením je, že je možné odstranit **umístění nového** úplně se vynechá. Pokud váš kód používá **umístění nového** implementace fondu paměti, kde argument umístění je velikost objektu se přidělené nebo odstraněna, pak velikostí dealokace funkce může být vhodné nahradit vlastním kódem fondu vlastní paměti a můžete vyřadit umístění funkce a stačí použít vlastní dvěma argumenty **odstranit** operátor namísto funkce umístění.

   Pokud nechcete aktualizovat váš kód okamžitě, můžete se vrátit k staré chování pomocí možnosti kompilátoru `/Zc:sizedDealloc-`. Pokud použijete tuto možnost, odstranění dvěma argumenty funkce neexistují a nebude způsobovat konflikt s vaší **umístění operátoru delete** operátor.

- **Sjednocení datových členů**

   Data členů sjednocení může mít už typy odkazů. Následující kód zkompilován úspěšně v sadě Visual Studio 2013, ale dojde k chybě v sadě Visual Studio 2015.

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

   Chcete-li tento problém vyřešit, změňte typy odkazů na ukazatel nebo hodnotu. Změna typu ukazatele vyžaduje změny v kódu, který používá pole typu union. Kód na hodnotu by změna dat uložených ve sjednocení, které ovlivňují ostatní pole, protože pole ve sjednocení typů sdílejí stejnou paměť. V závislosti na velikosti hodnotu se může také změnit velikost sjednocení.

- Anonymní sjednocení jsou teď další splňující podmínky standardu. Předchozí verze kompilátoru generované představují explicitní konstruktor a destruktor pro anonymní sjednocení. Odstraní se tyto funkce generované kompilátorem v sadě Visual Studio 2015.

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

   Chcete-li vyřešit tento problém, poskytnout vlastní definice konstruktor nebo destruktor.

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

- **Sjednocení s anonymní struktury**

   Aby bylo možné v souladu se standardem, chování za běhu změnil členům anonymní struktury ve sjednoceních. Konstruktor pro anonymní struktury členům ve sjednocení je už nebude implicitně volána při vytvoření těchto sjednocení. Destruktor pro anonymní struktury členům ve sjednocení také, je už nebude implicitně volána, když sjednocení dostane mimo rozsah. Uvažujme následující kód, ve kterém sjednocení U obsahuje anonymní struktury, která obsahuje strukturu s názvem člena S, který má destruktor.

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

   V sadě Visual Studio 2013 je konstruktor S volá, když se vytvoří sjednocení a destruktor S se volá, když je pro funkci f zásobník vyčištěn. Ale v sadě Visual Studio 2015, se nazývá konstruktor a destruktor. Kompilátor obsahuje upozornění týkající se této změny chování.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Chcete-li obnovit původní chování, pojmenujte anonymní struktury. Modul runtime chování – a anonymní struktury je stejný, bez ohledu na verze kompilátoru.

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

   Případně zkuste přesunout konstruktor a destruktor kód do nové funkce a přidejte volání těchto funkcí z konstruktor a destruktor pro sjednocení.

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

- **Šablony řešení**

   Překlad názvů pro šablony byly provedeny změny. V jazyce C++ při zvažování kandidáty pro rozlišení názvu může být případ, že jeden nebo více názvů uvažovanou jako potenciální shody vytváří instance neplatná šablona. Tyto neplatné instancí nezpůsobí obvykle chyby kompilátoru zásada říká SFINAE (nahrazení selhání je není chybovou).

   Nyní pokud SFINAE vyžaduje, aby kompilátor pro vytvoření instance specializace šablony třídy, pak všechny chyby, ke kterým dochází během tohoto procesu jsou chyby kompilátoru. V předchozích verzích by kompilátor ignorovat tyto chyby. Zvažte například následující kód:

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

   Pokud kompilujete s aktuální kompilátorem, zobrazí se následující chyba:

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

   Důvodem je, že při prvním vyvolání is_base_of – třída `D` ještě nebyl definován.

   V tomto případě opravy nechcete použít tyto typové vlastnosti, dokud je definována třída. Pokud přesunete definice `B` a `D` na začátek souboru kódu vyřeší chybu. Pokud jsou definice v souborech hlaviček, zkontrolujte pořadí příkazů zahrnout soubory hlaviček, abyste měli jistotu, že žádné definice tříd jsou zkompilovány před problematický šablony používá.

- **Kopírovací konstruktory**

   V sadě Visual Studio 2013 a Visual Studio 2015 kompilátor generuje kopírovací konstruktor pro třídu, pokud tato třída má konstruktor přesunutí definovaný uživatelem, ale žádná uživatelem definovaného kopírovacího konstruktoru. V Dev14 tento implicitně generovaný kopírovací konstuktor je také označena, "= delete".

<!--From here to VS_Update1 added 04/21/2017-->

- **hlavní deklarovány jako extern "C" nyní vyžaduje typ vrácené hodnoty.**

   Následující kód vytvoří nyní C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Chcete-li vyřešit chybu, přidejte návratového typu:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **Název typu není povolený v inicializátoru člena**

   Následující kód vytvoří nyní C2059:

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

- **Třída úložiště na explicitní specializace je ignorován.**

   V následujícím kódu je ignorován specifikátor třídy úložiště statické

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

- **Konstanty používané static_assert uvnitř šablony třídy se vždy nezdaří.**

   Následující kód způsobí, že `static_assert` vždy selhání:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Chcete-li tento problém obejít, zabalit hodnotu v **struktura**:

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

- **Pravidla pro dopředné deklarace. (Platí pouze pro C.)**

   Následující kód vytvoří nyní C2065:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Chcete-li vyřešit tento problém, přidáte správné dopředné deklarace:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Konzistentnější výkon typy ukazatelů na funkci**

   Následující kód vytvoří nyní C2197:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Nejednoznačné volání přetížené funkce**

   Následující kód vytvoří nyní C266: 'N::bind': nejednoznačné volání přetížené funkce

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

   Oprava chyby, se můžete plně kvalifikovat volání `bind: N::bind(...)`. Nicméně pokud tuto změnu je manifest prostřednictvím nedeklarovaný identifikátor (C2065), pak může být vhodné opravit to s **pomocí** deklarace místo.

   Tento model se často stane s ComPtr a ostatními typy v `Microsoft::WRL` oboru názvů.

- **Opravte nesprávné adresu**

   Následující kód nyní generuje upozornění C2440: '=': nelze převést z ' typ *' na 'type'. Chcete-li vyřešit chybu, změnit & (typ) na (typ) a (& f()) k (f()).

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

- **Textový literál je pole s konstantní**

   Následující kód nyní generuje upozornění C2664: "void f (void *)': nejde převést argument 1 z" const char (*) [2]' k ' void * "

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Oprava chyby, změňte typ parametru funkce na `const void*`, nebo jinak změňte obsah `h` , aby vypadala jako v tomto příkladu:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **C ++ 11 UDL řetězce**

   Následující kód nyní generuje chybu C3688: neplaná přípona literálu "L"; operátor literálu nebo šablona operátoru literálu ' operator "" L "nebyl nalezen

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Oprava chyby, změňte kód pro vložení mezery:

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

   V příkladu výše `MACRO` je už analyzovat jako tokeny dva (řetězec, který následuje makra). Nyní je analyzován jako jeden token UDL. Totéž platí i pro L "" L"", který byl dříve analyzovat jako L"" a L "" a teď je analyzován jako L "" L a "".

   Řetězec zřetězení pravidla přenesla také do stavu kompatibility se standardem, což znamená, že je ekvivalentní k L "ab" L "a" "b". Zřetězení řetězců s Šířka znaku různých nebyl přijat předchozích verzích sady Visual Studio.

- **Prázdný znak zcela c ++ 11**

   Následující kód nyní generuje chybu C2137: prázdná Znaková konstanta

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Oprava chyby, změňte kód, který null explicitní:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **Výjimky MFC nejde zachytit podle hodnoty, protože nejsou kopírovatelné**

   Následující kód v aplikaci MFC způsobí chybu C2316: Kdyby ": nejde zachytit, protože destruktor nebo kopírovací konstuktor jsou nedostupné nebo odstraněné

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

   Chcete-li vyřešit kód, můžete změnit blok catch, který má `catch (const D &)` ale lepší řešení je obvykle použít makra MFC TRY/CATCH.

- **alignof je nyní klíčové slovo**

   Následující kód nyní generuje chybu C2332: 'class': chybí název značky. Chcete-li vyřešit kód musíte přejmenovat třídu nebo, pokud třída provádí samé jako **alignof**, stačí nahradit třídy klíčové slovo new.

    ```cpp
    class alignof{}
    ```

- **constexpr je nyní klíčové slovo**

   Následující kód nyní generuje chybu C2059: Chyba syntaxe: ')'. Pokud chcete kód opravit, je nutné přejmenovat jakoukoli funkci nebo názvy proměnných, které se nazývají "constexpr".

    ```cpp
    int constexpr() {return 1;}
    ```

- **Typy přesouvatelných nemůže být konstantní**

   Když se funkce vrátí typ, který má v úmyslu přesunout, by neměl být její typ vrácené hodnoty **const**.

- **Odstraněné kopírovací konstruktory**

   Následující kód vytvoří nyní společnosti C2280:: S(S &&)': Pokus o odkazování na odstraněnou funkci:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Chcete-li opravit chybu, použijte přímé inicializace pro `S2`:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Převod na ukazatel na funkci pouze vygeneruje, když žádné zachycení lambdy**

   Následující kód vytvoří upozornění C2664 v sadě Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Chcete-li chybu opravit, odeberte `=` ze seznamu zachycení.

- **Nejednoznačné volání zahrnující operátory převodu**

   Následující kód nyní generuje chybu C2440: "přetypování": nelze převést z "S2" na "S1":

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

   Oprava chyby, explicitně volejte operátor převodu:

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   Následující kód nyní generuje chybu C2593: ' operator =' je nejednoznačný:

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

   Oprava chyby, explicitně volejte operátor převodu:

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Oprava neplatné kopírování inicializace v inicializaci členů nestatických dat (NSDMI)**

   Následující kód nyní vygeneruje Chyba upozornění C2664: 'S1::S1(S1 &&)': nelze převést argument 1 'bool' na ' const S1 & ":

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Oprava chyby, použijte přímé inicializace:

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Přístup k konstruktory uvnitř decltype – příkazy**

   Následující kód vytvoří nyní C2248: 'S::S': nelze přístup privátní člen deklarovaný v třídy ":

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

   Chcete-li vyřešit chybu, přidejte deklaraci typu friend pro `S2` v `S`:

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Výchozí ctor lambda se implicitně odstranila**

   Následující kód nyní generuje chybu C3497: Nelze vytvořit konstruktor instance lambdy:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Oprava chyby, zbavují uživatele nutnosti pro výchozí konstruktor, která se má volat. Pokud výraz lambda nezachytí nic, pak jej lze převést na ukazatel na funkci.

- **Výrazy lambda s operátorem odstraněných přiřazení**

   Následující kód nyní generuje chybu C2280:

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

   Chcete-li chybu opravit, nahraďte výraz lambda s třídou funktor nebo zbavují uživatele nutnosti provádět pomocí operátoru přiřazení.

- **Při pokusu o přesunutí objektu s odstraněné kopírovacího konstruktoru**

   Následující kód nyní generuje chybu C2280: 'přesouvat:: moveable(const moveable &)': Pokus o odkazování na odstraněnou funkci

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

   Chcete-li chybu opravit, použijte `std::move` místo:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **Místní třída nemůže odkazovat na jiné místní třídy definované později ve stejné funkci**

   Následující kód nyní generuje chybu C2079: na ' používá nedefinované struct 'main::S2'

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

   Oprava chyby, přesunout nahoru definici `S2`:

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

- **V těle konstruktoru odvozené nelze volat chráněné základní ctor.**

   Následující kód nyní generuje chybu C2248: 'S1::S1': Nelze získat přístup k chráněné člen deklarovaný ve třídě "S1.

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

   Chcete-li vyřešit chybu, v `S2` odeberte volání `S1()` z konstruktoru a v případě potřeby ji umístit v jiné funkci.

- **{} zabraňuje konverze na ukazatel**

   Následující kód vytvoří nyní C2439 'S::p': člen nešel inicializovat

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Chcete-li chybu opravit, odebrat závorky z kolem `0` nebo použijte jiný **nullptr** místo toho, jak je znázorněno v tomto příkladu:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Definice makra nesprávné a využití pomocí závorek**

   Následující příklad vytvoří nyní chyba C2008: ';': neočekávalo se v definici makra

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Chcete-li problém vyřešit, změňte na horní zobrazený řádek do `#define A();`

   Následující kód generuje chybu C2059: Chyba syntaxe: ").

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Pokud chcete kód opravit, odebrat mezery mezi objekt a ().

   Následující kód generuje chybu C2091: funkce vrací funkci:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Oprava chyby, odeberte závorky po příkazu DECLARE v S: `DECLARE;`.

   Následující kód vytvoří chyba C2062: typ "int neočekávaný

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Chcete-li problém vyřešit, definujte `A` tímto způsobem:

    ```cpp
    #define A int
    ```

- **Extra parens v deklaracích**

   Následující kód vytvoří chyba C2062: typ "int neočekávaný

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Chcete-li chybu opravit, odeberte závorky kolem `j`. Pokud závorky jsou nezbytné pro přehlednost a použijte **typedef**.

- **Konstruktory vygenerované kompilátorem a __declspec(novtable)**

   V sadě Visual Studio 2015 je vyšší pravděpodobnost, že konstruktory vygenerované kompilátorem vložené abstraktních tříd s virtuálními základními třídami může vystavit nesprávné použití `__declspec(novtable)` při použití v kombinaci s `__declspec(dllimport)`.

- **Auto vyžaduje jeden výraz v direct-list-initialization**

   Následující kód nyní generuje chybu C3518: 'testPositions': v kontextu direct-list-initialization může být typ pro 'auto' odvodit jenom z výrazu s jedním inicializátorem

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Oprava chyby, jednou z možností je inicializovat `testPositions` následujícím způsobem:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Kontroluje se typy a ukazatele na typy pro is_convertible –**

   Následující kód nyní způsobí, že se statický kontrolní výraz selže.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Chcete-li chybu opravit, změňte `static_assert` tak, aby porovnává ukazatele na `D` a `B2`:

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **deklarace __declspec(novtable) musí být konzistentní vzhledem k aplikacím**

   `__declspec` deklarace musí být konzistentní vzhledem k aplikacím napříč všechny knihovny. Následující kód vytvoří nyní porušení pravidla jednu definici (ODR):

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

###  <a name="VS_Update1"></a> Vylepšení shody aktualizace 1

- **Privátní virtuální základní třídy a nepřímé dědění**

   Předchozí verze kompilátoru povolené odvozené třídy za účelem volat členské funkce z jeho nepřímo odvozená `private virtual` základních tříd. Toto chování staré bylo nesprávné a neodpovídají standardu jazyka C++. Kompilátor už přijímá kódu napsaného v tímto způsobem a vydá Chyba kompilátoru C2280 ve výsledku.

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

- **Přetížený operátor new a delete – operátor**

   Předchozí verze kompilátoru povoleno bez členů **operátor new** a třetí **operátor delete** být deklarované jako statické a být deklarovány v oborech názvů, než je globální obor názvů.  Toto chování staré vytvořili riziko, že program by volat **nové** nebo **odstranit** operátor implementace, která má programátora, výsledný tiché chybný modul runtime chování. Kompilátor už přijímá kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C2323.

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

   Kromě toho Přestože kompilátor nedává konkrétní diagnostiky, operátor vložené **nové** se považuje za nedůvěryhodný.

- **Volání ' operator *typ*() "(uživatelem definovaný převod) na typech bez třídy**

   Předchozí verze kompilátoru povolené "operátor *typ*()" k volání na typech bez třídy při bezobslužném režimu je ignorována. Toto chování staré vytvořili riziko generování tiché chybného kódu, což vede k modulu runtime nepředvídatelné chování. Kompilátor už přijímá kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C2228.

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

- **Redundantní typename v elaborované specifikátory typu**

   Předchozí verze kompilátoru povolené **typename** v rozpracovaného typu je sémanticky nesprávný specifikátor, ale kód napsaný v tímto způsobem. Kompilátor už přijímá kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C3406.

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

- **Odvození typu polí ze seznamu inicializátorů**

   Předchozí verze kompilátoru nepodporuje odvození typu polí ze seznamu inicializátorů. Kompilátor nyní podporuje tento formulář odvození typu a v důsledku toho volání šablony funkce pomocí seznamy inicializátorů teď může být nejednoznačná nebo jiné přetížení může zvolit než v předchozích verzích kompilátoru. Jak tyto problémy vyřešit, program musí nyní explicitně určit přetížení, které určené programátorovi.

   Když toto nové chování způsobí, že řešení přetížení, které byste měli zvážit další Release candidate, který je stejně tak dobré jako historické Release candidate, stane se nejednoznačné volání a kompilátor vyvolá chybu kompilátoru C2668 ve výsledku.

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

   Když toto nové chování způsobí řešení přetížení, které byste měli zvážit další Release candidate, který je lepší shody než historické Release candidate, volání jednoznačně překládá na novou verzi Release candidate, což způsobí změnu v chování programu, které je pravděpodobně odlišná od programátor určené.

   Příklad 2: změny v řešení přetížení (před)

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

   Příklad 2: změny v řešení přetížení (po)

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

- **Obnovení upozornění switch – příkaz**

   Předchozí verze kompilátoru odebrat upozornění související s **přepnout** příkazů; toto upozornění ACLs byly obnoveny. Kompilátor vyvolá nyní obnovené upozornění a upozornění souvisejících s konkrétní případy (včetně výchozí případ) jsou teď vydaný na řádek obsahující problematický případu, nikoli na posledním řádku příkazu switch. Díky tomu teď vystavujících upozornění na samostatné řádky než v minulosti, upozornění dříve potlačit pomocí `#pragma warning(disable:####)` už dá potlačit očekávaným způsobem. Chcete-li tato upozornění potlačit očekávaným způsobem, může být potřeba přesunout `#pragma warning(disable:####)` direktivy řádku nad prvním případě problematické. Následují obnovené upozornění:

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

   Příklady dalších obnovené upozornění jsou k dispozici v jejich dokumentaci.

- **#include: použití specifikátoru nadřazený adresář '..' v názvu cesty** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistili použití specifikátoru nadřazený adresář '..' v cestě `#include` direktivy. Kód napsaný v tímto způsobem obvykle má zahrnout záhlaví, které existují mimo projekt nesprávně pomocí projektu relativní cesty. Toto chování staré vytvořili riziko, že program může zkompilovat zahrnutím souboru jiného zdroje než programátor určené nebo že tyto relativní cesty by být nepřenositelné na jiné prostředí sestavení. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C4464, pokud je povoleno.

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

   Kromě toho, přestože kompilátor nedává zvláštní diagnostiky, také doporučujeme, aby specifikátor nadřazený adresář ".." neměli použít k určení adresáře souborů k zahrnutí vašeho projektu.

- **#pragma optimize() přesahuje za konec souboru záhlaví** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru se nepodařilo rozpoznat změny nastavení příznaku optimalizace, které řídicí hlavičkovém souboru zahrnutém v jednotce překladu. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C4426 na umístění je problematický `#include`, pokud je povoleno. Pokud argumenty příkazového řádku pro kompilátor nastaven změny jsou v konfliktu s příznaky optimalizace se pouze objeví toto upozornění.

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

- **Neshoda #pragma warning(push)** a **#pragma warning(pop)** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistili `#pragma warning(push)` změny stavu je spárovaná s `#pragma warning(pop)` stavu změny v odlišném zdrojovém souboru, která je určena jen zřídka. Toto chování staré vytvořil riziko, který program by být kompilována s jinou sadu upozornění povolená než programátor určena, může být výsledkem chování za běhu tiché chybná. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C5031 na odpovídající pozici `#pragma warning(pop)`, pokud je povoleno. Toto upozornění zahrnuje poznámku odkazující na umístění odpovídající #pragma warning(push).

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

   I když je běžné, kód napsaný v tímto způsobem je někdy úmyslné. Je citlivá na změny v kódu napsaného v tímto způsobem `#include` pořadí; Pokud je to možné, doporučujeme vám, že soubory se zdrojovým kódem spravovat stav s varováním samostatná způsobem.

- **Bezkonkurenční #pragma warning(push)** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru nezjistili bezkonkurenční `#pragma warning(push)` stavu změny na konci jednotky překladu. Kompilátor nyní zjistí a upozorní programátor kódu napsaného v tímto způsobem a problémy volitelné kompilátor varování C5032 v umístění souboru neporovnané `#pragma warning(push)`, pokud je povoleno. Pokud nejsou žádné chyby během kompilace v jednotce překladu se pouze objeví toto upozornění.

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

- **Může se objevit další upozornění v důsledku stav varování #pragma vylepšené sledování**

   Předchozí verze kompilátoru sledovat varování #pragma, změny stavu nedostatečně dobře na problém, že všechny určené upozornění. Toto chování vytvoření rizika určitá upozornění by efektivně potlačit v případech liší od programátor určené. Kompilátor nyní sleduje `#pragma warning` stav více robustní – zejména související s `#pragma warning` stav se změní v rámci šablony – a volitelně vydá nová upozornění C5031 a C5032, které umožní programátora, vyhledejte neúmyslnému použití `#pragma warning(push)` a `#pragma warning(pop)`.

   Kvůli vylepšení `#pragma warning` stav řešení change tracking, dříve nesprávně potlačit upozornění a upozornění související s problémy dříve misdiagnosed mohou nyní být vydány.

- **Vylepšila se identifikace nedosažitelný kód**

   Změny standardní knihovny C++ a vylepšená možnost volání vložených funkcí porovnání s předchozími verzemi kompilátoru může umožnit kompilátoru prokázat, že určitý kód je nyní nedostupná. Toto nové chování může způsobit nové a dalších často vydané instancí upozornění C4720.

    ```Output
    warning C4720: unreachable code
    ```

   V mnoha případech se toto upozornění může se objevit jenom při kompilaci s povolenou optimalizací, od optimalizace může vložené více volání funkcí, vyloučit redundantní kód nebo jinak ji možné určit, že některé kód nedosažitelný. Zjistili jsme, že nové instance upozornění C4720 často došlo v **bloku try/catch** blokuje, zejména ve vztahu k užívání [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

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

###  <a name="VS_Update2"></a> Vylepšení ve verzi Update 2

- **Další upozornění a chyby mohou být vydány v důsledku částečná podpora sfinae u výrazů**

   Předchozí verze kompilátoru analyzovat určité druhy výrazy uvnitř **decltype** specifikátory vzhledem k absenci podpora sfinae u výrazů. Toto chování staré bylo nesprávné a neodpovídají standardu jazyka C++. Kompilátor nyní analyzuje tyto výrazy a má částečná podpora sfinae u výrazů z důvodu probíhající vylepšení. V důsledku toho kompilátor nyní vyvolá upozornění a chyby nalezené ve výrazech, že analyzovat předchozí verze kompilátoru.

   Když toto nové chování analyzuje **decltype** výraz, který obsahuje typ, který nebyl deklarován ještě, kompilátor vyvolá chybu kompilátoru C2039 v důsledku.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Příklad 1: použití neurčený typ (před)

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

   Když toto nové chování analyzuje **decltype** výraz, který chybí nezbytné používání **typename** – klíčové slovo k určení, že je název závislý typ, kompilátor vydává kompilátor varování C4346 spolu s chyba kompilátoru C2923.

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

- `volatile` **Členské proměnné zabránit implicitně definované konstruktory a operátory přiřazení**

   Třída, která má povolené předchozí verze kompilátoru **volatile** členské proměnné mají výchozí konstruktory kopírování nebo přesunutí a operátory přiřazení pro kopírování nebo přesunutí automaticky generuje výchozí. Toto chování staré bylo nesprávné a neodpovídají standardu jazyka C++. Kompilátor nyní brány v úvahu třídu, která má **volatile** členské proměnné nejsou v netriviálních konstrukce a operátory přiřazení, které by zabránily automatickému generování výchozí implementace těchto operátorů. Pokud takové třídy je člen sjednocení (nebo anonymní sjednocení uvnitř třídy), zkopírovat nebo přesunout konstruktory a operátory přiřazení pro kopírování nebo přesunutí sjednocení (nebo třídy obsahující anonymní sjednocení) bude být implicitně definovaný jako odstraněný. Pokus o vytvoření nebo zkopírujte sjednocení (nebo třídu obsahující anonymní sjednocení) bez nutnosti explicitně definovat jejich je chyba a Chyba kompilátoru problémy kompilátoru C2280 ve výsledku.

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

   Předchozí verze sady Visual Studio 2015 povoleny kvalifikátory cv mít statické členské funkce. Toto chování je z důvodu regrese v sadě Visual Studio 2015 a Visual Studio 2015 Update 1; Visual Studio 2013 a předchozí verze kompilátoru odmítnout kódu napsaného v tímto způsobem. Chování sady Visual Studio 2015 a Visual Studio 2015 Update 1 je nesprávný a neodpovídají standardu jazyka C++.  Visual Studio 2015 Update 2 odmítne kódu napsaného v tímto způsobem a místo toho vystavuje Chyba kompilátoru C2511.

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

   Example(After)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **Dopředná deklarace výčtu není povolený v kódu WinRT** (má vliv pouze `/ZW`)

   Kód zkompilován pro prostředí Windows Runtime (WinRT) neumožňuje **výčtu** typy vpřed deklarovat, podobně jako při kompilaci spravovaného kódu C++ pro rozhraní .net Framework pomocí `/clr` přepínač kompilátoru. To zaručuje, že velikost výčet je vždy známé a je možné správně promítnout do systému typů WinRT. Kompilátor odmítne kódu napsaného v tímto způsobem a vyvolá chybu kompilátoru C2599 spolu s chyba kompilátoru C3197.

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

- **Přetížení bez členů operátor new a operátor delete se nedá deklarovat vložené** (úroveň 1 (`/W1`) na výchozím nastavení)

   Předchozí verze kompilátoru bez vyvolání upozornění, když bez operátoru new a operátor delete funkce je deklarovaná jako inline. Kód napsaný v tímto způsobem je chybně vytvořený (vyžadováno žádné diagnostické) a může způsobit paměti problémy způsobené nový Neshoda a operátory (zejména při použití společně s velikostí dealokace), které může být obtížné diagnostikovat, odstranit. Kompilátor nyní vyvolá kompilátor varování C4595 vám pomůže identifikovat kód napsaný v tímto způsobem.

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

   Oprava kódu, která je napsána tímto způsobem může vyžadovat, že definice operátorů přesunout mimo soubor hlaviček a do odpovídající zdrojový soubor.

###  <a name="VS_Update3"></a> Vylepšení shody aktualizací Update 3

- **std::is_convertable nyní rozpozná vlastní přiřazení** (standardní knihovna)

   Předchozí verze `std::is_convertable` vlastnost typu nezjistili správně vlastní přiřazení typu třídy při jeho konstruktor kopie je odstraněna nebo soukromé. Nyní `std::is_convertable<>::value` správně nastavená na **false** při použití na typ třídy s odstraněný nebo soukromý kopírovací konstruktor.

   Neexistuje žádné diagnostiky kompilátoru přidružené k této změně.

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

   V předchozích verzích kompilátoru předat statický kontrolní výrazy v dolní části v tomto příkladu, protože `std::is_convertable<>::value` bylo nesprávně nastaveno jejich **true**. Nyní `std::is_convertable<>::value` správně nastavená na **false**, způsobuje selhání statický kontrolní výrazy.

- **Nastavit na výchozí hodnotu nebo odstranit triviální kopírování a přesun konstruktorů specifikátory přístupu dodržování**

   Předchozí verze kompilátoru není zkontrolujte specifikátor přístupu nastavených výchozích nebo odstraněných triviální kopírování a přesun konstruktorů před povolením, která se má volat. Toto chování staré bylo nesprávné a neodpovídají standardu jazyka C++. V některých případech se vytvoří toto staré chování riziko generování tiché chybného kódu, což vede k modulu runtime nepředvídatelné chování. Kompilátor nyní zkontroluje specifikátor přístupu nastavených výchozích nebo odstraněných triviální kopírování a přesun konstruktorů k určení, zda může být volána a pokud ne, problémy kompilátoru C2248 upozornění ve výsledku.

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

- **Vyřazení podpory kódu ATL s atributy** (úroveň 1 (`/W1`) na výchozím nastavení)

   Předchozí verze kompilátoru nepodporuje kódu ATL s přidělenými atributy. Jako další fází odebrání podpory knihovny ATL s atributy kódu, který [začal v sadě Visual Studio 2008](https://msdn.microsoft.com/library/bb384632), s atributy kódu ATL je zastaralá. Kompilátor nyní vyvolá kompilátor varování C4467 pomáhá rozpoznat tento druh zastaralý kód.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Pokud chcete pokračovat, dokud se odebrala se podpora z kompilátoru použití kódu ATL s atributy, které toto upozornění vypněte předáním `/Wv:18` nebo `/wd:4467` argumenty příkazového řádku pro kompilátor nebo přidáním `#pragma warning(disable:4467)` ve zdrojovém kódu.

   Příklad 1 (před)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Příklad 1 (po)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Někdy potřebujete nebo chcete vytvořit souboru IDL souboru se vyhněte použití zastaralé atributů ATL, stejně jako v níže uvedeného ukázkového kódu

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

   V dalším kroku přidejte krok MIDL vašeho sestavení, abyste měli jistotu, že jsou generovány definice rozhraní C++.

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

   Potom použijte ATL přímo v souboru implementace, stejně jako v následujícím příkladu kódu.

   Příklad 2 implementace (po)

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

- **Předkompilované hlavičky (PCH) soubory a neshoda #include** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru přijato neshoda `#include` direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilace při použití předkompilované hlavičky (PCH) soubory. Kód napsaný v tímto způsobem je už akceptuje kompilátor.   Kompilátor nyní problémy kompilátor varování CC4598 vám pomůže identifikovat neshoda `#include` direktivy při použití souborů PCH.

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

- **Předkompilované hlavičky (PCH) soubory a neshoda adresáře souborů k zahrnutí** (má vliv pouze `/Wall` `/WX`)

   Předchozí verze kompilátoru přijato neshoda zahrnout adresáře (`-I`) argumenty příkazového řádku pro kompilátor mezi `-Yc` a `-Yu` kompilace při použití předkompilované hlavičky (PCH) soubory. Kód napsaný v tímto způsobem je už akceptuje kompilátor. Kompilátor nyní problémy kompilátor varování CC4599 vám pomůže identifikovat neshoda zahrnout adresáře (`-I`) argumenty příkazového řádku při použití souborů PCH.

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

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 nejnovějšími změnami

### <a name="compiler"></a>Kompilátor

- **Konečné** – klíčové slovo nyní vygeneruje chybu nevyřešeného symbolu, kde ji by jinak dříve zkompilován:

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

   V dřívějších verzích nebyl vydán chybu, protože volání bylo **virtuální** volání; nicméně by selhání program za běhu. Nyní je přiřazena chyba linkeru, protože třída je nyní označena jako konečná. V tomto příkladu opravit chybu, třeba se propojit s objektem obsahujícím definici `S2::f`.

- Pokud používáte spřátelené funkce v oborech názvů, je třeba opětovně deklarovat spřátelenou funkci předtím, než na ni můžete odkazovat, nebo se zobrazí chyba, protože kompilátor nyní odpovídá standardu ISO C++. Například v tomto příkladu již ke kompilaci nedojde:

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

   Chcete-li tento kód opravit, deklarujte **friend** funkce:

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

- C++ Standard nepovoluje explicitní specializace ve třídě. I když kompilátor jazyka Microsoft Visual C++ umožňuje v některých případech se v případech, jako v následujícím příkladu je nyní generována chyba, protože kompilátor nezahrne druhou funkci jako specializaci té první.

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

- Kompilátor již nepokouší zdvojit dvě funkce v následujícím příkladu a nyní generuje chybu:

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

- Předtím, než kompilátor byla rozpoznána ISO C ++ 11, by následující kód zkompilován a proměnná `x` přeložit na typ **int**:

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Tento kód nyní vyřeší `x` typu `std::initializer_list<int>` a způsobí chybu na dalším řádku, který se pokusí přiřadit `x` na typ **int**. (Neexistuje žádný převod ve výchozím nastavení.) Chcete-li tento kód opravit, použijte **int** nahradit **automaticky**:

    ```cpp
    int x = {0};
    int y = x;
    ```

- Inicializace agregace již není povolena když typ pravé hodnoty neodpovídá typu levé hodnoty, která je inicializována, a dojde k vyvolání chyby protože ISO C ++ 11 Standard vyžaduje jednotnou inicializaci, aby pracoval bez Zužující převody. Dříve, pokud zužující převod je k dispozici, [upozornění kompilátoru (úroveň 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) upozornění by byl vydán namísto chyby.

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

- Vyhledávání názvu bylo změněno. Následující kód je přeložit odlišně v kompilátoru jazyka C++ v sadě Visual Studio 2012 a Visual Studio 2013:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   V sadě Visual Studio 2012 `E1` ve výrazu `E1::b` přeložit na `::E1` v globálním oboru. V sadě Visual Studio 2013 `E1` ve výrazu `E1::b` překládá `typedef E2` definice v `main()` a má typ `::E2`.

- Rozložení objektů se změnilo. Na platformě x 64 se může v porovnání z předchozími verzemi změnit rozložení objektů třídy. Pokud má **virtuální** funkce, ale neobsahuje základní třídu, která má **virtuální** funkci, objektový model kompilátoru vloží ukazatel na **virtuální** tabulky funkcí. za rozložení datových členů. To znamená, že rozložení nemusí být ve všech případech optimální. V předchozích verzích optimalizaci pro x64 mistranslation: zlepšení rozložení pro vás, ale protože fungovat správně v situacích, komplexního kódu, byla odebrána v sadě Visual Studio 2013. Podívejte se například na tento kód:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- V sadě Visual Studio 2013, výsledek `sizeof(S2)` na x64 je 48, ale v předchozích verzích, je vyhodnocen jako 32. Chcete-li toto vyhodnocení v kompilátoru Visual Studio 2013 C++ pro x64 32, přidejte fiktivní základní třídu, která má **virtuální** funkce:

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

   Chcete-li najít místa v kódu, starší verze by snažila optimalizovat, použijte kompilátor z této verze spolu s `/W3` – možnost kompilátoru a zapněte upozornění 4370. Příklad:

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

   Před Visual Studio 2013, tento kód vracel tuto zprávu: "C4370 upozornění: "S2": má ke změně rozložení třídy z předchozí verze kompilátoru z důvodu lepšího balení ".

   X86 kompilátoru má stejný problém neoptimální rozložení ve všech verzích kompilátoru. Pokud je například tento kód je zkompilován pro platformu x86:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Výsledek `sizeof(S)` je 24. Nicméně jej lze snížit až 16 Pokud použijete zástupné řešení uvedené výše pro x64:

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

Kompilátor C++ v sadě Visual Studio 2013 zjistí neshody v makru _ITERATOR_DEBUG_LEVEL, které bylo implementováno v sadě Visual Studio 2010, a neshody RuntimeLibrary. Tyto problémy dojít při – možnosti kompilátoru `/MT` (statická vydaná verze), `/MTd` (statické ladění), `/MD` (dynamická vydaná verze), a `/MDd` (dynamické ladění) jsou smíšené.

- Pokud váš kód potvrzuje předchozí verze šablony simulované aliasů, musíte ho změnit. Například namísto z `allocator_traits<A>::rebind_alloc<U>::other`, nyní musíte napsat `allocator_traits<A>::rebind_alloc<U>`. I když `ratio_add<R1, R2>::type` již není nezbytné a můžeme nyní doporučit, abyste říkali `ratio_add<R1, R2>`, první bude stále kompilovat, protože `ratio<N, D>` musí mít "typ" typedef pro snížení poměru, který bude stejného typu, pokud je již snížen.

- Je nutné použít `#include <algorithm>` při volání `std::min()` nebo `std::max()`.

- Pokud váš stávající kód používá předchozí verze simulovaný obor výčtů – tradiční výčty zabalené v oborech názvů bez – je třeba je změnit. Například, pokud jste odkazovali na typ `std::future_status::future_status`, nyní musíte napsat `std::future_status`. Většina kódu je však neovlivněna – například `std::future_status::ready` stále zkompiluje.

- `explicit operator bool()` je přísnější než unspecified-bool-type() operátor. `explicit operator bool()` umožňuje explicitní převody na typ bool – například dány `shared_ptr<X> sp`, obě `static_cast<bool>(sp)` a `bool b(sp)` jsou platné – a datový typ Boolean testovatelné "kontextové převody" na bool – například `if (sp)`, `!sp`, `sp &&` jakékoli. Ale `explicit operator bool()` zakazuje implicitní převod na typ bool, takže nelze definovat `bool b = sp;` a daný návratový typ bool, nelze definovat `return sp`.

- Teď, když jsou implementovány skutečné variadické šablony, příkaz _VARIADIC_MAX a související makra nemají žádný vliv. Pokud stále definujete příkaz _VARIADIC_MAX, je ignorována. Je-li potvrzen náš nástroj maker určený k podpoře simulovaných variadic šablon jiným způsobem, je nutné změnit váš kód.

- Kromě běžných klíčových slov záhlaví standardní knihovny C++ nyní zakazuje nahrazení makra kontextových klíčových slov **přepsat** a **konečné**.

- `reference_wrapper`, `ref()`, a `cref()` nyní zakazuje vazby na dočasné objekty.

- \<náhodné > nyní přísně předběžných podmínkách jeho kompilace.

- Různé typové vlastnosti standardní knihovny C++ mají předpoklad "T musí být dokončený typ". Ačkoli je kompilátor nyní vynucuje tato Předběžná podmínka přísněji, nemusí je vynutit ve všech situacích. (Protože porušení předběžných podmínek standardní knihovny C++ spustí nedefinované chování, Standard nezaručuje vynucení.)

- Standardní knihovny C++ nepodporuje `/clr:oldSyntax`.

- Specifikace C ++ 11 pro common_type <> měly neočekávané a nežádoucí důsledky; zejména je common_type\<int, int >:: typ návratové int & &. Proto kompilátor implementuje navrhované řešení problému 2141, pracovní skupiny, díky common_type\<int, int = "" >:: Zadejte návratový int.

   Jako vedlejším účinkem této změny, případ identity již nefunguje (common_type\<T > není vždy mít za následek typu T). Toto chování odpovídá navrženému řešení, ale dojde k porušení jakéhokoli kódu, který spoléhal na předchozí chování.

   Pokud požadujete vlastnost typu identita, nepoužívejte nestandardní `std::identity` , která je definována v \<type_traits >, které nebude fungovat pro \<void >. Místo toho implementujte vlastní typovou vlastnost identity tak, aby vyhovovala vašim potřebám. Tady je příklad:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

- **Visual Studio 2013 pouze**: Knihovna MFC MBCS není zahrnutý v sadě Visual Studio, protože kódování Unicode je Oblíbené a používání znakové sady MBCS je výrazně odmítli. Tato změna také udržuje MFC lépe zarovnané s Windows SDK, protože mnoho ovládacích prvků a zpráv má pouze kódování Unicode. Nicméně, pokud je nutné použít knihovnu MFC znakové sady MBCS, můžete ji stáhnout ze služby Stažení softwaru MSDN na [vícebajtová knihovna MFC pro Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770). Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.  (Poznámka: Knihovny DLL znakové sady MBCS je součástí komponenty instalačního programu C++ v sadě Visual Studio 2015 a novější).

- Přístupnost pásu karet MFC se změní.  Místo architektury existuje je nyní hierarchická architektura. Můžete přesto používat staré chování voláním `CRibbonBar::EnableSingleLevelAccessibilityMode()`.

- `CDatabase::GetConnect` Metoda odebrána. Pro zlepšení zabezpečení je připojovací řetězec nyní uložen zašifrovaně a je dešifrován pouze v případě potřeby; nelze jej vrátit jako prostý text.  Řetězec lze získat pomocí `CDatabase::Dump` metody.

- Podpis `CWnd::OnPowerBroadcast` se změnilo. Podpis tohoto popisovače zprávy se změní na LPARAM jako druhý parametr.

- Podpisy se mění tak, aby vyhovovaly obslužné rutiny zpráv. Seznamy parametrů u následujících funkcí se změnily a používají nově přidané popisovače zpráv ON_WM_ *:

   - `CWnd::OnDisplayChange` změnit na (UINT, int, int) namísto (WPARAM, LPARAM), takže nové makro ON_WM_DISPLAYCHANGE lze použít v mapování zprávy.

   - `CFrameWnd::OnDDEInitiate` změnit na (CWnd *, UINT, jednotky) namísto (WPARAM, LPARAM), takže nové makro ON_WM_DDE_INITIATE lze použít v mapování zprávy.

   - `CFrameWnd::OnDDEExecute` změnit na (CWnd *, POPISOVAČ) namísto (WPARAM, LPARAM), takže nové makro ON_WM_DDE_EXECUTE lze použít v mapování zprávy.

   - `CFrameWnd::OnDDETerminate` změnit na (CWnd *) jako parametr namísto (WPARAM, LPARAM), takže nové makro ON_WM_DDE_TERMINATE lze použít v mapování zprávy.

   - `CMFCMaskedEdit::OnCut` změnil na bez parametrů místo (WPARAM, LPARAM), takže nové makro ON_WM_CUT lze použít v mapování zprávy.

   - `CMFCMaskedEdit::OnClear` změnil na bez parametrů místo (WPARAM, LPARAM), takže nové makro ON_WM_CLEAR lze použít v mapování zprávy.

   - `CMFCMaskedEdit::OnPaste` změnil na bez parametrů místo (WPARAM, LPARAM), takže nové makro ON_WM_PASTE lze použít v mapování zprávy.

- `#ifdef` direktivy v souborech hlaviček knihovny MFC se odeberou. Mnoho `#ifdef` direktivy v souborech hlaviček knihovny MFC související s Nepodporovaná verze systému Windows (WINVER &lt; 0x0501) se odeberou.

- Knihovna ATL DLL (atl120.dll byla) odebrána. Knihovna ATL je nyní poskytována jako záhlaví a statická knihovna (atls.lib).

- Knihovny Atlsd.lib, atlsn.lib a atlsnd.lib byly odebrány. Knihovna Atls.lib již nemá závislosti na znakové sadě ani kód specifický pro ladění/vydání. Protože princip funkce je stejný pro Unicode/ANSI i ladění/vydání, je vyžadována pouze jedna verze knihovny.

- Trasovací nástroj ATL nebo MFC je odebrán společně s knihovnou ATL DLL a mechanismus trasování je zjednodušen. `CTraceCategory` Konstruktoru nyní přijímá jeden parametr (název kategorie) a makra trasování volají funkce vykazování ladění CRT.

## <a name="visual-c-2012-breaking-changes"></a>Visual C++ 2012 nejnovější změny

### <a name="compiler"></a>Kompilátor

- `/Yl` – Možnost kompilátoru změnilo. Ve výchozím nastavení používá kompilátor tuto možnost, což může vést k chybám LNK2011 za určitých podmínek. Další informace najdete v tématu [/Yl (Vložit referenci PCH knihovny ladění)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- V kódu, který je zkompilován s použitím `/clr`, **výčtu** class – klíčové slovo definuje C ++ 11 výčtu není common language runtime (CLR) výčtu. Definování výčtu CLR, musí být explicitní o jeho přístupnost.

- Použijte klíčové slovo šablony explicitně rozlišení názvu závislé (Standard jazyka C++ dodržování předpisů). V následujícím příkladu je klíčové slovo template zvýrazněné povinné se vyřešit nejednoznačnost. Další informace najdete v tématu [rozlišení názvů u závislých typů](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Konstanta typu float již není povolena jako argument šablony, jak je znázorněno v následujícím příkladu.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Kód, který je zkompilován s použitím `/GS` možnost příkazového řádku a který má vypnutí po druhém ohrožení zabezpečení může vést ke zpracování ukončení za běhu, jak je znázorněno v následujícím příkladu pseudokódu.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- Výchozí architektura x86 sestavení se změní na SSE2; Proto kompilátor může vygenerovat instrukcí SSE a registrů XMM bude používat k provádění výpočtů s plovoucí desetinnou čárkou. Pokud budete chtít vrátit k předchozí chování, použijte `/arch:IA32` kompilátoru příznak pro označení architekturu jako IA32.

- Kompilátor může vydat upozornění [upozornění kompilátoru (úroveň 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) a C4701 kde dříve tomu tak není. Kompilátor použije silnější kontroly pro použití neinicializovaná lokální proměnné typu ukazatel.

- Když příznak nové linkeru `/HIGHENTROPYVA` není zadána, Windows 8 obvykle způsobí, že přidělení paměti se vraťte na adresu 64-bit. (Před Windows 8, takové přidělení častěji vrátil adresy, které byly menší než 2 GB.) Tato změna může vystavit chyby zkrácení ukazatele v existujícím kódu. Ve výchozím nastavení je tento přepínač je zapnutý. Chcete-li toto chování zakázat, zadejte `/HIGHENTROPYVA:NO`.

- Spravovaný kompilátor (Visual Basic / C#) podporuje také `/HIGHENTROPYVA` pro spravované sestavení.  V takovém případě však `/HIGHENTROPYVAswitch` je vypnuto ve výchozím nastavení.

### <a name="ide"></a>IDE – integrované vývojové prostředí

- Přestože doporučujeme nevytvářet aplikace Windows Forms v jazyce C + +/ CLI, údržba existující C + +/ podporované aplikace uživatelského rozhraní příkazového řádku. Pokud máte pro vytvoření aplikace modelu Windows Forms nebo jakékoli jiné aplikace uživatelského rozhraní .NET, pomocí C# nebo Visual Basic. Pomocí C + +/ CLI pro interoperabilitu mají jenom.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Knihovna paralelních vzorů a knihovny modulu Runtime souběžnosti

`SchedulerType` Výčet `UmsThreadDefault` je zastaralý. Specifikace `UmsThreadDefault` vytváří nepoužívané upozornění a interně mapuje zpět na `ThreadScheduler`.

### <a name="standard-library"></a>Standardní knihovna

- Následující k zásadní změně C ++ 98/03 až 11 standardů C ++ pomocí explicitní argumenty šablony pro volání `make_pair()` – stejně jako v `make_pair<int, int>(x, y)` – obvykle nebude kompilace v jazyce Visual C++ v sadě Visual Studio 2012. Toto řešení je vždy volat `make_pair() `bez explicitní argumenty šablony, stejně jako v `make_pair(x, y)`. Poskytuje šablony explicitní argumenty popírá účel funkce. Pokud potřebujete mít naprostou kontrolu nad výsledný typ, použijte `pair` místo `make_pair` – stejně jako v `pair<short, short>(int1, int2)`.

- Další změnou rozdělení mezi C ++ 11 standardy a C ++ 98/03: Když je implicitně převést na B a B A je implicitně převést na C, ale není implicitně převést na C a C ++ 98/03 Visual C++ 2010 povolené A `pair<A, X>` má být převeden (implicitně nebo explicitně) do `pair<C, X>`. (Jiný typ, X, není zde zájmu a se neomezuje jen na první typ v páru.) Kompilátor C++ v sadě Visual Studio 2012 zjistí, že není implicitně převést na C A a odebere pár převod z řešení přetížení. Tato změna je pozitivní pro řadu scénářů. Například přetížení `func(const pair<int, int>&)` a `func(const pair<string, string>&)`a volání `func()` s `pair<const char *, const char *>` se zkompiluje podle této změny. Tato změna však konce kódu, který spoléhal na agresivní pár převody. Provedením jedné části převod explicitně obvykle lze napravit takového kódu – například tím, že předáte `make_pair(static_cast<B>(a), x)` funkci, která očekává, že `pair<C, X>`.

- Visual C++ 2010 simulované variadické šablony – například `make_shared<T>(arg1, arg2, argN)`– až po limit 10 argumentů, orazítkování přetížení a specializace preprocesoru zařízení. V sadě Visual Studio 2012 je tento limit snížena na pět argumentů zlepšit dobu potřebnou ke kompilaci a spotřebu paměti kompilátoru pro většinu uživatelů. Předchozí limit však můžete nastavit tak, že explicitně definujete příkaz _VARIADIC_MAX jako 10 celého projektu.

- C ++ 11 17.6.4.3.1 [macro.names]/2 zakazuje nahrazení makra klíčových slov, když hlavičky standardní knihovny C++ jsou zahrnuty. Záhlaví nyní generuje chyby kompilátoru při detekci makra nahrazeny klíčová slova. (Definování _ALLOW_KEYWORD_MACROS umožňuje takový kód mohl zkompilovat, ale důrazně budeme bránit tohle využívání.) Jako výjimku – makro formu `new` je povolené ve výchozím nastavení, protože záhlaví komplexně chránit s použitím `#pragma push_macro("new")` / `#undef new` / `#pragma pop_macro("new")`. Definování _ENFORCE_BAN_OF_MACRO_NEW nemá přesně jak název napovídá.

- Pokud chcete implementovat různých optimalizací a kontroly ladění, implementace standardní knihovny C++ záměrně neumožňuje binární kompatibilitu mezi verzemi sady Visual Studio (2005, 2008, 2010, 2012). Při použití standardní knihovny C++ zakazuje kombinování souborů objektů a statických knihoven, které jsou kompilovány pomocí různých verzí na jednom binárním souboru (EXE nebo DLL) a zakazuje předávání objektů standardní knihovny C++ mezi binárními soubory, které jsou kompilovány pomocí pomocí různých verzí. Kombinování souborů objektů a statických knihoven (pomocí standardní knihovny C++, které byly zkompilovány pomocí Visual C++ 2010 těmi, které byly zkompilovány pomocí C++ v sadě Visual Studio 2012 kompilátor chyby linkeru týkající se neshoda _MSC_VER, kde je _MSC_VER makra, které obsahuje hlavní verzi kompilátoru (1700 jazyka Visual C++ v sadě Visual Studio 2012). Tato kontrola nezjistí směšování knihoven DLL a nelze zjišťovat kombinace, která zahrnuje Visual C++ 2008 nebo dřívější.

- Kromě zjišťování neshody _ITERATOR_DEBUG_LEVEL, které bylo implementováno ve Visual C++ 2010, kompilátor jazyka C++ v sadě Visual Studio 2012 zjistí neshody knihovny prostředí Runtime. Tyto problémy dojít při možnosti kompilátoru `/MT` (statická vydaná verze), `/MTd` (statické ladění), `/MD` (dynamická vydaná verze), a `/MDd` (dynamické ladění) jsou smíšené.

- `operator<()`, `operator>()`, `operator<=()`, a `operator>=()` byly dříve k dispozici pro `std::unordered_map` a `stdext::hash_map` rodiny kontejnerů, i když jejich implementace nebylo užitečné. Tyto operátory nestandardní jsme odebrali v jazyce Visual C++ v sadě Visual Studio 2012. Kromě toho provádění `operator==()` a `operator!=()` pro `std::unordered_map` řady rozšířilo a zahrnují `stdext::hash_map` řady. (Doporučujeme, abyste se vyhněte použití `stdext::hash_map` řady v novém kódu.)

- C ++ 11 22.4.1.4 [locale.codecvt] Určuje, že `codecvt::length()` a `codecvt::do_length()` zabere upravitelná `stateT&` parametry, ale jazyk Visual C++ 2010 trvalo `const stateT&`. Kompilátor C++ v sadě Visual Studio 2012 trvá `stateT&` podle zákonného standard. Tento rozdíl je důležité pro každého, kdo se pokouší přepsat virtuální funkci `do_length()`.

### <a name="crt"></a>CRT

- Haldy C Runtime (CRT), který se používá pro nové a malloc(), již není privátní. CRT teď používá haldu procesu. To znamená, že haldy není zničen, pokud knihovna DLL je uvolněna, takže knihovny DLL, které staticky propojit CRT musíte zajistit, paměti, která je přidělena kód knihovny DLL je vyčištěn předtím, než se uvolnil.

- `iscsymf()` Funkce nepodmíněné výrazy s záporné hodnoty.

- `threadlocaleinfostruct` Došlo ke změně struktury tak, aby vyhovovaly změny funkce národního prostředí.

- Funkce CRT, které mají odpovídající vnitřní objekty, jako `memxxx()`, `strxxx()` jsou odebrány z intrin.h. Pokud jste zahrnuli intrin.h pouze pro tyto funkce, je nutné zahrnout nyní odpovídající záhlaví CRT.

### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL

- Odebrání podpory Fusion (afxcomctl32.h); proto všechny metody, které jsou definovány v \<afxcomctl32.h > byly odebrány. Soubory hlaviček \<afxcomctl32.h > a \<afxcomctl32.inl > se odstranily.

- Změnit název `CDockablePane::RemoveFromDefaultPaneDividier` k `CDockablePane::RemoveFromDefaultPaneDivider`.

- Změnit podpis `CFileDialog::SetDefExt` používat LPCTSTR; proto se to týká Unicode sestavení.

- Odebraný zastaralá ATL kategorií trasování.

- Změnit podpis `CBasePane::MoveWindow` provést `const CRect`.

- Změnit podpis `CMFCEditBrowseCtrl::EnableBrowseButton`.

- Odebrat `m_fntTabs` a `m_fntTabsBold` z `CMFCBaseTabCtrl`.

- Přidání parametru k `CMFCRibbonStatusBarPane` konstruktory. (Je to výchozí parametr, a proto není prolamující zdrojový.)

- Přidání parametru k `CMFCRibbonCommandsListBox` konstruktoru. (Je to výchozí parametr, a proto není prolamující zdrojový.)

- Odebrat `AFXTrackMouse` rozhraní API (a související časovače proc). Použití rozhraní Win32 `TrackMouseEvent` API místo.

- Přidání parametru k `CFolderPickerDialog` konstruktoru. (Je to výchozí parametr, a proto není prolamující zdrojový.)

- `CFileStatus` změnit velikost struktury: `m_attribute` Člena se změnil z BAJTŮ DWORD (tak, aby odpovídala hodnotě, která je vrácena z `GetFileAttributes`).

- `CRichEditCtrl` a `CRichEditView` v kódování Unicode sestavení použít MSFTEDIT_CLASS (ovládací prvek RichEdit 4.1) namísto RICHEDIT_CLASS (ovládací prvek RichEdit 3.0).

- Odebrat `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` vzhledem k tomu, že je vždy TRUE na Windows Vista, Windows 7 a Windows 8.

- Odebrat `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` vzhledem k tomu, že je vždy TRUE na Windows Vista, Windows 7 a Windows 8.

- Odebrat `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`. Volání Windows API přímo v systému Windows Vista, Windows 7 a Windows 8.

- Odebrat `AFX_GLOBAL_DATA::DwmDefWindowProc`. Volání Windows API přímo v systému Windows Vista, Windows 7 a Windows 8.

- Přejmenovat `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` k `IsDwmCompositionEnabled` vyloučit kolize názvů.

- Změnit identifikátory pro celou řadou časovače interní knihovny MFC a přesunout definice afxres.h (AFX_TIMER_ID_ *).

- Změnit podpis `OnExitSizeMove` metoda souhlas s ON_WM_EXITSIZEMOVE makra:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Změnit název a podpis `OnDWMCompositionChanged` souhlas s ON_WM_DWMCOMPOSITIONCHANGED makra:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Změnit podpis `OnMouseLeave` metoda souhlas s ON_WM_MOUSELEAVE makra:

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

- Změnit podpis `OnPowerBroadcast` souhlas s ON_WM_POWERBROADCAST makra:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

- Změnit podpis `OnStyleChanged` souhlas s ON_WM_STYLECHANGED makra:

   - `CMFCListCtrl`

   - `CMFCStatusBar`

- Přejmenovat metodu interní `FontFamalyProcFonts` k `FontFamilyProcFonts`.

- Odebrat mnoho globální statické `CString` objekty paměti eliminuje nevracení v některých situacích (nahradí #defines), a členské proměnné třídy následující:

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

- Změnit podpis `CKeyboardManager::ShowAllAccelerators` a odebrat parametr oddělovač akcelerátoru.

- Přidat `CPropertyPage::GetParentSheet`a `CPropertyPage` třídy, zavolejte místo něj `GetParent` správné nadřazené okno list, který může být nadřazený nebo okno dvě úrovně nadřazený `CPropertyPage`. Budete muset změnit váš kód volat `GetParentSheet` místo `GetParent`.

- Opraveno v ATLBASE nevyváženou #pragma warning(push). H, která způsobila upozornění nesprávně zakázán. Upozornění jsou teď povolené správně po ATLBASE. Má být H.

- Metody související D2D z afx_global_data – přesunout do _AFX_D2D_STATE:

   - `GetDirectD2dFactory`

   - `GetWriteFactory`

   - `GetWICFactory`

   - `InitD2D`

   - `ReleaseD2DRefs`

   - `IsD2DInitialized`

   - `D2D1MakeRotateMatrix`

   - Namísto volání, například `afxGlobalData.IsD2DInitialized`, volání `AfxGetD2DState->IsD2DInitialized`.

- Odebrat zastaralé ATL *. CPP soubory ze složky \atlmfc\include\.

- Přesunout `afxGlobalData` inicializaci, aby na vyžádání místo v době inicializace CRT, tím se uspokojí `DLLMain` požadavky.

- Přidá `RemoveButtonByIndex` metodu `CMFCOutlookBarPane` třídy.

- Opravit `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` k `IsFrequentlyUsedCmd`.

- Opravit několik instancí `RestoreOriginalstate` k `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`.

- Odebrat nepoužité metody z `CDockablePane`: `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, `GetRecentSiblingPaneInfo`, a `CanAdjustLayout`.

- Odebrat `CDockablePane` statické členské proměnné `m_bCaptionText` a `m_bHideDisabledButtons`.

- Přidání přepsání `DeleteString` metodu `CMFCFontComboBox`.

- Odebrat nepoužité metody z `CPane`: `GetMinLength` a `IsLastPaneOnLastRow`.

- Přejmenovat `CPane::GetDockSiteRow(CDockingPanesRow *)` k `CPane::SetDockSiteRow`.

## <a name="visual-c-2010-breaking-changes"></a>Visual C++ 2010 nejnovější změny

### <a name="compiler"></a>Kompilátor

- **Automaticky** – klíčové slovo má nové výchozí význam. Využívání staré význam je vzácné, nebude tato změna ovlivněno většinu aplikací.

- Nové **static_assert** – klíčové slovo se používá, což způsobí konflikt názvů, pokud je identifikátor s tímto názvem v kódu.

- Podpora pro nový zápis lambda nezahrnuje podporu pro kódování bez uvozovek GUID v atributu uuid IDL.

- Rozhraní .NET Framework 4 zavádí koncepci výjimky v poškozeném stavu, které jsou výjimkami opustí proces v neopravitelné poškozeném stavu. Ve výchozím nastavení nemůže zachytit poškozený stav výjimky, i s možností kompilátoru/EHa, který zachycuje všechny ostatní výjimky.                 Chcete-li explicitně zachycení výjimky poškozeném stavu, použijte definovaný blok __try –\__except příkazy. Nebo použijte atribut [HandledProcessCorruptedStateExceptions] povolit funkce pro zachycení výjimky v poškozeném stavu.  Tato změna ovlivní primárně systému programátory, kteří mohou mít pro zachycení výjimek v poškozeném stavu. Osm výjimky jsou STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, status_ – UNWIND_CONSOLIDATE.                 Další informace o těchto výjimkách naleznete v tématu [GetExceptionCode](/windows/desktop/Debug/getexceptioncode) – makro.

- Revidovaná `/GS` – možnost kompilátoru chrání proti přetečení vyrovnávací paměti komplexněji než v dřívějších verzích. Tato verze může vložit dalších kontrol zabezpečení do zásobníku, to může snížit výkon. Pomocí nové `__declspec(safebuffers)` – klíčové slovo, abyste instruovali kompilátor k zabezpečení není vložen vyhledává konkrétní funkce.

- Pokud kompilujete s oběma `/GL` (optimalizace celého programu) a `/clr` možnosti kompilátoru (kompilace Common Language Runtime), `/GL` možnost je ignorována. Tato změna byla provedena, protože zadaná kombinace parametrů kompilátoru málo výhodné. V důsledku této změny je výkon sestavení.

- Ve výchozím nastavení podpora trigraphs je vypnutá ve Visual C++ 2010. Použití `/Zc:trigraphs` povolení podpory trigraphs – možnost kompilátoru. Trigraf se skládá ze dvou po sobě jdoucími otazníky ("??") následovaný znakem třetí jedinečný. Kompilátor nahradí trigraph odpovídající znak interpunkce. Například, kompilátor nahradí `??=` trigraph znakem '#'. Použití trigraphs ve zdrojových souborech jazyka C, které používají znakovou sadu, která neobsahuje vhodné grafické reprezentace pro některá interpunkční znaménka.

- Propojovací program již podporuje optimalizaci pro Windows 98. `/OPT` Možnosti (optimalizace) vytvoří chybu v době kompilace při zadání `/OPT:WIN98` nebo `/OPT:NOWIN98`.

- Výchozí možnosti kompilátoru, která jsou určena podle RuntimeLibrary a DebugInformationFormat sestavovací systém, které se změnily vlastnosti. Ve výchozím nastavení tato sestavení, které jsou zadány vlastnosti v projektech, které jsou vytvořeny pomocí jazyka Visual C++ verze 7.0 prostřednictvím 10.0. Pokud provádíte migraci projekt, který byl vytvořen ve Visual C++ 6.0, zvažte, jestli můžete zadat hodnotu pro tyto vlastnosti.

- V sadě Visual C++ 2010 RuntimeLibrary = s více vlákny (`/MD`) a DebugInformationFormat = ProgramDatabase (`/Zi`). V jazyce Visual C++ 9.0, RuntimeLibrary = s více vlákny (`/MT`) a DebugInformationFormat = zakázáno.

### <a name="clr"></a>CLR

- Kompilátory Microsoft C# a Visual Basic můžete nyní vytvořit primární definiční sestavení (no-PIA). No-PIA sestavení můžete typy modelu COM bez nasazování relevantní primární sestavení vzájemné spolupráce (PIA). Při využívání no-PIA sestavení vytvořené Visual C# nebo Visual Basic, je třeba sestavení PIA, na příkaz compile odkazovat dříve, než odkazovat no-PIA sestavení, který používá knihovnu.

### <a name="visual-c-projects-and-msbuild"></a>Projekty Visual C++ a nástroje MSBuild

- Projekty Visual C++ jsou nyní podle nástroj MSBuild. V důsledku toho soubory projektu používají nový formát souboru XML a příponu souboru .vcxproj. Visual C++ 2010 automaticky převede soubory projektu z předchozích verzí sady Visual Studio na nový formát souboru. Existující projekt bude ovlivněna závisí na předchozím .vcproj nástroje, VCBUILD.exe nebo příponu souboru projektu sestavení.

- V dřívějších verzích Visual C++ nepodporuje opožděné vyhodnocení vlastností. Například nadřazený seznam vlastností může importovat seznam vlastností podřízené a nadřazené může používat proměnné definované v podřízeném definovat jiné proměnné. Opožděné vyhodnocení povolit nadřazené použít vlastnost podřízené ještě předtím, než bylo importováno podřízený seznam vlastností. V aplikaci Visual C++ 2010 nelze použít seznam proměnných projektu předtím, než je definován, protože MSBuild podporuje pouze dřívější vyhodnocení.

### <a name="ide"></a>IDE – integrované vývojové prostředí

- Dialogové okno ukončení aplikace už ukončí aplikaci. V předchozích verzích když `abort()` nebo `terminate()` funkce zavřené sestavení prodejní verze aplikace, knihovny Run-Time jazyka C v okně konzoly se okně nebo dialogovém okně zobrazí zprávu o ukončení aplikace. Zpráva říká, že v části "Tato aplikace vydala požadavek modulu Runtime, aby ji ukončil neobvyklým způsobem. Kontaktujte prosím tým podpory vaší aplikace pro další informace." Zpráva ukončení aplikace byla redundantní, protože Windows následně zobrazit aktuální rutinu ukončení, které se obvykle Windows hlášení chyb (zotavení po havárii. Dialogové okno programu Watson) nebo ladicího programu sady Visual Studio. Spouští se v sadě Visual Studio 2010, knihovny Run-Time jazyka C nezobrazuje zpráva. Kromě toho modul runtime zabrání aplikaci v končí před spuštěním ladicí program. Toto je zásadní změna pouze v případě, že závisí na předchozím chování zpráva ukončení aplikace.

- Konkrétně pro sadu Visual Studio 2010, nefunguje technologie IntelliSense pro C + +/ CLI kód nebo atributy, **najít všechny odkazy** nefunguje pro místní proměnné, a modelu kódu nelze načíst názvy typů z importované sestavení nebo řešení typy k jejich plně kvalifikovaných názvů.

### <a name="libraries"></a>Knihovny

- SafeInt – třída je zahrnuta v jazyce Visual C++ a již není v samostatný soubor ke stažení. Toto je zásadní změna pouze v případě, že jste vytvořili třídu, která je také s názvem "SafeInt".

- Manifesty model nasazení knihoven už používá k nalezení konkrétní verzi knihovny DLL. Místo toho název každou knihovnu DLL obsahuje číslo verze a používat tento název k vyhledání knihovny.

- V předchozích verzích sady Visual Studio může sestavení knihovny run-time. Visual C++ 2010 již podporuje vytváření vlastní kopie C spusťte soubory knihovny.

### <a name="standard-library"></a>Standardní knihovna

- \<Iterátor > hlavičky je už součástí automaticky mnoho dalších souborů záhlaví. Místo toho vložte tuto hlavičku explicitně, pokud budete potřebovat podporu pro samostatné iterátory definovaná v hlavičce. Existující projekt má vliv, pokud závisí na předchozím nástroj pro sestavení, VCBUILD.exe nebo příponu souboru projektu. vcproj.iterator.

- V \<algoritmus > hlavičky, checked_ * a unchecked_\* funkce jsou odebrány. A \<iterátoru >> záhlaví, `checked_iterator` třída je odebrána a `unchecked_array_iterator` třída byla přidána.

- `CComPtr::CComPtr(int)` Konstruktor je odebrán. Tento konstruktor povolený `CComPtr` objektu z makro NULL, ale bylo zbytečné a povolené nesmyslná konstrukce z nenulového celého čísla.

   A `CComPtr` lze stále zkonstruovat z NULL, což je definováno jako 0, ale selže, pokud je vytvořen z celé číslo než literálu 0. Použití **nullptr** místo.

- Následující `ctype` členské funkce byly odebrány: `ctype::_Do_narrow_s`, `ctype::_Do_widen_s`, `ctype::_narrow_s`, `ctype::_widen_s`. Pokud aplikace používá jednu z těchto členské funkce, je potřeba nahradit ji odpovídající nezabezpečené verze: `ctype::do_narrow`, `ctype::do_widen`, `ctype::narrow`, `ctype::widen`.

### <a name="crt-mfc-and-atl-libraries"></a>CRT knihovny MFC a knihovny ATL

- Pro uživatele k sestavení knihovny CRT knihovny MFC a ATL byla odebrána podpora. Například je k dispozici žádný odpovídající soubor NMAKE. Však mít uživatelé dál přístup ke zdrojovému kódu pro tyto knihovny. A dokument, který popisuje MSBuild možnosti, které společnost Microsoft používá k vytváření těchto knihoven pravděpodobně se zveřejní v blogu týmu Visual C++.

- Odebrala se podpora MFC pro IA64. Podporu CRT a knihovny ATL na IA64, je však stále poskytuje.

- Řadové číslovky se už znovu použít soubory definice modulu (.def) knihovny MFC. Tato změna znamená, že řadové číslovky nebudou lišit mezi podverze a se vylepší binární kompatibilitu pro aktualizace service Pack a rychlé opravy.

- Byla přidána nová virtuální funkce `CDocTemplate` třídy. Tato nová virtuální funkce je [CDocTemplate – třída](../mfc/reference/cdoctemplate-class.md). Předchozí verze `OpenDocumentFile` má dva parametry. Nová verze má tři parametry. Pro podporu správce restartování, libovolná třída odvozená z `CDocTemplate` musí implementovat verzi, která má tři parametry. Nový parametr je `bAddToMRU`.

### <a name="macros-and-environment-variables"></a>Makra a proměnných prostředí

- __MSVCRT_HEAP_SELECT proměnné prostředí se už nepodporuje. Tato proměnná prostředí se odebere a nebude ničím nahrazen.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční dokumentace

- Několik direktivy byly odebrány z kompilátoru Microsoft Macro Assembler – referenční dokumentace. Odebrání direktivy jsou `.186`, `.286`, `.286P`, `.287`, `.8086`, `.8087`, a `.NO87`.

## <a name="visual-c-2008-breaking-changes"></a>Visual C++ 2008 nejnovější změny

### <a name="compiler"></a>Kompilátor

- Windows 95, Windows 98, Windows ME a Windows NT platforem již nejsou podporovány. Tyto operační systémy byly odebrány ze seznamu cílových platforem.

- Kompilátor už nepodporuje více atributů, které byly přímo spojené s ATL Server. Již nejsou podporovány následující atributy:

   - perf_counter

   - perf_object

   - perfmon

   - request_handler

   - soap_handler

   - soap_header

   - soap_method

   - tag_name

### <a name="visual-c-projects"></a>Projekty Visual C++

- Upgrade projektů z předchozích verzí sady Visual Studio, je nutné upravit maker WINVER a _WIN32_WINNT tak, aby byly větší než nebo rovna hodnotě 0x0500.

- Od verze Visual Studio 2008, Průvodce vytvořením projektu nemá možnost pro vytvoření projektu C++ SQL Server. Projekty systému SQL Server vytvořili pomocí starší verze sady Visual Studio bude stále zkompilujte a správně fungovat.

- Soubor hlaviček rozhraní Windows API Winable.h byl odebrán. Včetně winuser.h místa.

- Knihovně rozhraní Windows API Rpcndr.lib se odebrala. Místo toho odkaz s rpcrt4.lib.

### <a name="crt"></a>CRT

- Odebrala se podpora pro Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4.0.

- Odebrali jsme tyto globální proměnné:

   - _osplatform

   - _osver

   - _winmajor

   - _winminor

   - _winver

- Následující funkce byly odebrány. Použití funkce rozhraní Windows API `GetVersion` nebo `GetVersionEx` místo:

   - _get_osplatform

   - _get_osver

   - _get_winmajor

   - _get_winminor

   - _get_winver

- Syntaxe poznámky SAL změnila. Další informace najdete v tématu [poznámky SAL](../c-runtime-library/sal-annotations.md).

- Filtr IEEE teď podporuje sadu instrukcí SSE 4.1. Další informace najdete v tématu [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Běhové knihovny jazyka C, které se dodávají pomocí sady Visual Studio, už nejsou závislé na msvcrt.dll systémové knihovny DLL.

### <a name="standard-library"></a>Standardní knihovna

- Odebrala se podpora pro Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4.0.

- Při kompilaci s _HAS_ITERATOR_DEBUGGING definované v režimu ladění (nahrazena [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po sadu Visual Studio 2010), aplikace bude nyní assert, když iterátor pokusí přičtena nebo odečtena za hranice základní kontejneru.

- Členské proměnné c zásobníku třídy je teď deklarována jako chráněná. Tato členská proměnná dříve, se deklaroval veřejné.

- Chování `money_get::do_get` došlo ke změně. Dříve, při analýze peněžní hodnotu s více číslic zlomku než jsou volány pro `frac_digits`, `do_get` používaných pro všechny. Nyní `do_get` zastaví parsování po spotřebování maximálně `frac_digits` znaků.

### <a name="atl"></a>ATL

- Knihovny ATL nelze sestavit bez závislosti na CRT. V dřívějších verzích sady Visual Studio, můžete použít #define ATL_MIN_CRT projektu ATL, aby minimálně závislé na CRT. V aplikaci Visual C++ 2008 jsou všechny projekty knihovny ATL minimálně závislé na CRT bez ohledu na to, zda je definován ATL_MIN_CRT.

- Základ kódu serveru ATL byla uvedena jako sdílený zdrojový projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio. Kódování a dekódování z funkce atlenc.h a nástroje a třídy z atlutil.h a atlpath.h dat byla držena a jsou teď součástí knihovny ATL. Několik souborů, které jsou přidružené k serveru knihovny ATL už nejsou součástí sady Visual Studio.

- Některé funkce jsou již zahrnuty v knihovně DLL. Jsou stále umístěny v knihovně importu. To nebude mít vliv na kód, který používá funkce staticky. Bude mít vliv pouze kód, který používá tyto funkce dynamicky.

- Makra PROP_ENTRY a PROP_ENTRY_EX byly zastaralé a nahradí makra PROP_ENTRY_TYPE a PROP_ENTRY_TYPE_EX z bezpečnostních důvodů.

### <a name="atlmfc-shared-classes"></a>Sdílené třídy ATL/MFC

- Knihovny ATL nelze sestavit bez závislosti na CRT. V dřívějších verzích sady Visual Studio, můžete použít `#define ATL_MIN_CRT` do projektu ATL, aby minimálně závislé na CRT. V aplikaci Visual C++ 2008 jsou všechny projekty knihovny ATL minimálně závislé na CRT bez ohledu na to, zda je definován ATL_MIN_CRT.

- Základ kódu serveru ATL byla uvedena jako sdílený zdrojový projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio. Kódování a dekódování z funkce atlenc.h a nástroje a třídy z atlutil.h a atlpath.h dat byla držena a jsou teď součástí knihovny ATL. Několik souborů, které jsou přidružené k serveru knihovny ATL už nejsou součástí sady Visual Studio.

- Některé funkce jsou již zahrnuty v knihovně DLL. Jsou stále umístěny v knihovně importu. To nebude mít vliv na kód, který používá funkce staticky. Bude mít vliv pouze kód, který používá tyto funkce dynamicky.

### <a name="mfc"></a>MFC

- `CTime` Třída: `CTime` Třídy nyní přijímá data od 1/1/1900 n. l. namísto 1/1/1970 n. l.

- Pořadí karet ovládacích prvků v dialogových oknech MFC: Správné pořadí prvků více ovládacích prvků v dialogovém okně knihovny MFC je narušen, pokud ovládací prvek ActiveX knihovny MFC je vložen do pořadí ovládacích prvků. Tato změna opravuje tohoto problému.

   Například vytvoření aplikace knihovny MFC dialogového okna, který má ovládací prvek ActiveX a několik ovládacích prvcích pro úpravy. Pozice ovládacího prvku ActiveX uprostřed pořadí ovládacích prvků pro úpravy. Spusťte aplikaci, klikněte na tlačítko ovládacího prvku pro úpravy, jejichž pořadí je po ovládacího prvku ActiveX a karty. Před touto změnou se nepovedlo fokus do ovládacího prvku edit následující ovládací prvek ActiveX namísto na další ovládací prvek úprav v pořadí.

- `CFileDialog` Třída: Vlastní šablony `CFileDialog` třídy nejde přenést automaticky na Windows Vista. Jsou i nadále použitelná, ale nebudou mít další funkce nebo vypadá dialogů styl, Windows Vista.

- `CWnd` Třídy a `CFrameWnd` třídy: `CWnd::GetMenuBarInfo` Metoda byla odebrána.

   `CFrameWnd::GetMenuBarInfo` Metoda je nyní nevirtuální metoda. Další informace najdete v tématu **GetMenuBarInfo funkce** v sadě Windows SDK.

- Podpora knihovny MFC rozhraní ISAPI: Knihovna MFC už podporuje vytváření aplikací s serveru aplikaci rozhraní ISAPI (Internet Programming). Pokud chcete k sestavení aplikace ISAPI, rozšíření ISAPI přímo volejte.

- Rozhraní API nepoužívané standardu ANSI: ANSI verze z několika metod MFC jsou zastaralé. Použijte Unicode verze těchto metod v budoucí aplikace. Další informace najdete v tématu **vytvářet požadavky pro Windows Vista běžné ovládací prvky**.

## <a name="visual-c-2005-breaking-changes"></a>Visual C++ 2005 nejnovější změny

### <a name="crt"></a>CRT

- Mnoho funkcí jsou zastaralé. Zobrazit **zastaralé CRT funkce**.

- Mnoho funkcí se teď ověřují své parametry, zastavení provádění, pokud je zadané neplatné parametry. Toto ověření způsobit nefunkčnost kód, který předává neplatné parametry a spoléhá na funkce ignorováním nebo jenom vrací kód chyby. Zobrazit **Parameter Validation**.

- Hodnota popisovače souboru -2 se teď používá k označení, že `stdout` a `stderr` nejsou k dispozici pro výstup, například v aplikaci Windows, který nemá žádné okno konzoly. Předchozí hodnota byla hodnota -1. Další informace najdete v tématu [_fileno](../c-runtime-library/reference/fileno.md).

- Knihovny CRT jednovláknový (libc.lib a libcd.lib) byly odebrány. Vícevláknové knihovny CRT použijte. `/ML` Příznaku kompilátoru se už nepodporuje. Bez uzamčení verze některé funkce byly přidány v případech, kdy je potenciálně významného rozdíly ve výkonnosti mezi vícevláknovém kódu a kódu s jedním vláknem.

- Přetížení pow, double pow (int, int), byla odebrána tak, aby lépe vyhovovala standard.

- Specifikátor formátu %n je již nejsou podporovány ve výchozím nastavení v některém z printf řadu funkcí, protože je ze své podstaty nezabezpečené. Pokud %n nalezen, je výchozí chování vyvolají obslužnou rutinu neplatného parametru. Chcete-li povolit podporu %n, použijte `_set_printf_count_output` (viz také `_get_printf_count_output`).

- `sprintf` Nyní vytiskne záporné znaménko podepsaný nula.

- `swprintf` se změnil v souladu se standardem; nyní vyžaduje parametr velikosti. Forma `swprintf` bez velikost parametru je zastaralá.

- `_set_security_error_handler` byl odebrán. Odeberte všechna volání dané funkce; výchozí obslužnou rutinu je mnohem bezpečnější způsob řešení problémů s chybami zabezpečení.

- `time_t` (Pokud je definována hodnota _USE_32BIT_TIME_T) je teď 64bitovou hodnotu.

- `_spawn`, `_wspawn` Funkce ponechejte tuto položku nyní `errno` zůstanou v případě úspěchu, jak je uvedeno ve standardu C.

- Ve výchozím nastavení používá RTC nyní širokých znaků.

- Funkce podpory slovo s plovoucí desetinnou čárkou ovládacího prvku jsou zastaralé pro kompilaci aplikací s `/CLR` nebo `/CLR:PURE`. Ovlivněná funkce jsou `_clear87`, `_clearfp`, `_control87`, `_controlfp`, `_fpreset`, `_status87`, `_statusfp`. Upozornění na vyřazení můžete zakázat tak, že definujete _CRT_MANAGED_FP_NO_DEPRECATE použití těchto funkcí ve spravovaném kódu je však nepředvídatelný a nepodporovaný.

- Některé funkce se teď vrátit ukazatele const. Nekonstantní, staré chování lze obnovit tak, že definujete _CONST_RETURN. Ovlivněná funkce

   - memchr, wmemchr

   - strchr, wcschr, _mbschr, _mbschr_l

   - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

   - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

   - strstr, wcsstr, _mbsstr, _mbsstr_l

- Při propojování s Setargv.obj nebo Wsetargv.obj, se už nedají potlačit rozšíření zástupných znaků na příkazovém řádku uzavřením do dvojitých uvozovek. Další informace najdete v tématu [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Standardní knihovny (2005)

- Třídy výjimek (umístěný ve \<výjimky > záhlaví) byl přesunut do `std` oboru názvů. V předchozích verzích tuto třídu automaticky vygenerovala v globálním oboru názvů. Chcete-li vyřešit jakékoli chyby naznačující, že nebyla nalezena třída výjimky, přidejte následující příkaz kódu: `using namespace std;`

- Při volání metody `valarray::resize()`, obsah `valarray` budou ztraceny a budou nahrazeny výchozí hodnoty. `resize()` Metoda je určena k inicializaci `valarray` místo dynamicky zvětšovat jako vektor.

- Ladění iterátorů: Aplikace vytvořené s ladicí verzí knihovny C Runtime a které používání iterátorů nesprávně můžou začít vyskytovat, chcete-li zobrazit vyhodnotí za běhu. Chcete-li zakázat tyto nepodmíněné výrazy, je nutné definovat _HAS_ITERATOR_DEBUGGING (nahrazena [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po sadu Visual Studio 2010) na hodnotu 0. Další informace najdete v tématu [Debug Iterator Support](../standard-library/debug-iterator-support.md)

## <a name="visual-c-net-2003-breaking-changes"></a>Rozbíjející změny v jazyce Visual C++ .NET 2003

### <a name="compiler"></a>Kompilátor

- Pravou závorkou nyní vyžadované pro definovaná direktiva preprocesoru (C2004).

- Explicitní specializace již nelze najít parametry šablony z primární šablony ([Chyba kompilátoru C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Chráněný člen (n) je přístupný pouze prostřednictvím funkce člena třídy (B), která dědí z třídy (A) je (n) je jejím členem ([Chyba kompilátoru C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Vylepšení usnadnění kontroly v kompilátoru nově detekuje nepřístupné základní třídy ([Chyba kompilátoru C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- Nejde zachytit výjimku, pokud destruktor nebo kopie konstruktoru je nedostupný (C2316).

- Výchozí argumenty ukazatele na funkce již není povolena ([Chyba kompilátoru C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Statický datový člen nejde inicializovat prostřednictvím odvozené třídy ([Chyba kompilátoru C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- Inicializace **typedef** není povolen Standard a nyní generuje chybu při kompilaci ([Chyba kompilátoru C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- **BOOL** je nyní správný typ ([Chyba kompilátoru C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- UDC můžete nyní vznikla nejednoznačnost s přetížené operátory ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Další výrazy jsou teď považuje za platný ukazatel s hodnotou null konstanty ([Chyba kompilátoru C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- na místech, kde kompilátor by dříve znamenalo, to je nyní vyžadován <> šablony ([Chyba kompilátoru C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- Explicitní specializace členské funkce mimo třídu není platný, pokud funkci již byla explicitně specializovaná prostřednictvím specializace šablony třídy ([Chyba kompilátoru C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Parametry šablony bez typu s plovoucí desetinnou čárkou bod již nejsou povoleny ([Chyba kompilátoru C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- Šablony třídy nejsou povoleny jako argumenty typu šablony (C3206).

- Názvy funkcí Friend jsou už zavedené do obsahující obor názvů ([Chyba kompilátoru C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Kompilátor nebude přijímat další čárkami v makru (C4002).

- Objekt typu POD zkonstruován pomocí inicializátoru (formuláře) bude inicializována ve výchozím nastavení (C4345).

- vlastnost TypeName je nyní požadováno, pokud název závislý považován za typ ([upozornění kompilátoru (úroveň 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Funkce, které se nesprávně považuje za specializace šablony jsou již považovány za Ano (C4347).

- Statické datové členy nelze inicializovat prostřednictvím odvozené třídy (C4356).

- Specializace šablony třídy musí být definován, než se použijí v návratovém typu ([upozornění kompilátoru (úroveň 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Kompilátor nyní hlásí nedosažitelný kód (C4702).

## <a name="see-also"></a>Viz také:

[Co je nového v aplikaci Visual C++ v sadě Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
