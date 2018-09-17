---
title: regex_iterator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/10/2018
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
ms.openlocfilehash: b723294c0ecdbdf585acecc257174251b13d56ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710356"
---
# <a name="regexiterator-class"></a>regex_iterator – třída

Iterator – třída pro shody.

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_iterator
```

## <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iterátoru pro dílčí shody.

*Elem*<br/>
Typ prvků, které se mají spárovat.

*RXtraits*<br/>
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt konstanty dopředný iterátor. Extrahuje objekty typu `match_results<BidIt>` opakovaně použitím jeho objekt regulárního výrazu `*pregex` do sekvence znaků, které jsou definovány rozsahem iterátoru `[begin, end)`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_iterator](#regex_iterator)|Vytvoří iterátor.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterator_category](#iterator_category)|Typ iterátoru kategorie.|
|[Ukazatel](#pointer)|Typ ukazatele na shodu.|
|[Referenční dokumentace](#reference)|Typ odkazu na shodu.|
|[regex_type](#regex_type)|Typ odpovídající regulární výraz.|
|[value_type](#value_type)|Typ shody.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Porovná nerovnost iterátory.|
|[Operator *](#op_star)|Přistupuje k určené shoda.|
|[Operator ++](#op_add_add)|Zvýší iterátor.|
|[operátor =](#op_eq)|Porovná rovnost iterátory.|
|[Operator ->](#op_arrow)|Přistupuje k určené shoda.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

## <a name="examples"></a>Příklady

V regulárních výrazech naleznete v následujících tématech příklady:

- [regex_match](../standard-library/regex-functions.md#regex_match)

- [regex_replace](../standard-library/regex-functions.md#regex_replace)

- [regex_search](../standard-library/regex-functions.md#regex_search)

- [Prohození](../standard-library/regex-functions.md#swap)

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

## <a name="iterator_category"></a>  regex_iterator::iterator_category

Typ iterátoru kategorie.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::forward_iterator_tag`.

## <a name="op_neq"></a>  regex_iterator::Operator! =

Porovná nerovnost iterátory.

```cpp
bool operator!=(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Iterátor, který má být porovnán s.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `!(*this == right)`.

## <a name="op_star"></a>  regex_iterator::Operator *

Přistupuje k určené shoda.

```cpp
const match_results<BidIt>& operator*();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uloženou hodnotu `match`.

## <a name="op_add_add"></a>  regex_iterator::Operator ++

Zvýší iterátor.

```cpp
regex_iterator& operator++();
regex_iterator& operator++(int);
```

### <a name="remarks"></a>Poznámky

Pokud aktuální shoda nemá žádné znaky první operátor zavolá `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail | regex_constants::match_not_null)`; v opačném případě zálohy uložené hodnoty `begin` tak, aby odkazoval na první znak za aktuální shodovat pak volání `regex_search(begin, end, match, *pregex, flags | regex_constants::match_prev_avail)`. V obou případech Pokud vyhledávání selže operátor, který nastaví objekt iterátoru koncová sekvence. Operátor vrací objekt.

Druhý operátor vytvoří kopii tohoto objektu, zvýší na objekt a potom vrátí kopii.

## <a name="op_eq"></a>  regex_iterator::Operator =

Porovná rovnost iterátory.

```cpp
bool operator==(const regex_iterator& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Iterátor, který má být porovnán s.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true, pokud `*this` a *správné* koncová sekvence iterátory nebo pokud ani jeden není iterátor koncová sekvence a `begin == right.begin`, `end == right.end`, `pregex == right.pregex`, a `flags == right.flags`. V opačném případě vrátí hodnotu false.

## <a name="op_arrow"></a>  regex_iterator::Operator-&gt;

Přistupuje k určené shoda.

```cpp
const match_results<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí adresu uloženou hodnotu `match`.

## <a name="pointer"></a>  regex_iterator::Pointer

Typ ukazatele na shodu.

```cpp
typedef match_results<BidIt> *pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `match_results<BidIt>*`, kde `BidIt` je parametr šablony.

## <a name="reference"></a>  regex_iterator::Reference

Typ odkazu na shodu.

```cpp
typedef match_results<BidIt>& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `match_results<BidIt>&`, kde `BidIt` je parametr šablony.

## <a name="regex_iterator"></a>  regex_iterator::regex_iterator

Vytvoří iterátor.

```cpp
regex_iterator();

regex_iterator(BidIt first,
    BidIt last,
    const regex_type& re,
    regex_constants::match_flag_type f = regex_constants::match_default);
```

### <a name="parameters"></a>Parametry

*první*<br/>
Začátek pořadí tak, aby odpovídaly.

*poslední*<br/>
Konec pořadí tak, aby odpovídaly.

*RE*<br/>
Regulárních výrazů pro shody.

*f*<br/>
Příznaky pro shody.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iterátor koncová sekvence. Druhý konstruktor inicializuje uložené hodnoty `begin` s *první*, uloženou hodnotu `end` s *poslední*, uloženou hodnotu `pregex` s `&re`a uložená hodnota `flags` s *f*. Poté zavolá `regex_search(begin, end, match, *pregex, flags)`. Pokud se hledání nezdaří, nastaví konstruktor objektu na iterátor koncová sekvence.

## <a name="regex_type"></a>  regex_iterator::regex_type

Typ odpovídající regulární výraz.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>  regex_iterator::value_type

Typ shody.

```cpp
typedef match_results<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `match_results<BidIt>`, kde `BidIt` je parametr šablony.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > – Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
