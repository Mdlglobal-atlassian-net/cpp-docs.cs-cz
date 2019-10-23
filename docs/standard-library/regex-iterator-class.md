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
ms.openlocfilehash: fb609df2bf52873dac3cddaa6b12f82ea1b53237
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689087"
---
# <a name="regex_iterator-class"></a>regex_iterator – třída

Iterátor třídy pro shody

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parametry

@No__t_1 *BiDi*
Typ iterátoru pro podshody.

*Elem* \
Typ prvků, které se mají spárovat.

*RXtraits* \
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt konstanty dopředné iterátory. Extrahuje objekty typu `match_results<BidIt>` tím, že opakovaně aplikuje objekt regulárního výrazu `*pregex` na sekvenci znaků definovanou `[begin, end)` rozsahu iterátoru.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_iterator](#regex_iterator)|Vytvoří iterátor.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterator_category](#iterator_category)|Typ kategorie iterátoru|
|[ukazatele](#pointer)|Typ ukazatele na shodu.|
|[odkaz](#reference)|Typ odkazu na shodu.|
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

**Záhlaví:** \<regex >

**Obor názvů:** std

## <a name="examples"></a>Příklady

Příklady regulárních výrazů najdete v následujících tématech:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [adresu](../standard-library/regex-functions.md#swap)

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

## <a name="difference_type"></a>regex_iterator::d ifference_type

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

*pravé* \
Iterátor, pro který se má porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce vrací `!(*this == right)`.

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

Pokud aktuální shoda nemá žádné znaky, první volá operátor `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; v opačném případě posune uloženou hodnotu `begin` tak, aby odkazovala na první znak po aktuální shodě, potom zavolá `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. V obou případech, pokud vyhledávání neuspěje, operátor nastaví objekt na iteraci na konci sekvence. Operátor vrací objekt.

Druhý operátor vytvoří kopii objektu, zvýší objekt a vrátí kopii.

## <a name="op_eq"></a>regex_iterator:: operator =

Porovná iterátory o rovnosti.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Iterátor, pro který se má porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true, pokud `*this` a *Right* jsou iterátory koncových sekvencí nebo pokud se nejedná o iterátor a `begin == right.begin`, `end == right.end`, `pregex == right.pregex` a `flags == right.flags`. V opačném případě vrátí hodnotu false.

## <a name="op_arrow"></a>regex_iterator:: operator-&gt;

Přistupuje k určené shodě.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu `match` uložené hodnoty.

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

*první* \
Začátek sekvence, která se má shodovat

*poslední* \
Konec sekvence, která se má shodovat.

*znovu* \
Regulární výraz pro shody

\ *f*
Příznaky pro shody

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iterátor konec sekvence. Druhý konstruktor inicializuje uloženou hodnotu `begin` *nejprve*s uloženou hodnotou `end` *Poslední*, uloženou hodnotou `pregex` s `&re` a uloženou hodnotou `flags` s *f*. Pak volá `regex_search(begin, end, match, *pregex, flags)`. Pokud se hledání nepovede, konstruktor nastaví objekt na iteraci na konci sekvence.

## <a name="regex_type"></a>regex_iterator::regex_type

Typ regulárního výrazu, který se má shodovat.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem pro `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>regex_iterator::value_type

Typ shody.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `match_results<BidIt>`, kde `BidIt` je parametr šablony.

## <a name="see-also"></a>Viz také:

[\<regex >](../standard-library/regex.md) \
\ [třídy regex_constants](../standard-library/regex-constants-class.md)
\ [třídy regex_error](../standard-library/regex-error-class.md)
[funkce \<regex >](../standard-library/regex-functions.md) \
\ [třídy regex_iterator](../standard-library/regex-iterator-class.md)
[operátory \<regex >](../standard-library/regex-operators.md) \
\ [třídy regex_token_iterator](../standard-library/regex-token-iterator-class.md)
\ [třídy regex_traits](../standard-library/regex-traits-class.md)
[\<regex > definice typedef](../standard-library/regex-typedefs.md)
