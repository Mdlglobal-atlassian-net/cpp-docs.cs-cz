---
title: regex_iterator – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
ms.openlocfilehash: 6bc57d6815fa6f30e26b22e9b7ab758a1ac20e16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374559"
---
# <a name="regex_iterator-class"></a>regex_iterator – třída

Třída iterátoru pro zápasy.

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parametry

*BidIt*\
Typ iterátoru pro podzápasy.

*Elem*\
Typ prvků, které se mají spárovat.

*RXtraits*\
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt konstantní dopředu iterátoru. Extrahuje objekty `match_results<BidIt>` typu opakovaným použitím `*pregex` svého objektu regulárního výrazu `[begin, end)`na posloupnost znaků definovanou rozsahem iterátoru .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_iterator](#regex_iterator)|Vytvoří iterátor.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterator_category](#iterator_category)|Typ kategorie iterátoru.|
|[ukazatel](#pointer)|Typ ukazatele na shodu.|
|[Odkaz](#reference)|Typ odkazu na shodu.|
|[regex_type](#regex_type)|Typ regulárního výrazu, který se má shodovat.|
|[value_type](#value_type)|Typ shody.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor!=](#op_neq)|Porovnává iterátory pro nerovnost.|
|[operátor*](#op_star)|Přistupuje k určené shodě.|
|[operátor++](#op_add_add)|Zintáží iterátor.|
|[operátor =](#op_eq)|Porovnává iterátory pro rovnost.|
|[operátor->](#op_arrow)|Přistupuje k určené shodě.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex>

**Obor názvů:** std

## <a name="examples"></a>Příklady

Příklady regulárních výrazů najdete v následujících tématech:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [Swap](../standard-library/regex-functions.md#swap)

```cpp
// std__regex__regex_iterator.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "axayaz";
    Myiter::regex_type rx("a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;

// other members
    Myiter it1(pat, pat + strlen(pat), rx);
    Myiter it2(it1);
    next = it1;

    Myiter::iterator_category cat = std::forward_iterator_tag();
    Myiter::difference_type dif = -3;
    Myiter::value_type mr = *it1;
    Myiter::reference ref = mr;
    Myiter::pointer ptr = &ref;

    dif = dif; // to quiet "unused" warnings
    ptr = ptr;

    return (0);
    }
```

```Output
match == a
match == a
match == a
```

## <a name="regex_iteratordifference_type"></a><a name="difference_type"></a>regex_iterator::difference_type

Typ rozdílu iterátoru.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `std::ptrdiff_t`pro .

## <a name="regex_iteratoriterator_category"></a><a name="iterator_category"></a>regex_iterator::iterator_category

Typ kategorie iterátoru.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `std::forward_iterator_tag`pro .

## <a name="regex_iteratoroperator"></a><a name="op_neq"></a>regex_iterator::operátor!=

Porovnává iterátory pro nerovnost.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Iterátor porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce `!(*this == right)`vrátí .

## <a name="regex_iteratoroperator"></a><a name="op_star"></a>regex_iterator::operátor*

Přistupuje k určené shodě.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `match`uloženou hodnotu .

## <a name="regex_iteratoroperator"></a><a name="op_add_add"></a>regex_iterator::operátor++

Zintáží iterátor.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Poznámky

Pokud aktuální shoda nemá žádné znaky, první operátor volá `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; v opačném případě posune uloženou hodnotu `begin` tak, aby `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`ukazovala na první znak po aktuální shodě a poté volá . V obou případech, pokud hledání selže operátor nastaví objekt na konci sekvence iterátoru. Operátor vrátí objekt.

Druhý operátor vytvoří kopii objektu, zintáží objekt a potom vrátí kopii.

## <a name="regex_iteratoroperator"></a><a name="op_eq"></a>regex_iterator::operátor=

Porovnává iterátory pro rovnost.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Iterátor porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `*this` hodnotu true, pokud a *vpravo* jsou oba iterátory konce sekvence nebo pokud `begin == right.begin` `end == right.end`ani `pregex == right.pregex`jeden `flags == right.flags`z nich není iterátor na konci sekvence a , , a . V opačném případě vrátí hodnotu false.

## <a name="regex_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_iterator::operátor-&gt;

Přistupuje k určené shodě.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené `match`hodnoty .

## <a name="regex_iteratorpointer"></a><a name="pointer"></a>regex_iterator::pointer

Typ ukazatele na shodu.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `match_results<BidIt>*`pro `BidIt` , kde je parametr šablony.

## <a name="regex_iteratorreference"></a><a name="reference"></a>regex_iterator::odkaz

Typ odkazu na shodu.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `match_results<BidIt>&`pro `BidIt` , kde je parametr šablony.

## <a name="regex_iteratorregex_iterator"></a><a name="regex_iterator"></a>regex_iterator::regex_iterator

Vytvoří iterátor.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

*První*\
Začátek sekvence tak, aby odpovídaly.

*Poslední*\
Konec sekvence tak, aby odpovídala.

*Re*\
Regulární výraz pro shody.

*F*\
Příznaky pro zápasy.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iterátor na konci sekvence. `begin` Druhý konstruktor inicializuje uloženou hodnotu s *first*, uloženou hodnotu `end` s *last*, uloženou hodnotu `pregex` s `&re`a uloženou hodnotu `flags` s *f*. Potom volá `regex_search(begin, end, match, *pregex, flags)`. Pokud hledání selže, konstruktor nastaví objekt na iterátor konce sekvence.

## <a name="regex_iteratorregex_type"></a><a name="regex_type"></a>regex_iterator::regex_type

Typ regulárního výrazu, který se má shodovat.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem `basic_regex<Elem, RXtraits>`pro .

## <a name="regex_iteratorvalue_type"></a><a name="value_type"></a>regex_iterator::value_type

Typ shody.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `match_results<BidIt>`pro `BidIt` , kde je parametr šablony.

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_constants třída](../standard-library/regex-constants-class.md)\
[regex_error třída](../standard-library/regex-error-class.md)\
[\<funkce> regulárních výrazů](../standard-library/regex-functions.md)\
[regex_iterator třída](../standard-library/regex-iterator-class.md)\
[\<operátory> regulárních výrazů](../standard-library/regex-operators.md)\
[regex_token_iterator třída](../standard-library/regex-token-iterator-class.md)\
[třída regex_traits](../standard-library/regex-traits-class.md)\
[\<regulární> typedefs](../standard-library/regex-typedefs.md)
