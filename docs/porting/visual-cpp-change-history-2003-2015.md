---
title: Visual C++ změnit historie 2003 2015 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0d4c4aeeaf79172950aae6d06c5e8a1246064246
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705683"
---
# <a name="visual-c-change-history-2003---2015"></a>Historie 2003 2015 změn Visual C++

Tento článek popisuje nejnovějších změn z Visual Studia 2015, přejděte zpět na Visual Studio 2003 a v tomto článku podmínky "nové chování" nebo "teď" prostudujte pro Visual Studio 2015 a novější. Podmínky "staré chování" a "před" odkazovat na Visual Studio 2013 a starších verzích.

Informace o Visual Studio 2017 najdete v tématu [co je nového pro Visual C++ v aplikaci Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) a [shoda vylepšení v jazyce Visual C++ v aplikaci Visual Studio 2017](../cpp-conformance-improvements-2017.md). 

> [!NOTE]
> Neexistují žádné binární nejnovější změny mezi Visual Studio 2015 a Visual Studio 2017.

Při upgradu na novou verzi sady Visual Studio se můžete setkat, kompilace a/nebo chyby za běhu v kódu, který dříve zkompilovat a spustil správně. Změny v nové verzi, které způsobují tyto problémy se označují jako *nejnovější změny*, a obvykle se vyžadovanou úpravy v standardní jazyk C++, funkce podpisy nebo rozložení objektů v paměti.

 Aby se zabránilo chybám za běhu, které by bylo obtížné najít a diagnostikovat, doporučujeme vám nikdy nevytvářet statická propojení na binární soubory, které byly zkompilovány pomocí jiných verzí kompilátoru. Když upgradujete projekt EXE nebo DLL, nezapomeňte také provést upgrade knihoven, na které odkazuje. Pokud používáte CRT (C Runtime) nebo typy standardní knihovny C++ (standardní knihovna C++), není jejich předání binárních souborů (včetně knihovny DLL), které byly zkompilovány pomocí různých verzích kompilátoru. Další informace najdete v tématu [potenciální chyby předávání CRT objekty přes hranice knihovny DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).  
  
 Dále doporučujeme nikdy nepsat kód závislý na konkrétním rozložení pro objekt, který není rozhraním modelu COM nebo objektem POD. Pokud takový kód napíšete, musíte zajistit, aby po upgradu fungoval. Další informace najdete v tématu [přenositelnost v ABI hranice](../cpp/portability-at-abi-boundaries-modern-cpp.md).  
  
 Kromě toho probíhající vylepšení shoda s kompilátorem prostředí můžete někdy změnit jak kompilátor rozumí existujícím zdrojovém kódu. Pokud k tomu dojde, můžete během sestavení nebo i chování rozdíly v kódu, který dříve vytvořené a došlo ke správnému setkat nové nebo jiné chyby. I když tyto nejsou nejnovější změny, jako jsou popsané v tomto dokumentu, zdrojový kód změny mohou být vyžadovány tyto problémy vyřešit.  
  
  
1.  [Nejnovější změny knihovna jazyka C Runtime (CRT)](#BK_CRT)  
  
2.  [Standardní C++ a standardní knihovna C++ nejnovější změny](#BK_STL)  
  
3.  [MFC a knihovna ATL nejnovější změny](#BK_MFC)  
  
4.  [Concurrency Runtime nejnovější změny](#BK_ConcRT)  
  
## <a name="VC_2015"></a> Visual C++ 2015 shoda změny  
  
###  <a name="BK_CRT"></a> Běhové knihovny jazyka C (CRT)  
  
#### <a name="general-changes"></a>Obecné změny  
  
-   **Rozdělili binární soubory** knihovny CRT má byla rozdělili do dvou různých binárních, Universal CRT (ucrtbase), který obsahuje většinu funkcí standardní a knihovny modulu Runtime VC (vcruntime), který obsahuje související kompilátoru Funkce, jako jsou zpracování výjimek a vnitřní funkce. Pokud používáte výchozí nastavení projektu, pak tato změna nemá negativní vliv na je vzhledem k tomu, že linkeru automaticky použije nový výchozí knihovny. Pokud jste nastavili projektu **Linkeru** vlastnost **ignorovat všechny výchozí knihovny** k **Ano** nebo používáte možnost /NODEFAULTLIB linkeru na příkazovém řádku a pak je potřeba Aktualizace vašeho seznamu knihoven (v **Další závislosti** vlastnost) zahrnout do nové, rozdělili knihoven. Nahraďte staré knihovny CRT (libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib) na ekvivalentní refactored knihovny. Pro každé dvě refactored knihovny jsou statické (LIB) a dynamické (.dll) verze a verze (se žádné přípony) a ladicí verze (s příponou "d"). Dynamické verze mají knihovnu importu, který můžete propojit s. Dvě refactored knihovny jsou Universal CRT, konkrétně ucrtbase.dll nebo .lib, ucrtbased.dll nebo .lib a knihovna modulu runtime VC, libvcruntime.lib, vcruntime*verze*.dll, libvcruntimed.lib a vcruntimed*verze*.dll. *Verze* v sadě Visual Studio 2015 a Visual Studio 2017 je 140. V tématu [funkce knihovny CRT](../c-runtime-library/crt-library-features.md).  
  
#### <a name="localeh"></a>\<Locale.h >  
  
-   **localeconv –** [localeconv –](../c-runtime-library/reference/localeconv.md) funkce v deklarována locale.h nyní pracuje správně při [národní prostředí podle vláken](../parallel/multithreading-and-locales.md) je povoleno. V předchozích verzích knihovně by tuto funkci vrácení dat lconv – globální národním prostředí, není národní prostředí vlákna.  
  
     Pokud chcete použít pro národní prostředí vlákna, zkontrolujte používání localeconv – Pokud chcete zobrazit, pokud kód předpokládá, že data lconv – vrátí je pro globální národní prostředí a příslušným způsobem upravte.  
  
#### <a name="mathh"></a>\<Math.h >  
  
-   **C++ přetížení funkce knihovny math** v předchozích verzích \<math.h > definované některé, ale ne všechny přetížení C++ pro matematické funkce knihovny. \<cmath – > definované zbývající přetížení, takže zobrazíte všechny přetížení, jeden obsahovat \<cmath – > záhlaví. To vedlo k problémům s překladem přetížení funkce v kódu, který zahrnuty pouze \<math.h >. Nyní, byly odebrány všechny přetížení C++ z \<math.h > a jsou nyní k dispozici pouze v \<cmath – >.  
  
     Chcete-li vyřešit chyby, zahrnují <cmath> získat deklarace funkcí, které byly odebrány z \<math.h >. Následující tabulka uvádí funkce, které byly přesunuty.  
  
     Funkce, které byly přesunuty:  
  
    1.  dvojité abs(float) abs(double) a float  
  
    2.  Double pow (double, int), float pow (float, float), float pow (float, int), dlouho dvakrát pow (long double, long double), dlouho dvakrát pow (long double, int)  
  
    3.  float a long double verze plovoucí bod funkce acos, acosh –, asin, asinh –, atan, atanh –, atan2, cbrt –, ceil, copysign –, cos, cosh, ERF –, erfc, exp, exp2 –, expm1 –, fabs, fdim –, floor, FMA –, fmax, fmin, fmod, frexp –, hypot –, ilogb –, ldexp –, lgamma –, llrint, llround –, protokolu , log10, log1p –, log2, lrint, lround –, modf –, nearbyint –, nextafter –, nexttoward, zbývající, remquo –, tisknout, kruhové, scalbln, scalbn –, sin, sinh, sqrt, tan, tanh, tgamma –, trunc  
  
     Pokud mají code, používá abs s plovoucí bod typ, který obsahuje jenom hlavičku math.h, procedura bodu bude verze žádné již nebudou dostupné, takže volání i s plovoucí bodu argument, teď přeloží na abs(int). Tímto se vytvoří následující chyba:  
  
    ```Output  
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data  
    ```  
  
     Toto upozornění je nahradit volání abs plovoucí bodu verzi abs, jako je například fabs dvojité argumentu nebo fabsf – pro float argument, nebo zahrnout cmath – hlavička a pokračovat v používání abs.  
  
-   **Plovoucí shoda bodu** mnoho změn do knihovny math mají za cíl vylepšit celkovou shoda na specifikace IEEE 754 a C11 přílohy F, s ohledem na zvláštní případu vstupy například NaN a nekonečno. Quiet NaN vstupy, které byly často považovány za chyby v předchozích verzích knihovny, jsou už považovány za chyby. V tématu [IEEE 754 standardní](http://grouper.ieee.org/groups/754) a přílohy F tohoto [C11 Standard](http://www.iso-9899.info/wiki/The_Standard).  
  
     Tyto změny nezpůsobí chyby při kompilaci, ale může způsobit, že programy chovat jinak a více správně podle standardní.  
  
-   **Flt_rounds –** v sadě Visual Studio 2013, flt_rounds – makro rozšířit tak, aby konstantní výraz, který byl nesprávný, protože je možné konfigurovat za běhu, například pomocí volání fesetround režimu zaokrouhlení. Flt_rounds – makro je nyní dynamické a správně odráží aktuální režim zaokrouhlení.  
  
#### <a name="new-and-newh"></a>\<Nový > a \<new.h >  
  
-   **nové a odstranit** v předchozích verzích knihovny definované implementací new – operátor a odstranění funkce byly exportovány z modulu runtime knihovny DLL (například msvcr120.dll). Tyto funkce operátor jsou nyní vždy staticky propojené do vaší binární soubory, i když pomocí běhové knihovny DLL.  
  
     Toto není narušující změně pro smíšený nebo nativní kód (/ clr), ale pro zkompilovaný kód jako [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), to může způsobit selhání kompilace kódu. Pokud při kompilaci kódu jako/CLR: pure, budete muset přidat #include \<nové > nebo #include \<new.h > obejít sestavení chyb v důsledku této změny. Všimněte si, že/CLR: pure je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017. Kód, který musí být "čistý" musí být přesně do jazyka C#.  
  
#### <a name="processh"></a>\<Process.h >  
  
-   **_beginthread – a _beginthreadex** [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) a [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) funkce teď obsahovat odkaz na modul, ve kterém je definovaný postup vlákno po dobu trvání přístup z více vláken. To pomáhá zajistit, že moduly nejsou odstraněny, až do dokončení má spuštění vlákna.  
  
#### <a name="stdargh"></a>\<stdarg.h>  
  
-   **referenční dokumentace a va_start – typy** při kompilaci kódu C++ [va_start –](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) nyní ověří při kompilaci, který není předaný argument odkazového typu. Argumenty typu odkazu je zakázáno C++ Standard.  
  
#### <a name="stdioh-and-conioh"></a>\<stdio.h > a \<conio.h >  
  
-   **Printf a scanf řadu funkcí jsou nyní definována vložené.** Definice všechny funkce printf a scanf byly přesunuté vložené do \<stdio.h >, \<conio.h > a další CRT záhlaví. Je to narušující změně, který vede k linkeru chyby (LNK2019, nerozpoznané externí symbol) pro všechny programy, které deklarované tyto funkce místně bez zahrnutí odpovídající CRT hlavičky. Pokud je to možné, by měl aktualizovat kód, který patří hlavičky CRT (to znamená, přidat #include \<stdio.h >) a vložené funkce, ale pokud nechcete změnit svůj kód zahrnují tyto soubory hlaviček, je alternativní řešení Chcete-li přidat další Knihovna pro vaše vstupní, legacy_stdio_definitions.lib linkeru.  
  
     Pokud chcete přidat tuto knihovnu pro váš vstup linkeru v prostředí IDE, otevřete v místní nabídce uzlu projektu, zvolte **vlastnosti**, potom v **vlastnosti projektu** dialogové okno Vyberte **Linkeru**a upravit **vstup Linkeru** legacy_stdio_definitions.lib přidat do seznamu oddělených na návěs colon.
     Pokud váš projekt odkazuje statických knihoven, které byly kompilovat s verzí starších než 2015 sady Visual Studio a linkeru hlásit symbol nerozpoznané externí. Tyto chyby může odkazovat na interní stdio definice pro _iob –, _iob_func nebo související importy pro určité funkce stdio ve formě\_*. Společnost Microsoft doporučuje při upgradu na projekt překompilovat všechny statické knihovny s nejnovější verzí kompilátoru C++ a knihovny. Pokud je knihovna knihovnu třetích stran pro zdroj, který není k dispozici, si vyžádat aktualizované binární od třetích stran nebo zapouzdřují vaše použití této knihovny do samostatné knihovny DLL, které zkompilujete se starší verzí kompilátoru a knihovny .
  
    > [!WARNING]
    >  Pokud se připojujete se systémem Windows 8.1 SDK nebo dřívější, může dojít k chybám tyto nerozpoznané externí symbol. V takovém případě byste měli vyřešit chyby přidáním legacy_stdio_definitions.lib linkeru zadejte, jak je popsáno výše.  
  
     Řešení chyb nerozpoznané symbol, můžete se pokusit [dumpbin.exe](../build/reference/dumpbin-reference.md) prozkoumat symboly definované v binární. Zkuste následující příkazový řádek pro zobrazení symbolů definovaných v knihovně.  
  
    ```cpp  
    dumpbin.exe /LINKERMEMBER somelibrary.lib  
    ```  
  
-   **Získá a _getws –** [získá](../c-runtime-library/gets-getws.md) a [_getws –](../c-runtime-library/gets-getws.md) funkce byly odebrány. Získá funkce byla odebrána ze standardní knihovny jazyka C v C11, protože jej nelze použít bezpečně. _Getws – funkce byla Microsoft rozšíření, která byla ekvivalentní získá, ale pro celou řetězce. Jako alternativy tyto funkce, zvažte použití [fgets –](../c-runtime-library/reference/fgets-fgetws.md), [fgetws –](../c-runtime-library/reference/fgets-fgetws.md), [gets_s –](../c-runtime-library/reference/gets-s-getws-s.md), a [_getws_s –](../c-runtime-library/reference/gets-s-getws-s.md).  
  
-   **_cgets – a _cgetws –** [_cgets –](../c-runtime-library/cgets-cgetws.md) a [_cgetws –](../c-runtime-library/cgets-cgetws.md) funkce byly odebrány. Jako alternativy tyto funkce, zvažte použití [_cgets_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md) a [_cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
-   **Infinity a formátování NaN** v předchozích verzích nekonečno a NaN by formátován pomocí sadu specifické MSVC sentinel řetězce.  
  
    -   Infinity: 1. #INF  
  
    -   Quiet NaN: 1. #QNAN  
  
    -   Signalizační NaN: 1. #SNAN  
  
    -   Neomezené NaN: 1. #IND  
  
     Některý z těchto může mít předponu znakem a může mít naformátován trochu jinak v závislosti na šířku pole a přesnost (někdy s neobvyklou důsledky, například printf ("%.2f\n", INFINITY) by vytisknout 1. #J vzhledem k tomu, že #INF by "zaokrouhlen" přesností 2 číslic). C99 zavedeny nové požadavky na tom, jak nekonečno a NaN mají být ve formátu. Implementace MSVC teď vyhovuje tyto požadavky. Nové řetězce jsou následující:  
  
    -   Infinity: inf  
  
    -   Quiet NaN: nan.  
  
    -   Signalizace NaN: nan(snan)  
  
    -   Neomezené NaN:nan(ind)  
  
     Některý z těchto může obsahovat předponu znakem. Pokud specifikátor kapitálové formát je použita (%F místo %f), pak budou vytištěny řetězce ve velkých písmen (INF místo inf), jako je požadovaná.  
  
     [Scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkce bylo upraveno, aby analyzovat těchto nových řetězců, takže bude mít odezvu prostřednictvím printf a scanf, tyto řetězce.  
  
-   **Plovoucí bodu formátování a analýza** ke zlepšení správnost byly zavedeny nové plovoucí bodu formátování a analýza algoritmy. Tato změna ovlivňuje [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) a [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) rodiny funkce, jakož i funkce jako [strtod –](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).  
  
     Na staré formátování algoritmy by vygeneroval pouze omezený počet číslic a potom by vyplníte zbývající desetinných míst nula. To je obvykle dostatečně vhodný k vygenerování řetězce, které bude operace round-trip zpět původní hodnotu s plovoucí desetinnou čárkou, ale není skvělé, pokud chcete přesná hodnota (nebo jejich nejbližší decimal reprezentace). Jak velký počet číslic, jako jsou potřeba k zobrazení hodnoty (nebo k vyplnění Zadaná přesnost) generují nových algoritmů formátování. Jako příklad zlepšování; Při tisku velké power dva vezměte v úvahu výsledky:  
  
    ```cpp  
    printf("%.0f\n", pow(2.0, 80))  
  
    ```  
  
    ```Output  
        Old:  1208925819614629200000000    New:  1208925819614629174706176  
    ```  
  
     Původní analýzy algoritmy jsou považovány za pouze až 17 platných číslic ze vstupního řetězce a by zahodit rest číslic. Toto je k dispozici velmi blízká aproximace hodnoty reprezentována řetězec a výsledek je obvykle velmi blízké správně zaokrouhlené výsledku. Novou implementací považovat všechny přítomen číslic a vytvoří správně zaokrouhlené výsledek pro všechny vstupy (délku až 768 číslice). Kromě toho tyto funkce teď respektují zaokrouhlení režimu (ovladatelné prostřednictvím fesetround).  Toto je potenciálně nejnovější chování změnit, protože tato funkce může výstup odlišné výsledky. Nové výsledky jsou vždy správné než původní výsledky.  
  
-   **Hexadecimální a infinity nebo NaN plovoucí bodu analýza** plovoucí desetinné čárky analýza algoritmy bude nyní analyzovat hexadecimálních řetězců plovoucí bodu (jako jsou ty vygenerovaných %a a specifikátory formátu printf %A) a všechny infinity a NaN řetězce generované funkce printf, jak je popsáno výše.  
  
-   **%A a %a nula odsazení** specifikátory formátu %a a %A formátu plovoucí bodu číslo jako hexadecimální mantisa a exponent binární. V předchozích verzích by funkce printf nesprávně nula pad řetězce. Například printf ("%07.0a\n", 1.0) by vytisknout 00x1p + 0, kde má vytisknout 0x01p + 0. To byl opraven.  
  
-   **Přesnost %A a %a** výchozí přesnost specifikátorů formátu %A a %a byl 6 v předchozích verzích knihovny. Výchozí přesnost je nyní 13 pro shodu s standardní C.  
  
     Jedná se o změnu modul runtime chování ve výstupu všechny funkce, která používá řetězec formátu s %A nebo %. V původním chování může být výstup pomocí specifikátor %A "1.1A2B3Cp + 111". Výstup pro stejnou hodnotu je nyní "1.1A2B3C4D5E6F7p + 111". Chcete-li získat staré chování, můžete zadat přesnost, například %.6A. V tématu [specifikace přesnosti](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).  
  
-   **Specifikátor %F** specifikátor převod formátu nebo %F se teď podporuje. Je funkčně srovnatelný specifikátor formátu %f, avšak nekonečno NaN formátování a používání písmeny.  
  
     V předchozích verzích implementace použitá k analýze F a N jako modifikátory délka. Toto chování s datem zpět na stáří segmentovaným adresních prostorů: tyto délka modifikátory jste použili k označení daleko a téměř ukazatele, hodnoty, jako % Fp nebo %Ns. Toto chování byla odebrána. Pokud je zjištěna %F, se teď zpracovává jako specifikátor formátu %F; Pokud je %N došlo, je nyní považovány za neplatný parametr.  
  
-   **Exponent formátování** %e a %E formátu specifikátory formátu plovoucí bodu číslo jako decimal mantisa a exponent. Specifikátory formátu %G a %g také formátování čísel v tomto formuláři v některých případech. V předchozích verzích by CRT vždy vygenerovat řetězce s třímístné exponenty. Například by printf ("%e\n", 1.0) vytisknout 1.000000e + 000. To byl nesprávný: C vyžaduje, že pokud exponent reprezentovat pomocí jednoho nebo dvou číslic, pak pouze dvě číslice se mají vytisknout.  
  
     V sadě Visual Studio 2005 byl přidán přepínač globální shoda: [_set_output_format –](../c-runtime-library/set-output-format.md). Program může volat tuto funkci s _two_digit_exponent – argument, povolení vyhovující exponentu tisku. Výchozí chování se změnil na odpovídající standardy exponentu tisk režimu.  
  
-   **Formátování řetězce ověření** v předchozích verzích, bude funkce printf a scanf bezobslužně přijímat mnoho neplatný formát řetězce, někdy s neobvyklou důsledky. Například % hlhlhld považována za %d. Všechny neplatný formát řetězce jsou nyní považovány za neplatné parametry.  
  
-   **fopen – režim řetězec ověření**  
  
     V předchozích verzích fopen – řadu funkcí bezobslužně přijaté některé řetězce neplatný režim (například r + b +). Neplatný režim řetězce jsou nyní zjištěn a považovány za neplatné parametry.  
  
-   **Režim _O_U8TEXT**  
  
     [_Setmode –](../c-runtime-library/reference/setmode.md) funkce nyní správně sestavy režim datové proudy otevřít in_O_U8TEXT režimu. V předchozích verzích knihovny ho by takové datové proudy jako otevíráte v _O_WTEXT sestavy.  
  
     Toto je narušující změně, pokud kód interpretuje _O_WTEXT režimu pro datové proudy, kde s kódováním je UTF-8. Pokud vaše aplikace nepodporuje UTF_8, zvažte přidání podpory pro toto stále běžné kódování.  
  
-   **snprintf – a vsnprintf –** [snprintf –](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) a [vsnprintf –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) funkce se teď implementuje. Starší kód často najdete definice makro verze těchto funkcí, protože nejsou implementované knihovny CRT, ale tyto již nejsou potřebné v novější verzi. Pokud [snprintf –](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) nebo [vsnprintf –](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) je definován jako makra před zahrnutím \<stdio.h >, kompilace nyní selže s chybou, která určuje, kde byla definována makro.  
  
     Za normálních okolností opravu tohoto problému je odstranit všechny deklarace snprintf – nebo vsnprintf – v uživatelském kódu.  
  
-   **tmpnam – vygeneruje použitelné názvy souborů** v předchozích verzích funkce tmpnam – a tmpnam_s – vygenerované názvy souborů v kořenovém adresáři jednotky (například \sd3c.). Tyto funkce nyní generovat použitelný název cesty v dočasném adresáři.  
  
-   **Zapouzdření souboru** v předchozích verzích, byl tento typ souboru úplně definovaný v \<stdio.h >, aby bylo možné pro uživatelský kód k dosažení do souboru a jeho internals upravit. Knihovna stdio byl změněn na skrýt podrobnosti implementace. V rámci tohoto souboru, jak jsou definovány v \<stdio.h > je teď typ neprůhledné a jeho členové jsou nedostupné z mimo CRT sám sebe.  
  
-   **_outp – a _inp –** funkce [_outp –](../c-runtime-library/outp-outpw-outpd.md), [_outpw –](../c-runtime-library/outp-outpw-outpd.md), [_outpd –](../c-runtime-library/outp-outpw-outpd.md), [_inp –](../c-runtime-library/inp-inpw-inpd.md), [_inpw –](../c-runtime-library/inp-inpw-inpd.md), a [_inpd –](../c-runtime-library/inp-inpw-inpd.md) byly odebrány.  
  
#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h >, \<malloc.h >, a \<sys/stat.h >  
  
-   **strtof – a wcstof –** funkce strtof – a wcstof – Nepodařilo se nastavit kód chyby na erange – Pokud hodnota nebyla reprezentovat jako plovoucí desetinné čárky. To byl opraven. (Upozorňujeme, že se tato chyba specifická pro tyto dvě funkce; strtod –, wcstod –, strtold a wcstold funkce byla poškozena.) To je modul runtime nejnovější změny.  
  
-   **Funkce přidělení zarovnán** v předchozích verzích by zarovnaných přidělení funkce (_aligned_malloc –, _aligned_offset_malloc – atd.) bezobslužně přijímat žádosti o blok s zarovnání 0. Požadovaný zarovnání musí být násobek dvou, které nula není. Tato chyba byla opravena a požadovaný zarovnání 0 je nyní považován za neplatný parametr. To je modul runtime nejnovější změny.  
  
-   **Haldy funkce** _heapadd – _heapset – a _heapused funkce byly odebrány. Tyto funkce nejsou funkční, vzhledem k tomu, že byl upraven CRT k použití haldy Windows.  
  
-   **smallheap** možnosti propojení smalheap byla odebrána. V tématu [odkaz Možnosti](../c-runtime-library/link-options.md).  
  
#### <a name="stringh"></a>\<String.h >  
  
-   **wcstok –** podpis wcstok – funkce se změnil tak, aby odpovídaly podle standardní C požadavku. V předchozích verzích knihovny podpis tato funkce byla:  
  
    ```cpp  
    wchar_t* wcstok(wchar_t*, wchar_t const*)  
    ```  
  
     Sledování stavu napříč volání, jak se provádí pro strtok – použije kontextu interní vlákno. Teď má podpis wchar_t * wcstok – funkce (wchar_t\*, wchar_t const\*, wchar_t\*\*) a vyžaduje volající předávat kontext jako třetí argument funkce.  
  
     Byla přidána nové funkce _wcstok s původním podpisu k usnadnění portování. Při kompilování kódu C++, je také vložené přetížení wcstok –, které má starý podpis. Toto přetížení je deklarován jako zastaralé. V kódu jazyka C může define_CRT_NON_CONFORMING_WCSTOK způsobí _wcstok má být použit místo wcstok –.  
  
#### <a name="timeh"></a>\<Time.h >  
  
-   **hodiny** v předchozích verzích [hodiny](../c-runtime-library/reference/clock.md) funkce byla implementována pomocí rozhraní API systému Windows [GetSystemTimeAsFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724397.aspx). S touto implementací funkce hodin byl citlivé systémového času a nebyl proto nutně monotónní. Funkce hodin má byla reimplemented z hlediska [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) a nyní je monotónní.  
  
-   **fstat – a _utime –** v předchozích verzích [_stat –](../c-runtime-library/reference/stat-functions.md), [fstat –](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), a [_utime –](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) funkce zpracování letní čas nesprávně. Před Visual Studiu 2013 se všechny tyto funkce nesprávně upravena časy (běžný čas) jako v případě, že byly v letní čas.  
  
     V sadě Visual Studio 2013 problém byl opraven v _stat – řadu funkcí, ale podobné problémy v řadách fstat – a _utime – funkce nebyly odstraněny. To vedlo k problémům nekonzistence mezi funkce. Nyní bylo opraveno fstat – a _utime – řady funkcí, takže všechny tyto funkce nyní zpracovat letní čas správnou a konzistentní.  
  
-   **asctime –** v předchozích verzích [asctime –](../c-runtime-library/reference/asctime-wasctime.md) funkce by odsadí řádu dnů s úvodní nuly, například: pátek června 06 08:00:00 2014. Specifikace vyžaduje, aby takové dnů bude doplněn s úvodní mezery, například pátek června 6 08:00:00 2014. To byl opraven.  
  
-   **STRFTIME – a wcsftime –** STRFTIME – a wcsftime – funkce teď podporují %C, specifikátory formátu %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u a %V. Kromě toho jsou modifikátory E a O analyzovat, ale ignoruje.  
  
     Specifikátor formátu %c je zadán jako generovala služby "odpovídající datum a čas reprezentace" pro aktuální národní prostředí. Pro prostředí C tento reprezentace musí být stejný jako %a %b %e %T %Y. Toto je stejný jako formulář, jako je produkovaný asctime –. V předchozích verzích specifikátor formátu %c nesprávně naformátováno časy pomocí znázornění hh: mm: MM/DD/RR. To byl opraven.  
  
-   **timespec a TIME_UTC** \<time.h > záhlaví teď definuje timespec typ a funkci timespec_get z standardní C11. Kromě toho je nyní definována TIME_UTC makro, pro použití s funkci timespec_get. Toto je zásadní změnu kód, který má konfliktní definice pro některý z těchto.  
  
-   **CLOCKS_PER_SEC** CLOCKS_PER_SEC makro teď zasahuje do celé clock_t – typ, podle potřeby podle jazyka C.  
  
####  <a name="BK_STL"></a> Standardní knihovna C++  
 Pokud byte chtěli povolit nové optimalizace a kontroly ladění, implementace standardní knihovny C++ záměrně neumožňuje binární kompatibilitu mezi verzemi. Proto při použití standardní knihovny C++ nelze objektové soubory a statické knihovny, které jsou kompilovány pomocí různých verzí, směšovat v jednom binárním souboru (EXE nebo DLL) a objekty standardní knihovny C++ nelze předávat mezi binárními soubory, které jsou kompilovány pomocí různých verzí. Takovéto směšování objektů vyvolává chyby linkeru týkající se neshod _MSC_VER. (Je _msc_ver – makro, který obsahuje hlavní verzi kompilátoru – například 1 800 pro Visual Studio 2013.) Tato kontrola nemůže zjistit kombinování knihovny DLL a nerozpozná kombinování, která zahrnuje sady Visual Studio 2008 nebo starším.  
  
-   **Standardní knihovna C++ zahrnout soubory** byly provedeny některé změny na strukturu zahrnout v hlavičkách standardní knihovna C++. Hlavičky standardní knihovna C++ mohou zahrnovat navzájem neurčené způsoby. Obecně platí by měl zadejte kód, tak, že všechny hlavičky, které se musí podle C++ standard a nemá spoléhají na které standardní knihovna C++ hlavičky zahrnují které jiné záhlaví standardní knihovna C++ pečlivě obsahují. Díky tomu kód přenosné mezi verzemi a platformy. Alespoň dva záhlaví změny v sadě Visual Studio 2015 ovlivnit uživatelského kódu. První, \<řetězec > už obsahuje \<iterator >. Druhý, \<řazené kolekce členů > teď deklaruje std::array bez včetně všech \<pole >, který může dojít k narušení kódu pomocí následující kombinace kódu konstrukce: váš kód obsahuje proměnné s názvem "pole" a vy musíte pomocí direktiva "pomocí obor názvů – std; ", a zahrnete hlavičku standardní knihovna C++ (například \<funkční >), který obsahuje \<řazené kolekce členů >, které teď deklaruje std::array.  
  
-   **steady_clock –** \<typu chrono > implementace [steady_clock –](../standard-library/steady-clock-struct.md) došlo ke změně splnění C++ Standard pro steadiness a monotonicity. steady_clock – je teď na základě [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) a high_resolution_clock je nyní typedef pro steady_clock –. V důsledku toho v sadě Visual Studio steady_clock::time_point je nyní typedef pro chrono::time_point < steady_clock – >; je to ale není nutně případ jiné implementace.  
  
-   **alokátorů a const** teď vyžadujeme porovnání rovnost či nerovnost allocator tak, aby přijímal const argumenty na obou stranách.  Pokud vaše alokátorů definujte tyto operátory takto:  
  
    ```cpp  
    bool operator==(const MyAlloc& other)  
    ```  
  
     Je třeba aktualizovat tyto je deklarovat jako const členy.  
  
    ```cpp  
    bool operator==(const MyAlloc& other) const  
    ```  
  
-   **Const elementy** C++ standard má vždy zakázáno kontejnery elementů const (například vektoru\<const T >, nebo nastavte\<const T >). Visual Studio 2013 a starší přijaté takové kontejnery. V aktuální verzi tyto kontejnery nepodaří zkompilovat.  
  
-   **std::Allocator:: navrácení** v sadě Visual Studio 2013 a starší, std::allocator::deallocate(p, n) ignorovat argument předaná n.  Standardní C++ vždy vyžaduje, že n být stejná jako hodnota předaná jako první argument vyvolání přidělit, který vrátil p. V aktuální verzi, ale hodnota n se prozkoumá. Kód, který předá argumenty pro n, které se liší od jaké standardní vyžaduje může dojít k chybě za běhu.  
  
-   **hash_map – a hash_set** nestandardní hlavičky souborů hash_map a hash_set jsou zastaralé v sadě Visual Studio 2015 a bude v budoucí verzi odebrána. Místo toho použijte unordered_map a unordered_set.  
  
-   **komparátorů a Operator() –** asociativní kontejnery ( \<mapy > rodiny) teď vyžadují jejich komparátorů tak, aby měl volatelná aplikacemi const funkce volání operátory. Následující kód v deklaraci třídy Komparátor, který je teď se nepovede zkompilovat:  
  
    ```cpp  
    bool operator()(const X& a, const X& b)  
    ```  
  
     Chcete-li tuto chybu vyřešit, změňte deklarace funkce na:  
  
    ```cpp  
    bool operator()(const X& a, const X& b) const  
    ```  
  
-   **Zadejte vlastnosti** původní názvy pro typové vlastnosti ze starší verze konceptu standardní C++ byly odebrány. Tyto byly změněny v C ++ 11 a byly aktualizovány na C ++ 11 hodnoty v sadě Visual Studio 2015. V následující tabulce jsou uvedeny staré a nové názvy.  
  
    |Starý název|Nový název|  
    |--------------|--------------|  
    |add_reference|add_lvalue_reference|  
    |has_default_constructor|is_default_constructible|  
    |has_copy_constructor|is_copy_constructible|  
    |has_move_constructor|is_move_constructible|  
    |has_nothrow_|is_nothrow_default_constructible|  
    |has_nothrow_default_constructor|is_nothrow_default_constructible|  
    |has_nothrow_copy –|is_nothrow_copy_constructible|  
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
  
-   **zásady Launch::Any a launch::sync** nestandardní zásady launch::any a launch::sync byly odebrány. Místo toho použijte pro launch::any, spusťte: asynchronní &#124; spusťte: odložené. Pro launch::sync použijte launch::deferred. V tématu [launch – výčet](../standard-library/future-enums.md#launch).  
  
####  <a name="BK_MFC"></a> MFC a knihovna ATL  
  
-   **Microsoft Foundation třídy (MFC)** je už součástí "Typické" instalací sady Visual Studio z důvodu jeho velké. Chcete-li nainstalovat MFC, zvolte možnost Vlastní instalace v instalačním programu sady Visual Studio 2015. Pokud je již nainstalovaná sada Visual Studio 2015, můžete nainstalovat MFC opětovné spuštění instalačního programu sady Visual Studio, zvolíte možnost Vlastní instalace a zvolením Microsoft Foundation třídy. Můžete znovu spustit instalaci sady Visual Studio z ovládacích panelů, programů a funkcí, nebo z instalačního média.  
  
     Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.  
  
####  <a name="BK_ConcRT"></a> Concurrency Runtime  
  
-   **YIELD – makro z konfliktní s concurrency::Context::Yield odkazující na Windows** Concurrency Runtime použil #undef k nedefinované makro Yield jak zamezit konfliktům mezi makro Yield definované v h odkazující na Windows a concurrency::Context: : Yield funkce. Odebrali jsme tento #undef a nové-konfliktní ekvivalentní rozhraní API volat [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) byla přidána. Je v konfliktu s Yield obejít, můžete buď aktualizujte kód a místo toho zavolejte funkci YieldExecution nebo uveďte název funkce Yield v hranatých závorkách v lokalitách, volání, jako v následujícím příkladu:  
  
    ```cpp  
    (concurrency::Context::Yield)();  
    ```  
  
## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Vylepšení kompilátoru shoda v sadě Visual Studio 2015  
 Při upgradu kódu z předchozích verzí, může dojít také chyby kompilátoru, které jsou z důvodu vylepšení shoda provedené v sadě Visual Studio 2015. Tato vylepšení nedojde k narušení binární kompatibilitu z dřívějších verzí sady Visual Studio, ale může vést k chybám kompilátoru kde žádné byly vygenerované před. Další informace najdete v tématu [Visual C++ Co je nového 2003 až 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).  
  
 V sadě Visual Studio 2015 probíhající vylepšení shoda s kompilátorem prostředí můžete někdy změnit, jak kompilátor rozumí existujícím zdrojovém kódu. Pokud k tomu dojde, můžete během sestavení nebo i chování rozdíly v kódu, který dříve vytvořené a došlo ke správnému setkat nové nebo jiné chyby.  
  
 Naštěstí tyto rozdíly mít žádné nebo téměř žádné dopad na většinu vašeho zdrojového kódu a vyřešit tyto rozdíly jsou potřeba zdrojový kód nebo další změny, opravy jsou obvykle malé a jednoduché. Jsme zahrnuli mnoho příklady dříve přijatelné zdrojový kód, který může být nutné změnit *(před)* a opravy a opravte je *(po)*.  
  
 I když tyto rozdíly mohou ovlivnit váš zdrojový kód nebo artefaktů sestavení, neovlivňují binární kompatibilitu mezi jednotlivými aktualizace verzí sady Visual Studio. Další závažné druhu změny, *nejnovější změny* může mít vliv na binární kompatibilitu, ale tyto typy binární kompatibilitu zalomení dojít pouze mezi hlavní verze sady Visual Studio. Například mezi Visual Studio 2013 a Visual Studio 2015. Informace o nejnovějších změn, které došlo mezi Visual Studio 2013 a Visual Studio 2015, najdete v části [Visual Studio 2015 shoda změny](#VC_2015).  
  
-   [Vylepšení shoda v sadě Visual Studio 2015](#VS_RTM)  
  
-   [Shoda vylepšení v aktualizaci 1](#VS_Update1)  
  
-   [Shoda vylepšení v aktualizaci 2](#VS_Update2)  
  
-   [Shoda vylepšení v aktualizaci 3](#VS_Update3)  
  
###  <a name="VS_RTM"></a> Vylepšení shoda v sadě Visual Studio 2015  
  
-   Možnost /Zc:forScope-  
  
     Možnost kompilátoru **/Zc:forScope-** je zastaralá a bude v budoucí verzi odebrána.  
  
    ```cpp  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     Chcete-li povolit nestandardní kód, který používá cykly proměnné za bod, kde podle standard, že by se nachází mimo obor se obvykle použila možnost. Byla pouze nezbytné při jsou kompilaci s parametrem /Za od bez /Za, použití pro proměnnou smyčky po konci smyčky je vždycky povolená. Pokud vám nezáleží standardy shoda (například pokud není určena pro přenosný na jiné kompilátory kódu), můžete je možnost /Za (nebo nastavte vlastnost zakázat jazyková rozšíření na Ne). Pokud se zajímáte o psaní kódu přenosné, kompatibilní se standardy, by se tak, aby u standardního přesunutím deklaraci takovéto proměnné do bodu mimo smyčky přepište kód.  
  
    ```cpp  
    // C2065 expected  
    int main() {  
        // Uncomment the following line to resolve.  
        // int i;  
        for (int i = 0; i < 1; i++);  
        i = 20;   // i has already gone out of scope under /Za  
    }  
  
    ```  
  
-   **/Zg – možnost kompilátoru**  
  
     Možnost kompilátoru /Zg (Generovat prototypy funkcí) již není k dispozici. Tato možnost kompilátoru byl dříve zastaralé.  
  
-   Už spuštěním testů jednotek s C + +/ CLI z příkazového řádku s mstest.exe. Místo toho použijte vstest.console.exe. V tématu [možnosti příkazového řádku VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options).  
  
-   **Mutable – klíčové slovo**  
  
     `mutable` Specifikátor třídy úložiště je již povolen v místech, kde dříve ho kompilovat bez chyby. Nyní, kompilátor poskytuje chyba C2071 (třída neplatné úložiště). Proměnný specifikátor podle standard, lze použít pouze na názvy členů tříd dat a nelze použít pro názvy deklarovaný const nebo statické a nelze použít k odkazování členů.  
  
     Zvažte například následující kód:  
  
    ```cpp  
    struct S   
    {  
        mutable int &r;  
    };  
  
    ```  
  
     To akceptovat předchozí verze kompilátoru, ale teď kompilátor dává k následující chybě:  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     Chcete-li chybu opravit, odeberte jednoduše redundantní mutable – klíčové slovo.  
  
-   **char_16_t a char32_t**  
  
     Už můžete `char16_t` nebo `char32_t` jako aliasy v definici typu, protože tyto typy jsou nyní považovány za předdefinované. Bylo běžné pro uživatele a knihovna autorům zadat char16_t a char32_t jako aliasy uint16_t a uint32_t, v uvedeném pořadí.  
  
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
  
     Aktualizace kódu, odeberte deklarace typedef a dalších identifikátorů, které je v konfliktu s těmito názvy přejmenovat.  
  
-   **Parametry šablony non-type**  
  
     Některé kód, který zahrnuje parametry šablon bez typu je nyní správně kontrolována typ kompatibility při zadat explicitní šablony argumenty. Například následující kód kompilovat bez chyby v předchozích verzích sady Visual Studio.  
  
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
  
     Aktuální kompilátor správně vrátí chybu, protože se neshoduje typ parametru šablony argumentu šablony (parametr je ukazatel na člena const, ale bez const je funkce f):  
  
    ```Output  
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'  
    ```  
  
     Chcete-li vyřešit tuto chybu v kódu, ujistěte se, že typ argumentu šablony používáte odpovídá deklarovaný typ parametr šablony.  
  
-   **__declspec(align)**  
  
     Kompilátor již přijímá `__declspec(align)` na funkce. To vždy ignorovat, ale nyní je dojde k chybě kompilátoru.  
  
    ```cpp  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     Chcete-li tento problém vyřešit, odeberte `__declspec(align)` z deklarace funkce. Vzhledem k tomu, že ho měl žádný vliv, odebrat ho nezmění nic.  
  
-   **Zpracování výjimek**  
  
     Existuje několik změn výjimek. Objekty výjimek nejprve musí být kopírovatelná nebo mobilní. Následující kód kompilovat v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nejde kompilovat v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
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
  
     Problém je, že je konstruktor copy privátní, takže objekt nelze kopírovat, jak se stane při běžném průběhu zpracovávat výjimku. Totéž platí i když je deklarovaná konstruktor copy `explicit`.  
  
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
  
     Aktualizace kódu, ověřte, že je konstruktor copy pro vaše objekt výjimky veřejné a není určena `explicit`.  
  
     Zachytávání výjimku hodnotou taky vyžaduje výjimka objekt, který má být kopírovatelná. Následující kód kompilovat v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nejde kompilovat v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
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
  
     Tento problém můžete vyřešit tak, že změníte typ parametru pro `catch` na odkaz.  
  
    ```cpp  
    catch (D& d)  
    {  
    }  
  
    ```  
  
-   **Textové literály, za nímž následuje makra**  
  
     Kompilátor teď podporuje uživatelsky definované literály. Textové literály, za nímž následuje makra bez jakékoli použité prázdných znaků v důsledku toho jsou interpretovány jako uživateli definované literály, které může být chyby nebo neočekávané výsledky. Například v předchozí kompilátory následující kód zkompilovat úspěšně:  
  
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
  
     Kompilátor interpretuje to jako řetězec literálu text "hello" následované makra, která je rozšířena "existuje", a pak se dva textové literály zřetězen do jednoho. V [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], kompilátor interpretuje jako literál definovaný uživatelem, ale vzhledem k tomu, že neexistuje žádné odpovídající uživatelské literálu _x definované, nabízí k chybě.  
  
    ```Output  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
    ```  
  
     Chcete-li tento problém vyřešit, přidejte mezeru mezi řetězcový literál a makra.  
  
-   **Sousední textové literály**  
  
     Podobně jako na předchozí, z důvodu související změny při analýze řetězce, byly přiléhající textové literály (buď široké nebo úzké znak textové literály) bez jakékoli prázdné interpretovat jako jeden řetězec zřetězených v předchozích verzích Visaul C++. V [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], je nutné přidat nyní mezery mezi dva řetězce. Například je třeba změnit následující kód:  
  
    ```cpp  
    char * str = "abc""def";  
    ```  
  
     Stačí přidáte mezeru mezi dva řetězce.  
  
    ```cpp  
    char * str = "abc" "def";  
    ```  
  
-   **Nové umístění a odstranění**  
  
     Ke změně byl proveden operátor delete, aby byla v shoda s C ++ 14 standardní. Podrobnosti o změnu standardy najdete na [C++ velikost navrácení](http://isocpp.org/files/papers/n3778.html). Změny přidat formu globální odstranit operátor, který přebírá parametr velikosti. Narušující změně je, že pokud jste dříve používali delete – operátor se stejným podpisem (tak, aby odpovídaly s operátor new umístění), zobrazí se chyba kompilátoru (C2956, který probíhá v okamžiku, kdy nové umístění se používá, protože to je operátor delete pozici v kódu, kde se pokusí identifikovat odpovídající odpovídající kompilátor).  
  
     Funkce `void operator delete(void *, size_t)` byl operátor delete umístění odpovídající nové funkce umístění "void \* new – operátor (size_t –, size_t –)" v C ++ 11. S C ++ 14 velikostí navrácení, tato funkce odstranění je teď *funkce obvykle navrácení* (globální delete – operátor). Standardní vyžaduje, aby pokud použití nové umístění vyhledá odpovídající funkce odstranit a vyhledá funkce obvykle navrácení, program nedůvěryhodný.  
  
     Předpokládejme například, že váš kód definuje nové umístění a odstranění umístění:  
  
    ```cpp  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     K problému dochází kvůli shodu v signatury funkce mezi operátor delete umístění, kterou jste definovali a operátor new globální velikostí odstranit. Zvažte, jestli můžete použít jiného typu než size_t – pro všechny umístění nový a odstranit operátory.  Upozorňujeme, že je typ size_t – typedef kompilátoru závislé; je typedef pro nepodepsané int v MSVC. Dobrým řešením je použití Výčtový typ jako je tato:  
  
    ```cpp  
    enum class my_type : size_t {};  
  
    ```  
  
     Pak změňte svou definici nové umístění a odstranit tento typ slouží jako druhý argument místo size_t –. Také budete muset aktualizovat volání do umístění nové předat nový typ (například pomocí `static_cast<my_type>` převést z celočíselnou hodnotu) definici nové aktualizace a odstranit zpět přetypovat na typ integer. Nemusíte používat výčet pro tento; Typ třídy s členem size_t – by taky měly fungovat.  
  
     Alternativní řešení je, že může být schopni zcela eliminovat nové umístění. Pokud váš kód používá umístění nového k implementaci fondu paměti, kde argument umístění je velikost na objekt, který přidělené nebo odstraněna, pak velikostí navrácení funkce může být vhodný nahradit vlastní kód vlastní paměti fondu a můžete získat odstranit umístění funkce a právě použít vlastní dva argument delete – operátor místo funkce umístění.  
  
     Pokud nechcete, aby váš kód okamžitou aktualizaci, můžete se vrátit k původní chování pomocí možnosti kompilátoru /Zc:sizedDealloc-. Pokud použijete tuto možnost, odstranění dva argument funkce neexistují a nebude způsobit konflikt s vaší umístění delete – operátor.  
  
-   **Union datové členy**  
  
     Data členů sjednocení už můžete mít odkazové typy. Následující kód zkompilovat úspěšně v [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale vytvoří chybu v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
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
  
     Chcete-li tento problém vyřešit, změňte odkazové typy buď na ukazatel nebo na hodnotu. Změna typu na ukazatel vyžaduje změny v kódu, který používá pole union. Změna kódu na hodnotu změní data uložená v union, který ovlivňuje další pole, protože pole v union typy sdílejí stejnou paměť. V závislosti na velikosti hodnotu se může také změnit velikost sjednocení.  
  
-   Anonymní sjednocení jsou teď další vyhovující pro standardní. Předchozí verze kompilátoru generovány explicitní konstruktor a destruktor pro anonymní sjednocení. Ty se odstraní [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
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
  
     Předchozí kód generuje následující chybu v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```cpp  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
  
    ```  
  
     Chcete-li vyřešit tento problém, zadejte vlastní definice konstruktor a/nebo destruktor.  
  
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
  
-   **Sjednocení s anonymní struktury**  
  
     Chcete-li v souladu se standardem, došlo ke změně modulu runtime chování pro členy anonymní struktury ve sjednoceních. V konstruktoru pro anonymní struktury členy ve spojení se nazývá už implicitně při vytváření této unie. Destruktor pro členy anonymní struktury sjednocení navíc je už implicitně volána, když sjednocení ocitne mimo rozsah. Vezměte v úvahu následující kód, ve kterém sjednocení U obsahuje strukturu anonymní, který obsahuje člena, který je s názvem struktura S, který má destruktor.  
  
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
  
     V [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], v konstruktoru pro S je volána, když se vytvoří sjednocení a destruktor pro S je volána, když je v zásobníku pro funkci f vyčištěna. Ale v [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], nejsou volá konstruktor a destruktor. Kompilátor poskytuje upozornění o této změně chování.  
  
    ```Output  
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called  
    ```  
  
     Pokud chcete obnovit původní chování, pojmenujte strukturu anonymní. Modul runtime chování anonymní struktury je stejný, bez ohledu na verzi kompilátoru.  
  
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
  
     Případně zkuste přesun konstruktor a destruktor kód do nové funkce a přidejte volání na tyto funkce z konstruktoru a destruktoru pro sjednocení.  
  
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
  
-   **Šablona řešení**  
  
     Překlad názvů pro šablony byly provedeny změny. V jazyce C++ při zvažování kandidáty pro překlad názvu může být případ, že jeden nebo více názvů v úvahu jako potenciální odpovídá vytváří vytváření instancí šablon neplatný. Tyto neplatné konkretizací obvykle nezpůsobí chyby kompilátoru, zásadu, která se označuje jako sfinae u výrazů (nahrazení selhání je není chyba).  
  
     Nyní pokud sfinae u výrazů vyžaduje kompilátor k vytváření instancí specializace šablony třídy, pak všechny chyby, ke kterým došlo během tohoto procesu jsou chyby kompilátoru. V předchozích verzích by kompilátor ignorovat takové chyby. Zvažte například následující kód:  
  
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
  
     Pokud kompilujete s aktuální kompilátoru, zobrazí se následující chyba:  
  
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
  
     Důvodem je, že v místě první volání is_base_of třídy by se ještě nebyl definován.  
  
     V takovém případě je nechcete používat takové typové vlastnosti, dokud byla třída definována. Pokud přesunete definice B a D na začátek souboru kódu, se vyřeší chyby. Pokud definice v soubory hlaviček, zkontrolujte pořadí příkazy include pro soubory hlaviček a ujistěte se, že všechny definice tříd jsou kompilovat, než se používají problematické šablony.  
  
-   **Kopírovací konstruktory**  
  
     V obou [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] a Visual Studio 2015, kompilátor generuje kopírovacího konstruktoru třídy Pokud třídy má konstruktor move definovaný uživatelem, ale žádné uživatelem definované kopírovacího konstruktoru. Dev14 je tento konstruktor implicitně generovaného kopie také označený "= odstranění".  

<!--From here to VS_Update1 added 04/21/2017-->

-   **hlavní deklarované jako extern "C" teď vyžaduje typ vrácené hodnoty.**  

Následující kód vytvoří teď C4430. 
```cpp
extern "C" __cdecl main(){} // C4430
```
Opravte chybu, přidejte návratový typ:
```cpp
extern "C" int __cdecl main(){} // OK
```

 -   **TypeName není povolen v inicializátoru člena**  

Následující kód vytvoří teď C2059:
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

-   **Třídy úložiště na explicitní specializace se ignoruje.** 

V následujícím kódu se ignoruje specifikátor třídy úložiště se statickými 
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

-   **Konstanta použít v static_assert uvnitř šablona třídy vždycky selže.**  

Následující kód způsobí, že static_assert vždy selhání:
```cpp
template <size_t some_value>
struct S1
{
    static_assert(false, "default not valid"); // always invoked

};

//other partial specializations here
```

Chcete-li tento problém obejít, tuto hodnotu zabalit do struktury:
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

-   **Pravidla pro dopředného deklarace vynucený. (Platí pouze pro c)**  

Následující kód vytvoří teď C2065:
```cpp
struct token_s;
typedef int BOOL;
typedef int INT;



typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
```

Chcete-li vyřešit problém přidejte správné dopředného deklarace:

```cpp
struct token_s;
typedef int BOOL;
typedef int INT;

// forward declarations:
typedef struct token_s TOKEN; 
typedef TOKEN *PTOKEN;

typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
```

-   **Více konzistentní vynucení typů ukazatele – funkce**  

Následující kód vytvoří teď C2197:

```cpp
typedef int(*F1)(int);
typedef int(*F2)(int, int);

void func(F1 f, int v1, int v2)
{
    f(v1, v2); // C2197
}
```

-   **Nejednoznačné volání přetížené funkce**  

Následující kód vytvoří teď C266: 'N::bind': nejednoznačné volání přetížené funkce
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

Postup řešení chyby, můžete plnému určení volání vazby: N::bind(...). Ale pokud tuto změnu je manifest prostřednictvím nedeklarovaný identifikátor (C2065), pak mohlo by být vhodné to opravu se deklaraci 'pomocí'.

Tento vzor se často stane s ComPtr a dalších typů v Microsoft::WRL – obor názvů.

-   **Opravte nesprávná adresa**  

Následující kód vytvoří teď C2440: '=': nelze převést ' typ * "na"typ". Opravit chyby, změnit & (typ) na (typ) a (& f()) k (f()).
 
```cpp
\\ C
typedef void (*type)(void);
 
void f(int i, type p);
void g(int);
void h(void)
{
    f(0, &(type)g);
}
 
\\ C++
typedef void(*type)(void);
 
type f();
 
void g(type);
 
void h()
{
    g(&f());
}

```

-   **Řetězcový literál se konstantní pole**  

Následující kód vytvoří teď C2664: ' void f (void *)': nelze převést argument 1 z ' const char (*) [2]' do ' void *.
```cpp
void f(void *);
 
void h(void)
{
    f(&__FUNCTION__); 
    void *p = &"";
}
```

Chcete-li chybu opravit, změňte typ parametru funkce "const void *", nebo změnit text h vypadat takto:

```cpp
void h(void)
{
    char name[] = __FUNCTION__;
    f( name); 
    void *p = &"";
}

```

-   **C ++ 11 UDL řetězce**  

Následující kód vytvoří nyní chyba C3688: Neplatný literálu příponu "L"; literál operátor nebo operátor literálu šablony "operátor" "L" nebyl nalezen


```cpp
#define MACRO

#define STRCAT(x, y) x\#\#y

int main(){

    auto *val1 = L"string"MACRO;
    auto *val2 = L"hello "L"world";

    std::cout << STRCAT(L"hi ", L"there");
}
```
Opravte chybu, změňte kód na toto:

```cpp
#define MACRO

// Remove ##. Strings are automatically
// concatenated so they are not needed
#define STRCAT(x, y) x y

int main(){
    //Add space after closing quote
    auto *val1 = L"string" MACRO;
    auto *val2 = L"hello " L"world";

    std::cout << STRCAT(L"hi ", L"there");
}

```
V příkladu nahoře `MACRO` je už analyzovat jako dvě tokeny (řetězec, který následuje makra).  Nyní je analyzovat jako jeden token UDL.  Totéž platí i pro L "" L"", který byl dříve analyzovat jako L"" a L "" a je nyní analyzovat jako L "" L a "".

Řetězec zřetězení pravidla přenesla také do stavu kompatibilního se standardem, což znamená, že je ekvivalentní L "ab" L "a" "b". Zřetězení řetězců s šířka různých znakových nebyl přijat předchozí vydání sady Visual Studio.


-   **C ++ 11 prázdný znak odebrat**  

Následující kód vytvoří nyní chyba C2137: Konstanta prázdný znak

```cpp
bool check(wchar_t c){
    return c == L''; //implicit null character
}
```

Opravte chybu, změňte kód na toto:

```cpp
bool check(wchar_t c){
    return c == L'\0';
}
```

-   **MFC – výjimky nemůže být zachycena hodnotou, protože nejsou kopírovatelná**  

Následující kód v aplikaci MFC způsobí, že chyba C2316: měl ': nemůže být zachycena destruktor nebo kopírovacího konstruktoru jsou nedostupné nebo odstraněné

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
Chcete-li opravit kód, můžete změnit blok catch, který má ' catch (const D &), ale lepší řešení, je obvykle použít MFC TRY/CATCH – makra.

-   **alignof je nyní klíčové slovo**  

Následující kód vytvoří nyní chyba C2332: 'class': chybí název značky. Opravit kód musíte přejmenovat třídu nebo, pokud třída provádí stejný pracovní jako alignof, právě nahraďte třída new – klíčové slovo.
```cpp
class alignof{}
```

-   **constexpr je nyní klíčové slovo**  

Následující kód vytvoří nyní chyba C2059: Chyba syntaxe: ')'. Pokud chcete vyřešit kód, je třeba přejmenovat všechny funkce nebo názvy proměnných, které se nazývají "constexpr". 
```cpp
int constexpr() {return 1;}
```

-   **Typy Movable nemohou být const**  

Když funkce vrátí typ, který slouží k přesunování, by neměl být její návratový typ const.

-   **Odstraněné kopírovací konstruktory**  

Následující kód vytvoří nyní na C2280:: S(S &&)': Při pokusu o odkazu na funkci odstraněné:

```cpp
struct S{
    S(int, int);
    S(const S&) = delete;
    S(S&&) = delete;
};

S s2 = S(2, 3); //C2280
```
Postup řešení chyby, použijte přímý inicializace pro S2:
```cpp
struct S{
    S(int, int);
    S(const S&) = delete;
    S(S&&) = delete;
};

S s2 = {2,3}; //OK
```

-   **Převod na ukazatel na funkci vygeneruje pouze tehdy, když žádné zachycení lambda**  

Následující kód vytvoří C2664 ve Visual Studiu 2015. 

```cpp
void func(int(*)(int)) {}

int main() {

    func([=](int val) { return val; });
}
```
Chcete-li chybu opravit, odeberte `=` ze seznamu zachycení.

-   **Nejednoznačné volání zahrnující operátory převodu**  

Následující kód vytvoří nyní chyba C2440: 'přetypování': nelze převést "S2" na "S1":

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
Opravte chybu, explicitně volejte operátor převodu:

```cpp
void f(S2 s2)
{
    //Explicitly call the conversion operator
    s2.operator S1();
    // Or
    S1((int)s2);
}

```

Následující kód vytvoří nyní chyba C2593: ' operátor =' je nejednoznačné:

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
Opravte chybu, explicitně volejte operátor převodu:
```cpp
void f(S1 *p, S2 s)
{
       *p = s.operator S1&();
}
```

-   **Odstraňte neplatný kopie inicializace dat nestatické členské inicializace (NSDMI)**  

Následující kód vytvoří nyní chyba C2664: 'S1::S1(S1 &&)': nelze převést argument 1, bool, na ' const S1 & ":
```cpp
struct S1 {
    explicit S1(bool);
};

struct S2 {
    S1 s2 = true; // error
};
```
Chcete-li opravit chyby, použijte přímé inicializace:
```cpp
struct S2 {
S1 s1{true}; // OK
};
```

-   **Přístup k konstruktory uvnitř decltype – příkazy**  

Následující kód vytvoří teď C2248: 'S::S': nelze přístup privátního člena deklarovaná ve třídě na ':
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
Postup řešení chyby, přidejte deklaraci friend pro S2 v S:
```cpp
class S {
    S();
    friend class S2; // Make S2 a friend
public:
    int i;
};
```

-   **Implicitně odstranění výchozího konstruktoru z lambda**  

Následující kód vytvoří nyní chyba C3497: Nelze vytvořit instanci lambda:
```cpp
void func(){
    auto lambda = [](){};    
 
    decltype(lambda) other;
}
```
Postup řešení chyby, odeberte nutnost výchozí konstruktor, který má být volána. Pokud argument lambda nezachytává nic pak ho lze převést na ukazatel na funkci.

-   **Lambdas pomocí operátoru odstraněné přiřazení**  

Následující kód vytvoří nyní chyba C2280:

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
Opravte chybu, nahraďte třídu functor argument lambda nebo odebrat nutnost používat operátor přiřazení.

-   **Probíhá pokus o přesunutí objektu s odstraněné kopírovací konstruktor**  

Následující kód vytvoří nyní chyba C2280: 'lze přesunout:: moveable(const moveable &)': Při pokusu o odkazu na funkci odstraněné
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
Chcete-li opravit chyby, použijte místo toho std::move:
```cpp
S(moveable && m) :
    m_m(std::move(m))
```
-   **Místní třídy nemůže odkazovat na jiné místní třídy definované později ve stejné funkci**  

Následující kód vytvoří nyní chyba C2079: na se používá nedefinovaný struktura main::S2
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
Postup řešení chyby, přesunete nahoru definici S2:
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

-   **Nelze volat chráněné základní konstruktoru v těle odvozené konstruktoru.**  

Následující kód vytvoří nyní chyba C2248: 'S1::S1': Nelze získat přístup k chráněného člena deklarovaná ve třídě "S1"
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
Postup řešení chyby, v S2 odeberte volání S1() z konstruktoru a v případě potřeby ji umístit do jiné funkce.

-   **{} zabraňuje převod na ukazatele**  

Následující kód vytvoří teď C2439 'S::p': člen nebylo možné inicializovat.   
```cpp
struct S {
    S() : p({ 0 }) {}
    void *p;
};
```
Postup řešení chyby, odeberte složené závorky z kolem 0, jinak použijte `nullptr` místo toho, jak je uvedeno v následujícím příkladu:
```cpp
struct S {
    S() : p(nullptr) {}
    void *p;
};
```

-   **Nesprávný makro definice a používání v závorkách**  

Následující příklad vytvoří nyní chyba C2008: ';': neočekávané definice makra
```cpp
#define A; //cause of error

struct S {
    A(); // error
};
```
Chcete-li opravit problém změňte horní řádek pro `#define A();`

Následující kód vytvoří chyba C2059: Chyba syntaxe: ').
```cpp

//notice the space after 'A'
#define A () ;

struct S {
    A();
};
```
Opravit mezery mezi odebrat kód A a ().

Následující kód vytvoří chyba C2091: funkce vrátí funkce:

```cpp

#define DECLARE void f()

struct S {
    DECLARE();
};
```
Chcete-li opravte chybu, odeberte závorkách po DECLARE v S: `DECLARE;`.

Následující kód vytvoří chyba C2062: typ 'int neočekávané

```cpp
#define A (int)

struct S {
    A a;
};
```
Chcete-li problém vyřešit, definujte A takto:
```cpp
#define A int
```

-   **Velmi parens v deklaracích**  

Následující kód vytvoří chyba C2062: typ 'int neočekávané
```cpp

struct S {
    int i;
    (int)j;
};
```
Chcete-li chybu opravit, odeberte parens z `j`. Pokud parens jsou potřebné pro přehlednost, potom použijte definici typu.

-   **Generované kompilátorem konstruktory a __declspec(novtable)**  

V sadě Visual Studio 2015 je vyšší pravděpodobnost, že vložené generované kompilátorem konstruktory abstraktní třídy s základní virtuální třídy mohou vystavit nesprávné použití __declspec(novtable), když se používá v kombinaci s deklarace __declspec(dllimport).

-   **Auto vyžaduje jeden výraz v přímo. seznam inicializace** následující kód vytvoří nyní chyba C3518: 'testPositions': v kontextu přímo. seznam inicializace můžete typ 'auto' pouze odvodit z jedné inicializátoru výrazu

```cpp
auto testPositions{
    std::tuple<int, int>{13, 33},
    std::tuple<int, int>{-23, -48},
    std::tuple<int, int>{38, -12},
    std::tuple<int, int>{-21, 17}
};
```
Postup řešení chyby, je jednou z možností k chybě při inicializaci testPositions následujícím způsobem:

```cpp
std::tuple<int, int> testPositions[]{
    std::tuple<int, int>{13, 33},
    std::tuple<int, int>{-23, -48},
    std::tuple<int, int>{38, -12},
    std::tuple<int, int>{-21, 17}
};
```

-   **Kontrola typy oproti ukazatele na typy pro is_convertible**  

Následující kód nyní způsobí, že statické assertion selhání. 

```cpp
struct B1 {
private:
    B1(const B1 &);
};
struct B2 : public B1 {};
struct D : public B2 {};

static_assert(std::is_convertible<D, B2>::value, "fail");
```
Postup řešení chyby, změňte static_assert tak, aby porovná ukazatele D a B2:

```cpp
static_assert(std::is_convertible<D*, B2*>::value, "fail");
```

-   **musí být konzistentní declspec(novtable) deklarace**  

deklarace declspec musí být konzistentní v rámci všech knihoven. Následující kód vytvoří nyní narušení jedna definice pravidla (ODR):

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


  
###  <a name="VS_Update1"></a> Shoda vylepšení v aktualizaci 1  
  
-   **Privátní virtuální základní třídy a nepřímé dědění**  
  
     Předchozí verze kompilátoru povolené odvozené třídy za účelem zavolejte členské funkce jeho *nepřímo odvozené* `private virtual` základní třídy. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor už akceptuje kód napsaný v tímto způsobem a v důsledku vydá Chyba kompilátoru C2280.  
  
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
  
     - nebo -  
  
    ```cpp  
    class base;  // as above  
  
    class middle : private virtual base {};  
    class top : public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
  
    ```  
  
-   **Přetížené new – operátor a delete – operátor**  
  
     Předchozí verze kompilátoru povolené třetí `operator new` a třetí `operator delete` deklarovat statickou a deklarovat v oborech názvů než globální obor názvů.  Toto chování původního vytvoření riziko, že tento program nebude volání `new` nebo `delete` operátor implementace, která programátorů určený, což vede k bezobslužné chybný modul runtime chování. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2323 místo.  
  
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
  
     Kromě toho i když kompilátor nedává konkrétní Diagnostika, vložené new – operátor považuje za nedůvěryhodný.  
  
-   **Volání metody ' operátor *typu*() ' (uživatelem definovaný převod) na typy jiné třídy**  
  
     Předchozí verze kompilátoru povolené ' operátor *typu*(), k volání na typy jiné třídy při tiché ignoruje se. Toto chování staré vytvořit riziko generování tichou chybného kódu, což vede k nepředvídatelným modul runtime chování. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2228 místo.  
  
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
  
-   **Redundantní typename použity ve specifikátorech typu propracována**  
  
     Předchozí verze kompilátoru povolené `typename` použity ve specifikátorech propracována typu; je sémanticky nesprávný kód napsaný v tímto způsobem. Kompilátor už akceptuje kód napsaný v tímto způsobem a vydá Chyba kompilátoru C3406 místo.  
  
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
  
-   **Odvození typu pole ze seznamu inicializátoru**  
  
     Předchozí verze kompilátoru nepodporuje odvození typu polí z inicializátoru seznamu. Kompilátor teď podporuje tato forma odvození typu a, v důsledku toho volání funkce šablon pomocí inicializační seznamy teď může být nejednoznačný nebo jiné přetížení může být zvolena než v předchozích verzích kompilátoru. Chcete-li tyto problémy vyřešit, program musí nyní explicitně zadáte přetížení, které programátorů určený.  
  
     Když toto nové chování způsobí, že rozlišení přetížení vzít v úvahu další candidate, který je vhodný stejně jako na historické candidate, stane se nejednoznačné volání a kompilátor problémy v důsledku chyby kompilátoru C2668.  
  
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
  
     Když toto nové chování způsobí rozlišení přetížení vzít v úvahu další candidate, který je lepší shodu než historické candidate volání jednoznačně přeloží na nové Candidate způsobí změnu v chování programu, který je pravděpodobně jiná než programátory určena.  
  
     Příklad 2: změňte rozlišení přetížení (před)  
  
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
  
     Příklad 2: změňte rozlišení přetížení (po)  
  
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
  
-   **Obnovení přepínač příkaz upozornění**  
  
     Předchozí verze kompilátoru odebrána dříve existující upozornění související s `switch` příkazy; tato upozornění byly obnoveny. Kompilátor teď vystavuje obnovené upozornění a upozornění souvisejících s konkrétní případy (včetně výchozí případ) jsou nyní vystavené na řádek obsahující problematické případu, ne na poslední řádek příkaz switch. Výsledkem je nyní vydávajícího upozornění na různé řádky než v minulosti, upozornění dříve potlačit pomocí `#pragma warning(disable:####)` může potlačit už tak, jak má. K potlačení tato upozornění tak, jak má, může být potřeba přesunout `#pragma warning(disable:####)` direktivy na řádek nad prvním případě potenciálně poškozený. Níže jsou uvedeny obnovené upozornění.  
  
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
  
     Příklady obnovené upozornění jsou uvedeny v jejich dokumentaci.  
  
-   **#include: použití nadřazený adresář specifikátor '..' v názvu cesty** (ovlivňuje pouze /Wall wdn)  
  
     Předchozí verze kompilátoru se nepodařilo rozpoznat použití nadřazený adresář specifikátor '..' v názvu cesty z `#include` direktivy. Kód napsaný v tímto způsobem se má obvykle patří hlavičky, které existují mimo projekt nesprávně pomocí projektu relativní cesty. Toto chování staré vytvořit riziko, že program může být zkompilovány zahrnutím soubor jiný zdroj než programátorů určený nebo že tyto relativní cesty nebude přenosné do dalších prostředí sestavení. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C4464, pokud je povoleno.  
  
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
  
     Kromě toho, přestože kompilátor není poskytnuta konkrétní Diagnostika, také doporučujeme specifikátor nadřazený adresář "..." má poznámka použít k určení adresáře souborů k zahrnutí vašeho projektu.  
  
-   **#pragma optimize() přesahuje za konec souboru záhlaví** (ovlivňuje pouze /Wall wdn)  
  
     Předchozí verze kompilátoru se nepodařilo rozpoznat změny nastavení příznaku optimalizace, které řídicí soubor hlaviček, který je zahrnutý v rámci překladu jednotky. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C4426 v umístění je problematický `#include`, pokud je povoleno. Pokud změny konflikt s příznaky optimalizace nastavuje argumentů příkazového řádku pro kompilátor se pouze objeví toto upozornění.  
  
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
  
-   **Neshoda #pragma warning(push)** a **#pragma warning(pop)** (ovlivňuje pouze /Wall wdn)  
  
     Předchozí verze kompilátoru se nepodařilo rozpoznat `#pragma warning(push)` stav se změní se spárovaný s `#pragma warning(pop)` stavu změny v souboru jiný zdroj, který je určený jen zřídka. Toto chování staré vytvoří riziko, který program by kompilovat s jinou sadu upozornění povoleno než programátorů určený, což může způsobit tichou chybný modul runtime chování. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C5031 v umístění odpovídajících `#pragma warning(pop)`, pokud je povoleno. Toto upozornění zahrnuje Poznámka odkazující na umístění odpovídající warning(push) #pragma.  
  
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
  
     Když neobvyklé, je někdy úmyslné kód napsaný v tímto způsobem. Kód napsaný v tímto způsobem je citlivé na změny v `#include` pořadí; Pokud je to možné, doporučujeme, že soubory zdrojového kódu spravovat stav varování nezávislý způsobem.  
  
-   **Neodpovídající #pragma warning(push)** (ovlivňuje pouze /Wall wdn)  
  
     Předchozí verze kompilátoru se nepodařilo rozpoznat neodpovídající `#pragma warning(push)` změny na konci jednotce překlad stavu. Kompilátor nyní zjistí a upozorní programátorů kód napsaný v tímto způsobem a problémy volitelné kompilátoru upozornění C5032 v umístění neodpovídající #pragma warning(push), pokud je povoleno. Pokud nejsou žádné chyby kompilace v jednotce překlad se pouze objeví toto upozornění.  
  
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
  
-   **Další upozornění může být vydaný v důsledku vylepšené #pragma upozornění stavu sledování**  
  
     Předchozí verze kompilátoru sledovat #pragma upozornění změny stavu nedostatečně i na problém, že vše určená upozornění. Toto chování vytvořit riziko určitá upozornění by efektivně potlačit v situacích, které se liší od programátorů určena. Kompilátor nyní sleduje stav varování #pragma více robustní – zejména související s #pragma upozornění změny stavu v rámci šablony – a volitelně vydá nové upozornění C5031 a C5032, které pomohou najít nezamýšleným používá programátorů`#pragma warning(push)` a `#pragma warning(pop)`.  
  
     V důsledku vylepšené #pragma může být nyní objeví upozornění sledování, upozornění dříve nesprávně Potlačené a upozornění souvisejících s problémy dříve misdiagnosed změny stavu.  
  
-   **Lepší identifikaci nedostupný kódu**  
  
     Standardní knihovna C++ změny a vylepšená možnost volání vnořené funkce porovnání s předchozími verzemi kompilátoru, mohou povolovat kompilátoru k prokázání, určitý kód je nyní nedostupný. Toto nové chování může mít za následek nové a další často vydané instancí upozornění C4720.  
  
    ```Output  
    warning C4720: unreachable code  
    ```  
  
     V mnoha případech toto upozornění se objevit pouze při kompilaci s povolenými optimalizacemi, od optimalizace může vložené více volání funkce, odstranit redundantní kódu nebo v opačném případě zkontrolujte možné určit, že určité kód nedosažitelný. Jsme zaznamenali, že se nové instance třídy upozornění C4720 došlo často v try/catch – bloky, zejména ve vztahu k použití [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).  
  
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
  
###  <a name="VS_Update2"></a> Shoda vylepšení v aktualizaci 2  
  
-   **Další upozornění a chyby může být vydaný v důsledku částečné podporu pro výraz sfinae u výrazů**  
  
     Předchozí verze kompilátoru analyzovat určité druhy výrazů uvnitř `decltype` specifikátory z důvodu nedostatku podpory pro výraz sfinae u výrazů. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor teď analyzuje tyto výrazy a částečné podporu pro výraz sfinae u výrazů z důvodu vylepšení probíhající shoda. V důsledku toho nyní vydá upozornění a chyby nalezené ve výrazech, že předchozí verze kompilátoru není analyzovat.  
  
     Když toto nové chování analyzuje `decltype` výraz, který zahrnuje typ, který nebyl ještě deklarován, kompilátor problémy v důsledku chyby kompilátoru C2039.  
  
    ```Output  
  
    error C2039: 'type': is not a member of '`global namespace''  
    ```  
  
     Příklad 1: použití nedeklarované typu (před)  
  
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
  
     Když toto nové chování analyzuje `decltype` výraz, který chybí nezbytné použití `typename` – klíčové slovo k určení, zda je závislé název typu, kompilátor vydá upozornění C4346 společně s chyba kompilátoru C2923 kompilátoru.  
  
    ```Output  
  
    warning C4346: 'S2<T>::Type': dependent name is not a type  
  
    ```  
  
    ```Output  
  
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'  
    ```  
  
     Příklad 2: závislé název není typu (před)  
  
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
  
-   `volatile` **Členské proměnné zabránit implicitně definované konstruktory a operátory přiřazení**  
  
     Předchozí verze kompilátoru povolené třídy, která má `volatile` členské proměnné tak, aby měl výchozí kopírování nebo přesunutí konstruktory a operátory přiřazení pro kopírování nebo přesunutí automaticky generovány výchozí. Toto chování staré nebyla správná a neodpovídá C++ standard. Kompilátor nyní brány v úvahu třídy, která má volatile členské proměnné tak, aby měl netriviální vytváření a operátory přiřazení, která brání automaticky generován výchozí implementace těchto operátorů.  Když tyto třídy je členem sjednocení (nebo anonymní sjednocení uvnitř třídu), zkopírovat nebo přesunout konstruktory a operátory přiřazení pro kopírování nebo přesunutí sjednocení (nebo třída obsahující sjednocení unonymous) budou implicitně definovány odstranit. Probíhá pokus o vytvoření nebo zkopírujte sjednocení (nebo třída obsahující anonymní sjednocení) bez nutnosti explicitně definovat je je chybu a Chyba kompilátoru problémy kompilátoru C2280 v důsledku.  
  
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
  
-   **Statické členské funkce nepodporují kvalifikátory odchylka nákladů.**  
  
     Předchozí verze sady Visual Studio 2015 povoleno statické členské funkce tak, aby měl kvalifikátory odchylka nákladů. Toto chování je z důvodu regrese v sadě Visual Studio 2015 a Visual Studio 2015 Update 1; Visual Studio 2013 a předchozích verzích kompilátor odmítnout kód napsaný v tímto způsobem. Chování sady Visual Studio 2015 a Visual Studio 2015 Update 1 není správná a neodpovídá standardní C++.  Visual Studio 2015 Update 2 odmítne kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2511 místo.  
  
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
  
-   **Předat dál deklarace výčtu není povolen v kódu WinRT** (/ZW ovlivňuje pouze)  
  
     Kód zkompilovat pro prostředí Windows Runtime (WinRT) neumožňuje `enum` typy dál deklarovat, podobně jako při kompilaci spravovaného kódu C++ pro rozhraní .net Framework pomocí kompilátoru/clr přepínače. Toto chování se zajistí, že velikost výčet je vždy známé a může být správně promítá do systému typu WinRT. Kompilátor odmítne kód napsaný v tímto způsobem a vydá Chyba kompilátoru C2599 společně s chyba kompilátoru C3197.  
  
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
  
-   **Přetížené třetí new – operátor a delete – operátor nemusí být deklarován vložené** (úroveň 1 (/ W1) na výchozím)  
  
     Předchozí verze kompilátoru není upozorní, když new – operátor třetí a operátor delete funkce jsou deklarovány vložené. Kód napsaný v tímto způsobem je nesprávně naformátován (nejsou potřeba žádné diagnostiky) a může způsobit paměti problémy vyplývající z nové Neshoda a odstranit operátory (zejména při použití společně s velikostí navrácení), které může být obtížné diagnostikovat.   Kompilátor nyní vydává kompilátoru upozornění C4595 k identifikaci kódu napsaného tímto způsobem.  
  
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
  
     Opravě kód, který je zapsaný tímto způsobem může vyžadovat, aby definice operátor přesunout mimo soubor hlaviček a do odpovídající zdrojový soubor.  
  
###  <a name="VS_Update3"></a> Shoda vylepšení v aktualizaci 3  
  
-   **std::is_convertable nyní rozpozná vlastní přiřazení** (standardní knihovna)  
  
     Předchozí verze `std::is_convertable` typ znak se nepodařilo rozpoznat správně vlastní přiřazení typu třídy, když se odstraní. jeho kopie konstruktoru nebo privátní. Nyní `std::is_convertable<>::value` je správně nastavena na `false` při použití typu třídy s odstraněný nebo soukromý kopírovacího konstruktoru.  
  
     Neexistuje žádné diagnostické kompilátoru přidružené k této změně.  
  
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
  
     V předchozích verzích kompilátor statické kontrolní výrazy v dolní části v tomto příkladu předat protože `std::is_convertable<>::value` nebyl správně nastaven `true`. Nyní `std::is_convertable<>::value` je správně nastavena na `false`, způsobuje statické kontrolní výrazy k selhání.  
  
-   **Uvedena odstranění trivial kopírování nebo přesunutí specifikátory přístupu ohledem konstruktory**  
  
     Předchozí verze kompilátoru není zkontrolujte specifikátor přístupu uvedena nebo odstraněné trivial kopie a přesunout konstruktory před povolením, která se má volat. Toto chování staré nebyla správná a neodpovídá C++ standard. V některých případech toto chování staré vytvořit riziko generování tichou chybného kódu, což vede k nepředvídatelným modul runtime chování. Kompilátor nyní zkontroluje přístup specifikátor uvedena nebo odstraněné trivial kopie a přesunout konstruktory k určení, zda může být volána a pokud ne, kompilátoru problémy v důsledku upozornění C2248.  
  
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
  
-   **S atributy podpory kódu ATL** (úroveň 1 (/ W1) na výchozím)  
  
     Kódu ATL s atributy předchozích verzích kompilátoru podporována. Jako další fáze odebrání podporu pro knihovny ATL s atributy kód, který [začal v sadě Visual Studio 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), s atributy ATL kód je zastaralá. Kompilátor nyní vydává kompilátoru upozornění C4467 k identifikaci tento druh nepoužívané kódu.  
  
    ```Output  
    warning C4467: Usage of ATL attributes is deprecated  
    ```  
  
     Pokud chcete pokračovat, dokud odebrala se podpora z kompilátoru použití kódu ATL s atributy, můžete toto upozornění zakázat předáním `/Wv:18` nebo `/wd:4467` argumenty příkazového řádku pro kompilátor nebo přidáním `#pragma warning(disable:4467)` ve zdrojovém kódu.  
  
     Příklad 1 (před)  
  
    ```cpp  
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]  
    class A {};  
  
    ```  
  
     Příklad 1 (po)  
  
    ```cpp  
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};  
  
    ```  
  
     Někdy může být nutné nebo chcete vytvořit IDL soubor nepoužívejte zastaralý ATL atributy, jako následující příklad kódu  
  
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
  
     Nejprve vytvořte soubor *.idl; soubor vc140.idl generované slouží k získání \*.idl souboru, který obsahuje rozhraní a poznámky.  
  
     Dále přidáte krok MIDL buildu a ujistěte se, že jsou generovány definice rozhraní C++.  
  
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
  
     Potom pomocí knihovny ATL přímo v souboru implementace, jako v příkladu kódu níže.  
  
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
  
-   **Předkompilované soubory hlaviček (PCH) a neshoda # direktivy include** (ovlivňuje pouze /Wall wdn)  
  
     Neshoda akceptovat předchozí verze kompilátoru `#include` direktivy ve zdrojových souborech mezi `-Yc` a `-Yu` kompilace při použití předkompilovaných hlaviček (PCH) souborů. Kód napsaný v tímto způsobem je už přijat kompilátoru.   Kompilátor teď problémy kompilátoru upozornění CC4598 k identifikaci neshoda `#include` direktivy při použití souborů PCH.  
  
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
  
-   **Předkompilované soubory hlaviček (PCH) a neshoda adresáře souborů k zahrnutí** (ovlivňuje pouze /Wall wdn)  
  
     Předchozí verze kompilátoru přijata neshoda adresář include (`-I`) argumenty příkazového řádku pro kompilátor mezi `-Yc` a `-Yu` kompilace při použití předkompilovaných hlaviček (PCH) souborů. Kód napsaný v tímto způsobem je už přijat kompilátoru.   Kompilátor teď problémy kompilátoru upozornění CC4599 k identifikaci neshoda adresář include (`-I`) argumenty příkazového řádku při použití souborů PCH.  
  
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
  
## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 shoda změny  
  
### <a name="compiler"></a>Kompilátoru  
  
-   Konečné – klíčové slovo nyní vygeneruje chybu nerozpoznané symbol, kde ho by sestavili dříve:  
  
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
  
     V dřívějších verzích nebyla chyba vyvolána, protože volání bylo virtuální volání; program by však spadl za běhu. Nyní je přiřazena chyba linkeru, protože třída je nyní označena jako konečná. V tomto příkladu postup řešení chyby, by propojení proti obj, který obsahuje definici S2::f.  
  
-   Při použití funkcí friend v oborech názvů, je potřeba znovu funkce friend deklarovat dřív, než je na něj odkazovat nebo bude dojde k chybě, protože kompilátor teď vyhovuje standardní C++ ISO. Toto se například již nezkompiluje:  
  
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
  
     Chcete-li tento kód opravit, deklarujte funkci přítele:  
  
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
  
-   Standardní C++ neumožňuje explicitní specializace v třídě. I když Microsoft Visual C++ compiler umožňuje v některých případech se v případech, například následujícím příkladu je nyní generována chyba, protože kompilátor nepovažuje funkce second být specializace první z nich.  
  
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
  
-   Už se pokusí odstranit nejednoznačnost dvě funkce v následujícím příkladu a nyní vysílá chybu:  
  
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
  
-   Před provedením kompilátor kompatibilní s ISO C ++ 11, následující kód zkompilovat a způsobila x přeložit na typ int:  
  
    ```cpp  
    auto x = {0};  
    int y = x;  
  
    ```  
  
     Tento kód se teď odstraňuje x typu std::initializer_list\<int > a výsledkem bude chyba na další řádek, který se pokouší přiřadit x na typ int. (Neexistuje žádný převod ve výchozím nastavení.) Chcete-li tento kód, použijte k nahrazení automaticky int:  
  
    ```cpp  
    int x = {0};  
    int y = x;  
  
    ```  
  
-   Inicializace agregace je již povolené, když typ pravém hodnota neodpovídá typu levé hodnotu, která probíhá inicializace a chyba se objeví, protože ISO C ++ 11 Standard vyžaduje jednotná inicializace pracovat bez Zužující převody. Dříve, pokud zužující převod byla k dispozici, [upozornění kompilátoru (úroveň 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) upozornění by byly vydané místo k chybě.  
  
    ```cpp  
    int i = 0;  
    char c = {i}; // error  
  
    ```  
  
     Chcete-li tento kód opravit, přidejte explicitní zužující převod:  
  
    ```cpp  
    int i = 0;  
    char c = {static_cast<char>(i)};  
  
    ```  
  
-   Už je povolená následující inicializace:  
  
    ```cpp  
    void *p = {{0}};  
  
    ```  
  
     Chcete-li tento kód opravit, použijte některou z těchto forem:  
  
    ```cpp  
    void *p = 0;  
    // or  
    void *p = {0};  
  
    ```  
  
-   Vyhledávání názvu se změnila. Následující kód je jinak přeložit v kompilátoru C++ v sadě Visual Studio 2012 a Visual Studio 2013:  
  
    ```cpp  
    enum class E1 { a };  
    enum class E2 { b };  
  
    int main()  
    {  
        typedef E2 E1;  
        E1::b;  
    }  
  
    ```  
  
     V sadě Visual Studio 2012 E1 ve výrazu E1::b přeložit na:: E1 v globálním oboru. V sadě Visual Studio 2013, E1 ve výrazu E1::b přeloží na typedef E2 definice v main() a má typ:: E2.  
  
-   Rozložení objektů se změnilo. Na platformě x 64 se může v porovnání z předchozími verzemi změnit rozložení objektů třídy. Pokud má virtuální funkci, ale neobsahuje základní třídu, která obsahuje virtuální funkci, objektový model kompilátoru vloží ukazatel na tabulku virtuálních funkcí za rozložení datových členů. To znamená, že rozložení nemusí být ve všech případech optimální. V předchozích verzích představuje optimalizaci pro x64 se pokusit o zlepšení rozložení pro vás, ale protože se nepodařilo správně fungovat v situacích, složitý kód, byla odebrána v sadě Visual Studio 2013. Podívejte se například na tento kód:  
  
    ```cpp  
    __declspec(align(16)) struct S1 {  
    };  
  
    struct S2 {  
        virtual ~S2();  
        void *p;  
        S1 s;  
    };  
  
    ```  
  
-   V sadě Visual Studio 2013 výsledkem sizeof(S2) na x64 je 48, ale v předchozích verzích vyhodnotí 32 znaků. Chcete-li to vyhodnocení na 32 v kompilátoru C++ v sadě Visual Studio 2013 pro x64, přidejte fiktivní základní třídy, která má virtuální funkce:  
  
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
  
     Hledání míst ve vašem kódu, který dřívější verze by jste se pokusili optimalizace, použijte kompilátoru z této verze společně s možností kompilátoru /W3 a zapnout 4370 upozornění. Příklad:  
  
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
  
     Před Visual Studio 2013, tento kód výstupy tuto zprávu: "upozornění C4370:"S2": rozložení třídy se změnil z předchozí verze kompilátoru kvůli lepší okolních".  
  
     X86 kompilátoru má stejný problém optimální rozložení ve všech verzích kompilátoru. Pokud je například tento kód je zkompilován pro platformu x86:  
  
    ```cpp  
    struct S {  
        virtual ~S();  
        int i;  
        double d;  
    };  
  
    ```  
  
     Výsledek sizeof (S) je 24. Může však být snížena na hodnotu 16, pokud použijete zástupné řešení uvedené výše pro platformu x64:  
  
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
 Kompilátor C++ v sadě Visual Studio 2013 zjišťuje neshody v _ITERATOR_DEBUG_LEVEL, které je implementované v sadě Visual Studio 2010, a RuntimeLibrary neshody. Tyto dojít, když kompilátoru možnosti/MT (statické vydání), jsou kombinované /MTd (statické ladění), /MD (dynamické verzi) a /MDd (dynamické debug).  
  
-   Pokud váš kód uznává na předchozí vydání simulované alias šablony, musíte ho změnit. Například místo allocator_traits\<A >:: rebind_alloc\<U >:: dalších, nyní je třeba k vyslovení allocator_traits\<A >:: rebind_alloc\<U >. I když ratio_add\<R1, R2 >:: typ již nejsou potřebné, a doporučujeme nyní sdělení ratio_add\<R1, R2 >, první bude stále kompilovat, protože poměr\<N, D > je potřeba mít typedef "type" pro snížené poměr, který bude stejného typu, pokud už je nižší.  
  
-   Je nutné použít #include \<algoritmus > při volání std::min() nebo std::max().  
  
-   Pokud vaše stávající kód používá na předchozí vydání je simulované obor výčty – tradiční bez ohledu na obor výčty zabalené v oborech názvů – je nutné ho změnit. Například pokud uvedené std::future_status::future_status typu, nyní máte k vyslovení std::future_status. Většinu kódu je ale neovlivní – například stále zkompiluje std::future_status::ready.  
  
-   explicitní operátor bool() je přísnější než unspecified-bool-type() operátor. explicitní operátor bool() umožňuje explicitní převody na bool – například uděleno shared_ptr\<X > sp, oba static_cast\<bool > (sp) a jsou platné bool b(sp) – a Boolean-možností intenzivního testování "kontextové převody" na bool – například Pokud (sp),! sp, sp & & aktivují. Ale explicitní operátor bool() zakazuje implicitní převody na bool, takže nemůže sdělení bool b = sp; a vzhledem bool návratový typ, nelze říkají návratový sp.  
  
-   Teď, když jsou implementované skutečné variadické šablony, _VARIADIC_MAX a související makra nemají žádný vliv. Pokud stále definujete _VARIADIC_MAX, je to prostě ignorováno. Je-li potvrzen náš nástroj maker určený k podpoře simulovaných variadic šablon jiným způsobem, je nutné změnit váš kód.  
  
-   Kromě obyčejnou klíčová slova hlavičky standardní knihovna C++ nyní nezakazuje makro izing kontextově závislá klíčová slova "přepsání" a "poslední".  
  
-   reference_wrapper/REF()/cref() nyní nezakazuje vazbu na dočasné objekty.  
  
-   \<náhodné > teď přísně používá předběžné podmínky jeho kompilace.  
  
-   Různé standardní knihovna C++ typové vlastnosti mít předpoklad "T musí být úplný typ". Ačkoli je kompilátor nyní vynucuje přísněji, nemusí je vynutit ve všech situacích. (Protože standardní knihovna C++ předběžnou porušení aktivovat nedefinované chování, standardní nezaručuje vynucení.)  
  
-   Standardní knihovna C++ nepodporuje /clr:oldSyntax.  
  
-   C ++ 11 specifikace pro common_type <> měl neočekávané a nežádoucí důsledky; konkrétně umožňuje common_type\<int, int >:: typ návratové int & &. Proto kompilátor implementuje navrhované řešení pro knihovny pracovní skupina problém 2141, takže je common_type\<int, int = "" >:: Zadejte návratové int.  
  
     Jako vedlejším účinkem této změny, případě identity již nefunguje (common_type\<T > vždy nevede typu t.). To odpovídá navrženému řešení, ale dojde k porušení jakéhokoli kódu, který spoléhal na předchozí chování.  
  
     Pokud budete potřebovat znak typ identity, nepoužívejte nestandardní std::identity, která je definována v < type_traits >, protože nebude fungovat pro \<void >. Místo toho implementujte vlastní typovou vlastnost identity tak, aby vyhovovala vašim potřebám. Tady je příklad:  
  
    ```cpp  
    template < typename T> struct Identity {  
        typedef T type;  
    };  
  
    ```  
  
### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL  
  
-  **Visual Studio 2013 pouze**: knihovny MFC MBCS není zahrnutý v sadě Visual Studio, protože je tak známý kódování Unicode a použití MBCS se výrazně snižuje. Tato změna také udržuje MFC lépe zarovnané s Windows SDK, protože mnoho ovládacích prvků a zpráv má pouze kódování Unicode. Ale pokud budete musí pokračovat na používání knihovny MFC MBCS, můžete ji stáhnout z webu Stažení softwaru MSDN v [knihovny MFC vícebajtových pro Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770). Distribuovatelný balíček Visual C++ stále zahrnuje i tuto knihovnu.  (Poznámka: MBCS DLL je součástí instalace součásti C++ v sadě Visual Studio 2015 a novější).
  
-   Usnadnění pro pásu karet MFC se změní.  Místo jednu úroveň architekturu není nyní hierarchickou architekturu. Můžete dál používat staré chování pomocí volání CRibbonBar::EnableSingleLevelAccessibilityMode().  
  
-   Metoda CDatabase::GetConnect se odebere. Pokud chcete zvýšit zabezpečení, jsou teď uložená připojovací řetězec zašifrována a dešifrována pouze v případě potřeby; nemůže být vrácen jako prostý text.  Řetězec lze získat pomocí metody CDatabase::Dump.  
  
-   Podpis CWnd::OnPowerBroadcast se změnil. Podpis tohoto popisovače zprávy se změní na LPARAM jako druhý parametr.  
  
-   Podpisy jsou změnit zohlednit obslužné rutiny zpráv. Seznamy parametrů u následujících funkcí se změnily a používají nově přidané popisovače zpráv ON_WM_ *:  
  
    -   CWnd::OnDisplayChange změnit tak, aby (UINT, int, int) namísto (WPARAM LPARAM) tak, aby nové makro ON_WM_DISPLAYCHANGE mohou být používány mapy zpráv.  
  
    -   CFrameWnd::OnDDEInitiate změnit tak, aby (CWnd *, UINT, jednotka) namísto (WPARAM LPARAM) tak, aby nové makro ON_WM_DDE_INITIATE mohou být používány mapy zpráv.  
  
    -   CFrameWnd::OnDDEExecute změnit tak, aby (CWnd *, POPISOVAČ) namísto (WPARAM LPARAM) tak, aby nové makro ON_WM_DDE_EXECUTE mohou být používány mapy zpráv.  
  
    -   CFrameWnd::OnDDETerminate změnit tak, aby (CWnd *) jako parametr místo (WPARAM LPARAM) tak, aby nové makro ON_WM_DDE_TERMINATE mohou být používány mapy zpráv.  
  
    -   CMFCMaskedEdit::OnCut změnit tak, aby žádné parametry místo (WPARAM LPARAM), tak, aby nové makro ON_WM_CUT mohou být používány mapy zpráv.  
  
    -   CMFCMaskedEdit::OnClear změnit tak, aby žádné parametry místo (WPARAM LPARAM), tak, aby nové makro ON_WM_CLEAR mohou být používány mapy zpráv.  
  
    -   CMFCMaskedEdit::OnPaste změnit tak, aby žádné parametry místo (WPARAM LPARAM), tak, aby nové makro ON_WM_PASTE mohou být používány mapy zpráv.  
  
-   \#ifdefs v souborech MFC záhlaví budou odebrány. Řada #ifdefs v hlavičce MFC soubory týkající se Nepodporovaná verze systému Windows (WINVER &lt; 0x0501) jsou odebrány.  
  
-   DLL knihovny ATL (atl120.dll) se odebere. Knihovna ATL je nyní poskytována jako záhlaví a statická knihovna (atls.lib).  
  
-   Atlsd.lib, atlsn.lib a atlsnd.lib se odeberou. Knihovna Atls.lib již nemá závislosti na znakové sadě ani kód specifický pro ladění/vydání. Protože princip funkce je stejný pro Unicode/ANSI i ladění/vydání, je vyžadována pouze jedna verze knihovny.  
  
-   Nástroj trasování ATL a MFC se odebere společně s knihovnou DLL knihovny ATL a je jednodušší mechanismus trasování. Konstruktor CTraceCategory nyní přijímá jeden parametr (název kategorie) a makra trasování volání ladění CRT funkce vytváření sestav.  
  
## <a name="visual-c-2012-breaking-changes"></a>Visual C++ 2012 nejnovější změny  
  
### <a name="compiler"></a>Kompilátoru  
  
-   Došlo ke změně /Yl – možnost kompilátoru. Ve výchozím nastavení používá kompilátor tuto možnost, což může vést k chybám LNK2011 za určitých podmínek. Další informace najdete v tématu [/Yl (Vložit referenci PCH knihovny ladění)](../build/reference/yl-inject-pch-reference-for-debug-library.md).  
  
-   Enum class – klíčové slovo v kódu, který se zkompiluje pomocí/CLR, definuje C ++ 11 výčtu, není common language runtime (CLR) výčtu. Pokud chcete definovat výčtu CLR, musí být explicitní o jeho usnadnění.  
  
-   Použijte klíčové slovo šablony explicitně rozlišení názvu závislé (standardní jazyk C++ dodržování předpisů). V následujícím příkladu je povinná vyřešit nejednoznačnosti – klíčové slovo zvýrazněná šablony. Další informace najdete v tématu [rozlišení názvů u závislých typů](../cpp/name-resolution-for-dependent-types.md).  
  
    ```cpp  
    template < typename X = "", typename = "" AY = "">  
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };  
  
    ```  
  
-   Je již povolen konstantní výraz typ float jako argument šablony, jak je znázorněno v následujícím příkladu.  
  
    ```cpp  
    template<float n=3.14>  
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'  
  
    ```  
  
-   Kód, který je zkompilován s použitím /GS možnosti příkazového řádku a má ohrožení zabezpečení vypnout po druhém může vést ke zpracování ukončení za běhu, jak je znázorněno v následujícím příkladu pseudokódu.  
  
    ```cpp  
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate  
    ```  
  
-   Architektura výchozí x86 sestavení se změní na SSE2; Proto může vysílat SSE pokyny a použije XMM registrů provádět výpočty s plovoucí desetinnou čárkou. Pokud chcete vrátit k předchozí chování, potom použijte příznak kompilátoru /arch:IA32 k určení architekturu jako IA32.  
  
-   Kompilátor může vydat varování [upozornění kompilátoru (úroveň 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) a C4701 kde dříve tomu tak není. Kompilátor použije silnější kontroly pro použití neinicializovaných místních proměnných ukazatel typu.  
  
-   Pokud nové linkeru příznak, který je zadán/highentropyva, Windows 8 obvykle způsobí, že přidělení paměti pro zpáteční adresa 64-bit.                 (Před Windows 8, toto přidělení více často vrátil adresy, které byly menší než 2 GB.)  To může vystavit ukazatel zkrácení chyby v existujícím kódu. Ve výchozím nastavení je tento přepínač na.  Chcete-li toto chování zakázat, zadejte /HIGHENTROPYVA:NO.  
  
-   Spravované kompilátoru (Visual Basic nebo C#) také podporuje/highentropyva pro spravované sestavení.  V takovém případě /HIGHENTROPYVAswitch je však vypnout ve výchozím nastavení.  
  
### <a name="ide"></a>IDE – integrované vývojové prostředí  
  
-   Přestože doporučujeme vytvořit formulářových aplikací Windows v jazyce C + +/ CLI udržování existující C + +/ CLI uživatelského rozhraní aplikace je podporována. Pokud máte k vytvoření formulářové aplikace Windows nebo jiné aplikace rozhraní .NET uživatelského rozhraní, pomocí jazyka C# nebo Visual Basic. Použijte C + +/ CLI interoperability pouze účely.  
  
### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Knihovna Parallel Patterns Library a knihovna Concurrency Runtime  
 Výčet SchedulerType UmsThreadDefault je zastaralý. Specifikace UmsThreadDefault vytváří nepoužívané upozornění a interně mapuje zpět ThreadScheduler.  
  
### <a name="standard-library"></a>Standardní knihovna  
  
-   Následující narušující změně mezi 03 C ++ 98/a C ++ 11 standardy, pomocí explicitní šablony argumenty pro volání (make_pair –) – jako inmake_pair\<int, int >(x, y) – obvykle nekompiluje v jazyce Visual C++ v sadě Visual Studio 2012. Řešení, je vždy volání make_pair – (bez argumentů explicitní šablony) – jako make_pair – (x, y). Poskytuje explicitní šablony argumenty popírá svůj účel funkce. Pokud budete potřebovat přesnou kontrolu nad výsledný typ, použijte místo make_pair – pár – jako dvojice\<krátký, krátké >(int1, int2).  
  
-   Jiné narušující změně mezi 03 C ++ 98/a C ++ 11 standardy: po implicitně převést na A B a server B je implicitně převést na C, ale není implicitně převést na C a C ++ 98/03 Visual C++ 2010 povolené pár A\<A, X > být převést ( implicitně nebo explicitně) pár\<C, X >. (Typ, X, není zde zajímají, a to není specifické pro daný typ první ve dvojici.) Protože C ++ 11 a kompilátor C++ v sadě Visual Studio 2012 zjistit, zda A není implicitně převést na C, odeberou pár převod rozlišení přetížení. Toto je kladné změnu pro mnoho scénářů. Například přetížení func (const pár\<int, int > &) a func (const pár\<řetězec, řetězec > &) a volání func() dvojice\<const char *, const char \*> bude kompilovat s tuto změnu. Tato změna však dělí kód, který spoléhali na převody agresivní pár. Takový kód obvykle odstraněny provedením jedné části převod explicitně – například podle předávání make_pair – (static_cast\<B > (a), x) k funkci, která očekává pár\<C, X >.  
  
-   Visual C++ 2010 simulated variadické šablony – například make_shared –\<T > (arg1, arg2, argN) – až limitu 10 argumenty, podle časového razítka přetížení a specializací preprocesoru zařízení. V sadě Visual Studio 2012 je tento limit snížit na 5 argumenty ke zlepšení kompilace časy a kompilátoru využití paměti pro většinu uživatelů. Však můžete nastavit limit předchozí explicitně definováním _VARIADIC_MAX jako 10, úrovni projektu.  
  
-   C ++ 11 17.6.4.3.1 [macro.names]/2 zakazuje makro izing klíčová slova, když standardní knihovna C++ hlavičky jsou zahrnuty. Hlavičky teď emitování chyby kompilátoru, pokud zjistí makro ized klíčová slova. (Definování _ALLOW_KEYWORD_MACROS umožňuje takový kód mohl zkompilovat, ale důrazně jsme bránit toto využití.) Jako výjimku makro ized nové je povolená ve výchozím nastavení, protože hlavičky komplexně vlastní ochranu pomocí #pragma push_macro("new") / #undef nové / #pragma pop_macro("new"). Definování _ENFORCE_BAN_OF_MACRO_NEW nemá přesně co naznačuje její název.  
  
-   K implementaci různých optimalizace a ladění kontroly, implementace standardní knihovna C++ záměrně dělí binární kompatibilitu mezi verzemi sady Visual Studio (2005, 2008, 2010, 2012). Pokud se používá standardní knihovna C++, to zakazuje smíšených soubory objektů a statických knihoven, které jsou kompilovaná pomocí různých verzí do jednoho binárního souboru (EXE nebo DLL) a zakazuje předávání objektů standardní knihovna C++ mezi binární soubory, které jsou kompilovaná používání různých verzí. Kombinování objekt souborů a statických knihoven (standardní knihovna C++, který se zkompiluje pomocí Visual C++ 2010 s těmi, které byly zkompilovány pomocí C++ pomocí kompilátoru v sadě Visual Studio 2012 vysílá chybami linkeru o _msc_ver – neshoda, kde je _msc_ver – makro, který obsahuje kompilátoru hlavní verzi (1 700 pro Visual C++ v sadě Visual Studio 2012). Tato kontrola nemůže zjistit kombinování knihovny DLL a nerozpozná kombinování, který zahrnuje Visual C++ 2008 nebo starším.  
  
-   Kromě zjišťování _ITERATOR_DEBUG_LEVEL neshody, který byl implementován ve Visual C++ 2010, zjistí kompilátoru C++ v sadě Visual Studio 2012 Runtime Library neshody. Tyto dojít, když kompilátor možnosti/MT (statické vydání), jsou kombinované /MTd (statické ladění), /MD (dynamické verzi) a /MDd (dynamické debug).  
  
-   operátor\<(), operátor > (), operátor\<= () a operator > = () byly dřív dostupné rodin andstdext::hash_map std::unordered_map kontejnerů, i když jejich implementace nebyly ve skutečnosti užitečné. Byly odebrány tyto nestandardní operátory v jazyce Visual C++ v sadě Visual Studio 2012. Kromě toho provádění operator==() a operator!=() pro řadu thestd::unordered_map rozšířilo tak, aby pokrývalo stdext::hash_map rodiny. (Doporučujeme Vyhněte se použití rodiny thestdext::hash_map v nový kód.)  
  
-   C ++ 11 22.4.1.4 [locale.codecvt] Určuje, že codecvt::length() a codecvt::do_length() zabere upravitelnými stateT & parametry, ale Visual C++ 2010 trvalo const stateT &. Kompilátor C++ v sadě Visual Studio 2012 trvá stateT & jako mandátem ve standardní. Tento rozdíl je důležité pro každého, kdo se pokouší o přepsání do_length() virtuální funkce.  
  
### <a name="crt"></a>CRT  
  
-   Halda C Runtime (CRT), který se používá pro nové a malloc(), už je soukromé. CRT teď používá haldy procesu. To znamená, že halda nebude odstraněn, když knihovny DLL je odpojen, ujistěte se, knihovny DLL, které odkazují staticky CRT paměti, která je přidělena kód DLL je vyčištěna předtím, než má odpojeno.  
  
-   Funkce iscsymf() vyhodnotí s záporné hodnoty.  
  
-   Struktura threadlocaleinfostruct došlo ke změně zohlednit změny funkce národního prostředí.  
  
-   CRT – funkce, které mají odpovídající vnitřní funkce jako je například memxxx(), strxxx() se odeberou z intrin.h. Pokud jste zahrnuli intrin.h pouze pro tyto funkce, musí nyní zahrnují odpovídající CRT hlavičky.  
  
### <a name="mfc-and-atl"></a>Rozhraní MFC a knihovna ATL  
  
-   Odebranou podporu Fusion (afxcomctl32.h); proto všechny metody, které jsou definovány v afxcomctl32.h se odebraly. Hlavičky souborů afxcomctl32.h a afxcomctl32.inl byl odstraněn.  
  
-   Změnit název CDockablePane::RemoveFromDefaultPaneDividier na CDockablePane::RemoveFromDefaultPaneDivider.  
  
-   Změnit podpis CFileDialog::SetDefExt používat LPCTSTR; Proto je zasaženo sestavení kódování Unicode.  
  
-   Odebrat zastaralé kategorií trasování ATL.  
  
-   Změnit podpis CBasePane::MoveWindow provést const CRect.  
  
-   Změnit podpis CMFCEditBrowseCtrl::EnableBrowseButton.  
  
-   Odebrané m_fntTabs a m_fntTabsBold z CMFCBaseTabCtrl.  
  
-   Přidat parametr do CMFCRibbonStatusBarPane konstruktory. (Je výchozí parametr, a proto není narušujících.)  
  
-   Přidat parametr konstruktoru CMFCRibbonCommandsListBox. (Je výchozí parametr, a proto není narušujících.)  
  
-   Odebrat rozhraní API AFXTrackMouse (a související proc časovače). Místo toho použijte rozhraní API Win32 TrackMouseEvent.  
  
-   Přidat parametr konstruktoru CFolderPickerDialog. (Je výchozí parametr, a proto není narušujících.)  
  
-   Změnit velikost struktury CFileStatus: člen m_attribute změněn z BAJTŮ na DWORD (tak, aby odpovídala hodnotu, která vrátila fromGetFileAttributes).  
  
-   CRichEditCtrl a rozhraní CRichEditView použít v sestaveních Unicode MSFTEDIT_CLASS (ovládacího prvku RichEdit 4.1) namísto RICHEDIT_CLASS (ovládacího prvku RichEdit 3.0).  
  
-   AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground odebrat, protože je vždy hodnotu TRUE v systému Windows Vista, Windows 7 a Windows 8.  
  
-   AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable odebrat, protože je vždy hodnotu TRUE v systému Windows Vista, Windows 7 a Windows 8.  
  
-   Removed AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea. Volání Windows API přímo v systému Windows Vista, Windows 7 a Windows 8.  
  
-   Odebrané AFX_GLOBAL_DATA::DwmDefWindowProc. Volání Windows API přímo v systému Windows Vista, Windows 7 a Windows 8.  
  
-   AFX_GLOBAL_DATA::DwmIsCompositionEnabled přejmenován na isdwmcompositionenabled – eliminovat kolize názvů.  
  
-   Změnit identifikátory pro počet interní časovače MFC a přesunout definice do afxres.h (AFX_TIMER_ID_ *).  
  
-   Změnit podpis metody OnExitSizeMove potvrdíte svůj souhlas s makro ON_WM_EXITSIZEMOVE:  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
    -   CPaneFrameWnd  
  
-   Změnit název a podpis OnDWMCompositionChanged potvrdíte svůj souhlas s makro ON_WM_DWMCOMPOSITIONCHANGED:  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
    -   CPaneFrameWnd  
  
-   Změnit podpis metody OnMouseLeave potvrdíte svůj souhlas s makro ON_WM_MOUSELEAVE:  
  
    -   CMFCCaptionBar  
  
    -   CMFCColorBar  
  
    -   CMFCHeaderCtrl  
  
    -   CMFCProperySheetListBox  
  
    -   CMFCRibbonBar  
  
    -   CMFCRibbonPanelMenuBar  
  
    -   CMFCRibbonRichEditCtrl  
  
    -   CMFCSpinButtonCtrl  
  
    -   CMFCToolBar ReplaceThisText  
  
    -   CMFCToolBarComboBoxEdit  
  
    -   CMFCToolBarEditCtrl  
  
    -   CMFCAutoHideBar  
  
-   Změnit podpis OnPowerBroadcast potvrdíte svůj souhlas s makro ON_WM_POWERBROADCAST:  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
-   Změnit podpis OnStyleChanged potvrdíte svůj souhlas s makro ON_WM_STYLECHANGED:  
  
    -   CMFCListCtrl  
  
    -   CMFCStatusBar  
  
-   Interní metoda FontFamalyProcFonts přejmenován na FontFamilyProcFonts.  
  
-   Odebrat množství globální statické CString – objekty eliminovat nevracení paměti v některých případech (nahrazena #defines), a následující třídy členské proměnné:  
  
    -   CKeyBoardManager::m_strDelimiter  
  
    -   CMFCPropertyGridProperty::m_strFormatChar  
  
    -   CMFCPropertyGridProperty::m_strFormatShort  
  
    -   CMFCPropertyGridProperty::m_strFormatLong  
  
    -   CMFCPropertyGridProperty::m_strFormatUShort  
  
    -   CMFCPropertyGridProperty::m_strFormatULong  
  
    -   CMFCPropertyGridProperty::m_strFormatFloat  
  
    -   CMFCPropertyGridProperty::m_strFormatDouble  
  
    -   CMFCToolBarImages::m_strPngResType  
  
    -   CMFCPropertyGridProperty::m_strFormat  
  
-   Změnit podpis CKeyboardManager::ShowAllAccelerators a odebrat parametr akcelerátoru oddělovač.  
  
-   Přidat CPropertyPage::GetParentSheet a ve třídě CPropertyPage volání místo getparent – k získání okně List správné nadřazené, které může být nadřazená nebo okno CPropertyPage s nadřazený. Možná budete muset změnit na volání GetParentSheet místo ofGetParent.  
  
-   Pevná nevyváženou #pragma warning(push) ve ATLBASE. H, který chybu způsobil upozornění deaktivovat nesprávně. Upozornění jsou nyní k dispozici správně po ATLBASE. H byla analyzována.  
  
-   Přesune D2D související metody ze afx_global_data – _AFX_D2D_STATE:  
  
    -   GetDirectD2dFactory  
  
    -   Getwritefactory –  
  
    -   Getwicfactory –  
  
    -   Initd2d –  
  
    -   ReleaseD2DRefs  
  
    -   Isd2dinitialized –  
  
    -   D2D1MakeRotateMatrix  
  
    -   Namísto volání, například afxGlobalData.IsD2DInitialized, volání AfxGetD2DState -> isd2dinitialized –.  
  
-   Odebrat zastaralé ATL *. CPP soubory ze složky \atlmfc\include\.  
  
-   Inicializace afxGlobalData přesunout do na vyžádání místo v době inicializace CRT, vyhovět požadavkům DLLMain.  
  
-   Přidat metodu RemoveButtonByIndex ke třídě CMFCOutlookBarPane.  
  
-   Opraveno CMFCCmdUsageCount::IsFreqeuntlyUsedCmd k IsFrequentlyUsedCmd.  
  
-   Opraveno několik instancí restoreoriginalstate – k restoreoriginalstate – (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane).  
  
-   Odebrat nepoužité metody z CDockablePane: SetCaptionStyle, IsDrawCaption, IsHideDisabledButtons, GetRecentSiblingPaneInfo, andCanAdjustLayout.  
  
-   Odebrané CDockablePane statické členské proměnné m_bCaptionText a m_bHideDisabledButtons.  
  
-   Přidat do CMFCFontComboBox přepsání DeleteString metoda.  
  
-   Odebrat nepoužité metody z CPane: GetMinLength a IsLastPaneOnLastRow.  
  
-   Přejmenovat CPane::GetDockSiteRow(CDockingPanesRow *) k CPane::SetDockSiteRow.  
  
## <a name="visual-c-2010-breaking-changes"></a>Visual C++ 2010 nejnovější změny  
  
### <a name="compiler"></a>Kompilátoru  
  
-   Auto – klíčové slovo má nové výchozí význam. Použití staré význam je taková situace vzácná, a proto nebude touto změnou ovlivněná většinu aplikací.  
  
-   New – klíčové slovo static_assert zavádí, které způsobí ke konfliktu názvů, pokud již existuje identifikátor s tímto názvem ve vašem kódu.  
  
-   Podpora pro nový zápis lambda nezahrnuje podporu pro kódování necitovaných identifikátorů GUID v IDL Atribut uuid.  
  
-   Rozhraní .NET Framework 4 zavádí koncepci výjimky v poškozeném stavu, které jsou výjimky, které opustí proces v neopravitelném stavu poškození. Ve výchozím nastavení nelze zachytit poškozený stav výjimky, dokonce i s možností/EHa kompilátoru, který zachytí všechny ostatní výjimky.                 Chcete-li explicitně zachytávat poškozeném stavu, použijte __try –\__except příkazy. Nebo použijte atribut [HandledProcessCorruptedStateExceptions] pro povolení funkce zachycení výjimky v poškozeném stavu.  Tato změna ovlivní především systémové programátory, kteří může mít pro zachycení výjimek v poškozeném stavu. Osm výjimky jsou STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, status_ – UNWIND_CONSOLIDATE.                 Další informace o těchto výjimkách naleznete v tématu [GetExceptionCode –](https://msdn.microsoft.com/en-us/library/windows/desktop/ms679356.aspx) makro.  
  
-   Revidované /GS kompilátoru možnosti chrání proti přetečení zásobníku více komplexněji než v dřívějších verzí. Tato verze může vložit další kontroly zabezpečení v zásobníku, která může snížit výkon. New – klíčové slovo __declspec(safebuffers) oznamujete použijte kompilátoru není vložit kontrol zabezpečení pro určité funkce.  
  
-   Pokud kompilujete s /GL (optimalizace celého programu) a možnosti kompilátoru/CLR (kompilace Common Language Runtime), /GLoption ignorována. Tato změna byla provedena, protože kombinace – možnosti kompilátoru poskytují málo výhod. V důsledku této změny je lepší výkon sestavení.  
  
-   Ve výchozím nastavení podpora trigraph vypnutá ve Visual C++ 2010. / Zc: trigraphs kompilátoru možnost použijte k povolení podpory trigraph. Trigraph se skládá ze dvou po sobě jdoucích otazníky ("??") následuje jedinečný třetí znak. Kompilátor nahradí trigraph odpovídající interpunkční znaménko. Například kompilátor nahradí "?? = "trigraph znakem '#'. Použití trigraphs ve zdrojových souborech C, které používají znaková sada, která neobsahuje vhodné grafické reprezentace pro některé znaky interpunkce.  
  
-   Linkeru již podporuje optimalizace pro systém Windows 98. Možnost/OPT (optimalizace) vytvoří chybu v době kompilace zadáte-li / OPT: systémem Windows 98 nebo /OPT:NOWIN98.  
  
-   Výchozí možnosti kompilátoru, které jsou určené RuntimeLibrary a DebugInformationFormat sestavení systému, které se změnily vlastnosti. Ve výchozím nastavení tyto sestavení, které jsou zadané vlastnosti v projektech, které jsou vytvořené pomocí Visual C++ verze 7.0 prostřednictvím 10.0. Pokud provádíte migraci projekt, který byl vytvořen Visual C++ verze 6.0, zvažte, zda chcete zadat hodnotu pro tyto vlastnosti.  
  
-   Ve Visual C++ 2010, RuntimeLibrary = vícevláknové (/ MD) a DebugInformationFormat = ProgramDatabase (/Zi). V jazyce Visual C++ 9.0, RuntimeLibrary = vícevláknové (/ MT) a DebugInformationFormat = zakázáno.  
  
### <a name="clr"></a>CLR  
  
-   Kompilátory jazyka Microsoft C# a Visual Basic můžete nyní vytvořit primární spolupracující sestavení (no-PIA). No-PIA sestavení můžete použít typy modelu COM bez nasazení relevantní primární spolupracující sestavení (PIA). Při využívání no-PIA sestavení vyprodukované Visual C# nebo Visual Basic, je nutné před odkazem no-PIA sestavení, která používá knihovnu odkazovat PIA sestavení na příkaz compile.  
  
### <a name="visual-c-projects-and-msbuild"></a>Projekty Visual C++ a nástroje MSBuild  
  
-   Projekty Visual C++ jsou nyní založené na nástroji MSBuild. Proto soubory projektu používat nový formát souboru XML a VCXPROJ příponu souboru. Visual C++ 2010 automaticky převádí soubory projektu z dřívějších verzí sady Visual Studio na nový formát souboru. Existující projekt má vliv, pokud je závislý na předchozí .vcproj nástroj, VCBUILD.exe nebo příponu souboru projektu, buildu.  
  
-   V dřívějších verzích Visual C++ podporována opožděné vyhodnocení vlastností. Například vlastností nadřazené může import podřízený seznam vlastností a nadřazený může pomocí proměnné definované v podřízeném definovat jiné proměnné. Opožděné vyhodnocení povoleno nadřazenému použít proměnnou podřízené ještě před naimportované podřízený seznam vlastností. Ve Visual C++ 2010 nelze použít seznam proměnných projektu předtím, než je definován, protože MSBuild podporuje pouze včasné vyhodnocení.  
  
### <a name="ide"></a>IDE – integrované vývojové prostředí  
  
-   Dialogové okno ukončení aplikace už ukončení aplikace. V předchozích verzích když funkce abort() nebo terminate() zavřeno sestavení aplikace, běhové knihovny jazyka C zobrazí zprávu o ukončení aplikace v poli okna nebo dialogového okna konzoly. Zpráva uvedená v části "Tato aplikace vyžaduje modul Runtime ukončen neobvyklým způsobem. Obraťte se na tým podpory aplikace Další informace."                 Zpráva ukončení aplikace byla redundantní, protože Windows následně zobrazí aktuální ukončení obslužná rutina, která byla obvykle chybách systému Windows (zotavení po havárii. Dialogové okno Watson) nebo ladicího programu sady Visual Studio. Spouštění v sadě Visual Studio 2010, běhové knihovny jazyka C nezobrazuje zprávy. Kromě toho modul runtime brání aplikaci v ukončení před zahájením ladicí program. Toto je narušující změně pouze v případě, že jste na předchozí chování zprávy ukončení aplikace závisí.  
  
-   Konkrétně pro Visual Studio 2010, IntelliSense nefunguje pro C + +/ CLI kódu nebo atributy, najít všechny odkazy nefunguje pro místní proměnné a modelu kódu není názvy typů z importovaných sestavení nebo odkazující na jejich qualifi plně typy ED názvy.  
  
### <a name="libraries"></a>Knihovny  
  
-   SafeInt – třída je součástí Visual C++ a již není v samostatný soubor ke stažení. Toto je narušující změně pouze v případě, že jste si vytvořili třídu, která je také s názvem "SafeInt".  
  
-   Manifesty nasazení modelu knihovny už používá k nalezení konkrétní verzi knihovny. Místo toho název každé knihovny DLL obsahuje číslo verze a tento název můžete použít k vyhledání knihovny.  
  
-   V předchozích verzích sady Visual Studio může znovu sestavit knihovny run-time. Visual C++ 2010 již nepodporuje vytváření vlastní kopie C spusťte soubory knihovny čas.  
  
### <a name="standard-library"></a>Standardní knihovna  
  
-   \<Iterator > hlavička již nebude automaticky zahrnuta v mnoha další hlavičkové soubory. Místo toho zahrnout toto hlavičku explicitně, pokud potřebujete podporu pro samostatných iterátorů definovaných v existující projekt An má vliv, pokud je závislý na předchozí nástroj pro sestavení, VCBUILD.exe nebo příponu souboru projektu. vcproj.interator > mu ader.  
  
-   V \<algoritmus > záhlaví, checked_ * a unchecked_\* funkce jsou odebrány. A v \<iterator >> záhlaví, checked_iteratorclass, bude odstraněn a třída unchecked_array_iterator byla přidána.  
  
-   Konstruktor CComPtr::CComPtr(int) je odebrán. Tento konstruktor povolené objekt a CComPtr zkonstruovat z makra hodnotu NULL, ale bylo zbytečné a nesmyslené konstrukce z celých čísel nulová.  
  
     CComPtr stále konstruovat z NULL, který je definován jako 0, ale selže, pokud je vytvořen z celé jiného než 0. Místo toho použijte nullptr.  
  
-   Byly odebrány následující funkce člen ctype: ctype::_Do_narrow_s, ctype::_Do_widen_s, ctype::_narrow_s, ctype::_widen_s. Pokud aplikace používá jednu z těchto členských funkcí, musíte jej nahradit s odpovídající verzi nezabezpečené: ctype::do_narrow, ctype::do_widen, ctype::narrow, ctype::widen.  
  
### <a name="crt-mfc-and-atl-libraries"></a>CRT, MFC a knihovny ATL  
  
-   Odebrala se podpora pro uživatele k vytvoření knihovny CRT, MFC a knihovna ATL. Například příslušné nmake soubor není k dispozici.                 Uživatelé však stále mají přístup ke zdrojovému kódu pro tyto knihovny. A dokument, který popisuje nástroje MSBuild možnosti, které společnost Microsoft používá k vytvoření tyto knihovny pravděpodobně budou odeslány v blogu týmu Visual C++.  
  
-   Odebrala se podpora MFC pro IA64. Však podpora pro CRT a knihovna ATL na IA64 je stále k dispozici.  
  
-   Řadové číslovky se už znovu použít MFC soubory definice modulu (.def). Tato změna znamená řadové číslovky nebudou liší podverze a bude možné zlepšit binární kompatibilitu pro aktualizace service Pack a rychlé opravy.  
  
-   CDocTemplate – třída byla přidána nová virtuální funkce. Tato nová virtuální funkce je [CDocTemplate – třída](../mfc/reference/cdoctemplate-class.md). Předchozí verze OpenDocumentFile měl dva parametry. Nová verze má tři parametry. Pro podporu správce restartování, musí všechny třídy odvozené od CDocTemplate implementovat verzi, která má tři parametry. Nový parametr je bAddToMRU.  
  
### <a name="macros-and-environment-variables"></a>Makra a proměnných prostředí  
  
-   __MSVCRT_HEAP_SELECT proměnné prostředí již není podporována. Tato proměnná prostředí je odebrána a žádná náhrada není dostupná.  
  
### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler – referenční dokumentace  
  
-   Několik direktivy byly odebrány z Microsoft Macro Assembler – referenční dokumentace kompilátoru. Odebrané směrnice jsou.186,.286, .286P.287,.8086,.8087, a. NO87.  
  
## <a name="visual-c-2008-breaking-changes"></a>Visual C++ 2008 nejnovější změny  
  
### <a name="compiler"></a>Kompilátoru  
  
-   Systému Windows 95, Windows 98, Windows ME a platformy systému Windows NT již nejsou podporovány. Tyto operační systémy byly odebrány ze seznamu cílových platforem.  
  
-   Kompilátor již nepodporuje více atributů, které byly přímo spojené s ATL Server. Již nejsou podporovány následující atributy:  
  
    -   perf_counter  
  
    -   perf_object  
  
    -   perfmon  
  
    -   request_handler  
  
    -   soap_handler  
  
    -   soap_header  
  
    -   soap_method  
  
    -   tag_name  
  
### <a name="visual-c-projects"></a>Projekty Visual C++  
  
-   Při upgradování projektů z dřívějších verzí sady Visual Studio, můžete chtít, aby byly větší než nebo rovna než 0x0500 upravit maker WINVER a _WIN32_WINNT.  
  
-   Počínaje verzí Visual Studio 2008, Průvodce vytvořením projektu nemá možnost pro vytvoření projektu C++ SQL Server. SQL Server projekty vytvořené pomocí starší verze sady Visual Studio bude stále zkompilování a správně fungovat.  
  
-   Odebral se soubor hlaviček Winable.h rozhraní API systému Windows. Včetně winuser.h místa.  
  
-   Knihovně rozhraní API systému Windows Rpcndr.lib byla odebrána. Propojte s rpcrt4.lib místo.  
  
### <a name="crt"></a>CRT  
  
-   Odebrala se podpora pro systém Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4.0.  
  
-   Odebrali jsme tyto globální proměnné:  
  
    -   _osplatform  
  
    -   _osver  
  
    -   _winmajor  
  
    -   _winminor  
  
    -   _winver  
  
-   Následující funkce byly odebrány. Místo toho použijte funkce rozhraní API systému Windows GetVersion nebo GetVersionEx:  
  
    -   _get_osplatform  
  
    -   _get_osver  
  
    -   _get_winmajor  
  
    -   _get_winminor  
  
    -   _get_winver  
  
-   Došlo ke změně syntaxe poznámek SAL. Další informace najdete v tématu [poznámek SAL](../c-runtime-library/sal-annotations.md).  
  
-   Filtr IEEE teď podporuje sada instrukcí SSE 4.1. Další informace najdete v tématu [_fpieee_flt –](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt –.  
  
-   Běhové knihovny jazyka C, které jsou dodávány pomocí sady Visual Studio již nejsou závislé na msvcrt.dll knihovny DLL systému.  
  
### <a name="standard-library"></a>Standardní knihovna  
  
-   Odebrala se podpora pro systém Windows 95, Windows 98, Windows Millennium Edition a Windows NT 4.0.  
  
-   Při kompilaci v režimu ladění s _HAS_ITERATOR_DEBUGGING definované (nahrazena [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010), aplikace bude nyní assert při iterovat se zvýší nebo sníží po rozsah základní kontejneru.  
  
-   Členské proměnné c zásobníku – třída je teď deklarována chráněný. Tato proměnná člen dříve, byla deklarována veřejné.  
  
-   Došlo ke změně chování money_get::do_get. Dříve při analýze peněžní částka s další část číslic, než jsou volány pro frac_digits –, do_get – umožňuje využívat všechny. Do_get – nyní zastaví Analýza po spotřebování maximálně frac_digits – znaky.  
  
### <a name="atl"></a>ATL  
  
-   ATL nemůže být sestaven bez závislosti na CRT. V dřívějších verzích sady Visual Studio, můžete použít #define atl_min_crt – aby projektu knihovny ATL minimálně závisí na CRT. V aplikaci Visual C++ 2008 jsou všechny projekty knihovny ATL minimálně závislá na CRT bez ohledu na to, jestli je definován atl_min_crt –.  
  
-   Základu kódu ATL Server byla vydána jako sdílený zdroj projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio. Data kódování a dekódování třídy z funkce atlenc.h a nástroj a třídy z atlutil.h a atlpath.h byla držena a jsou teď součástí knihovny serveru ATL. Několik souborů, které jsou přidružené k serveru ATL již nejsou součástí sady Visual Studio.  
  
-   Některé funkce jsou již zahrnuty v knihovně DLL. Stále se nacházejí v knihovně importu. To nebude mít vliv na kód, který využívá funkce staticky. Bude mít vliv pouze kód, který používá tyto funkce dynamicky.  
  
-   Makra PROP_ENTRY a PROP_ENTRY_EX byly zastaralé a nahradí andPROP_ENTRY_TYPE_EX PROP_ENTRY_TYPE makra z bezpečnostních důvodů.  
  
### <a name="atlmfc-shared-classes"></a>Sdílené třídy ATL/MFC  
  
-   ATL nemůže být sestaven bez závislosti na CRT. V dřívějších verzích sady Visual Studio, můžete použít #define atl_min_crt – aby projektu knihovny ATL minimálně závisí na CRT. V aplikaci Visual C++ 2008 jsou všechny projekty knihovny ATL minimálně závislá na CRT bez ohledu na to, jestli je definován atl_min_crt –.  
  
-   Základu kódu ATL Server byla vydána jako sdílený zdroj projekt na webu CodePlex a není nainstalován jako součást sady Visual Studio. Data kódování a dekódování třídy z funkce atlenc.h a nástroj a třídy z atlutil.h a atlpath.h byla držena a jsou teď součástí knihovny serveru ATL. Několik souborů, které jsou přidružené k serveru ATL již nejsou součástí sady Visual Studio.  
  
-   Některé funkce jsou již zahrnuty v knihovně DLL. Stále se nacházejí v knihovně importu. To nebude mít vliv na kód, který využívá funkce staticky. Bude mít vliv pouze kód, který používá tyto funkce dynamicky.  
  
### <a name="mfc"></a>MFC  
  
-   CTime – třída: CTime – třída nyní přijímá data od 1/1/1900 C.E. místo 1/1/1970 C.E.              
-   Pořadí prvků v dialogových oknech MFC polí: více ovládacích prvků v dialogovém okně pro MFC správné pořadí je mohli distribuovaný ovládacího prvku ActiveX knihovny MFC je vložit v pořadí. Tato změna opraví tohoto problému.  
  
     Můžete například vytvořit dialogové okno aplikace MFC, která má ovládací prvek ActiveX a několik ovládacích prvcích pro úpravy. Umístění ovládacího prvku ActiveX uprostřed pořadí karet ovládacích prvcích pro úpravy. Spustit aplikaci, klikněte na ovládací prvek upravit, jejichž pořadí je po ovládací prvek ActiveX a karty. Před touto změnou se fokus na ovládací prvek upravit následující ovládací prvek ActiveX místo na další ovládací prvek upravit v pořadí.  
  
-   Třída CFileDialog: Vlastních šablon pro třídu CFileDialog nelze přenést automaticky na systém Windows Vista. Jsou stále použitelné, ale nebude mít další funkce nebo vypadá dialogů styl, Windows Vista.  
  
-   Třída CWnd a CFrameWnd – třída: The CWnd::GetMenuBarInfo metoda byla odebrána.  
  
     Metoda CFrameWnd::GetMenuBarInfo je nyní nevirtuálních metoda. Další informace najdete v tématu GetMenuBarInfo Functionin Windows SDK.  
  
-   Podpora MFC ISAPI: MFC už podporuje vytváření aplikací s serveru aplikace rozhraní ISAPI (Internet Programming). Pokud chcete vytvářet aplikace ISAPI, rozšíření ISAPI přímo volejte.  
  
-   Zastaralé ANSI rozhraní API: Verze ANSI několik metod MFC jsou zastaralé. V aplikacích budoucí pomocí kódování Unicode verze těchto metod. Další informace najdete v tématu sestavení požadavky pro Windows Vista běžné ovládací prvky.  
  
## <a name="visual-c-2005-breaking-changes"></a>Visual C++ 2005 nejnovější změny  
  
### <a name="crt"></a>CRT  
  
-   Mnoho funkcí jsou zastaralé. Viz CRT zastaralé funkce.  
  
-   Mnoho funkcí nyní ověřit jejich parametrů zastavení provádění-li zadány neplatné parametry. Tato akce může přerušit kód, který předává neplatné parametry a spoléhá na funkce, je ignorována, nebo jenom vrací kód chyby. Najdete v části ověření parametru.  
  
-   Hodnota popisovač souboru -2 je nyní slouží k určení, že stdout a stderr nejsou k dispozici pro výstup, jako například v aplikaci Windows, který má žádné okno konzoly. Předchozí hodnotu použít byla -1. Další informace najdete v tématu [_fileno –](../c-runtime-library/reference/fileno.md).  
  
-   Jednovláknové CRT knihovny, libc.lib a libcd.lib, byly odebrány. Použijte vícevláknové knihovny CRT. Příznak kompilátoru /ML již není podporována. Uzamčení není verze některé funkce přidané v případech, kdy je potenciálně významného rozdíl mezi vícevláknové kód a kód jednovláknové výkonem.  
  
-   Přetížení pow, double pow (int, int), byla odebrána, aby lépe odpovídaly se standardem.  
  
-   Specifikátor formátu %n je ve výchozím nastavení v některém z řady printf funkcí již nebude podporována, protože je ze své podstaty nezabezpečené. Výchozí chování, pokud je zjištěna %n je vyvolat obslužnou rutinu neplatný parametr. Pokud chcete povolit podporu %n, použijte _set_printf_count_output – (také see_get_printf_count_output).  
  
-   sprintf nyní vytiskne záporné znaménko podepsaný nula.  
  
-   swprintf – se změnil na v souladu se standardem; nyní vyžaduje parametr velikosti. Formu swprintf – bez velikost parametru je zastaralá.  
  
-   Odebrali jsme _set_security_error_handler. Odeberte všechny volání této funkce; výchozí obslužnou rutinu je mnohem bezpečnější způsob práci s chybami zabezpečení.  
  
-   time_t – je nyní hodnotu 64-bit (Pokud je definována _USE_32BIT_TIME_T).  
  
-   _Spawn, _wspawn – funkce teď ponechte errno nezměněný v případě úspěchu podle specifikace standardní C.  
  
-   Široké znaky RTC teď používá ve výchozím nastavení.  
  
-   Funkce Podpora word s plovoucí desetinnou čárkou ovládacího prvku jsou zastaralé pro aplikace, kompilovat s/CLR nebo/CLR: PURE. Ovlivněné funkce jsou _clear87 – _clearfp –, _control87 –, _controlfp –, _fpreset –, _status87 –, _statusfp –. Upozornění na zastarání můžete zakázat tak, že definujete _CRT_MANAGED_FP_NO_DEPRECATE, ale používání těchto funkcí ve spravovaném kódu se nepředvídatelným a nepodporované.  
  
-   Některé funkce teď vrátit const ukazatele. Definováním _CONST_RETURN lze obnovit původní, bez const chování. Se týká funkcí  
  
    1.  memchr, wmemchr  
  
    2.  strchr, wcschr, _mbschr, _mbschr_l  
  
    3.  strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l  
  
    4.  strrchr, wcsrchr, _mbsrchr, _mbsrchr_l  
  
    5.  strstr, wcsstr, _mbsstr, _mbsstr_l  
  
-   Při propojení s Setargv.obj nebo Wsetargv.obj, je již nebude možné potlačit rozšíření zástupný znak na příkazovém řádku uveden v uvozovkách. Další informace najdete v tématu [rozbalení argumentů zástupných znaků](../c-language/expanding-wildcard-arguments.md).  
  
### <a name="standard-library-2005"></a>Standardní knihovny (2005)  
  
-   Třídy výjimek (umístěný ve \<výjimka > záhlaví) byl přesunut do oboru názvů – std. V předchozích verzích se tato třída byla v globálním oboru názvů. Chcete-li vyřešit všechny chyby naznačující, že třídy výjimek nebyl nalezen, přidejte následující pomocí příkazu kódu: použití oboru názvů – std;  
  
-   Při volání metody valarray::resize(), obsah valarray – budou ztraceny a budou nahrazeny výchozí hodnoty. Metoda resize() slouží k inicializaci valarray – místo dynamicky zvětšovat jako vektor.  
  
-   Iterátory ladění: Aplikace sestavené s verzí ladění knihoven C Runtime a které použití iterátory nesprávně může začít zobrazíte vyhodnotí za běhu. Chcete-li zakázat tyto vyhodnotí, je nutné definovat _HAS_ITERATOR_DEBUGGING (nahrazena [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010) na hodnotu 0. Další informace najdete v tématu [podpora ladění iterátorů](../standard-library/debug-iterator-support.md)  
  
## <a name="visual-c-net-2003-breaking-changes"></a>Visual C++ .NET 2003 nejnovější změny  
  
### <a name="compiler"></a>Kompilátoru  
  
-   Zavřením závorkách nyní vyžadován pro definované direktivy preprocesoru (C2004).  
  
-   Explicitní specializace již nelze najít parametry šablony z primární šablony ([C2146 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2146.md)).  
  
-   Chráněný člen (ne) lze přistupovat pouze prostřednictvím funkce člena třídy (B), která dědí z třídy (A), jehož (ne) je členem ([C2247 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2247.md)).  
  
-   Vylepšené usnadnění kontroly v kompilátoru nyní zjistit nepřístupný třídy base ([C2248 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2248.md)).  
  
-   Nemůže být zachycena výjimku, pokud destruktor nebo kopírování konstruktor je nedostupný (C2316).  
  
-   Výchozí argumenty ukazatelů na funkce již není povoleno ([C2383 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2383.md)).  
  
-   Člen statických dat nelze inicializovat prostřednictvím odvozené třídy ([C2477 Chyba kompilátoru](../error-messages/compiler-errors-1/compiler-error-c2477.md)).  
  
-   Inicializace definice typu není povolena standardní a nyní vygeneruje Chyba kompilátoru ([C2513 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c2513.md)).  
  
-   BOOL je nyní správný typ. ([C2632 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c2632.md)).  
  
-   UDC můžete nyní vytvoří nejednoznačnosti s přetížené operátory ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).  
  
-   Další výrazy jsou nyní považovány za platné ukazatele null konstanty ([C2668 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c2668.md)).  
  
-   Šablona <> je nyní vyžadován místech kompilátor by kde dříve implikují ho ([C2768 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c2768.md)).  
  
-   Expilicit specializace členské funkce ourside třída není platný, pokud funkci má již byla explicitně specializuje prostřednictvím specializace šablony třídy ([C2910 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c2910.md)).  
  
-   Plovoucí parametry šablon bez typu bod už nejsou povolená ([C2993 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c2993.md)).  
  
-   Šablony třídy nejsou povoleny jako argumenty typu šablony (C3206).  
  
-   Názvy funkcí Friend jsou už zasaženo obsahující obor názvů ([C3767 Chyba kompilátoru](../error-messages/compiler-errors-2/compiler-error-c3767.md)).  
  
-   Kompilátor nebude přijímat další čárkami v makru (C4002).  
  
-   Objekt typu POD zkonstruovat s inicializátoru (formuláře) bude inicializovat výchozí (C4345).  
  
-   TypeName teď je potřeba, pokud má být zpracována jako typ závislé název ([upozornění kompilátoru (úroveň 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).  
  
-   Funkce, které byly nesprávně považuje za specializací šablony jsou nelze nadále považovat za Ano (C4347).  
  
-   Členy statických dat nelze inicializovat prostřednictvím odvozené třídy (C4356).  
  
-   Specializace šablony třída musí být definován, než byl použit v návratový typ ([upozornění kompilátoru (úroveň 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).  
  
-   Kompilátor hlásí teď nedostupný kódu (C4702).  
  
## <a name="see-also"></a>Viz také  
[Co je nového pro Visual C++ v sadě Visual Studio](../what-s-new-for-visual-cpp-in-visual-studio.md)
