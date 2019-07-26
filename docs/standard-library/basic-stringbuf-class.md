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
ms.openlocfilehash: 0445c2f8868fc9f2863ad4a2a12cc00261546c75
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447848"
---
# <a name="basicstringbuf-class"></a>basic_stringbuf – třída

Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu `Elem`, jejichž vlastnosti znaků jsou určeny třídou `Tr`, na a z sekvence prvků uložených v objektu Array.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Vyhrazen*\
Třída alokátoru

*Elem*\
Typ základního prvku řetězce.

*Recenzent*\
Vlastnosti znaků specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Objekt je přidělen, rozšířen a uvolněn podle potřeby pro přizpůsobení změn v sekvenci.

Objekt třídy basic_stringbuf `Elem`< `ios_base::` [](../standard-library/ios-base-class.md#openmode) `stringbuf` , `Tr`> ukládá kopii argumentu openMode z jeho konstruktoru jako režim jeho režimu: `Alloc`

- Pokud `mode & ios_base::in` je hodnota nenulová, je vstupní vyrovnávací paměť přístupná. Další informace naleznete v tématu [Třída basic_streambuf](../standard-library/basic-streambuf-class.md).

- Pokud `mode & ios_base::out` je hodnota nenulová, je k dispozici výstupní vyrovnávací paměť.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Vytvoří objekt typu `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymum pro *přidělení*parametru šablony.|
|[char_type](#char_type)|Přidruží název typu k parametru šablony *elem* .|
|[int_type](#int_type)|Nastaví tento typ v `basic_filebuf`rámci rozsahu, který odpovídá typu stejného názvu v oboru *TR* .|
|[off_type](#off_type)|Nastaví tento typ v `basic_filebuf`rámci rozsahu, který odpovídá typu stejného názvu v oboru *TR* .|
|[pos_type](#pos_type)|Nastaví tento typ v `basic_filebuf`rámci rozsahu, který odpovídá typu stejného názvu v oboru *TR* .|
|[traits_type](#traits_type)|Přidruží název typu k parametru šablony *TR* .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[overflow](#overflow)|Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce se pokusí vrátit prvek do vstupní vyrovnávací paměti a pak nastaví aktuální prvek (ukazuje na další ukazatel).|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.|
|[str](#str)|Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.|
|swap||
|[podtečení](#underflow)|Chráněná virtuální členská funkce pro extrakci aktuálního prvku ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<sstream >

**Obor názvů:** std

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

Typ je synonymum pro *přidělení*parametru šablony.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>basic_stringbuf::basic_stringbuf

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
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*str*\
Objekt typu [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Poznámky

První konstruktor ukládá ukazatel s hodnotou null ve všech ukazatelích řídících vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Další informace naleznete v části poznámky [třídy basic_streambuf](../standard-library/basic-streambuf-class.md). Také ukládá *_Mode* jako režim stringbuf –. Další informace naleznete v části poznámky [třídy basic_stringbuf](../standard-library/basic-stringbuf-class.md).

Druhý konstruktor přiděluje kopii sekvence řízenou *str*objektu řetězce. Pokud `_Mode & ios_base::in` je hodnota nenulová, nastaví vstupní vyrovnávací paměť tak, aby začala číst na začátku sekvence. Pokud `_Mode & ios_base::out` je hodnota nenulová, nastaví výstupní vyrovnávací paměť tak, aby začala psát na začátku sekvence. Také ukládá *_Mode* jako režim stringbuf –. Další informace naleznete v části poznámky [třídy basic_stringbuf](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>  basic_stringbuf::char_type

Přidruží název typu k parametru šablony *elem* .

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

Nastaví tento typ v rámci oboru basic_filebuf's jako ekvivalent typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

Nastaví tento typ v rámci oboru basic_filebuf's jako ekvivalent typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>basic_stringbuf:: přetečení

Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který má být vložen do vyrovnávací paměti `traits_type::eof`, nebo.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`se. V opačném případě vrátí **traits_type::** [Not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *meta*).

### <a name="remarks"></a>Poznámky

Pokud[](../standard-library/char-traits-struct.md#eof)[](../standard-library/char-traits-struct.md#to_char_type) *\_*   *\_se meta* nerovná jako **traits_type::** EOF, chráněná virtuální členská funkce se pokusí vložit element traits_type:: to_char_type (meta) do výstupní vyrovnávací paměť. To lze provést různými způsoby:

- Pokud je k dispozici pozice pro zápis, může prvek Uložit do pozice pro zápis a zvýšit další ukazatel pro výstupní vyrovnávací paměť.

- Dá se k dispozici pozice pro zápis přidělením nového nebo dalšího úložiště pro výstupní vyrovnávací paměť. Rozšiřování výstupní vyrovnávací paměti tímto způsobem také rozšiřuje jakoukoli přidruženou vstupní vyrovnávací paměť.

## <a name="pbackfail"></a>basic_stringbuf::p neúspěšného selhání

Chráněná virtuální členská funkce se pokusí vrátit prvek do vstupní vyrovnávací paměti a poté jej nastavit na aktuální prvek (ukazuje na další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který má být vložen do vyrovnávací paměti `traits_type::eof`, nebo.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`se. V opačném případě vrátí **traits_type::** [Not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *meta*).

### <a name="remarks"></a>Poznámky

Pokud se *_Meta* porovná s **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), je element, který se má vrátit zpátky, efektivně ten, který už je v proudu před aktuálním prvkem. V opačném případě je tento prvek nahrazen **Byte** = **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *meta*). Funkce může vložit element zpět různými způsoby:

- Je-li k dispozici putback pozice a element, který je uložen, porovnává hodnotu Byte, může snížit další ukazatel pro vstupní vyrovnávací paměť.

- Pokud je k dispozici putback pozice a pokud režim stringbuf – umožňuje změnit sekvenci ( **mode & ios_base:: out** je nenulový), může uložit bajt do putback pozice a snížit další ukazatel pro vstupní vyrovnávací paměť.

## <a name="pos_type"></a>  basic_stringbuf::pos_type

Nastaví tento typ v rámci oboru basic_filebuf's jako ekvivalent typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozice pro hledání vzhledem k *_Way*. Další informace najdete v tématu [basic_stringbuf:: off_type](#off_type).

*_Way*\
Výchozí bod pro operace posunu. Možné hodnoty naleznete v tématu [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) .

*_Mode*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis. Další informace najdete v tématu [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo neplatnou pozici streamu.

### <a name="remarks"></a>Poznámky

V případě objektu třídy `basic_stringbuf<Elem, Tr, Alloc>`je umístění datového proudu tvořeno čistě posunem datového proudu. Nula odsazení určuje první prvek řízené sekvence.

Nová pozice je určena následujícím způsobem:

- Pokud `_Way` je == Novápozice začátek datového proudu a *_Off.* `ios_base::beg`

- Pokud `_Way` je == Novápozice aktuální pozice datového proudu a _Off.  `ios_base::cur`

- Pokud `_Way` je == Novápozice koncem datového proudu plus *_Off.* `ios_base::end`

Pokud `_Mode & ios_base::in` je hodnota nenulová, funkce změní další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud `_Mode & ios_base::out` je hodnota nenulová, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. Aby byl datový proud ovlivněn, musí existovat jeho vyrovnávací paměť. Aby operace umístění byla úspěšná, výsledná pozice v datovém proudu musí spadat do kontrolované sekvence. Pokud funkce ovlivňuje umístění datových proudů,  musí být `ios_base::beg` _Way nebo `ios_base::end` a oba proudy umístěny na stejném elementu. V opačném případě (nebo pokud není ovlivněná žádná poloha), operace umístění selže.

Pokud se funkce při změně buď nebo obou pozic streamu zdaří, vrátí výslednou pozici streamu. V opačném případě selže a vrátí neplatnou pozici streamu.

## <a name="seekpos"></a>  basic_stringbuf::seekpos

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice pro hledání.

*_Mode*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud se funkce při změně buď nebo obou pozic streamu zdaří, vrátí výslednou pozici streamu. V opačném případě selže a vrátí neplatnou pozici streamu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte `pos_type(off_type(-1))`návratovou hodnotu hodnotou.

### <a name="remarks"></a>Poznámky

Pro objekt třídy basic_stringbuf < **elem**, **TR**, `Alloc`> je umístění datového proudu čistě tvořeno posunem datového proudu. Nula odsazení určuje první prvek řízené sekvence. Nová pozice je určena v rámci _ *SP*.

Pokud **režim & ios_base:: in** je nenulová, funkce změní další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud **režim & ios_base:: out** je nenulová, funkce změní další pozici pro zápis do výstupní vyrovnávací paměti. Aby byl datový proud ovlivněn, musí existovat jeho vyrovnávací paměť. Aby operace umístění byla úspěšná, výsledná pozice v datovém proudu musí spadat do kontrolované sekvence. V opačném případě (nebo pokud není ovlivněná žádná poloha), operace umístění selže.

## <a name="str"></a>  basic_stringbuf::str

Nastaví nebo získá text v bufferu řetězce beze změny pozice zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md) \< **elem**, **TR**, ID přidělení **>,** jehož řízená sekvence je kopií sekvence řízené  **\*tímto**nastavením.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí objekt třídy basic_string < **elem**, **TR**, `Alloc`>, jehož řízená sekvence je kopií sekvence řízené  **\*tímto**rozhraním. Zkopírovaná sekvence závisí na uloženém režimu stringbuf –:

- Pokud **režim & ios_base:: out** je nenulová a výstupní vyrovnávací paměť existuje, sekvence je celá výstupní vyrovnávací paměť ( [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) elementy začínající `pbase`na).

- **Režim if & ios_base:: in** je nenulový a vstupní vyrovnávací paměť existuje, sekvence je celá vstupní vyrovnávací paměť ( [egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) elementy začínající `eback`na).

- V opačném případě je zkopírovaná sekvence prázdná.

Druhá členská funkce zruší přidělení jakékoli sekvence  **\*, která je**aktuálně kontrolována. Pak přidělí kopii sekvence řízené *_Newstr*. **Režim If & ios_base:: in** je nenulový, nastaví vstupní vyrovnávací paměť tak, aby se spouštěla na začátku sekvence. Pokud **režim & ios_base:: out** je nenulová, nastaví výstupní vyrovnávací paměť tak, aby začala psát na začátku sekvence.

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

## <a name="traits_type"></a>  basic_stringbuf::traits_type

Přidruží název typu k parametru šablony *TR* .

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *TR*.

## <a name="underflow"></a>basic_stringbuf:: subflow

Chráněná virtuální funkce pro extrakci aktuálního prvku ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof). V opačném případě vrátí aktuální prvek ve vstupním datovém proudu, který je převeden.

### <a name="remarks"></a>Poznámky

`byte` Chráněná virtuální členská funkce se pokusí extrahovat aktuální prvek ze vstupní vyrovnávací paměti, pokračovat v aktuálním umístění datového proudu a vrátit prvek jako **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **Byte**). Můžete to udělat jedním z těchto způsobů: Pokud je k dispozici pozice pro čtení, `byte` převezme se jako element uložený na pozici pro čtení a přesune další ukazatel pro vstupní vyrovnávací paměť.

## <a name="swap"></a>basic_streambuf:: swap

Zamění obsah této vyrovnávací paměti řetězce s jinou vyrovnávací pamětí řetězce.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*jiná*\
Basic_stringbuf, jehož obsah se bude v tomto basic_stringbuf zaměnit.

### <a name="remarks"></a>Poznámky

## <a name="op_eq"></a>basic_stringbuf:: operator =

Přiřadí obsah basic_stringbuf na pravé straně operátoru k basic_stringbuf na levé straně.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*jiná*\
Basic_stringbuf, jehož obsah, včetně vlastností národního prostředí, se přiřadí k stringbuf – na levé straně operátoru.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
