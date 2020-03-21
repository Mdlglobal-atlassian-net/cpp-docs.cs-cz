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
ms.openlocfilehash: c5cd93607f8e5a892d789dcb6aeef934f8936dad
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078049"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Syntaxe specifikace formátu: funkce printf a wprintf

Různé funkce `printf` a `wprintf` přebírají řetězec formátu a volitelné argumenty a vytvoří formátovanou sekvenci znaků pro výstup. Formátovací řetězec obsahuje nula nebo více *direktiv*, což jsou buď literálové znaky pro výstupní nebo kódované *specifikace převodu* , které popisují, jak formátovat argument ve výstupu. Tento článek popisuje syntaxi použitou ke kódování specifikace převodu v řetězci formátu. Seznam těchto funkcí najdete v tématu [vstupně-výstupní operace streamu](../c-runtime-library/stream-i-o.md).

Specifikace převodu se skládá z volitelných a povinných polí v tomto formuláři:

**%** [[*Flags*](#flags)] [[*Width*](#width)] [.[ *Precision*](#precision)] [[*Size*](#size)] –[*typ*](#type)

Každé pole specifikace převodu je znak nebo číslo, které označuje konkrétní možnost formátu nebo specifikátor převodu. Požadovaný *typ* pole určuje druh převodu, který má být použit na argument. Volitelná pole *Flags*, *Width*a *Precision* řídí další aspekty formátování, jako jsou například počáteční mezery nebo nuly, zdůvodnění a zobrazená přesnost. Pole *Velikost* určuje velikost spotřebovaného a převedeného argumentu.

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

> [!NOTE]
> V aplikaci Visual Studio 2015 `printf` a `scanf` rodina funkcí byly deklarovány jako **inline** a přesunuty do hlaviček `<stdio.h>` a `<conio.h>`. Pokud migrujete starší kód, může se v souvislosti s těmito funkcemi zobrazit *linkerů LNK2019* . Další informace najdete v tématu [o C++ historii vizuálních změn 2003 – 2015](../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

## <a name="type-conversion-specifier"></a>Specifikátor převodu typu

Znak specifikátoru převodu *typu* určuje, zda se má interpretovat odpovídající argument jako znak, řetězec, ukazatel, celé číslo nebo číslo s plovoucí desetinnou čárkou. Znak *typu* je jediná požadovaná pole specifikace převodu, která se zobrazí po všech volitelných polích.

Argumenty, které následují formátovací řetězec, jsou interpretovány podle odpovídajícího znaku *typu* a volitelné předpony [velikosti](#size) . Převody pro typy znaků `char` a `wchar_t` jsou zadány pomocí **jazyka c** nebo **c**a jednobajtové a vícebajtové nebo velké znakové řetězce jsou určeny pomocí **s** nebo **s**v závislosti na tom, která funkce formátování je používána. Znakové a řetězcové argumenty, které jsou určeny pomocí **jazyka c** a **s** , jsou interpretovány jako `char` a `char*` funkcí `printf` rodin nebo jako `wchar_t` a `wchar_t*` funkcemi řady `wprintf`. Znakové a řetězcové argumenty, které jsou určeny pomocí **jazyka C** a **S** , jsou interpretovány jako `wchar_t` a `wchar_t*` funkcí `printf` rodin nebo jako `char` a `char*` funkcemi řady `wprintf`. Toto chování je specifické pro společnost Microsoft.

Celočíselné typy, jako `short`, `int`, `long`, `long long`a jejich `unsigned` varianty, jsou určeny pomocí **d**, **i**, **o**, **u**, **x**a **x**. Typy s plovoucí desetinnou čárkou, jako jsou `float`, `double`a `long double`, jsou určeny pomocí **a** **, a,** **e**, **e**, **f**, **f**, **g**a **g**. Ve výchozím nastavení, pokud nejsou upraveny předponou *velikosti* , jsou celočíselné argumenty přizpůsobeny `int` typu a argumenty s plovoucí desetinnou čárkou jsou převedeny na `double`. V 64 systémech je `int` hodnotou 32; Proto budou při formátování pro výstup zkrácená celá čísla 64, pokud se nepoužije předpona *Size* s hodnotou **ll** nebo **I64** . Typy ukazatelů, které jsou určeny pomocí **p** , používají pro platformu výchozí velikost ukazatele.

> [!NOTE]
> **Specifické pro společnost Microsoft:** Znak typu **Z** a chování znaků typu **c**, **c**, **s**a **s** , pokud jsou použity s funkcemi `printf` a `wprintf`, jsou rozšířením společnosti Microsoft. Standard ISO C používá jazyky **c** a **y** konzistentně pro zúžené znaky a řetězce a jazyky **c** a **s** pro celé znaky a řetězce, a to ve všech funkcích formátování.

### <a name="type-field-characters"></a>Znaky pole typu

|Znak typu|Argument|Výstupní formát|
|--------------------|--------------|-------------------|
|**r**|Znak|Při použití s funkcemi `printf` určuje jednobajtové znak; Při použití s funkcí `wprintf` určuje velký znak.|
|**C**|Znak|Při použití s funkcí `printf` určuje velký znak; Při použití s funkcemi `wprintf` určuje jednobajtové znak.|
|**trojrozměrné**|Integer|Desítkové celé číslo se znaménkem.|
|**došlo**|Integer|Desítkové celé číslo se znaménkem.|
|**zápis**|Integer|Osmičkové celé číslo bez znaménka.|
|**h**|Integer|Celé číslo bez znaménka.|
|**znak**|Integer|Šestnáctkové celé číslo bez znaménka; používá "ABCDEF".|
|**Znak**|Integer|Šestnáctkové celé číslo bez znaménka; používá "ABCDEF".|
|**cerebrální**|Plovoucí desetinná čárka|Podepsaná hodnota, která má formu [-]*d. dddd*__e__ *-* \[*d*], kde *d* je jedna desítková číslice, *dddd* je jedna nebo více desítkových číslic v závislosti na zadané přesnosti nebo šest ve výchozím nastavení a *DD*\[*d*] je dvě nebo tři desítkové číslice v závislosti na [formátu výstupu](../c-runtime-library/set-output-format.md) a velikosti exponentu.|
|**Cerebrální**|Plovoucí desetinná čárka|Stejné jako ve formátu **e** **s výjimkou, že** místo **e** představuje exponent.|
|**FJ**|Plovoucí desetinná čárka|Podepsaná hodnota, která má tvar [-]*dddd* __.__ *dddd*, kde *dddd* je jedna nebo více desítkových číslic. Počet číslic před desetinnou čárkou závisí na velikosti čísla a počet číslic po desetinné čárkě závisí na požadované přesnosti nebo šesti ve výchozím nastavení.|
|**FJ**|Plovoucí desetinná čárka|Stejné jako ve formátu **f** s tím rozdílem, že nekonečno a NaN výstup je velkými písmeny.|
|**věcn**|Plovoucí desetinná čárka|Podepsané hodnoty se zobrazí ve formátu **f** nebo **e** , podle toho, která je pro danou hodnotu a přesnost kompaktnější. Formát **e** se používá pouze v případě, že je exponent hodnoty menší než-4 nebo větší nebo roven argumentu *přesnosti* . Koncové nuly jsou zkráceny a desetinná čárka se zobrazí pouze v případě, že se na ni bude řídit jedna nebo více číslic.|
|**Věcn**|Plovoucí desetinná čárka|Stejné jako ve formátu **g** , s výjimkou písmene e **,** představuje exponent ( **tam, kde**je to vhodné).|
|**určitého**|Plovoucí desetinná čárka|Podepsaná hexadecimální hodnota s dvojitou přesností a plovoucí desetinnou čárkou, která má tvar [-] 0x*h. hhhh*__p__. hhhh *, kde* *h.* jsou šestnáctkové číslice (s malými písmeny) mantisy a *DD* jsou jedna nebo více číslic pro exponent. Přesnost určuje počet číslic za bodem.|
|**Určitého**|Plovoucí desetinná čárka|Podepsaná hexadecimální hodnota s dvojitou přesností a plovoucí desetinnou čárkou, která má tvar [-] 0X*h. hhhh*__P__. hhhh *, kde* *h.* jsou šestnáctkové číslice (s velkými písmeny) mantisy a *DD* jsou jedna nebo více číslic pro exponent. Přesnost určuje počet číslic za bodem.|
|**n**|Ukazatel na celé číslo|Počet znaků, které byly dosud úspěšně zapsány do datového proudu nebo vyrovnávací paměti. Tato hodnota je uložena v celé číslo, jehož adresa je uvedena jako argument. Velikost celého čísla, na které se odkazuje, se dá řídit předponou specifikace velikosti argumentu. Specifikátor **n** je ve výchozím nastavení zakázaný. informace najdete v důležité poznámce zabezpečení.|
|**trub**|Typ ukazatele|Zobrazí argument jako adresu v šestnáctkových číslicích.|
|**pracují**|Řetězec|Při použití s funkcemi `printf` určuje jednobajtové nebo vícebajtový řetězec znaků; Při použití s funkcemi `wprintf` určuje řetězec s velkým znakem. Znaky jsou zobrazeny až do prvního znaku null nebo do dosažení hodnoty *přesnosti* .|
|**Pracují**|Řetězec|Při použití s funkcemi `printf` určuje řetězec s velkým znakem; Při použití s funkcemi `wprintf` určuje jednobajtové nebo vícebajtový řetězec znaků. Znaky jsou zobrazeny až do prvního znaku null nebo do dosažení hodnoty *přesnosti* .|
|**Od**|struktura `ANSI_STRING` nebo `UNICODE_STRING`|Když je adresa [ANSI_STRING](/windows/win32/api/ntdef/ns-ntdef-string) nebo struktury [UNICODE_STRING](/windows/win32/api/ntdef/ns-ntdef-_unicode_string) předána jako argument, zobrazí řetězec obsažený ve vyrovnávací paměti, na které ukazuje pole `Buffer` struktury. Použijte předponu modifikátoru *velikosti* **w** pro určení argumentu `UNICODE_STRING`, například `%wZ`. Pole `Length` struktury musí být nastavené na délku řetězce v bajtech. Pole `MaximumLength` struktury musí být nastavené na délku vyrovnávací paměti (v bajtech).<br /><br /> Obvykle se znak typu **z** používá pouze v ladicích funkcích ovladače, které používají specifikaci převodu, například `dbgPrint` a `kdPrint`.|

Počínaje verzí Visual Studio 2015, pokud argument, který odpovídá specifikátoru převodu s plovoucí desetinnou čárkou(a **, a,** **e**, **e**, **f**, **f**, **g**, **g**), je nekonečný, nekonečný nebo NaN, formátovaný výstup odpovídá standardu C99. V této tabulce je uveden formátovaný výstup:

|Hodnota|Výstup|
|-----------|------------|
|konečný|`inf`|
|Tiché NaN|`nan`|
|Signalizace – NaN|`nan(snan)`|
|Nekonečný NaN|`nan(ind)`|

Kterákoli z těchto hodnot může být předponou. Pokud je znak konverze *typu* s plovoucí desetinnou čárkou velké písmeno, výstup je také zformátován velkými písmeny. Například pokud je specifikátor formátu `%F` namísto `%f`, je nekonečno formátováno jako `INF` namísto `inf`. `scanf` funkce mohou také analyzovat tyto řetězce, takže tyto hodnoty mohou vytvořit kulatou cestu prostřednictvím `printf` a `scanf` funkcí.

Před Visual Studio 2015 se CRT používal jiný nestandardní formát pro výstup nekonečných, nekonečných a NaN hodnot:

|Hodnota|Výstup|
|-----------|------------|
|+ nekonečno|`1.#INF` *náhodných číslic*|
|– nekonečno|`-1.#INF` *náhodných číslic*|
|Neomezeno (stejné jako tiché NaN)|*číslice* `.#IND` *náhodnými číslicemi*|
|NaN|*číslice* `.#NAN` *náhodnými číslicemi*|

Některé z nich mohou být označeny znaménkem a mohou být mírně formátovány v závislosti na šířce a přesnosti pole, někdy u neobvyklých efektů. `printf("%.2f\n", INFINITY)` například vytiskne `1.#J`, protože #INF "zaokrouhlit" na 2 číslice přesnosti.

> [!NOTE]
> Pokud je argument, který odpovídá `%s` nebo `%S`, nebo pole `Buffer` argumentu, který odpovídá `%Z`, je zobrazen ukazatel s hodnotou null (hodnota null).

> [!NOTE]
> Ve všech exponenciálních formátech je minimální počet číslic exponentu k zobrazení dva a v případě potřeby pouze tři. Pomocí funkce [_set_output_format](../c-runtime-library/set-output-format.md) můžete nastavit počet číslic zobrazených na tři pro zpětnou kompatibilitu s kódem napsaným pro Visual Studio 2013 a před.

> [!IMPORTANT]
> Protože formát `%n` je ze své podstaty nezabezpečený, je ve výchozím nastavení zakázaný. Pokud je ve formátovacím řetězci zjištěna `%n`, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../c-runtime-library/parameter-validation.md). Pokud chcete povolit podporu `%n`, přečtěte si téma [_set_printf_count_output](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Direktivy Flag

První volitelné pole ve specifikaci převodu obsahuje *direktivy příznaků*, nula nebo více znaků označení, které určují výstup odůvodnění a řízení výstupů značek, prázdných, počátečních nul, desetinných míst a osmičkových a šestnáctkových předpon. Ve specifikaci převodu se může vyskytovat více než jedna direktiva příznaku a znaky příznaku se mohou zobrazit v libovolném pořadí.

### <a name="flag-characters"></a>Znaky příznaku

|Příznak|Význam|Výchozí|
|----------|-------------|-------------|
|**-**|Vlevo zarovná výsledek v rámci dané šířky pole.|Zarovnat doprava.|
|**+**|Použijte znaménko (+ nebo-) k označení výstupní hodnoty, pokud se jedná o typ se znaménkem.|Znaménko se zobrazí pouze pro záporné hodnoty se znaménkem (-).|
|**0**|Pokud je *Šířka* předpona **0**, jsou přidány počáteční nuly, dokud není dosaženo minimální šířky. Pokud se zobrazí jak **0** , tak **-** , **hodnota 0** se ignoruje. Je-li **hodnota 0** zadána pro celočíselný formát (**i**, **u**, **x**, **x**, **o**, **d**) a specifikace přesnosti, například `%04.d`– **hodnota 0** je ignorována. Je-li **hodnota 0** zadána pro formát **a** nebo **s** plovoucí desetinnou čárkou, jsou počáteční nuly před předponou `0x` nebo `0X` předpony do mantisy.|Bez odsazení.|
|**prázdné** (' ')|Použijte prázdnou pro vytvoření předpony výstupní hodnoty, pokud je podepsaná a kladná. Prázdné pole se ignoruje, pokud se objeví prázdné a + příznaky.|Nezobrazí se žádné prázdné znaky.|
|**#**|Pokud se používá s formátem **o**, **x**nebo **x** , příznak **#** používá 0, 0x nebo 0x pro předponu libovolné nenulové výstupní hodnoty.|Nezobrazí se žádné prázdné znaky.|
||Pokud se používá s formátem **e**, **e**, **f**, **f**, **a**nebo, **#** příznak vynutí, aby výstupní hodnota obsahovala desetinnou čárku.|Desetinná čárka se zobrazí pouze v případě, že následují číslice.|
||Pokud se používá ve formátu **g** nebo **g** , **#** příznak vynutí, aby výstupní hodnota obsahovala desetinnou čárku a zabránila zkrácení koncových nul.<br /><br /> Ignoruje se, pokud se používá v jazyce **c**, **d**, **i**, **u**nebo **s**.|Desetinná čárka se zobrazí pouze v případě, že následují číslice. Koncové nuly jsou zkráceny.|

<a name="width"></a>

## <a name="width-specification"></a>Specifikace šířky

Ve specifikaci převodu se pole volitelná šířka zobrazí za znaky *příznaků* . Argument *Width* je nezáporné celé číslo bez znaménka, které určuje minimální počet znaků, které jsou výstupem. Pokud je počet znaků ve výstupní hodnotě menší, než je zadaná šířka, prázdné hodnoty jsou přidány vlevo nebo vpravo od hodnot – v závislosti na tom, zda je zadán příznak zarovnání vlevo ( **-** ), dokud není dosaženo minimální šířky. Pokud je *Šířka* Předpona 0, jsou počáteční nuly přidány do celočíselného nebo plovoucího převodu, dokud není dosaženo minimální šířky, s výjimkou, kdy je převod na nekonečno nebo NaN.

Specifikace šířky nikdy nezpůsobí zkrácení hodnoty. Je-li počet znaků ve výstupní hodnotě větší, než je zadaná šířka, nebo pokud není zadána *Šířka* , jsou všechny znaky hodnoty výstupem v souladu se specifikací *přesnosti* .

Pokud je specifikace šířky hvězdička (`*`), `int` argument ze seznamu argumentů dodá hodnotu. Argument *Width* musí předcházet hodnotě, která je naformátována v seznamu argumentů, jak je znázorněno v následujícím příkladu:

`printf("%0*d", 5, 3);  /* 00003 is output */`

Chybějící nebo malá hodnota *šířky* ve specifikaci převodu nezpůsobí zkrácení výstupní hodnoty. Pokud je výsledek převodu širší než hodnota *Width* , pole se rozšíří, aby obsahovalo výsledek převodu.

<a name="precision"></a>

## <a name="precision-specification"></a>Specifikace přesnosti

Ve specifikaci převodu je třetí volitelné pole specifikací přesnosti. Skládá se z tečky (.) následovaný nezáporným desítkovým číslem, které v závislosti na typu převodu určuje počet řetězcových znaků, počet desetinných míst nebo počet platných číslic, které mají být výstupem.

Na rozdíl od specifikace šířky může specifikace přesnosti způsobit buď zkracování výstupní hodnoty, nebo zaokrouhlení hodnoty s plovoucí desetinnou čárkou. Pokud je *přesnost* zadána jako 0 a hodnota, která má být převedena, je 0, výsledek není výstupní znaky, jak je znázorněno v následujícím příkladu:

`printf( "%.0d", 0 );      /* No characters output */`

Pokud je specifikace přesnosti hvězdičkou (\*), `int` argument ze seznamu argumentů dodá hodnotu. V seznamu argumentů musí argument *přesnost* předcházet hodnotě, která je formátována, jak je znázorněno v následujícím příkladu:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

Znak *typu* Určuje buď výklad *přesnosti* , nebo výchozí přesnost, pokud je vynechána *přesnost* , jak je znázorněno v následující tabulce.

### <a name="how-precision-values-affect-type"></a>Vliv hodnot přesnosti na typ

|Typ|Význam|Výchozí|
|----------|-------------|-------------|
|**a**, **a**|Přesnost určuje počet číslic za bodem.|Výchozí přesnost je 13. Pokud je přesnost 0, není vytištěna desetinná čárka, pokud se nepoužije příznak **#** .|
|**c**, **c**|Přesnost nemá žádný vliv.|Znak je vytištěn.|
|**d**, **i**, **o**, **u**, **x**, **x**|Přesnost určuje minimální počet číslic, které mají být vytištěny. Je-li počet číslic v argumentu menší než *přesnost*, je výstupní hodnota odsazena vlevo s nulami. Hodnota není zkrácena v případě, že počet číslic překračuje *přesnost*.|Výchozí přesnost je 1.|
|**e**, **e**|Přesnost určuje počet číslic, které mají být vytištěny po desetinné místo. Poslední vytištěná číslice je zaokrouhlena.|Výchozí přesnost je 6. Pokud je *přesnost* 0 nebo tečka (.) se zobrazí bez čísla za ní, není vytištěna žádná desetinná čárka.|
|**f**, **f**|Hodnota přesnosti určuje počet číslic za desetinnou čárkou. Pokud se zobrazí desetinná čárka, před ní se zobrazí alespoň jedna číslice. Hodnota je zaokrouhlena na příslušný počet číslic.|Výchozí přesnost je 6. Pokud je *přesnost* 0, nebo pokud se tečka (.) objeví bez čísla za ní, není vytištěna žádná desetinná čárka.|
|**g**, **g**|Přesnost určuje maximální počet platných číslic, které se vytisknou.|Vytiskne se šest platných číslic a všechny koncové nuly se zkrátí.|
|**s**, **s**|Přesnost určuje maximální počet znaků, které mají být vytištěny. Znaky přesahující *přesnost* nejsou vytištěny.|Znaky jsou vytištěny, dokud není zjištěn znak null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Specifikace velikosti argumentu

Ve specifikaci převodu pole *Size* je modifikátor délky argumentu pro specifikátor převodu *typu* . Pole *Velikost přinese* předpony na *pole typ* –**HH**, **h**, **j**, **l** (malá písmena l), **l**, **ll**, **t**, **w**, **z**, **I** (velká písmena I), **i32**a **I64**– určete velikost odpovídajícího argumentu – dlouhý nebo krátký, 32 nebo 64 bajtový znak nebo velký znak – v závislosti na specifikátoru převodu, který upravují. Tyto předpony velikosti se používají s znaky *typu* v `printf` a `wprintf` rodin funkcí k určení interpretace velikostí argumentů, jak je znázorněno v následující tabulce. Pole *Size* je pro některé typy argumentů volitelné. Pokud není zadána žádná předpona velikosti, formátovací modul spotřebovává celočíselné argumenty, například podepsaný nebo nepodepsaný `char`, `short`, `int`, `long`a výčtové typy, jako 32 typy `int` bitů a `float`, `double`a `long double` argumenty s plovoucí desetinnou čárkou jsou spotřebovány jako 64 typy `double` bitů. Toto chování odpovídá výchozím pravidlům pro povýšení argumentů pro seznamy argumentů proměnných. Další informace o povýšení argumentů naleznete v tématu elipsy a výchozí argumenty ve [výrazech přípony](../cpp/postfix-expressions.md). V systémech 32 a 64 musí specifikace převodu argumentu celočíselné hodnoty 64 obsahovat předponu Size s hodnotou **ll** nebo **I64**. V opačném případě chování formátovacího modulu není definováno.

Některé typy jsou různé velikosti v 32 a 64 bitového kódu. Například `size_t` je 32 bitů dlouhý v kódu kompilovaném pro x86 a 64 bitů v kódu zkompilovaném pro x64. Chcete-li vytvořit kód pro formátování Platform-nezávislá pro typy s proměnlivou šířkou, můžete použít modifikátor velikosti argumentu proměnné šířky. Alternativně použijte modifikátor velikosti 64 bitového argumentu a explicitně zvyšte úroveň typu argumentu s proměnnou šířkou na 64 bitů. Modifikátor velikosti argumentu specifického pro Microsoft **i** (velká i malá) zpracovává celočíselné argumenty proměnné šířky, ale pro přenositelnost doporučujeme použít Modifikátory specifické pro typ **j**, **t**a **z** .

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Předpony velikosti pro specifikátory typu printf a wprintf formátu

|Zadání|Použít předponu|Se specifikátorem typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**HH**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`short int`<br />`short unsigned int`|**y**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`intmax_t`<br />`uintmax_t`|**j** nebo **I64**|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`long double`|**l** (malé písmeno l) nebo **l**|**a**, **a**, **e**, **e**, **f**, **f**, **g**nebo **g**|
|`long int`<br />`long unsigned int`|**l** (malé písmeno l)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`long long int`<br />`unsigned long long int`|**vše** (malé písmeno ll)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`ptrdiff_t`|**t** nebo **I** (velká písmena I)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|`size_t`|**z** nebo **I** (velká písmena i)|**d**, **i**, **o**, **u**, **x**nebo **x**|
|Jednobajtové znak|**y**|**c** nebo **c**|
|Velký znak|**l** (malé písmeno l) nebo **w**|**c** nebo **c**|
|Jednobajtové znakové řetězce|**y**|**s**, **s**nebo **Z**|
|Řetězec s velkým znakem|**l** (malé písmeno l) nebo **w**|**s**, **s**nebo **Z**|

Typy `ptrdiff_t` a `size_t` jsou `__int32` nebo `unsigned __int32` na 32 a `__int64` na 64ch platformách.`unsigned __int64` Předpony velikost **i** (velká i), **j**, **t**a **z** mají pro platformu správnou šířku argumentu.

V jazyce C++Visual, i když `long double` je odlišný typ, má stejnou vnitřní reprezentaci jako `double`.

Specifikátor typu **HC** nebo **HC** je synonymum s **c** v `printf` functions a s **c** v `wprintf` Functions. Specifikátor typu **LC**, **LC**, **WC**nebo **wc** je synonymum s **c** v `printf` functions a s **c** v `wprintf` Functions. Specifikátor typu **HS** nebo **HS** je synonymem s v `printf` Functions **a s s** **s v `wprintf`** Functions. Specifikátor typu **ls**, **ls**, **WS** nebo **ws** je synonymum **s s v `printf`** functions a s **s s v `wprintf`** Functions.

> [!NOTE]
> **Specifické pro společnost Microsoft:** **I** (velká písmena i), **i32**, **I64**a **w** argumenty modifikátoru velikosti ARGUMENTŮ jsou rozšíření Microsoft a nejsou kompatibilní s ISO C. Předpona **h** , pokud se používá s daty typu `char` a **l** (malá písmena l) předpony, když se používá s daty typu `double` jsou rozšíření společnosti Microsoft.

## <a name="see-also"></a>Viz také

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[printf_p – poziční parametry](../c-runtime-library/printf-p-positional-parameters.md)
