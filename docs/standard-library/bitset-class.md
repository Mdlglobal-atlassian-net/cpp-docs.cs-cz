---
title: bitset – třída
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: a4771e9c2c48bfe9c4c09629278533b031d60979
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890848"
---
# <a name="bitset-class"></a>bitset – třída

Popisuje typ objektu, který ukládá sekvenci sestávající z pevného počtu bitů, který poskytuje kompaktní způsob uchování příznaků pro sadu položek nebo podmínek. Třída bitset podporuje operace s objekty typu bitset, které obsahují kolekci bitů a poskytují přístup k jednotlivým bitům za běhu.

## <a name="syntax"></a>Syntaxe

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>Parametry

*N*\
Určuje počet bitů v objektu bitset s nenulovým celým číslem typu `size_t`, který musí být známý v době kompilace.

## <a name="remarks"></a>Poznámky

Na rozdíl od podobné [vektorové\<třídy bool >](../standard-library/vector-bool-class.md)třída bitset neobsahuje iterátory a není C++ standardním kontejnerem knihovny. Také se liší od vektorové\<bool > o konkrétní velikosti, která je opravena v době kompilace v souladu s velikostí určenou parametrem šablony *N* , pokud je deklarován **\>bitset\<N** .

Bit je nastaven, pokud je jeho hodnota 1 a resetuje se, pokud má hodnotu 0. Chcete-li převrátit nebo Invertovat bit, změňte jeho hodnotu z 1 na 0 nebo z 0 na 1. Bity *N* v bitset jsou indexovány pomocí celočíselných hodnot od 0 do *N* -1, kde 0 indexuje první bitovou polohu a *N* -1 konečnou bitovou polohu.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[bitset](#bitset)|Vytvoří objekt třídy `bitset\<N>` a inicializuje bity na nulu, na určitou zadanou hodnotu nebo na hodnoty získané ze znaků v řetězci.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ, který představuje synonymum pro datový typ **bool** a lze jej použít k odkazování na bity elementu v `bitset`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[všem](#all)|Testuje všechny bity v tomto `bitset` a určí, zda jsou všechny nastaveny na **hodnotu true**.|
|[jakýmikoli](#any)|Členská funkce testuje, zda je kterýkoli bit v sekvenci nastaven na hodnotu 1.|
|[count](#count)|Členská funkce vrátí počet bitů nastavený v bitové sekvenci.|
|[funkci](#flip)|Obrátí hodnotu všech bitů ve `bitset` nebo Invertuje jeden bit na zadané pozici.|
|[nTato](#none)|Testuje, zda nebyl v objektu `bitset` nastaven žádný bit na hodnotu 1.|
|[nové](#reset)|Obnoví všechny bity v `bitset` na 0 nebo obnoví bit na zadané pozici na 0.|
|[set](#set)|Nastaví všechny bity v `bitset` na 1 nebo nastaví bit na zadané pozici na 1.|
|[hodnota](#size)|Vrátí počet bitů v objektu `bitset`.|
|[napaden](#test)|Testuje, zda je bit na zadané pozici v `bitset` nastaven na hodnotu 1.|
|[to_string](#to_string)|Převede objekt `bitset` na řetězcovou reprezentaci.|
|[to_ullong](#to_ullong)|Vrátí součet bitových hodnot v `bitset` jako **unsigned long long**.|
|[to_ulong](#to_ulong)|Převede objekt `bitset` na **unsigned long** , který by generoval sekvenci bitů, které jsou obsaženy v případě použití k inicializaci `bitset`.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[odkaz](#reference)|Třída proxy, která poskytuje odkazy na bity obsažené v `bitset`, který se používá pro přístup k jednotlivým bitech a manipulaci s nimi jako pomocná třída pro `operator[]` třídy `bitset`.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](#op_neq)|Testuje cílovou `bitset` pro nerovnost se zadaným `bitset`.|
|[operátor & =](#op_and_eq)|Provede bitovou kombinaci Bitsets s logickou `AND`ovou operací.|
|[operátor < <](#op_lshift)|Posune bity v `bitset` vlevo a za zadaný počet pozic a vrátí výsledek do nového `bitset`.|
|[operátor < < =](#op_lshift_eq)|Posune bity v `bitset` doleva o zadaný počet pozic a vrátí výsledek cílovému `bitset`.|
|[operator = = – operátor](#op_eq_eq)|Testuje cílovou `bitset` pro rovnost se zadaným `bitset`.|
|[operátor > >](#op_rshift)|Posune bity v `bitset` napravo od zadaného počtu pozic a vrátí výsledek novému `bitset`.|
|[operátor > > =](#op_rshift_eq)|Posune bity v `bitset` napravo od zadaného počtu pozic a vrátí výsledek cílovému `bitset`.|
|[podnikatel&#91;&#93;](#op_at)|Vrátí odkaz na bit na zadané pozici ve `bitset`, pokud je `bitset` upravitelná; v opačném případě vrátí hodnotu bitu na této pozici.|
|[operátor ^ =](#op_xor_eq)|Provede bitovou kombinaci Bitsets s výhradní operací `OR`.|
|[operátor&#124;=](#op_or_eq)|Provede bitovou kombinaci Bitsets s operací zahrnujícím `OR`.|
|[~ – operátor](#op_not)|Obrátí všechny bity v cílovém `bitset` a vrátí výsledek.|

### <a name="structures"></a>Struktury

|||
|-|-|
|[kontrole](#hash)||

### <a name="all"></a>všem

Testuje všechny bity v tomto bitset a určí, jestli jsou všechny nastavené na true.

```cpp
bool all() const;
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud jsou všechny bity v této sadě pravdivé. Vrátí **hodnotu false** , pokud je jedna nebo více bitů false.

### <a name="any"></a>jakýmikoli

Testuje, zda je bit v sekvenci nastaven na hodnotu 1.

```cpp
bool any() const;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud je kterýkoli bit v bitset nastavený na 1; **false** , pokud jsou všechny bity 0.

#### <a name="example"></a>Příklad

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a>bitset

Vytvoří objekt třídy `bitset\<N>` a inicializuje bity na nulu nebo na určitou zadanou hodnotu nebo hodnoty získané ze znaků v řetězci.

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>Parametry

\ *Val*
Unsigned integer, jehož základní dvě reprezentace se používají k inicializaci bitů v sebitsetch sestavách.

\ *str*
Řetězec nul a hodnot používaných k inicializaci bitových hodnot bitset

*_CStr*\
Řetězec ve stylu jazyka C nul a ty, které se používají k inicializaci bitových hodnot bitset.

*_Pos*\
Pozice znaku v řetězci, počítáno zleva doprava a od nuly, která se používá k inicializaci prvního bitu v bitset.

*počet*\
Počet znaků v řetězci, který se používá k poskytnutí počátečních hodnot bitů v bitset.

*_Zero*\
Znak, který se používá k reprezentaci nuly. Výchozí hodnota je 0.

*_One*\
Znak, který se používá k reprezentaci jednoho. Výchozí hodnota je 1.

#### <a name="remarks"></a>Poznámky

Tři konstruktory lze použít k vytvoření obects třídy `bitset\<N>`:

- První konstruktor nepřijímá žádné parametry, sestaví objekt třídy `bitset\<N>` a inicializuje všechny N bitů na výchozí hodnotu nula.

- Druhý konstruktor vytvoří objekt třídy `bitset\<N>` a inicializuje bity pomocí jednoho **nepodepsaného dlouhého** parametru Long.

- Třetí konstruktor vytvoří objekt třídy `bitset\<N>`, inicializuje N bitů na hodnoty, které odpovídají znakům uvedeným v řetězci znaků ve stylu jazyka c nuly a. Zavoláte konstruktor bez přetypování řetězce do řetězcového typu: `bitset<5> b5("01011");`

K dispozici jsou také dvě šablony konstruktoru:

- Šablona prvního konstruktoru vytvoří objekt třídy `bitset\<N>` a inicializuje bity ze znaků, které jsou k dispozici v řetězci nul a. Pokud jsou jakékoli znaky v řetězci jiné než 0 nebo 1, vyvolá konstruktor objekt třídy, který není [platným argumentem](../standard-library/invalid-argument-class.md). Pokud je zadaná pozice ( *_Pos*) mimo délku řetězce, pak konstruktor vyvolá objekt třídy [out_of_range](../standard-library/out-of-range-class.md). Konstruktor nastaví pouze bity na pozici *j* v bitset, pro který je znak v řetězci na pozici `_Pos + j` 1. Ve výchozím nastavení je *_Pos* 0.

- Druhá šablona konstruktoru je podobná jako první, ale obsahuje další parametr (*Count*), který se používá k určení počtu bitů k inicializaci. Má také dva volitelné parametry *_Zero* a *_One*, které označují, jaký znak v *str* je interpretován tak, aby znamenal 0 bitů a 1 bit v uvedeném pořadí.

#### <a name="example"></a>Příklad

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a>výpočtu

Vrátí počet bitů nastavených v bitové sekvenci.

```cpp
size_t count() const;
```

#### <a name="return-value"></a>Návratová hodnota

Počet bitů nastavených v bitové sekvenci.

#### <a name="example"></a>Příklad

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a>element_type

Typ, který představuje synonymum pro datový typ **bool** a lze jej použít k odkazování na bity elementu v bitset.

```cpp
typedef bool element_type;
```

#### <a name="example"></a>Příklad

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a>funkci

Obrátí hodnotu všech bitů ve bitset nebo Invertuje jeden bit na zadané pozici.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozice bitu, jehož hodnota má být obrácena.

#### <a name="return-value"></a>Návratová hodnota

Kopie upraveného bitset, pro kterou byla vyvolána členská funkce.

#### <a name="remarks"></a>Poznámky

Druhá členská funkce vyvolá výjimku [out_of_range](../standard-library/out-of-range-class.md) , pokud je pozice zadaná jako parametr větší než velikost *n* **bitset\<** *n* **>** jejichž bit byl obrácen.

#### <a name="example"></a>Příklad

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a>kontrole

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a>nTato

Testuje, zda nebyl v objektu bitset nastaven žádný bit na hodnotu 1.

```cpp
bool none() const;
```

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud není bit bitset nastaven na hodnotu 1; **false** , pokud byl alespoň jeden bit nastaven na hodnotu 1.

#### <a name="example"></a>Příklad

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="op_neq"></a>! = – operátor

Testuje cílovou bitset pro nerovnost se zadaným bitset.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parametry

*pravé*\
Bitset, který má být porovnán s cílovým bitset pro nerovnost.

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud se Bitsets liší; **false** , pokud jsou stejné.

#### <a name="remarks"></a>Poznámky

Bitsets musí mít stejnou velikost, aby byla testována pro nerovnost funkcí member operator.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_and_eq"></a>operátor&amp;=

Provede bitovou kombinaci Bitsets s logickou `AND`ovou operací.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*pravé*\
Bitset, který má být sloučen s cílovým bitset.

#### <a name="return-value"></a>Návratová hodnota

Upravený cílový bitset, který je výsledkem bitové operace `AND` se bitset zadanou jako parametr.

#### <a name="remarks"></a>Poznámky

Dvě bity kombinované operátorem `AND` vrátí **hodnotu true** , pokud má každý bit hodnotu true. v opačném případě jejich kombinace vrátí **hodnotu false**.

Bitsets musí mít stejnou velikost, aby byla sloučena s operátorem `AND` pomocí funkce člen operator.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_lshift"></a>operátor\<\<

Posune bity v bitset vlevo a za zadaný počet pozic a vrátí výsledek do nového bitset.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic vlevo, které mají být bity v bitset posunuty.

#### <a name="return-value"></a>Návratová hodnota

Změněné bitset s bity se posunuly na levý požadovaný počet pozic.

#### <a name="remarks"></a>Poznámky

Funkce operátoru member vrátí **bitset**( **\*this**) **< < = POS,** kde [<<=](#op_lshift_eq) posune bity v bitset doleva a zadaný počet pozic a vrátí výsledek cílovému bitset.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="op_lshift_eq"></a>operátor&lt;&lt;=

Posune bity v bitset vlevo a za zadaný počet pozic a vrátí výsledek cílovému bitset.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic vlevo od bitů v bitset mají být posunuty.

#### <a name="return-value"></a>Návratová hodnota

Cílový bitset změněn tak, aby byly bity posunuty na levý požadovaný počet pozic.

#### <a name="remarks"></a>Poznámky

Pokud žádný prvek neexistuje, aby se posunul do pozice, funkce vymaže bit na hodnotu 0.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="op_eq_eq"></a>operator = = – operátor

Testuje cílovou bitset pro rovnost se zadaným bitset.

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parametry

*pravé*\
Bitset, který má být porovnán s cílovým bitset pro rovnost.

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou Bitsets stejné; **false** , pokud se liší.

#### <a name="remarks"></a>Poznámky

Bitsets musí mít stejnou velikost, aby byla testována na rovnost funkcí operátoru member.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_rshift"></a>operátor&gt;&gt;

Posune bity v bitset k pravému zadanému počtu pozic a vrátí výsledek do nového bitset.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic napravo od bitů v bitset musí být posunuty.

#### <a name="return-value"></a>Návratová hodnota

Nový bitset, kde byly bity posunuty do pravého požadovaného počtu pozic vzhledem k cílovému bitset.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="op_rshift_eq"></a>operátor&gt;&gt;=

Posune bity v bitset k pravému zadanému počtu pozic a vrátí výsledek cílovému bitset.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic napravo od bitů v bitset musí být posunuty.

#### <a name="return-value"></a>Návratová hodnota

Cílený bitset změněn tak, aby byly bity posunuty k pravému požadovanému počtu pozic.

#### <a name="remarks"></a>Poznámky

Pokud žádný prvek neexistuje, aby se posunul do pozice, funkce vymaže bit na hodnotu 0.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="op_at"></a>operator [] – operátor

Vrátí odkaz na bit na zadané pozici v bitset, pokud je bitset upravitelná; v opačném případě vrátí hodnotu bitu na této pozici.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozice, která hledá bit v rámci bitset.

#### <a name="remarks"></a>Poznámky

Při definování [\_iterátoru\_\_úroveň ladění](../standard-library/iterator-debug-level.md) jako 1 nebo 2 v sestavení, dojde k běhové chybě ve spustitelném souboru, pokud se pokusíte o přístup k prvku mimo hranice bitset. Další informace najdete v tématu [kontrolované iterátory](../standard-library/checked-iterators.md).

#### <a name="example"></a>Příklad

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="op_xor_eq"></a>operátor ^ =

Provede bitovou kombinaci Bitsets s výhradní operací `OR`.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*pravé*\
Bitset, který má být sloučen s cílovým bitset.

#### <a name="return-value"></a>Návratová hodnota

Upravený cílový bitset, který je výsledkem bitové operace s výhradním `OR` s bitset zadanou jako parametr.

#### <a name="remarks"></a>Poznámky

Dvě bity kombinované pomocí operátoru Exclusive **nebo** vrátí **hodnotu true** , pokud je alespoň jeden, ale ne obojí, z bitů je **true**. v opačném případě jejich kombinace vrátí **hodnotu false**.

Bitsets musí mít stejnou velikost, aby bylo možné kombinovat bitové s výhradním operátorem `OR` funkcí member operator.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_or_eq"></a>operátor&#124;=

Provede bitovou kombinaci Bitsets s operací zahrnujícím `OR`.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*pravé*\
Bitset, který má být sloučen s cílovým bitset.

#### <a name="return-value"></a>Návratová hodnota

Upravený cílový bitset, který je výsledkem bitové operace s bitovým plánem `OR`, s bitset, které se zadaly jako parametr.

#### <a name="remarks"></a>Poznámky

Dvě bity kombinované operátorem `OR` vrátí **hodnotu true** , pokud je alespoň jeden z bitů **pravda**. Pokud jsou obě bity **false**, jejich kombinace vrátí **false**.

Bitsets musí mít stejnou velikost, aby byla sloučena s operátorem s operátorem `OR` pomocí funkce člen operator.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_not"></a>~ – operátor

Obrátí všechny bity v cílovém bitset a vrátí výsledek.

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>Návratová hodnota

Bitset se všemi jeho bity se obrátí s ohledem na cílovou bitset.

#### <a name="example"></a>Příklad

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a>odkaz

Třída proxy, která poskytuje odkazy na bity obsažené v bitset, který se používá pro přístup k jednotlivým bitech a manipulaci s nimi jako pomocná třída pro `operator[]` třídy bitset.

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>Parametry

\ *Val*
Hodnota objektu typu **bool** , která má být přiřazena bitu v bitset.

*_Bitref*\
Odkaz na tvar *x [i]* na bit na pozici *i* v bitset *x*.

#### <a name="return-value"></a>Návratová hodnota

Odkaz na bitovou kopii v bitset určené pozici argumentu pro první, druhou a pátou členskou funkci odkazu na třídu a **hodnotu true** nebo **false**, aby odrážela hodnotu modifikovaného bitu v bitset pro třetí a čtvrtou členskou funkci odkazu na třídu.

#### <a name="remarks"></a>Poznámky

Třída `reference` existuje pouze jako pomocná třída pro `operator[]`bitset. Třída member popisuje objekt, který má přístup k jednotlivému bitu v rámci bitset. Nechť *b* je objekt typu **bool**, *x* a *y* typu **bitset\<** *N* **>** a platné pozice *i* a *j* v rámci takového objektu. Zápis *x [i]* odkazuje na bit na pozici *i* v bitset *x*. Členské funkce třídy `reference` poskytují v pořadí následující operace:

|Operace|Definice|
|---------------|----------------|
|*x*[*i*] = *b*|Ukládá hodnotu bool *b* v bitové pozici *i* v bitset *x*.|
|*x*[*i*] = *y*[*j*]|Ukládá hodnotu bitové *osy y*[ *j*] *na pozici v* bitset *x*.|
|*b* = ~ *x*[*i*]|Ukládá převrácenou hodnotu bitu *x*[ *i*] v **bool** *b*.|
|*b* = *x*[*i*]|Ukládá hodnotu bitu *x*[ *i*] v **bool** *b*.|
|*x*[*i*]. `flip`()|Ukládá převrácenou hodnotu bitu *x*[ *i*] zpátky do bitové pozice *i* v *x*.|

#### <a name="example"></a>Příklad

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a>nové

Obnoví všechny bity v bitset na 0 nebo obnoví bit na zadané pozici na 0.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozice bitu v bitset, která se má resetovat na 0.

#### <a name="return-value"></a>Návratová hodnota

Kopie bitset, pro kterou byla členská funkce vyvolána.

#### <a name="remarks"></a>Poznámky

Druhá členská funkce vyvolá výjimku [out_of_range](../standard-library/out-of-range-class.md) , pokud je zadaná pozice větší než velikost bitset.

#### <a name="example"></a>Příklad

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a>stanovenými

Nastaví všechny bity v bitset na 1 nebo nastaví bit na zadané pozici na 1.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozice bitu v bitset, která má být nastavena na přiřazenou hodnotu.

\ *Val*
Hodnota, která má být přiřazena k bitu na zadané pozici.

#### <a name="return-value"></a>Návratová hodnota

Kopie bitset, pro kterou byla členská funkce vyvolána.

#### <a name="remarks"></a>Poznámky

Druhá členská funkce vyvolá výjimku [out_of_range](../standard-library/out-of-range-class.md) , pokud je zadaná pozice větší než velikost bitset.

#### <a name="example"></a>Příklad

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a>hodnota

Vrátí počet bitů v objektu bitset.

```cpp
size_t size() const;
```

#### <a name="return-value"></a>Návratová hodnota

Počet bitů, *n*, v bitset\<N >.

#### <a name="example"></a>Příklad

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a>napaden

Testuje, zda je bit na zadané pozici v bitset nastaven na hodnotu 1.

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozice bitu v bitset, která má být testována na hodnotu.

#### <a name="return-value"></a>Návratová hodnota

**true** , pokud je bit určený argumentem pozice nastaven na hodnotu 1; v opačném případě **false**.

#### <a name="remarks"></a>Poznámky

Členská funkce vyvolá [out_of_range](../standard-library/out-of-range-class.md)

### <a name="to_string"></a>to_string

Převede objekt bitset na řetězcovou reprezentaci.

```cpp
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt String třídy `basic_string`, kde má každá bitová sada v bitset odpovídající znak 1 a znak 0, pokud je bit nastaven na hodnotu 0.

#### <a name="example"></a>Příklad

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char,
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a>to_ullong

Vrací dlouhou dlouhou hodnotu **bez znaménka** , která obsahuje stejnou sadu bitů jako obsah objektu bitset.

```cpp
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí součet bitových hodnot, které jsou v bitové sekvenci jako **unsigned long long**. Tato **nepodepsaná dlouhodobě dlouhá** hodnota by vytvořila znovu stejnou sadu bitů, pokud se používá k inicializaci bitset.

#### <a name="exceptions"></a>Výjimky

Vyvolá objekt [overflow_error](overflow-error-class.md) , pokud má nějaký bit v bitové sekvenci bitovou hodnotu, která nemůže být reprezentovaná jako hodnota typu **bez znaménka Long Long**.

#### <a name="remarks"></a>Poznámky

Vrátí součet bitových hodnot, které jsou v bitové sekvenci jako **unsigned long long**.

### <a name="to_ulong"></a>to_ulong

Převede objekt bitset na celé číslo, které by vygenerovalo sekvenci bitů obsažených v případě, že se používá k inicializaci bitset.

```cpp
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>Návratová hodnota

Celé číslo, které generuje bity v bitset, pokud se používá při inicializaci bitset.

#### <a name="remarks"></a>Poznámky

Použití členské funkce by vrátilo celé číslo, které má stejnou sekvenci 1 až 0 číslic, jak je nalezeno v sekvenci bitů obsažených v bitset.

Členská funkce vyvolá objekt [overflow_error](overflow-error-class.md) , pokud má nějaký bit v bitové sekvenci bitovou hodnotu, která nemůže být reprezentovaná jako hodnota typu **Long bez znaménka**.

#### <a name="example"></a>Příklad

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
