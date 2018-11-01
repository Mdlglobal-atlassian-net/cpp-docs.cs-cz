---
title: 'Syntaxe specifikace formátu: funkce printf a wprintf'
ms.date: 11/04/2016
helpviewer_keywords:
- format specification fields for printf function
- printf function format specification fields
- flag directives, printf function
- type fields, printf function
- width fields, printf function
- precision fields, printf function
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
ms.openlocfilehash: cb7d99077a082323a6662d29c0386cd1d416297c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665332"
---
# <a name="format-specification-syntax-printf-and-wprintf-functions"></a>Syntaxe specifikace formátu: funkce printf a wprintf

Různé `printf` a `wprintf` funkce řetězec formátu a nepovinné argumenty. a vytvoří formátovaných posloupnosti znaků pro výstup. Formátovací řetězec obsahuje nula nebo více *direktivy*, které jsou buď literálními znaky pro výstupní nebo kódovaného *převod specifikací* , která popisují, jak formátovat argument ve výstupu. Toto téma popisuje syntaxi použít ke kódování převod specifikací ve formátovacím řetězci. Seznam těchto funkcí naleznete v tématu [vstupně-výstupní operace Stream](../c-runtime-library/stream-i-o.md).

Specifikace převodu se skládá z povinných a volitelných polí v tomto formuláři:

**%**[[*příznaky*](#flags)] [[*šířka*](#width)] [.[ *přesnost*](#precision)] [[*velikost*](#size)][*typu*](#type)

Každé pole specifikace převodu je znak nebo číslo, které označuje, že danou formátovací volbu nebo specifikátor převodu. Požadovaný *typ* pole určuje druh převodu na argument použit. Volitelný *příznaky*, *šířka*, a *přesnost* polí určují další aspekty formátu například mezery nebo nuly, zarovnání a zobrazené přesnosti. *Velikost* pole určuje velikost argumentu spotřebované a převést.

Specifikace základní převodu obsahuje pouze znak procent a *typ* znak. Například `%s` specifikuje konverzi na řetězec. Pro výpis znaku procent je třeba použít `%%`. Pokud je znak procent následován znakem, který nemá žádný význam jako pole formátu, je vyvolána obslužná rutina neplatného parametru. Další informace najdete v tématu [Parameter Validation](../c-runtime-library/parameter-validation.md).

> [!IMPORTANT]
> Zabezpečení a stability zkontrolujte této specifikace převodu řetězců není definována uživatelem. Zvažte například program, který vyžaduje od uživatele zadání jména a ukládá vstup do proměnné řetězce s názvem `user_name`. Pro výpis `user_name` není vhodné použít:
>
> `printf( user_name ); /* Danger!  If user_name contains "%s", program will crash */`
>
> Místo toho je lepší použít:
>
> `printf( "%s", user_name );`

<a name="type"></a>

## <a name="type-conversion-specifier"></a>Specifikátoru převodu typu.

*Typ* znak specifikátoru převodu určuje, jestli se má odpovídající argument interpretovat jako znak, řetězec, ukazatel, celé číslo nebo číslo s plovoucí desetinnou čárkou. *Typ* znak je pouze požadovaná převod pole pro specifikaci a zobrazí se po volitelných polí.

Argumenty, které následují formátovacím řetězci interpretovány podle odpovídající *typ* znak a volitelné [velikost](#size) předponu. Převody pro typy znaků `char` a `wchar_t` je určené vlastností **c** nebo **C**, a jednobajtové a vícebajtové nebo široký znak řetězce je určené vlastností **s** nebo **S**, v závislosti na formátování funkci, která se používá. Znakové a řetězcové argumenty, které je určené vlastností **c** a **s** jsou interpretovány jako `char` a `char*` podle `printf` produktovou řadu funkcí, nebo jako `wchar_t` a `wchar_t*` podle `wprintf` řady funkcí. Znakové a řetězcové argumenty, které je určené vlastností **C** a **S** jsou interpretovány jako `wchar_t` a `wchar_t*` podle `printf` produktovou řadu funkcí, nebo jako `char` a `char*` podle `wprintf` řady funkcí. Toto chování je specifické pro Microsoft.

Celočíselné typy, jako `short`, `int`, `long`, `long long` a jejich `unsigned` variant, jsou určené pomocí **d**, **i**, **o**, **u**, **x**, a **X**. Typy s plovoucí desetinnou čárkou, jako `float`, `double`, a `long double`, jsou určené pomocí **a**, **A**, **e**, **E**, **f**, **F**, **g**, a **G**. Ve výchozím nastavení Pokud se změnil *velikost* předponu, jsou přiřazeny celočíselné argumenty do `int` typu a argumentů s plovoucí desetinnou čárkou jsou přiřazeny do `double`. V 64bitových systémech `int` je 32bitová hodnota; proto bude 64bitová celá čísla zkrácena, když jsou formátována pro výstup, není-li *velikost* předponu **ll** nebo **I64**se používá. Typy ukazatelů, která jsou určena podle **p** použít výchozí velikost ukazatele pro platformu.

> [!NOTE]
> **Specifické pro Microsoft** **Z** zadejte znak a chování **c**, **C**, **s**, a **S** znaky při jejich použití se službou `printf` a `wprintf` funkce, jsou rozšíření společnosti Microsoft. Standard ISO C používá **c** a **s** konzistentně pro úzkých znaků a řetězce, a **C** a **S** pro široké znaky a řetězce v všechny funkce, formátování.

### <a name="type-field-characters"></a>Znaky pole typu

|Znak typu|Argument|Výstupní formát|
|--------------------|--------------|-------------------|
|**c**|Znak|Při použití s `printf` funkce, určuje jednobajtový znak; při použití s `wprintf` funkce, určuje širokého znaku.|
|**C**|Znak|Při použití s `printf` funkce, určuje širokého znaku; při použití s `wprintf` funkce, určuje jednobajtový znak.|
|**d**|Integer|Desítkové celé číslo se znaménkem.|
|**i**|Integer|Desítkové celé číslo se znaménkem.|
|**O**|Integer|Osmičkové celé číslo bez znaménka.|
|**u**|Integer|Desítkové celé číslo bez znaménka.|
|**x**|Integer|Šestnáctkové celé číslo bez znaménka; používá "abcdef".|
|**X**|Integer|Šestnáctkové celé číslo bez znaménka; používá "ABCDEF".|
|**e**|S plovoucí desetinnou čárkou|Hodnota, která má tvar [-] podepsané*d.dddd*__e±__*dd*[*d*] kde *d* je jedním desítkovým číslem, *dddd* je jeden nebo více desítkových číslic v závislosti na zadané přesnosti nebo šest ve výchozím nastavení, a *dd*[*d*] je dvě nebo tři desítkové číslice v závislosti na tom, [výstupní formát](../c-runtime-library/set-output-format.md) a velikost exponent.|
|**E**|S plovoucí desetinnou čárkou|Stejné jako **e** formátu s výjimkou, že **E** spíše než **e** zavádí exponent.|
|**f**|S plovoucí desetinnou čárkou|Hodnota, která má tvar [-] podepsané*dddd*__.__ *dddd*, kde *dddd* je jeden nebo více desítkových číslic. Počet číslic od desetinné čárky závisí na velikosti číslo a počet číslic po desetinné čárky, závisí na požadovaná přesnost nebo šest ve výchozím nastavení.|
|**F**|S plovoucí desetinnou čárkou|Stejné jako **f** naformátovat s tím rozdílem, že velké výstup nekonečno a nan.|
|**g**|S plovoucí desetinnou čárkou|Hodnoty se znaménkem jsou zobrazeny v **f** nebo **e** formátování, podle toho, co je kompaktnější pro dané hodnoty a přesnosti. **e** formátu se používá jenom v případě, že exponent hodnota je menší než -4 nebo větší než nebo rovna hodnotě *přesnost* argument. Koncové nuly jsou zkrácena a oddělovač desetinných míst se zobrazí pouze v případě, že je jeden nebo více číslic na něho.|
|**G**|S plovoucí desetinnou čárkou|Stejné jako **g** formátu, s výjimkou, že **E**, spíše než **e**, zavádí exponent (kde je to vhodné).|
|**a**|S plovoucí desetinnou čárkou|Podepsané šestnáctkovou hodnotu s plovoucí desetinnou čárkou dvojité přesnosti, která má tvar [-] 0 x*h.hhhh*__p±__*dd*, kde *h.hhhh* jsou šestnáctkové soustavě číslice (pomocí malých písmen) v mantise a *dd* je jeden nebo více číslic exponentu. Přesnosti určuje počet číslic za čárkou.|
|**A**|S plovoucí desetinnou čárkou|Podepsané šestnáctkovou hodnotu s plovoucí desetinnou čárkou dvojité přesnosti, která má tvar [-] 0 X*h.hhhh*__P±__*dd*, kde *h.hhhh* jsou šestnáctkové soustavě číslice (použití velkých písmen) v mantise a *dd* je jeden nebo více číslic exponentu. Přesnosti určuje počet číslic za čárkou.|
|**n**|Ukazatel na celé číslo|Počet znaků, které se zatím zapisují úspěšně do datového proudu nebo vyrovnávací paměti. Tato hodnota je uložena v celé číslo, jehož adresa je zadána jako argument. Velikost celé číslo, na které mohou být řízena předponu specifikace velikost argumentu. **n** specifikátor je ve výchozím nastavení zakázané, informace naleznete v tématu poznámky pro důležité zabezpečení.|
|**p**|Typ ukazatele|Argument se zobrazí jako adresy v šestnáctkové číslice.|
|**s**|String|Při použití s `printf` funkce, určuje jednobajtové nebo vícebajtové znakové řetězce; při použití s `wprintf` funkce, určí širokoznaký řetězec. Až po první znak null, nebo dokud se zobrazí znaky *přesnost* nebude dosaženo hodnoty.|
|**S**|String|Při použití s `printf` funguje, určí širokoznaký řetězec; při použití s `wprintf` funkce, určuje jednobajtové nebo vícebajtové znakové řetězce. Až po první znak null, nebo dokud se zobrazí znaky *přesnost* nebude dosaženo hodnoty.|
|**Z**|`ANSI_STRING` nebo `UNICODE_STRING` struktura|Když adresu [ANSI_STRING](/windows/desktop/api/ntdef/ns-ntdef-_string) nebo [UNICODE_STRING](https://msdn.microsoft.com/library/windows/hardware/ff564879.aspx) struktura je předán jako argument, zobrazí řetězec obsažený ve vyrovnávací paměti, na které odkazují `Buffer` pole struktury. Použití *velikost* modifikátor předponu **w** k určení `UNICODE_STRING` argument – například `%wZ`. `Length` Pole struktury musí být nastaveno na délku řetězce v bajtech. `MaximumLength` Pole struktury musí být nastavené na délka vyrovnávací paměti v bajtech.<br /><br /> Obvykle **Z** – znak typu se používá jenom v ladění funkcí, které používají specifikace převodu, jako například ovladače `dbgPrint` a `kdPrint`.|

Od verze sady Visual Studio 2015, pokud argument, který odpovídá specifikátor převody plovoucí desetinné čárky (**a**, **A**, **e**, **E**, **f**, **F**, **g**, **G**) je nekonečné neomezené, nebo NaN, formátovaný výstup vyhovuje C99 standard. Tato tabulka shrnuje formátovaný výstup:

|Hodnota|Výstup|
|-----------|------------|
|nekonečna|`inf`|
|Tichý NaN|`nan`|
|Signalizace NaN|`nan(snan)`|
|Neomezené NaN|`nan(ind)`|

Některé z těchto hodnot mohou začínat znakem. Pokud plovoucí desetinné čárky *typ* znak specifikátoru převodu je velké písmeno, pak je výstup formátovaný také velkými písmeny. Například, pokud je specifikátor formátu `%F` místo `%f`, nekonečno je formátován jako `INF` místo `inf`. `scanf` Funkce můžete také analyzovat tyto řetězce, takže se tyto hodnoty zpátečního převodu prostřednictvím `printf` a `scanf` funkce.

Před Visual Studio 2015 CRT používá jiný, nestandardní formát pro výstup nekonečno, nekonečno a NaN hodnoty:

|Hodnota|Výstup|
|-----------|------------|
|+ nekonečno|`1.#INF` *náhodné číslic*|
|-nekonečno|`-1.#INF` *náhodné číslic*|
|Nekonečný (stejné jako tichý NaN)|*číslice* `.#IND` *náhodné číslic*|
|NaN|*číslice* `.#NAN` *náhodné číslic*|

Některé z těchto může mít předponu znakem a může formátována mírně liší v závislosti na šířku pole a přesnosti, někdy s neobvyklou účinky. Například `printf("%.2f\n", INFINITY)` vytiskne `1.#J` vzhledem k tomu, #INF by "zaokrouhlované" s přesností na 2 číslice.

> [!NOTE]
> Pokud argument, který odpovídá `%s` nebo `%S`, nebo `Buffer` pole argumentu, který odpovídá `%Z`, je ukazatel s hodnotou null, se zobrazí "(null).

> [!NOTE]
> V exponenciální formáty minimální počet číslic exponentu zobrazíte je dvě, tři použití pouze v případě potřeby. S použitím [_set_output_format –](../c-runtime-library/set-output-format.md) funkce, můžete nastavit počet zobrazených na tři z důvodu zpětné kompatibility s kódem napsaným pro Visual Studio 2013 a před číslic.

> [!IMPORTANT]
> Vzhledem k tomu, `%n` formát je ze své podstaty nezabezpečené, je ve výchozím nastavení zakázána. Pokud `%n` dochází v řetězci formátu, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../c-runtime-library/parameter-validation.md). Chcete-li povolit `%n` podporovat, najdete v článku [_set_printf_count_output –](../c-runtime-library/reference/set-printf-count-output.md).

<a name="flags"></a>

## <a name="flag-directives"></a>Direktivy příznaku

První volitelné pole ve specifikaci převod obsahuje *příznak direktivy*, nula nebo více znaků, které zadejte zarovnání výstupu a výstup znaménka, prázdné hodnoty, počátečních nul, desetinných míst a interpretace osmičková příznak a šestnáctkových předpon. Specifikace převodu se může vyskytovat více než jedna direktiva příznak a příznak znaky se mohou objevit v libovolném pořadí.

### <a name="flag-characters"></a>Příznak znaků

|Příznak|Význam|Výchozí|
|----------|-------------|-------------|
|**-**|Zarovnat vlevo výsledků v rámci dané pole šířky.|Zarovnejte doprava.|
|**+**|Symbol (+ nebo -) jako předpona výstupní hodnota, pokud se jedná o typ se znaménkem.|Přihlášení se zobrazí pouze pro záporné hodnoty se znaménkem (-).|
|**0**|Pokud *šířka* má předponu **0**, počáteční nuly jsou přidány, dokud nebude dosaženo minimální šířku. Pokud oba **0** a **-** se zobrazí, **0** je ignorována. Pokud **0** je určená pro celočíselný formát (**můžu**, **u**, **x**, **X**, **o**, **d**) a specifikace přesnosti je také k dispozici – například `%04.d`– **0** se ignoruje. Pokud **0** pro je zadána **a** nebo **A** s plovoucí desetinnou čárkou formátu úvodní nuly se přidá jako předpona k mantisa, po `0x` nebo `0X` předponu.|Bez oddělovačů.|
|**prázdné** ("")|Pomocí prázdné předpony výstupní hodnota, pokud je podepsaný a kladné. Začátku se ignoruje, pokud obě prázdnou a + příznaky se zobrazí.|Zobrazí se žádné prázdné.|
|**#**|Při použití s **o**, **x**, nebo **X** formátu, **#** příznak používá 0, 0 x, nebo 0 X, na každém nenulovou předponu výstupní hodnota.|Zobrazí se žádné prázdné.|
||Pokud se používá s **e**, **E**, **f**, **F**, **a** nebo **A** formát, **#** příznak vynutí výstupní hodnotu tak, aby obsahovala desetinné čárky.|Desetinné čárky se zobrazí jenom v případě, že na něho číslic.|
||Při použití s **g** nebo **G** formátu, **#** příznak vynutí výstupní hodnotu tak, aby obsahovala desetinné čárky a brání zkrácení koncovými nulami.<br /><br /> Ignoruje při použití s **c**, **d**, **můžu**, **u**, nebo **s**.|Desetinné čárky se zobrazí jenom v případě, že na něho číslic. Koncové nuly jsou zkrácena.|

<a name="width"></a>

## <a name="width-specification"></a>Specifikace šířky

Ve specifikaci převodu, zobrazí se pole pro specifikaci šířky volitelné po všech *příznaky* znaků. *Šířka* argument je záporná desítkové celé číslo, která určuje minimální počet znaků, které jsou výstupem. Pokud počet znaků v výstupní hodnota je menší než nastavená šířka, prázdné hodnoty se přidají do nalevo nebo napravo od hodnoty – v závislosti na tom, zda příznak zarovnání doleva (**-**) je zadán – dokud minimum bylo dosaženo šířku. Pokud *šířka* předchází 0, počáteční nuly jsou přidány do celé číslo nebo číslo s plovoucí desetinnou čárkou převody až do dosažení minimální šířku, s výjimkou případu, kdy převod na nekonečno nebo na NaN.

Specifikace šířky nikdy způsobí, že hodnota má být zkráceno. Pokud počet znaků ve výstupní hodnota je větší než nastavená šířka, nebo pokud *šířka* není zadaný, jsou všechny znaky hodnoty výstupu se vztahuje *přesnost* specifikace.

Pokud specifikace šířky je hvězdička (`*`), `int` poskytuje hodnotu argumentu v seznam argumentů. *Šířka* argumentu musí předcházet hodnotě, která se chystáte formátovat v seznamu argumentů tak, jak je znázorněno v tomto příkladu:

`printf("%0*f", 5, 3);  /* 00003 is output */`

Chybějící nebo malé *šířka* hodnotu ve specifikaci převod nezpůsobí zkrácení výstupní hodnoty. Pokud je výsledkem převodu širší než *šířka* hodnotu, rozbalí pole tak, aby obsahovala výsledku převodu.

<a name="precision"></a>

## <a name="precision-specification"></a>Specifikace přesnosti

Ve specifikaci převod třetí volitelné pole je specifikace přesnosti. Zahrnuje tečka (.), za nímž následuje záporná desítkové celé číslo určující, v závislosti na typu převodu řetězce znaků, počet desetinných míst nebo počet platných číslic pro výstup.

Na rozdíl od specifikace šířky může způsobit specifikace přesnosti buď zkrácení výstupní hodnotu nebo zaokrouhlení s plovoucí desetinnou čárkou. Pokud *přesnost* je zadán jako 0 a hodnota má být převeden je 0, výsledek je žádný výstup znaků, jak je znázorněno v tomto příkladu:

`printf( "%.0d", 0 );      /* No characters output */`

Pokud je specifikace přesnosti hvězdičku (\*), `int` poskytuje hodnotu argumentu v seznam argumentů. V seznamu argumentů tak *přesnost* argumentu musí předcházet hodnotě, která se chystáte formátovat, jak je znázorněno v tomto příkladu:

`printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`

*Typ* znaků určuje buď výklad *přesnost* nebo přesnost při *přesnost* je vynechán, jak je znázorněno v následující tabulce.

### <a name="how-precision-values-affect-type"></a>Jak hodnoty přesnosti ovlivňují typ

|Typ|Význam|Výchozí|
|----------|-------------|-------------|
|**a**, **A**|Přesnosti určuje počet číslic za čárkou.|Přesnost je 13. Pokud přesnost je 0, pokud není, vytiskne se žádné desetinné čárky **#** příznak se používá.|
|**c**, **C**|Přesnost nemá žádný vliv.|Znak je vytištěna.|
|**d**, **i**, **o**, **u**, **x**, **X**|Přesnost určuje minimální počet číslic, které se mají vytisknout. Pokud počet číslic v argumentu je menší než *přesnost*, výstupní hodnota je, aby bylo vytvořeno na levé straně nulami. Hodnota není zkrácena, když překročí počet číslic *přesnost*.|Přesnost je 1.|
|**elektronické**, **E**|Přesnosti určuje počet číslic, které se mají vytisknout za desetinnou čárkou. Poslední číslice tištěné zaokrouhleno.|Přesnost je 6. Pokud *přesnost* je 0 nebo tečku (.) se zobrazí bez čísla následující, vytiskne se žádné desetinné čárky.|
|**f**, **F**|Hodnota přesnosti určuje počet číslic za desetinnou čárkou. Pokud se zobrazí desetinné čárky, dříve, než se zobrazí alespoň jednu číslici. Hodnota se zaokrouhlí na odpovídající počet číslic.|Přesnost je 6. Pokud *přesnost* je 0, nebo pokud se bez čísla následující tečka (.), vytiskne se žádné desetinné čárky.|
|**g**, **G**|Přesnost určuje maximální počet nejvýznamnějších číslic vytisknout.|Jsou vypsány šest nejvýznamnějších číslic a všechny koncové nuly jsou zkrácena.|
|**s**, **S**|Přesnost určuje maximální počet znaků, které se mají vytisknout. Znaky překračuje *přesnost* nejsou zobrazeny.|Znaky jsou zobrazeny, dokud je zjištěn znak null.|

<a name="size"></a>

## <a name="argument-size-specification"></a>Argument specifikace velikosti

Ve specifikaci převod *velikost* je pole modifikátor délky argumentu pro *typ* specifikátoru převodu. *Velikost* polí předpony, jež mají *typ* pole –**hh**, **h**, **j**, **l** (malé písmeno L), **L**, **ll**, **t**, **w**, **z**, **můžu**(velká písmena i) **I32**, a **I64**– určují "velikost" odpovídajícího argumenty – long nebo short, 32bitovou verzi nebo 64-bit, jednobajtový znak nebo široký znak – v závislosti na tom specifikátoru převodu, který mění. Tyto předpony velikosti se používají s *typ* znaků `printf` a `wprintf` rodinách funkcí pro určení velikosti argument, jak je znázorněno v následující tabulce. *Velikost* pole je nepovinné pro některé typy argumentů. Když se nezadá žádná předpona velikosti, formátovací modul používá celočíselné argumenty – například podepsaná nebo nepodepsaná `char`, `short`, `int`, `long`a výčtové typy – jako 32-bit `int` typů, a `float`, `double`, a `long double` spotřebovávají argumentů s plovoucí desetinnou čárkou jako 64bitové `double` typy. To odpovídá výchozí argument propagační akce pravidla pro seznamy argumentů s proměnnou délkou. Další informace o podpoře argument, najdete v článku výpustky a výchozí argumenty v [výrazy přípony](../cpp/postfix-expressions.md). V 32bitových a 64bitových systémech, musí obsahovat specifikace převodu 64bitové celé číslo argumentu Předpona velikosti **ll** nebo **I64**. V opačném případě není definováno chování formátovacího modulu.

Některé typy v 32bitové a 64bitové kódu jsou různých velikostí. Například `size_t` je 32 bitů dlouhý v kódu zkompilovaném pro x86 a 64 bitů v kódu zkompilovaném pro x64. K vytvoření formátování kódu pro více platforem pro typy proměnné šířky, můžete použít modifikátor velikost argumentu proměnné šířky. Můžete také použít modifikátor velikost 64-bit argument a explicitně podporovat typ argumentu proměnné šířky na 64 bitů. Specifické pro Microsoft **můžu** (velkými písmeny psané i) zpracovává modifikátor velikost argumentu proměnné šířky celočíselné argumenty, ale doporučujeme konkrétní typ **j**, **t**a **z** modifikátory pro přenositelnost.

### <a name="size-prefixes-for-printf-and-wprintf-format-type-specifiers"></a>Předpony velikosti pro printf a wprintf specifikátory formátu

|Chcete-li určit|Použijte předponu|Pomocí specifikátoru typu|
|----------------|----------------|-------------------------|
|`char`<br />`unsigned char`|**hh**|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`short int`<br />`short unsigned int`|**h**|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`__int32`<br />`unsigned __int32`|**I32**|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`__int64`<br />`unsigned __int64`|**I64**|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`intmax_t`<br />`uintmax_t`|**j** nebo **I64**|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`long double`|**l** (malé písmeno L) nebo **L**|**a**, **A**, **e**, **E**, **f**, **F**, **g**, nebo **G**|
|`long int`<br />`long unsigned int`|**l** (malé písmeno L)|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`long long int`<br />`unsigned long long int`|**všechny** (malá písmena vše)|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`ptrdiff_t`|**t** nebo **můžu** (i velká)|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|`size_t`|**z** nebo **můžu** (i velká)|**d**, **můžu**, **o**, **u**, **x**, nebo **X**|
|Jednobajtový znak|**h**|**c** nebo **C**|
|široký znak|**l** (malé písmeno L) nebo **w**|**c** nebo **C**|
|Jednobajtové znakové řetězce|**h**|**s**, **S**, nebo **Z**|
|Řetězec širokých znaků|**l** (malé písmeno L) nebo **w**|**s**, **S**, nebo **Z**|

`ptrdiff_t` a `size_t` typy jsou `__int32` nebo `unsigned __int32` na 32bitových platformách a `__int64` nebo `unsigned __int64` na 64bitových platformách. **můžu** (velká písmena i) **j**, **t**, a **z** velikosti předponami trvat šířku správné argument pro platformu.

V jazyce Visual C++ i když `long double` je odlišný typ se má stejnou vnitřní reprezentaci jako `double`.

**Hc** nebo **hybridní připojení** specifikátor typu je synonymní s **c** v `printf` funkce a s **C** v `wprintf` funkce. **Lc**, **lC**, **RC** nebo **RC** specifikátor typu je synonymní s **C** v `printf` Funkce a s **c** v `wprintf` funkce. **Hs** nebo **hS** specifikátor typu je synonymní s **s** v `printf` funkce a s **S** v `wprintf` funkce. **Ls**, **lS**, **ws** nebo **wS** specifikátor typu je synonymní s **S** v `printf` Funkce a s **s** v `wprintf` funkce.

> [!NOTE]
> **Specifické pro Microsoft** **můžu** (velká písmena i) **I32**, **I64**, a **w** předpony modifikující velikost argumentu jsou společnosti Microsoft rozšíření a jsou není kompatibilní s ISO C. **h** předpony při použití s daty typu `char` a **l** (malé písmeno L) předpony při použití s daty typu `double` jsou rozšíření společnosti Microsoft.

## <a name="see-also"></a>Viz také

[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)<br/>
[printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)<br/>
[printf_p – poziční parametry](../c-runtime-library/printf-p-positional-parameters.md)