---
title: '&lt;regulární výraz&gt; funkce'
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_match
- regex/std::regex_replace
- regex/std::regex_search
- regex/std::swap
ms.assetid: 91a8314b-6f7c-4e33-b7d6-d8583dd75585
helpviewer_keywords:
- std::regex_match [C++]
- std::regex_replace [C++]
- std::regex_search [C++]
- std::swap [C++]
- std::swap [C++]
ms.openlocfilehash: 47b3ae9d59db7c39d7b9667038d216f24530d5dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62369602"
---
# <a name="ltregexgt-functions"></a>&lt;regulární výraz&gt; funkce

|||
|-|-|
|[regex_match](#regex_match)|Ověřuje, zda regulární výraz odpovídá celý cílový řetězec.|
|[regex_replace](#regex_replace)|Nahradí odpovídající regulární výrazy.|
|[regex_search](#regex_search)|Hledání regulárního výrazu shody.|
|[swap](#swap)|Prohodí dva `basic_regex` nebo `match_results` objekty.|

## <a name="regex_match"></a>  regex_match –

Ověřuje, zda regulární výraz odpovídá celý cílový řetězec.

```cpp
// (1)
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (2)
template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (3)
template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (4)
template <class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const Elem *ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (5)
template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

// (6)
template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_match(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iterátoru pro dílčí shody. Pro běžné případy to tak jeden z `string::const_iterator`, `wstring::const_iterator`, `const char*` nebo `const wchar_t*`.

*ALLOC*<br/>
Třída alokátoru výsledky porovnání.

*Elem*<br/>
Typ prvků, které se mají spárovat. Pro běžné případů to je `string`, `wstring`, `char*` nebo `wchar_t*`.

*RXtraits*<br/>
Třída vlastností prvků.

*Alloc2*<br/>
Třída alokátoru regulární výraz.

*IOtraits*<br/>
Třída vlastností řetězce.

*IOalloc*<br/>
Třída alokátoru řetězec.

*příznaky*<br/>
Příznaky pro shody.

*první*<br/>
Začátek pořadí tak, aby odpovídaly.

*last*<br/>
Konec pořadí tak, aby odpovídaly.

*match*<br/>
Výsledky porovnání. Odpovídá typu Elem: [smatch](../standard-library/regex-typedefs.md#smatch) pro `string`, [wsmatch](../standard-library/regex-typedefs.md#wsmatch) pro `wstring`, [cmatch](../standard-library/regex-typedefs.md#cmatch) pro `char*` nebo [wcmatch](../standard-library/regex-typedefs.md#wcmatch) pro `wchar_t*`.

*ptr*<br/>
Ukazatel na začátek pořadí tak, aby odpovídaly. Pokud *ptr* je `char*`, pak použijte `cmatch` a `regex`. Pokud *ptr* je `wchar_t*` použije `wcmatch` a `wregex`.

*re*<br/>
Regulární výraz tak, aby odpovídaly. Typ `regex` pro `string` a `char*`, nebo `wregex` pro `wstring` a `wchar_t*`.

*str*<br/>
Řetězec k porovnání shody. Odpovídá typu *Elem*.

### <a name="remarks"></a>Poznámky

Každá šablona funkce vrátí hodnotu true pouze v případě sekvenci operandů celý *str* přesně shoduje s regulárním výrazem argumentu *re*. Použití [regex_search –](../standard-library/regex-functions.md#regex_search) tak, aby odpovídaly podřetězce v cílové sekvenci a `regex_iterator` k vyhledání více shod. Funkcí, které přijímají `match_results` objekt nastaven jejích členů tak, aby odrážely, jestli byla úspěšná shoda a pokud ano co různých v regulárním výrazu zachycené skupiny zachycení.

Funkcí, které přijímají `match_results` objekt nastaven jejích členů tak, aby odrážely, jestli byla úspěšná shoda a pokud ano co různých v regulárním výrazu zachycené skupiny zachycení.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_match.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

using namespace std;

int main()
{
    // (1) with char*
    // Note how const char* requires cmatch and regex
    const char *first = "abc";
    const char *last = first + strlen(first);
    cmatch narrowMatch;
    regex rx("a(b)c");

    bool found = regex_match(first, last, narrowMatch, rx);
    if (found)
        wcout << L"Regex found in abc" << endl;

    // (2) with std::wstring
    // Note how wstring requires wsmatch and wregex.
    // Note use of const iterators cbegin() and cend().
    wstring target(L"Hello");
    wsmatch wideMatch;
    wregex wrx(L"He(l+)o");

    if (regex_match(target.cbegin(), target.cend(), wideMatch, wrx))
        wcout << L"The matching text is:" << wideMatch.str() << endl;

    // (3) with std::string
    string target2("Drizzle");
    regex rx2(R"(D\w+e)"); // no double backslashes with raw string literal

    found = regex_match(target2.cbegin(), target2.cend(), rx2);
    if (found)
        wcout << L"Regex found in Drizzle" << endl;

    // (4) with wchar_t*
    const wchar_t* target3 = L"2014-04-02";
    wcmatch wideMatch2;

    // LR"(...)" is a  raw wide-string literal. Open and close parens
    // are delimiters, not string elements.
    wregex wrx2(LR"(\d{4}(-|/)\d{2}(-|/)\d{2})");
    if (regex_match(target3, wideMatch2, wrx2))
    {
        wcout << L"Matching text: " << wideMatch2.str() << endl;
    }

     return 0;
}
```

```Output
Regex found in abc
The matching text is: Hello
Regex found in Drizzle
The matching text is: 2014-04-02
```

## <a name="regex_replace"></a>  regex_replace

Nahradí odpovídající regulární výrazy.

```cpp
template <class OutIt, class BidIt, class RXtraits, class Alloc, class Elem>
OutIt regex_replace(
    OutIt out,
    BidIt first,
    BidIt last,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);

template <class RXtraits, class Alloc, class Elem>
basic_string<Elem> regex_replace(
    const basic_string<Elem>& str,
    const basic_regex<Elem, RXtraits, Alloc>& re,
    const basic_string<Elem>& fmt,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parametry

*OutIt*<br/>
Typ iterátoru pro nahrazení.

*BidIt*<br/>
Typ iterátoru pro dílčí shody.

*RXtraits*<br/>
Třída vlastností prvků.

*ALLOC*<br/>
Třída alokátoru regulární výraz.

*Elem*<br/>
Typ prvků, které se mají spárovat.

*příznaky*<br/>
Příznaky pro shody.

*první*<br/>
Začátek pořadí tak, aby odpovídaly.

*fmt*<br/>
Formát pro nahrazení.

*last*<br/>
Konec pořadí tak, aby odpovídaly.

*out*<br/>
Výstupní iterátor.

*re*<br/>
Regulární výraz tak, aby odpovídaly.

*str*<br/>
Řetězec k porovnání shody.

### <a name="remarks"></a>Poznámky

Vytvoří první funkce [regex_iterator – třída](../standard-library/regex-iterator-class.md) objekt `iter(first, last, re, flags)` a použije ho k rozdělení jeho vstupním rozsahu `[first, last)` do řady dílčích sekvencí, které `T0 M0 T1 M1...TN-1 MN-1 TN`, kde `Mn` n-tý shody zjistí iterátor. Pokud se nenajdou žádné shody, `T0` je celý vstupním rozsahu a `N` je nula. Pokud `(flags & format_first_only) != 0` se použije pouze první shodu, `T1` je všechny vstupní text, který následuje po shodě a `N` 1. Pro každou `i` v rozsahu `[0, N)`, pokud `(flags & format_no_copy) == 0` zkopíruje text v rozsahu `Ti` na iterátor *si*. Poté zavolá `m.format(out, fmt, flags)`, kde `m` je `match_results` vrácený objekt iterátoru `iter` pro k dílčí sekvenci `Mi`. Nakonec pokud `(flags & format_no_copy) == 0` zkopíruje text v rozsahu `TN` na iterátor *si*. Funkce vrátí *si*.

Druhá funkce vytvoří místní proměnná `result` typu `basic_string<charT>` a volání `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`. Vrátí `result`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_replace.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    char buf[20];
    const char *first = "axayaz";
    const char *last = first + strlen(first);
    std::regex rx("a");
    std::string fmt("A");
    std::regex_constants::match_flag_type fonly =
        std::regex_constants::format_first_only;

    *std::regex_replace(&buf[0], first, last, rx, fmt) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    *std::regex_replace(&buf[0], first, last, rx, fmt, fonly) = '\0';
    std::cout << "replacement == " << &buf[0] << std::endl;

    std::string str("adaeaf");
    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt) << std::endl;

    std::cout << "replacement == "
        << std::regex_replace(str, rx, fmt, fonly) << std::endl;

    return (0);
}
```

```Output
replacement == AxAyAz
replacement == Axayaz
replacement == AdAeAf
replacement == Adaeaf
```

## <a name="regex_search"></a>  regex_search

Hledání regulárního výrazu shody.

```cpp
template <class BidIt, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    match_results<BidIt, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class BidIt, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    BidIt first,
    Bidit last,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class Alloc, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    match_results<const Elem*, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const Elem* ptr,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Alloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    match_results<typename basic_string<Elem, IOtraits, IOalloc>::const_iterator, Alloc>& match,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);

template <class IOtraits, class IOalloc, class Elem, class RXtraits, class Alloc2>
bool regex_search(
    const basic_string<Elem, IOtraits, IOalloc>& str,
    const basic_regex<Elem, RXtraits, Alloc2>& re,
    match_flag_type flags = match_default);
```

### <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iterátoru pro dílčí shody.

*ALLOC*<br/>
Třída alokátoru výsledky porovnání.

*Elem*<br/>
Typ prvků, které se mají spárovat.

*RXtraits*<br/>
Třída vlastností prvků.

*Alloc2*<br/>
Třída alokátoru regulární výraz.

*IOtraits*<br/>
Třída vlastností řetězce.

*IOalloc*<br/>
Třída alokátoru řetězec.

*příznaky*<br/>
Příznaky pro shody.

*první*<br/>
Začátek pořadí tak, aby odpovídaly.

*last*<br/>
Konec pořadí tak, aby odpovídaly.

*match*<br/>
Výsledky porovnání.

*ptr*<br/>
Ukazatel na začátek pořadí tak, aby odpovídaly.

*re*<br/>
Regulární výraz tak, aby odpovídaly.

*str*<br/>
Řetězec k porovnání shody.

### <a name="remarks"></a>Poznámky

Každá šablona funkce vrátí hodnotu true, pouze pokud hledání regulárního výrazu argument *re* v jeho operandu pořadí úspěšné. Funkcí, které přijímají `match_results` objekt nastaven jejích členů tak, aby odrážely, zda bylo hledání úspěšné a pokud ano co různých v regulárním výrazu zachycené skupiny zachycení.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_search.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    const char *first = "abcd";
    const char *last = first + strlen(first);
    std::cmatch mr;
    std::regex rx("abc");
    std::regex_constants::match_flag_type fl =
        std::regex_constants::match_default;

    std::cout << "search(f, f+1, \"abc\") == " << std::boolalpha
        << regex_search(first, first + 1, rx, fl) << std::endl;

    std::cout << "search(f, l, \"abc\") == " << std::boolalpha
        << regex_search(first, last, mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(\"a\", \"abc\") == " << std::boolalpha
        << regex_search("a", rx) << std::endl;

    std::cout << "search(\"xabcd\", \"abc\") == " << std::boolalpha
        << regex_search("xabcd", mr, rx) << std::endl;
    std::cout << "  matched: \"" << mr.str() << "\"" << std::endl;

    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(std::string("a"), rx) << std::endl;

    std::string str("abcabc");
    std::match_results<std::string::const_iterator> mr2;
    std::cout << "search(string, \"abc\") == " << std::boolalpha
        << regex_search(str, mr2, rx) << std::endl;
    std::cout << "  matched: \"" << mr2.str() << "\"" << std::endl;

    return (0);
}
```

```Output
search(f, f+1, "abc") == false
search(f, l, "abc") == true
  matched: "abc"
search("a", "abc") == false
search("xabcd", "abc") == true
  matched: "abc"
search(string, "abc") == false
search(string, "abc") == true
  matched: "abc"
```

## <a name="swap"></a>  Prohození

Prohodí dva `basic_regex` nebo `match_results` objekty.

```cpp
template <class Elem, class RXtraits>
void swap(
    basic_regex<Elem, RXtraits, Alloc>& left,
    basic_regex<Elem, RXtraits>& right) noexcept;

template <class Elem, class IOtraits, class BidIt, class Alloc>
void swap(
    match_results<BidIt, Alloc>& left,
    match_results<BidIt, Alloc>& right) noexcept;
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Typ prvků, které se mají spárovat.

*RXtraits*<br/>
Třída vlastností prvků.

### <a name="remarks"></a>Poznámky

Funkce šablony Prohodit obsah svých příslušných argumentů v konstantním času a nevyvolají výjimky.

### <a name="example"></a>Příklad

```cpp
// std__regex__swap.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx0("c(a*)|(b)");
    std::regex rx1;
    std::cmatch mr0;
    std::cmatch mr1;

    swap(rx0, rx1);
    std::regex_search("xcaaay", mr1, rx1);
    swap(mr0, mr1);

    std::csub_match sub = mr0[1];
    std::cout << "matched == " << std::boolalpha
        << sub.matched << std::endl;
    std::cout << "length == " << sub.length() << std::endl;
    std::cout << "string == " << sub << std::endl;

    return (0);
}
```

```Output
matched == true
length == 3
string == aaa
```

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > – Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
