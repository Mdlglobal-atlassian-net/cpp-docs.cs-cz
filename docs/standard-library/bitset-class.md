---
title: "bitset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 542be13898b18fb6f73a724eebe72f135f7ebde2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="bitset-class"></a>bitset – třída
Popisuje typ objektu, který ukládá pořadí, který se skládá z pevný počet bitů, které poskytují compact kvůli udržení příznaky pro sadu položek nebo podmínky. Bitset – třída podporuje operace s objekty typu bitset, které obsahují kolekci bitů a poskytují konstanta běhu je přístup k každý bit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <size_t N>  
class bitset  
```  
  
#### <a name="parameters"></a>Parametry  
 *N*  
 Určuje počet bitů v objektu bitset nenulové hodnoty v celé typu **size_t –** , musí být známo v době kompilace.  
  
## <a name="remarks"></a>Poznámky  
 Na rozdíl od podobné [vektoru\<bool > třída](../standard-library/vector-bool-class.md), bitset – třída nemá iterátory a není kontejner standardní knihovna C++. Se také liší od vektoru\<bool > podle vrácení některé konkrétní velikost, která je stanovena v době kompilace v souladu s velikosti určené parametrem šablony **N** při **bitset\<N\>**  je deklarován.  
  
 Bit je nastavit, pokud je jeho hodnota je 1 a obnovit, pokud je jeho hodnota je 0. Překlopit nebo Invertovat chvilku je změnit svou hodnotu z hodnoty 1 na 0 nebo od 0 do 1. **N** bitů bitset jsou indexované podle hodnoty celé číslo od 0 do **N** -1, kde 0 indexuje první pozici bit a **N** – 1 konečné bit pozici.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[bitset –](#bitset)|Vytvoří objekt třídy `bitset\<N>` a inicializuje bits na nulu, některé zadanou hodnotu nebo hodnoty získané z znaky v řetězci.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[ELEMENT_TYPE](#element_type)|Typ, který je pro datový typ synonymum `bool` a může sloužit k odkazování element bitů `bitset`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[všechny](#all)|Testy všechny bity v tomto `bitset` zjistěte, zda jsou všechny nastaven na `true`.|  
|[všechny](#any)|Členská funkce ověřuje, zda všechny bit v pořadí hodnotu 1.|  
|[počet](#count)|Členská funkce vrátí počet bitů, nastavte v pořadí bit.|  
|[Překlopit](#flip)|Invertuje výběr všechny bity v hodnotě `bitset` nebo Invertuje výběr jeden bit na zadané pozici.|  
|[None](#none)|Testuje, pokud byl nastaven na hodnotu 1 v žádné bit `bitset` objektu.|  
|[resetování](#reset)|Obnoví všechny bity v `bitset` na hodnotu 0 nebo resetování trochu na zadané pozici 0.|  
|[nastavení](#set)|Nastaví službu bits `bitset` na 1 nebo nastaví trochu na zadané pozici 1.|  
|[velikost](#size)|Vrátí počet bitů `bitset` objektu.|  
|[Test](#test)|Testy zda bit na zadané pozici v `bitset` je nastaven na hodnotu 1.|  
|[to_string –](#to_string)|Převede `bitset` řetězcovou reprezentaci objektu.|  
|[to_ullong –](#to_ullong)|Vrátí součet bitových hodnot v `bitset` jako `unsigned long long`.|  
|[to_ulong –](#to_ulong)|Převede `bitset` do objektu `unsigned long` , vytvoří posloupnost bitů obsažené Pokud použitý k inicializaci `bitset`.|  
  
### <a name="member-classes"></a>Člen třídy  
  
|||  
|-|-|  
|[referenční dokumentace](#reference)|Třídu proxy, který odkazuje na bits obsažené v `bitset` používané pro přístup k a jako pomocná třída pro manipulaci s jednotlivých bitů `operator[]` třídy `bitset`.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[Operator! =](#op_neq)|Testy cíl `bitset` nerovnost se zadaným `bitset`.|  
|[operátor & =](#op_and_eq)|Provede bitovou kombinaci bitové sady s logické `AND` operaci.|  
|[operátor <<](#op_lshift)|Posune bitů v `bitset` doleva o zadaný počet pozic a vrátí výsledek na nový `bitset`.|  
|[operátor << =](#op_lshift_eq)|Posune bitů v `bitset` doleva o zadaný počet pozic a vrátí výsledek na cílovou `bitset`.|  
|[Operator ==](#op_eq_eq)|Testy cíl `bitset` rovnosti se zadaným `bitset`.|  
|[operátor >>](#op_rshift)|Posune bitů v `bitset` doprava o zadaný počet pozic a vrátí výsledek na nový `bitset`.|  
|[operátor >> =](#op_rshift_eq)|Posune bitů v `bitset` doprava o zadaný počet pozic a vrátí výsledek na cílovou `bitset`.|  
|[operátor &#91; &#93;](#op_at)|Vrátí odkaz na bit na zadané pozici v `bitset` Pokud `bitset` je upravitelnými, jinak vrátí hodnotu verze na této pozici.|  
|[Operator ^ =](#op_xor_eq)|Provede bitovou kombinaci bitové sady s exkluzivní `OR` operaci.|  
|[operátor &#124; =](#op_or_eq')|Provede bitovou kombinaci bitové sady s včetně `OR` operaci.|  
|[operátor ~](#op_dtor)|Invertuje výběr všechny bity v cíl `bitset` a vrátí výsledek.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<bitset >  
  
 **Namespace:** – std  
  
##  <a name="all"></a>bitset::all  
 Všechny bity testů v této bitset – zjistěte, pokud jsou všechny nastaven na hodnotu true.  
  
```  
bool all() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu true, pokud všechny bity v této sadě mají hodnotu true. Vrátí **false** Pokud jeden nebo více bitů hodnotu false.  
  
##  <a name="any"></a>bitset::Any  
 Ověřuje, zda všechny bit v pořadí hodnotu 1.  
  
```  
bool any() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud žádné bit v bitset je nastavený na 1; **false** Pokud všechny bity mají hodnotu 0.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="bitset"></a>bitset::bitset  
 Vytvoří objekt třídy `bitset\<N>` a inicializuje bitů na hodnotu nula, nebo některé zadanou hodnotu nebo hodnoty získané z znaky v řetězci.  
  
```  
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
  
### <a name="parameters"></a>Parametry  
 `val`  
 Číslo bez znaménka, jehož základní dva reprezentace slouží k inicializaci bity v bitset vytvářen.  
  
 `str`  
 Řetězec nulami a ty, které slouží k chybě při inicializaci bitset bitových hodnot.  
  
 `_CStr`  
 Řetězec stylu jazyka C s nulami a ty, které slouží k chybě při inicializaci bitset bitových hodnot.  
  
 `_Pos`  
 Pozice znaku v řetězci, počítání zleva doprava a od nuly, použitý k inicializaci první bit v bitset.  
  
 `count`  
 Počet znaků v řetězci, který slouží k poskytování počáteční hodnoty pro službu bits v bitset.  
  
 `_Zero`  
 Znak, který se používá k reprezentování nulu. Výchozí hodnota je '0'.  
  
 `_One`  
 Znak, který se používá k reprezentování a. Výchozí hodnota je '1'.  
  
### <a name="remarks"></a>Poznámky  
 Tři konstruktory lze použít k vytvoření obects třídy `bitset\<N>`:  
  
-   První konstruktor přijímá žádné parametry, vytvoří objekt třídy `bitset\<N>` a inicializuje všechny bity N na výchozí hodnotu nula.  
  
-   Druhý konstruktor vytvoří objekt třídy `bitset\<N>` a inicializuje bity pomocí jedné `unsigned long long` parametr.  
  
-   Třetí konstruktoru vytvoří objekt třídy `bitset\<N>`, inicializace z N bits hodnoty, které odpovídají znaky řetězec znaků stylu jazyka c nulami a ty, které jsou součástí. Volat konstruktor bez přetypování řetězec do typu string:`bitset<5> b5("01011");`  
  
 Existují dvě šablony konstruktor poskytuje:  
  
-   První šablona konstruktoru vytvoří objekt třídy `bitset\<N>` a inicializuje bits ze znaků uvedených v řetězec nulami a ty, které jsou. Pokud se žádné znaky řetězce než 0 nebo 1, konstruktoru vyvolá objekt třídy [neplatný argument](../standard-library/invalid-argument-class.md). Pokud zadané pozici ( `_Pos`), je nad rámec délky řetězce, pak konstruktoru vyvolá objekt třídy [out_of_range](../standard-library/out-of-range-class.md). Konstruktor nastaví jenom tyto služby bits na pozici *j* v bitset, pro který znak v řetězci na pozici `_Pos + j` je 1. Ve výchozím nastavení `_Pos` je 0.  
  
-   Druhý konstruktor šablony je podobná první, ale zahrnuje další parametr ( `count`) používané k určení počtu bitů k chybě při inicializaci. Má také dva volitelné parametry, `_Zero` a `_One`, která označuje, co znak v `str` se budou interpretovat znamená úplně bitem 0 a 1 bit.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="count"></a>bitset::Count  
 Vrátí počet bitů, nastavte v pořadí bit.  
  
```  
size_t count() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
Počet bitů, nastavte v pořadí bit.  
  
### <a name="example"></a>Příklad  
  
Následující příklad ukazuje použití bitset::count – členská funkce.  
  
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
  
##  <a name="element_type"></a>bitset::ELEMENT_TYPE  
 Typ, který je pro datový typ synonymum `bool` a slouží k odkazování element bitů bitset.  
  
```  
typedef bool element_type;  
```  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="flip"></a>bitset::Flip  
 Invertuje výběr hodnotu službu bits bitset nebo Invertuje výběr jeden bit na zadané pozici.  
  
```  
bitset\<N>& flip();  
bitset\<N>& flip(size_t _Pos);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Pozice bit, jehož hodnota má být obrácený.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie upravené bitset, pro kterou byl vyvolán – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 Funkci druhý člen, vyvolá [out_of_range](../standard-library/out-of-range-class.md) Pokud pozice zadána jako parametr je větší než velikost *N* z **bitset\<**  *N*  **>**  jejichž bit byl obrácený.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="none"></a>bitset::none  
 Testy, pokud žádný bit byla nastavena na 1 v bitset objektu.  
  
```  
bool none() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** -li žádné bitů bitset nastavena na hodnotu 1; **false** pokud alespoň jeden bit byla nastavena na hodnotu 1.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="op_neq"></a>bitset::Operator! =  
 Testuje cílový bitset nerovnost s zadaný bitset.  
  
```  
bool operator!=(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Bitset –, který se má porovnat s bitset cíl nerovnost.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud jiné; bitové sady **false** Pokud jsou stejné.  
  
### <a name="remarks"></a>Poznámky  
 Bitové sady musí mít stejnou velikost má být testována nerovnost operátor funkcí člen.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="op_and_eq"></a>bitset::Operator&amp;=  
 Provede bitovou kombinaci bitové sady s logické **a** operaci.  
  
```  
bitset\<N>& operator&=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Bitset –, které má bitový kombinovat s bitset cíl.  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitset – upravené cíl, který je výsledkem bitové hodnotě **a** operaci s bitset zadána jako parametr.  
  
### <a name="remarks"></a>Poznámky  
 Dva bity kombinaci podle **a** operátor návratový **true** Pokud je každý bit true; jinak, jejich kombinaci vrátí **false**.  
  
 Bitové sady musí mít stejnou velikost a nelze jej zkombinovat bitový s **a** operátor operátor funkcí člen.  
  
### <a name="example"></a>Příklad  
  
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
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
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

##  <a name="op_lshift"></a>bitset::Operator\<\<    
  
Posune bitů v bitset doleva o zadaný počet pozic a vrátí výsledek do nové bitset.  
  
```  
bitset\<N> operator<<(size_t _Pos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Počet pozic, které jsou bity v bitset posunutí doleva.  
  
### <a name="return-value"></a>Návratová hodnota  
 Upravené bitset s bity zapuštěno vlevo požadovaný počet pozic.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí – členská funkce operátor **bitset**(  **\*to**) **<< = pos,** kde [ <<= ](#op_lshift_eq) posune bity v bitset doleva o zadaný počet pozic a vrátí výsledek do cílové bitset.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="op_lshift_eq"></a>bitset::Operator&lt;&lt;=  
 Posune bitů v bitset doleva o zadaný počet pozic a vrátí výsledek do cílové bitset.  
  
```  
bitset\<N>& operator<<=(size_t _Pos);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Počet pozic na levé straně, že jsou bity v bitset posunutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Cílové bitset upravit tak, aby byly bitů doleva zapuštěno požadovaný počet pozic.  
  
### <a name="remarks"></a>Poznámky  
 Pokud žádný element existuje se posunou do pozice, funkce vypne bity na hodnotu 0.  
  
### <a name="example"></a>Příklad  
  
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
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 00111 ).  
After shifting the bits 2 positions to the left,  
 the target bitset b1 becomes: ( 11100 ).  
```  
  
##  <a name="op_eq_eq"></a>bitset::Operator ==  
 Testuje cílový bitset rovnosti s zadaný bitset.  
  
```  
bool operator==(const bitset\<N>& right) const;
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Bitset –, který se má porovnat s bitset cíl rovnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud bitové sady jsou stejné. **false** Pokud se liší.  
  
### <a name="remarks"></a>Poznámky  
 Bitové sady musí mít stejnou velikost má být testována rovnosti operátor funkcí člen.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="op_rshift"></a>bitset::Operator&gt;&gt;  
 Posune bitů v bitset doprava o zadaný počet pozic a vrátí výsledek do nové bitset.  
  
```  
bitset\<N> operator>>(size_t _Pos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Počet pozic vpravo bity v bitset jsou posunutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové bitset, kde byla bity zapuštěno vpravo požadovaný počet pozic vzhledem k cílové bitset.  
  
### <a name="example"></a>Příklad  
  
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
        << " the bitset b2 is: ( "<< b2 << " )."  
        << endl;  
   bitset<5> b3 = b2 >> 1;  
  
   cout << "After shifting the bits 1 position to the right,\n"  
        << " the bitset b3 is: ( " << b3 << " )."  
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
  
##  <a name="op_rshift_eq"></a>bitset::Operator&gt;&gt;=  
 Posune bitů v bitset doprava o zadaný počet pozic a vrátí výsledek do cílové bitset.  
  
```  
bitset\<N>& operator>>=(size_t _Pos);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Počet pozic vpravo bity v bitset jsou posunutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Cílové bitset upravit tak, aby byly bity zapuštěno vpravo požadovaný počet pozic.  
  
### <a name="remarks"></a>Poznámky  
 Pokud žádný element existuje se posunou do pozice, funkce vypne bity na hodnotu 0.  
  
### <a name="example"></a>Příklad  
  
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
        << " the target bitset b1 becomes: ( "<< b1 << " )."   
        << endl;  
}  
```  
  
```Output  
The target bitset b1 is: ( 11100 ).  
After shifting the bits 2 positions to the right,  
 the target bitset b1 becomes: ( 00111 ).  
```  
  
##  <a name="op_at"></a>bitset::Operator]  
 Vrátí odkaz na bit na zadané pozici v bitset – Pokud je bitset upravitelnými; jinak vrátí hodnotu verze na této pozici.  
  
```  
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Pozice vyhledání bit v rámci bitset.  
  
### <a name="remarks"></a>Poznámky  
Když definujete [ \_ITERATOR\_ladění\_úroveň](../standard-library/iterator-debug-level.md) jako 1 nebo 2 v buildu běhová chyba dojde při vaší spustitelný soubor při pokusu o přístup k elementu mimo hranice bitset. Chcete-li – další informace, najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md).  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="op_xor_eq"></a>bitset::Operator ^ =  
 Provede bitovou kombinaci bitové sady s exkluzivní `OR` operaci.  
  
```  
bitset\<N>& operator^=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Bitset –, které má bitový kombinovat s bitset cíl.  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitset – upravené cíl, který je výsledkem bitový exkluzivní `OR` operaci s bitset zadána jako parametr.  
  
### <a name="remarks"></a>Poznámky  
 Dva bity kombinaci podle exkluzivní **nebo** operátor návratový **true** pokud alespoň jeden, ale ne obojí bity je **true**, jinak hodnota jejich kombinaci vrátí **false**.  
  
 Bitové sady musí mít stejnou velikost a nelze jej zkombinovat bitový s exkluzivní `OR` operátor operátor funkcí člen.  
  
### <a name="example"></a>Příklad  
  
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
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
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
  
##  <a name="op_or_eq"></a>bitset::Operator &#124; =  
 Provede bitovou kombinaci bitové sady s včetně `OR` operaci.  
  
```  
bitset\<N>& operator|=(const bitset\<N>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Bitset –, které má bitový kombinovat s bitset cíl.  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitset – upravené cíl, který je výsledkem bitové hodnotě včetně `OR` operaci s bitset zadána jako parametr.  
  
### <a name="remarks"></a>Poznámky  
 Dva bity kombinaci pomocí včetně `OR` operátor návratový **true** pokud alespoň jedna z bitů **true**; Pokud jsou obě bits **false**, vrátí jejich kombinaci **false**.  
  
 Bitové sady musí mít stejnou velikost a nelze jej zkombinovat bitový s včetně `OR` operátor operátor funkcí člen.  
  
### <a name="example"></a>Příklad  
  
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
        << " the target bitset b1 becomes:   ( "<< b1 << " )."   
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
  
##  <a name="op_dtor"></a>bitset::Operator ~  
 Invertuje výběr všechny bity v cílové bitset a vrátí výsledek.  
  
```  
bitset\<N> operator~() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitset – s jeho bity s ohledem na cílové bitset obrácený.  
  
### <a name="example"></a>Příklad  
  
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
  
##  <a name="reference"></a>bitset::Reference  
 Třídu proxy, který odkazuje na bits obsažené v bitset, který se používá pro přístup k a jako pomocná třída pro manipulaci s jednotlivých bitů `operator[]` z bitset – třída.  
  
```  
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
  
### <a name="parameters"></a>Parametry  
 `val`  
 Hodnota typu objektu `bool` přiřazení trochu v bitset.  
  
 `_Bitref`  
 Odkaz formulář *x [i]* na verzi na pozici *i* v bitset *x*.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na bit v bitset určeného pozici argument pro první, druhý a páté členské funkce tříd, a **true** nebo **false**, tak, aby odrážela hodnotu upravené bitové v bitset – pro třetí a čtvrtý členské funkce odkazu na třídu.  
  
### <a name="remarks"></a>Poznámky  
 Třída `reference` existuje jenom jako pomocná třída pro bitset `operator[]`. Třída členů popisuje objekt, který následuje jednotlivých bit v rámci bitset přístup. Umožní *b* se objekt typu `bool`, *x* a *y* objekty typu **bitset\<***N*  **>** , a *i* a *j* platný pozice v rámci takového objektu. Notace *x [i]* odkazuje bit na pozici *i* v bitset *x*. Funkce člena třídy `reference` zadejte postupně následující operace:  
  
|Operace|Definice|  
|---------------|----------------|  
|*x*[*i*] = *b*|Úložiště `bool` hodnotu *b* na pozici bit *i* v bitset *x*.|  
|*x*[*i*] = *y*[*j*]|Ukládá hodnotu identifikátoru bitu *y*[ *j*] na pozici bit *i* v bitset *x*.|  
|*b* = ~ *x*[*i*]|Uloží hodnotu přetočený bitu *x*[ *i*] v `bool` *b*.|  
|*b* = *x*[*i*]|Ukládá hodnotu identifikátoru bitu *x*[ *i*] v `bool` *b*.|  
|*x*[*i*]. `flip`( )|Uloží hodnotu přetočený bitu *x*[ *i*] zpět na pozici bit *i* v *x*.|  
  
### <a name="example"></a>Příklad  
  
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
        << " is: ( "<< b1 << " )" << endl;  
  
   // Example of x [i] = y [j] storing the bool value of the  
   // bit at position j in bitset y at bit position i in bitset x  
   b2 [4] = b1 [0];      // b1 [0] = true  
   cout << "The bitset<5> b2 with the bit at position 4 set to the "  
        << "value\n of the bit at position 0 of the bit in "  
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
        << "bitset b2,\n it is ( "<<  b2  << " )." << endl;  
   b2 [4].flip( );  
   cout << "After flipping the value of the bit at position 4 in "  
        << "bitset b2,\n it becomes ( "<<  b2  << " )." << endl;  
   bool c;  
   c = b2 [4].flip( );  
   cout << "After a second flip, the value of the position 4"  
        << " bit in b2 is now: " << c << ".";  
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
  
##  <a name="reset"></a>bitset::Reset  
 Obnoví službu bits bitset na 0 nebo obnoví trochu na zadané pozici 0.  
  
```  
bitset\<N>& reset();  
bitset\<N>& reset(size_t _Pos);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Pozice bitu v bitset – Chcete-li nastaven na hodnotu 0.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie bitset, pro kterou byl vyvolán – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 Funkci druhý člen, vyvolá [out_of_range](../standard-library/out-of-range-class.md) výjimka, pokud je větší než velikost bitset pozice zadána.  
  
### <a name="example"></a>Příklad  
  
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
        << " third bit of bitset b1 is: ( "<< b1r3 << " )"   
        << endl;  
  
   bitset<5> b1r;  
   b1r = b1.reset( );  
   cout << "The collecion of bits obtained from resetting all\n"  
        << " the elements of the bitset b1 is: ( "<< b1r << " )"  
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
  
##  <a name="set"></a>bitset::set  
 Nastaví všechny bity v bitset na 1 nebo nastaví trochu na zadané pozici 1.  
  
```   
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,   
    bool val = true);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Pozice bitu v bitset být nastavena na přiřazenou hodnotu.  
  
 `val`  
 Hodnota pro přiřazení ke bit na zadané pozici.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie bitset, pro kterou byl vyvolán – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 Funkci druhý člen, vyvolá [out_of_range](../standard-library/out-of-range-class.md) výjimka, pokud je větší než velikost bitset pozice zadána.  
  
### <a name="example"></a>Příklad  
  
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
        << " zeroth bit of bitset b1 is: ( "<< b1s0 << " )"   
        << endl;  
  
   bitset<5> bs1;  
   bs1 = b1.set( );  
   cout << "The collecion of bits obtained from setting all the\n"  
        << " elements of the bitset b1 is: ( "<< bs1 << " )"  
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
  
##  <a name="size"></a>bitset::size  
 Vrátí počet bitů v bitset objektu.  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bitů, *N*, v bitset\<N >.  
  
### <a name="example"></a>Příklad  
  Následující příklad ukazuje použití bitset::size – členská funkce.  
  
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
  
##  <a name="test"></a>bitset::test  
 Ověřuje, zda je bit na zadané pozici v bitset nastaven na hodnotu 1.  
  
```  
bool test(size_t _Pos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Pozice bitu v bitset má být testována pro jeho hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud je bit určeného pozice argument nastavený na hodnotu 1; jinak **false**.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vyvolá [out_of_range](../standard-library/out-of-range-class.md)

