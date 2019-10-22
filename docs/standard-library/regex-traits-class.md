---
title: regex_traits – třída
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_traits
- regex/std::regex_traits::char_type
- regex/std::regex_traits::size_type
- regex/std::regex_traits::string_type
- regex/std::regex_traits::locale_type
- regex/std::regex_traits::char_class_type
- regex/std::regex_traits::length
- regex/std::regex_traits::translate
- regex/std::regex_traits::translate_nocase
- regex/std::regex_traits::transform
- regex/std::regex_traits::transform_primary
- regex/std::regex_traits::lookup_classname
- regex/std::regex_traits::lookup_collatename
- regex/std::regex_traits::isctype
- regex/std::regex_traits::value
- regex/std::regex_traits::imbue
- regex/std::regex_traits::getloc
helpviewer_keywords:
- std::regex_traits [C++]
- std::regex_traits [C++], char_type
- std::regex_traits [C++], size_type
- std::regex_traits [C++], string_type
- std::regex_traits [C++], locale_type
- std::regex_traits [C++], char_class_type
- std::regex_traits [C++], length
- std::regex_traits [C++], translate
- std::regex_traits [C++], translate_nocase
- std::regex_traits [C++], transform
- std::regex_traits [C++], transform_primary
- std::regex_traits [C++], lookup_classname
- std::regex_traits [C++], lookup_collatename
- std::regex_traits [C++], isctype
- std::regex_traits [C++], value
- std::regex_traits [C++], imbue
- std::regex_traits [C++], getloc
ms.assetid: bc5a5eed-32fc-4eb7-913d-71c42e729e81
ms.openlocfilehash: 2a04e0f1c202717bb6d40a10f07475d78453ffd7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689031"
---
# <a name="regex_traits-class"></a>regex_traits – třída

Popisuje charakteristiky prvků pro porovnání.

## <a name="syntax"></a>Syntaxe

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>Parametry

*Elem* \
Typ prvku znaku, který má být popsán.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje různé vlastnosti regulárních výrazů pro typ *elem*. Třída šablony třídy [basic_regex](../standard-library/basic-regex-class.md) používá tyto informace k manipulaci s prvky typu *elem*.

Každý objekt `regex_traits` obsahuje objekt typu `regex_traits::locale`, který je používán některými z jeho členských funkcí. Výchozím národním prostředím je kopie `regex_traits::locale()`. Členská funkce `imbue` nahradí objekt národního prostředí a členská funkce `getloc` vrátí kopii objektu národního prostředí.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_traits](#regex_traits)|Vytvoří objekt.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_class_type](#char_class_type)|Typ specifikátorů třídy znaků.|
|[char_type](#char_type)|Typ prvku|
|[locale_type](#locale_type)|Typ uloženého objektu národního prostředí.|
|[size_type](#size_type)|Typ délky posloupnosti.|
|[string_type](#string_type)|Typ řetězce prvků.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[getloc](#getloc)|Vrátí uložený objekt národního prostředí.|
|[imbue –](#imbue)|Změní uložený objekt národního prostředí.|
|[isctype –](#isctype)|Testy pro členství ve třídě.|
|[časový](#length)|Vrátí délku sekvence zakončené znakem null.|
|[lookup_classname](#lookup_classname)|Mapuje sekvenci na třídu znaků.|
|[lookup_collatename](#lookup_collatename)|Mapuje sekvenci na řadicí prvek.|
|[převedení](#transform)|Převede na ekvivalentní uspořádanou sekvenci.|
|[transform_primary](#transform_primary)|Převede na ekvivalentní řazenou sekvenci s neodpovídajícími písmeny.|
|[posunut](#translate)|Převede na ekvivalentní odpovídající prvek.|
|[translate_nocase](#translate_nocase)|Převede na ekvivalentní prvek odpovídající velikosti písmen.|
|[value](#value)|Převede element na hodnotu číslice.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex >

**Obor názvů:** std

## <a name="example"></a>Příklad

```cpp
// std__regex__regex_traits.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::regex_traits<char> Mytr;
int main()
    {
    Mytr tr;

    Mytr::char_type ch = tr.translate('a');
    std::cout << "translate('a') == 'a' == " << std::boolalpha
        << (ch == 'a') << std::endl;

    std::cout << "nocase 'a' == 'A' == " << std::boolalpha
        << (tr.translate_nocase('a') == tr.translate_nocase('A'))
        << std::endl;

    const char *lbegin = "abc";
    const char *lend = lbegin + strlen(lbegin);
    Mytr::size_type size = tr.length(lbegin);
    std::cout << "length(\"abc\") == " << size <<std::endl;

    Mytr::string_type str = tr.transform(lbegin, lend);
    std::cout << "transform(\"abc\") < \"abc\" == " << std::boolalpha
        << (str < "abc") << std::endl;

    const char *ubegin = "ABC";
    const char *uend = ubegin + strlen(ubegin);
    std::cout << "primary \"ABC\" < \"abc\" == " << std::boolalpha
        << (tr.transform_primary(ubegin, uend) <
            tr.transform_primary(lbegin, lend))
        << std::endl;

    const char *dig = "digit";
    Mytr::char_class_type cl = tr.lookup_classname(dig, dig + 5);
    std::cout << "class digit == d == " << std::boolalpha
        << (cl == tr.lookup_classname(dig, dig + 1))
        << std::endl;

    std::cout << "'3' is digit == " <<std::boolalpha
        << tr.isctype('3', tr.lookup_classname(dig, dig + 5))
        << std::endl;

    std::cout << "hex C == " << tr.value('C', 16) << std::endl;

// other members
    str = tr.lookup_collatename(dig, dig + 5);

    Mytr::locale_type loc = tr.getloc();
    tr.imbue(loc);

    return (0);
    }
```

```Output
translate('a') == 'a' == true
nocase 'a' == 'A' == true
length("abc") == 3
transform("abc") < "abc" == false
primary "ABC" < "abc" == false
class digit == d == true
'3' is digit == true
hex C == 12
```

## <a name="char_class_type"></a>regex_traits::char_class_type

Typ specifikátorů třídy znaků.

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro nespecifikovaný typ, který určuje třídy znaků. Hodnoty tohoto typu lze kombinovat pomocí operátoru `|` k určení tříd znaků, které jsou sjednocením tříd určených operandy.

## <a name="char_type"></a>regex_traits::char_type

Typ prvku

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro argument šablony `Elem`.

## <a name="getloc"></a>regex_traits:: getloc

Vrátí uložený objekt národního prostředí.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený objekt `locale`.

## <a name="imbue"></a>regex_traits:: imbue –

Změní uložený objekt národního prostředí.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

\ *Loc*
Objekt národního prostředí, který se má uložit

### <a name="remarks"></a>Poznámky

Členská *funkce kopíruje* umístění do uloženého `locale` objektu a vrátí kopii předchozí hodnoty uloženého objektu `locale`.

## <a name="isctype"></a>regex_traits:: isctype –

Testy pro členství ve třídě.

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Prvek, který chcete otestovat.

\ *CLS*
Třídy, které se mají testovat.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pouze v případě, že znak *ch* je ve třídě znaků určené *specifikací CLS*.

## <a name="length"></a>regex_traits:: Length

Vrátí délku sekvence zakončené znakem null.

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>Parametry

\ *str*
Sekvence zakončené znakem null.

### <a name="remarks"></a>Poznámky

Statická členská funkce vrací `std::char_traits<char_type>::length(str)`.

## <a name="locale_type"></a>regex_traits::locale_type

Typ uloženého objektu národního prostředí.

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ, který zapouzdřuje národní prostředí. V specializacích `regex_traits<char>` a `regex_traits<wchar_t>` je synonymem pro `std::locale`.

## <a name="lookup_classname"></a>regex_traits::lookup_classname

Mapuje sekvenci na třídu znaků.

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první* \
Začátek sekvence, která se má vyhledat

*poslední* \
Konec sekvence, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu, která označuje třídu znaků pojmenovanou sekvencí znaků, na kterou odkazuje jeho argumenty. Hodnota nezávisí na velikosti písmen v sekvenci.

Specializace `regex_traits<char>` rozpoznává názvy `"d"`, `"s"`, `"w"`, `"alnum"`, `"alpha"`, `"blank"`, `"cntrl"`, `"digit"`, `"graph"`, 0, 1, 2, 3 , 4 a 5, bez ohledu na velikost písmen.

Specializace `regex_traits<wchar_t>` rozpoznává názvy `L"d"`, `L"s"`, `L"w"`, `L"alnum"`, `L"alpha"`, `L"blank"`, `L"cntrl"`, `L"digit"`, `L"graph"`, 0, 1, 2, 3 , 4 a 5, bez ohledu na velikost písmen.

## <a name="lookup_collatename"></a>regex_traits::lookup_collatename

Mapuje sekvenci na řadicí prvek.

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první* \
Začátek sekvence, která se má vyhledat

*poslední* \
Konec sekvence, která se má vyhledat

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt String obsahující element kompletování odpovídající sekvenci `[first, last)` nebo prázdný řetězec, pokud sekvence není platným prvkem kompletování.

## <a name="regex_traits"></a>regex_traits::regex_traits

Vytvoří objekt.

```cpp
regex_traits();
```

### <a name="remarks"></a>Poznámky

Konstruktor vytvoří objekt, jehož uložený `locale` objekt je inicializován do výchozího národního prostředí.

## <a name="size_type"></a>regex_traits::size_type

Typ délky posloupnosti.

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro celočíselný typ bez znaménka. V specializacích `regex_traits<char>` a `regex_traits<wchar_t>` je synonymem pro `std::size_t`.

Typedef je synonymem pro `std::size_t`.

## <a name="string_type"></a>regex_traits::string_type

Typ řetězce prvků.

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem pro `basic_string<Elem>`.

## <a name="transform"></a>regex_traits:: Transform

Převede na ekvivalentní uspořádanou sekvenci.

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první* \
Začátek sekvence, která se má transformovat

*poslední* \
Konec sekvence, která se má transformovat

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec, který generuje pomocí pravidla transformace, které závisí na uloženém objektu `locale`. Pro dvě sekvence znaků určené rozsahy iterátoru `[first1, last1)` a `[first2, last2)`, `transform(first1, last1) < transform(first2, last2)`, pokud sekvence znaků určená rozsahem iterátoru `[first1, last1)` seřadí před sekvencí znaků určenou `[first2, last2)` rozsahu iterátoru.

## <a name="transform_primary"></a>regex_traits::transform_primary

Převede na ekvivalentní řazenou sekvenci s neodpovídajícími písmeny.

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první* \
Začátek sekvence, která se má transformovat

*poslední* \
Konec sekvence, která se má transformovat

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec, který generuje pomocí pravidla transformace, které závisí na uloženém objektu `locale`. Pro dvě sekvence znaků určené rozsahy iterátoru `[first1, last1)` a `[first2, last2)` `transform_primary(first1, last1) < transform_primary(first2, last2)`, pokud sekvence znaků určená rozsahem iterátoru `[first1, last1)` seřadí před sekvenci znaků určenou rozsahem iterátoru `[first2, last2)` bez ohledu na Case nebo akcenty.

## <a name="translate"></a>regex_traits:: přeložit

Převede na ekvivalentní odpovídající prvek.

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Prvek, který má být převeden.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí znak, který generuje pomocí pravidla transformace, které závisí na uloženém objektu `locale`. Pro dva `char_type` objekty `ch1` a `ch2` `translate(ch1) == translate(ch2)` pouze v případě, že `ch1` a `ch2` by se měla shodovat, pokud k jedné z nich dojde v definici regulárního výrazu a druhá dojde na odpovídající pozici v cílové sekvenci pro porovnávání zohledňující národní prostředí.

## <a name="translate_nocase"></a>regex_traits::translate_nocase

Převede na ekvivalentní prvek odpovídající velikosti písmen.

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Prvek, který má být převeden.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí znak, který generuje pomocí pravidla transformace, které závisí na uloženém objektu `locale`. Pro dva `char_type` objekty `ch1` a `ch2` `translate_nocase(ch1) == translate_nocase(ch2)` pouze v případě, že `ch1` a `ch2` by se měla shodovat, pokud k jedné z nich dojde v definici regulárního výrazu a druhá dojde na odpovídající pozici v cílové sekvenci pro porovnávání bez rozlišení velkých a malých písmen.

## <a name="value"></a>regex_traits:: Value

Převede element na hodnotu číslice.

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Prvek, který má být převeden.

\ *základu*
Aritmetický základ, který se má použít.

### <a name="remarks"></a>Poznámky

Členská funkce vrací hodnotu reprezentovanou znakem *ch* v základní *základové*hodnotě nebo-1, pokud *ch* není platná číslice v *základní základové hodnotě.* Funkce bude volána pouze s argumentem *základu* 8, 10 nebo 16.

## <a name="see-also"></a>Viz také:

[\<regex >](../standard-library/regex.md) \
\ [třídy regex_constants](../standard-library/regex-constants-class.md)
\ [třídy regex_error](../standard-library/regex-error-class.md)
[funkce \<regex >](../standard-library/regex-functions.md) \
\ [třídy regex_iterator](../standard-library/regex-iterator-class.md)
[operátory \<regex >](../standard-library/regex-operators.md) \
\ [třídy regex_token_iterator](../standard-library/regex-token-iterator-class.md)
[\<regex > definice typedef](../standard-library/regex-typedefs.md) \
[regex_traits \<char > třídy](../standard-library/regex-traits-char-class.md) \
[regex_traits \<wchar_t > – třída](../standard-library/regex-traits-wchar-t-class.md)
