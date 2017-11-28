---
title: "Syntaxe specifikace formátu: funkce printf a wprintf | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e8c81bfa9f87d9612d989cef84ddf538ff28d98
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Syntaxe specifikace formátu: funkce printf a wprintf

Různé `printf` a `wprintf` funkce vezme řetězec formátu a volitelné argumenty a vytvoří formátovaný posloupnosti znaků pro výstup. Řetězec formátu obsahuje nula nebo více *direktivy*, což jsou buď literálu znaků pro výstupní nebo kódovaného *převod specifikace* popisují způsob formátování argument ve výstupu. Toto téma popisuje syntaxe použitá ke kódování převod specifikace ve formátovacím řetězci. Seznam těchto funkcí najdete v tématu [vstupně-výstupní datový proud](../c-runtime-library/stream-i-o.md).

Specifikace převod se skládá z volitelné a požadované pole v tomto formuláři:

**%**[[*příznaky*](#flags)] [[*šířka*](#width)] [.[ *přesnost*](#precision)] [[*velikost*](#size)][*typu*](#type)

Každé pole Specifikace převod je znak nebo číslo, které označuje, že konkrétní možnost nebo převod specifikátor formátu. Požadované *typ* pole určuje druh převodu má být použita pro argument. Volitelné *příznaky*, *šířka*, a *přesnost* pole řízení formátu dalších aspektů, například úvodní mezery nebo nul, zarovnání do bloku a zobrazit přesnost. *Velikost* pole určuje velikost argumentu spotřebované a převést.

Specifikace základní převod obsahuje pouze znak procenta a *typ* znak. Například `%s` Určuje převod řetězce. Pro výpis znaku procent je třeba použít `%%`. Pokud znak procenta následuje znak, který nemá žádný význam jako formát pole, je volána obslužná rutina neplatný parametr. Další informace najdete v tématu [ověření parametru](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Zabezpečení a stability Ujistěte se, že převod specifikace, které řetězce nejsou uživatelem definované. Zvažte například program, který vyžaduje od uživatele zadání jména a ukládá vstup do proměnné řetězce s názvem `user_name`. Pro výpis `user_name` není vhodné použít:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Místo toho je lepší použít:
>
> `printf( "%s", user_name );`

<a name="type"></a>

## <a name="type-conversion-specifier"></a>Specifikátor převod typu

*Typ* převod specifikátor znak určuje, jestli se k interpretaci odpovídající argument jako znak, řetězec, ukazatel, celé číslo nebo číslo s plovoucí desetinnou čárkou. *Typ* znak je pole Specifikace pouze požadované převod a zobrazí se po libovolná nepovinná pole.

Argumenty, které následují řetězec formátu se interpretují podle příslušné *typ* znak a volitelné [velikost](#size) předponu. Převody pro znakové typy `char` a `wchar_t` zadávají pomocí **c** nebo **C**, a zadávají se jednobajtové a vícebajtové nebo celý znak řetězců pomocí **s** nebo **S**, v závislosti na formátování funkci, která se používá. Znak a řetězec argumenty, které jsou určené pomocí **c** a **s** se interpretují jako `char` a `char*` podle `printf` rodiny funkce, nebo jako `wchar_t` a `wchar_t*` podle `wprintf` rodiny funkce. Znak a řetězec argumenty, které jsou určené pomocí **C** a **S** se interpretují jako `wchar_t` a `wchar_t*` podle `printf` rodiny funkce, nebo jako `char` a `char*` podle `wprintf` rodiny funkce. Toto chování se konkrétní společnosti Microsoft.

Celočíselné typy, jako `short`, `int`, `long`, `long long`a jejich `unsigned` variant, jsou určené pomocí **d**, **i**, **o**, **u**, **x**, a **X**. Typy s plovoucí desetinnou čárkou, jako `float`, `double`, a `long double`, jsou určené pomocí **a**, **A**, **e**, **E**, **f**, **F**, **g**, a **G**. Ve výchozím nastavení pokud jsou upraveném *velikost* předpona, celé číslo argumenty jsou sloučen s `int` typ a argumenty s plovoucí desetinnou čárkou jsou sloučen s `double`. V 64bitových systémech `int` je hodnota 32-bit; proto budou celých čísel 64-bit zkráceny, když jsou formátovány pro výstup, pokud *velikost* předpona **udou** nebo **I64**se používá. Typy ukazatelů, které jsou určené **p** použít výchozí velikost ukazatele pro platformu.

> [!NOTE]
> **Konkrétní Microsoft**  
> **Z** zadejte znak a chování **c**, **C**, **s**, a **S** typ znaků, kdy se používají se `printf` a `wprintf` funkce, jsou rozšíření Microsoft. Používá standardní ISO C **c** a **s** konzistentně pro úzké znaky a řetězce, a **C** a **S** pro široké znaky a řetězce, v všechny funkce formátování.

### <a name="type-field-characters"></a>Znaky pole typu

|– Znak typu|Argument|Výstupní formát|
|--------------------|--------------|-------------------|
|**c**|Znak|Při použití s `printf` funkce, určuje znak jednobajtové; při použití s `wprintf` funkce, určuje široký znak.|
|**C**|Znak|Při použití s `printf` funkce, určuje široká znaková; při použití s `wprintf` funkce, určuje jednobajtové znaky.|
|**d**|Integer|Desetinné číslo se znaménkem.|
|**i**|Integer|Desetinné číslo se znaménkem.|
|**o**|Integer|Osmičkové celé číslo bez znaménka.|
|**u**|Integer|Decimal celé číslo bez znaménka.|
|**x**|Integer|Hexadecimální celé číslo bez znaménka; používá "abcdef".|
|**X**|Integer|Hexadecimální celé číslo bez znaménka; používá "ABCDEF".|
|**e**|S plovoucí desetinnou čárkou|Podepsané hodnotu, která má tvar [-]*d.dddd*__e±__*dd*[*d*] kde *d* je jednu číslici desítkové soustavy, *dddd* je jeden nebo více desetinných míst v závislosti na Zadaná přesnost nebo šest ve výchozím nastavení, a *dd*[*d*] je dva nebo tři desetinných míst v závislosti na [výstupní formát](../c-runtime-library/set-output-format.md) a velikost exponent.|
|**E**|S plovoucí desetinnou čárkou|Stejný jako **e** formátu vyjma toho, že **E** místo **e** zavádí exponent.|
|**f**|S plovoucí desetinnou čárkou|Podepsané hodnotu, která má tvar [-]*dddd*__.__ *dddd*, kde *dddd* je jeden nebo více desetinných míst. Počet číslic od desetinné čárky závisí na velikosti číslo a počet číslic po desetinné čárky závisí na požadovanou přesnost nebo šest ve výchozím nastavení.|
|**F**|S plovoucí desetinnou čárkou|Stejný jako **f** formátu s tím rozdílem, že je aktivované výstup infinity a nan.|
|**g**|S plovoucí desetinnou čárkou|Podepsaný hodnoty jsou zobrazeny ve **f** nebo **e** formátu, podle toho, co je kompaktnější pro danou hodnotu a přesnosti. **e** formát se používá jenom v případě, že exponent hodnota je menší než -4 nebo větší než nebo rovna hodnotě *přesnost* argument. Koncové nuly se zkrátí a desetinné čárky se zobrazí pouze v případě, že je jeden nebo více číslic podle něj.|
|**G**|S plovoucí desetinnou čárkou|Stejný jako **g** formátu, vyjma toho, že **E**, místo **e**, představuje exponent (kde je to vhodné).|
|**a**|S plovoucí desetinnou čárkou|Podepsané šestnáctkové hodnoty s plovoucí desetinnou čárkou s dvojitou přesností, která má tvar [-] 0 x*h.hhhh*__p±__*dd*, kde *h.hhhh* jsou se hex číslice (použití malých písmen) mantisa, a *dd* pro exponent jsou jeden nebo více číslic. Přesnost určuje počet číslic za bodem.|
|**A**|S plovoucí desetinnou čárkou|Podepsané šestnáctkové hodnoty s plovoucí desetinnou čárkou s dvojitou přesností, která má tvar [-] 0 X*h.hhhh*__P±__*dd*, kde *h.hhhh* jsou se hex číslice (použití velkých písmen) mantisa, a *dd* pro exponent jsou jeden nebo více číslic. Přesnost určuje počet číslic za bodem.|
|**n**|Ukazatel na celé číslo|Počet znaků, které jsou úspěšně zapsána dosavadní do datového proudu nebo vyrovnávací paměti. Tato hodnota je uložena v celé číslo, jehož adresa je uvedena jako argument. Velikost odkazoval na celé číslo se dá nastavit podle specifikace předponu argument velikost. **n**  Specifikátor ve výchozím nastavení vypnutá, podrobnosti viz poznámka důležité zabezpečení.|
|**p**|Typ ukazatele|Zobrazí argument jako adresu v šestnáctkové číslice.|
|**s**|String|Při použití s `printf` funkce, určuje jednobajtové nebo vícebajtové znakové řetězce; při použití s `wprintf` funkce, určuje široká charakterová řetězec. Znaky se zobrazí až po prvním znaku hodnotu null, nebo dokud se *přesnost* nebude dosaženo hodnoty.|
|**S**|String|Při použití s `printf` funkce, určuje široká charakterová řetězec; při použití s `wprintf` funkce, určuje jednobajtové nebo vícebajtové znakové řetězce. Znaky se zobrazí až po prvním znaku hodnotu null, nebo dokud se *přesnost* nebude dosaženo hodnoty.|
|**Z**|`ANSI_STRING`nebo `UNICODE_STRING` struktura|Pokud adresu [ANSI_STRING](http://msdn.microsoft.com/library/windows/hardware/ff540605.aspx) nebo [UNICODE_STRING](http://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) struktura je předán jako argument, zobrazí řetězec obsažené ve vyrovnávací paměti, na kterou odkazuje `Buffer` pole struktury. Použití *velikost* modifikátor předpona **w** k určení `UNICODE_STRING` argument – například `%wZ`. `Length` Pole struktury musí být nastavené na délka řetězce v bajtech. `MaximumLength` Pole struktury musí být nastavené na délka vyrovnávací paměti v bajtech.<br /><br /> Obvykle **Z** – znak typu se používá pouze v ovladači ladění funkcí, které používají specifikaci převodu, jako `dbgPrint` a `kdPrint`.|

Od verze sady Visual Studio 2015, pokud argument, který odpovídá specifikátor převody plovoucí desetinné čárky (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) je nekonečné neomezené, nebo NaN, formátovaný výstup vyhovuje C99 standard. Tato tabulka uvádí formátovaný výstup:

|Hodnota|Výstup|
|-----------|------------|
|nekonečna|`inf`|
|Quiet NaN.|`nan`|
|Zabezpečovacím NaN.|`nan(snan)`|
|Neomezené NaN.|`nan(ind)`|

Všechny tyto hodnoty mohou obsahovat předponu znakem. Pokud s plovoucí desetinnou čárkou *typ* převod specifikátor znak je velké písmeno, a potom výstup je formát velkými písmeny. Například, pokud je specifikátor formátu `%F` místo `%f`, nekonečna je formátováno jako `INF` místo `inf`. `scanf` Funkce mohou také analyzovat tyto řetězce, takže tyto hodnoty můžete provádět operace round-trip prostřednictvím `printf` a `scanf` funkce.

Před Visual Studio 2015 CRT použít jiný, nestandardní formát pro výstup nekonečné neomezené a hodnoty NaN:

|Hodnota|Výstup|
|-----------|------------|
|+ infinity|`1.#INF`*náhodná čísla*|
|-infinity|`-1.#INF`*náhodná čísla*|
|Nekonečný (stejný jako quiet NaN)|*číslice* `.#IND` *náhodná čísla*|
|NaN|*číslice* `.#NAN` *náhodná čísla*|

Některý z těchto může mít předponu znakem a může mít naformátován trochu jinak v závislosti na šířku pole nebo přesnost, někdy s neobvyklou účinky. Například `printf("%.2f\n", INFINITY)` by tisku `1.#J` vzhledem k tomu, že #INF by "zaokrouhlen" přesností 2 číslic.

> [!NOTE]
> Pokud argument, který odpovídá `%s` nebo `%S`, nebo `Buffer` pole argumentu, která odpovídá `%Z`, je ukazatel s hodnotou null, se zobrazí "(null)".

> [!NOTE]
> V všechny exponenciální formáty minimální počet číslic exponent k zobrazení je dva týdny, pomocí tří pouze v případě potřeby. Pomocí [_set_output_format –](../c-runtime-library/set-output-format.md) funkce, můžete nastavit počet číslic, na které se zobrazí na tři pro zpětnou kompatibilitu s kódu napsaného pro Visual Studio 2013 a před.

> [!IMPORTANT]
> Protože `%n` formát je ze své podstaty nezabezpečené, je ve výchozím nastavení zakázaná. Pokud `%n` je došlo ve formátovacím řetězci, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../c-runtime-library/parameter-validation.md). Chcete-li povolit `%n` podpory naleznete v tématu [_set_printf_count_output –](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Direktivy příznaku

První volitelné pole ve specifikaci převod obsahuje *příznak direktivy*, nula nebo více znaků, které zadejte odůvodnění výstup a řídit výstupní přihlásí, prázdné hodnoty, úvodní nuly, desetinných míst a osmičková příznak a hexadecimální předpony. Může se zobrazit více než jedna direktiva příznak ve specifikaci převod a příznak znaky se mohou objevit v libovolném pořadí.

### <a name="flag-characters"></a>Příznak znaků

|Příznak|Význam|Výchozí|
|----------|-------------|-------------|
|**-**|Výsledek v rámci dané pole Šířka zarovnání doleva.|Zarovnání doprava.|
|**+**|Symbol (+ nebo -) jako předpona výstupní hodnotu, pokud je typ se znaménkem.|Přihlášení se zobrazí pouze pro podepsané záporné hodnoty (-).|
|**0**|Pokud *šířka* je předponu **0**, úvodní nuly se přidají, dokud nebude dosaženo minimální šířku. Pokud oba **0** a  **-**  se zobrazí, **0** je ignorována. Pokud **0** je zadán pro formátu celé číslo (**i**, **u**, **x**, **X**, **o**, **d**) a specifikace přesnosti je také k dispozici – například `%04.d`– **0** je ignorována. Pokud **0** pro je zadána **a** nebo **A** s plovoucí desetinnou čárkou formátu úvodní nuly se přidá jako předpona k mantisa, po `0x` nebo `0X` předponu.|Odsazení.|
|**prázdné** ("")|Pomocí prázdné předpony výstupní hodnotu, pokud je podepsaná a kladná. Prázdné je ignorována, pokud obě prázdné a + příznaky zobrazí.|Zobrazí se žádné prázdné.|
|**#**|Když se používá s **o**, **x**, nebo **X** formát,  **#**  příznak používá 0, 0 x, nebo 0 X, k předponě všechny nenulové hodnoty hodnota výstupu.|Zobrazí se žádné prázdné.|
||Pokud se používá s **e**, **E**, **f**, **F**, **a** nebo **A** formát, **#** příznak vynutí výstupní hodnotu tak, aby obsahovala desetinné čárky.|Desetinné čárky se zobrazí jenom v případě, že číslic podle něj.|
||Pokud se používá s **g** nebo **G** formát,  **#**  příznak vynutí výstupní hodnotu tak, aby obsahovala desetinné čárky a brání zkrácení koncové nuly.<br /><br /> Ignorovat při použití s **c**, **d**, **i**, **u**, nebo **s**.|Desetinné čárky se zobrazí jenom v případě, že číslic podle něj. Koncové nuly se zkrátí.|

<a name="width"></a>

## <a name="width-specification"></a>Specifikace šířky

Ve specifikaci převod se zobrazí pole Specifikace volitelné šířka po všech *příznaky* znaků. *Šířka* argument je nezáporná celočíselná decimal, která určuje minimální počet znaků, které jsou výstupem. Pokud počet znaků v výstupní hodnota je menší než nastavená šířka, prázdné hodnoty se přidají doleva nebo doprava hodnot – v závislosti na tom, jestli příznak zarovnání doleva (**-**) je zadán – dokud minimální je dosaženo šířku. Pokud *šířka* předponou je hodnotou 0, úvodní nuly jsou přidány do celé číslo nebo číslo s plovoucí desetinnou čárkou převody až do dosažení minimální šířka, kromě případů, kdy převod na infinity ani NaN.

Specifikace šířky nikdy způsobí, že hodnota k oříznutí. Pokud je počet znaků v výstupní hodnotu větší než nastavená šířka, nebo pokud *šířka* nebyla zadána, všechny znaky hodnoty jsou výstupem, podléhají *přesnost* specifikace.

Pokud je specifikace šířky hvězdičku (`*`), `int` argument ze seznamu argument poskytuje hodnota. *Šířka* argument musí předcházet hodnotu, která formátována v seznamu argumentů, jak je uvedeno v následujícím příkladu:

`printf("%0*f", 5, 3);  /* 00003 is output */`

Chybějící nebo malá *šířka* hodnotu ve specifikaci převod nezpůsobí zkrácení výstupní hodnotu. Pokud je výsledek převodu z širší než *šířka* hodnotu pole rozšíří tak, aby obsahovala výsledek převodu.

<a name="precision"></a>

## <a name="precision-specification"></a>Specifikace přesnosti

Ve specifikaci převod třetí volitelné pole je specifikace přesnosti. Skládá se z tečka (.), za nímž následuje nezáporná celočíselná decimal, který v závislosti na typu Převod určuje počet znaků řetězce, počet desetinných míst nebo počet platných číslic jako výstup.

Na rozdíl od specifikace šířky může způsobit specifikace přesnosti buď zkrácení výstupní hodnotu nebo zaokrouhlení hodnoty s plovoucí desetinnou čárkou. Pokud *přesnost* je zadán jako 0 a hodnotu, která má být převeden je 0, výsledkem je žádný výstup znaků, jak je uvedeno v následujícím příkladu:

`printf( "%.0d", 0 );      /* No characters output */`

Pokud je specifikace přesnosti hvězdičku (\*), `int` argument ze seznamu argument poskytuje hodnota. V seznamu argumentů *přesnost* argument musí předcházet hodnotu, která je formátována, jak je uvedeno v následujícím příkladu:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

*Typ* znak určuje buď výklad *přesnost* nebo výchozí přesnost při *přesnost* je vynechán, jak je znázorněno v následující tabulce.

### <a name="how-precision-values-affect-type"></a>Jak přesnosti hodnoty ovlivňují typ

|Typ|Význam|Výchozí|
|----------|-------------|-------------|
|**a**, **A**|Přesnost určuje počet číslic za bodem.|Výchozí přesnost je 13. Pokud přesnost je 0, pokud je vytištěno žádné desetinné čárky  **#**  příznak se používá.|
|**c**, **C**|Přesnost nemá žádný vliv.|Znak je vytisknout.|
|**d**, **i**, **o**, **u**, **x**, **X**|Přesnost určuje minimální počet číslic pro tisk. Pokud je počet číslic v argumentu menší než *přesnost*, je výstupní hodnotu odsazenou na levé straně nul. Hodnota není zkrácen, pokud počet číslic překročí *přesnost*.|Přesnost výchozí je 1.|
|**e**, **E**|Přesnost určuje počet číslic pro tisk za desetinnou čárkou. Se zaokrouhlí tištěných poslední číslice.|Výchozí přesnost je 6. Pokud *přesnost* je 0 nebo tečku (.) se zobrazí bez čísla následující ho, je vytištěna bez desetinné čárky.|
|**f**, **F**|Hodnota přesnosti určuje počet číslic za desetinnou čárkou. Pokud se zobrazí desetinné čárky, nejméně jednu číslici, zobrazí se před ním. Hodnota se zaokrouhlí na odpovídající počet číslic.|Výchozí přesnost je 6. Pokud *přesnost* je 0, nebo pokud tečka (.) se zobrazí bez čísla následující ho, je vytištěna bez desetinné čárky.|
|**g**, **G**|Přesnost určuje maximální počet platných číslic vytisknout.|Vytištění šest platných číslic, takže se zkrátí všechny koncové nuly.|
|**s**, **S**|Přesnost určuje maximální počet znaků k tisku. Znaky přes *přesnost* nejsou vytisknout.|Tisku znaků až do znak hodnoty null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Argument specifikace velikosti

Ve specifikaci převod *velikost* pole je modifikátor délka argument pro *typ* specifikátor převod. *Velikost* pole předpony, jež mají *typ* pole –**hh**, **h**, **j**, **l** (malá písmena L), **L**, **udou**, **t**, **w**, **z**, **I**(velká písmena i), **I32**, a **I64**– zadejte "velikost" odpovídající argument – dlouho nebo krátký, 32bitovou verzi nebo 64-bit, znakovou nebo široká znaková – v závislosti na Převod specifikátor jejich změnu. Tyto předpony velikost se používají s *typ* znaků `printf` a `wprintf` řady funkcí k určení výklad argument velikostí, jak je znázorněno v následující tabulce. *Velikost* pole je volitelné pro některé typy argumentů. Pokud je zadána žádná předpona. velikost, formátování využívá argumenty celé číslo – například podepsané nebo bez znaménka `char`, `short`, `int`, `long`, typy výčet a – jako 32bitový `int` typy, a `float`, `double`, a `long double` s plovoucí desetinnou čárkou argumenty spotřebování jako 64-bit `double` typy. To odpovídá argument povýšení výchozích pravidel pro seznam argumentů s proměnnou délkou. Další informace o povýšení argument najdete v tématu výpustky a výchozí argumenty v [výrazy přípony](../cpp/postfix-expressions.md). Na 32bitové a 64bitové systémy specifikace převod argumentu 64bitové celé číslo musí obsahovat předponu velikost **udou** nebo **I64**. Chování formátování, jinak hodnota není definován.

Některé typy jsou různé velikosti v 32bitové a 64bitové verze kódu. Například `size_t` je 32 bitů dlouho v kódu zkompilovaného pro x86 a 64 bitů v kódu zkompilovaného pro x64. Pokud chcete vytvořit formátování kódu bez ohledu na platformu pro typy proměnné šířky, můžete použít modifikátor Velikost argument proměnné šířky. Můžete taky použít modifikátor velikost 64-bit argument a explicitně povýšit typ argumentu proměnné šířky na 64 bitů. Microsoft specifické **I** (velká i) argument velikost modifikátor zpracovává argumenty proměnné šířky celé číslo, ale doporučujeme konkrétní typ **j**, **t**a **z** modifikátory pro přenositelnost.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Velikost předpon pro printf a wprintf specifikátory typ formátu

|Chcete-li určit|Použijte předponu|Pomocí specifikace typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`intmax_t`<br />`uintmax_t`|**j** nebo **I64**|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`long double`|**l** (malá písmena L) nebo **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g**, nebo **G**|
|`long int`<br />`long unsigned int`|**l** (malá písmena L)|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`long long int`<br />`unsigned long long int`|**Le** (malá písmena UDOU)|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`ptrdiff_t`|**t** nebo **I** (velká i)|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|`size_t`|**z** nebo **I** (velká i)|**d**, **i**, **o**, **u**, **x**, nebo **X**|
|Znakovou|**h**|**c** nebo **C**|
|Široké znaky|**l** (malá písmena L) nebo **w**|**c** nebo **C**|
|Řetězec o délce jednoho bajtu znaku|**h**|**s**, **S**, nebo **Z**|
|Široká charakterová řetězec|**l** (malá písmena L) nebo **w**|**s**, **S**, nebo **Z**|

`ptrdiff_t` a `size_t` typy jsou `__int32` nebo `unsigned __int32` na platformách 32bitová verze a `__int64` nebo `unsigned __int64` na 64bitových platformách. **I** (velká písmena i), **j**, **t**, a **z** velikost předpony trvat šířku správného argumentu pro platformu.

V jazyce Visual C++ i když `long double` je typu distinct má stejné interního vyjádření jako `double`.

**Hc** nebo **hC** specifikátor typu je totožná s **c** v `printf` funkce a s **C** v `wprintf` funkce. **Lc**, **lC**, **RC** nebo **RC** specifikátor typu je totožná s **C** v `printf` Funkce a s **c** v `wprintf` funkce. **Hs** nebo **hS** specifikátor typu je totožná s **s** v `printf` funkce a s **S** v `wprintf` funkce. **Ls**, **lS**, **ws** nebo **wS** specifikátor typu je totožná s **S** v `printf` Funkce a s **s** v `wprintf` funkce.

> [!NOTE]
> **Konkrétní Microsoft**  
> **I** (velká písmena i), **I32**, **I64**, a **w** argument předpony modifikátor velikost jsou rozšíření Microsoft a nejsou kompatibilní s ISO C. **h** předpony při použití s daty typu `char` a **l** (malá písmena L) předpony při použití s daty typu `double` jsou rozšíření Microsoft.

## <a name="see-also"></a>Viz také

[printf, _printf_l –, wprintf, _wprintf_l –](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
[printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)  
[printf_p – poziční parametry](../c-runtime-library/printf-p-positional-parameters.md)  