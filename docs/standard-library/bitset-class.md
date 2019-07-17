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
ms.openlocfilehash: 2337a5e8355006ef2c05874b9e3e46b469c41beb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243346"
---
# <a name="bitset-class"></a>bitset – třída

Popisuje typ objektu, který ukládá pořadí skládající se z pevný počet bitů, které umožňují compact udržování příznaky pro sadu položek nebo podmínky. Bitset – třída podporuje operace pro objekty bitset – typ, které obsahují sadu bitů a poskytují konstantním čase přístup k každý bit.

## <a name="syntax"></a>Syntaxe

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>Parametry

*N*\
Určuje počet bitů v objektu bitset – s nenulového celého čísla typu `size_t` , který musí být v době kompilace znám.

## <a name="remarks"></a>Poznámky

Na rozdíl od podobný [vektoru\<bool > třída](../standard-library/vector-bool-class.md), bitset – třída nemá žádné iterátory a není kontejneru standardní knihovny C++. Se také liší od vektoru\<bool > podle vrácení některých určité velikosti, která je stanoveno v době kompilace v souladu s velikost zadaná v parametru šablony *N* při **bitset –\<N\>**  je deklarována.

Bit je nastavit, pokud její hodnota je 1 a obnovit, pokud její hodnota je 0. Převrátit na ose nebo Invertovat trochu je můžete změnit jeho hodnotu z 1 na 0, nebo od 0 do 1. *N* bity bitset – jsou indexovány pomocí celočíselné hodnoty od 0 do *N* -1, kde 0 indexuje první bitová pozice a *N* – 1 finální bitové pozice.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[bitset](#bitset)|Vytvoří objekt třídy `bitset\<N>` a inicializuje bity na nulu, některé zadané hodnoty nebo hodnoty získané ze znaků v řetězci.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ, který je synonymum pro typ dat **bool** a je možné odkazovat na element bity `bitset`.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[Všechny](#all)|Testuje všechny bity v tomto `bitset` k určení, jestli jsou nastavené a můžete **true**.|
|[Všechny](#any)|Členská funkce testuje, jestli všechny bity v pořadí je nastavená na 1.|
|[Počet](#count)|Členská funkce vrátí počet bitů, nastavte v pořadí verze.|
|[Převrátit na ose](#flip)|Obrátí všechny bity v hodnotu `bitset` nebo Invertuje jeden bit na určené pozici.|
|[None](#none)|Testuje, zda žádná verze je nastavená na 1 `bitset` objektu.|
|[reset](#reset)|Obnoví všechny bity v `bitset` na hodnotu 0 nebo obnoví trochu na určené pozici na hodnotu 0.|
|[set](#set)|Nastaví všechny bity `bitset` na 1 nebo sady trochu na určenou pozici do 1.|
|[Velikost](#size)|Vrátí počet bitů `bitset` objektu.|
|[test](#test)|Testy, jestli je bit na určené pozici v `bitset` je nastavená na 1.|
|[to_string](#to_string)|Převede `bitset` objektu na řetězcovou reprezentaci.|
|[to_ullong](#to_ullong)|Vrátí součet hodnot bit do `bitset` jako **unsigned long long**.|
|[to_ulong](#to_ulong)|Převede `bitset` objektu **unsigned long** , který vygeneruje pořadí bitů, pokud je použita k inicializaci `bitset`.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[Referenční dokumentace](#reference)|Třída proxy, která poskytuje odkazy na bity součástí `bitset` , který se používá pro přístup k a manipulaci s jednotlivých bitů jako pomocnou třídu pro `operator[]` třídy `bitset`.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](#op_neq)|Testuje cílový `bitset` nerovnost se zadaným `bitset`.|
|[operátor & =](#op_and_eq)|Provádí bitová kombinace hodnot bitsets s logické `AND` operace.|
|[operátor <<](#op_lshift)|Posune bity `bitset` doleva o zadaný počet pozic a vrátí výsledek do nového `bitset`.|
|[operátor << =](#op_lshift_eq)|Posune bity `bitset` doleva o zadaný počet pozic a vrátí výsledek na cílovou `bitset`.|
|[operator==](#op_eq_eq)|Testuje cílový `bitset` rovnosti se zadaným `bitset`.|
|[operátor >>](#op_rshift)|Posune bity `bitset` doprava o zadaný počet pozic a vrátí výsledek do nového `bitset`.|
|[operator>>=](#op_rshift_eq)|Posune bity `bitset` doprava o zadaný počet pozic a vrátí výsledek na cílovou `bitset`.|
|[– operátor&#91;&#93;](#op_at)|Vrátí odkaz na bit na určené pozici v `bitset` Pokud `bitset` upravitelné; jinak vrátí hodnotu bit na této pozici.|
|[operátor ^ =](#op_xor_eq)|Bitová kombinace hodnot bitsets s exkluzivní provádí `OR` operace.|
|[operator&#124;=](#op_or_eq)|Bitová kombinace hodnot bitsets s také zahrnuto provádí `OR` operace.|
|[operator~](#op_not)|Obrátí všechny bity v cíli `bitset` a vrátí výsledek.|

### <a name="structures"></a>Struktury

|||
|-|-|
|[Hodnota hash](#hash)||

### <a name="all"></a> Všechny

Testy všechny bity v tomto bitset – Chcete-li zjistit, jestli jsou nastavené na hodnotu true.

```cpp
bool all() const;
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí true, pokud jsou splněny všechny bity v této sadě. Vrátí **false** Pokud jeden nebo více bity jsou false.

### <a name="any"></a> Všechny

Ověřuje, zda všechny bity v pořadí je nastavená na 1.

```cpp
bool any() const;
```

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud všechny bity v bitset – je nastavená na 1; **false** Pokud všechny bity jsou 0.

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

### <a name="bitset"></a> bitset –

Vytvoří objekt třídy `bitset\<N>` a inicializuje bity na nulu, nebo některé zadané hodnoty nebo hodnoty získané ze znaků v řetězci.

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

*Val*\
Číslo bez znaménka, jehož vyjádření base dvě slouží k inicializaci bity v bitset – vytváří.

*str*\
Řetězec nulové hodnoty a ty, které slouží k inicializaci bitset – bitové hodnoty.

*_CStr*\
Řetězec C-style nuly a ty, které slouží k inicializaci bitset – bitové hodnoty.

*_Pos*\
Pozice znaku v řetězci, počítací zleva doprava a od nuly, použitý k inicializaci prvního bitu v bitset –.

*Počet*\
Počet znaků v řetězci, který se používá k zadání bity bitset – počáteční hodnoty.

*_Zero*\
Znak, který se používá k reprezentování nulu. Výchozí hodnota je "0".

*_Jedna*\
Znak, který se používá k reprezentování jeden. Výchozí hodnota je '1'.

#### <a name="remarks"></a>Poznámky

Tři konstruktory lze použít k sestavení kompletních obects třídy `bitset\<N>`:

- První konstruktor nepřijímá žádné parametry, vytvoří objekt třídy `bitset\<N>` a inicializuje všechny bity N na výchozí hodnotu nula.

- Druhý konstruktor vytvoří objekt třídy `bitset\<N>` a inicializuje bity pomocí jedné **unsigned long long.** parametru.

- Třetí konstruktor vytvoří objekt třídy `bitset\<N>`, inicializace N bity na hodnoty, které odpovídají znaky součástí řetězce ve stylu jazyka c znaků nulové hodnoty a značky. Volání konstruktoru bez přetypování řetězce na typ řetězec: `bitset<5> b5("01011");`

Existují dvě šablony konstruktor k dispozici:

- První šablona konstruktor vytvoří objekt třídy `bitset\<N>` a inicializuje bitů z písmen podle řetězec nulové hodnoty a značky. Pokud jsou všechny znaky řetězce než 0 nebo 1, vyvolá konstruktor objekt třídy [neplatný argument](../standard-library/invalid-argument-class.md). Pokud zadaná pozice ( *_Pos*) je nad rámec délky řetězce, vyvolá konstruktor objekt třídy [out_of_range –](../standard-library/out-of-range-class.md). Konstruktor nastaví pouze ty bity na pozici *j* v bitset –, pro kterou znaku v řetězci na pozici `_Pos + j` 1. Ve výchozím nastavení *_Pos* je 0.

- Druhý konstruktor šablony je podobný jako první, ale zahrnuje další parametr (*počet*), který se používá k určení počtu bitů inicializace. Má také dva volitelné parametry, *_Zero* a *_Jedna*, která označuje, co znak v *str* , je interpretována jako trochu 0 a 1 bit, v uvedeném pořadí.

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

### <a name="count"></a> Počet

Vrátí počet bitů, nastavte v pořadí verze.

```cpp
size_t count() const;
```

#### <a name="return-value"></a>Návratová hodnota

Nastavit počet bitů v pořadí verze.

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

### <a name="element_type"></a> ELEMENT_TYPE

Typ, který je synonymum pro typ dat **bool** a je možné odkazovat na element bity bitset –.

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

### <a name="flip"></a> Převrátit na ose

Obrátí všechny bity v bitset – hodnota nebo Invertuje jeden bit na určené pozici.

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozice bit, jejíž hodnota má být obrácený.

#### <a name="return-value"></a>Návratová hodnota

Zkopírujte upravený bitset –, pro kterou má členská funkce se vyvolala.

#### <a name="remarks"></a>Poznámky

Druhá členská funkce vyvolá [out_of_range –](../standard-library/out-of-range-class.md) výjimku, pokud je větší než velikost zadaná jako parametr pozice *N* z **bitset –\<**  *N* **>** jehož bit byl obrácený.

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

### <a name="hash"></a> Hodnota hash

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a> None

Testuje, zda byl nastaven žádný bit na hodnotu 1 v objektu bitset –.

```cpp
bool none() const;
```

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud byla nastavena žádná bit bitset – 1. **false** pokud alespoň jeden bit byla nastavena na hodnotu 1.

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

### <a name="op_neq"></a> Operator! =

Testuje na cíl bitset – nerovnosti s zadané bitset –.

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
Bitset –, který je k porovnání s bitset – cíl pro nerovnost.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud bitsets liší; **false** Pokud jsou stejné.

#### <a name="remarks"></a>Poznámky

Bitsets musí být stejné velikosti má být testována nerovnost pomocí členské funkce operátora.

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

### <a name="op_and_eq"></a> – Operátor&amp;=

Provádí bitová kombinace hodnot bitsets s logické `AND` operace.

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*doprava*\
Bitset –, který je bitový kombinovat s bitset – cíl.

#### <a name="return-value"></a>Návratová hodnota

Bitset – změny cílových, která je výsledkem bitový `AND` operaci s bitset – zadán jako parametr.

#### <a name="remarks"></a>Poznámky

Kombinování dva bity `AND` operátor návratový **true** li každý bit na hodnotu true; v opačném případě jejich kombinaci vrátí **false**.

Bitsets musí mít stejnou velikost a nelze jej zkombinovat bitovým operátorem pomocí `AND` operátorem pomocí členské funkce operátora.

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

### <a name="op_lshift"></a> – Operátor\<\<

Posune bity bitset – doleva o zadaný počet pozic a vrátí výsledek do nové bitset –.

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic, které jsou bity bitset – posunutí doleva.

#### <a name="return-value"></a>Návratová hodnota

Upravené bitset – s bity posunuta doleva požadovaný počet pozic.

#### <a name="remarks"></a>Poznámky

Operátor členská funkce vrátí **bitset –** (  **\*to**) **<< = pos,** kde [ <<= ](#op_lshift_eq) posune bity v bitset – doleva o zadaný počet pozic a vrátí výsledek do cílové bitset –.

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

### <a name="op_lshift_eq"></a> – Operátor&lt;&lt;=

Posune bity bitset – doleva o zadaný počet pozic a vrátí výsledek do cílové bitset –.

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic, o bity bitset – jsou posunutí doleva.

#### <a name="return-value"></a>Návratová hodnota

Cílové bitset – upraví tak, aby byly bity posunuta doleva požadovaný počet pozic.

#### <a name="remarks"></a>Poznámky

Pokud neexistuje žádný prvek přesunout do umístění, funkce vymaže bit na hodnotu 0.

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

### <a name="op_eq_eq"></a> Operator ==

Testuje na cíl bitset – rovnosti s zadané bitset –.

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>Parametry

*doprava*\
Bitset –, který je k porovnání s bitset – cíl pro rovnost.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud bitsets jsou stejné. **false** Pokud se liší.

#### <a name="remarks"></a>Poznámky

Bitsets musí mít stejnou velikost má být testována na rovnost pomocí členské funkce operátora.

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

### <a name="op_rshift"></a> – Operátor&gt;&gt;

Posune bity bitset – doprava o zadaný počet pozic a vrátí výsledek do nové bitset –.

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic napravo bity bitset – jsou posunutí.

#### <a name="return-value"></a>Návratová hodnota

Nové bitset – kde bity byla posunuta doprava požadovaný počet pozic vzhledem k cílové bitset –.

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

### <a name="op_rshift_eq"></a> – Operátor&gt;&gt;=

Posune bity bitset – doprava o zadaný počet pozic a vrátí výsledek do cílové bitset –.

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Počet pozic napravo bity bitset – jsou posunutí.

#### <a name="return-value"></a>Návratová hodnota

Cílové bitset – upraví tak, aby byly bity posunuta doprava požadovaný počet pozic.

#### <a name="remarks"></a>Poznámky

Pokud neexistuje žádný prvek přesunout do umístění, funkce vymaže bit na hodnotu 0.

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

### <a name="op_at"></a> Operator [].

Vrátí odkaz na bit na určené pozici v bitset – Pokud je bitset – upravitelné; v opačném případě vrátí hodnotu bit na této pozici.

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozici bitu v rámci bitset – vyhledání.

#### <a name="remarks"></a>Poznámky

Při definování [ \_ITERÁTORU\_ladění\_úroveň](../standard-library/iterator-debug-level.md) jako 1 nebo 2 v sestavení, dojde k chybě v spustitelný soubor Pokud se pokusíte o přístup k prvku mimo hranice bitset –. Další informace najdete v části [Checked Iterators](../standard-library/checked-iterators.md).

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

### <a name="op_xor_eq"></a> operátor ^ =

Bitová kombinace hodnot bitsets s exkluzivní provádí `OR` operace.

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*doprava*\
Bitset –, který je bitový kombinovat s bitset – cíl.

#### <a name="return-value"></a>Návratová hodnota

Bitset – změny cílových, která je výsledkem bitový exkluzivní `OR` operaci s bitset – zadán jako parametr.

#### <a name="remarks"></a>Poznámky

Dva bity v kombinaci podle exkluzivní **nebo** operátor návratový **true** pokud alespoň jeden, ale ne obojí bitů je **true**; v opačném případě vrátí jejich kombinaci **false**.

Bitsets musí mít stejnou velikost a nelze jej zkombinovat bitovým operátorem pomocí exkluzivní `OR` operátorem pomocí členské funkce operátora.

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

### <a name="op_or_eq"></a> operátor&#124;=

Bitová kombinace hodnot bitsets s také zahrnuto provádí `OR` operace.

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>Parametry

*doprava*\
Bitset –, který je bitový kombinovat s bitset – cíl.

#### <a name="return-value"></a>Návratová hodnota

Bitset – změny cílových, která je výsledkem bitový inkluzivní `OR` operaci s bitset – zadán jako parametr.

#### <a name="remarks"></a>Poznámky

Dva bity v kombinaci podle také zahrnuto `OR` operátor návratový **true** pokud alespoň jedna z bitů **true**; Pokud jsou obě bits **false**, jejich kombinaci vrátí **false**.

Bitsets musí mít stejnou velikost a nelze jej zkombinovat bitovým operátorem pomocí také zahrnuto `OR` operátorem pomocí členské funkce operátora.

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

### <a name="op_not"></a> operátor ~

Obrátí všechny bity v bitset – cíl a vrátí výsledek.

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>Návratová hodnota

Bitset – s jeho bity s ohledem na cílovou bitset – obrácený.

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

### <a name="reference"></a> Referenční dokumentace

Třídu proxy, která obsahuje odkazy na bity součástí bitset –, který se používá pro přístup k a manipulaci s jednotlivých bitů jako pomocnou třídu pro `operator[]` z bitset – třída.

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

*Val*\
Hodnota objektu typu **bool** má být přiřazena k bitu v bitset –.

*_Bitref*\
Odkaz ve formuláři *x [i]* bitů na pozici *můžu* v bitset – *x*.

#### <a name="return-value"></a>Návratová hodnota

Odkaz na bit v bitset – určená pozice argumentu pro první, druhý a pátý členské funkce tříd, a **true** nebo **false**, tak, aby odrážely hodnotu upravené bitu v bitset – pro třetí a čtvrtá členská funkce třídy odkazu.

#### <a name="remarks"></a>Poznámky

Třída `reference` existuje pouze jako pomocnou třídu pro bitset – `operator[]`. Člen třídy popisuje objekt, který můžete přístup k individuální verzi v rámci bitset –. Umožní *b* být objekt typu **bool**, *x* a *y* objekty typu **bitset –\<**  *N* **>** , a *můžu* a *j* platná pozice v rámci takového objektu. Zápis *x [i]* odkazuje na pozici bitu *můžu* v bitset – *x*. Členské funkce třídy `reference` v pořadí, zadejte následující operace:

|Operace|Definice|
|---------------|----------------|
|*x*[*i*] = *b*|Úložiště **bool** hodnotu *b* pozici bit *můžu* v bitset – *x*.|
|*x*[*i*] = *y*[*j*]|Uloží hodnotu bitu *y*[ *j*] na pozici bit *můžu* v bitset – *x*.|
|*b* = ~ *x*[*i*]|Uloží hodnotu přetočený bitu *x*[ *můžu*] v **bool** *b*.|
|*b* = *x*[*i*]|Uloží hodnotu bitu *x*[ *můžu*] v **bool** *b*.|
|*x*[*i*]. `flip`( )|Uloží hodnotu přetočený bitu *x*[ *můžu*] zpět na pozici bit *můžu* v *x*.|

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

### <a name="reset"></a> Resetovat

Obnoví všechny bity v bitset – 0 nebo obnoví trochu na určené pozici na hodnotu 0.

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozici bitu v bitset – Chcete-li nastaven na hodnotu 0.

#### <a name="return-value"></a>Návratová hodnota

Kopie bitset –, pro kterou má členská funkce se vyvolala.

#### <a name="remarks"></a>Poznámky

Druhá členská funkce vyvolá [out_of_range –](../standard-library/out-of-range-class.md) výjimku, pokud je zadaná pozice větší než velikost bitset –.

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

### <a name="set"></a> Nastavit

Nastaví všechny bity v bitset – 1 a nastaví bit na určenou pozici do 1.

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozici bitu v bitset – nastavit přiřazena hodnota.

*Val*\
Hodnota má být přiřazena k bitu na zadané pozici.

#### <a name="return-value"></a>Návratová hodnota

Kopie bitset –, pro kterou má členská funkce se vyvolala.

#### <a name="remarks"></a>Poznámky

Druhá členská funkce vyvolá [out_of_range –](../standard-library/out-of-range-class.md) výjimku, pokud je zadaná pozice větší než velikost bitset –.

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

### <a name="size"></a> Velikost

Vrátí počet bitů v objektu bitset –.

```cpp
size_t size() const;
```

#### <a name="return-value"></a>Návratová hodnota

Počet bitů, *N*, v bitset –\<N >.

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

### <a name="test"></a> Test

Ověřuje, zda je bit na určené pozici v bitset – nastavený na hodnotu 1.

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>Parametry

*_Pos*\
Pozici bitu v bitset – má být testována pro jeho hodnotu.

#### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** pokud bit určené pozice argumentu je nastavená na 1; v opačném případě **false**.

#### <a name="remarks"></a>Poznámky

Členská funkce vyvolá [out_of_range –](../standard-library/out-of-range-class.md)

### <a name="to_string"></a> to_string

Převede objekt bitset – na řetězcovou reprezentaci.

```
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>Návratová hodnota

Objekt string třídy `basic_string`, kde každý bit sady v bitset – nemá odpovídající znak, 1, a znak 0, pokud je bit není nastavena.

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

### <a name="to_ullong"></a> to_ullong –

Vrátí **unsigned long long.** hodnotu, která obsahuje stejné bitů nastaven jako obsah objektu bitset –.

```
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí součet bitové hodnoty, které jsou v pořadí verze jako **unsigned long long.** . To **unsigned long long.** hodnotu by znovu vytvořit stejnou sadu bitů, pokud je použita k inicializaci bitset –.

#### <a name="exceptions"></a>Výjimky

Vyvolá [overflow_error –](overflow-error-class.md) objektu, pokud všechny bity v pořadí bitů má bitová hodnota, která nemůže být reprezentovaná jako hodnotu typu **unsigned long long.** .

#### <a name="remarks"></a>Poznámky

Vrátí součet bitové hodnoty, které jsou v pořadí verze jako **unsigned long long.** .

### <a name="to_ulong"></a> to_ulong –

Bitset – objekt převede na číslo, které vygenerují pořadí bitů, pokud je použita k inicializaci bitset –.

```
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>Návratová hodnota

Celé číslo, které by generovat bity bitset – Pokud se používá při inicializaci bitset –.

#### <a name="remarks"></a>Poznámky

Použití členská funkce vrátí celé číslo, který má stejné posloupností číslic 0 a 1, protože se nachází v pořadí bitů bitset –.

Členská funkce vyvolá [overflow_error –](overflow-error-class.md) objektu, pokud všechny bity v pořadí bitů má bitová hodnota, která nemůže být reprezentovaná jako hodnotu typu **unsigned long**.

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
