---
title: match_results – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 32a5f9d20999740d4368f7901c797d87acce0be9
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657458"
---
# <a name="matchresults-class"></a>match_results – třída

Obsahuje posloupnost dílčí shody.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iterátoru pro dílčí shody.

*ALLOC*<br/>
Typ alokátoru pro správu úložiště

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který řídí neupravitelnými sekvence elementů typu `sub_match<BidIt>` generovaných hledání regulárního výrazu. Každý prvek odkazuje na dílčí sekvenci, který odpovídá skupině zachycení odpovídá prvku.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[match_results](#match_results)|Vytvoří objekt.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ alokátoru pro správu úložiště|
|[char_type](#char_type)|Typ prvku|
|[const_iterator](#const_iterator)|Typ const iterator pro dílčí shody.|
|[const_reference](#const_reference)|Typ const odkaz na element.|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterátor](#iterator)|Typ iterátoru pro dílčí shody.|
|[Referenční dokumentace](#reference)|Typ odkazu na element.|
|[size_type](#size_type)|Typ počtu dílčí shoda.|
|[STRING_TYPE](#string_type)|Typ řetězec.|
|[value_type](#value_type)|Typ dílčí shoda.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[začít](#begin)|Určuje začátek pořadí dílčí shoda.|
|[prázdný](#empty)|Testy pro žádné dílčí shody.|
|[ukončení](#end)|Určuje konec pořadí dílčí shoda.|
|[Formát](#format)|Formátuje dílčí shody.|
|[get_allocator](#get_allocator)|Vrátí uložené alokátoru.|
|[Délka](#length)|Vrátí délku objektu dílčí shoda.|
|[max_size](#max_size)|Získá maximální počet dílčí shody.|
|[Pozice](#position)|Získejte počáteční posun podskupiny.|
|[prefix](#prefix)|Získá pořadí před první dílčí shoda.|
|[Velikost](#size)|Spočítá počet dílčí shody.|
|[str](#str)|Vrátí hodnotu dílčí shoda.|
|[Přípona](#suffix)|Získá pořadí po poslední dílčí shoda.|
|[Prohození](#swap)|Prohodí dva objekty match_results –.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Match_results – objekt kopírovat.|
|[– Operátor\[\]](#op_at)|Přístup k podřízeným objektům.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

## <a name="example"></a>Příklad

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="allocator_type"></a>  match_results::allocator_type

Typ alokátoru pro správu úložiště

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro argument šablony *alokační*.

## <a name="begin"></a>  match_results::begin

Určuje začátek pořadí dílčí shoda.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, na kterou odkazuje na první prvek pořadí (nebo přesně za konec k prázdné sekvenci).

## <a name="char_type"></a>  match_results::char_type

Typ prvku

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `iterator_traits<BidIt>::value_type`, což je typ prvku, který byl vyhledán sekvence znaků.

## <a name="const_iterator"></a>  match_results::const_iterator

Typ const iterator pro dílčí shody.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Poznámky

Definice typu popisuje objekt, který může sloužit jako konstantní iterátor s náhodným přístupem řízené sekvence.

## <a name="const_reference"></a>  match_results::const_reference

Typ const odkaz na element.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Definice typu popisuje objekt, který může sloužit jako konstantní odkaz na prvek řízené sekvence.

## <a name="difference_type"></a>  match_results::difference_type

Typ rozdílu iterátoru.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `iterator_traits<BidIt>::difference_type`; popisuje objekt, který může představovat rozdíl mezi všechny dvěma iterátory, které odkazují na prvky řízené sekvence.

## <a name="empty"></a>  match_results::Empty

Testy pro žádné dílčí shody.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true, pouze pokud hledání regulárního výrazu se nezdařilo.

## <a name="end"></a>  match_results::end

Určuje konec pořadí dílčí shoda.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který ukazuje za konec sekvence.

## <a name="format"></a>  match_results::Format

Formátuje dílčí shody.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parametry

*OutIt*<br/>
Typ výstupního iterátoru.

*out*<br/>
Výstupní tok, do kterého se má zapisovat.

*FMT*<br/>
Řetězec formátu.

*příznaky*<br/>
Příznaky formátu.

### <a name="remarks"></a>Poznámky

Každá členská funkce generuje formátovaný text ovládaný formát *fmt*. První členská funkce zapíše formátovaný text do sekvence definované jejím argumentem *si* a vrátí *si*. Druhá členská funkce vrátí objekt řetězce s kopií formátovaného textu.

Pro účely generování formátovaného textu. text literálu v řetězci formátu je obvykle zkopírován do cílové sekvenci. Každá sekvence escape v řetězci formátu je nahrazena textem, který reprezentuje. Podrobnosti kopírování a nahrazování jsou ovládány příznaky formátu předanými funkci.

## <a name="get_allocator"></a>  match_results::get_allocator

Vrátí uložené alokátoru.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí kopii přidělování objektu používanou podle `*this` přidělit jeho `sub_match` objekty.

## <a name="iterator"></a>  match_results::iterator

Typ iterátoru pro dílčí shody.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako iterátor náhodného přístupu řízené sekvence.

## <a name="length"></a>  match_results::length

Vrátí délku objektu dílčí shoda.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*sub*<br/>
Index dílčí shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `(*this)[sub].length()`.

## <a name="match_results"></a>  match_results::match_results

Vytvoří objekt.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parametry

*ALLOC*<br/>
Objekt alokátoru, který se má uložit.

*doprava*<br/>
Match_results – objekt ke kopírování.

### <a name="remarks"></a>Poznámky

První konstruktor zkonstruuje `match_results` objekt, který obsahuje žádné dílčí shody. Druhý konstruktor vytvoří `match_results` objekt, který je kopií *správné*.

## <a name="max_size"></a>  match_results::max_size

Získá maximální počet dílčí shody.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku objektu nejdelší sekvenci, která můžete řídit objektu.

## <a name="op_eq"></a>  match_results::Operator =

Match_results – objekt kopírovat.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Match_results – objekt ke kopírování.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí sekvence řízenou parametrem `*this` kopii sekvence řízenou parametrem *správné*.

## <a name="op_at"></a>  [] match_results::Operator

Přístup k podřízeným objektům.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parametry

*n*<br/>
Index dílčí shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na prvek *n* řízenou sekvenci nebo odkaz na prázdný `sub_match` objekt by `size() <= n` nebo, pokud skupina zachycení *n* nebyla součástí shody.

## <a name="position"></a>  match_results::position

Získejte počáteční posun podskupiny.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*sub*<br/>
Index dílčí shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `std::distance(prefix().first, (*this)[sub].first)`, tedy vzdálenost od prvního znaku v cílové sekvenci první znak dílčí shoda odkazuje element `n` řízené sekvence.

## <a name="prefix"></a>  match_results::prefix

Získá pořadí před první dílčí shoda.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na objekt typu `sub_match<BidIt>` , která odkazuje na sekvenci znaků, který začíná na začátku cílové sekvence a končí `(*this)[0].first`, to znamená, odkazuje na text, který předchází dílčí sekvenci odpovídající.

## <a name="reference"></a>  match_results::Reference

Typ odkazu na element.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro typ `const_reference`.

## <a name="size"></a>  match_results::size

Spočítá počet dílčí shody.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Poznámky

Člen funkce vrátí jeden vyšší než počet skupin zachycení v regulárním výrazu, které bylo použito pro vyhledávání, nebo nula, pokud byly provedeny žádné vyhledávání.

## <a name="size_type"></a>  match_results::size_type

Typ počtu dílčí shoda.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro typ `Alloc::size_type`.

## <a name="str"></a>  match_results::str

Vrátí hodnotu dílčí shoda.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*sub*<br/>
Index dílčí shoda.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `string_type((*this)[sub])`.

## <a name="string_type"></a>  match_results::STRING_TYPE

Typ řetězec.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro typ `basic_string<char_type>`.

## <a name="suffix"></a>  match_results::suffix

Získá pořadí po poslední dílčí shoda.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na objekt typu `sub_match<BidIt>` , která odkazuje na sekvenci znaků, který začíná na `(*this)[size() - 1].second` a končí na konci cílové sekvence, to znamená, odkazuje na text, který následuje za dílčí sekvencí odpovídající.

## <a name="swap"></a>  match_results::swap

Prohodí dva objekty match_results –.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Match_results – objekt se Prohodit s.

### <a name="remarks"></a>Poznámky

Členská funkce Zamění obsah `*this` a *správné* v konstantním času a nevyvolává výjimky.

## <a name="value_type"></a>  match_results::value_type

Typ dílčí shoda.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ `sub_match<BidIt>`.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
