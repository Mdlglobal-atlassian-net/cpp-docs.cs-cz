---
title: basic_filebuf – třída
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_filebuf
- fstream/std::basic_filebuf::char_type
- fstream/std::basic_filebuf::int_type
- fstream/std::basic_filebuf::off_type
- fstream/std::basic_filebuf::pos_type
- fstream/std::basic_filebuf::traits_type
- fstream/std::basic_filebuf::close
- fstream/std::basic_filebuf::is_open
- fstream/std::basic_filebuf::open
- fstream/std::basic_filebuf::overflow
- fstream/std::basic_filebuf::pbackfail
- fstream/std::basic_filebuf::seekoff
- fstream/std::basic_filebuf::seekpos
- fstream/std::basic_filebuf::setbuf
- fstream/std::basic_filebuf::Swap
- fstream/std::basic_filebuf::sync
- fstream/std::basic_filebuf::uflow
- fstream/std::basic_filebuf::underflow
helpviewer_keywords:
- std::basic_filebuf [C++]
- std::basic_filebuf [C++], char_type
- std::basic_filebuf [C++], int_type
- std::basic_filebuf [C++], off_type
- std::basic_filebuf [C++], pos_type
- std::basic_filebuf [C++], traits_type
- std::basic_filebuf [C++], close
- std::basic_filebuf [C++], is_open
- std::basic_filebuf [C++], open
- std::basic_filebuf [C++], overflow
- std::basic_filebuf [C++], pbackfail
- std::basic_filebuf [C++], seekoff
- std::basic_filebuf [C++], seekpos
- std::basic_filebuf [C++], setbuf
- std::basic_filebuf [C++], Swap
- std::basic_filebuf [C++], sync
- std::basic_filebuf [C++], uflow
- std::basic_filebuf [C++], underflow
ms.assetid: 3196ba5c-bf38-41bd-9a95-70323ddfca1a
ms.openlocfilehash: 817e7fb2b434d06d6c0dfdfc100be8004f6fa4ef
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332644"
---
# <a name="basicfilebuf-class"></a>basic_filebuf – třída

Popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky typu *Elem*, jehož vlastnosti znaků určuje třídu *Tr*, do a z pořadí prvků, které jsou uložené v externím souboru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
Základní prvek vyrovnávací paměti souboru.

*tr*<br/>
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky typu *Elem*, jehož vlastnosti znaků určuje třídu *Tr*, do a z pořadí prvků, které jsou uloženy v externí soubor.

> [!NOTE]
> Objekty typu `basic_filebuf` jsou vytvořeny pomocí vnitřní vyrovnávací paměť typu `char *` bez ohledu na to `char_type` určené parametrem typu *Elem*. To znamená, že řetězec znaků Unicode (obsahující **wchar_t** znaků) budou převedeny na řetězec ANSI (obsahující **char** znaků) před zápisem do vnitřní vyrovnávací paměti. K ukládání do vyrovnávací paměti řetězců v kódu Unicode, vytvořte nové vyrovnávací paměti typu **wchar_t** a nastavte ho pomocí [basic_streambuf::pubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` metody. Pokud chcete zobrazit příklad, který ukazuje toto chování, najdete níže.

Objekt třídy `basic_filebuf` <  `Elem`, `Tr`> ukládá ukazatel souboru, který vytváří `FILE` objekt, který určuje datový proud přidružený k otevření souboru. Také ukládá ukazatele do dvou charakteristiky převod souboru pro použití chráněných členským funkcím [přetečení](#overflow) a [podtečení](#underflow). Další informace najdete v tématu [basic_filebuf::open](#open).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vynutit objekt typu `basic_filebuf<wchar_t>` k uložení znaky znakové sady Unicode v jeho vnitřní vyrovnávací paměť pomocí volání `pubsetbuf()` metody.

```cpp
// unicode_basic_filebuf.cpp
// compile with: /EHsc

#include <iostream>
#include <string>
#include <fstream>
#include <iomanip>
#include <memory.h>
#include <string.h>

#define IBUFSIZE 16

using namespace std;

void hexdump(const string& filename);

int main()
{
    wchar_t* wszHello = L"Hello World";
    wchar_t wBuffer[128];

    basic_filebuf<wchar_t> wOutFile;

    // Open a file, wcHello.txt, then write to it, then dump the
    // file's contents in hex
    wOutFile.open("wcHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wcHello.txt\n";
        return -1;
    }
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "Hex Dump of wcHello.txt - note that output is ANSI chars:\n";
    hexdump(string("wcHello.txt"));

    // Open a file, wwHello.txt, then set the internal buffer of
    // the basic_filebuf object to be of type wchar_t, then write
    // to the file and dump the file's contents in hex
    wOutFile.open("wwHello.txt",
        ios_base::out | ios_base::trunc | ios_base::binary);
    if(!wOutFile.is_open())
    {
        cout << "Error Opening wwHello.txt\n";
        return -1;
    }
    wOutFile.pubsetbuf(wBuffer, (streamsize)128);
    wOutFile.sputn(wszHello, (streamsize)wcslen(wszHello));
    wOutFile.close();
    cout << "\nHex Dump of wwHello.txt - note that output is wchar_t chars:\n";
    hexdump(string("wwHello.txt"));

    return 0;
}

// dump contents of filename to stdout in hex
void hexdump(const string& filename)
{
    fstream ifile(filename.c_str(),
        ios_base::in | ios_base::binary);
    char *ibuff = new char[IBUFSIZE];
    char *obuff = new char[(IBUFSIZE*2)+1];
    int i;

    if(!ifile.is_open())
    {
        cout << "Cannot Open " << filename.c_str()
             << " for reading\n";
        return;
    }
    if(!ibuff || !obuff)
    {
        cout << "Cannot Allocate buffers\n";
        ifile.close();
        return;
    }

    while(!ifile.eof())
    {
        memset(obuff,0,(IBUFSIZE*2)+1);
        memset(ibuff,0,IBUFSIZE);
        ifile.read(ibuff,IBUFSIZE);

        // corner case where file is exactly a multiple of
        // 16 bytes in length
        if(ibuff[0] == 0 && ifile.eof())
            break;

        for(i = 0; i < IBUFSIZE; i++)
        {
            if(ibuff[i] >= ' ')
                obuff[i] = ibuff[i];
            else
                obuff[i] = '.';

            cout << setfill('0') << setw(2) << hex
                 << (int)ibuff[i] << ' ';
        }
        cout << "  " << obuff << endl;
    }
    ifile.close();
}
```

```Output
Hex Dump of wcHello.txt - note that output is ANSI chars:
48 65 6c 6c 6f 20 57 6f 72 6c 64 00 00 00 00 00   Hello World.....

Hex Dump of wwHello.txt - note that output is wchar_t chars:
48 00 65 00 6c 00 6c 00 6f 00 20 00 57 00 6f 00   H.e.l.l.o. .W.o.
72 00 6c 00 64 00 00 00 00 00 00 00 00 00 00 00   r.l.d...........
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_filebuf](#basic_filebuf)|Vytvoří objekt typu `basic_filebuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Přidruží název typu se `Elem` parametr šablony.|
|[int_type](#int_type)|Vytvoří tento typ v rámci `basic_filebuf`společnosti ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|
|[off_type](#off_type)|Vytvoří tento typ v rámci `basic_filebuf`společnosti ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|
|[pos_type](#pos_type)|Vytvoří tento typ v rámci `basic_filebuf`společnosti ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|
|[traits_type](#traits_type)|Přidruží název typu se `Tr` parametr šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[close](#close)|Soubor se zavře.|
|[is_open](#is_open)|Určuje, zda je soubor otevřen.|
|[open](#open)|Otevře se soubor.|
|[přetečení](#overflow)|Chráněné virtuální funkce, která může být volána při vložení nového znaku do plné vyrovnávací paměti.|
|[pbackfail –](#pbackfail)|Chráněná virtuální členská funkce se pokusí vrátit elementu do vstupního datového proudu a usnadňují aktuálního elementu (ukazuje další ukazatel).|
|[seekoff –](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.|
|[seekpos –](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.|
|[setbuf](#setbuf)|Chráněná virtuální členská funkce se provede konkrétní operace pro každou odvozené datový proud vyrovnávací paměti.|
|[Swap](#swap)|Vymění obsah této `basic_filebuf` obsahu poskytnutého `basic_filebuf` parametru.|
|[sync](#sync)|Chráněná, virtuální funkce se pokusí o synchronizaci řízené datové proudy s jakékoli přidružené externích datových proudů.|
|[uflow –](../standard-library/basic-streambuf-class.md#uflow)|Chráněná, virtuální funkce se extrahovat aktuálního elementu ze vstupního datového proudu.|
|[podtečení](#underflow)|Chráněná, virtuální funkce se extrahovat aktuálního elementu ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream – >

**Namespace:** std

## <a name="basic_filebuf"></a>  basic_filebuf::basic_filebuf

Vytvoří objekt typu `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Poznámky

První konstruktor uloží ukazatel s hodnotou null v všechny ukazatele řízení vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Také ukládá ukazatel s hodnotou null v ukazatel na soubor.

Druhý konstruktor inicializuje objekt s obsahem `right`, považován za odkaz rvalue.

## <a name="char_type"></a>  basic_filebuf::char_type

Přidruží název typu se `Elem` parametr šablony.

```cpp
typedef Elem char_type;
```

## <a name="close"></a>  basic_filebuf::Close

Soubor se zavře.

```cpp
basic_filebuf<Elem, Tr> *close();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí ukazatel s hodnotou null, pokud ukazatel souboru je ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

`close` volání `fclose`( **fp**). Pokud tato funkce vrátí nenulovou hodnotu, funkce vrátí ukazatel s hodnotou null. V opačném případě vrátí **to** k označení, že soubor byl úspěšně uzavřen.

Pro celou datového proudu, pokud žádné vložení došlo od datový proud byl otevřen nebo od posledního volání `streampos`, volání funkce [přetečení](#overflow). Také vloží jakékoli sekvenci potřebné k obnovení stavu počáteční převod pomocí omezující vlastnost převod souboru `fac` volat `fac.unshift` podle potřeby. Každý prvek `byte` typu **char** tedy vytvořilo se zapisují do přidružené datový proud určený ukazatel na soubor `fp` jako by následných voláních formuláře `fputc`( **bajtů**, **fp**). Pokud volání `fac.unshift` nebo jakékoli zápisu selže, funkce selže.

### <a name="example"></a>Příklad

Následující příklad předpokládá dva soubory v aktuálním adresáři: basic_filebuf_close.txt (obsah je "testování") a iotest.txt (obsah je "ssss").

```cpp
// basic_filebuf_close.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main() {
   using namespace std;
   ifstream file;
   basic_ifstream <wchar_t> wfile;
   char c;
   // Open and close with a basic_filebuf
   file.rdbuf()->open( "basic_filebuf_close.txt", ios::in );
   file >> c;
   cout << c << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "iotest.txt" );
   file >> c;
   cout << c << endl;
   file.close( );

   // open a file with a wide character name
   wfile.open( L"iotest.txt" );

   // Open and close a nonexistent with a basic_filebuf
   file.rdbuf()->open( "ziotest.txt", ios::in );
   cout << file.fail() << endl;
   file.rdbuf( )->close( );

   // Open/close directly
   file.open( "ziotest.txt" );
   cout << file.fail() << endl;
   file.close( );
}
```

```Output
t
s
0
1
```

## <a name="int_type"></a>  basic_filebuf::int_type

Vytvoří tento typ v rámci oboru basic_filebuf – od ekvivalentem typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a>  basic_filebuf::is_open

Určuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud ukazatel na soubor není ukazatel s hodnotou null.

### <a name="example"></a>Příklad

```cpp
// basic_filebuf_is_open.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;
   ifstream file;
   cout << boolalpha << file.rdbuf( )->is_open( ) << endl;

   file.open( "basic_filebuf_is_open.cpp" );
   cout << file.rdbuf( )->is_open( ) << endl;
}
```

```Output
false
true
```

## <a name="off_type"></a>  basic_filebuf::off_type

Vytvoří tento typ v rámci oboru basic_filebuf – od ekvivalentem typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a>  basic_filebuf::Open

Otevře se soubor.

```cpp
basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const char* _Filename,
    ios_base::openmode _Mode);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode,
    int _Prot = (int)ios_base::_Openprot);

basic_filebuf<Elem, Tr> *open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>Parametry

*Náze_v souboru*<br/>
Název souboru, který se otevře.

*Reži_m*<br/>
Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*_Prot*<br/>
Výchozí soubor otevřít ochranu, odpovídá *shflag* parametr [_fsopen – _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Návratová hodnota

Pokud ukazatel souboru je ukazatel s hodnotou null, funkce vrátí ukazatel s hodnotou null. V opačném případě vrátí **to**.

### <a name="remarks"></a>Poznámky

Členská funkce otevře soubor s názvem souboru *filename*, voláním [fopen](../c-runtime-library/reference/fopen-wfopen.md)( *filename*, **strmode**). `strmode` se určí na základě **režim &**~ ( [snědli](../standard-library/ios-base-class.md#openmode) & &#124; [binární](../standard-library/ios-base-class.md#openmode)):

- `ios_base::in` změní **"r"** (otevřít existující soubor pro čtení).

- [ios_base::Out](../standard-library/ios-base-class.md#fmtflags) nebo **ios_base::out &#124; ios_base::trunc** stane **"w"** (zkrátit existující soubor nebo vytvořte pro zápis).

- **ios_base::Out &#124; aplikace** stane **"a"** (otevřít existující soubor pro přidávání všechny operace zápisu).

- **ios_base::in &#124; ios_base::out** stane **"r +"** (otevřít existující soubor pro čtení a zápis).

- **ios_base::in &#124; ios_base::out &#124; ios_base::trunc** stane **"w +"** (zkrátit existující soubor nebo vytvořte pro čtení a zápis).

- **ios_base::in &#124; ios_base::out &#124; ios_base::app** stane **"a +"** (otevřít existující soubor pro čtení a pro přidávání všechny operace zápisu).

Pokud **režim & ios_base::binary** je nenulovou hodnotu, funkce přidá `b` k `strmode` otevřete binárního datového proudu místo textového datového proudu. Pak uloží hodnotu vrácenou příkazem `fopen` v ukazatel na soubor `fp`. Pokud **režim & ios_base::ate** je nenulový ukazatel na soubor není ukazatel s hodnotou null, volání funkce `fseek`( **fp**, 0, `SEEK_END`) na pozici datový proud na konci souboru. Pokud umístění operace selže, volání funkce [zavřete](#close)( `fp`) a ukládá ukazatel s hodnotou null ukazatel na soubor.

Pokud ukazatel na soubor není ukazatel s hodnotou null, funkce určuje omezující vlastnost převod souboru: `use_facet` <  `codecvt` <  **Elem**, `char`, **traits_type::** [ state_type](../standard-library/char-traits-struct.md#state_type)>> ( [getloc –](../standard-library/basic-streambuf-class.md#getloc)), používají [podtečení](#underflow) a [přetečení](#overflow).

Pokud ukazatel souboru je ukazatel s hodnotou null, funkce vrátí ukazatel s hodnotou null. V opačném případě vrátí **to**.

### <a name="example"></a>Příklad

Zobrazit [basic_filebuf::close](#close) příklad, který používá `open`.

## <a name="op_eq"></a>  basic_filebuf::Operator =

Přiřazení obsahu tohoto objektu. datový proud vyrovnávací paměti. Toto je přiřazení pro přesun zahrnující rvalue kopii nenechává za sebou.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Odkaz rvalue na [basic_filebuf –](../standard-library/basic-filebuf-class.md) objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí * to.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu s použitím obsah *správné*, považován za odkaz rvalue. Další informace najdete v tématu [Rvalue Reference Declarator: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a>  basic_filebuf::Overflow

Volá se, když znak nového je vložen do plné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti nebo `traits_type::eof`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`. V opačném případě vrátí **traits_type::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Poznámky

Pokud *_Meta* **! = traits_type::**[eof](../standard-library/char-traits-struct.md#eof), chcete-li vložit element endeavors chráněná virtuální členská funkce **ch = traits_type::** [ to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*_Meta*) do výstupní vyrovnávací paměť. To lze provést různými způsoby:

- Pokud pozici zápisu je k dispozici, můžete uložit prvek na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.

- To může zpřístupnit pozici zápisu přidělením nové nebo další úložiště pro výstupní vyrovnávací paměť.

- Může převést všechny čekající výstup do výstupní vyrovnávací paměť, za nímž následuje `ch`, s použitím omezující vlastnost převod souboru `fac` volat `fac.out` podle potřeby. Každý prvek `ch` typu *char* tedy vytvořilo se zapisují do přidružené datový proud určený ukazatel na soubor `fp` jako by následných voláních formuláře `fputc`( **ch**, **fp**). Pokud se zápis ani převod nezdaří, funkce selže.

## <a name="pbackfail"></a>  basic_filebuf::pbackfail

Se pokusí vrátit elementu do vstupního datového proudu a usnadňují aktuálního elementu (ukazuje další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti, nebo `traits_type::eof`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`. V opačném případě vrátí **traits_type::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(*\_Meta*).

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí zpět elementu do vstupní vyrovnávací paměť a pak jej aktuálního elementu (ukazuje další ukazatel). Pokud  *\_Meta* **== traits_type::**[eof](../standard-library/char-traits-struct.md#eof), elementu, který chcete vložit zpět je v podstatě je již ve službě stream před aktuální prvek. V opačném případě se nahrazuje tento prvek **ch = traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*). Funkci lze vrátit zpět element různými způsoby:

- Pokud putback – pozice je k dispozici a element v ní uloženy při porovnání rovna `ch`, je snížení další ukazatele pro vstupní vyrovnávací paměť.

- Pokud funkce můžete vytvářet `putback` umístění k dispozici, můžete udělat, nastavte další ukazatel tak, aby odkazoval na umístění a uložte `ch` na této pozici.

- Pokud funkce lze odeslat zpět element do vstupního datového proudu, je tak učinit, například voláním `ungetc` pro element typu **char**.

## <a name="pos_type"></a>  basic_filebuf::pos_type

Vytvoří tento typ v rámci oboru basic_filebuf – od ekvivalentem typu se stejným názvem v `Tr` oboru.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_filebuf::seekoff

Se pokusí změnit aktuální pozice řízené datových proudů.

```cpp
virtual pos_type seekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Pozice hledání pro relativně *_Way*.

*_Way*<br/>
Výchozí bod pro operace. Zobrazit [seekdir](../standard-library/ios-base-class.md#seekdir) možných hodnot.

*_Which*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo pozice neplatný datový proud.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce endeavors ke změně aktuální pozice řízené datových proudů. Pro objekt třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, pozici v datovém proudu lze znázornit v objektu typu `fpos_t`, která ukládá posun a bylo nutné žádné informace o stavu analyzovat širokou datového proudu. Posunutí nula označí první prvek datového proudu. (Objekt typu [pos_type](../standard-library/basic-streambuf-class.md#pos_type) ukládá alespoň `fpos_t` objektu.)

Pro soubor otevřen pro čtení a zápis vstupní a výstupní streamy jsou umístěny v kombinaci. Chcete-li přepnout mezi vkládání a extrahování, musí volat buď [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff) nebo [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos). Volání `pubseekoff` (a tedy do `seekoff`) mají různá omezení pro [textové datové proudy](../c-runtime-library/text-and-binary-streams.md), [binární datové proudy](../c-runtime-library/text-and-binary-streams.md), a [široké proudy](../c-runtime-library/byte-and-wide-streams.md).

Pokud se ukazatel na soubor `fp` je ukazatel s hodnotou null, funkce selže. V opačném případě endeavors změnit pozici v datovém proudu voláním `fseek`( **fp**, `_Off`, `_Way`). Pokud funkce uspěje a výsledné umístění `fposn` se dají určit pomocí volání `fgetpos`( **fp**, **& fposn**), funkce úspěšná. Pokud je funkce úspěšná, vrátí hodnotu typu `pos_type` obsahující `fposn`. V opačném případě vrátí pozici neplatný datový proud.

## <a name="seekpos"></a>  basic_filebuf::seekpos

Se pokusí změnit aktuální pozice řízené datových proudů.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Pozice k vyhledání pro.

*_Which*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Pokud se ukazatel na soubor `fp` je ukazatel s hodnotou null, funkce selže. V opačném případě endeavors změnit pozici v datovém proudu voláním `fsetpos`( **fp**, **& fposn**), kde `fposn` je `fpos_t` objekt uložený v `pos`. Pokud funkce uspěje, funkce vrátí `pos`. V opačném případě vrátí pozici neplatný datový proud. Chcete-li zjistit, zda pozici v datovém proudu je neplatný, porovnejte návratovou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce endeavors ke změně aktuální pozice řízené datových proudů. Pro objekt třídy [basic_filebuf –](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>, pozici v datovém proudu lze znázornit v objektu typu `fpos_t`, které obchody Posun a žádné informace o stavu potřebné analyzovat širokou datového proudu. Posunutí nula označí první prvek datového proudu. (Objekt typu `pos_type` ukládá alespoň `fpos_t` objektu.)

Pro soubor otevřen pro čtení a zápis vstupní a výstupní streamy jsou umístěny v kombinaci. Chcete-li přepnout mezi vkládání a extrahování, musí volat buď [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff) nebo [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos). Volání `pubseekoff` (a tedy na `seekoff`) mají různé omezení pro textové datové proudy, binární datové proudy a široké proudy.

Pro celou datového proudu, pokud žádné vložení došlo od datový proud byl otevřen nebo od posledního volání `streampos`, volání funkce [přetečení](#overflow). Také vloží jakékoli sekvenci potřebné k obnovení stavu počáteční převod pomocí omezující vlastnost převod souboru `fac` volat **fac** `.unshift` podle potřeby. Každý prvek `byte` typu **char** tedy vytvořilo se zapisují do přidružené datový proud určený ukazatel na soubor `fp` jako by následných voláních formuláře `fputc`( **bajtů**, **fp**). Pokud volání `fac.unshift` nebo jakékoli zápisu selže, funkce selže.

## <a name="setbuf"></a>  basic_filebuf::setbuf

Provádí konkrétní operace pro každou odvozené datový proud vyrovnávací paměti.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*<br/>
Ukazatel do vyrovnávací paměti.

*Počet*<br/>
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Chráněná členská funkce vrátí nula, pokud ukazatel na soubor `fp` je ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

`setbuf` volání `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **Elem**)) nabízí pole z `count` prvky počínaje _ *vyrovnávací paměti* jako vyrovnávací paměť pro datový proud. Pokud tato funkce vrátí nenulovou hodnotu, funkce vrátí ukazatel s hodnotou null. V opačném případě vrátí **to** na úspěšné provedení signálu.

## <a name="swap"></a>  basic_filebuf::swap

Vyměňuje obsahy to `basic_filebuf` pro obsah ze zadaných `basic_filebuf`.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
`lvalue` Odkaz na jiný `basic_filebuf`.

## <a name="sync"></a>  basic_filebuf::Sync

Se pokusí o synchronizaci řízené datové proudy s jakékoli přidružené externích datových proudů.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Návratová hodnota

Nula v případě vrátí ukazatel na soubor `fp` je ukazatel s hodnotou null. V opačném případě vrátí nula, pouze pokud volá i [přetečení](#overflow) a `fflush`( **fp**) podaří vyprázdnění všechny čekající výstup do datového proudu.

## <a name="traits_type"></a>  basic_filebuf::traits_type

Přidruží název typu se `Tr` parametr šablony.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a>  basic_filebuf::underflow

Extrahuje aktuálního elementu ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). V opačném případě vrátí `ch`, převedený, jak je popsáno v oddílu Poznámky.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce endeavors extrahovat aktuálního elementu `ch` ze vstupní datový proud stream a vrátí prvek jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`ch`). To lze provést různými způsoby:

- Pokud je k dispozici pozici pro čtení, trvá `ch` jako element uložené v pozici pro čtení a přejde na další ukazatele pro vstupní vyrovnávací paměť.

- Může zobrazit jeden nebo více prvků typu **char**, jako při následných voláních formuláře `fgetc`(**fp**) a převést je na prvek **ch** typu `Elem`pomocí fac omezující vlastnost převod souboru volat `fac.in` podle potřeby. Pokud se čtení ani převod nezdaří, funkce selže.

## <a name="see-also"></a>Viz také:

[\<fstream – >](../standard-library/fstream.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
