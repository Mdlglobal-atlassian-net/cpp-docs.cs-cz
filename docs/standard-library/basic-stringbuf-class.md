---
title: basic_stringbuf – třída
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
ms.openlocfilehash: 578d0e31e08f3e077a908c4344f77da5495df40d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364878"
---
# <a name="basic_stringbuf-class"></a>basic_stringbuf – třída

Popisuje vyrovnávací paměť datového proudu, která `Elem`řídí přenos prvků typu , `Tr`jejichž znakové znaky jsou určeny třídou , do a z posloupnosti prvků uložených v objektu pole.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Tr*\
Znakové znaky specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Objekt je přidělen, rozšířen a uvolněn podle potřeby přizpůsobit změny v pořadí.

Objekt třídy basic_stringbuf `Elem` `Tr`< `Alloc` ,> ukládá `ios_base::`kopii argumentu [openmode](../standard-library/ios-base-class.md#openmode) z jeho konstruktoru jako `stringbuf` **režimu režimu**:

- Pokud `mode & ios_base::in` je nenulová, vstupní vyrovnávací paměť je přístupná. Další informace naleznete [v tématu basic_streambuf Class](../standard-library/basic-streambuf-class.md).

- Pokud `mode & ios_base::out` je nenulová, výstupní vyrovnávací paměť je přístupná.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Vytvoří objekt typu `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymem pro parametr šablony *Alloc*.|
|[char_type](#char_type)|Přidruží název typu k parametru šablony *Elem.*|
|[int_type](#int_type)|Tento typ `basic_filebuf`v rámci oboru je ekvivalentní typu stejného názvu v oboru *Tr.*|
|[off_type](#off_type)|Tento typ `basic_filebuf`v rámci oboru je ekvivalentní typu stejného názvu v oboru *Tr.*|
|[pos_type](#pos_type)|Tento typ `basic_filebuf`v rámci oboru je ekvivalentní typu stejného názvu v oboru *Tr.*|
|[traits_type](#traits_type)|Přidruží název typu k parametru šablony *Tr.*|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Přetečení](#overflow)|Chráněná virtuální funkce, kterou lze volat při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce se pokusí vrátit prvek zpět do vstupní vyrovnávací paměti a pak z něj udělá aktuální prvek (na který odkazuje další ukazatel).|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[Str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce bez změny polohy zápisu.|
|swap||
|[Podtečení](#underflow)|Chráněná virtuální členská funkce extrahovat aktuální prvek ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream>

**Obor názvů:** std

## <a name="basic_stringbufallocator_type"></a><a name="allocator_type"></a>basic_stringbuf::allocator_type

Typ je synonymem pro parametr šablony *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbufbasic_stringbuf"></a><a name="basic_stringbuf"></a>basic_stringbuf::basic_stringbuf

Vytvoří objekt typu `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jeden z výčtů v [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Objekt typu [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Poznámky

První konstruktor ukládá ukazatel null ve všech ukazatelích ovládajících vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Další informace naleznete v části Poznámky [třídy basic_streambuf .](../standard-library/basic-streambuf-class.md) Ukládá také *_Mode* jako režim stringbuf. Další informace naleznete v části Poznámky [třídy basic_stringbuf .](../standard-library/basic-stringbuf-class.md)

Druhý konstruktor přiděluje kopii sekvence řízené objektu řetězce *str*. Pokud `_Mode & ios_base::in` je nenulová, nastaví vstupní vyrovnávací paměť pro spuštění čtení na začátku sekvence. Pokud `_Mode & ios_base::out` je nenulová, nastaví výstupní vyrovnávací paměť začít psát na začátku sekvence. Ukládá také *_Mode* jako režim stringbuf. Další informace naleznete v části Poznámky [třídy basic_stringbuf .](../standard-library/basic-stringbuf-class.md)

## <a name="basic_stringbufchar_type"></a><a name="char_type"></a>basic_stringbuf::char_type

Přidruží název typu k parametru šablony *Elem.*

```cpp
typedef Elem char_type;
```

## <a name="basic_stringbufint_type"></a><a name="int_type"></a>basic_stringbuf::int_type

Tento typ v rámci oboru basic_filebuf odpovídá typu stejného `Tr` názvu v oboru.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_stringbufoff_type"></a><a name="off_type"></a>basic_stringbuf::off_type

Tento typ v rámci oboru basic_filebuf odpovídá typu stejného `Tr` názvu v oboru.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_stringbufoverflow"></a><a name="overflow"></a>basic_stringbuf:přetečení

Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak vložit do vyrovnávací paměti `traits_type::eof`nebo .

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být `traits_type::eof`úspěšná, vrátí . V opačném případě vrátí **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Poznámky

Pokud * \_Meta* neporovnává rovno **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), chráněná virtuální členská funkce se pokusí vložit prvek **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) do výstupní vyrovnávací paměti. Může tak učinit různými způsoby:

- Pokud je k dispozici pozice zápisu, může uložit prvek do pozice zápisu a zvýšit další ukazatel pro výstupní vyrovnávací paměti.

- Může zpřístupnit pozici zápisu přidělením nového nebo dalšího úložiště pro výstupní vyrovnávací paměť. Rozšíření výstupní vyrovnávací paměti tímto způsobem také rozšiřuje všechny přidružené vstupní vyrovnávací paměti.

## <a name="basic_stringbufpbackfail"></a><a name="pbackfail"></a>basic_stringbuf::pbackfail

Chráněná virtuální členská funkce se pokusí vrátit prvek zpět do vstupní vyrovnávací paměti a potom jej učinit aktuálním prvkem (na který odkazuje další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak vložit do vyrovnávací paměti `traits_type::eof`nebo .

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být `traits_type::eof`úspěšná, vrátí . V opačném případě vrátí **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Poznámky

Pokud *_Meta* porovná rovná **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), prvek push back je účinně jeden již v datovém proudu před aktuální prvek. V opačném případě se tento prvek nahradí **bajtem** = **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Funkce může vrátit prvek různými způsoby:

- Pokud putback pozice je k dispozici a prvek uložený tam porovnává rovná bajt, může zmenšit další ukazatel pro vstupní vyrovnávací paměti.

- Pokud putback pozice je k dispozici a pokud stringbuf režim umožňuje pořadí změnit **(režim & ios_base::out** je nenulová), může uložit bajt do putback pozice a snížení další ukazatel pro vstupní vyrovnávací paměti.

## <a name="basic_stringbufpos_type"></a><a name="pos_type"></a>basic_stringbuf::pos_type

Tento typ v rámci oboru basic_filebuf odpovídá typu stejného `Tr` názvu v oboru.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_stringbufseekoff"></a><a name="seekoff"></a>basic_stringbuf::seekoff

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozice hledat vzhledem k *_Way*. Další informace naleznete [v tématu basic_stringbuf::off_type](#off_type).

*_Way*\
Počáteční bod pro operace odsazení. Viz [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) pro možné hodnoty.

*_Mode*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis. Další informace naleznete [v tématu ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo neplatnou pozici datového proudu.

### <a name="remarks"></a>Poznámky

Pro objekt třídy `basic_stringbuf<Elem, Tr, Alloc>`, pozice datového proudu se skládá čistě z posunu datového proudu. Posun nula označuje první prvek řízené sekvence.

Nová pozice je určena takto:

- `_Way`  == Pokud `ios_base::beg`je nová pozice začátkem datového proudu plus *_Off*.

- `_Way`  == Pokud `ios_base::cur`je nová pozice aktuální polohou datového proudu plus *_Off*.

- `_Way`  == Pokud `ios_base::end`je nová pozice koncem datového proudu plus *_Off*.

Pokud `_Mode & ios_base::in` je nenulová, funkce změní další pozici číst ve vstupní vyrovnávací paměti. Pokud `_Mode & ios_base::out` je nenulová, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. Chcete-li ovlivnit datový proud, musí existovat jeho vyrovnávací paměť. Aby byla operace umístění úspěšná, musí být výsledná pozice datového proudu v řízené posloupnosti. Pokud funkce ovlivňuje obě pozice datového `ios_base::end` proudu, _Way *musí* být `ios_base::beg` nebo a oba datové proudy jsou umístěny na stejném prvku. V opačném případě (nebo pokud není ovlivněna ani jedna pozice), operace umístění se nezdaří.

Pokud funkce uspěje při změně jedné nebo obou pozic datového proudu, vrátí výslednou pozici datového proudu. V opačném případě selže a vrátí pozici neplatného datového proudu.

## <a name="basic_stringbufseekpos"></a><a name="seekpos"></a>basic_stringbuf::seekpos

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice, o kterou se můžete snažit.

*_Mode*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje při změně jedné nebo obou pozic datového proudu, vrátí výslednou pozici datového proudu. V opačném případě selže a vrátí pozici neplatného datového proudu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Pro objekt třídy basic_stringbuf< **Elem**, **Tr**, `Alloc`>, pozice datového proudu se skládá čistě z posunu datového proudu. Posun nula označuje první prvek řízené sekvence. Nová pozice je určena _ *Sp*.

Pokud **režim & ios_base::in** je nenulová, funkce změní další pozici ke čtení ve vstupní vyrovnávací paměti. Pokud **režim & ios_base::out** je nenulová, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. Chcete-li ovlivnit datový proud, musí existovat jeho vyrovnávací paměť. Aby byla operace umístění úspěšná, musí být výsledná pozice datového proudu v řízené posloupnosti. V opačném případě (nebo pokud není ovlivněna ani jedna pozice), operace umístění se nezdaří.

## <a name="basic_stringbufstr"></a><a name="str"></a>basic_stringbuf::str

Nastaví nebo získá text ve vyrovnávací paměti řetězce bez změny polohy zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md) \< **Elem**, **Tr**, Alloc **>,** jehož řízená sekvence je kopií sekvence řízené ** \*touto**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí objekt třídy **Tr**basic_string `Alloc`< **Elem**, Tr ,>, jehož řízená sekvence je kopií sekvence řízené ** \*tímto**. Zkopírovaná sekvence závisí na uloženém režimu stringbuf:

- Pokud **je režim & ios_base::out** nenulová a výstupní vyrovnávací paměť existuje, sekvenci je celá výstupní vyrovnávací paměť ( prvky [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) začínající ). `pbase`

- Pokud **režim & ios_base::in** je nenulová a vstupní vyrovnávací paměť existuje, sekvence je celá `eback`vstupní vyrovnávací paměť ( [egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) prvky začínající ).

- V opačném případě je zkopírovaná sekvence prázdná.

Druhá členská funkce zruší přidělení libovolné sekvence, která je aktuálně řízena ** \*tímto**. Potom přidělí kopii sekvence řízené *_Newstr*. Pokud **režim & ios_base::in** je nenulová, nastaví vstupní vyrovnávací paměť tak, aby začala číst na začátku sekvence. Pokud **režim & ios_base::out** je nenulová, nastaví výstupní vyrovnávací paměť začít psát na začátku sekvence.

### <a name="example"></a>Příklad

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="basic_stringbuftraits_type"></a><a name="traits_type"></a>basic_stringbuf::traits_type

Přidruží název typu k parametru šablony *Tr.*

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *Tr*.

## <a name="basic_stringbufunderflow"></a><a name="underflow"></a>basic_stringbuf::podtočení

Chráněné, virtuální funkce extrahovat aktuální prvek ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). V opačném případě vrátí aktuální prvek ve vstupním datovém proudu, které jsou převedeny.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se `byte` pokusí extrahovat aktuální prvek ze vstupní vyrovnávací paměti, posunout aktuální pozici datového proudu a vrátit prvek jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **bajt**). Může tak učinit jedním způsobem: Pokud je k `byte` dispozici pozice pro čtení, trvá jako prvek uložený v pozici pro čtení a posune další ukazatel pro vstupní vyrovnávací paměti.

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::swap

Zamění obsah této vyrovnávací paměti řetězce s jinou vyrovnávací pamětí řetězce.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*Další*\
basic_stringbuf jejichž obsah bude vyměněn s tímto basic_stringbuf.

### <a name="remarks"></a>Poznámky

## <a name="basic_stringbufoperator"></a><a name="op_eq"></a>basic_stringbuf::operátor=

Přiřadí obsah basic_stringbuf na pravé straně operátoru basic_stringbuf na levé straně.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*Další*\
A basic_stringbuf jehož obsah, včetně vlastností národního prostředí, bude přiřazen stringbuf na levé straně operátoru.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
