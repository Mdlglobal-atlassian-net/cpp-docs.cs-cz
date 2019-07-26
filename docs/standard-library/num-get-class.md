---
title: num_get – třída
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 67aef1ce52b6717ce6d6381429982cf660aa5e20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457644"
---
# <a name="numget-class"></a>num_get – třída

Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů sekvencí typu `CharType` na číselné hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*InputIterator*\
Typ iterátoru, ze kterého číselné funkce get čtou svůj vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[num_get](#num_get)|Konstruktor pro objekty typu `num_get` , které slouží k extrakci číselných hodnot ze sekvencí.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje vstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_get](#do_get)|Virtuální funkce volaná k extrakci číselné hodnoty nebo logické hodnoty ze sekvence znaků.|
|[get](#get)|Extrahuje ze sekvence znaků číselnou nebo logickou hodnotu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="char_type"></a>num_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="do_get"></a>num_get::d o_get

Virtuální funkce volaná k extrakci číselné hodnoty nebo logické hodnoty ze sekvence znaků.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

### <a name="parameters"></a>Parametry

*první*\
Začátek rozsahu znaků, ze kterého má být číslo čteno.

*posledního*\
Konec rozsahu znaků, ze kterého má být číslo čteno.

*_Iosbase*\
[Ios_base](../standard-library/ios-base-class.md) , jehož příznaky jsou používány převodem.

*_State*\
Stav, ke kterému se failbit (viz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)), se přidá při selhání.

*počítává*\
Hodnota, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor po načtení hodnoty.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```

odpovídá sekvenčním prvkům  začínajícím v první `[first, last)` v sekvenci, dokud nerozpozná celé, neprázdné pole Input Integer. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu jako typ **Long**a výsledek uloží do hodnoty *Val*. Vrátí iterátor, který určuje první prvek nad číselným vstupním polem. V opačném případě funkce uloží nic  do hodnoty Val `ios_base::failbit` a `state`nastaví v. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného celočíselného pole. V obou případech, pokud se návratová hodnota rovná `last`, funkce nastaví `ios_base::eofbit` v `state`.

Pole typu celé číslo je převedeno pomocí stejných pravidel používaných funkcemi kontroly pro porovnání a převod řady prvků typu **char** ze souboru. (Každý takový element **char** se předpokládá, že se mapuje na ekvivalentní element typu `Elem` jednoduchým a 1:1m mapováním.) Ekvivalentní specifikace převodu vyhledávání se určuje takto:

IF `iosbase.` [ios_base:: Flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`– specifikace převodu je.[](../standard-library/ios-functions.md#oct) `lo`

Pokud `iosbase.flags() & ios_base::basefield == ios_base::`je [hex](../standard-library/ios-functions.md#hex), je `lx`specifikace převodu.

Pokud `iosbase.flags() & ios_base::basefield == 0` je`li`specifikace převodu.

V opačném případě je `ld`specifikace převodu.

`fac` Formát pole pro zadání celého čísla je dále určen [omezující vlastností národního prostředí](../standard-library/locale-class.md#facet_class) vrácenou voláním [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base:: getloc](../standard-library/ios-base-class.md#getloc)`())`. Určen

`fac.`[numpunct:: Grouping](../standard-library/numpunct-class.md#grouping) `()` určuje, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

`fac.`[numpunct:: thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` Určuje sekvenci, která odděluje skupiny číslic nalevo od libovolné desetinné čárky.

Pokud se žádné instance `fac.thousands_sep()` nevyskytují v poli číselného vstupu, není uloženo žádné omezení seskupení. Jinak dojde k vynucení všech omezení `fac.grouping()` seskupení, která jsou vynucená, a před převodem vyhledávání se odeberou oddělovače.

Čtvrtá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci `ld` převodu s. `lu` V případě úspěchu převede číselné vstupní pole na hodnotu typu **bez znaménka Long** a uloží tuto hodnotu v *Val*.

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci `ld` převodu s. `lld` V případě úspěchu převede číselné vstupní pole na hodnotu typu **Long Long** a uloží tuto hodnotu do hodnoty *Val*.

Šestá virtuální členská funkce Protected:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci `ld` převodu s. `llu` V případě úspěchu převede číselné vstupní pole na hodnotu typu **bez znaménka Long Long** a uloží tuto hodnotu v *Val*.

Sedmá virtuální funkce chráněná členem:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```

se chová stejně jako první, s tím rozdílem, že budoucna odpovídá celému vstupnímu poli s plovoucí desetinnou čárkou (Neprázdné). `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` Určuje sekvenci, která odděluje celočíselné číslice od číslic zlomku. Ekvivalentní specifikátor převodu vyhledávání je `lf`.

Osmá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

se chová stejně jako první, s tím rozdílem, že budoucna odpovídá celému vstupnímu poli s plovoucí desetinnou čárkou (Neprázdné). `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point) `()` Určuje sekvenci, která odděluje celočíselné číslice od číslic zlomku. Ekvivalentní specifikátor převodu vyhledávání je `lf`.

Devátá funkce virtuální chráněné členské funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

se chová stejně jako osmá, s tím rozdílem, že ekvivalentní specifikátor převodu vyhledávání `Lf`je.

Desátá členská funkce Protected:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

se chová stejně jako první, s tím rozdílem, že ekvivalentní specifikátor převodu `p`vyhledávání je.

Poslední (jedenáctá) virtuální funkce chráněná členem:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

se chová stejně jako první, s tím rozdílem, že budoucna odpovídá celému neprázdnému vstupnímu poli logických hodnot. V případě úspěchu převede vstupní pole Boolean na hodnotu typu **bool** a uloží tuto hodnotu do hodnoty *Val*.

Logické vstupní pole má jednu ze dvou forem. Pokud `iosbase.flags() & ios_base::`je [boolalpha](../standard-library/ios-functions.md#boolalpha) false, je stejný jako pole typu Integer, s tím rozdílem, že převedená hodnota musí být 0 (pro false) nebo 1 (pro true). V opačném případě musí sekvence odpovídat `fac.`buď`()` [numpunct:: false](../standard-library/numpunct-class.md#falsename) (pro false)`()` , nebo `fac.` [numpunct:: true](../standard-library/numpunct-class.md#truename) (pro true).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Get](#get), kde je virtuální členská funkce volána `do_get`nástrojem.

## <a name="get"></a>num_get:: Get

Extrahuje ze sekvence znaků číselnou nebo logickou hodnotu.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

### <a name="parameters"></a>Parametry

*první*\
Začátek rozsahu znaků, ze kterého má být číslo čteno.

*posledního*\
Konec rozsahu znaků, ze kterého má být číslo čteno.

*_Iosbase*\
[Ios_base](../standard-library/ios-base-class.md) , jehož příznaky jsou používány převodem.

*_State*\
Stav, ke kterému se failbit (viz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)), se přidá při selhání.

*počítává*\
Hodnota, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor po načtení hodnoty.

### <a name="remarks"></a>Poznámky

Všechny členské funkce vracejí [do_get](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).

První virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající první v sekvenci [ `first`, `last`), dokud nerozpozná celé neprázdné pole Input Integer. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu jako typ **Long** a výsledek uloží do hodnoty *Val*. Vrátí iterátor, který určuje první prvek nad číselným vstupním polem. V opačném případě funkce uloží nic  do hodnoty Val `ios_base::failbit` a nastaví ve *stavu*_. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného celočíselného pole. V obou případech, Pokud vrácená hodnota se rovná *Last*, funkce nastaví `ios_base::eofbit` v *_State*.

Pole typu celé číslo je převedeno pomocí stejných pravidel používaných funkcemi kontroly pro porovnání a převod řady prvků typu **char** ze souboru. U každého takového elementu **char** se předpokládá mapování na ekvivalentní prvek typu `CharType` jednoduchým mapováním 1:1. Ekvivalentní specifikace převodu vyhledávání se určuje takto:

- If `iosbase`. [Flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield`,specifikace[](../standard-library/ios-functions.md#oct)převodu je .`lo` == `ios_base::`

- Pokud **iosbase. Flags** & **ios_base:: basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), je `lx`specifikace převodu.

- Pokud **iosbase. Flags** & **ios_base:: basefield** = = 0, je `li`specifikace převodu.

- V opačném případě je `ld`specifikace převodu.

Formát pole pro celočíselné zadání je dále určen**FAC** omezujícími [vlastnostmi národního prostředí](../standard-library/locale-class.md#facet_class)vráceným voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md) \< **elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Určen

- **FAC**. [seskupení](../standard-library/numpunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

- **FAC**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) Určuje sekvenci, která odděluje skupiny číslic nalevo od libovolné desetinné čárky.

Nejsou-li žádné instance **FAC**. `thousands_sep`k dispozici v číselném poli input není uloženo žádné omezení seskupování. V opačném případě jakákoli omezení seskupení zavedená **FAC**. **seskupení** je vynutilo a před převodem vyhledávání dojde k odebrání oddělovačů.

Druhá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci `ld` převodu s. `lu` V případě úspěchu převede pole číselného vstupu na hodnotu typu **bez znaménka Long** a uloží tuto hodnotu v *Val*.

Třetí funkce virtuální chráněné členské funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

se chová stejně jako první, s tím rozdílem, že se pokusí vyhledat celé neprázdné vstupní pole s plovoucí desetinnou čárkou. **FAC**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) Určuje sekvenci, která odděluje celočíselné číslice od číslic zlomku. Ekvivalentní specifikátor převodu vyhledávání je `lf`.

Čtvrtá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

se chová stejně jako třetí, s tím rozdílem, že ekvivalentní specifikátor převodu `Lf`vyhledávání je.

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

se chová stejně jako první, s tím rozdílem, že ekvivalentní specifikátor převodu `p`vyhledávání je.

Šestá virtuální členská funkce Protected:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

se chová stejně jako první, s tím rozdílem, že se pokusí porovnat celé neprázdné logické vstupní pole. V případě úspěchu převede vstupní pole Boolean na hodnotu typu **bool** a uloží tuto hodnotu do hodnoty *Val*.

Logické vstupní pole má jednu ze dvou forem. IF **iosbase**. **příznaky**   [](../standard-library/ios-functions.md#boolalpha) boolalpha je false, je stejné jako pole typu Integer, s tím rozdílem, že převedená hodnota musí být 0 (pro false) nebo 1 (pro true). & `ios_base::` V opačném případě musí sekvence odpovídat buď **FAC**. [hodnota false](../standard-library/numpunct-class.md#falsename) (pro **false**) nebo **FAC**. [hodnota true](../standard-library/numpunct-class.md#truename) (pro **true**).

### <a name="example"></a>Příklad

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="iter_type"></a>num_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `InputIterator`šablony.

## <a name="num_get"></a>num_get::num_get

Konstruktor pro objekty typu `num_get` , které slouží k extrakci číselných hodnot ze sekvencí.

```cpp
explicit num_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, která jej obsahují.

- 1: Životnost objektu musí být ručně spravovaná.

- \> 1: Tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože je destruktor chráněný.

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="see-also"></a>Viz také:

[\<> národního prostředí](../standard-library/locale.md)\
[Face – třída](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
