---
title: fpos – třída
ms.date: 03/27/2019
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: 78b136d72067fa5fff58e8a7acc044fb4e1a409e
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565059"
---
# <a name="fpos-class"></a>fpos – třída

Třída šablony popisuje objekt, který můžete uložit všechny informace potřebné k obnovení Indikátor pozice souboru v libovolné v rámci jakékoli služby stream. Objekt fpos – třída\< **St**> efektivně ukládá aspoň dva členské objekty:

- Posun bajtů, typu [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Převod stavu, pro použití v objektu basic_filebuf – třída, typu `St`, obvykle `mbstate_t`.

Můžete také ukládat pozice libovolného souboru, pro použití objektem třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md), typu `fpos_t`. Pro prostředí s omezenou velikost souboru však `streamoff` a `fpos_t` může být někdy používat Zaměnitelně. Pro prostředí, které mají kódování závislá na stavu, se žádné streamy `mbstate_t` ve skutečnosti může nevyužité. Proto se mohou lišit počet uložených objektů členů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parametry

*Statetype*<br/>
Informace o stavu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[fpos –](#fpos)|Vytvoření objektu, který obsahuje informace o poloze (posun) v datovém proudu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[seekpos](#seekpos)|Interně jej využívá standardní knihovny C++ pouze. Nevolejte tuto metodu v kódu.|
|[state](#state)|Nastaví nebo vrátí stav převodu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Ukazatele pozice v souboru testy pro nerovnost.|
|[Operator +](#op_add)|Zvýší Indikátor pozice v souboru.|
|[operator+=](#op_add_eq)|Zvýší Indikátor pozice v souboru.|
|[Operator-](#operator-)|Indikátor pozice souboru sníží.|
|[operator-=](#operator-_eq)|Indikátor pozice souboru sníží.|
|[operator==](#op_eq_eq)|Ukazatele pozice v souboru testy pro rovnost.|
|[streamoff – operátor](#op_streamoff)|Objekt přetypování typu `fpos` na objekt typu `streamoff`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ios >

**Namespace:** std

## <a name="fpos"></a>  fpos::fpos

Vytvoření objektu, který obsahuje informace o poloze (posun) v datovém proudu.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Posun do datového proudu.

*_Stavu*<br/>
Počáteční stav `fpos` objektu.

*_Filepos*<br/>
Posun do datového proudu.

### <a name="remarks"></a>Poznámky

První konstruktor ukládá posun *_Off*, relativní na začátek souboru a ve stavu počáteční převod (Pokud je to, který je). Pokud *_Off* -1, je výsledný objekt představuje pozici neplatný datový proud.

Druhý konstruktor ukládá nulové posunutí a objekt *_stavu*.

## <a name="op_neq"></a>  fpos::Operator! =

Ukazatele pozice v souboru testy pro nerovnost.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Indikátor pozice v souboru, vůči kterému chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud ukazatele pozice v souboru nejsou stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `!(*this == right)`.

### <a name="example"></a>Příklad

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="op_add"></a>  fpos::Operator +

Zvýší Indikátor pozice v souboru.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Posun, podle kterého chcete zvýšit Indikátor pozice v souboru.

### <a name="return-value"></a>Návratová hodnota

Pozice v souboru.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **fpos – (\*to) +=** `_Off`.

### <a name="example"></a>Příklad

Zobrazit [operátor! =](#op_neq) ukázku použití `operator+`.

## <a name="op_add_eq"></a>  fpos::Operator +=

Zvýší Indikátor pozice v souboru.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Posun, podle kterého chcete zvýšit Indikátor pozice v souboru.

### <a name="return-value"></a>Návratová hodnota

Pozice v souboru.

### <a name="remarks"></a>Poznámky

Přidá členskou funkci *_Off* uložené posunu členský objekt a vrátí  **\*to**. Pro umístění v rámci souboru, výsledkem je obecně platný pouze pro binární datové proudy, které nemají v kódování závislá na stavu.

### <a name="example"></a>Příklad

Zobrazit [operátor! =](#op_neq) ukázku použití `operator+=`.

## <a name="operator-"></a>  fpos::Operator-

Indikátor pozice souboru sníží.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Pozice v souboru.

*_Off*<br/>
Posun Stream.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí `(streamoff)*this - (streamoff) right`. Druhá členská funkce vrátí `fpos(*this) -= _Off`.

### <a name="example"></a>Příklad

Zobrazit [operátor! =](#op_neq) ukázku použití `operator-`.

## <a name="operator-_eq"></a>  fpos::Operator-=

Indikátor pozice souboru sníží.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Posun Stream.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí `fpos(*this) -= _Off`.

### <a name="remarks"></a>Poznámky

Pro umístění v rámci souboru, výsledkem je obecně platný pouze pro binární datové proudy, které nemají v kódování závislá na stavu.

### <a name="example"></a>Příklad

Zobrazit [operátor! =](#op_neq) ukázku použití `operator-=`.

## <a name="op_eq_eq"></a>  fpos::Operator ==

Ukazatele pozice v souboru testy pro rovnost.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Indikátor pozice v souboru, vůči kterému chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud ukazatele pozice v souboru jsou stejné; jinak **false**.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `(streamoff)*this == (streamoff)right`.

### <a name="example"></a>Příklad

Zobrazit [operátor! =](#op_neq) ukázku použití `operator+=`.

## <a name="op_streamoff"></a>  fpos::Operator streamoff

Objekt přetypování typu `fpos` na objekt typu `streamoff`.

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený posunu člen objekt a žádné další odsazení uložené jako součást `fpos_t` členský objekt.

### <a name="example"></a>Příklad

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="seekpos"></a>  fpos::seekpos

Tato metoda používá standardní knihovny C++ pouze interně. Nevolejte tuto metodu v kódu.

```cpp
fpos_t seekpos() const;
```

## <a name="state"></a>  fpos::State

Nastaví nebo vrátí stav převodu.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Nový stav převodu.

### <a name="return-value"></a>Návratová hodnota

Převod stavu.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí hodnotu uloženou v `St` členský objekt. Druhá funkce úložišť člen *_stavu* v `St` členský objekt.

### <a name="example"></a>Příklad

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
