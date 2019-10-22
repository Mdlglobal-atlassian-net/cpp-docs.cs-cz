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
ms.openlocfilehash: aafa6f9498ee315c25e73833baf3c13d99d36743
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689306"
---
# <a name="money_put-class"></a>money_put – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu peněžních hodnot na sekvence typu `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType* \
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*OutputIterator* \
Typ iterátoru, do kterého finanční funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[money_put](#money_put)|Konstruktor pro objekty typu `money_put`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce volaná k převodu buď čísla, nebo řetězce na sekvenci znaků, která představuje finanční hodnotu.|
|[převést](#put)|Převede buď číslo, nebo řetězec na sekvenci znaků, která představuje finanční hodnotu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="char_type"></a>money_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="do_put"></a>money_put::d o_put

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

*další* \
Iterátor adresující první prvek vloženého řetězce.

*_Intl* \
Logická hodnota označující typ symbolu měny očekávaný v sekvenci: **true** , pokud mezinárodní, **false** , pokud je tuzemsko.

*_Iosbase* \
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

*_Fill* \
Znak, který se používá pro mezery.

\ *Val*
Objekt String, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění, které je umístěno na jednom za posledním vytvořeným prvkem.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce vytvoří sekvenční prvky začínající na *Další* pro vytvoření pole peněžního výstupu z [string_type](#string_type) objektu *Val*. Sekvence řízená pomocí *Val* musí začínat jednou nebo více desítkovými číslicemi, volitelně předcházet znaménkem mínus (-), které představuje množství. Funkce vrátí iterátor, který určuje první prvek za generovaným polem s peněžním výstupem.

Druhá funkce Virtual Protected member se chová stejně jako první, s tím rozdílem, že efektivně nejprve převede hodnotu *Val* na posloupnost desítkových číslic, volitelně předchází znaménkem mínus a následně převádí tuto sekvenci nahoru.

Formát pole s peněžním výstupem je určen FAC [vlastnostmi národního prostředí](../standard-library/locale-class.md#facet_class) vráceným (platným) voláním [use_facet](../standard-library/locale-functions.md#use_facet)  < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **mezinárodní**> > ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

Určen

- **FAC**. [pos_format](../standard-library/moneypunct-class.md#pos_format) určuje pořadí, ve kterém jsou komponenty pole generovány pro nezáporné hodnoty.

- **FAC**. [neg_format](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve kterém jsou komponenty pole generovány pro zápornou hodnotu.

- **FAC**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) určuje posloupnost prvků, které mají být generovány pro symbol měny.

- **FAC**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) Určuje sekvenci prvků, které mají být generovány pro kladné znaménko.

- **FAC**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) Určuje sekvenci prvků, které mají být generovány pro záporné znaménko.

- **FAC**. [seskupení](../standard-library/moneypunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

- **FAC**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) určuje prvek, který odděluje skupiny číslic nalevo od libovolné desetinné čárky.

- **FAC**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) určuje prvek, který odděluje celočíselné číslice od číslic zlomků.

- **FAC**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) určuje počet významných číslic zlomku napravo od desetinné čárky.

Pokud se podepisuje řetězec ( **FAC**. `negative_sign` nebo **FAC**. `positive_sign`) obsahuje více než jeden prvek, je vygenerován pouze první prvek, kde se element ve vzoru Format ( **FAC**) zobrazí v elementu, který se rovná **money_base:: Sign** . `neg_format` nebo **FAC**. `pos_format`). Všechny zbývající prvky jsou generovány na konci pole s peněžním výstupem.

IF **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags)  & [showbase](../standard-library/ios-functions.md#showbase) jsou nenulové, řetězec **FAC**. `curr_symbol` je vygenerováno, kde se ve vzoru formátu zobrazí element, který se rovná **money_base:: symbol** . V opačném případě se negeneruje žádný symbol měny.

Pokud **FAC**žádné omezení seskupení neukládá. **seskupení** (jeho první prvek má hodnotu CHAR_MAX), pak žádné instance **FAC**. `thousands_sep` jsou generovány v hodnotě pole s peněžním výstupem (kde se element rovnají **money_base:: Value** ve vzoru formátu). IF **FAC**. `frac_digits` je nula, pak žádná instance třídy **FAC**. `decimal_point` se vygeneruje za desítkovou číslicí. V opačném případě výsledné pole s peněžním výstupem umístí **FAC**na nižší objednávku. `frac_digits` desítkové číslice napravo od desetinné čárky.

K odsazení dochází jako pro jakékoliv číselné pole Output, s výjimkou případů, kdy je **iosbase**. **příznaky**  & **iosbase**. [interní](../standard-library/ios-functions.md#internal) je nenulový, jakékoli vnitřní odsazení je vygenerováno, kde se element, který se rovná **money_base:: Space** , se zobrazí ve vzoru formátu, pokud se zobrazí. V opačném případě dojde k vnitřnímu odsazení před vygenerovanou sekvencí. Znak odsazení je **Fill**.

Funkce volá **iosbase**. **Width**(0) pro obnovení šířky pole na nulu

### <a name="example"></a>Příklad

Podívejte se na příklad pro [vložení](#put), kde je virtuální členská funkce volána funkcí **Put**.

## <a name="iter_type"></a>money_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **OutputIterator.**

## <a name="money_put"></a>money_put::money_put

Konstruktor pro objekty typu `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* \
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože je destruktor chráněný.

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="put"></a>money_put::p UT

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

*další* \
Iterátor adresující první prvek vloženého řetězce.

*_Intl* \
Logická hodnota označující typ symbolu měny očekávaný v sekvenci: **true** , pokud mezinárodní, **false** , pokud je tuzemsko.

*_Iosbase* \
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

*_Fill* \
Znak, který se používá pro mezery.

\ *Val*
Objekt String, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění, které je umístěno na jednom za posledním vytvořeným prvkem.

### <a name="remarks"></a>Poznámky

Oba členské funkce vrací [do_put](#do_put)(`next`, `_Intl`, `_Iosbase`, `_Fill`, `val`).

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

## <a name="string_type"></a>money_put::string_type

Typ, který popisuje řetězec obsahující znaky typu `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) , jejíž objekty mohou ukládat sekvence prvků ze zdrojové sekvence.

## <a name="see-also"></a>Viz také:

[\<locale >](../standard-library/locale.md) \
\ [třídy omezující vlastnosti](../standard-library/locale-class.md#facet_class)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
