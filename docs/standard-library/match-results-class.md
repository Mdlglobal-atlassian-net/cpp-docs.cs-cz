---
title: match_results – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 31154a38f8bbcb879fd871f1eb1bf5a4b15af79b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371012"
---
# <a name="match_results-class"></a>match_results – třída

Obsahuje posloupnost podsladivených shod.

## <a name="syntax"></a>Syntaxe

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>Parametry

*BidIt*\
Typ iterátoru pro podzápasy.

*Alloc*\
Typ alokátoru pro správu úložiště

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který řídí neupravitelnou `sub_match<BidIt>` posloupnost prvků typu generovaných hledáním regulárních výrazů. Každý prvek odkazuje na dílčí sekvenci, která odpovídá skupině zachycení odpovídající tomuto prvku.

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
|[const_reference](#const_reference)|Typ odkazu elementu const.|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[Iterace](#iterator)|Typ iterátoru pro podzápasy.|
|[Odkaz](#reference)|Typ odkazu na prvek.|
|[size_type](#size_type)|Typ počtu dílčích shod.|
|[string_type](#string_type)|Typ řetězce.|
|[value_type](#value_type)|Typ dílčí shody.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Začít](#begin)|Označuje začátek sekvence podsvazení.|
|[empty](#empty)|Testy pro žádné dílčí shody.|
|[Konec](#end)|Označuje konec sekvence podshod.|
|[Formát](#format)|Formátuje dílčí shody.|
|[get_allocator](#get_allocator)|Vrátí uložený alokátor.|
|[Délka](#length)|Vrátí délku dílčí shody.|
|[max_size](#max_size)|Získá největší počet podshod.|
|[Pozici](#position)|Získejte počáteční posun podskupiny.|
|[Předponu](#prefix)|Získá pořadí před první dílčí shodu.|
|[Velikost](#size)|Spočítá počet dílčích shod.|
|[Str](#str)|Vrátí dílčí shodu.|
|[Přípona](#suffix)|Získá pořadí po poslední dílčí shodu.|
|[Swap](#swap)|Zamění dva match_results objekty.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Zkopírujte match_results objekt.|
|[Operátor\[\]](#op_at)|Přístup k podobjektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex>

**Obor názvů:** std

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

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a>match_results::allocator_type

Typ alokátoru pro správu úložiště

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem pro argument šablony *Alloc*.

## <a name="match_resultsbegin"></a><a name="begin"></a>match_results::začátek

Označuje začátek sekvence podsvazení.

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor náhodného přístupu, který odkazuje na první prvek sekvence (nebo těsně za koncem prázdné sekvence).

## <a name="match_resultschar_type"></a><a name="char_type"></a>match_results::char_type

Typ prvku

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum `iterator_traits<BidIt>::value_type`pro typ , což je typ prvku sekvence znaků, který byl prohledán.

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a>match_results::const_iterator

Typ const iterator pro dílčí shody.

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>Poznámky

Typedef popisuje objekt, který může sloužit jako konstantní random-access iterátor pro řízené sekvence.

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a>match_results::const_reference

Typ odkazu elementu const.

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>Poznámky

Typedef popisuje objekt, který může sloužit jako konstantní odkaz na prvek řízené sekvence.

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a>match_results::difference_type

Typ rozdílu iterátoru.

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem pro `iterator_traits<BidIt>::difference_type`typ ; popisuje objekt, který může představovat rozdíl mezi dvěma iterátory, které ukazují na prvky řízené sekvence.

## <a name="match_resultsempty"></a><a name="empty"></a>match_results::prázdný

Testy pro žádné dílčí shody.

```cpp
bool empty() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pouze v případě, že se nezdařilo hledání regulárních výrazů.

## <a name="match_resultsend"></a><a name="end"></a>match_results:konec

Označuje konec sekvence podshod.

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí iterátor, který ukazuje těsně za konec sekvence.

## <a name="match_resultsformat"></a><a name="format"></a>match_results::formát

Formátuje dílčí shody.

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>Parametry

*OutIt*\
Typ výstupního iterátoru.

*ven*\
Výstupní tok, do kterého se má zapisovat.

*Fmt*\
Řetězec formátu.

*Příznaky*\
Příznaky formátu.

### <a name="remarks"></a>Poznámky

Každá členská funkce generuje formátovaný text pod kontrolou formátu *fmt*. První členská funkce zapíše formátovaný text do sekvence definované jeho *argumentem* a vrátí *se*. Druhá členská funkce vrátí řetězec objektu, který drží kopii formátovaného textu.

Chcete-li generovat formátovaný text. doslovný text ve formátovacím řetězci se obvykle zkopíruje do cílové sekvence. Každá sekvence escape v řetězci formátu je nahrazena textem, který reprezentuje. Podrobnosti kopírování a nahrazování jsou ovládány příznaky formátu předanými funkci.

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a>match_results::get_allocator

Vrátí uložený alokátor.

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí kopii objektu přidělování, `*this` který `sub_match` používá k přidělení jeho objektů.

## <a name="match_resultsiterator"></a><a name="iterator"></a>match_results::iterátor

Typ iterátoru pro podzápasy.

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může sloužit jako iterátor náhodného přístupu pro řízenou sekvenci.

## <a name="match_resultslength"></a><a name="length"></a>match_results::délka

Vrátí délku dílčí shody.

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Dílčí*\
Index dílčí shody.

### <a name="remarks"></a>Poznámky

Členská funkce `(*this)[sub].length()`vrátí .

## <a name="match_resultsmatch_results"></a><a name="match_results"></a>match_results::match_results

Vytvoří objekt.

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>Parametry

*Alloc*\
Objekt alokátoru, který se má uložit.

*Právo*\
Objekt match_results ke kopírování.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří `match_results` objekt, který neobsahuje žádné dílčí shody. Druhý konstruktor vytvoří `match_results` objekt, který je kopií *right*.

## <a name="match_resultsmax_size"></a><a name="max_size"></a>match_results::max_size

Získá největší počet podshod.

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí délku nejdelší sekvence, kterou může objekt řídit.

## <a name="match_resultsoperator"></a><a name="op_eq"></a>match_results::operátor=

Zkopírujte match_results objekt.

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt match_results ke kopírování.

### <a name="remarks"></a>Poznámky

Operátor člena nahradí sekvenci řízenou `*this` kopií sekvence řízené pravým *.*

## <a name="match_resultsoperator"></a><a name="op_at"></a>match_results::operátor[]

Přístup k podobjektu.

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>Parametry

*N*\
Index dílčí shody.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na element *n* řízené sekvence nebo `sub_match` odkaz `size() <= n` na prázdný objekt, pokud nebo pokud skupina zachycení *n* nebyla součástí shody.

## <a name="match_resultsposition"></a><a name="position"></a>match_results::position

Získejte počáteční posun podskupiny.

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Dílčí*\
Index dílčí shody.

### <a name="remarks"></a>Poznámky

Členská funkce `std::distance(prefix().first, (*this)[sub].first)`vrátí , to znamená vzdálenost od prvního znaku v cílové sekvenci k prvnímu znaku v dílčí shodě, na který se vztahuje prvek `n` řízené sekvence.

## <a name="match_resultsprefix"></a><a name="prefix"></a>match_results::prefix

Získá pořadí před první dílčí shodu.

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na `sub_match<BidIt>` objekt typu, který odkazuje na posloupnost znaků, která `(*this)[0].first`začíná na začátku cílové sekvence a končí na , to znamená, že odkazuje na text, který předchází odpovídající dílčí sekvence.

## <a name="match_resultsreference"></a><a name="reference"></a>match_results::odkaz

Typ odkazu na prvek.

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `const_reference`typ .

## <a name="match_resultssize"></a><a name="size"></a>match_results::velikost

Spočítá počet dílčích shod.

```cpp
size_type size() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí o jednu více než počet skupin sběru v regulárním výrazu, který byl použit pro hledání, nebo nulu, pokud nebylo provedeno žádné hledání.

## <a name="match_resultssize_type"></a><a name="size_type"></a>match_results::size_type

Typ počtu dílčích shod.

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Alloc::size_type`typ .

## <a name="match_resultsstr"></a><a name="str"></a>match_results::str

Vrátí dílčí shodu.

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>Parametry

*Dílčí*\
Index dílčí shody.

### <a name="remarks"></a>Poznámky

Členská funkce `string_type((*this)[sub])`vrátí .

## <a name="match_resultsstring_type"></a><a name="string_type"></a>match_results::string_type

Typ řetězce.

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `basic_string<char_type>`typ .

## <a name="match_resultssuffix"></a><a name="suffix"></a>match_results::přípona

Získá pořadí po poslední dílčí shodu.

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na `sub_match<BidIt>` objekt typu, který odkazuje na `(*this)[size() - 1].second` posloupnost znaků, která začíná na konci cílové sekvence, to znamená, že odkazuje na text, který následuje odpovídající dílčí sekvence.

## <a name="match_resultsswap"></a><a name="swap"></a>match_results::swap

Zamění dva match_results objekty.

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>Parametry

*Právo*\
Objekt match_results zaměnit.

### <a name="remarks"></a>Poznámky

Členská funkce zamění `*this` obsah a *právo* v konstantním čase a nevyvolá výjimky.

## <a name="match_resultsvalue_type"></a><a name="value_type"></a>match_results::value_type

Typ dílčí shody.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum `sub_match<BidIt>`pro typ .

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)
