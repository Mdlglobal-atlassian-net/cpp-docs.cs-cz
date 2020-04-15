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
ms.openlocfilehash: 7d60a31e69e8a1ad82086f715cac6dde064d1fac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359206"
---
# <a name="fpos-class"></a>fpos – třída

Šablona třídy popisuje objekt, který může ukládat všechny informace potřebné k obnovení libovolného indikátoru pozice souboru v libovolném datovém proudu. Objekt třídy fpos\< **St**> efektivně ukládá alespoň dva členské objekty:

- Posun bajtů typu [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Stav převodu pro použití objektem třídy `St`basic_filebuf typu `mbstate_t`, obvykle .

Může také uložit libovolnou pozici souboru pro použití [basic_filebuf](../standard-library/basic-filebuf-class.md)objektem `fpos_t`třídy basic_filebuf typu . Pro prostředí s omezenou velikostí `streamoff` `fpos_t` souboru, však a může být někdy použit zaměnitelně. Pro prostředí bez datových proudů, které mají `mbstate_t` kódování závislé na stavu, může být ve skutečnosti nepoužívané. Proto počet uložených členů objekty se mohou lišit.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parametry

*Typ stavu*\
Informace o stavu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[fpos](#fpos)|Vytvořte objekt, který obsahuje informace o pozici (posun) v datovém proudu.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[seekpos](#seekpos)|Používá se interně pouze standardní knihovnou jazyka C++. Nevolat tuto metodu z kódu.|
|[Státu](#state)|Nastaví nebo vrátí stav převodu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor!=](#op_neq)|Testuje ukazatele pozice souboru pro nerovnost.|
|[operátor+](#op_add)|Nastaví indikátor polohy souboru.|
|[operátor+=](#op_add_eq)|Nastaví indikátor polohy souboru.|
|[operátor-](#operator-)|Sníží indikátor polohy souboru.|
|[operátor-=](#operator-_eq)|Sníží indikátor polohy souboru.|
|[operátor==](#op_eq_eq)|Testuje ukazatele pozice souboru pro rovnost.|
|[streamoff operátora](#op_streamoff)|Přetypována `fpos` objekt typu `streamoff`na objekt typu .|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ios>

**Obor názvů:** std

## <a name="fposfpos"></a><a name="fpos"></a>fpos::fpos

Vytvořte objekt, který obsahuje informace o pozici (posun) v datovém proudu.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun do datového proudu.

*_State*\
Počáteční stav objektu. `fpos`

*_Filepos*\
Posun do datového proudu.

### <a name="remarks"></a>Poznámky

První konstruktor ukládá odsazení *_Off*vzhledem k začátku souboru a ve stavu počáteční převod (pokud na tom záleží). Pokud *_Off* je -1, výsledný objekt představuje neplatnou pozici datového proudu.

Druhý konstruktor ukládá nulový posun a objekt *_State*.

## <a name="fposoperator"></a><a name="op_neq"></a>fpos::operátor!=

Testuje ukazatele pozice souboru pro nerovnost.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Indikátor pozice souboru, proti kterému chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud indikátory polohy souboru nejsou stejné, jinak **false**.

### <a name="remarks"></a>Poznámky

Členská funkce `!(*this == right)`vrátí .

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

## <a name="fposoperator"></a><a name="op_add"></a>fpos::operátor+

Nastaví indikátor polohy souboru.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, o který chcete inkresovat indikátor pozice souboru.

### <a name="return-value"></a>Návratová hodnota

Pozice v souboru.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `_Off` **fpos(\*this) +=** .

### <a name="example"></a>Příklad

Viz [operátor!=](#op_neq) pro vzorek `operator+`použití .

## <a name="fposoperator"></a><a name="op_add_eq"></a>fpos::operátor+=

Nastaví indikátor polohy souboru.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun, o který chcete inkresovat indikátor pozice souboru.

### <a name="return-value"></a>Návratová hodnota

Pozice v souboru.

### <a name="remarks"></a>Poznámky

Členská funkce přidá *_Off* uloženému objektu člena ofsaka a vrátí ** \*tuto**funkci . Pro umístění v rámci souboru je výsledek obecně platný pouze pro binární datové proudy, které nemají kódování závislé na stavu.

### <a name="example"></a>Příklad

Viz [operátor!=](#op_neq) pro vzorek `operator+=`použití .

## <a name="fposoperator-"></a><a name="operator-"></a>fpos::operátor-

Sníží indikátor polohy souboru.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Pozice souboru.

*_Off*\
Posun datového proudu.

### <a name="return-value"></a>Návratová hodnota

První členská `(streamoff)*this - (streamoff) right`funkce vrátí . Druhá členská `fpos(*this) -= _Off`funkce vrátí .

### <a name="example"></a>Příklad

Viz [operátor!=](#op_neq) pro vzorek `operator-`použití .

## <a name="fposoperator-"></a><a name="operator-_eq"></a>fpos::operátor-=

Sníží indikátor polohy souboru.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Posun datového proudu.

### <a name="return-value"></a>Návratová hodnota

Členská funkce `fpos(*this) -= _Off`vrátí .

### <a name="remarks"></a>Poznámky

Pro umístění v rámci souboru je výsledek obecně platný pouze pro binární datové proudy, které nemají kódování závislé na stavu.

### <a name="example"></a>Příklad

Viz [operátor!=](#op_neq) pro vzorek `operator-=`použití .

## <a name="fposoperator"></a><a name="op_eq_eq"></a>fpos::operátor==

Testuje ukazatele pozice souboru pro rovnost.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Právo*\
Indikátor pozice souboru, proti kterému chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou ukazatele polohy souboru stejné; jinak **false**.

### <a name="remarks"></a>Poznámky

Členská funkce `(streamoff)*this == (streamoff)right`vrátí .

### <a name="example"></a>Příklad

Viz [operátor!=](#op_neq) pro vzorek `operator+=`použití .

## <a name="fposoperator-streamoff"></a><a name="op_streamoff"></a>fpos::operátor streamoff

Přetypový `fpos` objekt typu `streamoff`na objekt typu .

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Poznámky

Členská funkce vrátí uložený objekt člena odsazení a další posun uložený jako součást členského objektu. `fpos_t`

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

## <a name="fposseekpos"></a><a name="seekpos"></a>fpos::seekpos

Tato metoda se používá interně pouze standardní knihovnou jazyka C++. Nevolat tuto metodu z kódu.

```cpp
fpos_t seekpos() const;
```

## <a name="fposstate"></a><a name="state"></a>fpos::stav

Nastaví nebo vrátí stav převodu.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parametry

*_State*\
Nový stav převodu.

### <a name="return-value"></a>Návratová hodnota

Stav převodu.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí hodnotu uloženou v členském objektu. `St` Druhá členská *_State* funkce ukládá `St` _State v členském objektu.

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

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
