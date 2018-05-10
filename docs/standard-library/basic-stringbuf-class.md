---
title: basic_stringbuf – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7ec812ffeb50e83d59df764224ed9dcdaf07d8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="basicstringbuf-class"></a>basic_stringbuf – třída

Popisuje datový proud vyrovnávací paměť, která řídí přenos elementy typu `Elem`, jehož vlastnosti znak určuje třídu `Tr`, do a z pořadí prvků, které jsou uložené v objektu array.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Alloc` Allocator – třída.

`Elem` Typ elementu základní řetězce.

`Tr` Vlastnosti znak specializované na základní prvek řetězce.

## <a name="remarks"></a>Poznámky

Objekt je přidělené, Rozšířená a vydání podle potřeby pro přizpůsobení změny v pořadí.

Objekt basic_stringbuf – třída < `Elem`, `Tr`, `Alloc`> ukládá kopie `ios_base::` [openmode –](../standard-library/ios-base-class.md#openmode) argument ze svého konstruktoru jako jeho `stringbuf` režimu **režimu** :

- Pokud `mode & ios_base::in` je nenulové hodnoty, vstupní vyrovnávací paměť je přístupný. Další informace najdete v tématu [basic_streambuf – třída](../standard-library/basic-streambuf-class.md).

- Pokud `mode & ios_base::out` je nenulové hodnoty, výstupní vyrovnávací paměť je přístupný.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Vytvoří objekt typu `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type –](#allocator_type)|Typ je synonymum pro parametr šablony `Alloc`.|
|[char_type](#char_type)|Přidruží název typu s `Elem` parametr šablony.|
|[int_type](#int_type)|Umožňuje v rámci tohoto typu `basic_filebuf`je ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|
|[off_type –](#off_type)|Umožňuje v rámci tohoto typu `basic_filebuf`je ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|
|[pos_type](#pos_type)|Umožňuje v rámci tohoto typu `basic_filebuf`je ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|
|[traits_type](#traits_type)|Přidruží název typu s `Tr` parametr šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Přetečení](#overflow)|Chráněné, virtuální funkce, která lze volat, když nové znak je vložen do plné vyrovnávací paměti.|
|[pbackfail –](#pbackfail)|Funkce chráněného člena virtuální se pokusí vrátit zpět element do vstupní vyrovnávací paměť, pak umožňuje aktuálního elementu (ukazuje další ukazatel).|
|[seekoff –](#seekoff)|Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[seekpos –](#seekpos)|Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[str –](#str)|Nastaví nebo získá beze změny na pozici zápis textu do vyrovnávací paměti řetězců.|
|swap||
|[podtečení](#underflow)|Chráněný člen virtuální funkce k extrakci aktuálního elementu ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream – >

**Namespace:** – std

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

Typ je synonymum pro parametr šablony `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>  basic_stringbuf::basic_stringbuf

Vytvoří objekt typu `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Mode` Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`str` Objekt typu [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Poznámky

První konstruktor ukládá ukazatele null v následující ukazatele řízení vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Další informace najdete v části poznámky [basic_streambuf – třída](../standard-library/basic-streambuf-class.md). Ukládá také `_Mode` stringbuf – režim. Další informace najdete v části poznámky [basic_stringbuf – třída](../standard-library/basic-stringbuf-class.md).

Druhý konstruktor přiděluje kopii pořadí řízené objekt řetězce `str`. Pokud `_Mode & ios_base::in` je nenulové hodnoty, nastaví vstupní vyrovnávací paměť zahájíte čtení při spuštění pořadí. Pokud `_Mode & ios_base::out` je nenulové hodnoty, nastaví výstupní vyrovnávací paměť má začít zapisovat na začátku pořadí. Ukládá také `_Mode` stringbuf – režim. Další informace najdete v části poznámky [basic_stringbuf – třída](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>  basic_stringbuf::char_type

Přidruží název typu s **Elem** parametr šablony.

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

Umožňuje tento typ v rámci oboru basic_filebuf je ekvivalentem typu se stejným názvem v **Tr** oboru.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

Umožňuje tento typ v rámci oboru basic_filebuf je ekvivalentem typu se stejným názvem v **Tr** oboru.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::Overflow

Chráněné virtuální funkce, která lze volat, když nové znak je vložen do plné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

`_Meta` Znak, který má vložit do vyrovnávací paměti, nebo **traits_type::eof**.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof**. Funkce **traits_type –::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Poznámky

Pokud _ *Meta* porovnat není rovno **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof), chráněného člena virtuální funkce pokusí vložit element **traits_type –::** [ to_char_type –](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) do výstupní vyrovnávací paměť. Můžete tak učinit různými způsoby:

- Pokud pozice zápisu je k dispozici, může uložit prvek na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.

- K dispozici na pozici zápisu mohl zajistit přidělí nové nebo další úložiště pro výstupní vyrovnávací paměť. Rozšíření výstupní vyrovnávací paměť tímto způsobem taky ji rozšiřuje na všechny přidružené vstupní vyrovnávací paměť.

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

Chráněný člen virtuální funkce se pokusí vrátit zpět element do vstupní vyrovnávací paměť a proveďte aktuálního elementu (ukazuje další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

`_Meta` Znak, který má vložit do vyrovnávací paměti, nebo **traits_type::eof**.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof**. Funkce **traits_type –::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Poznámky

Pokud `_Meta` porovná rovno **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof), element tak, aby nabízel zpět je efektivně už v datovém proudu před aktuálního elementu. Jinak je nahrazena daný element **bajtů** = **traits_type –::**[to_char_type –](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Funkce může vrátit zpět element různými způsoby:

- Pokud je k dispozici na pozici putback – a element v ní uloženy porovná rovna bajtů, je snížení další ukazatele pro vstupní vyrovnávací paměť.

- Pokud pozice putback – je k dispozici, a pokud stringbuf – režim umožňuje pořadí upravit ( **režimu & ios_base::out** nenulový), můžete ukládat bajtů do pozice putback – a snížení další ukazatele pro vstupní vyrovnávací paměť.

## <a name="pos_type"></a>  basic_stringbuf::pos_type

Umožňuje tento typ v rámci oboru basic_filebuf je ekvivalentem typu se stejným názvem v **Tr** oboru.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Off` Pozice k vyhledání pro vzhledem k `_Way`. Další informace najdete v tématu [basic_stringbuf::off_type](#off_type).

`_Way` Výchozí bod pro posunutí operace. V tématu [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) pro možné hodnoty.

`_Mode` Určuje režim pro umístění ukazatele. Ve výchozím nastavení se vám umožní změnit čtení a zápis pozic. Další informace najdete v tématu [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Návratová hodnota

Vrátí nový pozici nebo pozice neplatný datový proud.

### <a name="remarks"></a>Poznámky

Pro objekt třídy `basic_stringbuf<Elem, Tr, Alloc>`, pozice datového proudu se skládá výhradně z posun datového proudu. Posunutí nula označí první prvek řízené sekvenci.

Nové místo je stanoven následujícím způsobem:

- Pokud `_Way`  ==  `ios_base::beg`, začátku plus datového proudu se nové pozice `_Off`.

- Pokud `_Way`  ==  `ios_base::cur`, aktuální pozici datového proudu se nové pozice plus `_Off`.

- Pokud `_Way`  ==  `ios_base::end`, nové pozice se konec datového proudu plus `_Off`.

Pokud `_Mode & ios_base::in` je nenulové hodnoty, funkce mění další pozice číst vstupní vyrovnávací paměti. Pokud `_Mode & ios_base::out` je nenulové hodnoty, funkce mění další pozice se zapisovat do výstupní vyrovnávací paměť. Pro datový proud má pravděpodobně musí existovat jeho vyrovnávací paměti. Umísťovací operace úspěšná výsledný datový proud pozice musí ležet v řízené sekvenci. Pokud funkce ovlivní obě pozice datového proudu `_Way` musí být `ios_base::beg` nebo `ios_base::end` a oba datové proudy, které jsou umístěny v stejného elementu. V opačném případě (nebo pokud je ovlivněno ani pozice), umísťovací operace selže.

Pokud funkci podaří změna jedné nebo obou pozic datového proudu, vrátí pozici výsledné datového proudu. Jinak selže a vrátí pozici neplatný datový proud.

## <a name="seekpos"></a>  basic_stringbuf::seekpos

Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Sp` Pozice k vyhledání pro.

`_Mode` Určuje režim pro umístění ukazatele. Ve výchozím nastavení se vám umožní změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Pokud funkci podaří změna jedné nebo obou pozic datového proudu, vrátí pozici výsledné datového proudu. Jinak selže a vrátí pozici neplatný datový proud. Pokud chcete zjistit, pokud pozice datový proud je neplatný, porovnat návratovou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Pro objekt basic_stringbuf – třída < **Elem**, **Tr**, `Alloc`>, pozice datového proudu se skládá výhradně z posun datového proudu. Posunutí nula označí první prvek řízené sekvenci. Nové místo je dáno _ *Sp*.

Pokud **režimu & ios_base::in** je nenulové hodnoty, funkce mění další pozice číst vstupní vyrovnávací paměti. Pokud **režimu & ios_base::out** je nenulové hodnoty, funkce mění další pozice se zapisovat do výstupní vyrovnávací paměť. Pro datový proud má pravděpodobně musí existovat jeho vyrovnávací paměti. Umísťovací operace úspěšná výsledný datový proud pozice musí ležet v řízené sekvenci. V opačném případě (nebo pokud je ovlivněno ani pozice), umísťovací operace selže.

## <a name="str"></a>  basic_stringbuf::str

Nastaví nebo získá beze změny na pozici zápis textu do vyrovnávací paměti řetězců.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

`_Newstr` Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md) \< **Elem**, **Tr**, alokační **>,** jejichž řízené sekvenci je kopie pořadí řízené  **\*to**.

### <a name="remarks"></a>Poznámky

První člen funkce vrátí objekt basic_string – třída < **Elem**, **Tr**, `Alloc`>, jejíž řízené sekvenci je kopii pořadí řízené  **\*to**. Pořadí zkopírovat závisí na režimu uložené stringbuf –:

- Pokud **režimu & ios_base::out** nenulový a existuje výstupní vyrovnávací paměť, sekvenci celý výstupní vyrovnávací paměť ( [epptr –](../standard-library/basic-streambuf-class.md#epptr) - [pbase –](../standard-library/basic-streambuf-class.md#pbase) elementy od s `pbase`).

- Pokud **režimu & ios_base::in** nenulový a existuje vstupní vyrovnávací paměť, sekvenci celý vstupní vyrovnávací paměť ( [egptr –](../standard-library/basic-streambuf-class.md#egptr) - [eback –](../standard-library/basic-streambuf-class.md#eback) elementy počínaje `eback`).

- Zkopírovaný pořadí, jinak hodnota je prázdná.

Druhý členská funkce zruší přidělení žádné pořadí aktuálně řízené  **\*to**. Potom přiděluje kopii pořadí řízené `_Newstr`. Pokud **režimu & ios_base::in** je nenulové hodnoty, nastaví vstupní vyrovnávací paměť k začít číst od začátku pořadí. Pokud **režimu & ios_base::out** je nenulové hodnoty, nastaví výstupní vyrovnávací paměť zahájíte zápis na začátek pořadí.

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

Přidruží název typu s **Tr** parametr šablony.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **Tr**.

## <a name="underflow"></a>  basic_stringbuf::underflow

Chráněný, virtuální funkce k extrakci aktuálního elementu ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof). Funkce aktuálního elementu ve vstupní datový proud, který se převedou.

### <a name="remarks"></a>Poznámky

Chráněný člen virtuální funkce pokusí extrahovat aktuálního elementu **bajtů** ze vstupní vyrovnávací paměť, přechodu na aktuální pozici datového proudu a vrátí prvek jako **traits_type –::**[na _int_type](../standard-library/char-traits-struct.md#to_int_type)( **bajtů**). Je to lze provést jedním způsobem: na pozici pro čtení je k dispozici, pak má **bajtů** jako element uložené ve čtení pozici a přejde na další ukazatele pro vstupní vyrovnávací paměť.

## <a name="swap"></a>  basic_streambuf::swap

Zamění obsah této vyrovnávací paměti řetězců s jinou vyrovnávací paměti.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

`other` Basic_stringbuf jejichž obsah se vzájemně zaměněny s Tento basic_stringbuf.

### <a name="remarks"></a>Poznámky

## <a name="op_eq"></a>  basic_stringbuf::Operator =

Obsah basic_stringbuf na pravé straně operátoru přiřadí basic_stringbuf na levé straně.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

`other` Basic_stringbuf, jejichž obsah, včetně vlastnosti národního prostředí, budou přiřazeny stringbuf – na levé straně operátoru.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
