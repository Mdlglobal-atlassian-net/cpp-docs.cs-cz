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
ms.openlocfilehash: 2cb66ce4cbee0936211e5e991b18f3ae4b8a7fe5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473512"
---
# <a name="regextokeniterator-class"></a>regex_token_iterator – třída

Iterator – třída pro dílčí shody.

## <a name="syntax"></a>Syntaxe

```cpp
template<class BidIt,
   class Elem = typename std::iterator_traits<BidIt>::value_type,
   class RxTraits = regex_traits<Elem> >
class regex_token_iterator
```

## <a name="parameters"></a>Parametry

*BidIt*<br/>
Typ iterátoru pro dílčí shody.

*Elem*<br/>
Typ prvků, které se mají spárovat.

*RXtraits*<br/>
Třída vlastností prvků.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt konstanty dopředný iterátor. Koncepčně, obsahuje `regex_iterator` objekt, který se používá k hledání regulárního výrazu odpovídá sekvenci znaků. Extrahuje objekty typu `sub_match<BidIt>` představující podshody identifikovaný index hodnoty ve vektoru uložené `subs` pro jednotlivé shody regulárního výrazu.

Posloupnost znaků začínající hned za koncem předchozí shoda s regulárním výrazem, nebo začínající na začátek sekvence znaků, pokud se žádná předchozí shoda s regulárním výrazem a rozšiřuje ji pro, ale ne Určuje hodnotu indexu-1 Pokud není nalezena žádná aktuální shoda, včetně prvního znaku, aktuální shoda s regulárním výrazem nebo na konci sekvence znaků. Jakákoli jiná hodnota indexu `idx` označí obsah nachází ve skupině zachycení `it.match[idx]`.

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
|[iterator_category](#iterator_category)|Typ iterátoru kategorie.|
|[Ukazatel](#pointer)|Typ ukazatele na shodu.|
|[Referenční dokumentace](#reference)|Typ odkazu k dílčí shoda.|
|[regex_type](#regex_type)|Typ odpovídající regulární výraz.|
|[value_type](#value_type)|Typ dílčí shoda.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Porovná nerovnost iterátory.|
|[Operator *](#op_star)|Přistupuje k určené dílčí shoda.|
|[Operator ++](#op_add_add)|Zvýší iterátor.|
|[operator==](#op_eq_eq)|Porovná rovnost iterátory.|
|[Operator ->](#op_arrow)|Přistupuje k určené dílčí shoda.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

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

## <a name="difference_type"></a>  regex_token_iterator::difference_type

Typ rozdílu iterátoru.

```cpp
typedef std::ptrdiff_t difference_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::ptrdiff_t`.

## <a name="iterator_category"></a>  regex_token_iterator::iterator_category

Typ iterátoru kategorie.

```cpp
typedef std::forward_iterator_tag iterator_category;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::forward_iterator_tag`.

## <a name="op_neq"></a>  regex_token_iterator::Operator! =

Porovná nerovnost iterátory.

```cpp
bool operator!=(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Iterátor, který má být porovnán s.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `!(*this == right)`.

## <a name="op_star"></a>  regex_token_iterator::Operator *

Přistupuje k určené dílčí shoda.

```cpp
const sub_match<BidIt>& operator*();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `sub_match<BidIt>` objekt představující skupinu zachycení identifikovat podle hodnoty indexu `subs[pos]`.

## <a name="op_add_add"></a>  regex_token_iterator::Operator ++

Zvýší iterátor.

```cpp
regex_token_iterator& operator++();

regex_token_iterator& operator++(int);
```

### <a name="remarks"></a>Poznámky

Pokud uložený iterátor `it` je uložená hodnota nastaví iterátor koncová sekvence první operátor `pos` hodnotě `subs.size()` (čímž iterátor koncová sekvence). V opačném případě operátor, který zvýší uloženou hodnotu `pos`; Pokud je výsledek rovná hodnotě `subs.size()` nastaví uložené hodnoty `pos` na nulu a zvýší uložený iterátor `it`. Pokud zvyšování hodnoty ponechá uložený iterátor nerovnost iterátor koncová sekvence operátor nedělá nic. dále. V opačném případě, když se konec předchozí shoda se na konci sekvence znaků operátoru nastaví uložené hodnoty `pos` k `subs.size()`. V opačném případě operátor opakovaně zvýší uloženou hodnotu `pos` dokud `pos == subs.size()` nebo `subs[pos] == -1` (čímž zajišťuje, že další zrušení odkazu iterátoru vrátí zadní části sekvence znaků, pokud jedna z hodnot indexu je -1). Ve všech případech operátor vrací objekt.

Druhý operátor vytvoří kopii tohoto objektu, zvýší na objekt a potom vrátí kopii.

## <a name="op_eq_eq"></a>  regex_token_iterator::Operator ==

Porovná rovnost iterátory.

```cpp
bool operator==(const regex_token_iterator& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Iterátor, který má být porovnán s.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `it == right.it && subs == right.subs && pos == right.pos`.

## <a name="op_arrow"></a>  regex_token_iterator::Operator-&gt;

Přistupuje k určené dílčí shoda.

```cpp
const sub_match<BidIt> * operator->();
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí ukazatel `sub_match<BidIt>` objekt představující skupinu zachycení identifikovat podle hodnoty indexu `subs[pos]`.

## <a name="pointer"></a>  regex_token_iterator::Pointer

Typ ukazatele na shodu.

```cpp
typedef sub_match<BidIt> *pointer;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `sub_match<BidIt>*`, kde `BidIt` je parametr šablony.

## <a name="reference"></a>  regex_token_iterator::Reference

Typ odkazu k dílčí shoda.

```cpp
typedef sub_match<BidIt>& reference;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `sub_match<BidIt>&`, kde `BidIt` je parametr šablony.

## <a name="regex_token_iterator"></a>  regex_token_iterator::regex_token_iterator

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

*první*<br/>
Začátek pořadí tak, aby odpovídaly.

*poslední*<br/>
Konec pořadí tak, aby odpovídaly.

*RE*<br/>
Regulárních výrazů pro shody.

*f*<br/>
Příznaky pro shody.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří iterátor koncová sekvence.

Druhý konstruktor vytvoří objekt, jehož uložený iterátor `it` je inicializován na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jehož uložené vektoru `subs` obsahuje přesně jeden celé číslo s hodnotou `submatch`a jehož uložená hodnota `pos` je nula. Poznámka: výsledný objekt extrahuje dílčí shoda, identifikovat podle hodnoty indexu `submatch` pro jednotlivé shody úspěšné regulární výraz.

Třetí konstruktor vytvoří objekt, jehož uložený iterátor `it` je inicializován na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jehož uložené vektoru `subs` obsahuje kopii argument konstruktoru `submatches`a jehož uložená hodnota `pos` je nula.

Čtvrtý konstruktor vytvoří objekt, jehož uložený iterátor `it` je inicializován na `regex_iterator<BidIt, Elem, RXtraits>(first, last, re, f)`, jehož uložené vektoru `subs` obsahuje `N` hodnoty na které odkazuje parametr konstruktoru `submatches`a jehož uložená Hodnota `pos` je nula.

## <a name="regex_type"></a>  regex_token_iterator::regex_type

Typ odpovídající regulární výraz.

```cpp
typedef basic_regex<Elem, RXtraits> regex_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `basic_regex<Elem, RXtraits>`.

## <a name="value_type"></a>  regex_token_iterator::value_type

Typ dílčí shoda.

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `sub_match<BidIt>`, kde `BidIt` je parametr šablony.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_traits – třída](../standard-library/regex-traits-class.md)<br/>
[\<regulární výraz > – Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
