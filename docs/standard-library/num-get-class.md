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
ms.openlocfilehash: 76d2832141c65ca67c42f1994a3c8f5b532f0092
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373656"
---
# <a name="num_get-class"></a>num_get – třída

Šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost `CharType` národního prostředí pro řízení převodů sekvencí typu na číselné hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*Vstupní iterátor*\
Typ iterátoru, ze kterého číselné funkce get čtou svůj vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[num_get](#num_get)|Konstruktor pro objekty `num_get` typu, které se používají k extrahování číselné hodnoty z sekvencí.|

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

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="num_getchar_type"></a><a name="char_type"></a>num_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **CharType**.

## <a name="num_getdo_get"></a><a name="do_get"></a>num_get::do_get

Virtuální funkce volaná k extrakci číselné hodnoty nebo logické hodnoty ze sekvence znaků.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>Parametry

*První*\
Začátek rozsahu znaků, ze kterého chcete číst číslo.

*Poslední*\
Konec rozsahu znaků, ze kterého chcete číst číslo.

*iosbase*\
[ios_base,](../standard-library/ios-base-class.md) jehož příznaky jsou používány převodu.

*Státu*\
Stav, do kterého failbit (viz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) je přidán při selhání.

*Val*\
Hodnota, která byla přečtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor po čtení hodnoty.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce,

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

odpovídá sekvenčním prvkům začínajícím *nejprve* v sekvenci, `[first, last)` dokud nerozpozná celé pole. Pokud je úspěšná, převede toto pole na ekvivalentní hodnotu jako typ **long**a uloží výsledek do *val*. Vrátí iterátor označující první prvek za číselné vstupní pole. V opačném případě funkce ukládá `ios_base::failbit` nic `state`ve *val* a sady v . Vrátí iterátor označující první prvek za libovolnou předponou platného celého vstupního pole. V obou případech, pokud se `last`vrácená `ios_base::eofbit` hodnota `state`rovná , funkce nastaví v .

Celé vstupní pole je převedeno podle stejných pravidel, která používají funkce skenování pro párování a převod řady **znaků** ze souboru. (Předpokládá se, že každý takový **znakový** `Elem` prvek je mapován na ekvivalentní prvek typu jednoduchým mapováním 1:1.) Ekvivalentní specifikace převodu skenování se stanoví takto:

Pokud `iosbase.` [ios_base::příznaky](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[v říjnu](../standard-library/ios-functions.md#oct), specifikace převodu je `lo`.

Pokud `iosbase.flags() & ios_base::basefield == ios_base::` [hex](../standard-library/ios-functions.md#hex), specifikace `lx`převodu je .

Pokud `iosbase.flags() & ios_base::basefield == 0`je `li`specifikace převodu .

V opačném případě `ld`je specifikace převodu .

Formát celého vstupního pole je dále určen omezující majestátem`fac` [národního prostředí](../standard-library/locale-class.md#facet_class) vráceným voláním [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Konkrétně:

`fac.`[numpunct::seskupení](../standard-library/numpunct-class.md#grouping) `()` určuje, jak jsou číslice seskupeny nalevo od jakékoli desetinné čárky

`fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` určuje sekvenci, která odděluje skupiny číslic nalevo od libovolné desetinné čárky.

Pokud se v `fac.thousands_sep()` číselném vstupním poli nevyskytují žádné instance, není uloženo žádné omezení seskupení. V opačném případě jsou vynucena všechna omezení seskupení vynucená `fac.grouping()` a oddělovače jsou odebrány dříve, než dojde k převodu skenování.

Čtvrtá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

chová se stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lu`. Pokud je úspěšná, převede číselné vstupní pole na hodnotu typu **nepodepsané long** a uloží tuto hodnotu ve *val*.

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

chová se stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lld`. Pokud je úspěšná, převede číselné vstupní pole na hodnotu typu **long** long a uloží tuto hodnotu do *val*.

Šestá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

chová se stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `llu`. Pokud je úspěšná, převede číselné vstupní pole na hodnotu typu **nepodepsané dlouhé** a ukládá tuto hodnotu ve *val*.

Sedmá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

chová se stejně jako první, s tím rozdílem, že se snaží odpovídat úplné, neprázdné vstupní pole s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` určuje sekvenci, která odděluje celé číslice od číslic zlomku. Ekvivalentní specifikátor převodu `lf`skenování je .

Osmá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

chová se stejně jako první, s tím rozdílem, že se snaží odpovídat úplné, neprázdné vstupní pole s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` určuje sekvenci, která odděluje celé číslice od číslic zlomku. Ekvivalentní specifikátor převodu `lf`skenování je .

Devátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

chová se stejně jako osmý, s tím rozdílem, `Lf`že ekvivalentní specifikátor převodu skenování je .

Desátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

chová se stejně jako první, s tím rozdílem, že ekvivalentní specifikátor převodu skenování je `p`.

Poslední (jedenáctá) virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

chová stejně jako první, s tím rozdílem, že se snaží odpovídat úplné, neprázdné logické vstupní pole. Pokud je úspěšná, převede logické vstupní pole na hodnotu typu **bool** a uloží tuto hodnotu do *val*.

Logické vstupní pole má jeden ze dvou formulářů. Pokud `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) je false, je stejný jako celé vstupní pole, s tím rozdílem, že převedená hodnota musí být buď 0 (pro false) nebo 1 (pro true). V opačném případě musí `fac.`sekvence odpovídat buď [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (pro false) nebo `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (pro true).

### <a name="example"></a>Příklad

Viz příklad pro [get](#get), kde je `do_get`volána virtuální členská funkce .

## <a name="num_getget"></a><a name="get"></a>num_get::získat

Extrahuje ze sekvence znaků číselnou nebo logickou hodnotu.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>Parametry

*První*\
Začátek rozsahu znaků, ze kterého chcete číst číslo.

*Poslední*\
Konec rozsahu znaků, ze kterého chcete číst číslo.

*iosbase*\
[ios_base,](../standard-library/ios-base-class.md) jehož příznaky jsou používány převodu.

*Státu*\
Stav, do kterého failbit (viz [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) je přidán při selhání.

*Val*\
Hodnota, která byla přečtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor po čtení hodnoty.

### <a name="remarks"></a>Poznámky

Všechny členské funkce vrátí [do_get](#do_get)`( first, last, iosbase, state, val)`.

První virtuální chráněná členská funkce se pokusí porovnat `first`sekvenční prvky začínající nejprve v sekvenci [ , `last`), dokud nerozpozná celé pole. Pokud je úspěšná, převede toto pole na ekvivalentní hodnotu jako **dlouhý** typ a uloží výsledek do *val*. Vrátí iterátor označující první prvek za číselné vstupní pole. V opačném případě funkce ukládá `ios_base::failbit` nic ve *val* a sady ve *stavu*. Vrátí iterátor označující první prvek za libovolnou předponou platného celého vstupního pole. V obou případech, pokud se vrácená hodnota `ios_base::eofbit` rovná *poslední*, funkce nastaví ve *stavu*.

Celé vstupní pole je převedeno podle stejných pravidel, která používají funkce skenování pro párování a převod řady **znaků** ze souboru. Předpokládá se, že každý takový **znakový** `CharType` prvek je mapován na ekvivalentní prvek typu jednoduchým mapováním 1:1. Ekvivalentní specifikace převodu skenování se stanoví takto:

- Pokud `iosbase.` [příznaky](../standard-library/ios-base-class.md#flags)`& ios_base::basefield == ios_base::`[října](../standard-library/ios-functions.md#oct), `lo`specifikace převodu je .

- Pokud `iosbase.flags & ios_base::basefield == ios_base::` [hex](../standard-library/ios-functions.md#hex), specifikace `lx`převodu je .

- Pokud `iosbase.flags & ios_base::basefield == 0`je `li`specifikace převodu .

- V opačném případě `ld`je specifikace převodu .

Formát celého vstupního pole je dále určen omezující majestát [emotér](../standard-library/locale-class.md#facet_class) `fac` národního prostředí vrácenou voláním [use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[getloc](../standard-library/ios-base-class.md#getloc)`())`. Konkrétně:

- `fac.`[seskupení](../standard-library/numpunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od jakékoli desetinné čárky.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) určuje sekvenci, která odděluje skupiny číslic nalevo od jakékoli desetinné čárky.

Pokud se v `fac.thousands_sep` číselném vstupním poli nevyskytují žádné instance, není uloženo žádné omezení seskupení. V opačném případě jsou vynucena všechna omezení seskupení vynucená `fac.grouping` a oddělovače jsou odebrány dříve, než dojde k převodu skenování.

Druhá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

chová se stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lu`. Pokud je úspěšná, převede číselné vstupní pole na hodnotu typu **long bez znaménka** a tuto hodnotu uloží do *val*.

Třetí virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

chová stejně jako první, s tím rozdílem, že se pokusí porovnat úplné, neprázdné vstupní pole s plovoucí desetinnou desetinnou hlavou. `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point) určuje sekvenci, která odděluje celé číslice od dělicích čísel zlomků. Ekvivalentní specifikátor převodu `lf`skenování je .

Čtvrtá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

chová se stejně třetí, s tím rozdílem, `Lf`že ekvivalentní specifikátor převodu skenování je .

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

chová se stejně jako první, s tím rozdílem, že ekvivalentní specifikátor převodu skenování je `p`.

Šestá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

chová stejně jako první, s tím rozdílem, že se pokusí porovnat úplné, neprázdné logické vstupní pole. Pokud je úspěšná, převede logické vstupní pole na hodnotu typu **bool** a uloží tuto hodnotu do *val*.

Logické vstupní pole má jednu ze dvou forem. Pokud `iosbase.flags & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) je **false**, je stejný jako celé vstupní pole, s tím rozdílem, že převedená hodnota musí být buď 0 (pro **false)** nebo 1 (pro **true).** V opačném případě se `fac.`sekvence musí shodovat buď [falsename](../standard-library/numpunct-class.md#falsename) (pro **false**), nebo `fac.` [truename](../standard-library/numpunct-class.md#truename) (pro **true**).

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

## <a name="num_getiter_type"></a><a name="iter_type"></a>num_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `InputIterator`parametr šablony .

## <a name="num_getnum_get"></a><a name="num_get"></a>num_get::num_get

Konstruktor pro objekty `num_get` typu, které se používají k extrahování číselné hodnoty z sekvencí.

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- \>1: Tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože destruktor je chráněn.

Konstruktor inicializuje svůj základní `locale::`objekt [s faškou](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[fazeta třídy](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
