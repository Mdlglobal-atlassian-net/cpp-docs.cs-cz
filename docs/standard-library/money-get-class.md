---
title: money_get – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
dev_langs:
- C++
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cae819ccffae37ca27d1e062ae9a766e7acba1f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201748"
---
# <a name="moneyget-class"></a>money_get – třída

Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu `CharType` na finanční hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
 Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*InputIterator*<br/>
 Typ iterátoru, ze kterého funkce get čtou svůj vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[money_get](#money_get)|Konstruktor pro objekty typu `money_get` , který slouží k extrakci číselných hodnot ze sekvencí představujících peněžní hodnoty.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje vstupní iterátor.|
|[STRING_TYPE](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_get](#do_get)|Virtuální funkce volaná k extrakci číselné hodnoty ze sekvence znaků, která představuje peněžní hodnotu.|
|[get](#get)|Extrahuje číselnou hodnotu ze sekvence znaků, která představuje peněžní hodnotu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="char_type"></a>  money_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *CharType*.

## <a name="do_get"></a>  money_get::do_get

Virtuální funkce volaná k extrahuje číselnou hodnotu ze sekvence znaků, která představuje finanční hodnotu.

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

*první*<br/>
 Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*<br/>
 Vstupní iterátor adresující konec sekvence má být převeden.

*Intl*<br/>
 Logická hodnota označující typ symbolu měny očekávání v pořadí: **true** pokud mezinárodní **false** Pokud domácí.

*iosbase*<br/>
 Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinný.

*Stav*<br/>
 Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda operace proběhla úspěšně nebo ne.

*Val*<br/>
 Řetězec převedený pořadí ukládání.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek mimo peněžní vstupní pole.

### <a name="remarks"></a>Poznámky

První chráněná virtuální členská funkce se pokusí porovnat sekvenční začínající na první v pořadí elementů [ `first`, `last`) dokud rozpoznal kompletní, není prázdný peněžní vstupní pole. Pokud úspěšné, převede toto pole na řadu jeden nebo více desítkových číslic, může volitelně předcházet znaménko minus ( `-`), k reprezentaci velikost a uloží výsledek v [string_type](#string_type) objekt *val*. Vrátí iterátor určení prvního prvku mimo peněžní vstupní pole. Jinak, uloží funkce k prázdné sekvenci v *val* a nastaví `ios_base::failbit` v *stavu*. Vrátí iterátor určení prvního prvku mimo jakoukoli předponu platné peněžní vstupní pole. V obou případech, pokud je návratová hodnota `last`, funkce nastaví `ios_base::eofbit` v `State`.

Druhá chráněná virtuální členská funkce se chová stejně jako první, s tím rozdílem, že v případě úspěšného ověření převádí na hodnotu typu pořadí číslo se znaménkem. volitelně **long double** a uloží hodnotu v *val*.

Formát vstupního závisí [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)**fac** vrácený voláním efektivní [use_facet](../standard-library/locale-functions.md#use_facet)  <  [ moneypunct –](../standard-library/moneypunct-class.md) \< **CharType**, **intl**>> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)).

Konkrétně:

- **FAC**. [neg_format –](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve kterém dojde k součásti pole.

- **FAC**. [curr_symbol –](../standard-library/moneypunct-class.md#curr_symbol) určuje pořadí prvků, který představuje symbol měny.

- **FAC**. [positive_sign –](../standard-library/moneypunct-class.md#positive_sign) určuje pořadí prvků, který představuje kladné znaménko.

- **FAC**. [negative_sign –](../standard-library/moneypunct-class.md#negative_sign) určuje pořadí prvků, který představuje záporným znaménkem.

- **FAC**. [seskupení](../standard-library/moneypunct-class.md#grouping) určuje způsob seskupení číslic vlevo od desetinné čárky.

- **FAC**. [thousands_sep –](../standard-library/moneypunct-class.md#thousands_sep) určuje prvek, který odděluje skupin číslic nalevo od desetinné čárky.

- **FAC**. [decimal_point –](../standard-library/moneypunct-class.md#decimal_point) určuje prvek, který odděluje celá čísla od číslic zlomku.

- **FAC**. [frac_digits –](../standard-library/moneypunct-class.md#frac_digits) určuje počet významných zlomek číslic vpravo od každé desetinné čárky. Při analýze peněžní hodnotu s více zlomek číslic, než jsou volány pro `frac_digits`, `do_get` zastaví parsování po spotřebování maximálně `frac_digits` znaků.

Pokud řetězec znak ( **fac**. `negative_sign` nebo **fac**. `positive_sign`) má více než jeden element, pouze první prvek je nalezena shoda s kde element rovna **money_base::sign** se zobrazí ve formátu vzoru ( **fac**. `neg_format`). Všechny zbývající prvky jsou porovnány na konci peněžní vstupní pole. Pokud žádný řetězec má první prvek, který odpovídá další prvek v poli vstupní peněžní, znak řetězec se používá jako prázdný a je kladné znaménko.

Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) nenulové, řetězec **fac**. `curr_symbol` kde se musí shodovat prvek s hodnotou **money_base::symbol** se zobrazí ve formátu vzoru. Jinak, pokud **money_base::symbol** dochází na konci formátovací vzor, a pokud žádné elementy, řetězce přihlašování i nadále odpovídat, symbol měny, se neshoduje. V opačném případě je volitelně odpovídající symbol měny.

Pokud žádné instance **fac**. `thousands_sep` v části hodnoty peněžní vstupní pole dojde k (kde prvek s hodnotou **money_base::value** se zobrazí v vzorek formátu), se nevyžaduje žádná omezení seskupení. V opačném případě technologie nevyžaduje žádná omezení seskupení **fac**. **seskupení** bude vynucovat. Všimněte si, že pro výsledné pořadí číslice představuje celé číslo, jehož nižšího řádu **fac**. `frac_digits` vpravo od desetinné čárky jsou považovány za desítkové číslice.

Libovolné prázdné místo je nalezena shoda s kde element rovna **money_base::space** se zobrazí ve formátu vzoru, pokud se objeví jiné než na konci vzorku formátu. V opačném případě je neodpovídají žádná vnitřní prázdné znaky. Element *ch* je považován za prázdný znak, pokud [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md) \< **CharType**>> () **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)). [je](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) je **true**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [získat](#get), který volá `do_get`.

## <a name="get"></a>  money_get::Get

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

*první*<br/>
 Vstupní iterátor adresující začátek sekvence má být převeden.

*poslední*<br/>
 Vstupní iterátor adresující konec sekvence má být převeden.

*Intl*<br/>
 Logická hodnota označující typ symbolu měny očekávání v pořadí: **true** pokud mezinárodní **false** Pokud domácí.

*iosbase*<br/>
 Příznak formátu, který při nastavení znamená, že symbol měny je volitelná. v opačném případě je povinné

*Stav*<br/>
 Nastaví prvky odpovídající bitové masky pro stav datového proudu podle Určuje, zda byla operace úspěšná.

*Val*<br/>
 Řetězec převedený pořadí ukládání.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek mimo peněžní vstupní pole.

### <a name="remarks"></a>Poznámky

Obě členské funkce vrátí [do_get –](#do_get)`(first, last, Intl, Iosbase, State, val)`.

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

## <a name="iter_type"></a>  money_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **InputIterator**.

## <a name="money_get"></a>  money_get::money_get

Konstruktor pro objekty typu `money_get` , který slouží k extrakci číselných hodnot ze sekvencí představujících peněžní hodnoty.

```cpp
explicit money_get(size_t _Refs = 0);
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

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(*_Refs*).

## <a name="string_type"></a>  money_get::STRING_TYPE

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[facet – třída](../standard-library/locale-class.md#facet_class)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
