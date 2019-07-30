---
title: Řetězcové a znakové literályC++()
description: Jak deklarovat a definovat řetězcové a znakové literály v C++.
ms.date: 07/29/2019
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
ms.openlocfilehash: 9fce1ef9636aaa85be71cafffb5c4247e5c2e2d9
ms.sourcegitcommit: 20a1356193fbe0ddd1002e798b952917eafc3439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661516"
---
# <a name="string-and-character-literals--c"></a>Řetězcové a znakové literályC++()

C++podporuje různé typy řetězců a znaků a poskytuje způsoby, jak vyjádřit hodnoty literálu každého z těchto typů. Ve vašem zdrojovém kódu budete vyjadřovat obsah znakových a řetězcových literálů pomocí znakové sady. Univerzální názvy znaků a řídicí znaky umožňují vyjádřit libovolný řetězec pouze pomocí základní zdrojové znakové sady. Nezpracovaný řetězcový literál umožňuje vyhnout se použití ukončovacích znaků a lze jej použít k vyjádření všech typů řetězcových literálů. Můžete také vytvořit `std::string` literály bez nutnosti provádět dodatečné kroky konstrukce nebo převodu.

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

Řetězcové literály nemohou mít předpony, `u8`ani `L`, `u`, `U` a předpony k označení úzkého znaku (jednobajtové nebo vícebajtového), UTF-8, roztažitelné znaku (UCS-2 nebo UTF-16 32), v uvedeném pořadí. Nezpracovaný řetězcový literál může obsahovat `R`předpony `LR`, `uR` `u8R`,, `UR` a pro nezpracované ekvivalenty verzí těchto kódování.  Chcete-li vytvořit dočasné `std::string` nebo statické hodnoty, můžete použít řetězcové literály nebo nezpracované řetězcové `s` literály s příponou. Další informace naleznete níže v části [řetězcové literály](#string-literals) . Další informace o základní zdrojové znakové sadě, univerzální názvy znaků a použití znaků z rozšířených znakových sad ve zdrojovém kódu naleznete v tématu [znakové sady](../cpp/character-sets.md).

## <a name="character-literals"></a>Literály znaků

*Znakový literál* se skládá z konstantního znaku. Je reprezentován znakem uzavřeným do jednoduchých uvozovek. Existuje pět druhů znakových literálů:

- Běžné znakové literály typu **char**, například`'a'`

- Znakové literály UTF-8 typu **char**, například`u8'a'`

- Literály s velkým znakem typu `wchar_t`, například`L'a'`

- Literály znaků UTF-16 typu `char16_t`, například`u'a'`

- Literály znaků UTF-32 typu `char32_t`, například`U'a'`

Znak použitý pro znakový literál může být libovolný znak, s výjimkou zpětného lomítka (\\' '), jednoduché uvozovky (') nebo nového řádku. Vyhrazené znaky lze zadat pomocí řídicí sekvence. Znaky mohou být zadány pomocí univerzálních názvů znaků, pokud je typ dostatečně velký pro uložení znaku.

### <a name="encoding"></a>Kódování

Znakové literály se kódují odlišně na základě jejich předpony.

- Znakový literál bez předpony je běžný znakový literál. Hodnota obyčejného znakového literálu, který obsahuje jeden znak, řídicí sekvenci nebo univerzální název znaku, který lze reprezentovat ve znakové sadě spuštění, má hodnotu rovnou číselné hodnotě jeho kódování ve znakové sadě spuštění. Běžný znakový literál, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je *literální znak*. Literál s více znakovými písmeny nebo běžný znakový literál, který nelze reprezentovat ve znakové sadě spuštění, je podmíněně podporován, je typu **int**a jeho hodnota je definovaná implementací.

- Znakový literál, který začíná `L` předponou, je literál s velkým znakem. Hodnota literálu s velkým znakem obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se číselnou hodnotou svého kódování v sadě s velkým znakem, pokud znak literálu nemá žádné reprezentace v je-li nastavena 64bitová znaková sada, v takovém případě je hodnota definována jako implementace. Hodnota literálu s velkým znakem, který obsahuje více znaků, řídicí sekvence nebo názvy univerzálních znaků, je definována implementací.

- Znakový literál, který začíná `u8` předponou, je znakový literál UTF-8. Hodnota literálu znaku UTF-8 obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se hodnotě bodu kódu ISO 10646, pokud může být reprezentována jednou jednotkou znakové sady UTF-8 (odpovídající ovládacím prvkům C0 a základní latinkou Blok kódování Unicode). Pokud hodnota nemůže být reprezentovaná jednou jednotkou znakové sady UTF-8, program je nesprávně vytvořen. Znakový literál UTF-8, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je nesprávně vytvořen.

- Znakový literál začínající `u` předponou je znakový literál UTF-16. Hodnota znakového literálu ve formátu UTF-16 obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se hodnotě bodu kódu ISO 10646, pokud může být reprezentovaná jednou jednotkou UTF-16 (odpovídající rovině Basic multi-Sequence). ). Pokud hodnota nemůže být reprezentovaná jednou jednotkou znakové sady UTF-16, program je nesprávně vytvořen. Znakový literál UTF-16, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je nesprávně vytvořen.

- Znakový literál začínající `U` předponou je znakový literál UTF-32. Hodnota literálu znaku UTF-32 obsahující jeden znak, řídicí sekvence nebo univerzální název znaku má hodnotu rovnající se hodnotě bodu kódu ISO 10646. Znakový literál UTF-32, který obsahuje více než jeden znak, řídicí sekvenci nebo univerzální název znaku, je nesprávně vytvořen.

###  <a name="bkmk_Escape"></a>Řídicí sekvence

Existují tři druhy řídicích sekvencí: jednoduché, osmičkové a hexadecimální. Řídicí sekvence mohou být následující:

|Value|Řídicí sekvence|
|-----------|---------------------|
| newline | \\n |
| zpětné lomítko | \\\\ |
| horizontální karta | \\t |
| otazník | ? nebo \\? |
| svislá karta | \\v |
| jednoduchá uvozovka | \\' |
| BACKSPACE | \\b |
| dvojité uvozovky | \\" |
| návrat na začátek řádku | \\r |
| znak null | \\0 |
| Posun strany | \\f |
| osmičkové | \\OOO |
| upozornění (zvonek) | \\a |
| hexadecimální | \\xhhh |

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

    cout << "Newline character: " << newline << "ending" << endl; // Newline character:
                                                                  //  ending
    cout << "Tab character: " << tab << "ending" << endl; // Tab character : ending
    cout << "Backspace character: " << backspace << "ending" << endl; // Backspace character : ending
    cout << "Backslash character: " << backslash << "ending" << endl; // Backslash character : \ending
    cout << "Null character: " << nullChar << "ending" << endl; //Null character:  ending
}
```

**Specifické pro společnost Microsoft**

Chcete-li vytvořit hodnotu z obyčejného znakového literálu (bez předpony), kompilátor převede znak nebo sekvenci znaků mezi jednotlivými uvozovkami na 8bitové hodnoty v rámci 32 celého čísla. Více znaků v literálu vyplní odpovídající bajty podle potřeby z vysokého řádu na nižší. Chcete-li vytvořit hodnotu typu **char** , kompilátor vezme bajt s nižším pořadím. Chcete-li vytvořit wchar_t `char16_t` nebo hodnotu, kompilátor vezme slovo s nižším pořadím. Kompilátor upozorní, že výsledek je zkrácen, pokud jsou všechny bity nastaveny nad přiřazeným bajtem nebo slovem.

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
```

Osmičková řídicí sekvence je zpětné lomítko následované sekvencí až 3 osmičkových číslic. Chování osmičkové řídicí sekvence, která se zdá, že obsahuje více než tři číslice, je považována za tři číslice, následované následujícími číslicemi jako znaky, což může vést k překvapivé výsledkům. Příklad:

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

Řídicí sekvence, které vypadají jako obsahující neosmičkové znaky, jsou vyhodnocovány jako osmičková sekvence až po poslední osmičkový znak následovaný zbývajícími znaky. Příklad:

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

Šestnáctková řídicí sekvence je zpětné lomítko následované znakem `x`následovaný sekvencí šestnáctkových číslic. Řídicí sekvence, která neobsahuje žádné šestnáctkové číslice, způsobí chybu kompilátoru C2153: "hex literály musí mít alespoň jednu šestnáctkovou číslici". Úvodní nuly jsou ignorovány. Řídicí sekvence, která se jeví jako šestnáctkové a nešestnáctkové znaky, je vyhodnocena jako šestnáctková řídicí sekvence až do posledního šestnáctkového znaku následovaný nešestnáctkovými znaky. V běžném nebo U8 s předem opraveným znakovým literálem je nejvyšší šestnáctková hodnota 0xFF. V literálu předplatného, který je v předplatném, je nejvyšší šestnáctková hodnota 0xFFFF. V rámci předplatného literálu U znaku U, nejvyšší šestnáctková hodnota je 0xFFFFFFFF.

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

Pokud se literály s `L` velkým znakem a obsahují více než jeden znak, hodnota se převezme z prvního znaku. Další znaky jsou ignorovány na rozdíl od chování ekvivalentního obyčejného znakového literálu.

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

**Specifické pro konec Microsoftu**

Znak zpětného lomítka\\() je znak pro pokračování řádku, když je umístěn na konci řádku. Pokud chcete, aby se znak zpětného lomítka zobrazil jako znakový literál, je nutné zadat dvě zpětná lomítka v řádku`\\`(). Další informace o znaku pro pokračování řádku naleznete v tématu [fáze překladu](../preprocessor/phases-of-translation.md).

###  <a name="bkmk_UCN"></a>Univerzální názvy znaků

V literálech znaků a nativních (nezpracovaných) řetězcových literálů může být libovolný znak reprezentován univerzálním názvem znaku.  Univerzální názvy znaků jsou tvořeny předponou `\U` následovanou osmimístným bodem kódování Unicode nebo prefixem `\u` následovaným čtyřmi číslicemi bod kódu Unicode. Aby se vytvořil název univerzálního znaku, musí být k dispozici všechny osm nebo čtyři číslice (v uvedeném pořadí).

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>Náhradní páry

Univerzální názvy znaků nemůžou kódovat hodnoty v rozsahu bodu nahrazení D800-DFFF. Pro náhradní páry Unicode zadejte univerzální název znaku pomocí `\UNNNNNNNN`, kde nnnnnnnn je osmimístný bod kódu pro daný znak. Kompilátor vygeneruje v případě potřeby náhradní dvojici.

V jazyce C++ 03 jazyk povoluje pouze podmnožinu znaků, které mají být reprezentovány svými názvy univerzálních znaků, a povoluje některé univerzální názvy znaků, které ve skutečnosti nepředstavovaly platné znaky kódování Unicode. Tato chyba byla opravena ve standardu C++ 11. V jazyce C++ 11 mohou znakové a řetězcové literály a identifikátory používat univerzální názvy znaků.  Další informace o univerzálních názvech znaků naleznete v tématu [znakové sady](../cpp/character-sets.md). Další informace o kódování Unicode naleznete v tématu [Unicode](https://msdn.microsoft.com/library/dd374081). Další informace o náhradních dvojicích naleznete v tématu [náhradní páry a doplňující znaky](/windows/desktop/Intl/surrogates-and-supplementary-characters).

## <a name="string-literals"></a>Řetězcové literály

Řetězcový literál představuje posloupnost znaků, které dohromady tvoří řetězec zakončený hodnotou null. Znaky musí být uzavřeny mezi dvojité uvozovky. Existují následující typy řetězcových literálů:

### <a name="narrow-string-literals"></a>Úzké řetězcové literály

Úzký řetězcový literál je nepevné, dvojité uvozovky, pole `const char[n]`zakončené znakem null, kde n je délka pole v bajtech. Úzký řetězcový literál může obsahovat libovolný grafický znak kromě dvojité uvozovky (`"`), zpětného lomítka (`\`) nebo znaku nového řádku. Úzký řetězcový literál může obsahovat také řídicí sekvence uvedené výše a univerzální názvy znaků, které se vejdou do bajtu.

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>Řetězce kódované v kódování UTF-8

Řetězec zakódovaný v kódování UTF-8 je typ `const char[n]`"předpevněný", oddělený uvozovky, pole zakončené znakem null, kde *n* je délka kódovaného pole v bajtech. Textový literál U8 a-fixed může obsahovat libovolný grafický znak kromě dvojité uvozovky (`"`), zpětného lomítka (`\`) nebo znaku nového řádku. Textový literál s názvem U8 může také obsahovat řídicí sekvence, které jsou uvedeny výše, a jakýkoli univerzální název znaku.

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>Velké řetězcové literály

Velký řetězcový literál je pole zakončené znakem null konstanty **wchar_t** , které má předponu`L`' ' a obsahuje libovolný grafický znak kromě dvojité uvozovky ("), zpětného lomítka (\\) nebo znaku nového řádku. Libovolný řetězcový literál může obsahovat řídicí sekvence uvedené výše a jakýkoli univerzální název znaku.

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16t-and-char32t-c11"></a>char16_t a char32_t (C++ 11)

C++ 11 zavádí přenosné `char16_t` (16bitové znakové sady Unicode) a `char32_t` (32-bit Unicode) typy znaků:

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>Nezpracované řetězcové literály (C++ 11)

Nezpracovaný řetězcový literál je pole zakončené znakem null – libovolný typ znaku, který obsahuje libovolný grafický znak, včetně dvojité uvozovky ("), zpětného lomítka\\() nebo znaku nového řádku. Nezpracované řetězcové literály se často používají v regulárních výrazech, které používají třídy znaků, a v řetězcích HTML a v řetězcích XML. Příklady najdete v následujícím článku: [Nejčastější dotazy k Bjarne Stroustrup na c++ 11](http://www.stroustrup.com/C++11FAQ.html).

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

Oddělovač je uživatelsky definovaná sekvence až 16 znaků, která bezprostředně předchází levé závorce nezpracovaného řetězcového literálu a hned následuje za pravou závorkou.  Například v `R"abc(Hello"\()abc"` sekvenci oddělovače je `abc` a obsah řetězce je `Hello"\(`. Pomocí oddělovače můžete určit nezpracované řetězce, které obsahují dvojité uvozovky a závorky. Tento řetězcový literál způsobí chybu kompilátoru:

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

`std::string`literály jsou standardní implementace knihoven literálů definovaných uživatelem (viz níže), které jsou reprezentovány `"xyz"s` jako ( `s` s příponou). Tento druh řetězcového literálu vytváří dočasný objekt `std::string`typu `std::u32string`, `std::wstring`, nebo `std::u16string`, v závislosti na zadané předponě. Není- `std::string` li použita žádná předpona, jak je uvedeno výše, je vytvořena. `L"xyz"s``std::wstring`vytvoří. `u"xyz"s`vytvoří [std:: u16string](../standard-library/string-typedefs.md#u16string)a `U"xyz"s` vytvoří [std:: u32string](../standard-library/string-typedefs.md#u32string).

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

`s` Přípona se dá použít taky u nezpracovaných řetězcových literálů:

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

`std::string`literály jsou definovány v oboru názvů `std::literals::string_literals` \<v řetězcové > hlavičkovém souboru. Vzhledem `std::literals::string_literals`k tomu `std::literals` , že a jsou deklarovány jako `std::literals::string_literals` [vložené obory názvů](../cpp/namespaces-cpp.md), se automaticky považují za, `std`jako by patřily přímo do oboru názvů.

### <a name="size-of-string-literals"></a>Velikost řetězcových literálů

V případě `char*` řetězců ANSI a dalších jednobajtových kódování (ale ne UTF-8) je velikost řetězcového literálu (v bajtech) řetězcového literálu počet znaků plus 1 pro ukončující znak null. Pro všechny ostatní typy řetězců není velikost přesně spojena s počtem znaků. Kódování UTF-8 používá **až čtyři prvky** pro kódování některých *jednotek kódu* `char16_t` a nebo `wchar_t` zakódovaných jako UTF-16 může použít dva prvky (celkem čtyři bajty) ke kódování jedné *jednotky kódu*. V tomto příkladu se zobrazuje velikost textového literálu v bajtech:

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

Všimněte si `strlen()` , `wcslen()` že a neobsahují velikost ukončujícího znaku null, jehož velikost je rovna velikosti prvku typu řetězec `char*` : jeden bajt v řetězci, dva bajty na `wchar_t*` nebo `char16_t*` řetězce a čtyři počet bajtů `char32_t*` v řetězcích.

Maximální délka řetězcového literálu je 65 535 bajtů. Toto omezení platí pro úzké řetězcové literály i pro velké řetězcové literály.

### <a name="modifying-string-literals"></a>Úprava literálů řetězce

Vzhledem k tomu, že řetězcové `std::string` literály (bez literálů) jsou konstanty, pokusí se je `str[2] = 'A'`změnit, například – způsobí chybu kompilátoru.

**Specifické pro společnost Microsoft**

V Microsoftu C++můžete použít řetězcový literál k inicializaci ukazatele na nekonstantní **znak** nebo **wchar_t**. Tato nekonstantní inicializace je povolena v C99 kódu, ale je zastaralá v C++ 98 a odebrána v C++ 11. Pokus o změnu řetězce způsobí porušení přístupu, jako v tomto příkladu:

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

Můžete způsobit, že kompilátor vygeneruje chybu, pokud je řetězcový literál převeden na ukazatel non_const znaku při nastavení možnosti kompilátoru [/Zc: strictStrings (Disable převod typu string literal)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) . Doporučujeme pro přenos přenositelného kódu kompatibilního se standardem. Je také vhodné použít klíčové slovo **auto** k deklaraci ukazatelů inicializovaných řetězcovým literálem, protože se překládá na správný typ (const). Tento příklad kódu například zachytí pokus o zápis do řetězcového literálu v době kompilace:

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

V některých případech mohou být do fondu uloženy identické řetězcové literály, aby se ušetřilo místo ve spustitelném souboru. V rámci sdružování řetězcového literálu kompilátor způsobí, že všechny odkazy na konkrétní řetězcový literál odkazují na stejné místo v paměti, místo aby každý odkaz odkazoval na samostatnou instanci řetězcového literálu. Chcete-li povolit sdružování řetězců, použijte možnost kompilátoru [/GF](../build/reference/gf-eliminate-duplicate-strings.md) .

**Specifické pro konec Microsoftu**

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

Skutečný výsledek je hexadecimální 5F, což je kód ASCII pro podtržítko následovaný znaky i, v a e. Chcete-li získat správný výsledek, můžete použít jednu z těchto akcí:

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

`std::string`literály, protože jsou `std::string` typy, mohou být zřetězeny `+` s operátorem definovaným pro typy [basic_string](../standard-library/basic-string-class.md) . Lze je také zřetězit stejným způsobem jako sousední řetězcové literály. V obou případech musí kódování řetězce a přípona odpovídat:

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>Řetězcové literály s názvy univerzálních znaků

Nativní (nezpracované) řetězcové literály mohou používat univerzální názvy znaků k reprezentaci libovolného znaku, pokud je název Universal Character možné kódovat jako jeden nebo více znaků v typu řetězce.  Například univerzální název znaku představující rozšířený znak nelze zakódovat v úzkém řetězci pomocí znakové stránky ANSI, ale může být kódovaný v úzkých řetězcích v některých vícebajtových znakových stránkách nebo v řetězcích UTF-8 nebo v rámci celé řady. V jazyce c++ 11 je podpora kódování Unicode rozšířena `char16_t*` o `char32_t*` typy řetězců a:

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

## <a name="see-also"></a>Viz také:

[Znakové sady](../cpp/character-sets.md)<br/>
[Číselné literály, logické a literály typu ukazatele](../cpp/numeric-boolean-and-pointer-literals-cpp.md)<br/>
[Uživateli definované literály](../cpp/user-defined-literals-cpp.md)
