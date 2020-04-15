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
ms.openlocfilehash: 5ada2ad69cbcac15e09968045e54095dfb2623d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366402"
---
# <a name="regex_token_iterator-class"></a>regex_token_iterator – třída

Třída Iterátor pro podzápasy.

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>Parametry

*BidIt*\
Typ iterátoru pro podzápasy.

*Elem*\
Typ prvků, které se mají spárovat.

*RXtraits*\
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt konstantní dopředu iterátoru. Koncepčně obsahuje `regex_iterator` objekt, který používá k hledání shody regulárních výrazů v posloupnosti znaků. Extrahuje objekty `sub_match<BidIt>` typu představující dílčí shody identifikované hodnotami indexu v uloženém vektoru `subs` pro každou shodu regulárních výrazů.

Hodnota indexu -1 označuje posloupnost znaků začínající bezprostředně po skončení předchozí shody regulárních výrazů nebo počínaje začátkem sekvence znaků, pokud nebyla žádná předchozí shoda regulárních výrazů, a rozšiřuje se na první znak aktuální shody regulárních výrazů nebo na konec sekvence znaků, pokud neexistuje žádná aktuální shoda. Jakákoli jiná `idx` hodnota indexu označuje obsah skupiny `it.match[idx]`zachycení držené v .

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
|[iterator_category](#iterator_category)|Typ kategorie iterátoru.|
|[ukazatel](#pointer)|Typ ukazatele na shodu.|
|[Odkaz](#reference)|Typ odkazu na dílčí shodu.|
|[regex_type](#regex_type)|Typ regulárního výrazu, který se má shodovat.|
|[value_type](#value_type)|Typ dílčí shody.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor!=](#op_neq)|Porovnává iterátory pro nerovnost.|
|[operátor*](#op_star)|Přistupuje k určené dílčí shodě.|
|[operátor++](#op_add_add)|Zintáží iterátor.|
|[operátor==](#op_eq_eq)|Porovnává iterátory pro rovnost.|
|[operátor->](#op_arrow)|Přistupuje k určené dílčí shodě.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex>

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

## <a name="regex_token_iteratordifference_type"></a><a name="difference_type"></a>regex_token_iterator::difference_type

Typ rozdílu iterátoru.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `std::ptrdiff_t`pro .

## <a name="regex_token_iteratoriterator_category"></a><a name="iterator_category"></a>regex_token_iterator::iterator_category

Typ kategorie iterátoru.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `std::forward_iterator_tag`pro .

## <a name="regex_token_iteratoroperator"></a><a name="op_neq"></a>regex_token_iterator::operátor!=

Porovnává iterátory pro nerovnost.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Iterátor porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce `!(*this == right)`vrátí .

## <a name="regex_token_iteratoroperator"></a><a name="op_star"></a>regex_token_iterator::operátor*

Přistupuje k určené dílčí shodě.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>Poznámky

Členská funkce `sub_match<BidIt>` vrátí objekt představující skupinu sběru `subs[pos]`identifikovaný hodnotou indexu .

## <a name="regex_token_iteratoroperator"></a><a name="op_add_add"></a>regex_token_iterator::operátor++

Zintáží iterátor.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>Poznámky

Pokud uložený iterátor `it` je end-of-sequence iterátor první operátor `pos` nastaví uloženou hodnotu na hodnotu `subs.size()` (tedy provedení end-of-sequence iterátor). V opačném případě operátor inkumuje uloženou hodnotu `pos`; pokud je výsledek roven `subs.size()` hodnotě, `pos` nastaví uloženou hodnotu na nulu `it`a zintáží uložený iterátor . Pokud zvýšení uložené iterátor uchová nerovné na konci sekvence iterátoru operátor neprovede nic dalšího. V opačném případě pokud byl konec předchozí shody na konci sekvence znaků, `pos` `subs.size()`operátor nastaví uloženou hodnotu na . V opačném případě operátor opakovaně zvýší uloženou `pos == subs.size()` `subs[pos] == -1` hodnotu `pos` do nebo (a tím zajistí, že další dereference iterátoru vrátí ocas sekvence znaků, pokud je jedna z hodnot indexu -1). Ve všech případech operátor vrátí objekt.

Druhý operátor vytvoří kopii objektu, zintáží objekt a potom vrátí kopii.

## <a name="regex_token_iteratoroperator"></a><a name="op_eq_eq"></a>regex_token_iterator::operátor==

Porovnává iterátory pro rovnost.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Iterátor porovnat.

### <a name="remarks"></a>Poznámky

Členská funkce `it == right.it && subs == right.subs && pos == right.pos`vrátí .

## <a name="regex_token_iteratoroperator-gt"></a><a name="op_arrow"></a>regex_token_iterator::operátor-&gt;

Přistupuje k určené dílčí shodě.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí ukazatel `sub_match<BidIt>` na objekt představující skupinu sběru identifikovanou hodnotou `subs[pos]`indexu .

## <a name="regex_token_iteratorpointer"></a><a name="pointer"></a>regex_token_iterator::pointer

Typ ukazatele na shodu.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `sub_match<BidIt>*`pro `BidIt` , kde je parametr šablony.

## <a name="regex_token_iteratorreference"></a><a name="reference"></a>regex_token_iterator::odkaz

Typ odkazu na dílčí shodu.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `sub_match<BidIt>&`pro `BidIt` , kde je parametr šablony.

## <a name="regex_token_iteratorregex_token_iterator"></a><a name="regex_token_iterator"></a>regex_token_iterator::regex_token_iterator

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

*První*\
Začátek sekvence tak, aby odpovídaly.

*Poslední*\
Konec sekvence tak, aby odpovídala.

*Re*\
Regulární výraz pro shody.

*F*\
Příznaky pro zápasy.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iterátor na konci sekvence.

Druhý konstruktor vytvoří objekt, jehož uložený `it` iterátor je inicializován na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jehož uložený vektor `subs` obsahuje přesně jedno celé číslo s hodnotou `submatch`a jehož uložená hodnota `pos` je nulová. Poznámka: Výsledný objekt extrahuje dílčí shodu identifikovanou hodnotou `submatch` indexu pro každou úspěšnou shodu regulárních výrazů.

Třetí konstruktor vytvoří objekt, jehož uložený `it` iterátor je inicializován na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jehož uložený vektor `subs` obsahuje kopii argumentu `submatches`konstruktoru a jehož uložená hodnota `pos` je nulová.

Čtvrtý konstruktor vytvoří objekt, jehož uložený iterátor `it` je inicializován na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jehož uložený vektor `subs` obsahuje `N` hodnoty, na které je argument konstruktoru `submatches`a jehož uložená hodnota `pos` je nulová.

## <a name="regex_token_iteratorregex_type"></a><a name="regex_type"></a>regex_token_iterator::regex_type

Typ regulárního výrazu, který se má shodovat.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem `basic_regex<Elem, RXtraits>`pro .

## <a name="regex_token_iteratorvalue_type"></a><a name="value_type"></a>regex_token_iterator::value_type

Typ dílčí shody.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `sub_match<BidIt>`pro `BidIt` , kde je parametr šablony.

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_constants třída](../standard-library/regex-constants-class.md)\
[regex_error třída](../standard-library/regex-error-class.md)\
[\<funkce> regulárních výrazů](../standard-library/regex-functions.md)\
[regex_iterator třída](../standard-library/regex-iterator-class.md)\
[\<operátory> regulárních výrazů](../standard-library/regex-operators.md)\
[třída regex_traits](../standard-library/regex-traits-class.md)\
[\<regulární> typedefs](../standard-library/regex-typedefs.md)
