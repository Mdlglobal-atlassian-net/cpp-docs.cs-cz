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
ms.openlocfilehash: 8879336c48d0fec8a20411abf1c07d570a1575e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366394"
---
# <a name="regex_traits-class"></a>regex_traits – třída

Popisuje vlastnosti prvků pro porovnávání.

## <a name="syntax"></a>Syntaxe

```cpp
template<class Elem>
class regex_traits
```

## <a name="parameters"></a>Parametry

*Elem*\
Typ prvku znaku, který chcete popsat.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje různé znaky regulárních výrazů pro typ *Elem*. Šablona třídy [basic_regex Class](../standard-library/basic-regex-class.md) používá tyto informace k manipulaci s prvky typu *Elem*.

Každý `regex_traits` objekt obsahuje objekt `regex_traits::locale` typu, který je používán některými jeho členskými funkcemi. Výchozí národní prostředí je `regex_traits::locale()`kopie aplikace . Členská `imbue` funkce nahradí objekt národního prostředí `getloc` a členská funkce vrátí kopii objektu národního prostředí.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[regex_traits](#regex_traits)|Vytvoří objekt.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_class_type](#char_class_type)|Typ označení třídy znaků.|
|[char_type](#char_type)|Typ prvku|
|[locale_type](#locale_type)|Typ uloženého objektu národního prostředí.|
|[size_type](#size_type)|Typ délky sekvence.|
|[string_type](#string_type)|Typ řetězce prvků.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[getloc](#getloc)|Vrátí uložený objekt národního prostředí.|
|[Naplnit](#imbue)|Změní uložený objekt národního prostředí.|
|[isctype](#isctype)|Testy pro členství ve třídě.|
|[Délka](#length)|Vrátí délku sekvence ukončené hodnotou null.|
|[lookup_classname](#lookup_classname)|Mapuje sekvenci na třídu znaků.|
|[lookup_collatename](#lookup_collatename)|Mapuje sekvenci na kompletující prvek.|
|[Transformace](#transform)|Převede na ekvivalentní seřazené pořadí.|
|[transform_primary](#transform_primary)|Převede na ekvivalentní sekvenci bez případu.|
|[Přeložit](#translate)|Převede na ekvivalentní odpovídající prvek.|
|[translate_nocase](#translate_nocase)|Převede na ekvivalentní prvek bez případu odpovídající.|
|[Hodnotu](#value)|Převede prvek na hodnotu číslice.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<regex>

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

## <a name="regex_traitschar_class_type"></a><a name="char_class_type"></a>regex_traits::char_class_type

Typ označení třídy znaků.

```cpp
typedef T8 char_class_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro nespecifikovaný typ, který označuje třídy znaků. Hodnoty tohoto typu lze kombinovat `|` pomocí operátoru k označení tříd znaků, které jsou sjednocením tříd určených operandy.

## <a name="regex_traitschar_type"></a><a name="char_type"></a>regex_traits::char_type

Typ prvku

```cpp
typedef Elem char_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem pro `Elem`argument šablony .

## <a name="regex_traitsgetloc"></a><a name="getloc"></a>regex_traits::getloc

Vrátí uložený objekt národního prostředí.

```cpp
locale_type getloc() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `locale` uložený objekt.

## <a name="regex_traitsimbue"></a><a name="imbue"></a>regex_traits::imbue

Změní uložený objekt národního prostředí.

```cpp
locale_type imbue(locale_type loc);
```

### <a name="parameters"></a>Parametry

*Loc*\
Objekt národního prostředí, který chcete uložit.

### <a name="remarks"></a>Poznámky

Členská funkce *loc* zkopíruje `locale` loc do uloženého objektu a `locale` vrátí kopii předchozí hodnoty uloženého objektu.

## <a name="regex_traitsisctype"></a><a name="isctype"></a>regex_traits::isctype

Testy pro členství ve třídě.

```cpp
bool isctype(char_type ch, char_class_type cls) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek k testování.

*Cls*\
Třídy, které mají být testovány.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu true pouze v případě, že znak *ch* je ve třídě znaků určené *cls*.

## <a name="regex_traitslength"></a><a name="length"></a>regex_traits::délka

Vrátí délku sekvence ukončené hodnotou null.

```cpp
static size_type length(const char_type *str);
```

### <a name="parameters"></a>Parametry

*Str*\
Sekvence ukončená hodnotou null.

### <a name="remarks"></a>Poznámky

Vrátí statickou `std::char_traits<char_type>::length(str)`členská funkce .

## <a name="regex_traitslocale_type"></a><a name="locale_type"></a>regex_traits::locale_type

Typ uloženého objektu národního prostředí.

```cpp
typedef T7 locale_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro typ, který zapouzdřuje národní prostředí. V `regex_traits<char>` specializacích `regex_traits<wchar_t>` a je `std::locale`synonymem pro .

## <a name="regex_traitslookup_classname"></a><a name="lookup_classname"></a>regex_traits::lookup_classname

Mapuje sekvenci na třídu znaků.

```cpp
template <class FwdIt>
char_class_type lookup_classname(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Začátek sekvence se podívat nahoru.

*Poslední*\
Konec sekvence se podívat nahoru.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu, která označuje třídu znaků pojmenovanou posloupností znaků, na kterou se pozařují její argumenty. Hodnota nezávisí na případě znaků v sekvenci.

`regex_traits<char>` Specializace rozpozná názvy `"d"` `"s"`, `"w"` `"alnum"`, `"alpha"` `"blank"`, `"cntrl"` `"digit"`, `"graph"` `"lower"`, `"print"` `"punct"`, `"space"` `"upper"`, `"xdigit"`, , , , , , a , a , vše bez ohledu na případ.

`regex_traits<wchar_t>` Specializace rozpozná názvy `L"d"` `L"s"`, `L"w"` `L"alnum"`, `L"alpha"` `L"blank"`, `L"cntrl"` `L"digit"`, `L"graph"` `L"lower"`, `L"print"` `L"punct"`, `L"space"` `L"upper"`, `L"xdigit"`, , , , , , a , a , vše bez ohledu na případ.

## <a name="regex_traitslookup_collatename"></a><a name="lookup_collatename"></a>regex_traits::lookup_collatename

Mapuje sekvenci na kompletující prvek.

```cpp
template <class FwdIt>
string_type lookup_collatename(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Začátek sekvence se podívat nahoru.

*Poslední*\
Konec sekvence se podívat nahoru.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí objekt řetězce obsahující kompletační prvek `[first, last)`odpovídající sekvenci nebo prázdný řetězec, pokud sekvence není platným kompletujícím prvkem.

## <a name="regex_traitsregex_traits"></a><a name="regex_traits"></a>regex_traits::regex_traits

Vytvoří objekt.

```cpp
regex_traits();
```

### <a name="remarks"></a>Poznámky

Konstruktor vytvoří objekt, jehož uložený `locale` objekt je inicializován na výchozí národní prostředí.

## <a name="regex_traitssize_type"></a><a name="size_type"></a>regex_traits::size_type

Typ délky sekvence.

```cpp
typedef T6 size_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymum pro nepodepsaný integrální typ. V `regex_traits<char>` specializacích `regex_traits<wchar_t>` a je `std::size_t`synonymem pro .

Typedef je synonymem `std::size_t`pro .

## <a name="regex_traitsstring_type"></a><a name="string_type"></a>regex_traits::string_type

Typ řetězce prvků.

```cpp
typedef basic_string<Elem> string_type;
```

### <a name="remarks"></a>Poznámky

Typedef je synonymem `basic_string<Elem>`pro .

## <a name="regex_traitstransform"></a><a name="transform"></a>regex_traits::transformace

Převede na ekvivalentní seřazené pořadí.

```cpp
template <class FwdIt>
string_type transform(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Začátek sekvence transformace.

*Poslední*\
Konec sekvence transformace.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec, který generuje pomocí pravidla transformace, `locale` který závisí na uloženém objektu. Pro dvě znakové sekvence určené rozsahy `[first1, last1)` iterátoru a `[first2, last2)`, `transform(first1, last1) < transform(first2, last2)` pokud se znaková sekvence určená rozsahem `[first1, last1)` iterátoru seřadí před posloupnost znaků určenou rozsahem iterátoru `[first2, last2)`.

## <a name="regex_traitstransform_primary"></a><a name="transform_primary"></a>regex_traits::transform_primary

Převede na ekvivalentní sekvenci bez případu.

```cpp
template <class FwdIt>
string_type transform_primary(FwdIt first, FwdIt last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Začátek sekvence transformace.

*Poslední*\
Konec sekvence transformace.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec, který generuje pomocí pravidla transformace, `locale` který závisí na uloženém objektu. Pro dvě znakové sekvence určené rozsahy `[first1, last1)` iterátoru a `[first2, last2)`, `transform_primary(first1, last1) < transform_primary(first2, last2)` pokud se znaková sekvence určená rozsahem `[first1, last1)` iterátoru seřadí před posloupností znaků určenou rozsahem iterátoru `[first2, last2)` bez ohledu na případ nebo přízvuk.

## <a name="regex_traitstranslate"></a><a name="translate"></a>regex_traits::přeložit

Převede na ekvivalentní odpovídající prvek.

```cpp
char_type translate(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek převést.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí znak, který generuje pomocí pravidla transformace, `locale` který závisí na uloženém objektu. Pro `char_type` dva `ch1` `ch2`objekty `ch1` a `ch2` , `translate(ch1) == translate(ch2)` pouze pokud a by měla odpovídat, když jeden nastane v definici regulárního výrazu a druhý nastane na odpovídající pozici v cílové sekvenci pro shodu citlivou na národní prostředí.

## <a name="regex_traitstranslate_nocase"></a><a name="translate_nocase"></a>regex_traits::translate_nocase

Převede na ekvivalentní prvek bez případu odpovídající.

```cpp
char_type translate_nocase(char_type ch) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek převést.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí znak, který generuje pomocí pravidla transformace, `locale` který závisí na uloženém objektu. Pro `char_type` dva `ch1` `ch2`objekty `ch1` a `ch2` , `translate_nocase(ch1) == translate_nocase(ch2)` pouze pokud a by měla odpovídat, když jeden nastane v definici regulárního výrazu a druhý nastane na odpovídající pozici v cílové sekvenci pro případ nerozlišující shody.

## <a name="regex_traitsvalue"></a><a name="value"></a>regex_traits::hodnota

Převede prvek na hodnotu číslice.

```cpp
int value(Elem ch, int radix) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Prvek převést.

*Radix*\
Aritmetické základny k použití.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí hodnotu reprezentovanou znakem *ch* v základním *radixu*nebo -1, pokud *ch* není platnou číslicí v základním *radixu*. Funkce bude volána pouze s *argumentem radix* 8, 10 nebo 16.

## <a name="see-also"></a>Viz také

[\<regulární>](../standard-library/regex.md)\
[regex_constants třída](../standard-library/regex-constants-class.md)\
[regex_error třída](../standard-library/regex-error-class.md)\
[\<funkce> regulárních výrazů](../standard-library/regex-functions.md)\
[regex_iterator třída](../standard-library/regex-iterator-class.md)\
[\<operátory> regulárních výrazů](../standard-library/regex-operators.md)\
[regex_token_iterator třída](../standard-library/regex-token-iterator-class.md)\
[\<regulární> typedefs](../standard-library/regex-typedefs.md)\
[regex_traits\<char> třídy](../standard-library/regex-traits-char-class.md)\
[>\<wchar_t> regex_traits>](../standard-library/regex-traits-wchar-t-class.md)
