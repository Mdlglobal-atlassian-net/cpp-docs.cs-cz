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
ms.openlocfilehash: c0984c15e2bf1682fc902264f47f340d0bd3c859
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472758"
---
# <a name="numget-class"></a>num_get – třída

Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu `CharType` na číselné hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*InputIterator*<br/>
Typ iterátoru, ze kterého číselné funkce get čtou svůj vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[num_get](#num_get)|Konstruktor pro objekty typu `num_get` , který slouží k extrakci číselných hodnot ze sekvencí.|

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

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="char_type"></a>  num_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="do_get"></a>  num_get::do_get

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

*první*<br/>
Začátek rozsahu znaků ze kterého se má přečíst číslo.

*poslední*<br/>
Konec rozsahu znaků od kterého se mají číst číslo.

*_Iosbase*<br/>
[Ios_base –](../standard-library/ios-base-class.md) jehož příznaky jsou používány převodu.

*_Stavu*<br/>
Stav, který má které failbit (naleznete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) se přidá nebude úspěšná.

*Val*<br/>
Hodnota, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor, jakmile byla načtena hodnota.

### <a name="remarks"></a>Poznámky

První chráněná virtuální členská funkce

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```

Porovná sekvenční prvky počínaje *první* v sekvenci `[first, last)` dokud rozpoznal kompletní, prázdný celé číslo vstupní pole. Pokud úspěšné, převede toto pole na její ekvivalentní hodnotu jako typ **dlouhé**a uloží výsledek v *val*. Vrátí iterátor určení prvního prvku mimo číselné vstupní pole. V opačném případě funkce ukládá ustanovení *val* a nastaví `ios_base::failbit` v `state`. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu platné celé číslo vstupní pole. V obou případech, pokud je návratová hodnota `last`, funkce nastaví `ios_base::eofbit` v `state`.

Vstupní pole celé číslo je převedeno stejnými pravidly, používá funkce kontroly pro porovnávání a převod řadu **char** elementy ze souboru. (Každý například **char** element předpokládá, že je mapují na odpovídající element typu `Elem` tak jednoduchý, 1: 1, mapování.) Specifikace ekvivalentní kontrolu převodu je stanoven následujícím způsobem:

Pokud `iosbase.` [ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), je specifikace převodu `lo`.

Pokud `iosbase.flags() & ios_base::basefield == ios_base::` [hex](../standard-library/ios-functions.md#hex), je specifikace převodu `lx`.

Pokud `iosbase.flags() & ios_base::basefield == 0`, je specifikace převodu `li`.

V opačném případě je specifikace převodu `ld`.

Formát vstupního pole celé číslo další určené [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class) `fac` vrácený voláním [use_facet](../standard-library/locale-functions.md#use_facet) `<` [numpunct –](../standard-library/numpunct-class.md) `<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. Konkrétně:

`fac.` [numpunct::Grouping](../standard-library/numpunct-class.md#grouping) `()` určuje způsob seskupení číslic vlevo od desetinné čárky

`fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` Určuje sekvenci, která odděluje skupin číslic nalevo od desetinné čárky.

Pokud žádné instance `fac.thousands_sep()` vyskytují v číselné vstupní pole, se nevyžaduje žádná omezení seskupení. V opačném případě technologie nevyžaduje žádná omezení seskupení `fac.grouping()` vynucují a oddělovače jsou odebrány, než dojde k převodu kontroly.

Čtvrtý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

chová se stejně jako první, s tím rozdílem, že ji nahradí specifikace převodu z `ld` s `lu`. Pokud úspěšně převede číselné vstupní pole na hodnotu typu **unsigned long** a uloží hodnotu v *val*.

Pátý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```

chová se stejně jako první, s tím rozdílem, že ji nahradí specifikace převodu z `ld` s `lld`. Pokud úspěšně převede číselné vstupní pole na hodnotu typu **long long** a uloží hodnotu v *val*.

Šestý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```

chová se stejně jako první, s tím rozdílem, že ji nahradí specifikace převodu z `ld` s `llu`. Pokud úspěšně převede číselné vstupní pole na hodnotu typu **unsigned long long.** a uloží hodnotu v *val*.

Sedmý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```

chová se stejně jako první, s tím rozdílem, že ho endeavors tak, aby odpovídaly prázdný, kompletní s plovoucí desetinnou čárkou vstupní pole. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` Určuje sekvenci, která odděluje celá čísla od číslic zlomku. Je ekvivalentní kontroly specifikátoru převodu `lf`.

Osmého chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

chová se stejně jako první, s tím rozdílem, že ho endeavors tak, aby odpovídaly prázdný, kompletní s plovoucí desetinnou čárkou vstupní pole. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point) `()` Určuje sekvenci, která odděluje celá čísla od číslic zlomku. Je ekvivalentní kontroly specifikátoru převodu `lf`.

Devátý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

chová se stejně jako osmou, s tím rozdílem, že je kontrola ekvivalentní specifikátoru převodu `Lf`.

Desátý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

se chová stejně první, s tím rozdílem, že je kontrola ekvivalentní specifikátoru převodu `p`.

Poslední chráněná (eleventh) virtuální členská funkce:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

chová se stejně jako první, s tím rozdílem, že ho endeavors tak, aby odpovídaly prázdný, kompletní logické vstupní pole. Pokud úspěšně převede vstupní pole logickou hodnotu typu **bool** a uloží hodnotu v *val*.

Vstupní pole Boolean má jednu z těchto dvou tvarů. Pokud `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) má hodnotu false, je stejný jako vstupní pole celé číslo, s tím rozdílem, že převedená hodnota musí být 0 (false) nebo 1 (pravda). V opačném pořadí musí odpovídat buď `fac.` [numpunct::falsename](../standard-library/numpunct-class.md#falsename) `()` (pro false), nebo `fac.` [numpunct::truename](../standard-library/numpunct-class.md#truename) `()` (pro hodnotu PRAVDA).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [získat](#get), kde je virtuální členská funkce volána `do_get`.

## <a name="get"></a>  num_get::Get

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

*první*<br/>
Začátek rozsahu znaků ze kterého se má přečíst číslo.

*poslední*<br/>
Konec rozsahu znaků od kterého se mají číst číslo.

*_Iosbase*<br/>
[Ios_base –](../standard-library/ios-base-class.md) jehož příznaky jsou používány převodu.

*_Stavu*<br/>
Stav, který má které failbit (naleznete v tématu [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) se přidá nebude úspěšná.

*Val*<br/>
Hodnota, která byla načtena.

### <a name="return-value"></a>Návratová hodnota

Iterátor, jakmile byla načtena hodnota.

### <a name="remarks"></a>Poznámky

Vrátí všechny členské funkce [do_get –](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`).

První chráněná virtuální členská funkce se pokusí porovnat sekvenční začínající na první v pořadí elementů [ `first`, `last`) dokud rozpoznal kompletní, prázdný celé číslo vstupní pole. Pokud úspěšné, převede toto pole na její ekvivalentní hodnotu jako typ **dlouhé** a uloží výsledek v *val*. Vrátí iterátor určení prvního prvku mimo číselné vstupní pole. V opačném případě funkce ukládá ustanovení *val* a nastaví `ios_base::failbit` v _ *stavu*. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu platné celé číslo vstupní pole. V obou případech, pokud je návratová hodnota *poslední*, funkce nastaví `ios_base::eofbit` v *_stavu*.

Vstupní pole celé číslo je převedeno stejnými pravidly, používá funkce kontroly pro porovnávání a převod řadu **char** elementy ze souboru. Každé takové **char** element předpokládá, že je mapují na odpovídající element typu `CharType` mapováním jednoduché, 1: 1. Specifikace ekvivalentní kontrolu převodu je stanoven následujícím způsobem:

- Pokud `iosbase`. [příznaky](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct), je specifikace převodu `lo`.

- Pokud **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex), je specifikace převodu `lx`.

- Pokud **iosbase.flags** & **ios_base::basefield** == 0, je specifikace převodu `li`.

- V opačném případě je specifikace převodu `ld`.

Formát vstupního pole celé číslo další určené [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)**fac** vrácený voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct – ](../standard-library/numpunct-class.md) \< **Elem**> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)). Konkrétně:

- **FAC**. [seskupení](../standard-library/numpunct-class.md#grouping) určuje způsob seskupení číslic vlevo od desetinné čárky.

- **FAC**. [thousands_sep –](../standard-library/numpunct-class.md#thousands_sep) Určuje sekvenci, která odděluje skupin číslic nalevo od desetinné čárky.

Pokud žádné instance **fac**. `thousands_sep` Probíhá číselné vstupní pole, se nevyžaduje žádná omezení seskupení. V opačném případě technologie nevyžaduje žádná omezení seskupení **fac**. **seskupení** se nevynutí a oddělovače jsou odebrány, než dojde k převodu kontroly.

Chráněná virtuální členská funkce second:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

chová se stejně jako první, s tím rozdílem, že ji nahradí specifikace převodu z `ld` s `lu`. Pokud úspěšné, převede číselné vstupní pole na hodnotu typu **unsigned long** a uloží hodnotu v *val*.

Třetí chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

chová se stejně jako první, s tím rozdílem, pokusí se vyhledat prázdný, kompletní s plovoucí desetinnou čárkou vstupní pole. **FAC**. [decimal_point –](../standard-library/numpunct-class.md#decimal_point) Určuje sekvenci, která odděluje celá čísla od číslic zlomku. Je ekvivalentní kontroly specifikátoru převodu `lf`.

Čtvrtý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

se chová stejně třetí, s tím rozdílem, že je kontrola ekvivalentní specifikátoru převodu `Lf`.

Pátý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

se chová stejně první, s tím rozdílem, že je kontrola ekvivalentní specifikátoru převodu `p`.

Šestý chráněná virtuální členská funkce:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

chová se stejně jako první, s tím rozdílem, pokusí se vyhledat prázdný, kompletní logické vstupní pole. Pokud úspěšně převede vstupní pole logickou hodnotu typu **bool** a uloží hodnotu v *val*.

Vstupní pole boolean má jednu z těchto dvou tvarů. Pokud **iosbase**. **příznaky** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) je **false**, je stejný jako vstupní pole celé číslo, s tím rozdílem, že převedená hodnota musí být buď 0 (pro **false** ) nebo 1 (pro **true**). V opačném pořadí musí odpovídat buď **fac**. [falsename –](../standard-library/numpunct-class.md#falsename) (pro **false**), nebo **fac**. [truename –](../standard-library/numpunct-class.md#truename) (pro **true**).

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

## <a name="iter_type"></a>  num_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `InputIterator`.

## <a name="num_get"></a>  num_get::num_get

Konstruktor pro objekty typu `num_get` , který slouží k extrakci číselných hodnot ze sekvencí.

```cpp
explicit num_get(size_t _Refs = 0);
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

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[facet – třída](../standard-library/locale-class.md#facet_class)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
