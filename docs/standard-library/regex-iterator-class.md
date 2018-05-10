---
title: regex_iterator – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_iterator
- regex/std::regex_iterator::operator==
- regex/std::regex_iterator::operator!=
- regex/std::regex_iterator::operator*
- regex/std::regex_iterator::operator->
- regex/std::regex_iterator::operator++
dev_langs:
- C++
helpviewer_keywords:
- std::regex_iterator
- std::regex_iterator::operator==
- std::regex_iterator::operator!=
- std::regex_iterator::operator*
- std::regex_iterator::operator->
- std::regex_iterator::operator++
ms.assetid: 0cfd8fd0-5a95-4f3c-bf8e-6ef028c423d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fffa778854519bff6f947aec779e36b77fd4e202
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="regexiterator-class"></a>regex_iterator – třída

Iterator – třída pro odpovídající položky.

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator {
public:
   typedef basic_regex<Elem, RXtraits> regex_type;
   typedef match_results<BidIt> value_type;
   typedef std::forward_iterator_tag iterator_category;
   typedef std::ptrdiff_t difference_type;
   typedef const match_results<BidIt>* pointer;
   typedef const match_results<BidIt>& reference;

   regex_iterator();
   regex_iterator(
      BidIt first, BidIt last, const regex_type& re,
      regex_constants::match_flag_type f = regex_constants::match_default);

   bool operator==(const regex_iterator& right);
   bool operator!=(const regex_iterator& right);
   const match_results<BidIt>& operator*();
   const match_results<BidIt> * operator->();
   regex_iterator& operator++();
   regex_iterator& operator++(int);

private:
   BidIt begin; // exposition only
   BidIt end; // exposition only
   regex_type *pregex;     // exposition only
   regex_constants::match_flag_type flags; // exposition only
   match_results<BidIt> match; // exposition only
   };
```

### <a name="parameters"></a>Parametry

`BidIt` Typ iterator submatches.

`Elem` Typ elementů.

`RXtraits` Třída vlastnosti pro elementy.

## <a name="remarks"></a>Poznámky

Šablony třídy popisuje konstantní dopředného iterator objektu. Extrahuje objekty typu `match_results<BidIt>` opakovaně použitím jeho objekt regulárního výrazu `*pregex` znak pořadí definované rozsahu iterator `[begin, end)`.

## <a name="examples"></a>Příklady

Najdete v následujících tématech Příklady regulárních výrazů:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [Swap](../standard-library/regex-functions.md#swap)

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex >

**Namespace:** – std

## <a name="difference_type"></a>  regex_iterator::difference_type

Typ iterator rozdíl.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `std::ptrdiff_t`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_difference_type.cpp
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

## <a name="iterator_category"></a>  regex_iterator::iterator_category

Typ kategorie iterator.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `std::forward_iterator_tag`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_iterator_category.cpp
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

## <a name="op_neq"></a>  regex_iterator::Operator! =

Porovná nerovnost iterátory.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

`right` Iterator pro porovnání.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu `!(*this == right)`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_operator_ne.cpp
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

## <a name="op_star"></a>  regex_iterator::Operator *

Přístup k určené shody.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu uložené `match`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_operator_star.cpp
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

## <a name="op_add_add"></a>  regex_iterator::Operator ++

Zvýší iteraci.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Poznámky

Pokud aktuální shoda se žádné znaky první operátor zavolá `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; v opačném případě se posune uložené hodnoty `begin` tak, aby odkazoval na první znak po aktuálním odpovídat pak volání `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. V obou případech Pokud se hledání nezdaří operátor nastaví objekt iterovat koncová sekvence. Operátor vrátí objekt.

Druhý operátor vytvoří kopii objektu, zvýší objektu a pak vrátí kopie.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_operator_inc.cpp
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

## <a name="op_eq"></a>  regex_iterator::Operator =

Porovná iterátory rovnosti.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

`right` Iterator pro porovnání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true, pokud `*this` a `right` iterátory end pořadí nebo pokud je ani iterátor koncová sekvence a `begin == right.begin`, `end == right.end`, `pregex == right.pregex`, a `flags == right.flags`. V opačném případě vrátí hodnotu false.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_operator_as.cpp
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

## <a name="op_arrow"></a>  regex_iterator::Operator-&gt;

Přístup k určené shody.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uložené hodnoty `match`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_operator_arrow.cpp
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

## <a name="pointer"></a>  regex_iterator::Pointer

Typ ukazatele na shodu.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `match_results<BidIt>*`, kde `BidIt` je parametr šablony.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_pointer.cpp
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

## <a name="reference"></a>  regex_iterator::Reference

Typ odkaz na shodu.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `match_results<BidIt>&`, kde `BidIt` je parametr šablony.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_reference.cpp
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

## <a name="regex_iterator"></a>  regex_iterator::regex_iterator

Vytvoří iteraci.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

`first` Začátek pořadí tak, aby odpovídaly.

`last` Konec pořadí tak, aby odpovídaly.

`re` Regulární výraz pro odpovídající položky.

`f` Příznaky pro odpovídající položky.

### <a name="remarks"></a>Poznámky

První konstruktoru vytvoří iterovat koncová sekvence. Druhý konstruktor inicializuje uložené hodnoty `begin` s `first`, uložené hodnoty `end` s `last`, uložené hodnoty `pregex` s `&re`a uložené hodnoty `flags` s `f`. Potom zavolá `regex_search(begin, end, match, *pregex, flags)`. Pokud se hledání nezdaří, nastaví konstruktoru objektu na iterovat koncová sekvence.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_construct.cpp
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

## <a name="regex_type"></a>  regex_iterator::regex_type

Typ odpovídající regulární výraz.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef se jedná o synonymum `basic_regex<Elem, RXtraits>`.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_regex_type.cpp
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

## <a name="value_type"></a>  regex_iterator::value_type

Druh shody.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ se jedná o synonymum `match_results<BidIt>`, kde `BidIt` je parametr šablony.

### <a name="example"></a>Příklad

```cpp
// std__regex__regex_iterator_value_type.cpp
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

## <a name="see-also"></a>Viz také

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
