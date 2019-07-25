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
ms.openlocfilehash: 60d7d00e6b9426df9b3086d9b82deaf1fdd1463c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454149"
---
# <a name="fpos-class"></a>fpos – třída

Třída šablony popisuje objekt, který může ukládat všechny informace potřebné k obnovení libovolného indikátoru pozice souboru v jakémkoli datovém proudu. Objekt třídy fpos\< **St**> efektivně ukládá alespoň dva členské objekty:

- Posun bajtů typu [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Stav konverze pro použití objektem třídy basic_filebuf typu `St`, obvykle. `mbstate_t`

Může také uložit libovolné umístění souboru pro použití objektem třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)typu `fpos_t`. Pro prostředí s omezeným počtem souborů se ale `streamoff` `fpos_t` může v některých případech použít zaměnitelné. Pro prostředí bez datových proudů, které mají kódování závislé na stavu, `mbstate_t` může být ve skutečnosti nepoužitelné. Proto se počet uložených členských objektů může lišit.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parametry

*Statetype*\
Informace o stavu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[fpos](#fpos)|Vytvoří objekt, který obsahuje informace o pozici (posunu) v datovém proudu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[seekpos](#seekpos)|Používáno interně C++ pouze standardním knihovnou. Nevolejte tuto metodu z vašeho kódu.|
|[státech](#state)|Nastaví nebo vrátí stav převodu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](#op_neq)|Testuje indikátory pozice souboru pro nerovnost.|
|[operator + – operátor](#op_add)|Zvýší ukazatel pozice v souboru.|
|[operator+=](#op_add_eq)|Zvýší ukazatel pozice v souboru.|
|[podnikatel](#operator-)|Sníží ukazatel pozice v souboru.|
|[operator-=](#operator-_eq)|Sníží ukazatel pozice v souboru.|
|[operator==](#op_eq_eq)|Testuje indikátory pozice souboru pro rovnost.|
|[operátor streamoff](#op_streamoff)|Přetypování objekt typu `fpos` na objekt typu `streamoff`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> pro iOS

**Obor názvů:** std

## <a name="fpos"></a>fpos:: fpos

Vytvoří objekt, který obsahuje informace o pozici (posunu) v datovém proudu.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun do datového proudu.

*_State*\
Počáteční stav `fpos` objektu.

*_Filepos*\
Posun do datového proudu.

### <a name="remarks"></a>Poznámky

První konstruktor ukládá *_Off*posunu vzhledem k začátku souboru a ve stavu prvotního převodu (pokud to je v tomto případě). Pokud je *_Off* -1, výsledný objekt představuje neplatnou pozici streamu.

Druhý konstruktor ukládá nulový posun a objekt *_State*.

## <a name="op_neq"></a>fpos:: operator! =

Testuje indikátory pozice souboru pro nerovnost.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Indikátor pozice souboru, u kterého se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se indikátory pozice souboru neshodují, jinak **false**.

### <a name="remarks"></a>Poznámky

Vrátí `!(*this == right)`členské funkce.

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

## <a name="op_add"></a>fpos:: operator + – operátor

Zvýší ukazatel pozice v souboru.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, kterým chcete zvýšit ukazatel pozice souboru.

### <a name="return-value"></a>Návratová hodnota

Pozice v souboru.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí **fpos (\*this) + =.** `_Off`

### <a name="example"></a>Příklad

Ukázku použití `operator+`naleznete v tématu [Operator! =](#op_neq) .

## <a name="op_add_eq"></a>fpos:: operator + =

Zvýší ukazatel pozice v souboru.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, kterým chcete zvýšit ukazatel pozice souboru.

### <a name="return-value"></a>Návratová hodnota

Pozice v souboru.

### <a name="remarks"></a>Poznámky

Členská funkce přidá *_Off* k uloženému členskému objektu posunu a pak  **\*ho vrátí.** Pro umístění v rámci souboru je výsledek obecně platný pouze pro binární proudy, které nemají kódování závislé na stavu.

### <a name="example"></a>Příklad

Ukázku použití `operator+=`naleznete v tématu [Operator! =](#op_neq) .

## <a name="operator-"></a>fpos:: operator-

Sníží ukazatel pozice v souboru.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Pozice souboru.

*_Off*\
Posun datového proudu.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí `(streamoff)*this - (streamoff) right`. Druhá členská funkce vrátí `fpos(*this) -= _Off`.

### <a name="example"></a>Příklad

Ukázku použití `operator-`naleznete v tématu [Operator! =](#op_neq) .

## <a name="operator-_eq"></a>fpos:: operator-=

Sníží ukazatel pozice v souboru.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun datového proudu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `fpos(*this) -= _Off`členské funkce.

### <a name="remarks"></a>Poznámky

Pro umístění v rámci souboru je výsledek obecně platný pouze pro binární proudy, které nemají kódování závislé na stavu.

### <a name="example"></a>Příklad

Ukázku použití `operator-=`naleznete v tématu [Operator! =](#op_neq) .

## <a name="op_eq_eq"></a>fpos:: operator = = – operátor

Testuje indikátory pozice souboru pro rovnost.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknutím*\
Indikátor pozice souboru, u kterého se má porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou indikátory pozice souboru stejné; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Vrátí `(streamoff)*this == (streamoff)right`členské funkce.

### <a name="example"></a>Příklad

Ukázku použití `operator+=`naleznete v tématu [Operator! =](#op_neq) .

## <a name="op_streamoff"></a>fpos:: operator streamoff

Přetypování objektu typu `fpos` na objekt typu `streamoff`

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený členský objekt posunu a všechny další posuny uložené jako součást `fpos_t` členského objektu.

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

## <a name="seekpos"></a>fpos:: seekpos

Tato metoda se používá interně pouze C++ pomocí standardní knihovny. Nevolejte tuto metodu z vašeho kódu.

```cpp
fpos_t seekpos() const;
```

## <a name="state"></a>fpos:: State

Nastaví nebo vrátí stav převodu.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parametry

*_State*\
Nový stav konverze.

### <a name="return-value"></a>Návratová hodnota

Stav konverze.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí hodnotu uloženou v `St` objektu member. Druhá členská funkce ukládá *_State* do `St` objektu member.

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

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
