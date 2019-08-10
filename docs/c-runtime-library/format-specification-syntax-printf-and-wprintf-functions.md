---
title: 'Syntaxe specifikace formátu: funkce printf a wprintf'
ms.date: 07/30/2019
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
ms.openlocfilehash: 3ba4f91c86727986762b3431c093ee7304a3a83f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915497"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Syntaxe specifikace formátu: funkce printf a wprintf

Různé `printf` funkce a `wprintf` mají řetězec formátu a volitelné argumenty a vytvoří formátovanou sekvenci znaků pro výstup. Formátovací řetězec obsahuje nula nebo více *direktiv*, což jsou buď literálové znaky pro výstupní nebo kódované *specifikace převodu* , které popisují, jak formátovat argument ve výstupu. Tento článek popisuje syntaxi použitou ke kódování specifikace převodu v řetězci formátu. Seznam těchto funkcí najdete v tématu [vstupně-výstupní operace streamu](../c-runtime-library/stream-i-o.md).

Specifikace převodu se skládá z volitelných a povinných polí v tomto formuláři:

**%** [[*příznaky*](#flags)] [[*Šířka*](#width)] [. [*přesnost*](#precision)] [[*Velikost*](#size)] [*typ*](#type)

Každé pole specifikace převodu je znak nebo číslo, které označuje konkrétní možnost formátu nebo specifikátor převodu. Požadovaný *typ* pole určuje druh převodu, který má být použit na argument. Volitelnápole Flags, *Width*a *Precision* řídí další aspekty formátování, jako jsou například počáteční mezery nebo nuly, zdůvodnění a zobrazená přesnost. Pole *Velikost* určuje velikost spotřebovaného a převedeného argumentu.

Základní specifikace převodu obsahuje pouze znak procenta a znak *typu* . Například `%s` určuje převod řetězce. Pro výpis znaku procent je třeba použít `%%`. Je-li znak procenta následován znakem, který nemá žádný význam jako pole Format, je vyvolána obslužná rutina neplatného parametru. Další informace najdete v tématu [ověření parametru](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Pro zabezpečení a stabilitu zajistěte, aby se řetězce specifikace převodu nedefinovaly uživatelem. Zvažte například program, který vyžaduje od uživatele zadání jména a ukládá vstup do proměnné řetězce s názvem `user_name`. Pro výpis `user_name` není vhodné použít:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Místo toho je lepší použít:
>
> `printf( "%s", user_name );`

<a name="type"></a>

## <a name="type-conversion-specifier"></a>Specifikátor převodu typu

Znak specifikátoru převodu *typu* určuje, zda se má interpretovat odpovídající argument jako znak, řetězec, ukazatel, celé číslo nebo číslo s plovoucí desetinnou čárkou. Znak *typu* je jediná požadovaná pole specifikace převodu, která se zobrazí po všech volitelných polích.

Argumenty, které následují formátovací řetězec, jsou interpretovány podle odpovídajícího znaku *typu* a volitelné předpony [velikosti](#size) . Převody `char` pro typy znaků a `wchar_t` jsou určeny pomocí **jazyka c** nebo **c**a jednobajtové a vícebajtové a dvoubajtové znakové řetězce jsou určeny pomocí **s** nebo **s**v závislosti na tom, které formátování je používána funkce. Znakové a řetězcové argumenty, které jsou zadány pomocí **jazyka c** a **s** , jsou `printf` interpretovány jako `char` a `char*` funkcemi `wchar_t` rodiny nebo `wprintf` jako a `wchar_t*` podle rodinných funkcí. Znakové a řetězcové argumenty, které jsou zadány pomocí **jazyka C** a **S** , jsou `printf` interpretovány jako `wchar_t` a `wchar_t*` funkcemi `char` rodiny nebo `wprintf` jako a `char*` podle rodinných funkcí. Toto chování je specifické pro společnost Microsoft.

Celočíselné typy, jako `short`, `int`, `long`, `long long` a jejich `unsigned` variant, jsou určené pomocí **d**, **i**, **o**, **u**, **x**, a **X**. Typy s plovoucí desetinnou čárkou, jako `float`, `double`, a `long double`, jsou určené pomocí **a**, **A**, **e**, **E**, **f**, **F**, **g**, a **G**. Ve výchozím nastavení, pokud nejsou upraveny předponou *velikosti* , jsou `int` celočíselné argumenty přiřazeny typu a argumenty s plovoucí desetinnou čárkou jsou přizpůsobeny na `double`. V `int` 64 bitových systémech je hodnota 32; proto se při formátování pro výstup 64 zkrátí celá čísla, pokud není použita předpona s *velikostí* **ll** nebo **I64** . Typy ukazatelů, které jsou určeny pomocí **p** , používají pro platformu výchozí velikost ukazatele.

> [!NOTE]
> **Specifické pro společnost Microsoft** Znak typu **Z** a chování znaků **jazyka c**, **c**, **s**a **s** v případě použití s `printf` funkcemi a `wprintf` jsou rozšířeními společnosti Microsoft. Standard ISO C používá jazyky **c** a **y** konzistentně pro zúžené znaky a řetězce a jazyky **c** a **s** pro celé znaky a řetězce, a to ve všech funkcích formátování.

### <a name="type-field-characters"></a>Znaky pole typu

|Znak typu|Argument|Výstupní formát|
|--------------------|--------------|-------------------|
|**c**|Znak|Při použití s `printf` funkcemi určuje znak s jedním Byte; při použití s `wprintf` funkcemi určuje velký znak.|
|**C**|Znak|Při použití s `printf` funkcemi, určuje velký znak; při použití s `wprintf` funkcemi určuje znak s jedním Byte.|
|**d**|Integer|Desítkové celé číslo se znaménkem.|
|**i**|Integer|Desítkové celé číslo se znaménkem.|
|**o**|Integer|Osmičkové celé číslo bez znaménka.|
|**u**|Integer|Celé číslo bez znaménka.|
|**x**|Integer|Šestnáctkové celé číslo bez znaménka; používá "ABCDEF".|
|**X**|Integer|Šestnáctkové celé číslo bez znaménka; používá "ABCDEF".|
|**e**|Plovoucí desetinná čárka|Podepsaná hodnota, která má tvar [-]*d. dddd* __*DD*\[*d*], kde *d* je jedna desítková číslice, *dddd* je jedna nebo více desítkových číslic v závislosti na zadané přesnosti nebo šest ve výchozím nastavení a *DD* d] jsou dvě nebo tři desítkové číslice v závislosti na [formátu výstupu](../c-runtime-library/set-output-format.md) a velikosti exponentu. \[|
|**E**|Plovoucí desetinná čárka|Stejné jako ve formátu **e** s výjimkou, že místo **e** představuje exponent.|
|**f**|Plovoucí desetinná čárka|Podepsaná hodnota, která má tvar [-]*dddd* __.__ *dddd*, kde *dddd* je jedna nebo více desítkových číslic. Počet číslic před desetinnou čárkou závisí na velikosti čísla a počet číslic po desetinné čárkě závisí na požadované přesnosti nebo šesti ve výchozím nastavení.|
|**F**|Plovoucí desetinná čárka|Stejné jako ve formátu **f** s tím rozdílem, že nekonečno a NaN výstup je velkými písmeny.|
|**g**|Plovoucí desetinná čárka|Podepsané hodnoty se zobrazí ve formátu **f** nebo **e** , podle toho, která je pro danou hodnotu a přesnost kompaktnější. Formát **e** se používá pouze v případě, že je exponent hodnoty menší než-4 nebo větší nebo roven argumentu *přesnosti* . Koncové nuly jsou zkráceny a desetinná čárka se zobrazí pouze v případě, že se na ni bude řídit jedna nebo více číslic.|
|**G**|Plovoucí desetinná čárka|Stejné jako ve formátu **g** , s výjimkou písmene e, představuje exponent (tam, kde je to vhodné).|
|**a**|Plovoucí desetinná čárka|Podepsaná hexadecimální hodnota s dvojitou přesností a plovoucí desetinnou čárkou, která má tvar [-] 0x*h. hhhh* __. hhhh, kde *h.* jsou šestnáctkové číslice (s malými písmeny) mantisy a *DD* jsou jedna nebo více číslic pro zmocněn. Přesnost určuje počet číslic za bodem.|
|**A**|Plovoucí desetinná čárka|Podepsaná hexadecimální hodnota s dvojitou přesností a plovoucí desetinnou čárkou, která má tvar [-] 0X*h. hhhh* __. hhhh, kde *h.* jsou šestnáctkové číslice (s velkými písmeny) mantisy a *DD* jsou jedna nebo více číslic pro exponent. . Přesnost určuje počet číslic za bodem.|
|**n**|Ukazatel na celé číslo|Počet znaků, které byly dosud úspěšně zapsány do datového proudu nebo vyrovnávací paměti. Tato hodnota je uložena v celé číslo, jehož adresa je uvedena jako argument. Velikost celého čísla, na které se odkazuje, se dá řídit předponou specifikace velikosti argumentu. Specifikátor **n** je ve výchozím nastavení zakázaný. informace najdete v důležité poznámce zabezpečení.|
|**p**|Typ ukazatele|Zobrazí argument jako adresu v šestnáctkových číslicích.|
|**s**|String|Při použití s `printf` funkcemi Určuje jeden bajt nebo vícebajtový řetězec znaků; při použití s `wprintf` funkcemi určuje řetězec s velkým znakem. Znaky jsou zobrazeny až do prvního znaku null nebo do dosažení hodnoty *přesnosti* .|
|**S**|String|Při použití s `printf` funkcemi určuje řetězec s velkým znakem; při použití s `wprintf` funkcemi určuje jednobajtové nebo dvoubajtové znakové řetězce. Znaky jsou zobrazeny až do prvního znaku null nebo do dosažení hodnoty *přesnosti* .|
|**Z**|`ANSI_STRING`nebo `UNICODE_STRING` struktura|Když je adresa struktury [ANSI_STRING](/windows/desktop/api/ntdef/ns-ntdef-string) nebo [UNICODE_STRING](/windows/win32/api/ntdef/ns-ntdef-_unicode_string) předána jako argument, zobrazuje řetězec obsažený ve vyrovnávací paměti, `Buffer` na kterou odkazuje pole struktury. Použijte předponu modifikátoru velikosti **w** `UNICODE_STRING` pro určení argumentu – například. `%wZ` `Length` Pole struktury musí být nastaveno na délku řetězce v bajtech. `MaximumLength` Pole struktury musí být nastavené na délku vyrovnávací paměti (v bajtech).<br /><br /> Obvykle se znak typu **z** používá pouze v ladicích funkcích ovladače, které používají specifikaci převodu, jako `dbgPrint` je například a. `kdPrint`|

Od verze sady Visual Studio 2015, pokud argument, který odpovídá specifikátor převody plovoucí desetinné čárky (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) je nekonečné neomezené, nebo NaN, formátovaný výstup vyhovuje C99 standard. V této tabulce je uveden formátovaný výstup:

|Value|Výstup|
|-----------|------------|
|konečný|`inf`|
|Tiché NaN|`nan`|
|Signalizace – NaN|`nan(snan)`|
|Nekonečný NaN|`nan(ind)`|

Kterákoli z těchto hodnot může být předponou. Pokud je znak konverze *typu* s plovoucí desetinnou čárkou velké písmeno, výstup je také zformátován velkými písmeny. Například pokud je `%F` specifikátor formátu `%f`namísto, `inf`je nekonečno naformátováno jako `INF` místo. Funkce mohou také analyzovat tyto řetězce, takže tyto hodnoty mohou vytvořit kruhové `printf` odezvy a `scanf` funkce. `scanf`

Před Visual Studio 2015 se CRT používal jiný nestandardní formát pro výstup nekonečných, nekonečných a NaN hodnot:

|Value|Výstup|
|-----------|------------|
|+ nekonečno|`1.#INF`*náhodné číslice*|
|– nekonečno|`-1.#INF`*náhodné číslice*|
|Neomezeno (stejné jako tiché NaN)|*číslice* `.#IND` *náhodné číslice*|
|NaN|*číslice* `.#NAN` *náhodné číslice*|

Některé z nich mohou být označeny znaménkem a mohou být mírně formátovány v závislosti na šířce a přesnosti pole, někdy u neobvyklých efektů. Například by byl `printf("%.2f\n", INFINITY)` vytištěn `1.#J` , protože #INF by byl "zaokrouhleno" na 2 číslice přesnosti.

> [!NOTE]
> Pokud argument, který `%s` odpovídá nebo `%S`, nebo `Buffer` `%Z`pole argumentu, který odpovídá, je zobrazen ukazatel s hodnotou null (hodnota null).

> [!NOTE]
> Ve všech exponenciálních formátech je minimální počet číslic exponentu k zobrazení dva a v případě potřeby pouze tři. Pomocí funkce [_set_output_format](../c-runtime-library/set-output-format.md) můžete nastavit počet číslic zobrazených na tři pro zpětnou kompatibilitu s kódem napsaným pro Visual Studio 2013 a před.

> [!IMPORTANT]
> Vzhledem k `%n` tomu, že tento formát je z podstaty nezabezpečený, je ve výchozím nastavení zakázán. Pokud `%n` je nalezen ve formátovacím řetězci, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../c-runtime-library/parameter-validation.md). Pokud chcete `%n` povolit podporu, přečtěte si téma [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Direktivy Flag

První volitelné pole ve specifikaci převodu obsahuje direktivy *příznaků*, nula nebo více znaků označení, které určují výstup odůvodnění a řízení výstupů značek, prázdných, počátečních nul, desetinných míst a osmičkových a šestnáctkových předpon. Ve specifikaci převodu se může vyskytovat více než jedna direktiva příznaku a znaky příznaku se mohou zobrazit v libovolném pořadí.

### <a name="flag-characters"></a>Znaky příznaku

|Příznak|Význam|Výchozí|
|----------|-------------|-------------|
|**-**|Vlevo zarovná výsledek v rámci dané šířky pole.|Zarovnat doprava.|
|**+**|Použijte znaménko (+ nebo-) k označení výstupní hodnoty, pokud se jedná o typ se znaménkem.|Znaménko se zobrazí pouze pro záporné hodnoty se znaménkem (-).|
|**0**|Pokud je *Šířka* předpona **0**, jsou přidány počáteční nuly, dokud není dosaženo minimální šířky. Pokud oba **0** a **-** se zobrazí, **0** je ignorována. Je-li **hodnota 0** zadána pro celočíselný formát (**i**, **u**, **x**, **x**, **o**, **d**) a specifikace přesnosti, například, `%04.d`je **hodnota 0** ignorována. Pokud **0** pro je zadána **a** nebo **A** s plovoucí desetinnou čárkou formátu úvodní nuly se přidá jako předpona k mantisa, po `0x` nebo `0X` předponu.|Bez odsazení.|
|**prázdné** (' ')|Použijte prázdnou pro vytvoření předpony výstupní hodnoty, pokud je podepsaná a kladná. Prázdné pole se ignoruje, pokud se objeví prázdné a + příznaky.|Nezobrazí se žádné prázdné znaky.|
|**#**|Pokud se používá s formátem **o**, **x**nebo **#** **x** , příznak používá 0, 0x nebo 0x pro předponu libovolné nenulové výstupní hodnoty.|Nezobrazí se žádné prázdné znaky.|
||Pokud se používá s formátem **e**, **e**, **f**, **f**, **a**nebo, **#** příznak vynutí, aby výstupní hodnota obsahovala desetinnou čárku.|Desetinná čárka se zobrazí pouze v případě, že následují číslice.|
||Pokud se používá ve **#** formátu **g** nebo **g** , příznak vynutí, aby výstupní hodnota obsahovala desetinnou čárku a zabránila zkrácení koncových nul.<br /><br /> Ignoruje se, pokud se používá v jazyce **c**, **d**, **i**, **u**nebo **s**.|Desetinná čárka se zobrazí pouze v případě, že následují číslice. Koncové nuly jsou zkráceny.|

<a name="width"></a>

## <a name="width-specification"></a>Specifikace šířky

Ve specifikaci převodu se pole volitelná šířka zobrazí za znaky *příznaků* . Argument *Width* je nezáporné celé číslo bez znaménka, které určuje minimální počet znaků, které jsou výstupem. Pokud je počet znaků ve výstupní hodnotě menší než zadaná šířka, prázdné znaky jsou přidány vlevo nebo vpravo od hodnot – v závislosti na tom, zda je zadána příznak zarovnání vlevo ( **-** ), dokud není dosaženo minimální šířky. Pokud je *Šířka* Předpona 0, jsou počáteční nuly přidány do celočíselného nebo plovoucího převodu, dokud není dosaženo minimální šířky, s výjimkou, kdy je převod na nekonečno nebo NaN.

Specifikace šířky nikdy nezpůsobí zkrácení hodnoty. Je-li počet znaků ve výstupní hodnotě větší, než je zadaná šířka, nebo pokud není zadána *Šířka* , jsou všechny znaky hodnoty výstupem v souladu se specifikací *přesnosti* .

Pokud je specifikace šířky hvězdička (`*`) `int` , argument ze seznamu argumentů dodá hodnotu. Argument *Width* musí předcházet hodnotě, která je naformátována v seznamu argumentů, jak je znázorněno v následujícím příkladu:

`printf("%0*d", 5, 3);  /* 00003 is output */`

Chybějící nebo malá hodnota *šířky* ve specifikaci převodu nezpůsobí zkrácení výstupní hodnoty. Pokud je výsledek převodu širší než hodnota *Width* , pole se rozšíří, aby obsahovalo výsledek převodu.

<a name="precision"></a>

## <a name="precision-specification"></a>Specifikace přesnosti

Ve specifikaci převodu je třetí volitelné pole specifikací přesnosti. Skládá se z tečky (.) následovaný nezáporným desítkovým číslem, které v závislosti na typu převodu určuje počet řetězcových znaků, počet desetinných míst nebo počet platných číslic, které mají být výstupem.

Na rozdíl od specifikace šířky může specifikace přesnosti způsobit buď zkracování výstupní hodnoty, nebo zaokrouhlení hodnoty s plovoucí desetinnou čárkou. Pokud je *přesnost* zadána jako 0 a hodnota, která má být převedena, je 0, výsledek není výstupní znaky, jak je znázorněno v následujícím příkladu:

`printf( "%.0d", 0 );      /* No characters output */`

Pokud je specifikace přesnosti hvězdičkou (\*) `int` , argument ze seznamu argumentů dodá hodnotu. V seznamu argumentů musí argument *přesnost* předcházet hodnotě, která je formátována, jak je znázorněno v následujícím příkladu:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Znak *typu* Určuje buď výklad *přesnosti* , nebo výchozí přesnost, pokud je vynechána *přesnost* , jak je znázorněno v následující tabulce.

### <a name="how-precision-values-affect-type"></a>Vliv hodnot přesnosti na typ

|type|Význam|Výchozí|
|----------|-------------|-------------|
|**a**, **A**|Přesnost určuje počet číslic za bodem.|Výchozí přesnost je 13. Pokud je přesnost 0, není vytištěna desetinná čárka **#** , pokud se nepoužije příznak.|
|**c**, **C**|Přesnost nemá žádný vliv.|Znak je vytištěn.|
|**d**, **i**, **o**, **u**, **x**, **X**|Přesnost určuje minimální počet číslic, které mají být vytištěny. Je-li počet číslic v argumentu menší než *přesnost*, je výstupní hodnota odsazena vlevo s nulami. Hodnota není zkrácena v případě, že počet číslic překračuje *přesnost*.|Výchozí přesnost je 1.|
|**e**, **E**|Přesnost určuje počet číslic, které mají být vytištěny po desetinné místo. Poslední vytištěná číslice je zaokrouhlena.|Výchozí přesnost je 6. Pokud je *přesnost* 0 nebo tečka (.) se zobrazí bez čísla za ní, není vytištěna žádná desetinná čárka.|
|**f**, **F**|Hodnota přesnosti určuje počet číslic za desetinnou čárkou. Pokud se zobrazí desetinná čárka, před ní se zobrazí alespoň jedna číslice. Hodnota je zaokrouhlena na příslušný počet číslic.|Výchozí přesnost je 6. Pokud je *přesnost* 0, nebo pokud se tečka (.) objeví bez čísla za ní, není vytištěna žádná desetinná čárka.|
|**g**, **G**|Přesnost určuje maximální počet platných číslic, které se vytisknou.|Vytiskne se šest platných číslic a všechny koncové nuly se zkrátí.|
|**s**, **S**|Přesnost určuje maximální počet znaků, které mají být vytištěny. Znaky přesahující *přesnost* nejsou vytištěny.|Znaky jsou vytištěny, dokud není zjištěn znak null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Specifikace velikosti argumentu

Ve specifikaci převodu pole *Size* je modifikátor délky argumentu pro specifikátor převodu *typu* . Pole *Velikost* předpony na pole *typ* –**HH**, **h**, **j**, **l** (malá l), **l**, **ll**, **t**, **w**, **z**, **I** (velká písmena i), **i32**a **I64** – Určete "velikost" odpovídajícího argumentu – dlouhý nebo krátký, 32 nebo 64 bajtový znak nebo velký znak – v závislosti na specifikátoru převodu, který upravují. Tyto předpony velikosti se používají s znaky *typu* v rámci `printf` řady `wprintf` funkcí a k určení interpretace velikostí argumentů, jak je znázorněno v následující tabulce. Pole *Size* je pro některé typy argumentů volitelné. Pokud není zadána žádná předpona velikosti, formátovací modul spotřebovává celočíselné argumenty, například signed nebo unsigned `char`, `short`, `int` `long`,, a výčtové typy, jako 32 `int` typy a `float`, a argumenty s plovoucí desetinnou čárkou jsou spotřebovány jako typy 64-bit `double`. `double` `long double` Toto chování odpovídá výchozím pravidlům pro povýšení argumentů pro seznamy argumentů proměnných. Další informace o povýšení argumentů naleznete v tématu elipsy a výchozí argumenty ve [výrazech přípony](../cpp/postfix-expressions.md). V systémech 32 a 64 musí specifikace převodu argumentu celočíselné hodnoty 64 obsahovat předponu Size s hodnotou **ll** nebo **I64**. V opačném případě chování formátovacího modulu není definováno.

Některé typy jsou různé velikosti v 32 a 64 bitového kódu. Například `size_t` je 32 bitů dlouhý v kódu kompilovaném pro x86 a 64 bitů v kódu zkompilovaném pro x64. Chcete-li vytvořit kód pro formátování Platform-nezávislá pro typy s proměnlivou šířkou, můžete použít modifikátor velikosti argumentu proměnné šířky. Alternativně použijte modifikátor velikosti 64 bitového argumentu a explicitně zvyšte úroveň typu argumentu s proměnnou šířkou na 64 bitů. Modifikátor velikosti argumentu specifického pro Microsoft **i** (velká i malá) zpracovává celočíselné argumenty proměnné šířky, ale pro přenositelnost doporučujeme použít Modifikátory specifické pro typ **j**, **t**a **z** .

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Předpony velikosti pro specifikátory typu printf a wprintf formátu

|Zadání|Použít předponu|Se specifikátorem typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`short int`<br />`short unsigned int`|**h**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`intmax_t`<br />`uintmax_t`|**j** nebo **I64**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`long double`|**l** (malé písmeno l) nebo **l**|**a**, **A**, **e**, **E**, **f**, **F**, **g**, nebo **G**|
|`long int`<br />`long unsigned int`|**l** (malé písmeno l)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`long long int`<br />`unsigned long long int`|**vše** (malé písmeno ll)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`ptrdiff_t`|**t** nebo **I** (velká písmena I)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`size_t`|**z** nebo **I** (velká písmena i)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|Jednobajtové znak|**h**|**c** nebo **c**|
|Velký znak|**l** (malé písmeno l) nebo **w**|**c** nebo **c**|
|Jednobajtové znakové řetězce|**h**|**s**, **s**nebo **Z**|
|Řetězec s velkým znakem|**l** (malé písmeno l) nebo **w**|**s**, **s**nebo **Z**|

`ptrdiff_t` Typy a `size_t` jsou nebona`unsigned __int32` 32 a`__int64` na 64`unsigned __int64`platformách. `__int32` Předpony velikost **i** (velká i), **j**, **t**a **z** mají pro platformu správnou šířku argumentu.

V jazyce C++Visual, `long double` i když je odlišný typ, má stejnou vnitřní reprezentaci jako `double`.

Specifikátor **typu HC** nebo **HC** je synonymum s **c** `printf` ve funkcích a s **c** v `wprintf` Functions. Specifikátor typu **LC**, **LC**, **WC**nebo **WC** je synonymum s **c** ve `printf` funkcích a s **c** v `wprintf` Functions. Specifikátor **typu HS** nebo **HS** je synonymum s ve `printf` funkcích a s s v `wprintf` funkce. Specifikátor typu **ls**, **ls**, **WS** nebo **WS** je synonymum s **s** ve `printf` funkcích a s s v `wprintf` funkce.

> [!NOTE]
> **Specifické pro společnost Microsoft** **I** (velká písmena i), **i32**, **I64**a **w** argumenty modifikátoru velikosti ARGUMENTŮ jsou rozšíření Microsoft a nejsou kompatibilní s ISO C. Předpona **h** , pokud se používá s daty typu `char` a předponou **l** (v malých l), pokud se používá s daty typu `double` jsou rozšíření společnosti Microsoft.

## <a name="see-also"></a>Viz také:

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[printf_p – poziční parametry](../c-runtime-library/printf-p-positional-parameters.md)
