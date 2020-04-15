---
title: num_put – třída
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: 3f65d7140bb5c691fa58ec9d74ceda5573280ddb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373650"
---
# <a name="num_put-class"></a>num_put – třída

Šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost národního `CharType`prostředí pro řízení převodů číselných hodnot na sekvence typu .

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*Výstupní iterátor*\
Typ iterátoru, do kterého číselné funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[num_put](#num_put)|Konstruktor pro objekty `num_put`typu .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce, která je volána převést `CharType`číslo do posloupnosti s, která představuje číslo formátované pro dané národní prostředí.|
|[Dát](#put)|Převede číslo na posloupnost `CharType`s, která představuje číslo formátované pro dané národní prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="num_putchar_type"></a><a name="char_type"></a>num_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `CharType`parametr šablony .

## <a name="num_putdo_put"></a><a name="do_put"></a>num_put::do_put

Virtuální funkce, která je volána převést `CharType`číslo do posloupnosti s, která představuje číslo formátované pro dané národní prostředí.

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>Parametry

*Další*\
Iterátor adresování první prvek vloženého řetězce.

*_Iosbase*\
Zadali datový proud, který obsahuje národní prostředí s numpunct omezující plochu slouží k interpunkci výstupu a příznaky pro formátování výstupu.

*_Fill*\
Znak, který se používá pro mezery.

*Val*\
Číslo nebo logický typ, který má být výstup.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy pozici jeden za poslední prvek vyrobené.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce generuje sekvenční prvky začínající *vedle* vytvoření celého výstupního pole z hodnoty *val*. Funkce vrátí iterátor určení další místo vložit prvek za generované celé číslo výstupní pole.

Celé výstupní pole je generováno stejnými pravidly používanými tiskovými funkcemi pro generování řady **znaků** do souboru. Předpokládá se, že každý takový znakový `CharType` prvek je mapován na ekvivalentní prvek typu jednoduchým mapováním 1:1. Pokud však funkce tisku vymaže pole s `do_put` mezerami nebo číslicí 0, místo toho použije `fill`. Ekvivalentní specifikace převodu tisku se stanoví takto:

- Pokud **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & příznaky ==  `lo`října , specifikace převodu je .[oct](../standard-library/ios-functions.md#oct)`ios_base::basefield``ios_base::`

- Pokud **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), `lx`specifikace převodu je .

- V opačném případě `ld`je specifikace převodu .

Pokud **iosbase**. [šířka](../standard-library/ios-base-class.md#width) je nenulová, je předřazena šířka pole této hodnoty. Funkce pak volá **iosbase**. **šířku**(0) pro obnovení šířky pole na nulu.

Odsazení dochází pouze v případě, že minimální počet prvků *N* potřebné k určení výstupní pole je menší než **iosbase**. [šířku](../standard-library/ios-base-class.md#width). Toto odsazení se skládá z posloupnosti kopií **výplně****šířky** *N* - . Odsazení pak dochází takto:

- Pokud **iosbase**. **flags** & příznaky ==  **-** vlevo , příznak je předřazený.[left](../standard-library/ios-functions.md#left)`ios_base::adjustfield``ios_base::` (Odsazení dojde po vygenerovaném textu.)

- Pokud **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal), příznak **0** je předřazený. (Pro číselné výstupní pole dojde k odsazení, kde tiskové funkce podložka s 0.)

- V opačném případě není předřazena žádná další vlajka. (Před generovanou sekvencí dojde k odsazení.)

Konečně:

- Pokud **iosbase**. **flags** & příznaky`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) je nenulová, příznak **+** je předřazený ke specifikaci převodu.

- Pokud **iosbase**. **příznaky** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) je nenulová, příznak **#** je předřazený ke specifikaci převodu.

Formát celého výstupního pole je dále určen [fac patice národního prostředí,](../standard-library/locale-class.md#facet_class)**fac** která byla vrácena voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md) \< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Konkrétně:

- **fac**. [Seskupení](../standard-library/numpunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od jakékoli desetinné čárky

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) určuje sekvenci, která odděluje skupiny číslic nalevo od libovolné desetinné čárky.

Pokud **fac**neukládají žádná omezení seskupení . **seskupení** (jeho první prvek má hodnotu CHAR_MAX), pak žádné instance **fac**. `thousands_sep`jsou generovány ve výstupním poli. V opačném případě se po převodu tisku vloží oddělovače.

Druhá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

chová se stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lu`.

Třetí virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

chová se stejně jako první, s tím rozdílem, že vytváří výstupní pole s plovoucí desetinnou desetinnou desetinnou desetinnou hlavou z hodnoty **val**. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) určuje sekvenci, která odděluje celé číslice od dělicích čísel zlomků. Ekvivalentní specifikace převodu tisku se stanoví takto:

- Pokud **iosbase**. **příznaky** & `ios_base::floatfield` == `ios_base::`[opraveny](../standard-library/ios-functions.md#fixed), `lf`specifikace převodu je .

- Pokud **iosbase**. **příznaky** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific), `le`specifikace převodu je . Pokud **iosbase**. **flags** & příznaky`ios_base::`[velká písmena](../standard-library/ios-functions.md#uppercase) `e` je nenulová, je nahrazena `E`.

- V opačném případě je specifikace převodu **lg**. Pokud **iosbase**. **příznaky** & **ios_base::velká písmena** `g` je nenulová, je nahrazena . `G`

Pokud **iosbase**. **příznaky** & **ios_base::fixed** je nenulová nebo pokud **iosbase**. [přesnost](../standard-library/ios-base-class.md#precision) je větší než nula, přesnost s hodnotou **iosbase**. **přesnost** je předřazena specifikaci převodu. Jakékoli odsazení se chová stejně jako pro celé výstupní pole. Znak odsazení je **výplň**. Konečně:

- Pokud **iosbase**. **flags** & příznaky`ios_base::`[showpos](../standard-library/ios-functions.md#showpos) je nenulová, příznak **+** je předřazený ke specifikaci převodu.

- Pokud **iosbase**. **flags** & příznak`ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) je nenulová, příznak **#** je předřazený ke specifikaci převodu.

Čtvrtá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

chová se stejně třetí, s `l` tím rozdílem, že `L`kvalifikátor ve specifikaci převodu je nahrazen .

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

chová se stejně první, s tím `p`rozdílem, že specifikace převodu je **,** plus všechny kvalifikátor potřebné k určení odsazení.

Šestá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

chová se stejně jako první, s tím rozdílem, že generuje logické výstupní pole z *val*.

Logické výstupní pole má jednu ze dvou forem. Pokud `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) je **false**, `do_put(_Next, _Iosbase, _Fill, (long)val)`členské funkce vrátí , který obvykle vytváří generované sekvence buď 0 (pro **false**) nebo 1 (pro **true).** V opačném případě je vygenerovaná sekvence buď *fac*. [falsename](../standard-library/numpunct-class.md#falsename) (pro **false**), nebo *fac*. [truename](../standard-library/numpunct-class.md#truename) (pro **true).**

Sedmá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

chová se stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lld`.

Osmá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

chová se stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `llu`.

### <a name="example"></a>Příklad

Viz příklad pro [put](#put) `do_put`, který volá .

## <a name="num_putiter_type"></a><a name="iter_type"></a>num_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **OutputIterator.**

## <a name="num_putnum_put"></a><a name="num_put"></a>num_put::num_put

Konstruktor pro objekty `num_put`typu .

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- \>1: Tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože destruktor je chráněn.

Konstruktor inicializuje svůj základní objekt s **národním prostředím::**[omezující_ka](../standard-library/locale-class.md#facet_class)(_ *Refs).*

## <a name="num_putput"></a><a name="put"></a>num_put::put

Převede číslo na posloupnost `CharType`s, která představuje číslo formátované pro dané národní prostředí.

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>Parametry

*Dest*\
Iterátor adresování první prvek vloženého řetězce.

*_Iosbase*\
Zadali datový proud, který obsahuje národní prostředí s numpunct omezující plochu slouží k interpunkci výstupu a příznaky pro formátování výstupu.

*_Fill*\
Znak, který se používá pro mezery.

*Val*\
Číslo nebo logický typ, který má být výstup.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy pozici jeden za poslední prvek vyrobené.

### <a name="remarks"></a>Poznámky

Všechny členské funkce `next`vrátí `_Iosbase` `_Fill`do_put `val`( , , ). [do_put](#do_put)

### <a name="example"></a>Příklad

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[fazeta třídy](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
