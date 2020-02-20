---
title: Řetězcové a znakové literályC++()
description: Jak deklarovat a definovat řetězcové a znakové literály v C++.
ms.date: 02/18/2020
f1_keywords:
- R
- L
- u
- u8
- LR
- uR
- u8R
helpviewer_keywords:
- literal strings [C++]
- string literals [C++]
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
ms.openlocfilehash: 1b4cfb8059b116b0d91886f5b78b3911e8dc316c
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504464"
---
# <a name="string-and-character-literals-c"></a>Řetězcové a znakové literályC++()

C++podporuje různé typy řetězců a znaků a poskytuje způsoby, jak vyjádřit hodnoty literálu každého z těchto typů. Ve vašem zdrojovém kódu budete vyjadřovat obsah znakových a řetězcových literálů pomocí znakové sady. Univerzální názvy znaků a řídicí znaky umožňují vyjádřit libovolný řetězec pouze pomocí základní zdrojové znakové sady. Nezpracovaný řetězcový literál umožňuje vyhnout se použití ukončovacích znaků a lze jej použít k vyjádření všech typů řetězcových literálů. Můžete také vytvořit `std::string` literály, aniž byste museli provádět dodatečné kroky konstrukce nebo převodu.

```cpp
#include <string>
using namespace std::string_literals; // enables s-suffix for std::string literals

int main()
{
    // Character literals
    auto c0 =   'A'; // char
    auto c1 = u8'A'; // char
    auto c2 =  L'A'; // wchar_t
    auto c3 =  u'A'; // char16_t
    auto c4 =  U'A'; // char32_t

    // Multicharacter literals
    auto m0 = 'abcd'; // int, value 0x61626364

    // String literals
    auto s0 =   "hello"; // const char*
    auto s1 = u8"hello"; // const char*, encoded as UTF-8
    auto s2 =  L"hello"; // const wchar_t*
    auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16
    auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32

    // Raw string literals containing unescaped \ and "
    auto R0 =   R"("Hello \ world")"; // const char*
    auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8
    auto R2 =  LR"("Hello \ world")"; // const wchar_t*
    auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16
    auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32

    // Combining string literals with standard s-suffix
    auto S0 =   "hello"s; // std::string
    auto S1 = u8"hello"s; // std::string
    auto S2 =  L"hello"s; // std::wstring
    auto S3 =  u"hello"s; // std::u16string
    auto S4 =  U"hello"s; // std::u32string

    // Combining raw string literals with standard s-suffix
    auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char*
    auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8
    auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t*
    auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16
    auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32
}
```

Řetězcové literály nesmí mít žádnou předponu, ani `u8`, `L`, `u`a `U` předpony k označení úzkého znaku (jednobajtové nebo vícebajtového), UTF-8, roztažitelné znaku (UCS-2 nebo UTF-16), v uvedeném pořadí UTF-16 a kódování UTF-32. Nezpracovaný řetězcový literál může mít `R`, `u8R`, `LR`, `uR`a `UR` předpony pro nezpracované ekvivalenty těchto kódování.  Chcete-li vytvořit dočasné nebo statické hodnoty `std::string`, můžete použít řetězcové literály nebo nezpracované řetězcové literály s příponou `s`. Další informace naleznete níže v části [řetězcové literály](#string-literals) . Další informace o základní zdrojové znakové sadě, univerzální názvy znaků a použití znaků z rozšířených znakových sad ve zdrojovém kódu naleznete v tématu [znakové sady](../cpp/character-sets.md).

## <a name="character-literals"></a>Literály znaků

*Znakový literál* se skládá z konstantního znaku. Je reprezentován znakem uzavřeným v jednoduchých uvozovkách. Existuje pět druhů znakových literálů:

- Běžné znakové literály typu **char**, například `'a'`

- Znakové literály UTF-8 typu **char** (**char8_t** v c++ 20), například `u8'a'`

- Literály s velkým znakem typu `wchar_t`, například `L'a'`

- Znakové literály UTF-16 typu `char16_t`, například `u'a'`

- Literály znaků UTF-32 typu `char32_t`, například `U'a'`

Znak použitý pro literál znaků může být libovolný znak, s výjimkou zpětného lomítka ('\\'), jednoduché uvozovky (') nebo nového řádku. Vyhrazené znaky lze zadat pomocí řídicí sekvence. Znaky mohou být zadány pomocí univerzálních názvů znaků, pokud je typ dostatečně velký pro uložení znaku.

### <a name="encoding"></a>Kódování

Znakové literály se kódují odlišně na základě jejich předpony.

- Znakový literál bez předpony je běžný znakový literál. Hodnota obyčejného znakového literálu, který obsahuje jeden znak, řídicí sekvenci nebo univerzální název znaku, který lze reprezentovat ve znakové sadě spuštění, má hodnotu rovnou číselné hodnotě jeho kódování ve znakové sadě spuštění. Běžný znakový literál, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je *literální znak*. Literál s více znakovými písmeny nebo běžný znakový literál, který nelze reprezentovat ve znakové sadě spuštění, má typ **int**a jeho hodnota je definovaná implementací. MSVC naleznete v části **specifické pro společnost Microsoft** níže.

- Znakový literál, který začíná předponou `L`, je literál s velkým znakem. Hodnota literálu s velkým znakem obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se číselnou hodnotou svého kódování v sadě s velkým znakem, pokud znak literálu nemá žádné reprezentace v je-li nastavena 64bitová znaková sada, v takovém případě je hodnota definována jako implementace. Hodnota literálu s velkým znakem, který obsahuje více znaků, řídicí sekvence nebo názvy univerzálních znaků, je definována implementací. MSVC naleznete v části **specifické pro společnost Microsoft** níže.

- Znakový literál, který začíná předponou `u8`, je znakový literál UTF-8. Hodnota literálu znaku UTF-8 obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se hodnotě bodu kódu ISO 10646, pokud může být reprezentována jednou jednotkou znakové sady UTF-8 (odpovídající ovládacím prvkům C0 a základní latinkou Blok kódování Unicode). Pokud hodnota nemůže být reprezentovaná jednou jednotkou znakové sady UTF-8, program je nesprávně vytvořen. Znakový literál UTF-8, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je nesprávně vytvořen.

- Znakový literál, který začíná předponou `u`, je znakový literál UTF-16. Hodnota znakového literálu ve formátu UTF-16 obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se hodnotě bodu kódu ISO 10646, pokud může být reprezentovaná jednou jednotkou UTF-16 (odpovídající rovině Basic multi-Sequence). ). Pokud hodnota nemůže být reprezentovaná jednou jednotkou znakové sady UTF-16, program je nesprávně vytvořen. Znakový literál UTF-16, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je nesprávně vytvořen.

- Znakový literál, který začíná předponou `U`, je literální znak UTF-32. Hodnota literálu znaku UTF-32 obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se hodnotě bodu kódu ISO 10646. Znakový literál UTF-32, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je nesprávně vytvořen.

### <a name="bkmk_Escape"></a>Řídicí sekvence

Existují tři druhy řídicích sekvencí: jednoduché, osmičkové a hexadecimální. Řídicí sekvence můžou být kteroukoli z následujících hodnot:

|Hodnota|Řídicí sekvence|
|-----------|---------------------|
| newline | \\n |
| zpětné lomítko | \\\\ |
| horizontální karta | \\t |
| otazník | ? nebo \\? |
| svislá karta | \\v |
| jednoduchá uvozovka | \\ |
| BACKSPACE | \\b |
| dvojité uvozovky | \\" |
| Návrat na začátek | \\r |
| znak null | \\0 |
| Posun strany | \\f |
| osmičkové | \\OOO |
| upozornění (zvonek) | \\ |
| hexadecimální | \\xhhh |

Osmičková řídicí sekvence je zpětné lomítko následované posloupností jednoho až tří osmičkových číslic. Osmičková řídicí sekvence končí prvním znakem, který není osmičkovou číslicí, pokud byl nalezen dříve než třetí číslice. Nejvyšší možná osmičková hodnota je `\377`.

Šestnáctková řídicí sekvence je zpětné lomítko následované znakem `x`následovaný sekvencí jednoho nebo více hexadecimálních číslic. Úvodní nuly jsou ignorovány. V běžném nebo U8 s předem opraveným znakovým literálem je nejvyšší šestnáctková hodnota 0xFF. V literálu předplatného, který je v předplatném, je nejvyšší šestnáctková hodnota 0xFFFF. V rámci předplatného literálu U znaku U, nejvyšší šestnáctková hodnota je 0xFFFFFFFF.

Tento vzorový kód ukazuje několik příkladů řídicích znaků pomocí běžných literálů znaků. Stejná syntaxe sekvence Escape je platná pro jiné typy literálů znaků.

```cpp
#include <iostream>
using namespace std;

int main() {
    char newline = '\n';
    char tab = '\t';
    char backspace = '\b';
    char backslash = '\\';
    char nullChar = '\0';

    cout << "Newline character: " << newline << "ending" << endl;
    cout << "Tab character: " << tab << "ending" << endl;
    cout << "Backspace character: " << backspace << "ending" << endl;
    cout << "Backslash character: " << backslash << "ending" << endl;
    cout << "Null character: " << nullChar << "ending" << endl;
}
/* Output:
Newline character:
ending
Tab character:  ending
Backspace character:ending
Backslash character: \ending
Null character:  ending
*/
```

Znak zpětného lomítka (\\) je znak pro pokračování řádku, když je umístěn na konci řádku. Pokud chcete, aby se znak zpětného lomítka zobrazil jako znakový literál, je nutné zadat dvě zpětná lomítka v řádku (`\\`). Další informace o znaku pro pokračování řádku naleznete v tématu [fáze překladu](../preprocessor/phases-of-translation.md).

#### <a name="microsoft-specific"></a>specifické pro společnost Microsoft

Chcete-li vytvořit hodnotu z zúženého literálu s jedním znakem, kompilátor převede znak nebo sekvenci znaků mezi jednotlivými uvozovkami na 8bitové hodnoty v 32 celé číslo. Více znaků v literálu vyplní odpovídající bajty podle potřeby z vysokého řádu na nižší. Kompilátor pak převede celé číslo na cílový typ podle obvyklých pravidel. Chcete-li například vytvořit hodnotu typu **char** , kompilátor vezme bajt s nižším pořadím. Chcete-li vytvořit hodnotu **wchar_t** nebo `char16_t`, kompilátor vezme slovo s nižším pořadím. Kompilátor upozorní, že výsledek je zkrácen, pokud jsou všechny bity nastaveny nad přiřazeným bajtem nebo slovem.

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
int i0     = 'abcd';    // 0x61626364
```

Osmičková řídicí sekvence, která se zdá, že obsahuje více než tři číslice, je považována za tři číslice, následované následujícími číslicemi jako znaky v literálu s více znaky, což může vést k překvapivé výsledků. Například:

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

Řídicí sekvence, které vypadají jako neosmičkové znaky, jsou vyhodnoceny jako osmičková sekvence až do posledního osmičkového znaku následovaný zbývajícími znaky jako následující znaky v literálu s více znaky. Pokud je první neosmičkový znak desítkové číslice, vygeneruje se upozornění C4125. Například:

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

Osmičková řídicí sekvence, která má vyšší hodnotu než `\377` způsobí chybu C2022:*hodnota-in-Decimal*: příliš velká pro znak.

Řídicí sekvence, která se jeví jako šestnáctkové a nešestnáctkové znaky, je vyhodnocena jako literální znak, který obsahuje šestnáctkovou řídicí sekvenci až na poslední hexadecimální znak následovaný znaky, které nejsou hexadecimální. Šestnáctková řídicí sekvence, která neobsahuje žádné šestnáctkové číslice, způsobí chybu kompilátoru C2153: "hex literály musí mít alespoň jednu šestnáctkovou číslici".

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

Pokud se literály s velkým znakem, který je předponou `L`, obsahuje více sekvencí znaků, hodnota je pořízena z prvního znaku a kompilátor vyvolá upozornění C4066. Další znaky jsou ignorovány, na rozdíl od chování ekvivalentního obyčejného literálu s více znaky.

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

Část **týkající se Microsoftu** končí tady.

### <a name="bkmk_UCN"></a>Univerzální názvy znaků

V literálech znaků a nativních (nezpracovaných) řetězcových literálů může být libovolný znak reprezentován univerzálním názvem znaku.  Univerzální názvy znaků jsou tvořeny předponou `\U` následovanou bodem kódování Unicode, nebo prefixem `\u` následovaným čtyřmi číslicemi bodu kódu Unicode. Aby se vytvořil název univerzálního znaku, musí být k dispozici všechny osm nebo čtyři číslice (v uvedeném pořadí).

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>Náhradní páry

Univerzální názvy znaků nemůžou kódovat hodnoty v rozsahu bodu nahrazení D800-DFFF. Pro náhradní páry Unicode zadejte univerzální název znaku pomocí `\UNNNNNNNN`, kde NNNNNNNN je osmimístný bod kódu pro daný znak. Kompilátor vygeneruje v případě potřeby náhradní dvojici.

V jazyce C++ 03 jazyk povoluje pouze podmnožinu znaků, které mají být reprezentovány svými názvy univerzálních znaků, a povoluje některé univerzální názvy znaků, které ve skutečnosti nepředstavovaly platné znaky kódování Unicode. Tato chyba byla opravena ve standardu C++ 11. V jazyce C++ 11 mohou znakové a řetězcové literály a identifikátory používat univerzální názvy znaků.  Další informace o univerzálních názvech znaků naleznete v tématu [znakové sady](../cpp/character-sets.md). Další informace o kódování Unicode naleznete v tématu [Unicode](/windows/win32/intl/unicode). Další informace o náhradních dvojicích naleznete v tématu [náhradní páry a doplňující znaky](/windows/win32/Intl/surrogates-and-supplementary-characters).

## <a name="string-literals"></a>Řetězcové literály

Řetězcový literál představuje posloupnost znaků, které dohromady tvoří řetězec zakončený hodnotou null. Znaky musí být uzavřeny mezi dvojité uvozovky. Existují následující typy řetězcových literálů:

### <a name="narrow-string-literals"></a>Úzké řetězcové literály

Úzký řetězcový literál je nepevné, dvojité uvozovky, pole zakončené znakem null typu `const char[n]`, kde n je délka pole v bajtech. Úzký řetězcový literál může obsahovat libovolný grafický znak kromě dvojité uvozovky (`"`), zpětného lomítka (`\`) nebo znaku nového řádku. Úzký řetězcový literál může obsahovat také řídicí sekvence uvedené výše a univerzální názvy znaků, které se vejdou do bajtu.

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>Řetězce kódované v kódování UTF-8

Řetězec zakódovaný v kódování UTF-8 je hodnota "U8", která je ohraničena dvojitými uvozovkami, pole zakončené znakem null typu `const char[n]`, kde *n* je délka kódovaného pole v bajtech. Textový literál U8 a-fixed může obsahovat libovolný grafický znak kromě dvojité uvozovky (`"`), zpětného lomítka (`\`) nebo znaku nového řádku. Textový literál s názvem U8 může také obsahovat řídicí sekvence, které jsou uvedeny výše, a jakýkoli univerzální název znaku.

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>Velké řetězcové literály

Velký řetězcový literál je pole zakončené znakem null konstanty **wchar_t** , které má předponu "`L`" a obsahuje libovolný grafický znak kromě dvojité uvozovky ("), zpětného lomítka (\\) nebo znaku nového řádku. Libovolný řetězcový literál může obsahovat řídicí sekvence uvedené výše a jakýkoli univerzální název znaku.

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16_t-and-char32_t-c11"></a>char16_t a char32_t (C++ 11)

C++ 11 zavádí přenosné `char16_t` (16bitové kódování Unicode) a `char32_t` (32-bit Unicode) typy znaků:

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>Nezpracované řetězcové literály (C++ 11)

Nezpracovaný řetězcový literál je pole zakončené znakem null – libovolný typ znaku, který obsahuje libovolný grafický znak, včetně dvojité uvozovky ("), zpětného lomítka (\\) nebo znaku nového řádku. Nezpracované řetězcové literály se často používají v regulárních výrazech, které používají třídy znaků, a v řetězcích HTML a v řetězcích XML. Příklady najdete v následujícím článku: [Nejčastější dotazy k Bjarne Stroustrup na c++ 11](http://www.stroustrup.com/C++11FAQ.html).

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

Oddělovač je uživatelsky definovaná sekvence až 16 znaků, která bezprostředně předchází levé závorce nezpracovaného řetězcového literálu a hned následuje za pravou závorkou.  Například v `R"abc(Hello"\()abc"` sekvence oddělovače je `abc` a obsah řetězce je `Hello"\(`. Pomocí oddělovače můžete určit nezpracované řetězce, které obsahují dvojité uvozovky a závorky. Tento řetězcový literál způsobí chybu kompilátoru:

```cpp
// meant to represent the string: )"
const char* bad_parens = R"()")";  // error C2059
```

Ale tento oddělovač ho vyřeší:

```cpp
const char* good_parens = R"xyz()")xyz";
```

Můžete sestavit nezpracovaný řetězcový literál, který obsahuje nový řádek (ne řídicí znak) ve zdroji:

```cpp
// represents the string: hello
//goodbye
const wchar_t* newline = LR"(hello
goodbye)";
```

### <a name="stdstring-literals-c14"></a>std:: String – literály (C++ 14)

`std::string` literály jsou standardními implementacemi literálů definovaných uživatelem (viz níže), které jsou reprezentovány jako `"xyz"s` (s příponou `s`). Tento druh řetězcového literálu vytváří dočasný objekt typu `std::string`, `std::wstring`, `std::u32string`nebo `std::u16string`, v závislosti na zadané předponě. Pokud se nepoužije žádná předpona, jak je uvedeno výše, `std::string` je vytvořen. `L"xyz"s` vytváří `std::wstring`. `u"xyz"s` vytvoří [std:: u16string](../standard-library/string-typedefs.md#u16string)a `U"xyz"s` vytvoří [std:: u32string](../standard-library/string-typedefs.md#u32string).

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

Pro nezpracované řetězcové literály se můžou použít taky přípony `s`:

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

`std::string` literály jsou definovány v oboru názvů `std::literals::string_literals` v \<m souboru hlaviček >. Vzhledem k tomu, že `std::literals::string_literals`a `std::literals` jsou deklarovány jako [vložené obory názvů](../cpp/namespaces-cpp.md), `std::literals::string_literals` je automaticky považována za, jako by patřila přímo do `std`oboru názvů.

### <a name="size-of-string-literals"></a>Velikost řetězcových literálů

Pro kódování ANSI `char*` řetězců a dalších jednobajtových kódování (ale ne UTF-8) je velikost řetězcového literálu (v bajtech) řetězcového literálu počet znaků plus 1 pro ukončující znak null. Pro všechny ostatní typy řetězců není velikost přesně spojena s počtem znaků. UTF-8 používá až čtyři prvky pro kódování některých *jednotek kódu*a `char16_t` nebo `wchar_t` KÓDOVANÝ jako UTF-16 můžou použít **dva prvky (** celkem čtyři bajty) ke kódování jedné *jednotky kódu*. V tomto příkladu se zobrazuje velikost textového literálu v bajtech:

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

Všimněte si, že `strlen()` a `wcslen()` neobsahují velikost ukončujícího znaku null, jehož velikost je rovna velikosti prvku typu řetězec: jeden bajt na `char*` nebo `char8_t*` řetězec, dva bajty na `wchar_t*` nebo `char16_t*` řetězce a čtyři bajty na `char32_t*`ch řetězcích.

Maximální délka řetězcového literálu je 65 535 bajtů. Toto omezení platí pro úzké řetězcové literály i pro velké řetězcové literály.

### <a name="modifying-string-literals"></a>Úprava literálů řetězce

Vzhledem k tomu, že řetězcové literály (bez `std::string` literály) jsou konstanty, které se pokoušejí upravit – například `str[2] = 'A'`, způsobí chybu kompilátoru.

#### <a name="microsoft-specific"></a>specifické pro společnost Microsoft

V Microsoftu C++můžete použít řetězcový literál k inicializaci ukazatele na nekonstantní **znak** nebo **wchar_t**. Tato nekonstantní inicializace je povolena v C99 kódu, ale je zastaralá v C++ 98 a odebrána v C++ 11. Pokus o změnu řetězce způsobí porušení přístupu, jako v tomto příkladu:

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

Můžete způsobit, že kompilátor vygeneruje chybu, pokud je řetězcový literál převeden na ukazatel nekonstantního znaku při nastavení možnosti kompilátoru [/Zc: strictStrings (Disable převod typu string literal)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) . Doporučujeme pro přenos přenositelného kódu kompatibilního se standardem. Je také vhodné použít klíčové slovo **auto** k deklaraci ukazatelů inicializovaných řetězcovým literálem, protože se překládá na správný typ (const). Tento příklad kódu například zachytí pokus o zápis do řetězcového literálu v době kompilace:

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

V některých případech mohou být do fondu uloženy identické řetězcové literály, aby se ušetřilo místo ve spustitelném souboru. V rámci sdružování řetězcového literálu kompilátor způsobí, že všechny odkazy na konkrétní řetězcový literál odkazují na stejné místo v paměti, místo aby každý odkaz odkazoval na samostatnou instanci řetězcového literálu. Chcete-li povolit sdružování řetězců, použijte možnost kompilátoru [/GF](../build/reference/gf-eliminate-duplicate-strings.md) .

Část **týkající se Microsoftu** končí tady.

### <a name="concatenating-adjacent-string-literals"></a>Zřetězení sousedících řetězcových literálů

Sousední a úzké řetězcové literály jsou zřetězeny. Tato deklarace:

```cpp
char str[] = "12" "34";
```

je stejná jako tato deklarace:

```cpp
char atr[] = "1234";
```

a do této deklarace:

```cpp
char atr[] =  "12\
34";
```

Použití vložených hexadecimálních řídicích kódů pro určení řetězcových literálů může způsobit neočekávané výsledky. V následujícím příkladu se vytvoří řetězcový literál, který obsahuje znak ASCII 5 následovaný znaky f, i, v a e:

```cpp
"\x05five"
```

Skutečný výsledek je hexadecimální 5F, což je kód ASCII pro podtržítko následovaný znaky i, v a e. Chcete-li získat správný výsledek, můžete použít jednu z těchto řídicích sekvencí:

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

`std::string` literály, protože jsou `std::string` typy, lze zřetězit pomocí operátoru `+`, který je definován pro [basic_string](../standard-library/basic-string-class.md) typy. Lze je také zřetězit stejným způsobem jako sousední řetězcové literály. V obou případech musí kódování řetězce a přípona odpovídat:

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>Řetězcové literály s názvy univerzálních znaků

Nativní (nezpracované) řetězcové literály mohou používat univerzální názvy znaků k reprezentaci libovolného znaku, pokud je název Universal Character možné kódovat jako jeden nebo více znaků v typu řetězce.  Například univerzální název znaku představující rozšířený znak nelze zakódovat v úzkém řetězci pomocí znakové stránky ANSI, ale může být kódovaný v úzkých řetězcích v některých vícebajtových znakových stránkách nebo v řetězcích UTF-8 nebo v rámci celé řady. V jazyce C++ 11 je podpora kódování Unicode rozšířena o `char16_t*` a `char32_t*` typech řetězců:

```cpp
// ASCII smiling face
const char*     s1 = ":-)";

// UTF-16 (on Windows) encoded WINKING FACE (U+1F609)
const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)";

// UTF-8  encoded SMILING FACE WITH HALO (U+1F607)
const char*     s3 = u8"😇 = \U0001F607 is O:-)";

// UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603)
const char16_t* s4 = u"😃 = \U0001F603 is :-D";

// UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E)
const char32_t* s5 = U"😎 = \U0001F60E is B-)";
```

## <a name="see-also"></a>Viz také

[Znakové sady](../cpp/character-sets.md)\
[Číselné, logické a literály ukazatelů](../cpp/numeric-boolean-and-pointer-literals-cpp.md)\
[Uživateli definované literály](../cpp/user-defined-literals-cpp.md)
