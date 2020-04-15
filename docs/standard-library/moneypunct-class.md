---
title: moneypunct – třída
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
ms.openlocfilehash: 3a277b2f97fd53c52b705051c30eb18faf6364d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366250"
---
# <a name="moneypunct-class"></a>moneypunct – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí k popisu sekvencí typu *CharType,* které slouží k reprezentaci pole peněžního vstupu nebo pole peněžního výstupu. Pokud je parametr šablony *Intl* *true*, jsou dodrženy mezinárodní konvence.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků.

*Intl*\
Příznak určující, zda je třeba dodržovat mezinárodní konvence.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložená hodnota ukládá jedinečnou kladnou hodnotu v **id.**

Intl objektu const static object ukládá hodnotu parametru šablony *Intl*.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[moneypunct](#moneypunct)|Konstruktor objektů typu `moneypunct`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky `CharType`typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[curr_symbol](#curr_symbol)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol měny.|
|[decimal_point](#decimal_point)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol desetinné čárky.|
|[do_curr_symbol](#do_curr_symbol)|Chráněná virtuální členská funkce, která vrátí sekvenci prvků specifickou pro národní prostředí, která se použije jako symbol měny.|
|[do_decimal_point](#do_decimal_point)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol desetinné čárky.|
|[do_frac_digits](#do_frac_digits)|Chráněná virtuální členská funkce, která vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od každé desetinné čárky.|
|[do_grouping](#do_grouping)|Chráněná virtuální členská funkce, která vrátí pravidlo specifické pro národní prostředí k určení způsobu seskupení číslic vlevo od desetinné čárky.|
|[do_neg_format](#do_neg_format)|Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů se zápornými částkami.|
|[do_negative_sign](#do_negative_sign)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol záporného znaménka.|
|[do_pos_format](#do_pos_format)|Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů s kladnými částkami.|
|[do_positive_sign](#do_positive_sign)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol kladného znaménka.|
|[do_thousands_sep](#do_thousands_sep)|Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol oddělovače tisíců.|
|[frac_digits](#frac_digits)|Vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od každé desetinné čárky.|
|[Seskupení](#grouping)|Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.|
|[neg_format](#neg_format)|Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů se zápornými částkami.|
|[negative_sign](#negative_sign)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol záporného znaménka.|
|[pos_format](#pos_format)|Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů s kladnými částkami.|
|[positive_sign](#positive_sign)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol kladného znaménka.|
|[thousands_sep](#thousands_sep)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol oddělovače tisíců.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="moneypunctchar_type"></a><a name="char_type"></a>moneypunct::char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony **CharType**.

## <a name="moneypunctcurr_symbol"></a><a name="curr_symbol"></a>moneypunct::curr_symbol

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol měny.

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující symbol měny.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_curr_symbol](#do_curr_symbol).

### <a name="example"></a>Příklad

```cpp
// moneypunct_curr_symbol.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;
};
```

## <a name="moneypunctdecimal_point"></a><a name="decimal_point"></a>moneypunct::dEcimal_point

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol desetinné čárky.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Posloupnost prvků specifická pro národní prostředí, která se má použít jako symbol desetinné čárky.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_decimal_point](#do_decimal_point).

### <a name="example"></a>Příklad

```cpp
// moneypunct_decimal_pt.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc("german_germany");

   const moneypunct < char, true > &mpunct = use_facet
      < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international decimal point "
        << mpunct.decimal_point( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet
      < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic decimal point "
        << mpunct2.decimal_point( ) << endl;
}
```

```Output
German_Germany.1252 international decimal point ,
German_Germany.1252 domestic decimal point ,
```

## <a name="moneypunctdo_curr_symbol"></a><a name="do_curr_symbol"></a>moneypunct::do_curr_symbol

Chráněná virtuální členská funkce, která vrátí sekvenci prvků specifickou pro národní prostředí, která se použije jako symbol měny.

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>Návratová hodnota

Posloupnost prvků specifická pro národní prostředí, která se má použít jako symbol desetinné čárky.

### <a name="example"></a>Příklad

Viz příklad pro [curr_symbol](#curr_symbol), kde virtuální `curr_symbol`členská funkce je volána .

## <a name="moneypunctdo_decimal_point"></a><a name="do_decimal_point"></a>moneypunct::do_decimal_point

Chráněná virtuální členská funkce, která vrací posloupnost prvků specifickou pro národní prostředí, která se má použít jako symbol desetinné čárky.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Posloupnost prvků specifická pro národní prostředí, která se má použít jako symbol desetinné čárky.

### <a name="example"></a>Příklad

Viz příklad pro [decimal_point](#decimal_point), kde je `decimal_point`virtuální členská funkce volána .

## <a name="moneypunctdo_frac_digits"></a><a name="do_frac_digits"></a>moneypunct::do_frac_digits

Chráněná virtuální členská funkce, která vrací počet číslic specifický pro národní prostředí, který se má zobrazit vpravo od libovolné desetinné čárky.

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet čísel specifických pro dané prostředí, které se mají zobrazit vpravo od jakékoli desetinné čárky.

### <a name="example"></a>Příklad

Viz příklad pro [frac_digits](#frac_digits), kde je `frac_digits`virtuální členská funkce volána .

## <a name="moneypunctdo_grouping"></a><a name="do_grouping"></a>moneypunct::do_grouping

Chráněná virtuální členská funkce, která vrací pravidlo specifické pro národní prostředí pro určení způsobu seskupení číslic nalevo od jakékoli desetinné čárky.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro určení způsobu seskupení číslic nalevo od jakékoli desetinné čárky.

### <a name="example"></a>Příklad

Viz příklad pro [seskupení](#grouping), kde virtuální `grouping`členská funkce je volána .

## <a name="moneypunctdo_neg_format"></a><a name="do_neg_format"></a>moneypunct::do_neg_format

Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů se zápornými částkami.

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí pravidlo specifické pro národní prostředí pro určení, jak generovat pole peněžního výstupu pro zápornou částku. Každý ze čtyř `pattern::field` prvků může mít hodnoty:

- `none`tak, aby odpovídaly nule nebo více mezerám nebo negenerovaly nic.

- `sign`tak, aby odpovídalo nebo generovalo kladné nebo záporné znaménko.

- `space`tak, aby odpovídaly nule nebo více mezerám nebo vygenerovaly mezeru.

- `symbol`tak, aby odpovídalo nebo vygenerovalo symbol měny.

- `value`pro shodovat nebo generovat peněžní hodnotu.

Jsou generovány součásti pole peněžního výstupu a součásti pole peněžního vstupu jsou spárovány v pořadí, ve kterém jsou tyto prvky zobrazeny v . `pattern::field` Každá z `sign`hodnot `symbol` `value`, , `none` `space` a buď nebo musí být zobrazena přesně jednou. Hodnota `none` se nesmí zobrazit jako první. Místo hodnoty se **nesmí** zobrazit jako první nebo poslední. Pokud `Intl` je true, `symbol`objednávka `none`je `value`, `sign`, , then .

`moneypunct` \< Verze šablony **CharType**, **Intl**> vrátí `{` **money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Příklad

Viz příklad pro [neg_format](#neg_format), kde je `neg_format`virtuální členská funkce volána .

## <a name="moneypunctdo_negative_sign"></a><a name="do_negative_sign"></a>moneypunct::do_negative_sign

Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol záporného znaménka.

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>Návratová hodnota

Národní prostředí specifické posloupnost prvků použít jako záporné znaménko.

### <a name="example"></a>Příklad

Viz příklad pro [negative_sign](#negative_sign), kde je `negative_sign`virtuální členská funkce volána .

## <a name="moneypunctdo_pos_format"></a><a name="do_pos_format"></a>moneypunct::do_pos_format

Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů s kladnými částkami.

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí pravidlo specifické pro národní prostředí pro určení, jak generovat pole peněžního výstupu pro kladnou částku. (Určuje také, jak se mají spárovat složky pole peněžního vstupu.) Kódování je stejné jako pro [do_neg_format](#do_neg_format).

Verze šablony moneypunct\< **CharType**, **Inputlterator** `{`> vrátí **money_base::symbol**, **money_base::sign**, **money_base::value**, **money_base::none**`}`.

### <a name="example"></a>Příklad

Viz příklad pro [pos_format](#pos_format), kde je `pos_format`virtuální členská funkce volána .

## <a name="moneypunctdo_positive_sign"></a><a name="do_positive_sign"></a>moneypunct::do_positive_sign

Chráněná virtuální členská funkce, která vrací posloupnost prvků specifickou pro národní prostředí, která se má použít jako kladné znaménko.

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>Návratová hodnota

Národní prostředí specifické posloupnost prvků použít jako kladné znaménko.

### <a name="example"></a>Příklad

Viz příklad pro [positive_sign](#positive_sign), kde je `positive_sign`virtuální členská funkce volána .

## <a name="moneypunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>moneypunct::do_thousands_sep

Chráněná virtuální členská funkce, která vrací prvek specifický pro národní prostředí, který se má použít jako oddělovač skupiny nalevo od libovolné desetinné čárky.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se má použít jako oddělovač skupiny nalevo od jakékoli desetinné čárky.

### <a name="example"></a>Příklad

Viz příklad pro [thousands_sep](#thousands_sep), kde je `thousands_sep`virtuální členská funkce volána .

## <a name="moneypunctfrac_digits"></a><a name="frac_digits"></a>moneypunct::frac_digits

Vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od každé desetinné čárky.

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet čísel specifických pro dané prostředí, které se mají zobrazit vpravo od jakékoli desetinné čárky.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_frac_digits](#do_frac_digits).

### <a name="example"></a>Příklad

```cpp
// moneypunct_frac_digits.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >(loc);
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >(loc);
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctgrouping"></a><a name="grouping"></a>moneypunct::seskupení

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
// moneypunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >( loc );
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >( loc );
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctmoneypunct"></a><a name="moneypunct"></a>moneypunct::moneypunct

Konstruktor objektů typu `moneypunct`.

```cpp
explicit moneypunct(size_t _Refs = 0);
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

Konstruktor inicializuje svůj základní objekt pomocí [národního prostředí::faset](../standard-library/locale-class.md#facet_class)(_ *Refs).*

## <a name="moneypunctneg_format"></a><a name="neg_format"></a>moneypunct::neg_format

Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů se zápornými částkami.

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro formátování výstupů se zápornými částkami.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_neg_format](#do_neg_format).

### <a name="example"></a>Příklad

```cpp
// moneypunct_neg_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( ) {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international negative number format: "
        << mpunct.neg_format( ).field[0]
        << mpunct.neg_format( ).field[1]
        << mpunct.neg_format( ).field[2]
        << mpunct.neg_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative number format: "
        << mpunct2.neg_format( ).field[0]
        << mpunct2.neg_format( ).field[1]
        << mpunct2.neg_format( ).field[2]
        << mpunct2.neg_format( ).field[3] << endl;
}
```

## <a name="moneypunctnegative_sign"></a><a name="negative_sign"></a>moneypunct::negative_sign

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol záporného znaménka.

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol záporného znaménka.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_negative_sign](#do_negative_sign).

### <a name="example"></a>Příklad

```cpp
// moneypunct_neg_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international negative sign: "
        << mpunct.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative sign: "
        << mpunct2.negative_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international negative sign: "
        << mpunct3.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic negative sign: "
        << mpunct4.negative_sign( ) << endl;
};
```

```Output
German_Germany.1252 international negative sign: -
German_Germany.1252 domestic negative sign: -
French_France.1252 international negative sign: -
French_France.1252 domestic negative sign: -
```

## <a name="moneypunctpos_format"></a><a name="pos_format"></a>moneypunct::pos_format

Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů s kladnými částkami.

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro formátování výstupů s kladnými částkami.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_pos_format](#do_pos_format).

### <a name="example"></a>Příklad

```cpp
// moneypunct_pos_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main() {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international positive number format: "
        << mpunct.pos_format( ).field[0]
        << mpunct.pos_format( ).field[1]
        << mpunct.pos_format( ).field[2]
        << mpunct.pos_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive number format: "
        << mpunct2.pos_format( ).field[0]
        << mpunct2.pos_format( ).field[1]
        << mpunct2.pos_format( ).field[2]
        << mpunct2.pos_format( ).field[3] << endl;
}
```

## <a name="moneypunctpositive_sign"></a><a name="positive_sign"></a>moneypunct::positive_sign

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol kladného znaménka.

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>Návratová hodnota

Národní prostředí specifické posloupnost prvků použít jako symbol kladné znaménko.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_positive_sign](#do_positive_sign).

### <a name="example"></a>Příklad

```cpp
// moneypunct_pos_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international positive sign:"
        << mpunct.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive sign:"
        << mpunct2.positive_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international positive sign:"
        << mpunct3.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic positive sign:"
        << mpunct4.positive_sign( ) << endl;
};
```

```Output
German_Germany.1252 international positive sign:
German_Germany.1252 domestic positive sign:
French_France.1252 international positive sign:
French_France.1252 domestic positive sign:
```

## <a name="moneypunctstring_type"></a><a name="string_type"></a>moneypunct::string_type

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) jehož objekty mohou ukládat kopie interpunkčních sekvencí.

## <a name="moneypunctthousands_sep"></a><a name="thousands_sep"></a>moneypunct::thousands_sep

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol oddělovače tisíců.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Posloupnost prvků specifických pro národní prostředí, která se má použít jako oddělovač tisíců

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_thousands_sep](#do_thousands_sep).

### <a name="example"></a>Příklad

```cpp
// moneypunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international thousands separator: "
        << mpunct.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic thousands separator: "
        << mpunct2.thousands_sep( ) << endl << endl;

   locale loc2( "english_canada" );

   const moneypunct <char, true> &mpunct3 =
       use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international thousands separator: "
        << mpunct3.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic thousands separator: "
        << mpunct4.thousands_sep( ) << endl;
}
```

```Output
German_Germany.1252 international thousands separator: .
German_Germany.1252 domestic thousands separator: .

English_Canada.1252 international thousands separator: ,
English_Canada.1252 domestic thousands separator: ,
```

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
