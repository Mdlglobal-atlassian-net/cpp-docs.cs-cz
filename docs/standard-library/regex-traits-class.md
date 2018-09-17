---
title: regex_traits – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff45758e0c458ea333595ced51476826651b593e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723889"
---
# <a name="regextraits-class"></a>regex_traits – třída

Popisuje charakteristiky elementů pro porovnání.

## <a name="syntax"></a>Syntaxe

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu znaků pro popis.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje různé vlastnosti regulárního výrazu pro typ *Elem*. Třída šablony [basic_regex – třída](../standard-library/basic-regex-class.md) používá tuto informaci k manipulaci s prvky typu *Elem*.

Každý `regex_traits` obsahuje objekt typu `regex_traits::locale` která je používána některými jeho členských funkcí. Výchozí národní prostředí je kopie `regex_traits::locale()`. Členská funkce `imbue` nahrazuje objekt národního prostředí a členské funkce `getloc` vrátí kopii objektu národního prostředí.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_traits –](#regex_traits)|Vytvoří objekt.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_class_type](#char_class_type)|Typ třídy specifikátory znak.|
|[char_type](#char_type)|Typ prvku|
|[locale_type](#locale_type)|Typ objektu uloženého národního prostředí.|
|[size_type](#size_type)|Typ délka sekvence.|
|[STRING_TYPE](#string_type)|Typ prvků řetězce.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[getloc –](#getloc)|Vrátí objekt uloženého národního prostředí.|
|[imbue –](#imbue)|Změní objekt uloženého národního prostředí.|
|[isctype –](#isctype)|Testy pro členství ve třídě.|
|[Délka](#length)|Vrátí délku objektu sekvence zakončená hodnotou null.|
|[lookup_classname](#lookup_classname)|Sekvence se mapuje na třídu znaků.|
|[lookup_collatename –](#lookup_collatename)|Kolační prvek mapuje sekvenci.|
|[Transformace](#transform)|Převede ekvivalent pořadí řazení.|
|[transform_primary –](#transform_primary)|Převede ekvivalent caseless pořadí řazení.|
|[Překlad](#translate)|Převede na ekvivalentní odpovídající prvek.|
|[translate_nocase –](#translate_nocase)|Převede na ekvivalentní caseless odpovídající prvek.|
|[value](#value)|Převede prvek na hodnotu číslice.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regulární výraz >

**Namespace:** std

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

## <a name="char_class_type"></a>  regex_traits::char_class_type

Typ třídy specifikátory znak.

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro neurčeného typu, který určuje třídy znaků. Hodnoty tohoto typu lze spojovat pomocí `|` operátor k určení třídy znaků, které jsou sjednocení tříd operandy určený.

## <a name="char_type"></a>  regex_traits::char_type

Typ prvku

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro argument šablony `Elem`.

## <a name="getloc"></a>  regex_traits::getloc

Vrátí objekt uloženého národního prostředí.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený `locale` objektu.

## <a name="imbue"></a>  regex_traits::imbue

Změní objekt uloženého národního prostředí.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Umístění*<br/>
Objekt národního prostředí pro uložení.

### <a name="remarks"></a>Poznámky

Tyto kopie členské funkce *loc* k uložené `locale` objekt a vrátí kopii objektu předchozí hodnotu uloženou `locale` objektu.

## <a name="isctype"></a>  regex_traits::isctype

Testy pro členství ve třídě.

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Testovaný prvek.

*specifikace CLS*<br/>
Třídy pro testování.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pouze tehdy, pokud znak *ch* je ve třídě znaků určených *kompatibilní se specifikací*.

## <a name="length"></a>  regex_traits::length

Vrátí délku objektu sekvence zakončená hodnotou null.

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>Parametry

*str*<br/>

Posloupnost zakončená hodnotou null.

### <a name="remarks"></a>Poznámky

Statická členská funkce vrátí `std::char_traits<char_type>::length(str)`.

## <a name="locale_type"></a>  regex_traits::locale_type

Typ objektu uloženého národního prostředí.

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ, který zapouzdřuje národní prostředí. V odborností `regex_traits<char>` a `regex_traits<wchar_t>` je synonymum pro `std::locale`.

## <a name="lookup_classname"></a>  regex_traits::lookup_classname

Sekvence se mapuje na třídu znaků.

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Začátek pořadí k vyhledání.

*poslední*<br/>
Konec pořadí k vyhledání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu, která určuje třídu znaků, který je pojmenován podle sekvence znaků, na které odkazuje argumenty. Hodnota není závislý na velká písmena v sekvenci.

Specializace `regex_traits<char>` rozpoznává názvy `"d"`, `"s"`, `"w"`, `"alnum"`, `"alpha"`, `"blank"`, `"cntrl"`, `"digit"`, `"graph"`, `"lower"`, `"print"`, `"punct"`, `"space"`, `"upper"`, a `"xdigit"`, všechny bez ohledu na případ.

Specializace `regex_traits<wchar_t>` rozpoznává názvy `L"d"`, `L"s"`, `L"w"`, `L"alnum"`, `L"alpha"`, `L"blank"`, `L"cntrl"`, `L"digit"`, `L"graph"`, `L"lower"`, `L"print"`, `L"punct"`, `L"space"`, `L"upper"`, a `L"xdigit"`, všechny bez ohledu na případ.

## <a name="lookup_collatename"></a>  regex_traits::lookup_collatename

Kolační prvek mapuje sekvenci.

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Začátek pořadí k vyhledání.

*poslední*<br/>
Konec pořadí k vyhledání.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt string obsahující kolační prvek odpovídající pořadí `[first, last)`, nebo na prázdný řetězec, pokud sekvence není platný kolační prvek.

## <a name="regex_traits"></a>  regex_traits::regex_traits

Vytvoří objekt.

```cpp
regex_traits();
```

### <a name="remarks"></a>Poznámky

Konstruktor vytvoří objekt, jehož uložené `locale` objekt je inicializován pro výchozí národní prostředí.

## <a name="size_type"></a>  regex_traits::size_type

Typ délka sekvence.

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro celočíselný typ bez znaménka. V odborností `regex_traits<char>` a `regex_traits<wchar_t>` je synonymum pro `std::size_t`.

Typedef je synonymum pro `std::size_t`.

## <a name="string_type"></a>  regex_traits::STRING_TYPE

Typ prvků řetězce.

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro `basic_string<Elem>`.

## <a name="transform"></a>  regex_traits::Transform

Převede ekvivalent pořadí řazení.

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Začátek pořadí transformace.

*poslední*<br/>
Konec pořadí transformace.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec, který generuje s použitím pravidla transformace, které závisí na uložených `locale` objektu. Pro dvě znakové sekvence určené rozsahy iterátoru `[first1, last1)` a `[first2, last2)`, `transform(first1, last1) < transform(first2, last2)` Pokud došlo ke shodě sekvence znaků rozsahem iterátoru `[first1, last1)` řadí před sekvence znaků, které jsou určené rozsahem iterátoru `[first2, last2)`.

## <a name="transform_primary"></a>  regex_traits::transform_primary

Převede ekvivalent caseless pořadí řazení.

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Začátek pořadí transformace.

*poslední*<br/>
Konec pořadí transformace.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec, který generuje s použitím pravidla transformace, které závisí na uložených `locale` objektu. Pro dvě znakové sekvence určené rozsahy iterátoru `[first1, last1)` a `[first2, last2)`, `transform_primary(first1, last1) < transform_primary(first2, last2)` Pokud došlo ke shodě sekvence znaků rozsahem iterátoru `[first1, last1)` řadí před sekvence znaků, které jsou určené rozsahem iterátoru `[first2, last2)` bez ohledu na velikost písmen nebo přízvuky.

## <a name="translate"></a>  regex_traits::translate

Převede na ekvivalentní odpovídající prvek.

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Elementu, který chcete převést.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí znak, který generuje s použitím pravidla transformace, které závisí na uložených `locale` objektu. Pro dva `char_type` objekty `ch1` a `ch2`, `translate(ch1) == translate(ch2)` pouze tehdy, pokud `ch1` a `ch2` by měl odpovídat, když v definici regulárních výrazů dojde k jedné a druhý dojde k na odpovídající pozici v cílovém pořadí pro porovnání citlivé na národní prostředí.

## <a name="translate_nocase"></a>  regex_traits::translate_nocase

Převede na ekvivalentní caseless odpovídající prvek.

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Elementu, který chcete převést.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí znak, který generuje s použitím pravidla transformace, které závisí na uložených `locale` objektu. Pro dva `char_type` objekty `ch1` a `ch2`, `translate_nocase(ch1) == translate_nocase(ch2)` pouze tehdy, pokud `ch1` a `ch2` by měl odpovídat, když v definici regulárních výrazů dojde k jedné a druhý dojde k na odpovídající pozici v cílovém pořadí pro porovnávání.

## <a name="value"></a>  regex_traits::Value

Převede prvek na hodnotu číslice.

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Elementu, který chcete převést.

*radix*<br/>
Aritmetické operace základní použití.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu představovanou znakem *ch* v základní třídě *základ číselné soustavy*, nebo -1, pokud *ch* není platnou číslici v základu *základ číselné soustavy*. Funkce bude volána pouze *základ číselné soustavy* argument 8, 10 nebo 16.

## <a name="see-also"></a>Viz také:

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants – třída](../standard-library/regex-constants-class.md)<br/>
[regex_error – třída](../standard-library/regex-error-class.md)<br/>
[\<regulární výraz > funkce](../standard-library/regex-functions.md)<br/>
[regex_iterator – třída](../standard-library/regex-iterator-class.md)<br/>
[\<regulární výraz > operátory](../standard-library/regex-operators.md)<br/>
[regex_token_iterator – třída](../standard-library/regex-token-iterator-class.md)<br/>
[\<regulární výraz > – Definice TypeDef](../standard-library/regex-typedefs.md)<br/>
[regex_traits\<char > třída](../standard-library/regex-traits-char-class.md)<br/>
[regex_traits\<wchar_t > třída](../standard-library/regex-traits-wchar-t-class.md)<br/>
