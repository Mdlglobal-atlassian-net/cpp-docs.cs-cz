---
title: money_put – třída
ms.date: 11/01/2018
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
ms.openlocfilehash: 035cc4e7b9cfac262979509bf7b4570e2c55336c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377431"
---
# <a name="money_put-class"></a>money_put – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí `CharType`pro řízení převodů peněžních hodnot na sekvence typu .

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*Výstupní iterátor*\
Typ iterátoru, do kterého finanční funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[money_put](#money_put)|Konstruktor pro objekty `money_put`typu .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky `CharType`typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce volaná k převodu buď čísla, nebo řetězce na sekvenci znaků, která představuje finanční hodnotu.|
|[Dát](#put)|Převede buď číslo, nebo řetězec na sekvenci znaků, která představuje finanční hodnotu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="money_putchar_type"></a><a name="char_type"></a>money_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **CharType**.

## <a name="money_putdo_put"></a><a name="do_put"></a>money_put::do_put

Virtuální funkce volaná k převodu buď čísla, nebo řetězce na sekvenci znaků, která představuje finanční hodnotu.

```cpp
virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

virtual iter_type do_put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parametry

*Další*\
Iterátor adresování první prvek vloženého řetězce.

*_Intl*\
Logická hodnota označující typ symbolu měny očekávanév pořadí: **true** if international, **false** if domestic.

*_Iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je nutné

*_Fill*\
Znak, který se používá pro mezery.

*Val*\
Objekt řetězce, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy pozici jeden za poslední prvek vyrobené.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce generuje sekvenční prvky začínající *vedle* vytvoření měnového výstupního pole z [string_type](#string_type) *objektu val*. Sekvence řízená *val* musí začínat jednou nebo více desetinnými číslicemi, které volitelně předchází znaménko mínus (-), které představuje částku. Funkce vrátí iterátor označující první prvek za generované měnové výstupní pole.

Druhá virtuální chráněná členská funkce se chová stejně jako první, s tím rozdílem, že nejprve nejprve převede *val* na posloupnost desetinných míst, volitelně předchází znaménko mínus, pak převede tuto sekvenci, jak je uvedeno výše.

Formát pole měnového výstupu je určen [fac národního prostředí](../standard-library/locale-class.md#facet_class) , který je vrácen (efektivním) voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

Konkrétně:

- **fac**. [pos_format](../standard-library/moneypunct-class.md#pos_format) určuje pořadí, ve kterém jsou komponenty pole generovány pro nezápornou hodnotu.

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve kterém jsou komponenty pole generovány pro zápornou hodnotu.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) určuje posloupnost prvků, které mají být generovány pro symbol měny.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) určuje posloupnost prvků generovat pro kladné znaménko.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) určuje posloupnost prvků, které mají být generovány pro záporné znaménko.

- **fac**. [seskupení](../standard-library/moneypunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od jakékoli desetinné čárky.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) určuje prvek, který odděluje skupiny číslic nalevo od jakékoli desetinné čárky.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) určuje prvek, který odděluje celé číslice od všech zlomků číslic.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) určuje počet číslic významného zlomku vpravo od jakékoli desetinné čárky.

Pokud znakový řetězec ( **fac**. `negative_sign`nebo **fac**. `positive_sign`) má více než jeden prvek, pouze první prvek je generován, kde se prvek rovný **money_base::sign** zobrazí ve vzoru formátu ( **fac**. `neg_format`nebo **fac**. `pos_format`). Všechny zbývající prvky jsou generovány na konci pole měnového výstupu.

Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) je nenulová, řetězec **fac**. `curr_symbol`je generován, kde se ve vzorovém formátu zobrazí prvek rovný **money_base::symbol.** V opačném případě není generován žádný symbol měny.

Pokud **fac**neukládají žádná omezení seskupení . **seskupení** (jeho první prvek má hodnotu CHAR_MAX), pak žádné instance **fac**. `thousands_sep`jsou generovány v hodnotové části pole peněžního výstupu (kde se prvek rovný **money_base::hodnota** zobrazí ve formátu vzoru). Pokud **fac**. `frac_digits`je nula, pak žádná instance **fac**. `decimal_point`je generována za desetinnými číslicemi. V opačném případě výsledné pole peněžního výstupu umístí **fac**nižšího řádu . `frac_digits`desetinná místa napravo od desetinné čárky.

K odsazení dochází jako u libovolného číselného výstupního pole s tím rozdílem, že pokud **iosbase**. **příznaky** & **iosbase**. [vnitřní](../standard-library/ios-functions.md#internal) je nenulová, je generováno jakékoli vnitřní odsazení, kde se prvek rovný **money_base::space** zobrazí ve vzoru formátu, pokud se zobrazí. V opačném případě dojde k interní odsazení před generované sekvence. Znak odsazení je **výplň**.

Funkce volá **iosbase**. **šířku**(0) pro obnovení šířky pole na nulu.

### <a name="example"></a>Příklad

Viz příklad pro [put](#put), kde je virtuální členská funkce volána **put**.

## <a name="money_putiter_type"></a><a name="iter_type"></a>money_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **OutputIterator.**

## <a name="money_putmoney_put"></a><a name="money_put"></a>money_put::money_put

Konstruktor pro objekty `money_put`typu .

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* a jejich význam jsou:

- 0: životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: životnost objektu musí být spravována ručně.

- \>1: tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože destruktor je chráněn.

Konstruktor inicializuje svůj základní objekt pomocí **národního prostředí::**[omezující stolku](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="money_putput"></a><a name="put"></a>money_put::put

Převede buď číslo, nebo řetězec na sekvenci znaků, která představuje finanční hodnotu.

```cpp
iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    const string_type& val) const;

iter_type put(
    iter_type next,
    bool _Intl,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

### <a name="parameters"></a>Parametry

*Další*\
Iterátor adresování první prvek vloženého řetězce.

*_Intl*\
Logická hodnota označující typ symbolu měny očekávanév pořadí: **true** if international, **false** if domestic.

*_Iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je nutné

*_Fill*\
Znak, který se používá pro mezery.

*Val*\
Objekt řetězce, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy pozici jeden za poslední prvek vyrobené.

### <a name="remarks"></a>Poznámky

Obě členské funkce `next`vrátí `_Intl` `_Iosbase`do_put `_Fill` `val`( , , , ). [do_put](#do_put)

### <a name="example"></a>Příklad

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

int main()
{
    std::locale loc( "german_germany" );
    std::basic_stringstream<char> psz;

    psz.imbue(loc);
    psz.flags(psz.flags() | std::ios_base::showbase); // force the printing of the currency symbol
    std::use_facet<std::money_put<char> >(loc).put(std::basic_ostream<char>::_Iter(psz.rdbuf()), true, psz, ' ', 100012);
    if (psz.fail())
        std::cout << "money_put() FAILED" << std::endl;
    else
        std::cout << "money_put() = \"" << psz.rdbuf()->str() << "\"" << std::endl;
}
```

```Output
money_put() = "EUR1.000,12"
```

## <a name="money_putstring_type"></a><a name="string_type"></a>money_put::string_type

Typ, který popisuje řetězec obsahující znaky `CharType`typu .

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) jehož objekty mohou ukládat sekvence prvků ze zdrojové sekvence.

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[fazeta třídy](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
