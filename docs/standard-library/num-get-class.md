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
ms.openlocfilehash: bf6623bb61e7a217fcc18a268a583a7ecea4931d
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72889992"
---
# <a name="num_get-class"></a>num_get – třída

Šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu `CharType` na číselné hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType* \
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*InputIterator* \
Typ iterátoru, ze kterého číselné funkce get čtou svůj vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[num_get](#num_get)|Konstruktor pro objekty typu `num_get`, které slouží k extrakci číselných hodnot ze sekvencí.|

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

**Záhlaví:** \<locale >

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

*první* \
Začátek rozsahu znaků, ze kterého má být číslo čteno.

*poslední* \
Konec rozsahu znaků, ze kterého má být číslo čteno.

*iosbase* \
[Ios_base](../standard-library/ios-base-class.md) , jehož příznaky jsou používány převodem.

\ *stavu*
Stav, ke kterému se failbit (viz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)), se přidá při selhání.

\ *Val*
Hodnota, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor po načtení hodnoty.

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

Porovná sekvenční prvky začínající *první* v sekvenci `[first, last)`, dokud nerozpozná celé, neprázdné pole Input Integer. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu jako typ **Long**a výsledek uloží do hodnoty *Val*. Vrátí iterátor, který určuje první prvek nad číselným vstupním polem. V opačném případě funkce uloží nic do hodnoty *Val* a nastaví `ios_base::failbit` v `state`. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného celočíselného pole. V obou případech, pokud se návratová hodnota rovná `last`, funkce nastaví `ios_base::eofbit` v `state`.

Pole typu celé číslo je převedeno pomocí stejných pravidel používaných funkcemi kontroly pro porovnání a převod řady prvků typu **char** ze souboru. (Každý takový element **char** se předpokládá, že se mapuje na ekvivalentní prvek typu `Elem` jednoduchým mapováním 1:1.) Ekvivalentní specifikace převodu vyhledávání se určuje takto:

Pokud `iosbase.`[ios_base:: flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[OCT](../standard-library/ios-functions.md#oct), je specifikace převodu `lo`.

Pokud `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), je specifikace převodu `lx`.

Je-li `iosbase.flags() & ios_base::basefield == 0`, je specifikace převodu `li`.

V opačném případě je specifikace převodu `ld`.

Formát pole pro zadání celého čísla je dále určen [omezující vlastností národního prostředí](../standard-library/locale-class.md#facet_class)`fac` vrácených voláním [use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[ios_base:: getloc](../standard-library/ios-base-class.md#getloc)`())`. Určen

`fac.`[numpunct:: seskupovací](../standard-library/numpunct-class.md#grouping)`()` určuje, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

`fac.`[numpunct:: thousands_sep](../standard-library/numpunct-class.md#thousands_sep)`()` Určuje sekvenci, která odděluje skupiny číslic nalevo od desetinné čárky.

Pokud nedošlo k žádné instanci `fac.thousands_sep()` v poli číselného vstupu, není uloženo žádné omezení seskupení. V opačném případě jsou vynucená všechna omezení seskupení zavedená `fac.grouping()` a pak se odeberou oddělovače, než dojde k převodu vyhledávání.

Čtvrtá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lu`. V případě úspěchu převede číselné vstupní pole na hodnotu typu **bez znaménka Long** a uloží tuto hodnotu v *Val*.

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lld`. V případě úspěchu převede číselné vstupní pole na hodnotu typu **Long Long** a uloží tuto hodnotu do hodnoty *Val*.

Šestá virtuální členská funkce Protected:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `llu`. V případě úspěchu převede číselné vstupní pole na hodnotu typu **bez znaménka Long Long** a uloží tuto hodnotu v *Val*.

Sedmá virtuální funkce chráněná členem:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

se chová stejně jako první, s tím rozdílem, že budoucna odpovídá celému vstupnímu poli s plovoucí desetinnou čárkou (Neprázdné). `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point)`()` Určuje sekvenci, která odděluje celočíselné číslice od číslic zlomku. Ekvivalentní specifikátor převodu vyhledávání je `lf`.

Osmá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

se chová stejně jako první, s tím rozdílem, že budoucna odpovídá celému vstupnímu poli s plovoucí desetinnou čárkou (Neprázdné). `fac.`[numpunct::d ecimal_point](../standard-library/numpunct-class.md#decimal_point)`()` Určuje sekvenci, která odděluje celočíselné číslice od číslic zlomku. Ekvivalentní specifikátor převodu vyhledávání je `lf`.

Devátá funkce virtuální chráněné členské funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

se chová stejně jako osmá, s tím rozdílem, že ekvivalentní specifikátor převodu vyhledávání je `Lf`.

Desátá členská funkce Protected:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

se chová stejně jako první, s výjimkou, že je `p` ekvivalentní specifikátor převodu vyhledávání.

Poslední (jedenáctá) virtuální funkce chráněná členem:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

se chová stejně jako první, s tím rozdílem, že budoucna odpovídá celému neprázdnému vstupnímu poli logických hodnot. V případě úspěchu převede vstupní pole Boolean na hodnotu typu **bool** a uloží tuto hodnotu do hodnoty *Val*.

Logické vstupní pole má jednu ze dvou forem. Pokud `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) je false, je stejný jako pole typu Integer, s výjimkou, že převedená hodnota musí být 0 (pro false) nebo 1 (pro true). V opačném případě musí sekvence odpovídat buď `fac.`[numpunct:: false](../standard-library/numpunct-class.md#falsename) `()` (pro false), nebo `fac.`[numpunct:: true](../standard-library/numpunct-class.md#truename) `()` (pro true).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Get](#get), kde je virtuální členská funkce volána nástrojem `do_get`.

## <a name="get"></a>num_get:: Get

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

*první* \
Začátek rozsahu znaků, ze kterého má být číslo čteno.

*poslední* \
Konec rozsahu znaků, ze kterého má být číslo čteno.

*iosbase* \
[Ios_base](../standard-library/ios-base-class.md) , jehož příznaky jsou používány převodem.

\ *stavu*
Stav, ke kterému se failbit (viz [ios_base:: iostate](../standard-library/ios-base-class.md#iostate)), se přidá při selhání.

\ *Val*
Hodnota, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor po načtení hodnoty.

### <a name="remarks"></a>Poznámky

Všechny členské funkce vracejí [do_get](#do_get)`( first, last, iosbase, state, val)`.

První virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající první v sekvenci [`first`, `last`), dokud nerozpozná celé, neprázdné pole Input Integer. V případě úspěchu převede toto pole na jeho ekvivalentní hodnotu jako typ **Long** a výsledek uloží do hodnoty *Val*. Vrátí iterátor, který určuje první prvek nad číselným vstupním polem. V opačném případě funkce uloží nic do hodnoty *Val* a nastaví `ios_base::failbit` ve *stavu*. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného celočíselného pole. V obou případech, Pokud vrácená hodnota se rovná *Last*, sada funkcí nastaví `ios_base::eofbit` ve *stavu*.

Pole typu celé číslo je převedeno pomocí stejných pravidel používaných funkcemi kontroly pro porovnání a převod řady prvků typu **char** ze souboru. U každého takového elementu **char** se předpokládá mapování na ekvivalentní prvek typu `CharType` jednoduchým mapováním 1:1. Ekvivalentní specifikace převodu vyhledávání se určuje takto:

- Pokud `iosbase.`[flags](../standard-library/ios-base-class.md#flags)` & ios_base::basefield == ios_base::`[ZZÚ](../standard-library/ios-functions.md#oct), je specifikace převodu `lo`.

- Pokud `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), je specifikace převodu `lx`.

- Je-li `iosbase.flags & ios_base::basefield == 0`, je specifikace převodu `li`.

- V opačném případě je specifikace převodu `ld`.

Formát pole pro zadání celého čísla je dále určen [omezující vlastností národního prostředí](../standard-library/locale-class.md#facet_class) `fac` vrácených voláním [use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[getloc](../standard-library/ios-base-class.md#getloc)`())`. Určen

- [seskupení](../standard-library/numpunct-class.md#grouping) `fac.`určuje, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep) Určuje sekvenci, která odděluje skupiny číslic nalevo od libovolné desetinné čárky.

Pokud nedošlo k žádné instanci `fac.thousands_sep` v poli číselného vstupu, není uloženo žádné omezení seskupení. V opačném případě se vynucuje všechna omezení seskupení zavedená `fac.grouping` a před převodem vyhledávání se odeberou oddělovače.

Druhá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

se chová stejně jako první, s tím rozdílem, že nahrazuje specifikaci převodu `ld` s `lu`. V případě úspěchu převede pole číselného vstupu na hodnotu typu **bez znaménka Long** a uloží tuto hodnotu v *Val*.

Třetí funkce virtuální chráněné členské funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

se chová stejně jako první, s tím rozdílem, že se pokusí vyhledat celé neprázdné vstupní pole s plovoucí desetinnou čárkou. `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point) Určuje sekvenci, která odděluje celočíselné číslice od číslic zlomku. Ekvivalentní specifikátor převodu vyhledávání je `lf`.

Čtvrtá virtuální funkce Protected member:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

se chová stejně jako třetí, s tím rozdílem, že ekvivalentní specifikátor převodu pro kontrolu je `Lf`.

Pátá virtuální chráněná členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

se chová stejně jako první, s výjimkou, že je `p` ekvivalentní specifikátor převodu vyhledávání.

Šestá virtuální členská funkce Protected:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

se chová stejně jako první, s tím rozdílem, že se pokusí porovnat celé neprázdné logické vstupní pole. V případě úspěchu převede vstupní pole Boolean na hodnotu typu **bool** a uloží tuto hodnotu do hodnoty *Val*.

Logické vstupní pole má jednu ze dvou forem. Pokud `iosbase.flags & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) je **false**, je stejný jako pole typu Integer, s výjimkou, že převedená hodnota musí být 0 (pro **false**) nebo 1 (pro **true**). V opačném případě musí sekvence odpovídat buď `fac.`[false](../standard-library/numpunct-class.md#falsename) (pro **false**), nebo `fac.`[hodnotu true](../standard-library/numpunct-class.md#truename) (pro **true**).

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

Typ je synonymum pro parametr šablony `InputIterator`.

## <a name="num_get"></a>num_get::num_get

Konstruktor pro objekty typu `num_get`, které slouží k extrakci číselných hodnot ze sekvencí.

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

\ *ReFS*
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *ReFS* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože je destruktor chráněný.

Konstruktor inicializuje svůj základní objekt pomocí `locale::`[omezujících vlastností](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="see-also"></a>Viz také:

[\<locale >](../standard-library/locale.md) \
\ [třídy omezující vlastnosti](../standard-library/locale-class.md#facet_class)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
