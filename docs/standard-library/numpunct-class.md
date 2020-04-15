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
ms.openlocfilehash: 0bdd6556df892e5e231919dbc4ae95d14a6f95fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373619"
---
# <a name="numpunct-class"></a>numpunct – třída

Šablona třídy, která popisuje objekt, který může sloužit jako místní `CharType` omezující vlastnost k popisu sekvencí typu, které slouží k reprezentaci informací o formátování a interpunkci číselných a logických výrazů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class numpunct : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků v národním prostředí.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[numpunct](#numpunct)|Konstruktor pro objekty `numpunct`typu .|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky `CharType`typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[decimal_point](#decimal_point)|Vrátí prvek specifický pro národní prostředí, který se použije jako desetinná čárka.|
|[do_decimal_point](#do_decimal_point)|Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako desetinná čárka.|
|[do_falsename](#do_falsename)|Chráněná virtuální členská funkce, která je volána k vrácení řetězce, který má být používán jako textová reprezentace hodnoty **false**.|
|[do_grouping](#do_grouping)|Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.|
|[do_thousands_sep](#do_thousands_sep)|Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako oddělovač tisíců.|
|[do_truename](#do_truename)|Chráněná virtuální členská funkce, která je volána k vrácení řetězce, který má být používán jako textová reprezentace hodnoty **true**.|
|[falsename](#falsename)|Vrátí řetězec, který se má použít jako textová reprezentace hodnoty **false**.|
|[Seskupení](#grouping)|Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.|
|[thousands_sep](#thousands_sep)|Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.|
|[truename](#truename)|Vrátí řetězec, který se má použít jako textová reprezentace hodnoty **true**.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="numpunctchar_type"></a><a name="char_type"></a>numpunct::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **CharType.**

## <a name="numpunctdecimal_point"></a><a name="decimal_point"></a>numpunct::decimal_point

Vrátí prvek specifický pro národní prostředí, který se použije jako desetinná čárka.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se má použít jako desetinná čárka.

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

## <a name="numpunctdo_decimal_point"></a><a name="do_decimal_point"></a>numpunct::do_decimal_point

Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako desetinná čárka.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se má použít jako desetinná čárka.

### <a name="example"></a>Příklad

Viz příklad pro [decimal_point](#decimal_point), kde je `decimal_point`virtuální členská funkce volána .

## <a name="numpunctdo_falsename"></a><a name="do_falsename"></a>numpunct::do_falsename

Chráněná virtuální členská funkce vrátí posloupnost, která se má použít jako textová reprezentace hodnoty **false**.

```cpp
virtual string_type do_falsename() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující posloupnost, která má být používána jako textová reprezentace hodnoty **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec "false" představovat hodnotu **false** ve všech národních prostředích.

### <a name="example"></a>Příklad

Viz příklad [falsename](#falsename), kde je virtuální `falsename`členská funkce volána .

## <a name="numpunctdo_grouping"></a><a name="do_grouping"></a>numpunct::do_grouping

Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro určení způsobu seskupení číslic nalevo od jakékoli desetinné čárky.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce, která vrátí pravidlo specifické pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky. Kódování je stejné jako pro **lconv::grouping**.

### <a name="example"></a>Příklad

Viz příklad pro [seskupení](#grouping), kde virtuální `grouping`členská funkce je volána .

## <a name="numpunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>numpunct::do_thousands_sep

Chráněná virtuální členská funkce, která je volána k vrácení prvku specifického pro národní prostředí, který se použije jako oddělovač tisíců.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí prvek `CharType` typu specifický pro národní prostředí, který se použije jako oddělovač skupiny nalevo od libovolné desetinné čárky.

### <a name="example"></a>Příklad

Viz příklad pro [thousands_sep](#thousands_sep), kde je `thousands_sep`virtuální členská funkce volána .

## <a name="numpunctdo_truename"></a><a name="do_truename"></a>numpunct::do_truename

Chráněná virtuální členská funkce, která je volána k vrácení řetězce, který má být používán jako textová reprezentace hodnoty **true**.

```cpp
virtual string_type do_truename() const;
```

### <a name="remarks"></a>Poznámky

Řetězec, který se má použít jako textová reprezentace hodnoty **true**.

Všechna národní prostředí vrátí řetězec "true" představující hodnotu **true**.

### <a name="example"></a>Příklad

Viz příklad [truename](#truename), kde virtuální členská `truename`funkce je volána .

## <a name="numpunctfalsename"></a><a name="falsename"></a>numpunct::falsename

Vrátí řetězec, který se má použít jako textová reprezentace hodnoty **false**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující posloupnost `CharType`s použít jako text reprezentace hodnoty **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí řetězec "false" představovat hodnotu **false** ve všech národních prostředích.

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

## <a name="numpunctgrouping"></a><a name="grouping"></a>numpunct::seskupení

Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.

```cpp
string grouping() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro určení způsobu seskupení číslic nalevo od jakékoli desetinné čárky.

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

## <a name="numpunctnumpunct"></a><a name="numpunct"></a>numpunct::numpunct

Konstruktor pro objekty `numpunct`typu .

```cpp
explicit numpunct(size_t _Refs = 0);
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

Konstruktor inicializuje svůj základní objekt pomocí **národního prostředí::**[omezující stolku](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="numpunctstring_type"></a><a name="string_type"></a>numpunct::string_type

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) jehož objekty mohou ukládat kopie interpunkčních sekvencí.

## <a name="numpunctthousands_sep"></a><a name="thousands_sep"></a>numpunct::thousands_sep

Vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač tisíců.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se má použít jako oddělovač tisíců.

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

## <a name="numpuncttruename"></a><a name="truename"></a>numpunct::truename

Vrátí řetězec, který se má použít jako textová reprezentace hodnoty **true**.

```cpp
string_type falsename() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec, který se má použít jako textová reprezentace hodnoty **true**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_truename](#do_truename).

Všechna národní prostředí vrátí řetězec "true" představující hodnotu **true**.

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

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[fazeta třídy](../standard-library/locale-class.md#facet_class)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
