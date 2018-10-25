---
title: money_put – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_put
- xlocmon/std::money_put::char_type
- xlocmon/std::money_put::iter_type
- xlocmon/std::money_put::string_type
- xlocmon/std::money_put::do_put
- xlocmon/std::money_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::money_put [C++]
- std::money_put [C++], char_type
- std::money_put [C++], iter_type
- std::money_put [C++], string_type
- std::money_put [C++], do_put
- std::money_put [C++], put
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6163e3db11da717eaf188b4b2f585f78d7eb511
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50073367"
---
# <a name="moneyput-class"></a>money_put – třída

Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů finančních hodnot na sekvence typu `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class money_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*OutputIterator*<br/>
Typ iterátoru, do kterého finanční funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[money_put](#money_put)|Konstruktor pro objekty typu `money_put`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|
|[STRING_TYPE](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce volaná k převodu buď čísla, nebo řetězce na sekvenci znaků, která představuje finanční hodnotu.|
|[Vložit](#put)|Převede buď číslo, nebo řetězec na sekvenci znaků, která představuje finanční hodnotu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="char_type"></a>  money_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="do_put"></a>  money_put::do_put

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

*next*<br/>
Iterátor adresující první prvek vložený řetězec.

*_Intl*<br/>
Logická hodnota označující typ symbolu měny očekávání v pořadí: **true** pokud mezinárodní **false** Pokud domácí.

*_Iosbase*<br/>
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinné

*_Fill*<br/>
Znak, který se používá k vytvoření mezer.

*Val*<br/>
Objekt string má být převeden.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy jedna pozice za posledním prvkem, který vytváří.

### <a name="remarks"></a>Poznámky

První chráněná virtuální členská funkce generuje sekvenční prvky počínaje *Další* vytvoří pole peněžní výstup z [string_type](#string_type) objekt *val*. Sekvence řízenou parametrem *val* musí začínat jeden nebo více desítkových číslic, může volitelně předcházet mínus (-), který představuje částku. Vrátí iterátor určení prvního prvku mimo peněžní generovaný pole.

Druhá chráněná virtuální členská funkce se chová stejně jako první, s výjimkou, že první efektivně převede *val* na posloupnost desítková číslice, může volitelně předcházet znaménko minus potom převede tento pořadí, jak je uvedeno výše.

Formát pole peněžní výstupu je určeno [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class) fac vrácený voláním (skutečná) [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**>> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)).

Konkrétně:

- **FAC**. [pos_format –](../standard-library/moneypunct-class.md#pos_format) určuje pořadí, ve kterém se generují komponenty pole pro nezápornou hodnotu.

- **FAC**. [neg_format –](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve kterém se generují komponenty pole pro záporné hodnoty.

- **FAC**. [curr_symbol –](../standard-library/moneypunct-class.md#curr_symbol) určuje pořadí prvků, které se generují jako symbol měny.

- **FAC**. [positive_sign –](../standard-library/moneypunct-class.md#positive_sign) určuje pořadí prvků, které se generují pro kladné znaménko.

- **FAC**. [negative_sign –](../standard-library/moneypunct-class.md#negative_sign) určuje pořadí prvků, které se generují pro záporné znaménko.

- **FAC**. [seskupení](../standard-library/moneypunct-class.md#grouping) určuje způsob seskupení číslic vlevo od desetinné čárky.

- **FAC**. [thousands_sep –](../standard-library/moneypunct-class.md#thousands_sep) určuje prvek, který odděluje skupin číslic nalevo od desetinné čárky.

- **FAC**. [decimal_point –](../standard-library/moneypunct-class.md#decimal_point) určuje prvek, který odděluje celá čísla od žádné číslice zlomku.

- **FAC**. [frac_digits –](../standard-library/moneypunct-class.md#frac_digits) určuje počet významných zlomek číslic vpravo od každé desetinné čárky.

Pokud řetězec znak ( **fac**. `negative_sign` nebo **fac**. `positive_sign`) má více než jeden element, pouze první prvek je generována pokud element rovna **money_base::sign** se zobrazí v vzorek formátu ( **fac**. `neg_format` nebo **fac**. `pos_format`). Na konci peněžní výstupního pole jsou generovány všechny zbývající prvky.

Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) nenulové, řetězec **fac**. `curr_symbol` kde se generuje prvek s hodnotou **money_base::symbol** se zobrazí ve formátu vzoru. V opačném případě je generována bez symbolu měny.

Pokud technologie se nevyžaduje žádná omezení seskupení **fac**. **seskupení** (jeho prvního prvku má hodnotu CHAR_MAX), pak žádné instance **fac**. `thousands_sep` jsou generovány v části peněžní výstupního pole pro hodnotu (kde element rovna **money_base::value** se zobrazí v vzorek formátu). Pokud **fac**. `frac_digits` je nula, neuvidí žádný výskyt **fac**. `decimal_point` je generován poté desítkových číslic. V opačném případě umístí výsledný peněžní výstupního pole nižšího řádu **fac**. `frac_digits` desítkových číslic vpravo od desetinné čárky.

Jako u jakékoli výstup číselné pole, s výjimkou, že pokud dojde k odsazení **iosbase**. **příznaky** & **iosbase**. [interní](../standard-library/ios-functions.md#internal) je nenulová, všechny vnitřní odsazení generováno kde element rovna **money_base::space** se zobrazí ve formátu vzoru, pokud se zobrazí. Vnitřní odsazení v opačném případě dojde před generovaný sekvenční. Odsazení znaku je **výplně**.

Volání funkcí **iosbase**. **Šířka**(0) k resetování šířku pole na hodnotu nula.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [umístit](#put), kde je virtuální členská funkce volána **umístit**.

## <a name="iter_type"></a>  money_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **OutputIterator.**

## <a name="money_put"></a>  money_put::money_put

Konstruktor pro objekty typu `money_put`.

```cpp
explicit money_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Celočíselná hodnota určuje typ Správa paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* parametrů a jejich význam:

- 0: Životnost objektu se spravuje přes národní prostředí, které je obsahují.

- 1: doba života objektu je nutné ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je to možné, protože destruktor je chráněn.

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="put"></a>  money_put::Put

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

*next*<br/>
Iterátor adresující první prvek vložený řetězec.

*_Intl*<br/>
Logická hodnota označující typ symbolu měny očekávání v pořadí: **true** pokud mezinárodní **false** Pokud domácí.

*_Iosbase*<br/>
Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinné

*_Fill*<br/>
Znak, který se používá k vytvoření mezer.

*Val*<br/>
Objekt string má být převeden.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy jedna pozice za posledním prvkem, který vytváří.

### <a name="remarks"></a>Poznámky

Obě členské funkce vrátí [do_put –](#do_put)( `next`, `_Intl`, `_Iosbase`, `_Fill`, `val`).

### <a name="example"></a>Příklad

```cpp
// money_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
//   locale loc( "german_germany" );
   locale loc( "english_canada" );
   basic_stringstream<char> psz, psz2;
   ios_base::iostate st = 0;

   psz2.imbue( loc );
   psz2.flags( psz2.flags( )|ios_base::showbase ); // force the printing of the currency symbol
   use_facet < money_put < char > >(loc).put(basic_ostream<char>::_Iter( psz2.rdbuf( ) ), true, psz2, st, 100012);
   if (st & ios_base::failbit)
      cout << "money_put( ) FAILED" << endl;
   else
      cout << "money_put( ) = \"" << psz2.rdbuf( )->str( ) <<"\""<< endl;

   st = 0;
};
```

```Output
money_put( ) = "CAD1,000.12"
```

## <a name="string_type"></a>  money_put::STRING_TYPE

Typ, který popisuje řetězec obsahující znaky typu `CharType`.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [basic_string](../standard-library/basic-string-class.md) jejíž objekty mohou ukládat sekvencí ze zdrojové sekvence prvků.

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[facet – třída](../standard-library/locale-class.md#facet_class)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
