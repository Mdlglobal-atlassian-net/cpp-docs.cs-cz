---
title: funkce &lt;Regex&gt;
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
ms.openlocfilehash: b2be3e4a830113ee86a05fea0d39fd8e12ec3e9a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876131"
---
# <a name="ltregexgt-functions"></a>funkce &lt;Regex&gt;

|||
|-|-|
|[regex_match](#regex_match)|Testuje, zda regulární výraz odpovídá celému cílovému řetězci.|
|[regex_replace](#regex_replace)|Nahradí párové regulární výrazy.|
|[regex_search](#regex_search)|Vyhledá shodu regulárního výrazu.|
|[adresu](#swap)|Prohodí dva objekty `basic_regex` nebo `match_results`.|

## <a name="regex_match"></a>regex_match

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

\ *BiDi*
Typ iterátoru pro podshody. V některých případech je tato jedna z `string::const_iterator`, `wstring::const_iterator`, `const char*` nebo `const wchar_t*`.

\ *přidělení*
Třída přidělování výsledků shody

*Elem*\
Typ prvků, které se mají spárovat. V běžných případech se jedná o `string`, `wstring`, `char*` nebo `wchar_t*`.

*RXtraits*\
Třída vlastností prvků.

*Alloc2*\
Třída přidělování regulárních výrazů

*IOtraits*\
Třída řetězcových vlastností.

*IOalloc*\
Třída přidělování řetězců

\ *příznaků*
Příznaky pro shody

*první*\
Začátek sekvence, která se má shodovat

*poslední*\
Konec sekvence, která se má shodovat.

*shoda*\
Výsledky shody Odpovídá elem typu: [Smatch –](../standard-library/regex-typedefs.md#smatch) pro `string`, [wsmatch –](../standard-library/regex-typedefs.md#wsmatch) pro `wstring`, [cmatch –](../standard-library/regex-typedefs.md#cmatch) pro `char*` nebo [wcmatch –](../standard-library/regex-typedefs.md#wcmatch) pro `wchar_t*`.

\ *PTR*
Ukazatel na začátek sekvence, který se má shodovat. Pokud je *ptr* `char*`, použijte `cmatch` a `regex`. Pokud je *ptr* `wchar_t*` pak použijte `wcmatch` a `wregex`.

*znovu*\
Regulární výraz, který se má shodovat. Zadejte `regex` pro `string` a `char*`nebo `wregex` pro `wstring` a `wchar_t*`.

\ *str*
Řetězec, který se má shodovat. Odpovídá typu *elem*.

### <a name="remarks"></a>Poznámky

Každá funkce šablony vrátí hodnotu true pouze v případě, že se *celá sekvence* operandů přesně shoduje *s argumentem*regulárního výrazu. Použijte [regex_search](../standard-library/regex-functions.md#regex_search) , aby odpovídal podřetězci v cílové sekvenci a `regex_iterator` najít více shod. Funkce, které přijímají objekt `match_results`, nastaví své členy tak, aby odrážely, zda byla shoda úspěšná, a pokud ano, jaké jsou různé skupiny zachycení v regulárním výrazu.

Funkce, které přijímají objekt `match_results`, nastaví své členy tak, aby odrážely, zda byla shoda úspěšná, a pokud ano, jaké jsou různé skupiny zachycení v regulárním výrazu.

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

## <a name="regex_replace"></a>regex_replace

Nahradí párové regulární výrazy.

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

\ *BiDi*
Typ iterátoru pro podshody.

*RXtraits*\
Třída vlastností prvků.

\ *přidělení*
Třída přidělování regulárních výrazů

*Elem*\
Typ prvků, které se mají spárovat.

\ *příznaků*
Příznaky pro shody

*první*\
Začátek sekvence, která se má shodovat

*fmt*\
Formát pro nahrazení.

*poslední*\
Konec sekvence, která se má shodovat.

*\*
Výstupní iterátor

*znovu*\
Regulární výraz, který se má shodovat.

\ *str*
Řetězec, který se má shodovat.

### <a name="remarks"></a>Poznámky

První funkce vytvoří objekt [Regex_iterator třídy](../standard-library/regex-iterator-class.md) `iter(first, last, re, flags)` a použije jej k rozdělení vstupního rozsahu `[first, last)` do řady dílčích sekvencí `T0 M0 T1 M1...TN-1 MN-1 TN`, kde `Mn` je n-tý porovnávání zjištěné iterátorem. Pokud se nenajde žádná shoda, `T0` je celý vstupní rozsah a `N` je nula. Pokud se používá `(flags & format_first_only) != 0` jenom první shoda, `T1` je celý vstupní text, který odpovídá shodě, a `N` je 1. Pro každý `i` v rozsahu `[0, N)`, pokud `(flags & format_no_copy) == 0` zkopíruje text v `Ti` rozsahu *do iterátoru*. Poté volá `m.format(out, fmt, flags)`, kde `m` je objekt `match_results` vrácený objektem iterátoru `iter` pro dílčí sekvenci `Mi`. Nakonec, pokud `(flags & format_no_copy) == 0` zkopíruje text v rozsahu `TN` *do iterátoru*. Funkce vrátí *výstup*.

Druhá funkce vytvoří místní proměnnou `result` typu `basic_string<charT>` a zavolá `regex_replace(back_inserter(result), str.begin(), str.end(), re, fmt, flags)`. Vrátí `result`.

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

## <a name="regex_search"></a>regex_search

Vyhledá shodu regulárního výrazu.

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

\ *BiDi*
Typ iterátoru pro podshody.

\ *přidělení*
Třída přidělování výsledků shody

*Elem*\
Typ prvků, které se mají spárovat.

*RXtraits*\
Třída vlastností prvků.

*Alloc2*\
Třída přidělování regulárních výrazů

*IOtraits*\
Třída řetězcových vlastností.

*IOalloc*\
Třída přidělování řetězců

\ *příznaků*
Příznaky pro shody

*první*\
Začátek sekvence, která se má shodovat

*poslední*\
Konec sekvence, která se má shodovat.

*shoda*\
Výsledky shody

\ *PTR*
Ukazatel na začátek sekvence, který se má shodovat.

*znovu*\
Regulární výraz, který se má shodovat.

\ *str*
Řetězec, který se má shodovat.

### <a name="remarks"></a>Poznámky

Každá funkce šablony vrátí hodnotu true pouze v případě, že vyhledávání jeho argumentu regulárního výrazu *znovu* v jeho sekvenci operandů je úspěšné. Funkce, které přijímají objekt `match_results`, nastaví své členy tak, aby odrážely, zda bylo hledání úspěšné, a pokud tak chcete, aby byly v rámci regulárního výrazu zachyceny různé skupiny zachycení.

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

## <a name="swap"></a>adresu

Prohodí dva objekty `basic_regex` nebo `match_results`.

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

Funkce šablony vymění obsah svých příslušných argumentů v konstantním čase a nevyvolají výjimky.

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

[\<regulárního výrazu >](../standard-library/regex.md)\
[regex_constants\ třídy](../standard-library/regex-constants-class.md)
[regex_error\ třídy](../standard-library/regex-error-class.md)
[regex_iterator\ třídy](../standard-library/regex-iterator-class.md)
[\<operátory regulárního výrazu >](../standard-library/regex-operators.md)\
[regex_token_iterator\ třídy](../standard-library/regex-token-iterator-class.md)
[regex_traits\ třídy](../standard-library/regex-traits-class.md)
[\<Regex > definice typedef](../standard-library/regex-typedefs.md)
