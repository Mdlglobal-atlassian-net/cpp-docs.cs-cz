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
ms.openlocfilehash: eb5e1a7b83db561687f83be96c79add8b54589e8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455559"
---
# <a name="moneyget-class"></a>money_get – třída

Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů sekvencí typu `CharType` na peněžní hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

*InputIterator*\
Typ iterátoru, ze kterého funkce get čtou svůj vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[money_get](#money_get)|Konstruktor pro objekty typu `money_get` , které slouží k extrakci číselných hodnot ze sekvencí představujících peněžní hodnoty.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[iter_type](#iter_type)|Typ, který popisuje vstupní iterátor.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_get](#do_get)|Virtuální funkce volaná k extrakci číselné hodnoty ze sekvence znaků, která představuje peněžní hodnotu.|
|[get](#get)|Extrahuje číselnou hodnotu ze sekvence znaků, která představuje peněžní hodnotu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="char_type"></a>money_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *CharType*.

## <a name="do_get"></a>money_get::d o_get

Virtuální funkce volaná k extrakci číselné hodnoty ze sekvence znaků, která představuje peněžní hodnotu.

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

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*posledního*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*Mezinárodních*\
Logická hodnota označující typ symbolu měny očekávaný v sekvenci: **true** , pokud mezinárodní, **false** , pokud je tuzemsko.

*Iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

*Státech*\
Nastaví příslušné prvky maskování dat pro stav datového proudu podle toho, zda operace proběhly úspěšně, nebo ne.

*počítává*\
Řetězec, který ukládá převedenou sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za peněžní vstupní pole.

### <a name="remarks"></a>Poznámky

První virtuální chráněná členská funkce se pokusí porovnat sekvenční prvky začínající první v sekvenci [ `first`, `last`), dokud nerozpozná celé neprázdné peněžní vstupní pole. Pokud je to úspěšné, převede toto pole na sekvenci jedné nebo více desítkových číslic, volitelně předchází znaménkem mínus ( `-`), aby představovalo množství a uložil výsledek do objektu [string_type](#string_type) *Val*. Vrátí iterátor, který určuje první prvek za peněžním vstupním polem. V opačném případě funkce ukládá prázdnou sekvenci v *Val* a `ios_base::failbit` nastaví ve *stavu*. Vrátí iterátor určení prvního prvku nad rámec libovolné předpony platného peněžního pole. V obou případech, pokud se návratová hodnota rovná `last`, funkce nastaví `ios_base::eofbit` v `State`.

Druhá funkce Virtual Protected member se chová stejně jako první, s tím rozdílem, že pokud je úspěšná, převede volitelnou posloupnost číslic na hodnotu typu **Long Double** a uloží tuto hodnotu do pole *Val*.

Formát peněžního vstupního pole je určen**FAC** [omezujícími vlastnostmi národního prostředí](../standard-library/locale-class.md#facet_class)vráceným efektivním voláním [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **Intl**> > ( **iosbase** . [getloc](../standard-library/ios-base-class.md#getloc)).

Určen

- **FAC**. [neg_format](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve kterém se vyskytují komponenty pole.

- **FAC**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) Určuje sekvenci prvků, které tvoří symbol měny.

- **FAC**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) Určuje sekvenci prvků, které tvoří kladné znaménko.

- **FAC**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) Určuje sekvenci prvků, které tvoří záporné znaménko.

- **FAC**. [seskupení](../standard-library/moneypunct-class.md#grouping) určuje, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

- **FAC**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) určuje prvek, který odděluje skupiny číslic nalevo od libovolné desetinné čárky.

- **FAC**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) určuje prvek, který odděluje celočíselné číslice od číslic zlomku.

- **FAC**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) určuje počet významných číslic zlomku napravo od desetinné čárky. Při analýze peněžních částek s více číslicemi zlomků, než jsou `frac_digits`volány nástrojem, `do_get` zastaví `frac_digits` analýzu po obdobu zpracování maximálně znaků.

Pokud se podepisuje řetězec ( **FAC**. `negative_sign`nebo **FAC**. `positive_sign`) má více než jeden prvek, je porovnán pouze první prvek, kde se element EQUAL by **money_base:: Sign** ve vzoru Format ( **FAC**. `neg_format`). Všechny zbývající prvky se shodují na konci pole peněžního vstupu. Pokud žádný z řetězců nemá první prvek, který se shoduje s dalším prvkem v poli peněžního vstupu, znaménko se přiřadí jako prázdné a znaménko je kladné.

IF **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) jsou nenulové, řetězec **FAC**. `curr_symbol`musí odpovídat umístění, kde se ve vzoru formátu zobrazí element EQUAL by **money_base:: symbol** . V opačném případě, pokud **money_base:: symbol** probíhá na konci vzoru formátu a pokud žádné prvky řetězce znaménka nadále nejsou porovnány, symbol měny se neshoduje. V opačném případě se symbol měny může volitelně shodovat.

Nejsou-li žádné instance **FAC**. `thousands_sep`nastává se v hodnotě pole peněžního vstupu (kde se element Equal **money_base:: Value** objevuje ve vzoru formátu), není uloženo žádné omezení seskupování. V opačném případě jakákoli omezení seskupení zavedená **FAC**. **seskupování** je vynutilo. Všimněte si, že výsledná sekvence číslic představuje celé číslo, jehož dolní pořadí **FAC**. `frac_digits`desítkové číslice jsou považovány za napravo od desetinné čárky.

K dispozici je libovolné prázdné místo, kde se element, který se rovná **money_base:: Space** , zobrazuje ve vzoru formátu, pokud se zobrazí jako na konci vzoru formátu. V opačném případě se neshodují žádné interní prázdné znaky. Element *ch* se považuje za prázdné místo, pokud [use_facet](../standard-library/locale-functions.md#use_facet) < [CType](../standard-library/ctype-class.md) \< **CharType**> > ( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [je](../standard-library/ctype-class.md#is) ( **ctype_base:: Space**, *ch*) má **hodnotu true**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [Get](#get), která `do_get`volá.

## <a name="get"></a>money_get:: Get

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

*první*\
Vstupní iterátor adresující začátek posloupnosti, která má být převedena.

*posledního*\
Vstupní iterátor adresující konec posloupnosti, která má být převedena.

*Mezinárodních*\
Logická hodnota označující typ symbolu měny očekávaný v sekvenci: **true** , pokud mezinárodní, **false** , pokud je tuzemsko.

*Iosbase*\
Příznak formátu, který po nastavení označuje, že symbol měny je nepovinný; v opačném případě se vyžaduje.

*Státech*\
Nastaví odpovídající prvky maskování pro stav datového proudu podle toho, zda operace proběhla úspěšně.

*počítává*\
Řetězec, který ukládá převedenou sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterátor adresující první prvek za peněžní vstupní pole.

### <a name="remarks"></a>Poznámky

Oba členské funkce vrací [do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`.

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

## <a name="iter_type"></a>money_get::iter_type

Typ, který popisuje vstupní iterátor.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **InputIterator**.

## <a name="money_get"></a>money_get::money_get

Konstruktor pro objekty typu `money_get` , které slouží k extrakci číselných hodnot ze sekvencí představujících peněžní hodnoty.

```cpp
explicit money_get(size_t _Refs = 0);
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

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)( *_Refs*).

## <a name="string_type"></a>  money_get::string_type

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci třídy šablony [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Viz také:

[\<> národního prostředí](../standard-library/locale.md)\
[Face – třída](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
