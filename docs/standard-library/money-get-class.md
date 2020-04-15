---
title: money_get – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: ac85e99bfb834fd970a804269f25ec9f20960a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375904"
---
# <a name="money_get-class"></a>money_get – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního `CharType` prostředí pro řízení převodů posloupností typu na peněžní hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*Vstupní iterátor*\
Typ iterátoru, ze kterého funkce get čtou svůj vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[money_get](#money_get)|Konstruktor pro objekty `money_get` typu, které se používají k extrahování číselné hodnoty z sekvencí představující peněžní hodnoty.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje vstupní iterátor.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky `CharType`typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_get](#do_get)|Virtuální funkce volaná k extrakci číselné hodnoty ze sekvence znaků, která představuje peněžní hodnotu.|
|[get](#get)|Extrahuje číselnou hodnotu ze sekvence znaků, která představuje peněžní hodnotu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="money_getchar_type"></a><a name="char_type"></a>money_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *CharType*.

## <a name="money_getdo_get"></a><a name="do_get"></a>money_get::do_get

Virtuální funkce volána k extrahování číselné hodnoty z posloupnosti znaků, která představuje peněžní hodnotu.

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*Intl*\
Logická hodnota označující typ symbolu měny očekávanév pořadí: **true** if international, **false** if domestic.

*Iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je vyžadována.

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné či nikoli.

*Val*\
Řetězec ukládání převedené sekvence.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek mimo pole peněžního vstupu.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce se pokusí porovnat `first`sekvenční prvky začínající nejprve v sekvenci [ , `last`), dokud nerozpozná úplné, neprázdné peněžní vstupní pole. Pokud je úspěšná, převede toto pole na posloupnost jedné nebo více desetinných míst, které je volitelně předchází znaménko mínus ( `-`), aby reprezentovalo částku a uskladnělo výsledek ve [string_type](#string_type) *objektu val*. Vrátí iterátor určení první prvek mimo pole peněžní vstup. V opačném případě funkce uloží prázdnou `ios_base::failbit` sekvenci ve *val* a sady ve *stavu*. Vrátí iterátor určení první prvek za všechny předpony platné pole peněžní vstup. V obou případech, pokud se `last`vrácená `ios_base::eofbit` hodnota `State`rovná , funkce nastaví v .

Druhá virtuální chráněná členská funkce se chová stejně jako první, s tím rozdílem, že pokud je úspěšná, převede volitelně podepsanou číselnou sekvenci na hodnotu typu **long double** a uloží tuto hodnotu ve *val*.

Formát pole peněžního vstupu je určen [fac národního](../standard-library/locale-class.md#facet_class)**prostředí,** který je vrácen efektivním voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)).

Konkrétně:

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve kterém se vyskytují součásti pole.

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) určuje posloupnost prvků, které tvoří symbol měny.

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) určuje posloupnost prvků, které tvoří kladné znaménko.

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) určuje posloupnost prvků, které tvoří záporné znaménko.

- **fac**. [seskupení](../standard-library/moneypunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od jakékoli desetinné čárky.

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) určuje prvek, který odděluje skupiny číslic nalevo od jakékoli desetinné čárky.

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) určuje prvek, který odděluje celé číslice od dělicích čísel zlomků.

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) určuje počet číslic významného zlomku vpravo od jakékoli desetinné čárky. Při analýzě peněžní částky s více zlomkových `frac_digits` `do_get` číslic, než jsou volány `frac_digits` podle , zastaví analýzu po náročné na většinu znaků.

Pokud znakový řetězec ( **fac**. `negative_sign`nebo **fac**. `positive_sign`) má více než jeden prvek, pouze první prvek je uzavřeno, kde se prvek rovný **money_base::sign** zobrazí ve vzoru formátu ( **fac**. `neg_format`). Všechny zbývající prvky jsou porovnány na konci pole peněžního vstupu. Pokud ani řetězec nemá první prvek, který odpovídá další prvek v poli peněžní vstup, znaménko řetězec je přijata jako prázdný a znaménko je pozitivní.

Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) je nenulová, řetězec **fac**. `curr_symbol`musí odpovídat místu, kde se ve vzorovém formátu zobrazí prvek rovný **money_base::symbol.** V opačném případě, pokud **money_base::symbol** dojde na konci vzoru formátu a pokud žádné prvky znakového řetězce zůstávají odpovídat, symbol měny není spárován. V opačném případě je symbol měny volitelně spárován.

Pokud žádné instance **fac**. `thousands_sep`dojít v hodnotové části pole peněžního vstupu (kde se prvek rovný **money_base::hodnota** zobrazí ve formátu vzoru), není uložena žádná omezení seskupení. V opačném případě všechna omezení seskupení uložená **fac**. **seskupení** je vynuceno. Všimněte si, že výsledná sekvence číslic představuje celé číslo, jehož **fac**nižšího řádu . `frac_digits`desetinná místa se považují za vpravo od desetinné čárky.

Libovolné prázdné místo je porovnáno, kde se prvek rovný **money_base::mezera** zobrazí ve vzoru formátu, pokud se zobrazí jinak než na konci vzoru formátu. V opačném případě není spárováno žádné vnitřní prázdné místo. Element *ch* je považován za prázdné [místo,](../standard-library/locale-functions.md#use_facet) < pokud use_facet[ctype](../standard-library/ctype-class.md) \< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [is](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) je **true**.

### <a name="example"></a>Příklad

Viz příklad pro [get](#get) `do_get`, který volá .

## <a name="money_getget"></a><a name="get"></a>money_get::získat

Extrahuje číselnou hodnotu ze sekvence znaků, která představuje peněžní hodnotu.

```cpp
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```

### <a name="parameters"></a>Parametry

*První*\
Vstupní iterátor adresování začátek sekvence, která má být převedena.

*Poslední*\
Vstupní iterátor adresování konec sekvence, která má být převedena.

*Intl*\
Logická hodnota označující typ symbolu měny očekávanév pořadí: **true** if international, **false** if domestic.

*Iosbase*\
Příznak formátu, který při nastavení označuje, že symbol měny je volitelný; v opačném případě je nutné

*Státu*\
Nastaví příslušné prvky bitové masky pro stav datového proudu podle toho, zda byly operace úspěšné.

*Val*\
Řetězec ukládání převedené sekvence.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek mimo pole peněžního vstupu.

### <a name="remarks"></a>Poznámky

Obě členské funkce vrátí [do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`.

### <a name="example"></a>Příklad

```cpp
// money_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;

int main( )
{
   locale loc( "german_germany" );

   basic_stringstream< char > psz;
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";
   basic_stringstream< char > psz2;
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();

   ios_base::iostate st = 0;
   long double fVal;

   psz.flags( psz.flags( )|ios_base::showbase );
   // Which forced the READING the currency symbol
   psz.imbue(loc);
   use_facet < money_get < char > >( loc ).
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"
           << endl;
   else
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "
           << fVal/100.0 << endl;

   use_facet < money_get < char > >( loc ).
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"
           << endl;
   else
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "
           << fVal/100.0 << endl;
};
```

## <a name="money_getiter_type"></a><a name="iter_type"></a>money_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **InputIterator**.

## <a name="money_getmoney_get"></a><a name="money_get"></a>money_get::money_get

Konstruktor pro objekty `money_get` typu, které se používají k extrahování číselné hodnoty z sekvencí představující peněžní hodnoty.

```cpp
explicit money_get(size_t _Refs = 0);
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

Konstruktor inicializuje svůj základní objekt pomocí **národního prostředí::**[omezující stoodka](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="money_getstring_type"></a><a name="string_type"></a>money_get::string_type

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[fazeta třídy](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
