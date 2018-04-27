---
title: num_put – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 212de77da6e1f8134f311a4dcb4440b4e61a4b11
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="numput-class"></a>num_put – třída

Třídu šablony, která popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převody číselných hodnot pořadí typu `CharType`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ v rámci programu použitá ke kódování znaků v národním prostředí.

`OutputIterator` Typ iterator, ke kterému číselné vložení funkcí zápis jejich výstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[num_put](#num_put)|V konstruktoru pro objekty typu `num_put`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje výstupní iterátor.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_put](#do_put)|Virtuální funkce, která je volána k převodu čísla do posloupnost `CharType`s, který představuje číslo formátu pro dané národní prostředí.|
|[PUT](#put)|Převádí číslo na posloupnost `CharType`s, který představuje číslo formátu pro dané národní prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="char_type"></a>  num_put::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="do_put"></a>  num_put::do_put

Virtuální funkce, která je volána k převodu čísla do posloupnost **CharType**s, který představuje číslo formátu pro dané národní prostředí.

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

`next` Iterace adresování první prvek vložené řetězce.

`_Iosbase` Zadaný datový proud obsahující národního prostředí s numpunct omezující vlastnost umožňuje vložit interpunkci výstup a příznaky pro formátování výstupu.

`_Fill` Znak, který se používá k vytvoření mezer.

`val` Číslo nebo typem logická hodnota, která má být výstup.

### <a name="return-value"></a>Návratová hodnota

Iterátor výstup vytváří jeden pozice za posledním elementem adresy.

### <a name="remarks"></a>Poznámky

První virtuální chráněného člena funkce generuje sekvenční elementy začínající na `next` k vytvoření výstupní pole celé číslo od hodnoty `val`. Funkce vrátí hodnotu iterator určení další místo vložte element nad rámec pole výstup generovaný celé číslo.

Pole výstup celé číslo je generován stejná pravidla používané tiskové funkce pro generování řadu `char` elementy do souboru. Každý char prvek se předpokládá, že k mapování na ekvivalentní element typu **CharType** mapováním jednoduchý, 1: 1. Kde tiskové funkce ohraničí pole s mezery ani číslice 0, ale `do_put` místo toho používá **výplně**. Specifikace ekvivalentní tiskové převod je stanoven následujícím způsobem:

- Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), je specifikace převod **u**.

- Pokud **iosbase.flags** & **ios_base::basefield** == `ios_base::`[šestnáctkových](../standard-library/ios-functions.md#hex), je specifikace převod **lx** .

- Jinak je specifikace převod **ld**.

Pokud **iosbase**. [Šířka](../standard-library/ios-base-class.md#width) je nenulové hodnoty, šířka pole tato hodnota se přidá jako předpona. Pak zavolá funkci **iosbase**. **Šířka**(0) k šířce pole nastaven na hodnotu nula.

Odsazení dojde pouze v případě minimální počet elementů *N* zapotřebí zadat pole výstupu je menší než **iosbase**. [Šířka](../standard-library/ios-base-class.md#width). Takové odsazení se skládá z posloupnost *N* - **šířka** zkopíruje z **výplně**. Odsazení pak probíhá následujícím způsobem:

- Pokud **iosbase**. **příznaky** & `ios_base::adjustfield` == `ios_base::`[levém](../standard-library/ios-functions.md#left), příznak **-** se přidá jako předpona. (Odsazení nachází za generovaným textem.)

- Pokud **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[interní](../standard-library/ios-functions.md#internal), příznak **0** před. (U číselné výstup pole odsazení dochází k kde tiskové funkce odsadí s 0.)

- V opačném před žádné další příznak. (Odsazení dojde před generovaným pořadí).

Nakonec:

- Pokud **iosbase**. **příznaky** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) nenulové hodnoty, je příznak **+** se přidá jako předpona specifikaci převod.

- Pokud **iosbase**. **příznaky** & **ios_base::**[showbase](../standard-library/ios-functions.md#showbase) nenulové hodnoty, je příznak **#** se přidá jako předpona specifikaci převod.

Výstupní formát celé pole je dáno Další [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)**fac** volání vráceny [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct ](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)). Konkrétně:

- **FAC**. [seskupování](../standard-library/numpunct-class.md#grouping) určuje způsob seskupení číslic nalevo od všech desetinné čárky

- **FAC**. [thousands_sep –](../standard-library/numpunct-class.md#thousands_sep) určuje pořadí, který odděluje skupiny číslic nalevo od všech desetinné čárky

Pokud se nevyžaduje žádná omezení seskupení **fac**. **seskupování** (jeho první prvek má hodnotu char_max –), pak žádné instance **fac**. `thousands_sep` jsou generovány, v poli výstup. Jinak jsou vloženy oddělovače potom, co dojde tiskové převod.

Druhý virtuální chráněného člena funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

se chová stejně jako první, s tím rozdílem, že se nahradí převod specifikaci **ld** s **lu**.

Třetí virtuální chráněného člena funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

se chová stejně jako první, s tím rozdílem, že vytváří pole od hodnoty s plovoucí desetinnou čárkou výstup **val**. **FAC**. [decimal_point –](../standard-library/numpunct-class.md#decimal_point) určuje pořadí, který odděluje číslic celé číslo od zlomek číslic. Specifikace ekvivalentní tiskové převod je stanoven následujícím způsobem:

- Pokud **iosbase**. **příznaky** & `ios_base::floatfield` == `ios_base::`[pevné](../standard-library/ios-functions.md#fixed), je specifikace převod **lf**.

- Pokud **iosbase**. **příznaky** & **ios_base::floatfield** == `ios_base::`[scientific](../standard-library/ios-functions.md#scientific), je specifikace převod `le`. Pokud **iosbase**. **příznaky** & `ios_base::`[velká](../standard-library/ios-functions.md#uppercase) nenulový, **e** se nahradí **E**.

- Jinak je specifikace převod **kontaktní skupině**. Pokud **iosbase**. **příznaky** & **ios_base::uppercase** nenulový, **g** se nahradí **G**.

Pokud **iosbase**. **příznaky** & **ios_base::fixed** nenulový nebo, pokud **iosbase**. [přesnost](../standard-library/ios-base-class.md#precision) je větší než nula, přesností s hodnotou **iosbase**. **přesnost** se přidá jako předpona specifikaci převod. Všechny odsazení se chová stejně jako u výstupní pole celé číslo. Znak odsazení je **výplně**. Nakonec:

- Pokud **iosbase**. **příznaky** & `ios_base::`[showpos](../standard-library/ios-functions.md#showpos) nenulové hodnoty, je příznak **+** se přidá jako předpona specifikaci převod.

- Pokud **iosbase**. **příznaky** & `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint) nenulové hodnoty, je příznak **#** se přidá jako předpona specifikaci převod.

Čtvrtý chráněného člena virtuální funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

třetí, vyjma toho, že se chová stejně kvalifikátor **l** v převodu se nahradí specifikace **L**.

Funkci páté virtuální chráněného člena:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

se chová stejně první, s tím rozdílem, že je specifikace převod `p` **,** plus žádné kvalifikátor potřebná pro určení odsazení.

Šesté chráněného člena virtuální funkce:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

se chová stejně jako první, s tím rozdílem, že vygeneruje pole logický výstup z `val`.

Pole logická výstup trvá dvě formy. Pokud **iosbase**. **příznaky** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) je **false**, vrátí funkce člena `do_put`(_ *Další*, \_ *Iosbase*, \_ *vyplnění*, ( **dlouho**) `val`), který obvykle vytvoří generovaného pořadí buď 0 (pro **false**) nebo 1 (pro **true**). Jinak generovaného pořadí je buď **fac**. [falsename –](../standard-library/numpunct-class.md#falsename) `)` (pro **false**), nebo **fac**. [truename –](../standard-library/numpunct-class.md#truename) (pro **true**).

Funkci sedmého virtuální chráněného člena:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

se chová stejně jako první, s tím rozdílem, že se nahradí převod specifikaci **ld** s **stanovená v čl**.

Funkci osmého virtuální chráněného člena:

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

se chová stejně jako první, s tím rozdílem, že se nahradí převod specifikaci `ld` s `llu`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [put](#put), který volá `do_put`.

## <a name="iter_type"></a>  num_put::iter_type

Typ, který popisuje výstupní iterátor.

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **OutputIterator.**

## <a name="num_put"></a>  num_put::num_put

V konstruktoru pro objekty typu `num_put`.

```cpp
explicit num_put(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Celočíselná hodnota určuje typ správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty `_Refs` parametrů a jejich významu jsou:

- 0: doba života objektu spravuje národní prostředí, které je obsahují.

- 1: doba života objektu, se musí ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je možné, protože je chráněn destruktoru.

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(_ *odolný systém souborů*).

## <a name="put"></a>  num_put::Put

Převádí číslo na posloupnost **CharType**s, který představuje číslo formátu pro dané národní prostředí.

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

`dest` Iterace adresování první prvek vložené řetězce.

`_Iosbase` Zadaný datový proud, který obsahuje národního prostředí s numpunct omezující vlastnost umožňuje vložit interpunkci výstup a příznaky pro formátování výstupu.

`_Fill` Znak, který se používá k vytvoření mezer.

`val` Číslo nebo typem logická hodnota, která má být výstup.

### <a name="return-value"></a>Návratová hodnota

Iterátor výstup vytváří jeden pozice za posledním elementem adresy.

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

## <a name="see-also"></a>Viz také

[\<národní prostředí >](../standard-library/locale.md)<br/>
[facet – třída](../standard-library/locale-class.md#facet_class)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
