---
title: 'Syntaxe specifikace formátu: funkce printf a wprintf'
ms.date: 10/21/2019
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
ms.openlocfilehash: 781c90414090ff8a21414c72f744ed275e315d56
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032158"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Syntaxe specifikace formátu: funkce printf a wprintf

Různé `printf` a `wprintf` funkce trvat formát řetězec a volitelné argumenty a vytvořit formátované posloupnost znaků pro výstup. Formátovací řetězec obsahuje nula nebo více *direktiv*, což jsou literály pro výstupní nebo kódované *specifikace převodu,* které popisují, jak formátovat argument ve výstupu. Tento článek popisuje syntaxi použitou ke kódování specifikací převodu ve formátovacím řetězci. Seznam těchto funkcí naleznete v [tématu Stream I/O](../c-runtime-library/stream-i-o.md).

Specifikace převodu se skládá z volitelných a požadovaných polí v tomto formuláři:

**%**[[*vlajky*](#flags)] [[*šířka*](#width)] [. [*přesnost*](#precision)] [[*velikost*](#size)] [*typ*](#type)

Každé pole specifikace převodu je znak nebo číslo, které označuje konkrétní možnost formátu nebo specifikátor převodu. Pole požadovaného *typu* určuje druh převodu, který má být použit u argumentu. Pole volitelné *příznaky*, *šířka*a *přesnost* řídí další aspekty formátu, jako jsou úvodní mezery nebo nuly, zarovnání a zobrazená přesnost. Pole *velikosti* určuje velikost spotřebovaného a převedeného argumentu.

Základní specifikace převodu obsahuje pouze znak procenta a znak *typu.* Například `%s` určuje převod řetězce. Pro výpis znaku procent je třeba použít `%%`. Pokud znak procenta následuje znak, který nemá žádný význam jako pole formátu, je vyvolána neplatná obslužná rutina parametru. Další informace naleznete v [tématu Ověření parametru](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Z důvodu zabezpečení a stability zajistěte, aby řetězce specifikací převodu nebyly definovány uživatelem. Zvažte například program, který vyžaduje od uživatele zadání jména a ukládá vstup do proměnné řetězce s názvem `user_name`. Pro výpis `user_name` není vhodné použít:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Místo toho je lepší použít:
>
> `printf( "%s", user_name );`

<a name="type"></a>

> [!NOTE]
> V sadě Visual Studio `printf` `scanf` 2015 A rodina funkcí byly `<stdio.h>` deklarovány jako **vřádkové** a přesunuty do záhlaví a. `<conio.h>` Pokud migrujete starší kód, může se vám v souvislosti s těmito funkcemi zobrazit *LNK2019.* Další informace naleznete v [tématu Visual C++ historie změn 2003 - 2015](../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

## <a name="type-conversion-specifier"></a>Specifikátor převodu typu

Znak specifikátoru převodu *typu* určuje, zda má být odpovídající argument interpretován jako znak, řetězec, ukazatel, celé číslo nebo číslo s plovoucí desetinnou tázkou. Znak *typu* je jediným povinným polem specifikace převodu a zobrazí se za libovolnými volitelnými poli.

Argumenty, které následují za formátovacím řetězcem, jsou interpretovány podle odpovídajícího znaku *typu* a předpony volitelné [velikosti.](#size) Převody pro `char` typy `wchar_t` znaků a jsou určeny pomocí **c** nebo **C**, a jednobajtové a vícebajtové nebo široké řetězce znaků jsou určeny pomocí **s** nebo **S**, v závislosti na tom, která funkce formátování se používá. Argumenty znaků a řetězců, které jsou určeny `char` pomocí `char*` `printf` **c** a **s,** jsou interpretovány jako a podle funkcí rodiny nebo jako `wchar_t` a `wchar_t*` `wprintf` rodinné funkce. Argumenty znaků a řetězců, které jsou určeny `wchar_t` pomocí `wchar_t*` `printf` **C** a **S,** jsou interpretovány jako a podle funkcí rodiny nebo jako `char` a `char*` `wprintf` rodinné funkce. Toto chování je specifické pro společnost Microsoft.

Typy celých čísel, `int` `long` `long long`například `short`, `unsigned` , , a jejich varianty, jsou určeny pomocí **d**, **i**, **o**, **u**, **x**a **X**. Typy s plovoucí `float`desetinnou táhou, například , `double`, `long double`a , jsou určeny pomocí , **A**, **e**, **E**, **f**, **F**, **g**a **G**. **a** Ve výchozím nastavení, pokud nejsou změněny předponou *velikosti,* jsou `int` argumenty celého čísla dosazeny `double`k typu a argumenty s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou lisy jsou dosazovány k . V 64bitových systémech `int` je 32bitová hodnota; Proto 64bitová celá čísla budou zkrácena, pokud jsou formátovány pro výstup, pokud není *použita předpona velikost* **i** nebo **I64.** Typy ukazatelů, které jsou určeny **p** použít výchozí velikost ukazatele pro platformu.

> [!NOTE]
> **Specifické pro Microsoft:** Znak typu **Z** a chování znaků typu **c**, **C**, **s**a `printf` **S** při použití s funkcemi a `wprintf` jsou rozšíření společnosti Microsoft. Standard ISO C používá **c** a **s** konzistentně pro úzké znaky a řetězce a **C** a **S** pro široké znaky a řetězce ve všech formátovacích funkcích.

### <a name="type-field-characters"></a>Textové znaky pole

|Znak typu|Argument|Výstupní formát|
|--------------------|--------------|-------------------|
|**C**|Znak|Při použití `printf` s funkcemi určuje jednobajtový znak; při použití `wprintf` s funkcemi určuje široký znak.|
|**C**|Znak|Při použití `printf` s funkcemi určuje široký znak; při použití `wprintf` s funkcemi určuje jednobajtový znak.|
|**D**|Integer|Podepsané desítkové celé číslo.|
|**I**|Integer|Podepsané desítkové celé číslo.|
|**O**|Integer|Nepodepsané osmičkové číslo.|
|**U**|Integer|Nepodepsané desítkové celé číslo.|
|**X**|Integer|Nepodepsané šestnáctkové celé číslo; používá "abcdef."|
|**×**|Integer|Nepodepsané šestnáctkové celé číslo; používá "ABCDEF."|
|**E**|Plovoucí|Podepsaná hodnota, která má formulář [-]*d.dddd*__e±__*dd*\[*d*], kde *d* je jedna desetinná číslice, *dddd* je jedna nebo více desetinných míst v závislosti na zadané přesnosti nebo šest ve výchozím nastavení a *dd*\[*d*] je dvě nebo tři desetinná místa v závislosti na [formátu](../c-runtime-library/set-output-format.md) a velikosti exponentu.|
|**E**|Plovoucí|Shodné s formátem **e** s tím rozdílem, že **E** spíše než **e** zavádí exponent.|
|**F**|Plovoucí|Podepsaná hodnota, která má formulář [-]*dddd*__.__ *dddd*, kde *dddd* je jedna nebo více desetinných míst. Počet číslic před desetinnou čárkou závisí na velikosti čísla a počet číslic za desetinnou čárkou závisí na požadované přesnosti nebo ve výchozím nastavení na šesti.|
|**F**|Plovoucí|Shodné s formátem **f** s tím rozdílem, že nekonečno a nan výstup je velkými písmeny.|
|**G**|Plovoucí|Podepsané hodnoty jsou zobrazeny ve formátu **f** nebo **e,** podle toho, co je kompaktnější pro danou hodnotu a přesnost. Formát **e** se používá pouze v případě, že exponent hodnoty je menší než -4 nebo větší nebo rovno argumentu *přesnosti.* Koncové nuly jsou zkráceny a desetinná čárka se zobrazí pouze v případě, že za ní následuje jedna nebo více číslic.|
|**G**|Plovoucí|Shodné s formátem **g,** s tím rozdílem, že **E**, spíše než **e**, zavádí exponent (v případě potřeby).|
|**A**|Plovoucí|Podepsaná šestnáctková hodnota s dvojitou přesností s plovoucí desetinnou čárkou, která má tvar [-]0x*h.hhhh*__p±__*dd*, kde *h.hhhh* jsou šestnáctkové číslice (s použitím malých písmen) mantisy a *dd* jsou jedna nebo více číslic pro exponent. Přesnost určuje počet číslic za bodem.|
|**A**|Plovoucí|Podepsaná šestnáctková hodnota s dvojitou přesností s plovoucí desetinnou čárkou, která má tvar [-]0X*h.hhhh*__P±__*dd*, kde *h.hhhh* jsou šestnáctkové číslice (pomocí velkých písmen) mantisy a *dd* jsou jedna nebo více číslic pro exponent. Přesnost určuje počet číslic za bodem.|
|**N**|Ukazatel na celé číslo|Počet znaků, které jsou úspěšně zapsány tak daleko do datového proudu nebo vyrovnávací paměti. Tato hodnota je uložena v celé číslo, jehož adresa je uveden jako argument. Velikost celého čísla, na které je uvedeno, může být řízena předponou specifikace velikosti argumentu. Specifikátor **n** je ve výchozím nastavení zakázán. Informace naleznete v důležité bezpečnostní poznámce.|
|**P**|Typ ukazatele|Zobrazí argument jako adresu v šestnáctkových číslicích.|
|**S**|Řetězec|Při použití `printf` s funkcemi určuje jednobajtový nebo vícebajtový znakový řetězec; při použití `wprintf` s funkcemi určuje řetězec se širokým znakem. Znaky jsou zobrazeny až do prvního znaku null nebo dokud není dosaženo hodnoty *přesnosti.*|
|**S**|Řetězec|Při použití `printf` s funkcemi určuje řetězec se širokým znakem; při použití `wprintf` s funkcemi určuje jednobajtovo nebo vícebajtový znakový řetězec. Znaky jsou zobrazeny až do prvního znaku null nebo dokud není dosaženo hodnoty *přesnosti.*|
|**Z**|`ANSI_STRING`nebo `UNICODE_STRING` struktura|Pokud je adresa [ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string) nebo [UNICODE_STRING](/windows/win32/api/ntdef/ns-ntdef-_unicode_string) struktury předána jako argument, zobrazí řetězec obsažený `Buffer` ve vyrovnávací paměti, na který je odkazováno polem struktury. Pomocí předpony modifikátoru *velikosti* **w** určete `UNICODE_STRING` argument – například `%wZ`. Pole `Length` struktury musí být nastaveno na délku řetězce v bajtech. Pole `MaximumLength` struktury musí být nastaveno na délku vyrovnávací paměti v bajtech.<br /><br /> Znak typu **Z** se obvykle používá pouze ve funkcích ladění ovladačů, `dbgPrint` které `kdPrint`používají specifikaci převodu, například a .|

Počínaje Visual Studio 2015, pokud argument, který odpovídá specifikátor převodu s plovoucí desetinnou čárkou (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) je nekonečný, neurčitý nebo NaN, formátovaný výstup odpovídá standardu C99. V této tabulce je uveden formátovaný výstup:

|Hodnota|Výstup|
|-----------|------------|
|Nekonečno|`inf`|
|Tichý NaN|`nan`|
|Signalizace NaN|`nan(snan)`|
|Nan na dobu neurčitou|`nan(ind)`|

Každá z těchto hodnot může být předponou znaménkem. Pokud je znak *převodu typu* s plovoucí desetinnou desetinnou desetinnou tácem velké písmeno, je výstup formátován také velkými písmeny. Pokud `%F` je například specifikátor formátu `%f`místo , je `INF` nekonečno formátováno jako namísto `inf`. Funkce `scanf` můžete také analyzovat tyto řetězce, takže tyto hodnoty `printf` můžete `scanf` provést odezvu a funkce.

Před Visual Studio 2015 CRT používá jiný, nestandardní formát pro výstup nekonečné, neurčité a NaN hodnoty:

|Hodnota|Výstup|
|-----------|------------|
|+ nekonečno|`1.#INF`*náhodné číslice*|
|- nekonečno|`-1.#INF`*náhodné číslice*|
|Neurčitý (stejně jako tichý NaN)|*číslice* `.#IND` *náhodných číslic*|
|Není číslo|*číslice* `.#NAN` *náhodných číslic*|

Některé z nich mohou být předponou znaménkem a mohou být formátovány mírně odlišně v závislosti na šířce a přesnosti pole, někdy s neobvyklými efekty. Například `printf("%.2f\n", INFINITY)` by `1.#J` vytisknout, protože #INF by být "zaokrouhlena" na 2 číslice přesnosti.

> [!NOTE]
> Pokud argument, který `%s` odpovídá `%S`nebo `Buffer` , nebo pole `%Z`argumentu, který odpovídá , je ukazatel null, "(null)" se zobrazí.

> [!NOTE]
> Ve všech exponenciálních formátech je minimální počet číslic exponentu k zobrazení dva, pouze v případě potřeby použije tři. Pomocí [funkce _set_output_format](../c-runtime-library/set-output-format.md) můžete nastavit počet číslic zobrazených na tři pro zpětnou kompatibilitu s kódem napsaným pro Visual Studio 2013 a před.

> [!IMPORTANT]
> Vzhledem `%n` k tomu, že formát je ze své podstaty nezabezpečený, je ve výchozím nastavení zakázán. Pokud `%n` je zjištěna ve formátu řetězce, je vyvolána neplatná obslužná rutina parametru, jak je popsáno v [ověření parametru](../c-runtime-library/parameter-validation.md). Chcete-li povolit `%n` podporu, [přečtěte si _set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Směrnic příznaku

První volitelné pole ve specifikaci převodu obsahuje *direktivy příznaků*, nula nebo více znaků příznaku, které určují výstupní zarovnání a řídicí výstup znamének, prázdných míst, počátečních nul, desetinných míst a osmičkových a šestnáctkových předpon. Ve specifikaci převodu se může zobrazit více než jeden příznak a znaky příznaku se mohou zobrazit v libovolném pořadí.

### <a name="flag-characters"></a>Znaky příznaku

|Příznak|Význam|Výchozí|
|----------|-------------|-------------|
|**-**|Vlevo zarovnejte výsledek v rámci dané šířky pole.|Zarovnat doprava.|
|**+**|Použijte znaménko (+ nebo -) k předponě výstupní hodnoty, pokud je podepsaného typu.|Znaménko se zobrazí pouze pro záporné podepsané hodnoty (-).|
|**0**|Pokud je *šířka* předpona **0**, úvodní nuly jsou přidány, dokud není dosaženo minimální šířky. Pokud **0** oba **-** 0 a zobrazí se **0** je ignorována. Pokud je pro formát celéčíslo zadáno **0** (**i**, **u**, **x**, **X**, `%04.d` **o**, **d**) a je také k dispozici specifikace přesnosti – například **– 0** je ignorováno. Pokud **0** je určen pro formát **a** nebo **A** s plovoucí desetinnou desetinnou `0x` čarou, úvodní nuly jsou předřazené mantisa, za nebo `0X` předponou.|Žádné vycpávky.|
|**prázdné** (' ')|Použijte prázdné předponu výstupní hodnotu, pokud je podepsána a pozitivní. Prázdné je ignorováno, pokud se zobrazí příznaky blank a + .|Nezobrazí se žádné prázdné místo.|
|**#**|Při použití s formátem **o**, **x**nebo **#** **X,** příznak používá 0, 0x nebo 0X, respektive předponu libovolnou nenulovou výstupní hodnotu.|Nezobrazí se žádné prázdné místo.|
||Při použití ve formátu **e**, **E**, **f**, **F** **#** , **a**nebo **A** vynutí příznak, aby výstupní hodnota obsahovala desetinnou čárku.|Desetinná čárka se zobrazí pouze v případě, že ji následují číslice.|
||Při použití s formátem **g** nebo **#** **G** vynutí příznak výstupní hodnota obsahovat desetinnou čárku a zabraňuje zkrácení koncové nuly.<br /><br /> Ignorováno při použití s **c,** **d,** **i,** **u**nebo **s**.|Desetinná čárka se zobrazí pouze v případě, že ji následují číslice. Koncové nuly jsou zkráceny.|

<a name="width"></a>

## <a name="width-specification"></a>Specifikace šířky

Ve specifikaci převodu se pole specifikace volitelné šířky zobrazí za znaky *příznaků.* Argument *šířky* je nezáporné desetinné celé číslo, které řídí minimální počet znaků, které jsou výstupní. Pokud je počet znaků ve výstupní hodnotě menší než zadaná šířka, budou k levé nebo pravé straně**-** hodnot přidány mezery – v závislosti na tom, zda je určen příznak zarovnání vlevo ( ) až do dosažení minimální šířky. Pokud je *šířka* předpona 0, úvodní nuly jsou přidány do celočíselné nebo plovoucí desetinné hodnoty převody, dokud není dosaženo minimální šířky, s výjimkou převodu na nekonečno nebo NaN.

Specifikace šířky nikdy nezpůsobí zkrácení hodnoty. Pokud je počet znaků ve výstupní hodnotě větší než zadaná šířka nebo pokud není *zadána šířka,* jsou výstupy všechny znaky hodnoty, s výhradou specifikace *přesnosti.*

Pokud je specifikace šířky hvězdičkou`*` `int` ( ), argument ze seznamu argumentů poskytuje hodnotu. Argument *šířky* musí předcházet hodnotě, která je formátována v seznamu argumentů, jak je znázorněno v tomto příkladu:

`printf("%0*d", 5, 3);  /* 00003 is output */`

Chybějící nebo malá *šířka* hodnota ve specifikaci převodu nezpůsobí zkrácení výstupní hodnoty. Pokud je výsledek převodu širší než hodnota *šířky,* pole se rozbalí tak, aby obsahovalo výsledek převodu.

<a name="precision"></a>

## <a name="precision-specification"></a>Specifikace přesnosti

Ve specifikaci převodu je třetí volitelné pole specifikace přesnosti. Skládá se z tečky (.) následované nezáporným desetinným celočíselným číslem, které v závislosti na typu převodu určuje počet znaků řetězce, počet desetinných míst nebo počet platných číslic, které mají být výstupem.

Na rozdíl od specifikace šířky může specifikace přesnosti způsobit zkrácení výstupní hodnoty nebo zaokrouhlení hodnoty s plovoucí desetinnou desetinnou hodnotou. Pokud *precision* přesnost je zadán jako 0 a hodnota, která má být převedena je 0, výsledkem je žádný výstup znaků, jak je znázorněno v tomto příkladu:

`printf( "%.0d", 0 );      /* No characters output */`

Pokud je specifikace přesnosti hvězdičkou\* `int` ( ), argument ze seznamu argumentů poskytuje hodnotu. V seznamu argumentů musí argument *přesnost* předcházet hodnotě, která je formátována, jak je znázorněno v tomto příkladu:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Znak *typu* určuje *interpretaci přesnosti* nebo výchozí přesnost, když je přesnost *vynechána,* jak je znázorněno v následující tabulce.

### <a name="how-precision-values-affect-type"></a>Jak přesné hodnoty ovlivňují typ

|Typ|Význam|Výchozí|
|----------|-------------|-------------|
|**a**, **A**|Přesnost určuje počet číslic za bodem.|Výchozí přesnost je 13. Pokud je přesnost 0, nevytisknou se žádná **#** desetinná čárka, pokud není použit příznak.|
|**c**, **C**|Přesnost nemá žádný vliv.|Znak je vytištěn.|
|**d**, **i**, **o,** **u**, **x**, **X**|Přesnost určuje minimální počet číslic, které mají být vytištěny. Pokud je počet číslic v argumentu menší než *přesnost*, je výstupní hodnota na levé straně doplněna nulami. Hodnota není zkrácena, pokud počet číslic překročí *přesnost*.|Výchozí přesnost je 1.|
|**e**, **E**|Přesnost určuje počet číslic, které mají být vytištěny za desetinnou čárkou. Poslední vytištěná číslice je zaokrouhlena.|Výchozí přesnost je 6. Pokud je *přesnost* 0 nebo se tečka (.) zobrazí bez čísla, které za ní následuje, nezobrazí se žádná desetinná čárka.|
|**f**, **F**|Hodnota přesnosti určuje počet číslic za desetinnou čárkou. Pokud se objeví desetinná čárka, zobrazí se před ní alespoň jedna číslice. Hodnota je zaokrouhlena na příslušný počet číslic.|Výchozí přesnost je 6. Pokud je *přesnost* 0 nebo pokud se tečka (.) zobrazí bez čísla za ním, nezobrazí se žádná desetinná čárka.|
|**g**, **G**|Přesnost určuje maximální počet platných číslic vytištěných.|Vytiskne se šest platných číslic a všechny koncové nuly se zkrátí.|
|**s**, **S**|Přesnost určuje maximální počet znaků, které mají být vytištěny. Znaky přesahující *přesnost* se nevytisknou.|Znaky jsou vytištěny, dokud není zjištěn znak null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Specifikace velikosti argumentu

Ve specifikaci převodu je pole *velikosti* modifikátorem délky argumentu pro specifikátor převodu *typu.* Předpony pole *velikosti* k poli *typu* –**hh**, **h**, **j**, **l** (malá písmena L), **L**, **ll**, **t**, **w**, **z**, **I** (velká písmena i), **I32**a **I64**– zadejte "velikost" odpovídajícího argumentu – dlouhý nebo krátký, 32bitový nebo 64bitový, jednobajtový znak nebo široký znak – v závislosti na specifikátoru, který upravují. Tyto předpony velikosti se používají `printf` `wprintf` s *textovými* znaky v a rodiny funkcí k určení interpretace velikosti argumentů, jak je znázorněno v následující tabulce. Pole *velikosti* je pro některé typy argumentů volitelné. Pokud není zadána žádná předpona velikosti, formátovací modul spotřebovává celočíselné argumenty – například podepsané nebo nepodepsané `char`, `short` `double` `long double` `double` `int`, `long`, a typy výčtu – jako 32bitové `int` typy a `float`, a argumenty s plovoucí desetinnou desetinnou desetinnou desetinnou spotřebou jako 64bitové typy. Toto chování odpovídá výchozím pravidlům propagace argumentů pro seznamy proměnných argumentů. Další informace o propagaci argumentů naleznete v tématu Tři tečky a výchozí argumenty ve [výrazech Postfix](../cpp/postfix-expressions.md). V 32bitových i 64bitových systémech musí specifikace převodu 64bitového celočíselného argumentu obsahovat předponu velikosti **ll** nebo **I64**. V opačném případě chování modulu pro honosem není definována.

Některé typy mají různé velikosti v 32bitovém a 64bitovém kódu. Například `size_t` je 32 bitů dlouhý v kódu kompilované pro x86 a 64 bitů v kódu kompilované pro x64. Chcete-li vytvořit kód formátování bez ohledu na platformu pro typy s proměnnou šířkou, můžete použít modifikátor velikosti argumentu s proměnnou šířkou. Alternativně použijte modifikátor velikosti 64bitového argumentu a explicitně povýšit typ argumentu s proměnnou šířkou na 64 bitů. Modifikátor velikosti argumentu **I** specifické pro Microsoft (velká písmena i) zpracovává argumenty s celou šířkou proměnné, ale doporučujeme modifikátory j **,** **t**a **z** specifické pro typ pro přenositelnost.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Předpony velikosti pro specifikátory formátu printf a wprintf

|Chcete-li určit|Použití předpony|S specifikátorem typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`short int`<br />`short unsigned int`|**H**|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`intmax_t`<br />`uintmax_t`|**j** nebo **I64**|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`long double`|**l** (malé l) nebo **l**|**a**, **A**, **e**, **E,** **f,** **F,** **g**nebo **G**|
|`long int`<br />`long unsigned int`|**l** (malé L)|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`long long int`<br />`unsigned long long int`|**ll** (malá LL)|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`ptrdiff_t`|**t** nebo **I** (velká písmena i)|**d**, **i**, **o**, **u**, **x**nebo **X**|
|`size_t`|**z** nebo **I** (velká písmena i)|**d**, **i**, **o**, **u**, **x**nebo **X**|
|Jednobajtový znak|**H**|**c** nebo **C**|
|Široký charakter|**l** (malé L) nebo **w**|**c** nebo **C**|
|Jednobajtový znakový řetězec|**H**|**s**, **S**nebo **Z**|
|Řetězec s širokým znakem|**l** (malé L) nebo **w**|**s**, **S**nebo **Z**|

Typy `ptrdiff_t` `size_t` a `__int32` jsou `unsigned __int32` nebo na 32bitových platformách a `__int64` nebo `unsigned __int64` na 64bitových platformách. Předpony velikosti **I** (velká písmena i), **j**, **t**a **z** mají správnou šířku argumentu pro platformu.

V jazyce Visual `long double` C++, i když je odlišný `double`typ, má stejnou vnitřní reprezentaci jako .

Specifikátor typu **hc** nebo **hC** je synonymem pro **c** ve `printf` funkcích a s **c** ve `wprintf` funkcích. Specifikátor typu **lc**, **lC**, **wc**nebo **wC** `printf` je synonymem `wprintf` pro **C** ve funkcích a s **c** ve funkcích. Specifikátor typu **hs** nebo **hS** je synonymem **s** `printf` ve `wprintf` funkcích a **s** ve funkcích. Specifikátor typu **ls**, **lS**, **ws** nebo **wS** je synonymem `wprintf` s **S** ve `printf` funkcích a **s** ve funkcích.

> [!NOTE]
> **Specifické pro Microsoft:** **I** (velká písmena i), **I32**, **I64**a **w** argument velikost i modifikátor předpony jsou rozšíření společnosti Microsoft a nejsou kompatibilní s ISO C. H **h** předpona, pokud se používá `char` s daty typu a **l** (malá l) předpona při použití s daty typu `double` jsou rozšíření společnosti Microsoft.

## <a name="see-also"></a>Viz také

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[printf_p poziční parametry](../c-runtime-library/printf-p-positional-parameters.md)
