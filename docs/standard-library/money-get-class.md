---
title: money_get – třída | Microsoft Docs
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
ms.openlocfilehash: 1e3059a4291d21e11304fdf571d2e12828df26fb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861698"
---
# <a name="moneyget-class"></a>money_get – třída

Šablony třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převody pořadí typu `CharType` peněžní hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ v rámci programu použitá ke kódování znaků v národním prostředí.

`InputIterator` Typ iterator, ze kterého funkce get, přečtěte si jejich vstup.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[money_get](#money_get)|V konstruktoru pro objekty typu `money_get` , se používají k získání číselné hodnoty z pořadí představující peněžní hodnoty.|

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

**Namespace:** – std

## <a name="char_type"></a>  money_get::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="do_get"></a>  money_get::do_get

Virtuální funkce volat za účelem extrahuje číselnou hodnotu z posloupnost znaků, který představuje peněžní hodnota.

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

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`Intl` Logická hodnota označující typ symbolu měny v sekvenci byl očekáván: **true** pokud mezinárodní, **false** Pokud příslušné.

`Iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je vyžadována.

`State` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná či nikoli.

`val` Řetězec převedený pořadí ukládání.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec peněžní vstupní pole.

### <a name="remarks"></a>Poznámky

První virtuální chráněného člena funkce se pokusí vyhledat sekvenční elementy začínající na první v pořadí [ `first`, `last`) dokud má rozpoznána úplná, neprázdná peněžní vstupní pole. Pokud úspěšné, převede ji toto pole do pořadí jeden nebo více desítkových číslic, volitelně uvozená znakem minus ( `-`), výši a ukládá výsledky v [string_type](#string_type) objekt `val`. Vrátí iterovat určení první prvek nad rámec peněžní vstupní pole. Jinak bude uložena v prázdné sekvenci `val` a nastaví `ios_base::failbit` v `State`. Vrátí iterovat určení první prvek nad rámec všechny předpony platné peněžní vstupní pole. V obou případech, pokud se rovná návratovou hodnotu `last`, nastaví funkce `ios_base::eofbit` v `State`.

Druhý virtuální chráněného člena funkce se chová stejně jako první, s tím rozdílem, že v případě úspěšného převádí na hodnotu typu pořadí číslo se znaménkem. volitelně `long double` a uloží tuto hodnotu v `val`.

Formát peněžní vstupní pole je dáno [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)**fac** vrácený efektivní volání [use_facet](../standard-library/locale-functions.md#use_facet)  <  [ moneypunct](../standard-library/moneypunct-class.md) \< **CharType**, **mezinárodní**>> ( **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)).

Konkrétně:

- **FAC**. [neg_format –](../standard-library/moneypunct-class.md#neg_format) určuje pořadí, ve kterém dojde k součásti pole.

- **FAC**. [curr_symbol –](../standard-library/moneypunct-class.md#curr_symbol) určuje pořadí prvků, které se považuje za symbolu měny.

- **FAC**. [positive_sign –](../standard-library/moneypunct-class.md#positive_sign) určuje pořadí prvků, které se považuje za znaménkem kladná.

- **FAC**. [negative_sign –](../standard-library/moneypunct-class.md#negative_sign) určuje pořadí prvků, které se považuje za znaménkem záporné.

- **FAC**. [seskupování](../standard-library/moneypunct-class.md#grouping) určuje způsob seskupení číslic nalevo od všech desetinné čárky.

- **FAC**. [thousands_sep –](../standard-library/moneypunct-class.md#thousands_sep) určuje element, který odděluje skupiny číslic nalevo od všech desetinné čárky.

- **FAC**. [decimal_point –](../standard-library/moneypunct-class.md#decimal_point) určuje element, který odděluje číslic celé číslo od zlomek číslic.

- **FAC**. [frac_digits –](../standard-library/moneypunct-class.md#frac_digits) určuje počet číslic významné zlomek napravo od všech desetinné čárky. Při analýze peněžní částka s více zlomek číslic, než jsou volány pro `frac_digits`, `do_get` zastaví Analýza po spotřebování maximálně `frac_digits` znaků.

Pokud řetězec přihlašovací ( **fac**. `negative_sign` nebo **fac**. `positive_sign`) má více než jeden element pouze první prvek je shodný, kde element rovna **money_base::sign** se zobrazí ve formátu vzoru ( **fac**. `neg_format`). Na konci peněžní vstupní pole se splní všechny zbývající elementy. Pokud ani řetězec má první prvek, který odpovídá na další prvek v peněžním vstupní pole, nebyla provedena jako prázdný řetězec přihlášení a přihlášení je kladné.

Pokud **iosbase**. [příznaky](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) nenulový, řetězec **fac**. `curr_symbol` kde se musí shodovat rovna element **money_base::symbol** se zobrazí ve formátu vzoru. Jinak Pokud **money_base::symbol** dojde na konci tohoto vzoru formátu a pokud žádné elementy řetězce přihlašovací zůstanou lze porovnat, není shodná symbolu měny. Jinak je volitelně odpovídající symbolu měny.

Pokud žádné instance **fac**. `thousands_sep` v části hodnota peněžní vstupní pole dojde k (kde rovna element **money_base::value** se zobrazí ve formátu vzoru), se nevyžaduje žádná omezení seskupení. Jinak, nevyžaduje žádná omezení seskupení **fac**. **seskupování** je vynucená. Poznámka: představuje výsledné pořadí číslice celé jejichž nejnižší **fac**. `frac_digits` jsou považovány za desetinných číslic vpravo od desetinné čárky.

Libovolné prázdné místo je nalezena shoda s kde rovna element **money_base::space** se zobrazí ve formátu vzoru, pokud se zobrazí, jiné než na konci tohoto vzoru formátu. Jinak je neodpovídají žádné interní mezer. Element *ch* je považován za prázdné znaky, pokud [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md) \< **CharType**>> () **iosbase**. [getloc –](../standard-library/ios-base-class.md#getloc)). [je](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) je **true**.

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

`first` Vstupní iterator adresování na začátek pořadí má být převeden.

`last` Vstupní iterator adresování konci pořadí má být převeden.

`Intl` Logická hodnota označující typ symbolu měny v sekvenci byl očekáván: **true** pokud mezinárodní, **false** Pokud příslušné.

`Iosbase` Příznak formátu, který při sadu označuje, že symbolu měny je volitelná. jinak je požadováno

`State` Nastaví prvky příslušné bitové masky pro datový proud stav podle zda operace byla úspěšná.

`val` Řetězec převedený pořadí ukládání.

### <a name="return-value"></a>Návratová hodnota

Vstupní iterovat adresování první prvek nad rámec peněžní vstupní pole.

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

V konstruktoru pro objekty typu `money_get` , se používají k získání číselné hodnoty z pořadí představující peněžní hodnoty.

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Celočíselná hodnota určuje typ správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty `_Refs` parametrů a jejich významu jsou:

- 0: doba života objektu spravuje národní prostředí, které je obsahují.

- 1: doba života objektu, se musí ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je možné, protože je chráněn destruktoru.

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(**_ *** odolný systém souborů*).

## <a name="string_type"></a>  money_get::STRING_TYPE

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Popisuje typ specializace šablon třídy [basic_string](../standard-library/basic-string-class.md).

## <a name="see-also"></a>Viz také

[\<národní prostředí >](../standard-library/locale.md)<br/>
[facet – třída](../standard-library/locale-class.md#facet_class)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
