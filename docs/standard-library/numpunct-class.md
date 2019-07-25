---
title: numpunct – třída
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct
- xlocnum/std::numpunct::char_type
- xlocnum/std::numpunct::string_type
- xlocnum/std::numpunct::decimal_point
- xlocnum/std::numpunct::do_decimal_point
- xlocnum/std::numpunct::do_falsename
- xlocnum/std::numpunct::do_grouping
- xlocnum/std::numpunct::do_thousands_sep
- xlocnum/std::numpunct::do_truename
- xlocnum/std::numpunct::falsename
- xlocnum/std::numpunct::grouping
- xlocnum/std::numpunct::thousands_sep
- xlocnum/std::numpunct::truename
helpviewer_keywords:
- std::numpunct [C++]
- std::numpunct [C++], char_type
- std::numpunct [C++], string_type
- std::numpunct [C++], decimal_point
- std::numpunct [C++], do_decimal_point
- std::numpunct [C++], do_falsename
- std::numpunct [C++], do_grouping
- std::numpunct [C++], do_thousands_sep
- std::numpunct [C++], do_truename
- std::numpunct [C++], falsename
- std::numpunct [C++], grouping
- std::numpunct [C++], thousands_sep
- std::numpunct [C++], truename
ms.assetid: 73fb93cc-ac11-4c98-987c-bfa6267df596
ms.openlocfilehash: c23f23172894ce0b5adcbff1d2db58c78caf7a03
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454186"
---
# <a name="numpunct-class"></a>numpunct – třída

Třída šablony popisující objekt, který může sloužit jako místní omezující vlastnost k popisu sekvencí typu `CharType` používaného k reprezentaci informací o formátování a interpunkci číselných a logických výrazů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[numpunct](#numpunct)|Konstruktor pro objekty typu `numpunct`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[decimal_point](#decimal_point)|Vrátí prvek specifický pro národní prostředí, který se použije jako desetinná čárka.|
|[do_decimal_point](#do_decimal_point)|Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako desetinná čárka.|
|[do_falsename](#do_falsename)|Chráněná virtuální členská funkce, která je volána k vrácení řetězce, který má být použit jako textová reprezentace hodnoty **false**.|
|[do_grouping](#do_grouping)|Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.|
|[do_thousands_sep](#do_thousands_sep)|Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako oddělovač tisíců.|
|[do_truename](#do_truename)|Chráněná virtuální členská funkce, která je volána k vrácení řetězce, který má být použit jako textová reprezentace hodnoty **true**.|
|[hodnota false](#falsename)|Vrátí řetězec, který má být použit jako textová reprezentace hodnoty **false**.|
|[sloučení](#grouping)|Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.|
|[thousands_sep](#thousands_sep)|Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.|
|[hodnota true](#truename)|Vrátí řetězec, který má být použit jako textová reprezentace hodnoty **true**.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="char_type"></a>numpunct:: char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType.**

## <a name="decimal_point"></a>numpunct::d ecimal_point

Vrátí prvek specifický pro národní prostředí, který se použije jako desetinná čárka.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se použije jako desetinná čárka.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Příklad

```cpp
// numpunct_decimal_point.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet <numpunct <char> >( loc);
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="do_decimal_point"></a>numpunct::d o_decimal_point

Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako desetinná čárka.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se použije jako desetinná čárka.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [decimal_point](#decimal_point), kde je virtuální členská funkce volána `decimal_point`nástrojem.

## <a name="do_falsename"></a>numpunct::d o_falsename

Chráněná virtuální členská funkce vrátí sekvenci, která se použije jako textová reprezentace hodnoty **false**.

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující sekvenci, která má být použita jako textová reprezentace hodnoty **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec "false", který bude reprezentovat hodnotu **false** ve všech národních prostředích.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [hodnotu false](#falsename), kde je virtuální členská funkce volána `falsename`nástrojem.

## <a name="do_grouping"></a>numpunct::d o_grouping

Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro určení, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce, která vrátí pravidlo specifické pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky. Kódování je stejné jako pro **lconv:: Grouping**.

### <a name="example"></a>Příklad

Podívejte se na příklad [seskupení](#grouping), kde je virtuální členská funkce volána nástrojem `grouping`.

## <a name="do_thousands_sep"></a>numpunct::d o_thousands_sep

Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako oddělovač tisíců.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí prvek specifický pro národní prostředí typu `CharType` , který se použije jako oddělovač skupin nalevo od libovolné desetinné čárky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [thousands_sep](#thousands_sep), kde je virtuální členská funkce volána `thousands_sep`nástrojem.

## <a name="do_truename"></a>numpunct::d o_truename

Chráněná virtuální členská funkce, která je volána k vrácení řetězce, který má být použit jako textová reprezentace hodnoty **true**.

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>Poznámky

Řetězec, který má být použit jako textová reprezentace hodnoty **true**.

Všechna národní prostředí vrátí řetězec "true", který bude představovat hodnotu **true**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [hodnotu true](#truename), kde je virtuální členská funkce volána `truename`nástrojem.

## <a name="falsename"></a>numpunct:: false

Vrátí řetězec, který má být použit jako textová reprezentace hodnoty **false**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující sekvenci `CharType`s pro použití jako text reprezentace hodnoty **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec "false", který bude reprezentovat hodnotu **false** ve všech národních prostředích.

Členská funkce vrátí [do_falsename](#do_falsename).

### <a name="example"></a>Příklad

```cpp
// numpunct_falsename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct <char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2( "French" );
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >(loc2);
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="grouping"></a>numpunct:: Grouping

Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro určení, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_grouping](#do_grouping).

### <a name="example"></a>Příklad

```cpp
// numpunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany");

   const numpunct <char> &npunct =
       use_facet < numpunct <char> >( loc );
   for (unsigned int i = 0; i < npunct.grouping( ).length( ); i++)
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(npunct.grouping ( )[i])
           << endl;
   }
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
```

## <a name="numpunct"></a>numpunct:: numpunct

Konstruktor pro objekty typu `numpunct`.

```cpp
explicit numpunct(size_t _Refs = 0);
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

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="string_type"></a>numpunct:: string_type

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci třídy šablony [basic_string](../standard-library/basic-string-class.md) , jejíž objekty mohou ukládat kopie sekvencí interpunkce.

## <a name="thousands_sep"></a>numpunct:: thousands_sep

Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Příklad

```cpp
// numpunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const numpunct <char> &npunct =
   use_facet < numpunct < char > >( loc );
   cout << loc.name( ) << " decimal point "<<
   npunct.decimal_point( ) << endl;
   cout << loc.name( ) << " thousands separator "
   << npunct.thousands_sep( ) << endl;
};
```

```Output
German_Germany.1252 decimal point ,
German_Germany.1252 thousands separator .
```

## <a name="truename"></a>numpunct:: true

Vrátí řetězec, který má být použit jako textová reprezentace hodnoty **true**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který má být použit jako textová reprezentace hodnoty **true**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_truename](#do_truename).

Všechna národní prostředí vrátí řetězec "true", který bude představovat hodnotu **true**.

### <a name="example"></a>Příklad

```cpp
// numpunct_truename.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "English" );

   const numpunct < char> &npunct = use_facet <numpunct <char> >( loc );
   cout << loc.name( ) << " truename "<< npunct.truename( ) << endl;
   cout << loc.name( ) << " falsename "<< npunct.falsename( ) << endl;

   locale loc2("French");
   const numpunct <char> &npunct2 = use_facet <numpunct <char> >( loc2 );
   cout << loc2.name( ) << " truename "<< npunct2.truename( ) << endl;
   cout << loc2.name( ) << " falsename "<< npunct2.falsename( ) << endl;
}
```

```Output
English_United States.1252 truename true
English_United States.1252 falsename false
French_France.1252 truename true
French_France.1252 falsename false
```

## <a name="see-also"></a>Viz také:

[\<> národního prostředí](../standard-library/locale.md)\
[Face – třída](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
