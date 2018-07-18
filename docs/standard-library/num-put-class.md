---
title: num_put – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
dev_langs:
- C++
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81bdbd07e06ef2ec24a5f220fcd11a228b783888
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965987"
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

*CharType* typ používaný v rámci programu ke kódování znaků v národním prostředí.

*OutputIterator* typ iterátoru, do kterého číselné funkce zapisují svůj výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v **id.**

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
|[do_put](#do_put)|Virtuální funkce, která je volána pro převod čísla na sekvenci `CharType`reprezentující Číslo formátované pro dané národní prostředí.|
|[Vložit](#put)|Převede číslo na sekvenci `CharType`reprezentující Číslo formátované pro dané národní prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="char_type"></a>  num_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

## <a name="do_put"></a>  num_put::do_put

Virtuální funkce, která je volána pro převod čísla na sekvenci `CharType`reprezentující Číslo formátované pro dané národní prostředí.

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

*Další* iterátor adresující první prvek vložený řetězec.

*_Iosbase* zadaný datový proud, který obsahuje národní prostředí s omezující vlastnost numpunct – umožňuje vložit interpunkci výstup a příznaky pro formátování výstupu.

*_Fill* znak, který se používá k vytvoření mezer.

*Val* číslo nebo logický typ, který má být výstup.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy jedna pozice za posledním prvkem, který vytváří.

### <a name="remarks"></a>Poznámky

První chráněná virtuální členská funkce generuje sekvenční prvky počínaje *Další* vytvoří celočíselné pole výstup z hodnoty *val*. Vrátí iterátor s vyznačením další místo na vkládání elementů nad rámec výstupního pole pro generované číslo.

Výstupní pole celé číslo je generován stejná pravidla používat funkce tisku pro generování posloupnosti **char** elementy do souboru. Každý znak prvek předpokládá, že je mapují na odpovídající element typu `CharType` mapováním jednoduché, 1: 1. Pokud tisk funkce vyplní pole s mezerami nebo číslice 0, ale `do_put` místo toho používá `fill`. Specifikace ekvivalentní tisku převodu je stanoven následujícím způsobem:

- Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), je specifikace převodu `lo`.

- Pokud **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), je specifikace převodu `lx`.

- V opačném případě je specifikace převodu `ld`.

Pokud **iosbase**. [Šířka](../standard-library/ios-base-class.md#width) je nenulová, šířku pole z této hodnoty se přidá jako předpona. Potom volá funkci **iosbase**. **Šířka**(0) k resetování šířku pole na hodnotu nula.

Odsazení dojde pouze v případě minimální počet prvků *N* vyžaduje k určení pole výstupu je menší než **iosbase**. [Šířka](../standard-library/ios-base-class.md#width). Takové odsazení se skládá z posloupnost *N* - **šířka** kopie **výplně**. Odsazení poté vyvolá následujícím způsobem:

- Pokud **iosbase**. **příznaky** & `ios_base::adjustfield` == `ios_base::`[levé](../standard-library/ios-functions.md#left), příznak **-** se přidá jako předpona. (Odsazení nastane po generovaný text).

- Pokud **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[interní](../standard-library/ios-functions.md#internal), příznak **0** je přidáno jako předpona. (Pro výstup číselné pole, odsazení nastane, kde funkce tisku pro zapisování s 0.)

- V opačném případě žádné další příznak se přidá jako předpona. (Odsazení předchází generovaného sekvenčního.)

Nakonec:

- Pokud **iosbase**. **příznaky** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) nenulovou hodnotu, je příznak **+** je přidáno jako předpona specifikace převodu.

- Pokud **iosbase**. **příznaky** & **ios_base –::**[showbase](../standard-library/ios-functions.md#showbase) nenulovou hodnotu, je příznak **#** je přidáno jako předpona specifikace převodu.

Formát celé výstup pole Další závisí [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)**fac** vrácený voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct – ](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)). Konkrétně:

- **FAC**. [seskupení](../standard-library/numpunct-class.md#grouping) určuje způsob seskupení číslic vlevo od desetinné čárky

- **FAC**. [thousands_sep –](../standard-library/numpunct-class.md#thousands_sep) Určuje sekvenci, která odděluje skupin číslic nalevo od desetinné čárky

Pokud technologie se nevyžaduje žádná omezení seskupení **fac**. **seskupení** (jeho prvního prvku má hodnotu CHAR_MAX), pak žádné instance **fac**. `thousands_sep` jsou generovány v poli výstup. V opačném případě jsou vloženy oddělovače, když dojde k tisku převodu.

Chráněná virtuální členská funkce second:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

chová se stejně jako první, s tím rozdílem, že ji nahradí specifikace převodu z `ld` s `lu`.

Třetí chráněná virtuální členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

chová se stejně jako první, s tím rozdílem, že vytvoří pole s plovoucí desetinnou čárkou výstup z hodnoty **val**. **FAC**. [decimal_point –](../standard-library/numpunct-class.md#decimal_point) Určuje sekvenci, která odděluje celá čísla od číslic zlomku. Specifikace ekvivalentní tisku převodu je stanoven následujícím způsobem:

- Pokud **iosbase**. **příznaky** & `ios_base::floatfield` == `ios_base::`[oprava](../standard-library/ios-functions.md#fixed), je specifikace převodu `lf`.

- Pokud **iosbase**. **příznaky** & **ios_base::floatfield** == `ios_base::`[vědecké](../standard-library/ios-functions.md#scientific), je specifikace převodu `le`. Pokud **iosbase**. **příznaky** & `ios_base::`[velká](../standard-library/ios-functions.md#uppercase) nenulové, `e` nahradí `E`.

- V opačném případě je specifikace převodu **lg**. Pokud **iosbase**. **příznaky** & **ios_base::uppercase** nenulové, `g` nahradí `G`.

Pokud **iosbase**. **příznaky** & **ios_base::fixed** je nenulová nebo pokud **iosbase**. [přesnost](../standard-library/ios-base-class.md#precision) je větší než nula, přesností s hodnotou **iosbase**. **přesnost** je přidáno jako předpona specifikace převodu. Žádné odsazení se chová stejně jako pro výstupní pole celé číslo. Odsazení znaku je **výplně**. Nakonec:

- Pokud **iosbase**. **příznaky** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) nenulovou hodnotu, je příznak **+** je přidáno jako předpona specifikace převodu.

- Pokud **iosbase**. **příznaky** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) nenulovou hodnotu, je příznak **#** je přidáno jako předpona specifikace převodu.

Čtvrtý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

třetí, s výjimkou, že se chová stejně kvalifikátor `l` v převodu je nahrazen specifikace `L`.

Pátý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

se chová stejně první, s tím rozdílem, že je specifikace převodu `p` **,** plus všechny kvalifikátor třeba určit odsazení.

Šestý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

chová se stejně jako první, s tím rozdílem, že generuje logická výstupního pole z *val*.

Logická výstupního pole má jednu z těchto dvou tvarů. Pokud **iosbase**. **příznaky** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) je **false**, členská funkce vrátí `do_put`(_ *Další*, \_ *Iosbase*, \_ *vyplnit*, ( **dlouhé**) `val`), které obvykle vytváří generovaného sekvenčního buď 0 (pro **false**) nebo 1 (pro **true**). V opačném případě generovaného sekvenčního je buď **fac**. [falsename –](../standard-library/numpunct-class.md#falsename) `)` (pro **false**), nebo **fac**. [truename –](../standard-library/numpunct-class.md#truename) (pro **true**).

Sedmý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

chová se stejně jako první, s tím rozdílem, že ji nahradí specifikace převodu z `ld` s `lld`.

Osmého chráněná virtuální členská funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

chová se stejně jako první, s tím rozdílem, že ji nahradí specifikace převodu z `ld` s `llu`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [umístit](#put), který volá `do_put`.

## <a name="iter_type"></a>  num_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **OutputIterator.**

## <a name="num_put"></a>  num_put::num_put

Konstruktor pro objekty typu `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* celočíselnou hodnotu použít k určení typu Správa paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* parametrů a jejich význam:

- 0: Životnost objektu se spravuje přes národní prostředí, které je obsahují.

- 1: doba života objektu je nutné ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je to možné, protože destruktor je chráněn.

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(_ *odolný systém souborů*).

## <a name="put"></a>  num_put::Put

Převede číslo na sekvenci `CharType`reprezentující Číslo formátované pro dané národní prostředí.

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

*DEST* iterátor adresující první prvek vložený řetězec.

*_Iosbase* zadaný datový proud, který obsahuje národní prostředí s omezující vlastnost numpunct – umožňuje vložit interpunkci výstup a příznaky pro formátování výstupu.

*_Fill* znak, který se používá k vytvoření mezer.

*Val* číslo nebo logický typ, který má být výstup.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresy jedna pozice za posledním prvkem, který vytváří.

### <a name="remarks"></a>Poznámky

Vrátí všechny členské funkce [do_put –](#do_put)( `next`, `_Iosbase`, `_Fill`, `val`).

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

[\<národní prostředí >](../standard-library/locale.md)<br/>
[facet – třída](../standard-library/locale-class.md#facet_class)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
