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
ms.openlocfilehash: 7960ee8b5e9ce6b27494e896e38bbf6b5256fe7e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689299"
---
# <a name="moneypunct-class"></a>moneypunct – třída

Šablona třídy popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro popis sekvencí typu *CharType* sloužících k reprezentaci peněžního vstupního pole nebo pole s peněžním výstupem. Pokud je parametr šablony *Intl* v *hodnotě true*, jsou dodržovány mezinárodní konvence.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>Parametry

*CharType* \
Typ používaný v rámci programu ke kódování znaků.

*Mezinárodní* \
Příznak určující, zda je třeba dodržovat mezinárodní konvence.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v ID jedinečnou kladnou hodnotu **.**

Konstantní statický objekt v zahraničí ukládá hodnotu parametru šablony *Intl*.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[moneypunct](#moneypunct)|Konstruktor objektů typu `moneypunct`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který se používá k popisu znaku používaného národním prostředním.|
|[string_type](#string_type)|Typ, který popisuje řetězec obsahující znaky typu `CharType`.|

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
|[sloučení](#grouping)|Vrátí pravidlo specifické pro národní prostředí určující způsob seskupení číslic nalevo od desetinné čárky.|
|[neg_format](#neg_format)|Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů se zápornými částkami.|
|[negative_sign](#negative_sign)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol záporného znaménka.|
|[pos_format](#pos_format)|Vrátí pravidlo specifické pro národní prostředí pro formátování výstupů s kladnými částkami.|
|[positive_sign](#positive_sign)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol kladného znaménka.|
|[thousands_sep](#thousands_sep)|Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol oddělovače tisíců.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="char_type"></a>moneypunct:: char_type

Typ, který se používá k popisu znaku používaného národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="curr_symbol"></a>moneypunct:: curr_symbol

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

## <a name="decimal_point"></a>moneypunct::d ecimal_point

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol desetinné čárky.

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Sekvence prvků specifických pro národní prostředí, která se má použít jako symbol desetinné čárky.

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

## <a name="do_curr_symbol"></a>moneypunct::d o_curr_symbol

Chráněná virtuální členská funkce, která vrátí sekvenci prvků specifickou pro národní prostředí, která se použije jako symbol měny.

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>Návratová hodnota

Sekvence prvků specifických pro národní prostředí, která se má použít jako symbol desetinné čárky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [curr_symbol](#curr_symbol), kde je virtuální členská funkce volána pomocí `curr_symbol`.

## <a name="do_decimal_point"></a>moneypunct::d o_decimal_point

Chráněná virtuální členská funkce, která vrací sekvenci prvků specifickou pro národní prostředí, která se má použít jako symbol desetinné čárky.

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>Návratová hodnota

Sekvence prvků specifických pro národní prostředí, která se má použít jako symbol desetinné čárky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [decimal_point](#decimal_point), kde je virtuální členská funkce volána pomocí `decimal_point`.

## <a name="do_frac_digits"></a>moneypunct::d o_frac_digits

Chráněná virtuální členská funkce, která vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od libovolné desetinné čárky.

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet číslic specifických pro národní prostředí, které se zobrazí vpravo od libovolné desetinné čárky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [frac_digits](#frac_digits), kde je virtuální členská funkce volána pomocí `frac_digits`.

## <a name="do_grouping"></a>moneypunct::d o_grouping

Chráněná virtuální členská funkce, která vrátí pravidlo specifické pro národní prostředí pro určení způsobu seskupení číslic vlevo od desetinné čárky.

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>Návratová hodnota

Pravidlo specifické pro národní prostředí pro určení, jak jsou číslice seskupeny nalevo od libovolné desetinné čárky.

### <a name="example"></a>Příklad

Podívejte se na příklad [seskupení](#grouping), kde je virtuální členská funkce volána pomocí `grouping`.

## <a name="do_neg_format"></a>moneypunct::d o_neg_format

Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů se zápornými částkami.

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí pravidlo specifické pro národní prostředí, které určuje, jak se má pro záporné množství vygenerovat pole s peněžním výstupem. Každý ze čtyř prvků `pattern::field` může mít hodnoty:

- `none` odpovídat žádnému nebo více mezerám nebo generovat nic.

- `sign`, aby odpovídaly nebo vygenerovaly kladné nebo záporné znaménko.

- `space` odpovídat žádnému nebo více mezerám nebo vygenerovat mezeru.

- `symbol`, aby odpovídaly nebo vygenerovaly symbol měny.

- `value`, aby odpovídaly nebo vygenerovaly peněžní hodnotu.

Komponenty pole s peněžním výstupem jsou generovány a komponenty peněžního vstupního pole jsou porovnány v pořadí, ve kterém jsou tyto prvky zobrazeny v `pattern::field`. Každá z hodnot `sign`, `symbol`, `value` a buď `none` nebo `space`, musí být přesně jednou. Hodnota `none` nesmí být uvedena jako první. **Prostor hodnoty se nesmí** nacházet jako první nebo poslední. Pokud má `Intl` hodnotu true, je pořadí `symbol`, `sign`, `none` a `value`.

Verze šablony `moneypunct` \< **CharType**, **mezinárodní**> vrátí `{`**money_base:: symbol**, **money_base:: Sign**, **money_base:: Value**, **money_base:: none** `}`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [neg_format](#neg_format), kde je virtuální členská funkce volána pomocí `neg_format`.

## <a name="do_negative_sign"></a>moneypunct::d o_negative_sign

Chráněná virtuální členská funkce, která je volána k vrácení sekvence prvků specifických pro národní prostředí, která se použije jako symbol záporného znaménka.

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>Návratová hodnota

Sekvence prvků specifických pro národní prostředí, která se má použít jako záporné znaménko.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [negative_sign](#negative_sign), kde je virtuální členská funkce volána pomocí `negative_sign`.

## <a name="do_pos_format"></a>moneypunct::d o_pos_format

Chráněná virtuální členská funkce, která je volána k vrácení pravidla specifického pro národní prostředí pro formátování výstupů s kladnými částkami.

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí pravidlo specifické pro národní prostředí, které určuje, jak generovat pole peněžního výstupu pro kladnou částku. (Také určuje, jak se bude shodovat s komponentami peněžního vstupního pole.) Kódování je stejné jako pro [do_neg_format](#do_neg_format).

Verze šablony moneypunct \< **CharType**, **Inputlterator**> vrací `{`**money_base:: symbol**, **money_base:: Sign**, **money_base:: Value**, **money_base:: none** `}`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [pos_format](#pos_format), kde je virtuální členská funkce volána pomocí `pos_format`.

## <a name="do_positive_sign"></a>moneypunct::d o_positive_sign

Chráněná virtuální členská funkce, která vrací sekvenci prvků specifickou pro národní prostředí, která se má použít jako kladné znaménko.

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>Návratová hodnota

Sekvence prvků specifických pro národní prostředí, která se má použít jako kladné znaménko.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [positive_sign](#positive_sign), kde je virtuální členská funkce volána pomocí `positive_sign`.

## <a name="do_thousands_sep"></a>moneypunct::d o_thousands_sep

Chráněná virtuální členská funkce, která vrátí prvek specifický pro národní prostředí, který se použije jako oddělovač skupin nalevo od libovolné desetinné čárky.

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Prvek specifický pro národní prostředí, který se použije jako oddělovač skupin nalevo od libovolné desetinné čárky.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [thousands_sep](#thousands_sep), kde je virtuální členská funkce volána pomocí `thousands_sep`.

## <a name="frac_digits"></a>moneypunct:: frac_digits

Vrátí počet číslic specifický pro národní prostředí, který se zobrazí vpravo od každé desetinné čárky.

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet číslic specifických pro národní prostředí, které se zobrazí vpravo od libovolné desetinné čárky.

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

## <a name="grouping"></a>moneypunct:: Grouping

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

## <a name="moneypunct"></a>moneypunct:: moneypunct

Konstruktor objektů typu `moneypunct`.

```cpp
explicit moneypunct(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* \
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože je destruktor chráněný.

Konstruktor inicializuje svůj základní objekt pomocí [locale:: Face](../standard-library/locale-class.md#facet_class)(_ *ReFS*).

## <a name="neg_format"></a>moneypunct:: neg_format

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

## <a name="negative_sign"></a>moneypunct:: negative_sign

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

## <a name="pos_format"></a>moneypunct::p os_format

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

## <a name="positive_sign"></a>moneypunct::p ositive_sign

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol kladného znaménka.

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>Návratová hodnota

Sekvence prvků specifických pro národní prostředí, která se má použít jako symbol kladného znaménka.

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

## <a name="string_type"></a>moneypunct:: string_type

Typ, který popisuje řetězec obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) , jejíž objekty mohou ukládat kopie sekvencí interpunkce.

## <a name="thousands_sep"></a>moneypunct:: thousands_sep

Vrátí sekvenci prvků pro specifické národní prostředí, která se použije jako symbol oddělovače tisíců.

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>Návratová hodnota

Sekvence prvků specifických pro národní prostředí, která se má použít jako oddělovač tisíců

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

## <a name="see-also"></a>Viz také:

[\<locale >](../standard-library/locale.md) \
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
