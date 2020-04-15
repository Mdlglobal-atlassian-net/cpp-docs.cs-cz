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
ms.openlocfilehash: 35bed08f2495c971df7f79f62e32b3ff68dfb3d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376883"
---
# <a name="basic_filebuf-class"></a>basic_filebuf – třída

Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu *Char_T*, jejichž znakové znaky jsou určeny třídou *Tr*, do a z posloupnosti prvků uložených v externím souboru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Char_T, class Tr = char_traits<Char_T>>
class basic_filebuf : public basic_streambuf<Char_T, Tr>
```

### <a name="parameters"></a>Parametry

*Char_T*\
Základní prvek vyrovnávací paměti souboru.

*Tr*\
Znaky základního prvku vyrovnávací paměti souboru `char_traits<Char_T>`(obvykle).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu *Char_T*, jejichž znakové znaky jsou určeny třídou *Tr*, do a z posloupnosti prvků uložených v externím souboru.

> [!NOTE]
> Objekty `basic_filebuf` typu jsou vytvořeny s vnitřní vyrovnávací paměti `char_type` typu __char\* __ bez ohledu na zadaný parametr typu *Char_T*. To znamená, že řetězec Unicode (obsahující **wchar_t** znaky) bude před zápisem do vnitřní vyrovnávací paměti převeden na řetězec ANSI (obsahující **znaky znaku).** Chcete-li uložit řetězce Unicode do vyrovnávací paměti, vytvořte novou [`basic_streambuf::pubsetbuf`](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` vyrovnávací paměť typu **wchar_t** a nastavte ji pomocí metody. Chcete-li zobrazit příklad, který ukazuje toto chování, viz níže.

Objekt třídy `basic_filebuf<Char_T, Tr>` ukládá ukazatel souboru, `FILE` který označuje objekt, který řídí datový proud přidružený k otevřenému souboru. Ukládá také ukazatele na dvě omezující okolnosti převodu souborů pro použití chráněné členské funkce [přetečení](#overflow) a [podtečení](#underflow). Další informace naleznete [`basic_filebuf::open`](#open)v tématu .

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vynutit `basic_filebuf<wchar_t>` objekt typu pro uložení znaků Unicode v jeho vnitřní vyrovnávací paměti voláním `pubsetbuf()` metody.

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
|[char_type](#char_type)|Přidruží název `Char_T` typu k parametru šablony.|
|[int_type](#int_type)|Tento typ `basic_filebuf`v oboru je ekvivalentní typu stejného `Tr` názvu v oboru.|
|[off_type](#off_type)|Tento typ `basic_filebuf`v oboru je ekvivalentní typu stejného `Tr` názvu v oboru.|
|[pos_type](#pos_type)|Tento typ `basic_filebuf`v oboru je ekvivalentní typu stejného `Tr` názvu v oboru.|
|[traits_type](#traits_type)|Přidruží název `Tr` typu k parametru šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Zavřete](#close)|Zavře soubor.|
|[is_open](#is_open)|Označuje, zda je soubor otevřen.|
|[Otevřít](#open)|Otevře soubor.|
|[Přetečení](#overflow)|Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce se pokusí vrátit prvek zpět do vstupního datového proudu a pak jej znehodnotit aktuálním prvkem (na který odkazuje další ukazatel).|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[setbuf](#setbuf)|Chráněná virtuální členská funkce provádí konkrétní operaci pro každou vyrovnávací paměť odvozeného datového proudu.|
|[Swap](#swap)|Vymění obsah `basic_filebuf` tohoto za obsah zadaný `basic_filebuf` parametr.|
|[synchronizace](#sync)|Chráněná virtuální funkce se pokusí synchronizovat řízené datové proudy se všemi přidruženými externími datovými proudy.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Chráněné, virtuální funkce extrahovat aktuální prvek ze vstupního datového proudu.|
|[Podtečení](#underflow)|Chráněné, virtuální funkce extrahovat aktuální prvek ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream>

**Obor názvů:** std

## <a name="basic_filebufbasic_filebuf"></a><a name="basic_filebuf"></a>basic_filebuf::basic_filebuf

Vytvoří objekt typu `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Poznámky

První konstruktor ukládá ukazatel null ve všech ukazatelích ovládajících vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Také ukládá ukazatel null v ukazatel souboru.

Druhý konstruktor inicializuje objekt s obsahem *right*, považován za odkaz rvalue.

## <a name="basic_filebufchar_type"></a><a name="char_type"></a>basic_filebuf::char_type

Přidruží název `Char_T` typu k parametru šablony.

```cpp
typedef Char_T char_type;
```

## <a name="basic_filebufclose"></a><a name="close"></a>basic_filebuf::zavřít

Zavře soubor.

```cpp
basic_filebuf<Char_T, Tr> *close();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí ukazatel null, pokud je ukazatel souboru ukazatel null.

### <a name="remarks"></a>Poznámky

`close`volání `fclose(fp)`. Pokud tato funkce vrátí nenulovou hodnotu, vrátí funkce ukazatel null. V opačném případě vrátí **toto** označuje, že soubor byl úspěšně uzavřen.

Pro široký datový proud, pokud došlo k vložení od otevření datového proudu `streampos`nebo od [`overflow`](#overflow)posledního volání , volání funkce . Také vloží všechny sekvence potřebné k obnovení počátečního stavu převodu `fac` pomocí `fac.unshift` omezující znak převodu souboru volat podle potřeby. Každý vyrobený `byte` prvek typu **char** je zapsán do přidruženého datového proudu určeného ukazatelem `fp` souboru, jako by po sobě jdoucími voláními formuláře `fputc(byte, fp)`. Pokud volání `fac.unshift` nebo zápis selže, funkce se nezdaří.

### <a name="example"></a>Příklad

Následující ukázka předpokládá dva soubory v aktuálním adresáři: *basic_filebuf_close.txt* (obsah je "testování") a *iotest.txt* (obsah je "ssss").

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

## <a name="basic_filebufint_type"></a><a name="int_type"></a>basic_filebuf::int_type

Umožňuje tento `basic_filebuf` typ v rámci oboru ekvivalentní typu `Tr` stejného názvu v oboru.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_filebufis_open"></a><a name="is_open"></a>basic_filebuf::is_open

Označuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud ukazatel souboru není null.

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

## <a name="basic_filebufoff_type"></a><a name="off_type"></a>basic_filebuf::off_type

Umožňuje tento `basic_filebuf` typ v rámci oboru ekvivalentní typu `Tr` stejného názvu v oboru.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_filebufopen"></a><a name="open"></a>basic_filebuf::otevřít

Otevře soubor.

```cpp
basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const char* filename,
    ios_base::openmode mode);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode,
    int protection = (int)ios_base::_Openprot);

basic_filebuf<Char_T, Tr> *open(
    const wchar_t* filename,
    ios_base::openmode mode);
```

### <a name="parameters"></a>Parametry

*Název_souboru*\
Název souboru, který chcete otevřít.

*Režimu*\
Jeden z výčtů [`ios_base::openmode`](../standard-library/ios-base-class.md#openmode)v .

*Ochranu*\
Výchozí ochrana při otevírání souborů, která odpovídá parametru *shflag* v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Návratová hodnota

Pokud je vyrovnávací paměť již otevřena nebo pokud je ukazatel souboru ukazatelem null, funkce vrátí ukazatel null. V opačném případě vrátí **toto**.

### <a name="remarks"></a>Poznámky

Členská funkce otevře soubor s názvem [`fopen`](../c-runtime-library/reference/fopen-wfopen.md) `(filename, strmode)` *názvu souboru*voláním . `strmode`se stanoví `mode & ~(` [`ate`](../standard-library/ios-base-class.md#openmode) `|` [`binary`](../standard-library/ios-base-class.md#openmode) `)`z :

- `ios_base::in``"r"` (otevřete existující soubor pro čtení).

- [ios_base::out](../standard-library/ios-base-class.md#fmtflags) `ios_base::out | ios_base::trunc` nebo `"w"` se stane (zkrátit existující soubor nebo vytvořit pro zápis).

- `ios_base::out | app`(otevřete `"a"` existující soubor pro připojení všech zápisů).

- `ios_base::in | ios_base::out``"r+"` (otevřete existující soubor pro čtení a zápis).

- `ios_base::in | ios_base::out | ios_base::trunc`(zkrátit `"w+"` existující soubor nebo vytvořit pro čtení a zápis).

- `ios_base::in | ios_base::out | ios_base::app`(otevřete `"a+"` existující soubor pro čtení a pro připojení všech zápisů).

Pokud `mode & ios_base::binary` je nenulová, `b` funkce `strmode` připojí k otevření binárnídatový proud namísto textového datového proudu. Potom uloží hodnotu `fopen` vrácenou v `fp`ukazateli souboru . Pokud `mode & ios_base::ate` je nenulová a ukazatel souboru není ukazatel `fseek(fp, 0, SEEK_END)` null, funkce volá umístit datový proud na konci souboru. Pokud tato operace umístění selže, [`close`](#close) `(fp)` funkce volá a ukládá ukazatel null v ukazatel souboru.

Pokud ukazatel souboru není ukazatel null, funkce určuje omezující znak `use_facet<codecvt<Char_T, char, traits_type::` [`state_type`](../standard-library/char-traits-struct.md#state_type) `> >(` [`getloc`](../standard-library/basic-streambuf-class.md#getloc) `)`převodu souboru: , pro použití [podtečením](#underflow) a [přetečením](#overflow).

Pokud je ukazatel souboru ukazatel null, funkce vrátí ukazatel null. V opačném případě vrátí **toto**.

### <a name="example"></a>Příklad

Viz [`basic_filebuf::close`](#close) příklad, který `open`používá .

## <a name="basic_filebufoperator"></a><a name="op_eq"></a>basic_filebuf::operátor=

Přiřaďte obsah tohoto objektu vyrovnávací paměti datového proudu. Toto je přiřazení přesunutí zahrnující rvalue, která nezanechává kopii za sebou.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Rvalue odkaz na [objekt basic_filebuf.](../standard-library/basic-filebuf-class.md)

### <a name="return-value"></a>Návratová hodnota

Vrátí __*this__.

### <a name="remarks"></a>Poznámky

Operátor člena nahradí obsah objektu pomocí obsahu *right*, považovaného za odkaz na rvalue. Další informace naleznete v tématu [Rvalue reference declarator: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="basic_filebufoverflow"></a><a name="overflow"></a>basic_filebuf::přetečení

Nazývá se při vložení nového znaku do úplné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který chcete vložit `traits_type::eof`do vyrovnávací paměti nebo .

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže uspět, vrátí `traits_type::eof`. V opačném `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`případě vrátí .

### <a name="remarks"></a>Poznámky

Pokud `_Meta != traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof)se chráněná virtuální členská funkce `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)` pokusí vložit prvek do výstupní vyrovnávací paměti. Může tak učinit různými způsoby:

- Pokud je k dispozici pozice zápisu, může uložit prvek do pozice zápisu a zvýšit další ukazatel pro výstupní vyrovnávací paměti.

- Může zpřístupnit pozici zápisu přidělením nového nebo dalšího úložiště pro výstupní vyrovnávací paměť.

- Může převést všechny čekající výstup ve `ch`výstupní vyrovnávací paměti, následovaný `fac` , `fac.out` pomocí omezující název převodu souboru volat podle potřeby. Každý vyrobený `ch` prvek typu *char* je zapsán do přidruženého datového proudu určeného ukazatelem `fp` souboru, jako by po sobě jdoucími voláními formuláře `fputc(ch, fp)`. Pokud se nezdaří převod nebo zápis, funkce se nezdaří.

## <a name="basic_filebufpbackfail"></a><a name="pbackfail"></a>basic_filebuf::pbackfail

Pokusí se vrátit prvek zpět do vstupního datového proudu a pak jej učinit aktuálním prvkem (na který odkazuje další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak vložit do vyrovnávací paměti `traits_type::eof`nebo .

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže uspět, vrátí `traits_type::eof`. V opačném `traits_type::` [`not_eof`](../standard-library/char-traits-struct.md#not_eof) `(_Meta)`případě vrátí .

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí prvek zpět do vstupní vyrovnávací paměti a pak z něj udělá aktuální prvek (na který odkazuje další ukazatel). Pokud `_Meta == traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof), prvek push back je efektivně ten, který již v datovém proudu před aktuální prvek. V opačném případě je `ch = traits_type::` [`to_char_type`](../standard-library/char-traits-struct.md#to_char_type) `(_Meta)`tento prvek nahrazen . Funkce může vrátit prvek různými způsoby:

- `putback` Pokud pozice je k dispozici a prvek uložený tam porovná rovná `ch`, může zmenšit další ukazatel pro vstupní vyrovnávací paměti.

- Pokud funkce může `putback` zpřístupnit pozici, může tak učinit, nastavit další ukazatel tak, `ch` aby ukazoval na tuto pozici, a uložit v této pozici.

- Pokud funkce může tlačit zpět prvek na vstupní datový proud, může `ungetc` tak učinit, například voláním pro prvek typu **char**.

## <a name="basic_filebufpos_type"></a><a name="pos_type"></a>basic_filebuf::pos_type

Umožňuje tento `basic_filebuf` typ v rámci oboru ekvivalentní typu `Tr` stejného názvu v oboru.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_filebufseekoff"></a><a name="seekoff"></a>basic_filebuf::seekoff

Pokusí se změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozice hledat vzhledem k *_Way*.

*_Way*\
Počáteční bod pro operace odsazení. Viz [seekdir](../standard-library/ios-base-class.md#seekdir) pro možné hodnoty.

*_Which*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo neplatnou pozici datového proudu.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy. Pro objekt třídy [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`může být pozice datového proudu `fpos_t`reprezentována objektem typu , který ukládá posun a všechny informace o stavu potřebné k analýzě širokého datového proudu. Posun nula odkazuje na první prvek datového proudu. (Objekt typu [`pos_type`](../standard-library/basic-streambuf-class.md#pos_type) ukládá alespoň `fpos_t` objekt.)

Pro soubor otevřený pro čtení i zápis jsou vstupní i výstupní datové proudy umístěny v tandemu. Chcete-li přepínat mezi vkládáním [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)a extrahováním, musíte volat buď nebo . Volání `pubseekoff` (a tedy `seekoff`i ) mají různá omezení pro [textové datové proudy](../c-runtime-library/text-and-binary-streams.md), [binární datové proudy](../c-runtime-library/text-and-binary-streams.md)a [široké datové proudy](../c-runtime-library/byte-and-wide-streams.md).

Pokud je `fp` ukazatel souboru ukazatel null, funkce se nezdaří. V opačném případě se pokusí změnit `fseek(fp, _Off, _Way)`pozici datového proudu voláním . Pokud tato funkce proběhne úspěšně `fposn` a výslednou `fgetpos(fp, &fposn)`pozici lze určit voláním , funkce úspěšné. Pokud je funkce úspěšná, vrátí `pos_type` hodnotu `fposn`typu obsahujícího . V opačném případě vrátí pozici neplatného datového proudu.

## <a name="basic_filebufseekpos"></a><a name="seekpos"></a>basic_filebuf::seekpos

Pokusí se změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual pos_type seekpos(
    pos_type _Sp,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice, o kterou se můžete snažit.

*_Which*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud je `fp` ukazatel souboru ukazatel null, funkce se nezdaří. V opačném případě se pokusí změnit `fsetpos(fp, &fposn)`pozici `fposn` datového `fpos_t` proudu `pos`voláním , kde je objekt uložen v . Pokud tato funkce proběhne `pos`úspěšně, vrátí funkce . V opačném případě vrátí pozici neplatného datového proudu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy. Pro objekt třídy [`basic_filebuf`](../standard-library/basic-filebuf-class.md) `<Char_T, Tr>`může být pozice datového proudu `fpos_t`reprezentována objektem typu , který ukládá posun a všechny informace o stavu potřebné k analýzě širokého datového proudu. Posun nula odkazuje na první prvek datového proudu. (Objekt typu `pos_type` ukládá alespoň `fpos_t` objekt.)

Pro soubor otevřený pro čtení i zápis jsou vstupní i výstupní datové proudy umístěny v tandemu. Chcete-li přepínat mezi vkládáním [`pubseekoff`](../standard-library/basic-streambuf-class.md#pubseekoff) [`pubseekpos`](../standard-library/basic-streambuf-class.md#pubseekpos)a extrahováním, musíte volat buď nebo . Volání `pubseekoff` (a `seekoff`) mají různá omezení pro textové datové proudy, binární datové proudy a široké datové proudy.

Pro široký datový proud, pokud došlo k vložení od otevření datového proudu `streampos`nebo od posledního volání , funkce volá [přetečení](#overflow). Také vloží všechny sekvence potřebné k obnovení počátečního stavu převodu `fac` pomocí `fac.unshift` omezující znak převodu souboru volat podle potřeby. Každý vyrobený `byte` prvek typu **char** je zapsán do přidruženého datového proudu určeného ukazatelem `fp` souboru, jako by po sobě jdoucími voláními formuláře `fputc(byte, fp)`. Pokud volání `fac.unshift` nebo zápis selže, funkce se nezdaří.

## <a name="basic_filebufsetbuf"></a><a name="setbuf"></a>basic_filebuf::setbuf

Provede konkrétní operaci pro každou vyrovnávací paměť odvozeného datového proudu.

```cpp
virtual basic_streambuf<Char_T, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Ukazatel na vyrovnávací paměť.

*Počet*\
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Chráněná členská funkce vrátí `fp` nulu, pokud je ukazatel souboru ukazatelem null.

### <a name="remarks"></a>Poznámky

`setbuf`volání `setvbuf( fp, (char*) _Buffer, _IOFBF, count * sizeof( Char_T))` nabídnout pole `count` prvků začínající *ch_Buffer* jako vyrovnávací paměť pro datový proud. Pokud tato funkce vrátí nenulovou hodnotu, vrátí funkce ukazatel null. V opačném případě se vrátí **k** signalizaci úspěchu.

## <a name="basic_filebufswap"></a><a name="swap"></a>basic_filebuf::swap

Vymění obsah `basic_filebuf` tohoto obsahu za obsah `basic_filebuf`poskytnutého .

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Lvalue odkaz na `basic_filebuf`jinou .

## <a name="basic_filebufsync"></a><a name="sync"></a>basic_filebuf::synchronizace

Pokusí se synchronizovat řízené datové proudy se všemi přidruženými externími datovými proudy.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nulu, `fp` pokud je ukazatel souboru ukazatelem null. V opačném případě vrátí nulu pouze `fflush(fp)` v případě, že volání obou [přetečení](#overflow) a úspěšné vyprázdnění všech čekající výstup do datového proudu.

## <a name="basic_filebuftraits_type"></a><a name="traits_type"></a>basic_filebuf::traits_type

Přidruží název `Tr` typu k parametru šablony.

```cpp
typedef Tr traits_type;
```

## <a name="basic_filebufunderflow"></a><a name="underflow"></a>basic_filebuf::podtočení

Extrahuje aktuální prvek ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže uspět, vrátí `traits_type::` [`eof`](../standard-library/char-traits-struct.md#eof). V opačném `ch`případě vrátí , převedeny, jak je popsáno v poznámky části.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se `ch` pokusí extrahovat aktuální prvek `traits_type::` [`to_int_type`](../standard-library/char-traits-struct.md#to_int_type) `(ch)`ze vstupního datového proudu a vrátí prvek jako . Může tak učinit různými způsoby:

- Pokud je k dispozici pozice `ch` pro čtení, trvá jako prvek uložený v pozici pro čtení a posune další ukazatel pro vstupní vyrovnávací paměti.

- Může číst jeden nebo více prvků typu **char**, jako `fgetc(fp)`by po sobě `ch` jdoucích `Char_T` volání formuláře , `fac` a `fac.in` převést je na prvek typu pomocí omezující název převodu souboru volat podle potřeby. Pokud se nezdaří čtení nebo převod, funkce se nezdaří.

## <a name="see-also"></a>Viz také

[\<fstream>](../standard-library/fstream.md)\
[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
