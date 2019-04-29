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
ms.openlocfilehash: 1ed9deee46f7c99750ee3260a6b2a8de1f0f3397
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409756"
---
# <a name="basicstringbuf-class"></a>basic_stringbuf – třída

Popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky typu `Elem`, jehož vlastnosti znaků určuje třídu `Tr`, do a z pořadí prvků, které jsou uloženy v objektu array.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*ALLOC*<br/>
Třída alokátoru

*Elem*<br/>
Typ základního prvku objektu řetězec.

*tr*<br/>
Vlastnosti znaků specializované na základního elementu řetězce.

## <a name="remarks"></a>Poznámky

Objekt je přidělené, rozšířit a uvolnění podle potřeby a vyřešit tak změny v pořadí.

Objekt basic_stringbuf – třída < `Elem`, `Tr`, `Alloc`> ukládá kopie `ios_base::` [openmode](../standard-library/ios-base-class.md#openmode) argument ze svého konstruktoru jako jeho `stringbuf` režimu **režimu** :

- Pokud `mode & ios_base::in` je nenulová, vstupní vyrovnávací paměť je přístupný. Další informace najdete v tématu [basic_streambuf – třída](../standard-library/basic-streambuf-class.md).

- Pokud `mode & ios_base::out` je nenulová, výstupní vyrovnávací paměť je přístupný.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Vytvoří objekt typu `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[allocator_type](#allocator_type)|Typ je synonymum pro parametr šablony *alokační*.|
|[char_type](#char_type)|Přidruží název typu se *Elem* parametr šablony.|
|[int_type](#int_type)|Vytvoří tento typ v rámci `basic_filebuf`společnosti ekvivalentem typu se stejným názvem v oboru *Tr* oboru.|
|[off_type](#off_type)|Vytvoří tento typ v rámci `basic_filebuf`společnosti ekvivalentem typu se stejným názvem v oboru *Tr* oboru.|
|[pos_type](#pos_type)|Vytvoří tento typ v rámci `basic_filebuf`společnosti ekvivalentem typu se stejným názvem v oboru *Tr* oboru.|
|[traits_type](#traits_type)|Přidruží název typu se *Tr* parametr šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[overflow](#overflow)|Chráněná, virtuální funkce, která může být volána při vložení nového znaku do plné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Funkce chráněná virtuální členská se pokusí vrátit elementu do vstupní vyrovnávací paměť, pak díky aktuálního elementu (ukazuje další ukazatel).|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.|
|[str](#str)|Nastaví nebo získá text ve vyrovnávací paměti řetězce beze změny pozici zápisu.|
|swap||
|[underflow](#underflow)|Chráněná virtuální členská funkce se extrahovat aktuálního elementu ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<sstream >

**Namespace:** std

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

Typ je synonymum pro parametr šablony *alokační*.

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

*_Mode*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Objekt typu [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Poznámky

První konstruktor uloží ukazatel s hodnotou null v všechny ukazatele řízení vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Další informace najdete v části poznámky [basic_streambuf – třída](../standard-library/basic-streambuf-class.md). Také ukládá *reži_m* stringbuf režim. Další informace najdete v části poznámky [basic_stringbuf – třída](../standard-library/basic-stringbuf-class.md).

Druhý konstruktor přiděluje kopii sekvence řízenou objektem řetězce *str*. Pokud `_Mode & ios_base::in` je nenulová, nastaví vstupní vyrovnávací paměť čtení na začátek pořadí spuštění. Pokud `_Mode & ios_base::out` je nenulová, nastaví výstupní vyrovnávací paměť má začít zapisovat na začátek pořadí. Také ukládá *reži_m* stringbuf režim. Další informace najdete v části poznámky [basic_stringbuf – třída](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>  basic_stringbuf::char_type

Přidruží název typu se *Elem* parametr šablony.

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

Vytvoří tento typ v rámci oboru basic_filebuf – od ekvivalentem typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

Vytvoří tento typ v rámci oboru basic_filebuf – od ekvivalentem typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::overflow

Chráněné virtuální funkce, která může být volána při vložení nového znaku do plné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti, nebo `traits_type::eof`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`. V opačném případě vrátí **traits_type::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Poznámky

Pokud  *\_Meta* není výsledkem porovnání **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), chráněná virtuální členská funkce se pokusí vložit element  **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) do výstupní vyrovnávací paměť. To lze provést různými způsoby:

- Pokud pozici zápisu je k dispozici, můžete uložit prvek na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.

- To může zpřístupnit pozici zápisu přidělením nové nebo další úložiště pro výstupní vyrovnávací paměť. Rozšíření do vyrovnávací paměti výstupních tímto způsobem rozšiřuje také všechny přidružené vstupní vyrovnávací paměť.

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

Chráněná virtuální členská funkce se pokusí vrátit elementu do vstupní vyrovnávací paměť a nastavte ji aktuálního elementu (ukazuje další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti, nebo `traits_type::eof`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`. V opačném případě vrátí **traits_type::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Poznámky

Pokud *_Meta* porovná rovno **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), elementu, který chcete vložit zpět je v podstatě je již ve službě stream před aktuální prvek. V opačném případě se nahrazuje tento prvek **bajtů** = **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Funkci lze vrátit zpět element různými způsoby:

- Pokud putback – pozice je k dispozici a element v ní uloženy při porovnání rovna bajtů, je snížení další ukazatele pro vstupní vyrovnávací paměť.

- Pokud putback – pozice je k dispozici, a pokud stringbuf režim umožňuje sekvence má být změněn ( **režim & ios_base::out** je nenulový), může ukládat bajt na pozici putback – a snížení další ukazatele pro vstupní vyrovnávací paměť.

## <a name="pos_type"></a>  basic_stringbuf::pos_type

Vytvoří tento typ v rámci oboru basic_filebuf – od ekvivalentem typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Pozice hledání pro relativně *_Way*. Další informace najdete v tématu [basic_stringbuf::off_type](#off_type).

*_Way*<br/>
Výchozí bod pro operace. Zobrazit [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) možných hodnot.

*_Mode*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic. Další informace najdete v tématu [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo pozice neplatný datový proud.

### <a name="remarks"></a>Poznámky

Pro objekt třídy `basic_stringbuf<Elem, Tr, Alloc>`, pozici v datovém proudu se skládá ze čistě posun datového proudu. Posunutí nula označí první prvek řízené sekvence.

Na nové pozici je stanoven následujícím způsobem:

- Pokud `_Way`  ==  `ios_base::beg`, na nové pozici je začátku datového proudu plus *_Off*.

- Pokud `_Way`  ==  `ios_base::cur`, na nové pozici, je aktuální pozici v datovém proudu plus *_Off*.

- Pokud `_Way`  ==  `ios_base::end`, na nové pozici je konec datového proudu plus *_Off*.

Pokud `_Mode & ios_base::in` je nenulová, změní funkci na další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud `_Mode & ios_base::out` je nenulová, změní funkci na další pozici pro zápis do výstupní vyrovnávací paměť. Pro datový proud bude ovlivněná musí existovat vyrovnávací paměti. Umístění operace úspěšná musí být v řízené sekvenci od výsledný pozici v datovém proudu. Pokud funkce ovlivní obě pozice datového proudu *_Way* musí být `ios_base::beg` nebo `ios_base::end` a oba datové proudy jsou umístěny v stejného elementu. V opačném případě (nebo pokud je ovlivněno ani umístění), umístění nezdaří.

Pokud je funkce úspěšná v změna jednu nebo obě z pozice datového proudu, vrátí pozici výsledný datový proud. V opačném případě selže a vrátí pozici neplatný datový proud.

## <a name="seekpos"></a>  basic_stringbuf::seekpos

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Pozice k vyhledání pro.

*_Mode*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná v změna jednu nebo obě z pozice datového proudu, vrátí pozici výsledný datový proud. V opačném případě selže a vrátí pozici neplatný datový proud. Chcete-li zjistit, zda pozici v datovém proudu je neplatný, porovnejte návratovou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Basic_stringbuf – třída objektu < **Elem**, **Tr**, `Alloc`>, pozici v datovém proudu se skládá ze čistě posun datového proudu. Posunutí nula označí první prvek řízené sekvence. Nové umístění je určeno _ *Sp*.

Pokud **režim & ios_base::in** je nenulová, změní funkci na další pozici pro čtení ve vstupní vyrovnávací paměti. Pokud **režim & ios_base::out** je nenulová, změní funkci na další pozici pro zápis do výstupní vyrovnávací paměť. Pro datový proud bude ovlivněná musí existovat vyrovnávací paměti. Umístění operace úspěšná musí být v řízené sekvenci od výsledný pozici v datovém proudu. V opačném případě (nebo pokud je ovlivněno ani umístění), umístění nezdaří.

## <a name="str"></a>  basic_stringbuf::str

Nastaví nebo získá text ve vyrovnávací paměti řetězce beze změny pozici zápisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*<br/>
Nový řetězec.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt třídy [basic_string](../standard-library/basic-string-class.md) \< **Elem**, **Tr**, alokační **>,** jehož řízené sekvence je kopie řídí pořadí  **\*to**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí objekt třídy basic_string < **Elem**, **Tr**, `Alloc`>, jehož kopii sekvence řízenou parametrem je řízené sekvence  **\*to**. Pořadí zkopírovat závisí na uložených stringbuf režimu:

- Pokud **režim & ios_base::out** je nenulová a výstupní mezipaměti existuje, sekvence je celý výstupní vyrovnávací paměť ( [epptr –](../standard-library/basic-streambuf-class.md#epptr) - [pbase –](../standard-library/basic-streambuf-class.md#pbase) prvků od s `pbase`).

- Pokud **režim & ios_base::in** je nenulová a vstupní vyrovnávací paměť existuje, sekvence je celý vstupní vyrovnávací paměť ( [egptr –](../standard-library/basic-streambuf-class.md#egptr) - [eback –](../standard-library/basic-streambuf-class.md#eback) prvky počínaje `eback`).

- V opačném případě zkopírovaný pořadí je prázdný.

Druhá členská funkce uvolní všechny pořadí, v současnosti řízeno  **\*to**. Potom přiděluje kopii sekvence řízenou parametrem *_Newstr*. Pokud **režim & ios_base::in** je nenulová, nastaví vstupní vyrovnávací paměť čtení na začátek pořadí spuštění. Pokud **režim & ios_base::out** je nenulová, nastaví do vyrovnávací paměti výstupních začít psát na začátek pořadí.

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

Přidruží název typu se *Tr* parametr šablony.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *Tr*.

## <a name="underflow"></a>  basic_stringbuf::underflow

Chráněná, virtuální funkce se extrahovat aktuálního elementu ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). V opačném případě vrátí aktuálního elementu ve vstupní datový proud, které jsou převedeny.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí extrahovat aktuálního elementu `byte` ze vstupní vyrovnávací paměť, přejděte aktuální pozici v datovém proudu a vrátí prvek jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **bajtů**). To lze provést jedním ze způsobů: Pokud je k dispozici pozici pro čtení, trvá `byte` jako element uložené v pozici pro čtení a přejde na další ukazatele pro vstupní vyrovnávací paměť.

## <a name="swap"></a>  basic_streambuf::swap

Zamění obsah této vyrovnávací paměti řetězce s jinou vyrovnávací paměti řetězce.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Basic_stringbuf – jehož obsah se Prohodit s této basic_stringbuf –.

### <a name="remarks"></a>Poznámky

## <a name="op_eq"></a>  basic_stringbuf::operator=

Přiřadí obsah basic_stringbuf – na pravé straně operátoru basic_stringbuf – na levé straně.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Basic_stringbuf –, jejichž obsah, včetně vlastnosti národního prostředí, se přiřadí stringbuf na levé straně operátoru.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
