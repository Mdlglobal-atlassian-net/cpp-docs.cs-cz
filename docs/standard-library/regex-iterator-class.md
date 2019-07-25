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
ms.openlocfilehash: ccf806a7918100c58e04ab403f3a8b895e8dc256
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451561"
---
# <a name="regexiterator-class"></a>regex_iterator – třída

Iterátor třídy pro shody

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parametry

*BidI*\
Typ iterátoru pro podshody.

*Elem*\
Typ prvků, které se mají spárovat.

*RXtraits*\
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt konstanty dopředné iterátory. Extrahuje objekty typu `match_results<BidIt>` tím, že opakovaně aplikuje objekt `*pregex` regulárního výrazu do sekvence znaků definované rozsahem `[begin, end)`iterátoru.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_iterator](#regex_iterator)|Vytvoří iterátor.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterator_category](#iterator_category)|Typ kategorie iterátoru|
|[pointer](#pointer)|Typ ukazatele na shodu.|
|[Referenční dokumentace](#reference)|Typ odkazu na shodu.|
|[regex_type](#regex_type)|Typ regulárního výrazu, který se má shodovat.|
|[value_type](#value_type)|Typ shody.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Porovná iterátory pro nerovnost.|
|[podnikatel](#op_star)|Přistupuje k určené shodě.|
|[operator + + – operátor](#op_add_add)|Zvýší iterátor.|
|[operátor =](#op_eq)|Porovná iterátory o rovnosti.|
|[operátor->](#op_arrow)|Přistupuje k určené shodě.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> regulárního výrazu

**Obor názvů:** std

## <a name="examples"></a>Příklady

Příklady regulárních výrazů najdete v následujících tématech:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [swap](../standard-library/regex-functions.md#swap)

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

## <a name="difference_type"></a>  regex_iterator::difference_type

Typ rozdílu iterátoru.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::ptrdiff_t`.

## <a name="iterator_category"></a>regex_iterator::iterator_category

Typ kategorie iterátoru

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::forward_iterator_tag`.

## <a name="op_neq"></a>regex_iterator:: operator! =

Porovná iterátory pro nerovnost.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Iterátor, pro který se má porovnat.

### <a name="remarks"></a>Poznámky

Vrátí `!(*this == right)`členské funkce.

## <a name="op_star"></a>regex_iterator:: operator * – operátor

Přistupuje k určené shodě.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uloženou hodnotu `match`.

## <a name="op_add_add"></a>regex_iterator:: operator + +

Zvýší iterátor.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Poznámky

Pokud aktuální shoda nemá žádné znaky pro první volání `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`operátoru; v opačném případě posune uloženou hodnotu `begin` tak, aby odkazovala na první znak po `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`aktuální shodě, potom volání. V obou případech, pokud vyhledávání neuspěje, operátor nastaví objekt na iteraci na konci sekvence. Operátor vrací objekt.

Druhý operátor vytvoří kopii objektu, zvýší objekt a vrátí kopii.

## <a name="op_eq"></a>regex_iterator:: operator =

Porovná iterátory o rovnosti.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Iterátor, pro který se má porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true `*this` , pokud a *Right* jsou iterace koncového pořadí nebo `begin == right.begin`Pokud ani není iterátorem konci sekvence a, `end == right.end`, `pregex == right.pregex`a `flags == right.flags`. V opačném případě vrátí hodnotu false.

## <a name="op_arrow"></a>regex_iterator:: operator-&gt;

Přistupuje k určené shodě.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené hodnoty `match`.

## <a name="pointer"></a>regex_iterator::p ointer

Typ ukazatele na shodu.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `match_results<BidIt>*`, kde `BidIt` je parametr šablony.

## <a name="reference"></a>regex_iterator:: Reference

Typ odkazu na shodu.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `match_results<BidIt>&`, kde `BidIt` je parametr šablony.

## <a name="regex_iterator"></a>regex_iterator::regex_iterator

Vytvoří iterátor.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

*první*\
Začátek sekvence, která se má shodovat

*posledního*\
Konec sekvence, která se má shodovat.

*odebrat*\
Regulární výraz pro shody

*FJ*\
Příznaky pro shody

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iterátor konec sekvence. Druhý konstruktor inicializuje uloženou hodnotu `begin` jako *první*, uloženou hodnotu `end` s *Poslední*, uloženou `pregex` hodnotou s `&re`a uloženou hodnotou `flags` v *f*. Pak volá `regex_search(begin, end, match, *pregex, flags)`. Pokud se hledání nepovede, konstruktor nastaví objekt na iteraci na konci sekvence.

## <a name="regex_type"></a>  regex_iterator::regex_type

Typ regulárního výrazu, který se má shodovat.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>regex_iterator::value_type

Typ shody.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `match_results<BidIt>`, kde `BidIt` je parametr šablony.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)\
[regex_constants – třída](../standard-library/regex-constants-class.md)\
[regex_error – třída](../standard-library/regex-error-class.md)\
[\<regulární funkce >](../standard-library/regex-functions.md)\
[regex_iterator – třída](../standard-library/regex-iterator-class.md)\
[\<operátory > Regex](../standard-library/regex-operators.md)\
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)\
[regex_traits – třída](../standard-library/regex-traits-class.md)\
[\<Regex > definice typedef](../standard-library/regex-typedefs.md)
