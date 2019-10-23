---
title: regex_token_iterator – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_token_iterator
- regex/std::regex_token_iterator::regex_type
- regex/std::regex_token_iterator::value_type
- regex/std::regex_token_iterator::iterator_category
- regex/std::regex_token_iterator::difference_type
- regex/std::regex_token_iterator::pointer
- regex/std::regex_token_iterator::reference
- regex/std::regex_token_iterator::operator==
- regex/std::regex_token_iterator::operator!=
- regex/std::regex_token_iterator::operator*
- regex/std::regex_token_iterator::operator->
- regex/std::regex_token_iterator::operator++
helpviewer_keywords:
- std::regex_token_iterator [C++]
- std::regex_token_iterator [C++], regex_type
- std::regex_token_iterator [C++], value_type
- std::regex_token_iterator [C++], iterator_category
- std::regex_token_iterator [C++], difference_type
- std::regex_token_iterator [C++], pointer
- std::regex_token_iterator [C++], reference
ms.assetid: a213ba48-8e4e-4b6b-871a-2637acf05f15
ms.openlocfilehash: 57fac1d9d5c73c2644a679402809933290dd3fc3
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689060"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator – třída

Iterátor třídy pro podshody

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>Parametry

@No__t_1 *BiDi*
Typ iterátoru pro podshody.

*Elem* \
Typ prvků, které se mají spárovat.

*RXtraits* \
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt konstanty dopředné iterátory. V koncepčním případě obsahuje objekt `regex_iterator`, který používá pro hledání shody regulárních výrazů ve znakové sekvenci. Extrahuje objekty typu `sub_match<BidIt>` reprezentující podshody identifikované hodnotami indexu v uloženém vektorovém `subs` pro každou shodu regulárního výrazu.

Hodnota indexu-1 označuje sekvenci znaků začínající bezprostředně po konci předchozího regulárního výrazu nebo začíná na začátku sekvence znaků, pokud se neshoduje předchozí regulární výraz a rozšíření na, ale ne. včetně prvního znaku aktuálního regulárního výrazu nebo na konec sekvence znaků, pokud neexistuje žádná aktuální shoda. Jakákoli jiná hodnota indexu `idx` určí obsah skupiny zachycení uložené v `it.match[idx]`.

### <a name="members"></a>Členové

|Člen|Výchozí hodnota|
|-|-|
|`private regex_iterator<BidIt, Elem, RXtraits> it`||
|`private vector<int> subs`||
|`private int pos`||

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_token_iterator](#regex_token_iterator)|Vytvoří iterátor.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[difference_type](#difference_type)|Typ rozdílu iterátoru.|
|[iterator_category](#iterator_category)|Typ kategorie iterátoru|
|[ukazatele](#pointer)|Typ ukazatele na shodu.|
|[odkaz](#reference)|Typ odkazu na podshodu.|
|[regex_type](#regex_type)|Typ regulárního výrazu, který se má shodovat.|
|[value_type](#value_type)|Typ podshody.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Porovná iterátory pro nerovnost.|
|[podnikatel](#op_star)|Přistupuje k určené podshodě.|
|[operator + + – operátor](#op_add_add)|Zvýší iterátor.|
|[operator = = – operátor](#op_eq_eq)|Porovná iterátory o rovnosti.|
|[operátor->](#op_arrow)|Přistupuje k určené podshodě.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex >

**Obor názvů:** std

## <a name="example"></a>Příklad

```cpp
#include <regex>
#include <iostream>

typedef std::regex_token_iterator<const char *> Myiter;
int main()
    {
    const char *pat = "aaxaayaaz";
    Myiter::regex_type rx("(a)a");
    Myiter next(pat, pat + strlen(pat), rx);
    Myiter end;

// show whole match
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefix before match
    next = Myiter(pat, pat + strlen(pat), rx, -1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show (a) submatch only
    next = Myiter(pat, pat + strlen(pat), rx, 1);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and submatches
    std::vector<int> vec;
    vec.push_back(-1);
    vec.push_back(1);
    next = Myiter(pat, pat + strlen(pat), rx, vec);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

// show prefixes and whole matches
    int arr[] = {-1, 0};
    next = Myiter(pat, pat + strlen(pat), rx, arr);
    for (; next != end; ++next)
        std::cout << "match == " << next->str() << std::endl;
    std::cout << std::endl;

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
match == aa
match == aa
match == aa

match ==
match == x
match == y
match == z

match == a
match == a
match == a

match ==
match == a
match == x
match == a
match == y
match == a
match == z

match ==
match == aa
match == x
match == aa
match == y
match == aa
match == z
```

## <a name="difference_type"></a>regex_token_iterator::d ifference_type

Typ rozdílu iterátoru.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::ptrdiff_t`.

## <a name="iterator_category"></a>regex_token_iterator::iterator_category

Typ kategorie iterátoru

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::forward_iterator_tag`.

## <a name="op_neq"></a>regex_token_iterator:: operator! =

Porovná iterátory pro nerovnost.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Iterátor, pro který se má porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce vrací `!(*this == right)`.

## <a name="op_star"></a>regex_token_iterator:: operator * – operátor

Přistupuje k určené podshodě.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt `sub_match<BidIt>` reprezentující skupinu zachycení identifikovanou hodnotou indexu `subs[pos]`.

## <a name="op_add_add"></a>regex_token_iterator:: operator + +

Zvýší iterátor.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>Poznámky

Pokud je uložený iterátor `it` sekvencí end-Sequence, první operátor nastaví uloženou hodnotu `pos` na hodnotu `subs.size()` (takže vytvoří iterátor konec sekvence). Jinak operátor zvýší uloženou hodnotu `pos`; Pokud je výsledek roven hodnotě `subs.size()` nastaví uloženou hodnotu `pos` na nulu a zvýší uložený iterátor `it`. Pokud se zvýšením uloženého iterátoru ponechá, že je nerovno iterátoru koncové sekvence, operátor neprovede žádné další akce. V opačném případě, pokud byl konec předchozí shody na konci sekvence znaků, operátor nastaví uloženou hodnotu `pos` na `subs.size()`. V opačném případě operátor opakovaně zvyšuje uloženou hodnotu `pos` až do `pos == subs.size()` nebo `subs[pos] == -1` (čímž zajistíte, že další zpětný odkaz na iterátor vrátí konec sekvence znaků, pokud je jedna z hodnot indexu-1). Ve všech případech operátor vrací objekt.

Druhý operátor vytvoří kopii objektu, zvýší objekt a vrátí kopii.

## <a name="op_eq_eq"></a>regex_token_iterator:: operator = = – operátor

Porovná iterátory o rovnosti.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Iterátor, pro který se má porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce vrací `it == right.it && subs == right.subs && pos == right.pos`.

## <a name="op_arrow"></a>regex_token_iterator:: operator-&gt;

Přistupuje k určené podshodě.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrací ukazatel na objekt `sub_match<BidIt>` reprezentující skupinu zachycení identifikovanou hodnotou indexu `subs[pos]`.

## <a name="pointer"></a>regex_token_iterator::p ointer

Typ ukazatele na shodu.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `sub_match<BidIt>*`, kde `BidIt` je parametr šablony.

## <a name="reference"></a>regex_token_iterator:: Reference

Typ odkazu na podshodu.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `sub_match<BidIt>&`, kde `BidIt` je parametr šablony.

## <a name="regex_token_iterator"></a>regex_token_iterator::regex_token_iterator

Vytvoří iterátor.

```cpp
regex_token_iterator();

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, int submatch = 0,
    regex_constants::match_flag_type f = regex_constants::match_default);

regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const vector<int> submatches,
    regex_constants::match_flag_type f = regex_constants::match_default);

template <std::size_t N>
regex_token_iterator(BidIt first, BidIt last,
    const regex_type& re, const int (&submatches)[N],
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

První konstruktor vytvoří iterátor konec sekvence.

Druhý konstruktor vytvoří objekt, jehož uložené iterátory `it` jsou inicializovány na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jejichž uložený vektorový `subs` obsahuje přesně jedno celé číslo, s hodnotou `submatch` a jehož uložená hodnota `pos` je nula. Poznámka: výsledný objekt extrahuje dílčí shodu identifikovanou hodnotou indexu `submatch` pro každou úspěšnou shodu regulárního výrazu.

Třetí konstruktor vytvoří objekt, jehož uložené iterátory `it` jsou inicializovány na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jejichž uložený vektorový `subs` obsahuje kopii argumentu konstruktoru `submatches` a jehož uložená hodnota `pos` je nula.

Čtvrtý konstruktor vytvoří objekt, jehož uložené iterátory `it` jsou inicializovány na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jejichž uložený vektorový `subs` obsahuje `N` hodnoty, na které odkazoval argument konstruktoru `submatches` a jehož uložená hodnota `pos` je nula.

## <a name="regex_type"></a>regex_token_iterator::regex_type

Typ regulárního výrazu, který se má shodovat.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem pro `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>regex_token_iterator::value_type

Typ podshody.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `sub_match<BidIt>`, kde `BidIt` je parametr šablony.

## <a name="see-also"></a>Viz také:

[\<regex >](../standard-library/regex.md) \
\ [třídy regex_constants](../standard-library/regex-constants-class.md)
\ [třídy regex_error](../standard-library/regex-error-class.md)
[funkce \<regex >](../standard-library/regex-functions.md) \
\ [třídy regex_iterator](../standard-library/regex-iterator-class.md)
[operátory \<regex >](../standard-library/regex-operators.md) \
\ [třídy regex_traits](../standard-library/regex-traits-class.md)
[\<regex > definice typedef](../standard-library/regex-typedefs.md)
