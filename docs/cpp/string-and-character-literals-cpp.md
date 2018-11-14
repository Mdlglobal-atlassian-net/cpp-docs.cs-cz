---
title: Řetězcové a znakové literály (C++)
ms.date: 11/04/2016
f1_keywords:
- R
helpviewer_keywords:
- L constant
- escape sequences
- Null strings, null-terminated strings
- literal strings, C++
- Null strings
- string literals, syntax
- string literals
- literal strings
- strings [C++], string literals
- NULL, character constant
- wide characters, strings
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
ms.openlocfilehash: d3721f3624a64a24de0a5458d88de4836b07a9c1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329836"
---
# <a name="string-and-character-literals--c"></a>Řetězcové a znakové literály (C++)

C++ podporuje různé typy řetězců a znaků a nabízí způsobů, jak vyjádřit jednu hodnotu literálu každý z těchto typů. Ve zdrojovém kódu express obsah vaší znakové a řetězcové literály pomocí znakové sady. Univerzální názvy znaků a řídicích znaků umožňují express libovolný řetězec za použití pouze základní zdrojové znakové sady. Nezpracovaný Textový literál vám umožní předcházet pomocí řídicí znaky a je možné vyjádřit všech typů řetězcových literálů. Můžete také vytvořit std::string literály bez nutnosti provádět další konstrukci nebo převod kroky.

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

Řetězcové literály může mít žádná předpona nebo `u8`, `L`, `u`, a `U` předpony k označení zúžit znak (jednobajtové nebo vícebajtové), UTF-8, široký znak (UCS-2 nebo UTF-16), UTF-16 a UTF-32 kódování, v uvedeném pořadí. Nezpracovaný řetězcový literál může mít `R`, `u8R`, `LR`, `uR` a `UR` předpony pro ekvivalenty nezpracovaná verze těchto kódování.  K vytvoření dočasné nebo statické std::string hodnoty, můžete použít řetězcových literálů nebo nezpracované řetězcové literály s `s` příponu. Další informace najdete v článku následující části literály řetězce. Další informace o základní zdrojové znakové nastavit, univerzální názvy znaků a pomocí znaků z rozšířené kódové stránky ve zdrojovém kódu, najdete v tématu [znakových sad](../cpp/character-sets.md).

## <a name="character-literals"></a>Znakové literály

A *znakový literál* je tvořen konstantním znakem. Je reprezentován znakem uzavřeným v jednoduchých uvozovkách. Existuje pět typů literálů znaku:

- Běžný znak literálů typu **char**, například `'a'`

- UTF-8 znakových literálů typu **char**, například `u8'a'`

- Literály širokých znaků typu `wchar_t`, například `L'a'`

- UTF-16 znakových literálů typu `char16_t`, například `u'a'`

- UTF-32 znakových literálů typu `char32_t`, například `U'a'`

Znak použitý pro znak literálu může být libovolný znak, s výjimkou vyhrazených znaků zpětného lomítka ("\\"), jednoduché uvozovky (') nebo znaku nového řádku. Vyhrazené znaky lze zadat pomocí řídící sekvence. Znaky lze zadat pomocí univerzální názvy znaků, za předpokladu, typ je dostatečně velký pro znak.

### <a name="encoding"></a>Kódování

Znakové literály jsou kódovány odlišně podle jejich předpony.

- Běžný znak literálu je znak literálu bez předpony. Hodnota literálu běžný znak obsahující jeden znak řídicí sekvence, nebo univerzální název znaku, který může být reprezentována ve znakové sadě spuštění má hodnota se shoduje s číselnou hodnotu kódování ve znakové sadě spuštění. Běžný znak literálu, který obsahuje více než jeden znak řídicí sekvence a univerzální název znaku je *víceznakové literálu*. Víceznaková literál nebo běžný znak literálu, který nemůže být reprezentovaný ve znakové sadě spuštění je podmíněně podporovaný, má typ int a její hodnota je definován implementací.

- Znakový literál, který začíná příslušnou předponou L je literál širokého znaku. Hodnota literálu širokého znaku obsahující znak, řídicí sekvence nebo univerzální název znaku má hodnota se shoduje s číselnou hodnotu kódování v nastavit, pokud znakového literálu nemá zastoupení širokoznaké provádění nastavit širokého znaku spuštění, v takovém případě hodnota je definováno implementací. Hodnota literálu širokého znaku obsahující více znaků, řídicích sekvencí nebo univerzální názvy znaků je definován implementací.

- Znakový literál, který začíná příslušnou předponou u8 je literální znak kódování UTF-8. Hodnota UTF-8 znakový literál obsahující jeden znak řídicí sekvence, nebo univerzální název znaku má hodnota se shoduje s jeho hodnota bodu kódu ISO 10646, pokud může být reprezentována jednu jednotku kódu UTF-8 (odpovídající C0 ovládací prvky a základní latinky Blok sady Unicode). Pokud hodnota nemůže být reprezentována jednu jednotku kódu UTF-8, program má chybný formát. Znak kódování UTF-8 literál obsahující více než jeden znak řídicí sekvence a univerzální název znaku je chybně vytvořený.

- Znakový literál, který začíná u předpony je UTF-16 znakový literál. Hodnota UTF-16 znakový literál obsahující jeden znak řídicí sekvence, nebo univerzální název znaku má hodnota se shoduje s jeho hodnota bodu kódu ISO 10646, pokud může být reprezentována jednu jednotku kódu UTF-16 (odpovídající základní vícejazyčné roviny ). Pokud hodnota nemůže být reprezentována jednu jednotku kódu UTF-16, program má chybný formát. Literál obsahující více než jeden znak řídicí sekvence a univerzální název znaku UTF-16 znak má chybný formát.

- Znakový literál, který začíná U předpony je UTF-32 znakový literál. Hodnota UTF-32 znakový literál obsahující jeden znak řídicí sekvence, nebo univerzální název znaku má hodnota se shoduje s jeho hodnota bodu kódu ISO 10646. Znak kódování UTF-8 literál obsahující více než jeden znak řídicí sekvence a univerzální název znaku je chybně vytvořený.

###  <a name="bkmk_Escape"></a> Řídicí sekvence

Existují tři typy sekvence úniku: jednoduchá, osmičková a šestnáctková. Řídicí sekvence může být libovolná z následujících akcí:

|Hodnota|Řídicí sekvence|
|-----------|---------------------|
| newline | \\n |
| Zpětné lomítko | \\\\ |
| horizontální tabulátor | \\t |
| otazník | ? nebo \\? |
| vertikální tabulátor | \\V |
| jednoduché uvozovky | \\' |
| BACKSPACE | \\B |
| dvojité uvozovky | \\" |
| návrat na začátek řádku | \\r |
| znak null | \\0 |
| Posun strany | \\F |
| osmičkové | \\ooo |
| upozornění (zvonek) | \\A |
| hexadecimální | \\xhhh |

Následující kód ukazuje příklady použití literály běžný znak řídicí znaky. Podle stejné syntaxe řídicí sekvence je platný pro další znak literálu typy.

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

**Specifické pro Microsoft**

K vytvoření hodnoty z běžný znak literálu, (ta bez předpony), kompilátor převede znak nebo posloupnost znaků mezi jednoduchými uvozovkami na 8bitové hodnoty v rámci 32bitové celé číslo. Více znaků v literálu vyplnit odpovídající bajtů podle potřeby od nejvyšší k nejnižší. Chcete-li vytvořit **char** hodnota, kompilátor má nejnižší bajt. Chcete-li vytvořit **wchar_t** nebo `char16_t` hodnota, kompilátor má nižší řád slova. Kompilátor vás upozorní, že výsledek je zkrácen, pokud všechny bity jsou nastaveny nad přiřazené bajtů nebo word.

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
```

Osmičková řídicí sekvence je zpětné lomítko následované sekvencí až 3 osmičkových číslic. Chování oktalových řídících sekvencí, které se zobrazí tak, aby obsahovala více než tři číslice, je považováno za 3 číslice osmičková sekvence a následné číslicemi jako znaků. To vám může poskytnout překvapivé výsledky. Příklad:

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

Řídicí sekvence, které se zobrazují na obsahují neosmičkové znaky jsou vyhodnoceny jako osmičková sekvence až po poslední znak osmičkové, za nímž následuje zbývající znaky. Příklad:

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

Šestnáctková řídicí sekvence je zpětné lomítko následované znakem `x`, následované posloupnosti hexadecimálních číslic. Sekvence escape neobsahuje žádné šestnáctkové číslice způsobí chybu kompilátoru C2153: "šestnáctkové literály musí mít alespoň jednu číslici hex". Počáteční nuly jsou ignorovány. Sekvence escape, která má šestnáctkové a nešestnáctkové znaky je vyhodnocena jako šestnáctková řídicí sekvence až po poslední znak šestnáctkové, následované znaky nešestnáctkový.   V běžné nebo tvoří jeho předponu u8 znak literálu nejvyšší šestnáctková hodnota je 0xFF. Nejvyšší šestnáctková hodnota v předponu L u předpony široký znak nebo literálu, je 0xFFFF. V U předpony široký znak literálu je nejvyšší šestnáctková hodnota 0xFFFFFFFF.

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

Pokud literál širokého znaku s předponou `L` obsahuje více než jeden znak, hodnota je převzata z prvního znaku. Následující znaky jsou ignorovány, na rozdíl od chování odpovídá běžnému znaku literálu.

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

**Specifické pro END Microsoft**

Znak zpětného lomítka (\\) je znak pro pokračování řádku, pokud je umístěn na konci řádku. Pokud chcete, aby zpětné lomítko jako literální znak, musí zadat dvě zpětná lomítka v řadě (`\\`). Další informace o znak pro pokračování řádku naleznete v tématu [fáze překladu](../preprocessor/phases-of-translation.md).

###  <a name="bkmk_UCN"></a> Univerzální názvy znaků

Znakové literály a nativní (bez –) literály nezpracovaných řetězců může být libovolný znak zastoupen univerzální název znaku.  Univerzální názvy znaků jsou tvořeny předpony, které následují \U bodem kódu Unicode v osmi číslicemi, nebo předponou \u za nímž následuje bod kódu Unicode čtyři číslice. Všechny osmi nebo čtyři číslice, v uvedeném pořadí, musí být k dispozici, aby ve správném formátu univerzální název znaku.

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>Náhradní dvojice

Univerzální názvy znaků nelze dekódovat hodnoty v náhradní rozsah bodového kódu D800 DFFF. Páry nahrazení Unicode, zadat název univerzálních znaků pomocí `\UNNNNNNNN`, kde je NNNNNNNN bodu osm 6místným číselným kódem znaku. Kompilátor generuje náhradní pár v případě potřeby.

V C ++ 03 jazyk pouze povolené podmnožinu znaků a nelze je reprezentovat podle jejich univerzální názvy znaků a povoleny některé univerzální názvy znaků, které skutečně nepředstavovala platnou znaky Unicode. Tato chyba byla opravena v C ++ 11 standard. V C ++ 11 můžete použít univerzální názvy znaků znakové a řetězcové literály a identifikátory.  Další informace o univerzální názvy znaků, naleznete v tématu [znakových sad](../cpp/character-sets.md). Další informace o kódování Unicode naleznete v tématu [Unicode](https://msdn.microsoft.com/library/dd374081). Další informace o náhradních párech naleznete v tématu [náhradní páry a doplňující znaky](/windows/desktop/Intl/surrogates-and-supplementary-characters).

## <a name="string-literals"></a>Řetězcové literály

Textový literál představuje posloupnost znaků, které společně tvoří řetězec zakončený hodnotou null. Znaky musí být uzavřeny mezi dvojité uvozovky. Existují následující typy řetězcových literálů:

### <a name="narrow-string-literals"></a>Úzký řetězcové literály

Úzký řetězcový literál je mimo předponou, dvojité uvozovky s oddělovači, zakončený hodnotou null pole typu `const char[n]`, kde n je délka pole v bajtech. Úzký řetězcový literál může obsahovat libovolný grafický znak kromě dvojité uvozovky (`"`), zpětného lomítka (`\`), nebo znak nového řádku. Úzký řetězcový literál může obsahovat také názvy uvedené výše a univerzální znak řídicí sekvence, které přizpůsobit v bajtu.

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>Kódovaný řetězec UTF-8

Řetězec UTF-8 je u8 předponou, dvojité uvozovky s oddělovači, zakončený hodnotou null pole typu `const char[n]`, kde n je délka kódovaného pole v bajtech. Předponu u8 řetězcový literál může obsahovat libovolný grafický znak kromě dvojité uvozovky (`"`), zpětného lomítka (`\`), nebo znak nového řádku. Řetězcový literál s předponou u8 může také obsahovat řídicí sekvence je uvedena výše a všechny univerzální název znaku.

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>Široké řetězcové literály

Široký řetězcový literál je pole zakončené znakem null konstanty **wchar_t** , který má předponu "`L`" a obsahuje libovolný grafický znak kromě dvojité uvozovky ("), zpětného lomítka (\\), nebo znak nového řádku. Široký řetězcový literál může obsahovat řídicí sekvence je uvedena výše a všechny univerzální název znaku.

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16t-and-char32t-c11"></a>char16_t a char32_t (C ++ 11)

C ++ 11 zavádí přenosný počítač `char16_t` (16-bit Unicode) a `char32_t` (32bitová verze Unicode) znakové typy:

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>Literály nezpracovaných řetězců (C ++ 11)

Nezpracovaný Textový literál je pole zakončené znakem null – znak typu –, která obsahuje libovolný grafický znak včetně dvojité uvozovky ("), zpětného lomítka (\\), nebo znak nového řádku. Nezpracované řetězcové literály se často používají v regulárních výrazech, které používají třídy znaků a v řetězcích HTML a XML. Příklady najdete v následujícím článku: [Bjarne Stroustrup – nejčastější dotazy o C ++ 11](http://www.stroustrup.com/C++11FAQ.html).

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

Oddělovač je uživatelem definované sekvence až 16 znaků, která bezprostředně předchází levé závorce nezpracovaného textového literálu a následuje jeho pravou závorku.  Například v `R"abc(Hello"\()abc"` pořadí oddělovačů `abc` a obsah řetězce je `Hello"\(`. Můžete použít oddělovač k rozlišení nezpracovaných řetězců, které obsahují dvojité uvozovky i závorky. To způsobí chybu kompilátoru:

```cpp
// meant to represent the string: )"
const char* bad_parens = R"()")";  // error C2059
```

Ale to je řešeno oddělovačem:

```cpp
const char* good_parens = R"xyz()")xyz";
```

Můžete sestavit nezpracovaný řetězcový literál ve kterém je nový řádek (ne znak sekvence escape) ve zdroji:

```cpp
// represents the string: hello
//goodbye
const wchar_t* newline = LR"(hello
goodbye)";
```

### <a name="stdstring-literals-c14"></a>std::String literálů (C ++ 14)

std::String literály jsou uživatelem definované literály (viz níže), které jsou reprezentovány ve formě "xyx" s implementace standardní knihovny (s `s` přípony). Tento typ řetězcového literálu vytvoří dočasný objekt typu std::string, std::wstring, std::u32string nebo std::u16string v závislosti na předponu, která je zadána. Při použití žádná předpona jako výše, std::string je vytvořen. L "xyz" s vytváří std::wstring. vytvoří s u "xyz" [std::u16string](../standard-library/string-typedefs.md#u16string)a vytvoří s U "xyz" [std::u32string](../standard-library/string-typedefs.md#u32string).

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

Přípona s může být také použita na literály nezpracovaných řetězců:

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

std::String literály jsou definovány v oboru názvů `std::literals::string_literals` v \<řetězec > soubor hlaviček. Protože `std::literals::string_literals`, a `std::literals` jsou deklarovány jako [pomocí vložených oborů názvů](../cpp/namespaces-cpp.md), `std::literals::string_literals` automaticky zpracovávány jako by to patří, vytvářela přímo v oboru názvů `std`.

### <a name="size-of-string-literals"></a>Velikost řetězcových literálů

Pro ANSI char\* řetězce a další jednobajtové kódování (nikoli UTF-8), velikost (v bajtech) řetězcového literálu je počet znaků plus 1 pro ukončující znak null. Pro všechny ostatní typy řetězce velikost není v relaci výhradně na počet znaků. UTF-8 až čtyři prvky char používá ke kódování některé *znakové jednotky*a char16_t nebo wchar_t kódovaný jako UTF-16, můžete používat dva prvky (k celkem čtyři bajty) určený ke kódování jediného *jednotku kódu*.   Tento příklad ukazuje velikost širokého řetězce literálu v bajtech:

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

Všimněte si, že `strlen()` a `wcslen()` neobsahují velikost ukončujícího znaku null, jejichž velikost se rovná velikosti elementu typu řetězec: jeden bajt na znak\* string, dva bajty na wchar_t\* nebo char16_t\*řetězce a čtyři bajty v char32_t\* řetězce.

Maximální délka řetězce literálu je 65535 bajtů. Toto omezení platí pro úzké i široké řetězcové literály.

### <a name="modifying-string-literals"></a>Úprava literálů řetězce

Protože (nezahrnuje std:string literály) řetězcové literály jsou konstanty, pokus upravit je – například `str[2] = 'A'`– způsobí chybu kompilátoru.

**Specifické pro Microsoft**

V jazyce Visual C++ můžete použít textový literál k inicializaci ukazatele na nekonstantní **char** nebo **wchar_t**. To je povoleno v kódu C99, ale je zastaralé v C ++ 98 odebírají a v C ++ 11. Pokus upravit řetězec způsobuje narušení přístupu, jako v následujícím příkladu:

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

Může způsobit, že kompilátor generuje chybu při převodu řetězcového literálu na ukazatel na nekonstantní znak při nastavení [/Zc: strictstrings (zakázání převodů typů řetězcových literálů)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) – možnost kompilátoru. Doporučujeme ho pro standardům přenosného kódu. Je také vhodné k použití **automaticky** – klíčové slovo deklarovat řetězec iniciovaný textovým literálem ukazatele, protože se překládá na správný typ (const). Tento příklad kódu například zachycen například pokus o zápis do řetězcového literálu v době kompilace:

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

V některých případech mohou být shromážděny identické řetězcové literály a šetřit tak místo ve spustitelném souboru. Ve sdružování řetězcového literálu kompilátor způsobí, že všechny odkazy na konkrétní řetězcový literál budou odkazovat do stejného umístění v paměti namísto toho, aby každý odkaz přejděte na samostatnou instanci řetězcového literálu. Chcete-li povolit sdružování řetězců, použijte [/GF](../build/reference/gf-eliminate-duplicate-strings.md) – možnost kompilátoru.

**Specifické pro end Microsoft**

### <a name="concatenating-adjacent-string-literals"></a>Zřetězení sousedních řetězcových literálů

Sousední široký nebo úzký řetězcové literály jsou zřetězeny. Tato deklarace:

```cpp
char str[] = "12" "34";
```

je stejný jako tato deklarace:

```cpp
char atr[] = "1234";
```

a tato deklarace:

```cpp
char atr[] =  "12\
34";
```

Použití vložených hexadecimálních řídicích kódů k určení řetězcových literálů může způsobit neočekávané výsledky. Následující příklad se snaží o vytvoření literálu řetězce obsahujícího znaky ASCII 5, následované znaky f, i, v a e:

```cpp
"\x05five"
```

Skutečný výsledek je hexadecimální 5F, což je kód ASCII pro podtržítko, následované znaky i, v a e. Chcete-li získat správný výsledek, můžete použít jednu z těchto:

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

literály std::String, protože jsou typy std::string, mohou být spojeny s + – operátor, který je definován pro [basic_string](../standard-library/basic-string-class.md) typy. Také mohou být spojeny stejným způsobem jako sousedních textových literálů. V obou případech musí odpovídat kódování, řetězce a přípony:

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>Řetězcové literály s univerzální názvy znaků

Nativní (bez –) literály nezpracovaných řetězců mohou používat univerzální názvy znaků k zastupování libovolného znaku tak dlouho, dokud univerzální název znaku může být zakódován jako jeden nebo více znaků v typu řetězec.  Například univerzální název znaku představující znak rozšířené nemůže být kódovaný v úzký řetězcový pomocí znakovou stránku ANSI, ale může být zakódován v úzkém řetězce v některých vícebajtové znakové stránky, nebo řetězce UTF-8 nebo širokého řetězce. Podpora kódování Unicode je v C ++ 11, prodloužena char16_t\* a char32_t\* typy řetězců:

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
