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
ms.openlocfilehash: ac034a4b80225bd9674e72ca3255938316c5905a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457704"
---
# <a name="numput-class"></a>num_put – třída

Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu číselných hodnot na sekvence typu `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*OutputIterator*\
Typ iterátoru, do kterého číselné funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[num_put](#num_put)|Konstruktor pro objekty typu `num_put`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce, která je volána k převedení čísla na sekvenci `CharType`s, která představuje číslo formátované pro dané národní prostředí.|
|[převést](#put)|Převede číslo na sekvenci `CharType`s, která představuje číslo formátované pro dané národní prostředí.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="char_type"></a>num_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `CharType`šablony.

## <a name="do_put"></a>num_put::d o_put

Virtuální funkce, která je volána k převedení čísla na sekvenci `CharType`s, která představuje číslo formátované pro dané národní prostředí.

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

*generace*\
Iterátor adresující první prvek vloženého řetězce.

*_Iosbase*\
Byl zadán datový proud, který obsahuje národní prostředí s omezující vlastností numpunct, která se používá k punctuateí výstupu a příznaků formátování výstupu.

*_Fill*\
Znak, který se používá pro mezery.

*počítává*\
Typ Number nebo Boolean, který má být výstup.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění, které je umístěno na jednom za posledním vytvořeným prvkem.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce vygeneruje sekvenční prvky začínající na *Další* pro vytváření celočíselného výstupní pole z hodnoty *Val*. Funkce vrátí iterátor, který určuje další místo pro vložení elementu nad pole generovaného celočíselného výstupu.

Pole s celočíselným výstupem je vygenerováno pomocí stejných pravidel, která jsou používána funkcemi tisku pro vygenerování řady elementů **char** do souboru. U každého takového elementu char se předpokládá mapování na ekvivalentní prvek typu `CharType` jednoduchým mapováním 1:1. Místo toho, `do_put` kde funkce Print doplní pole buď mezerou, nebo číslicí 0. `fill` Ekvivalentní specifikace převodu tisk je určena následujícím způsobem:

- IF **iosbase**. [Flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield`,specifikace[](../standard-library/ios-functions.md#oct)převodu je .`lo` == `ios_base::`

- Pokud **iosbase. Flags** & **ios_base:: basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), je `lx`specifikace převodu.

- V opačném případě je `ld`specifikace převodu.

IF **iosbase**. [Šířka](../standard-library/ios-base-class.md#width) je nenulová, Šířka pole této hodnoty je přednastavena. Funkce pak zavolá **iosbase**. **Šířka** (0) Chcete-li obnovit šířku pole na nulu.

K odsazení dochází pouze v případě, že minimální počet prvků *N* vyžadovaných pro určení výstupního pole je menší než **iosbase**. [Šířka](../standard-library/ios-base-class.md#width). Takové odsazení se skládá z sekvence *N* - **šířky** kopie **výplně**. K odsazení pak dojde následujícím způsobem:

- IF **iosbase**. **příznaky** & [vlevo,](../standard-library/ios-functions.md#left)příznak **je-** předpona.`ios_base::adjustfield` == `ios_base::` (Odsazení proběhne po vygenerovaném textu.)

- Pokud **iosbase. Flags** & **ios_base:: adjustfield** == `ios_base::`[internal](../standard-library/ios-functions.md#internal), příznak **0** se přiřadí. (Pro pole číselného výstupu dojde k odsazení, kde je panel funkce tisku s 0.)

- Jinak se nepřidá žádný další příznak. (Odsazení proběhne před vygenerovanou sekvencí.)

Uznan

- IF **iosbase**. **příznaky** & [](../standard-library/ios-functions.md#showpos) showpos jsou nenulové, příznak **+** je předponou specifikace převodu.`ios_base::`

- IF **iosbase**. **příznaky**[](../standard-library/ios-functions.md#showbase) **#** ios_base:: showbase je nenulové, příznak je předponou specifikace převodu. & 

Formát pole s celočíselným výstupem je dále určen**FAC** [omezujícími vlastnostmi národního prostředí](../standard-library/locale-class.md#facet_class)vráceným voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md) \< **elem**> ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). Určen

- **FAC**. [seskupení](../standard-library/numpunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

- **FAC**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) Určuje sekvenci, která odděluje skupiny číslic nalevo od libovolné desetinné čárky.

Pokud **FAC**žádné omezení seskupení neukládá. **seskupení** (jeho první prvek má hodnotu CHAR_MAX), pak žádné instance **FAC**. `thousands_sep`jsou generovány v poli výstup. V opačném případě se po převodu tisku Vloží oddělovače.

Druhá virtuální funkce Protected member:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci `ld` převodu s. `lu`

Třetí funkce virtuální chráněné členské funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

se chová stejně jako první, s tím rozdílem, že generuje výstupní pole s plovoucí desetinnou čárkou z hodnoty **Val**. **FAC**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) Určuje sekvenci, která odděluje celočíselné číslice od číslic zlomku. Ekvivalentní specifikace převodu tisk je určena následujícím způsobem:

- IF **iosbase**. **příznaky**jsouopraveny, & specifikace[](../standard-library/ios-functions.md#fixed)převodu je`lf`.`ios_base::floatfield` == `ios_base::`

- IF **iosbase**. **Flags** & **ios_base:: floatfield** == `ios_base::`[vědecký](../standard-library/ios-functions.md#scientific), specifikace převodu je `le`. IF **iosbase**. **příznaky** `E`[](../standard-library/ios-functions.md#uppercase) `e` velká písmena jsou nenulové, jsou nahrazeny hodnotou. & `ios_base::`

- V opačném případě je specifikace převodu **LG**. IF **iosbase**. **příznaky** `g` `G`ios_base:: velká písmena jsou nenulové, jsou nahrazeny hodnotou. & 

IF **iosbase**. **příznaky** & **ios_base:: fixed** jsou nenulové nebo IF **iosbase**. [přesnost](../standard-library/ios-base-class.md#precision) je větší než nula, přesnost s hodnotou **iosbase**. do specifikace převodu se přidá **přesnost** . Jakékoli odsazení se chová stejně jako u pole s celočíselným výstupem. Znak odsazení je **Fill**. Uznan

- IF **iosbase**. **příznaky** & [](../standard-library/ios-functions.md#showpos) showpos jsou nenulové, příznak **+** je předponou specifikace převodu.`ios_base::`

- IF **iosbase**. **příznaky** & [](../standard-library/ios-functions.md#showpoint) showpoint jsou nenulové, příznak **#** je předponou specifikace převodu.`ios_base::`

Čtvrtá virtuální funkce Protected member:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

se chová stejně jako třetí, s tím rozdílem, že `l` kvalifikátor ve specifikaci převodu je `L`nahrazen.

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

se chová stejně jako první, s tím rozdílem, že je `p`specifikace převodu **,** a jakýkoliv kvalifikátor potřebný k určení odsazení.

Šestá virtuální členská funkce Protected:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

se chová stejně jako první, s tím rozdílem, že generuje výstupní pole Boolean z hodnoty *Val*.

Pole s logickým výstupem má jednu ze dvou forem. Pokud `iosbase.flags & ios_base::`je [boolalpha](../standard-library/ios-functions.md#boolalpha) **false**, vrátí `do_put(_Next, _Iosbase, _Fill, (long)val)`členská funkce, což obvykle vytvoří vygenerované pořadí buď 0 (pro **false**), nebo 1 (pro **true**). V opačném případě je vygenerovaná sekvence buď *FAC*. [hodnota false](../standard-library/numpunct-class.md#falsename) (pro **false**) nebo *FAC*. [hodnota true](../standard-library/numpunct-class.md#truename) (pro **true**).

Sedmá virtuální funkce chráněná členem:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci `ld` převodu s. `lld`

Osmá virtuální funkce Protected member:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci `ld` převodu s. `llu`

### <a name="example"></a>Příklad

Podívejte se na příklad pro [vložení](#put), která `do_put`volá.

## <a name="iter_type"></a>num_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **OutputIterator.**

## <a name="num_put"></a>num_put::num_put

Konstruktor pro objekty typu `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
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

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(_ *ReFS*).

## <a name="put"></a>num_put::p UT

Převede číslo na sekvenci `CharType`s, která představuje číslo formátované pro dané národní prostředí.

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

*propojovací*\
Iterátor adresující první prvek vloženého řetězce.

*_Iosbase*\
Byl zadán datový proud, který obsahuje národní prostředí s omezující vlastností numpunct, která se používá k punctuateí výstupu a příznaků formátování výstupu.

*_Fill*\
Znak, který se používá pro mezery.

*počítává*\
Typ Number nebo Boolean, který má být výstup.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresuje umístění, které je umístěno na jednom za posledním vytvořeným prvkem.

### <a name="remarks"></a>Poznámky

Všechny členské funkce vracejí [do_put](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`).

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

## <a name="see-also"></a>Viz také:

[\<> národního prostředí](../standard-library/locale.md)\
[Face – třída](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
