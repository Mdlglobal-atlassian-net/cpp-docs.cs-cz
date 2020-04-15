---
title: '&lt;funkce&gt; regulárního výrazu'
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
ms.openlocfilehash: ff6ea37208aef19431bf7aefe612dccd589c638b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374547"
---
# <a name="ltregexgt-functions"></a>&lt;funkce&gt; regulárního výrazu

|||
|-|-|
|[regex_match](#regex_match)|Testuje, zda regulární výraz odpovídá celému cílovému řetězci.|
|[regex_replace](#regex_replace)|Nahrazuje odpovídající regulární výrazy.|
|[regex_search](#regex_search)|Vyhledá shodu regulárních výrazů.|
|[Swap](#swap)|Zamění `basic_regex` dva `match_results` nebo objekty.|

## <a name="regex_match"></a><a name="regex_match"></a>regex_match

Testuje, zda regulární výraz odpovídá celému cílovému řetězci.

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

*BidIt*\
Typ iterátoru pro podzápasy. V běžných případech `string::const_iterator` `wstring::const_iterator`se `const char*` `const wchar_t*`jedná o jeden z , nebo .

*Alloc*\
Výsledky shody alokátor třídy.

*Elem*\
Typ prvků, které se mají spárovat. V běžných `string`případech `wstring` `char*` se `wchar_t*`jedná o , nebo .

*RXtraits*\
Třída vlastností prvků.

*Alloc2 (Alloc2)*\
Třída alokátoru regulárních výrazů.

*IOtraits*\
Třída vlastností řetězce.

*IOalloc*\
Třída alokátoru řetězce.

*Příznaky*\
Příznaky pro zápasy.

*První*\
Začátek sekvence tak, aby odpovídaly.

*Poslední*\
Konec sekvence tak, aby odpovídala.

*Zápas*\
Výsledky zápasu. Odpovídá elem typu: [smatch](../standard-library/regex-typedefs.md#smatch) for `string`, `wstring` [wsmatch](../standard-library/regex-typedefs.md#wsmatch) `char*` for , `wchar_t*` [cmatch](../standard-library/regex-typedefs.md#cmatch) for nebo [wcmatch](../standard-library/regex-typedefs.md#wcmatch) for .

*Ptr*\
Ukazatel na začátek sekvence tak, aby odpovídala. Pokud *ptr* je `char*` `cmatch` , `regex`pak použijte a . Pokud *ptr* `wchar_t*` je `wcmatch` `wregex`pak použít a .

*Re*\
Regulární výraz, který má odpovídat. `regex` Zadejte `string` `char*`pro `wregex` písmena a), `wstring` nebo, nebo. `wchar_t*`

*Str*\
Řetězec tak, aby odpovídaly. Odpovídá typu *Elem*.

### <a name="remarks"></a>Poznámky

Každá funkce šablony vrátí hodnotu true pouze v případě, že celá sekvence *operandu přesně* odpovídá argumentu regulárního výrazu *re*. Pomocí [regex_search,](../standard-library/regex-functions.md#regex_search) aby odpovídaly podřetězec `regex_iterator` v rámci cílové sekvence a najít více shod. Funkce, které `match_results` trvat objekt nastavit jeho členy tak, aby odrážely, zda shoda proběhla úspěšně a pokud ano, jaké různé skupiny zachycení v regulárním výrazu zachyceny.

Funkce, které `match_results` trvat objekt nastavit jeho členy tak, aby odrážely, zda shoda proběhla úspěšně a pokud ano, jaké různé skupiny zachycení v regulárním výrazu zachyceny.

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

## <a name="regex_replace"></a><a name="regex_replace"></a>regex_replace

Nahrazuje odpovídající regulární výrazy.

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

*OutIt*\
Typ iterátoru pro náhrady.

*BidIt*\
Typ iterátoru pro podzápasy.

*RXtraits*\
Třída vlastností prvků.

*Alloc*\
Třída alokátoru regulárních výrazů.

*Elem*\
Typ prvků, které se mají spárovat.

*Příznaky*\
Příznaky pro zápasy.

*První*\
Začátek sekvence tak, aby odpovídaly.

*Fmt*\
Formát pro nahrazení.

*Poslední*\
Konec sekvence tak, aby odpovídala.

*ven*\
Výstupní iterátor.

*Re*\
Regulární výraz, který má odpovídat.

*Str*\
Řetězec tak, aby odpovídaly.

### <a name="remarks"></a>Poznámky

První funkce vytvoří [objekt](../standard-library/regex-iterator-class.md) `iter(first, last, re, flags)` regex_iterator Class a použije jej `[first, last)` k rozdělení vstupního `T0 M0 T1 M1...TN-1 MN-1 TN`rozsahu `Mn` do řady dílčích sekvencí , kde je n-té shody zjištěné iterátorem. Pokud nejsou nalezeny `T0` žádné shody, `N` je celý vstupní rozsah a je nula. Pokud `(flags & format_first_only) != 0` je použita pouze `T1` první shoda, je všechny vstupní text, který následuje za shodu a `N` je 1. Pro `i` každého v `[0, N)`rozsahu `(flags & format_no_copy) == 0` , pokud zkopíruje `Ti` text v rozsahu do iterátoru *ven*. Potom volá `m.format(out, fmt, flags)`, `m` kde `match_results` je objekt vrácený objektem `iter` iterátoru pro dílčí sekvenci `Mi`. Nakonec, `(flags & format_no_copy) == 0` pokud zkopíruje text `TN` v rozsahu iterátoru *ven*. Funkce vrátí *ven*.

Druhá funkce vytvoří místní `result` proměnnou `basic_string<charT>` typu `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`a volání . Vrátí `result`.

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

## <a name="regex_search"></a><a name="regex_search"></a>regex_search

Vyhledá shodu regulárních výrazů.

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

*BidIt*\
Typ iterátoru pro podzápasy.

*Alloc*\
Výsledky shody alokátor třídy.

*Elem*\
Typ prvků, které se mají spárovat.

*RXtraits*\
Třída vlastností prvků.

*Alloc2 (Alloc2)*\
Třída alokátoru regulárních výrazů.

*IOtraits*\
Třída vlastností řetězce.

*IOalloc*\
Třída alokátoru řetězce.

*Příznaky*\
Příznaky pro zápasy.

*První*\
Začátek sekvence tak, aby odpovídaly.

*Poslední*\
Konec sekvence tak, aby odpovídala.

*Zápas*\
Výsledky zápasu.

*Ptr*\
Ukazatel na začátek sekvence tak, aby odpovídala.

*Re*\
Regulární výraz, který má odpovídat.

*Str*\
Řetězec tak, aby odpovídaly.

### <a name="remarks"></a>Poznámky

Každá funkce šablony vrátí hodnotu true pouze v případě, že je úspěšné hledání argumentu reregulárního výrazu *v* posloupnosti operandu. Funkce, které `match_results` berou objekt nastavit jeho členy tak, aby odrážely, zda hledání proběhlo úspěšně a pokud ano, jaké různé skupiny zachycení v regulárním výrazu zachyceny.

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

## <a name="swap"></a><a name="swap"></a>Swap

Zamění `basic_regex` dva `match_results` nebo objekty.

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

*Elem*\
Typ prvků, které se mají spárovat.

*RXtraits*\
Třída vlastností prvků.

### <a name="remarks"></a>Poznámky

Funkce šablony zaměnit obsah jejich příslušné argumenty v konstantním čase a nevyvolávají výjimky.

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

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_constants třída](../standard-library/regex-constants-class.md)\
[regex_error třída](../standard-library/regex-error-class.md)\
[regex_iterator třída](../standard-library/regex-iterator-class.md)\
[\<operátory> regulárních výrazů](../standard-library/regex-operators.md)\
[regex_token_iterator třída](../standard-library/regex-token-iterator-class.md)\
[třída regex_traits](../standard-library/regex-traits-class.md)\
[\<regulární> typedefs](../standard-library/regex-typedefs.md)
