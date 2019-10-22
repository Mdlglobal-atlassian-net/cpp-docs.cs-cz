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
ms.openlocfilehash: f162545f28af3e2720dceace6c604b5e2441cf48
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690023"
---
# <a name="basic_filebuf-class"></a>basic_filebuf – třída

Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu *elem*, jejichž vlastnosti znaků jsou určeny třídou *TR*, do a z sekvence prvků uložených v externím souboru.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_filebuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Elem* \
Základní prvek vyrovnávací paměti souboru.

*Tr* \
Vlastnosti základního prvku vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem` >).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků typu *elem*, jejichž znakové vlastnosti jsou určeny třídou *TR*, do a z sekvence prvků uložených v externím souboru.

> [!NOTE]
> Objekty typu `basic_filebuf` jsou vytvořeny s vnitřní vyrovnávací pamětí typu `char *` bez ohledu na `char_type` určené parametrem typu *elem*. To znamená, že řetězec Unicode (obsahující znaky **wchar_t** ) bude převeden na řetězec ANSI (obsahující znaky **znaku** ) před zápisem do vnitřní vyrovnávací paměti. Pro ukládání řetězců Unicode do vyrovnávací paměti vytvořte novou vyrovnávací paměť typu **wchar_t** a nastavte ji pomocí metody `()` [basic_streambuf::p ubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) . Příklad, který demonstruje toto chování, najdete níže.

Objekt třídy `basic_filebuf` <  `Elem`, `Tr` > ukládá ukazatel na soubor, který určuje objekt `FILE`, který ovládá datový proud přidružený k otevřenému souboru. Také ukládá ukazatele na dvě omezující vlastnosti převodu souborů pro použití [přetečení](#overflow) a podtečení chráněných členských funkcí [.](#underflow) Další informace naleznete v tématu [basic_filebuf:: Open](#open).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vynutit objekt typu `basic_filebuf<wchar_t>` k ukládání znaků Unicode do vnitřní vyrovnávací paměti voláním metody `pubsetbuf()`.

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
|[char_type](#char_type)|Přidruží název typu k parametru `Elem` šablony.|
|[int_type](#int_type)|Nastaví tento typ v rámci rozsahu `basic_filebuf` ekvivalentem typu se stejným názvem v oboru `Tr`.|
|[off_type](#off_type)|Nastaví tento typ v rámci rozsahu `basic_filebuf` ekvivalentem typu se stejným názvem v oboru `Tr`.|
|[pos_type](#pos_type)|Nastaví tento typ v rámci rozsahu `basic_filebuf` ekvivalentem typu se stejným názvem v oboru `Tr`.|
|[traits_type](#traits_type)|Přidruží název typu k parametru `Tr` šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[close](#close)|Zavře soubor.|
|[is_open](#is_open)|Označuje, zda je soubor otevřen.|
|[open](#open)|Otevře soubor.|
|[plně](#overflow)|Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce se pokusí vrátit prvek do vstupního datového proudu a pak ho nastavit jako aktuální (ukazuje na další ukazatel).|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.|
|[setbuf](#setbuf)|Chráněná virtuální členská funkce provádí operaci specifickou pro každou odvozenou vyrovnávací paměť datového proudu.|
|[Adresu](#swap)|Vyměňuje obsah tohoto `basic_filebuf` pro obsah zadaného `basic_filebuf` parametru.|
|[brání](#sync)|Chráněná virtuální funkce se pokusí synchronizovat řízené streamy s případnými přidruženými externími proudy.|
|[uflow](../standard-library/basic-streambuf-class.md#uflow)|Chráněná virtuální funkce pro extrakci aktuálního prvku ze vstupního datového proudu.|
|[podtečení](#underflow)|Chráněná virtuální funkce pro extrakci aktuálního prvku ze vstupního datového proudu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<fstream >

**Obor názvů:** std

## <a name="basic_filebuf"></a>basic_filebuf::basic_filebuf

Vytvoří objekt typu `basic_filebuf`.

```cpp
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```

### <a name="remarks"></a>Poznámky

První konstruktor ukládá ukazatel s hodnotou null ve všech ukazatelích řídících vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. V ukazateli na soubor také ukládá ukazatel s hodnotou null.

Druhý konstruktor inicializuje objekt s obsahem `right`, který se považuje za odkaz rvalue.

## <a name="char_type"></a>basic_filebuf::char_type

Přidruží název typu k parametru `Elem` šablony.

```cpp
typedef Elem char_type;
```

## <a name="close"></a>basic_filebuf:: Close

Zavře soubor.

```cpp
basic_filebuf<Elem, Tr> *close();
```

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí ukazatel s hodnotou null, pokud je ukazatel na soubor ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

`close` volá `fclose` ( **FP**). Pokud tato funkce vrací nenulovou hodnotu, funkce vrátí ukazatel s hodnotou null. V opačném případě **vrátí hodnotu, která označuje** , že byl soubor úspěšně uzavřen.

Pro velký proud, pokud k nějakému vložení došlo od otevření datového proudu nebo od posledního volání `streampos`, funkce volá [přetečení](#overflow). Vloží také všechny sekvence potřebné k obnovení stavu prvotního převodu pomocí omezující vlastnosti převodu souboru `fac` k volání `fac.unshift` podle potřeby. Každý prvek `byte` typu, který **je takto vytvořen** , je zapsán do přidruženého datového proudu, který je označen ukazatelem souboru `fp` jako if po následných voláních formuláře `fputc` ( **Byte**, **FP**). Pokud volání `fac.unshift` nebo jakýkoli zápis selže, funkce není úspěšná.

### <a name="example"></a>Příklad

Následující příklad předpokládá dva soubory v aktuálním adresáři: basic_filebuf_close. txt (obsah je "test") a iotest. txt (obsah je "ssss").

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

## <a name="int_type"></a>basic_filebuf::int_type

Nastaví tento typ v rámci oboru basic_filebuf's jako ekvivalent typu se stejným názvem v oboru `Tr`.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="is_open"></a>basic_filebuf::is_open

Označuje, zda je soubor otevřen.

```cpp
bool is_open() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud ukazatel na soubor není ukazatel s hodnotou null.

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

## <a name="off_type"></a>basic_filebuf::off_type

Nastaví tento typ v rámci oboru basic_filebuf's jako ekvivalent typu se stejným názvem v oboru `Tr`.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="open"></a>basic_filebuf:: Open

Otevře soubor.

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

*_Filename* \
Název souboru, který se má otevřít

*_Mode* \
Jeden z výčtů v [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*_Prot* \
Výchozí ochrana při otevírání souborů, která odpovídá parametru *Shflag* v [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md).

### <a name="return-value"></a>Návratová hodnota

Pokud je ukazatel na soubor ukazatel s hodnotou null, funkce vrátí ukazatel s hodnotou null. V opačném případě **to vrátí.**

### <a name="remarks"></a>Poznámky

Členská funkce otevře soubor *s názvem filename a*zavolá [fopen](../c-runtime-library/reference/fopen-wfopen.md)( *filename*, **strmode**). `strmode` se určuje z **režimu &** [~ (](../standard-library/ios-base-class.md#openmode) &#124; [binární](../standard-library/ios-base-class.md#openmode)&.

- `ios_base::in` se bude **"r"** (otevřít existující soubor pro čtení).

- [ios_base:: out](../standard-library/ios-base-class.md#fmtflags) nebo **ios_base:: &#124; ios_base:: TRUNC –** se bude **"w"** (ořízne existující soubor nebo vytvoří pro zápis).

- **ios_base:: out &#124; App** se spustí **"a"** (otevře existující soubor pro připojení všech zápisů).

- **ios_base:: in &#124; ios_base:: out** se zobrazí **"r +"** (otevřít existující soubor pro čtení a zápis).

- **ios_base:: in &#124; ios_base:: out &#124; ios_base:: TRUNC –** se přestanou **"w +"** (ořízne existující soubor nebo vytvoří pro čtení a zápis).

- **ios_base:: in &#124; ios_base:: out &#124; ios_base:: App** se spustí **"a +"** (otevře existující soubor pro čtení a připojení všech zápisů).

Pokud **režim & ios_base:: Binary** je nenulový, funkce připojí `b` k `strmode` k otevření binárního datového proudu namísto textového streamu. Pak uloží hodnotu vrácenou `fopen` v `fp` ukazatel na soubor. IF **& ios_base::** oddálení je nenulové a ukazatel souboru není ukazatel s hodnotou null, funkce volá `fseek` ( **FP**, 0, `SEEK_END`) k umístění datového proudu na konci souboru. Pokud tato operace umístění neproběhne úspěšně, volání funkce [ukončí](#close)(`fp`) a uloží ukazatel s hodnotou null do ukazatele souboru.

Pokud ukazatel na soubor není ukazatel s hodnotou null, funkce určuje omezující vlastnost souboru: `use_facet` <  `codecvt` < **elem**, `char`, **traits_type::** [state_type](../standard-library/char-traits-struct.md#state_type)> > ( [getloc](../standard-library/basic-streambuf-class.md#getloc)) pro použití [podtečením. ](#underflow)a [přetečení](#overflow).

Pokud je ukazatel na soubor ukazatel s hodnotou null, funkce vrátí ukazatel s hodnotou null. V opačném případě **to vrátí.**

### <a name="example"></a>Příklad

Příklad, který používá `open`, naleznete v tématu [basic_filebuf:: Close](#close) .

## <a name="op_eq"></a>basic_filebuf:: operator =

Přiřaďte obsah tohoto objektu vyrovnávací paměti streamu. Toto je přiřazení přesunutí zahrnující rvalue, které neopouští kopii.

```cpp
basic_filebuf& operator=(basic_filebuf&& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Odkaz rvalue na objekt [basic_filebuf](../standard-library/basic-filebuf-class.md) .

### <a name="return-value"></a>Návratová hodnota

Vrátí * this.

### <a name="remarks"></a>Poznámky

Členský operátor nahradí obsah objektu pomocí obsahu *vpravo*, který se považuje za odkaz rvalue. Další informace naleznete v tématu [rvalue reference deklarátor: & &](../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="overflow"></a>basic_filebuf:: přetečení

Volá se, když se do úplné vyrovnávací paměti vloží nový znak.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta* \
Znak, který má být vložen do vyrovnávací paměti nebo `traits_type::eof`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`. V opačném případě vrátí **traits_type::** [Not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *meta*).

### <a name="remarks"></a>Poznámky

Pokud *_Meta* **! = traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), chráněná virtuální členská funkce budoucna vloží element **ch = traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *_Meta*) do výstupní vyrovnávací paměti. Může tak učinit různými způsoby:

- Pokud je k dispozici pozice pro zápis, může prvek Uložit do pozice pro zápis a zvýšit další ukazatel pro výstupní vyrovnávací paměť.

- Dá se k dispozici pozice pro zápis přidělením nového nebo dalšího úložiště pro výstupní vyrovnávací paměť.

- Může převést libovolný nedokončený výstup ve výstupní vyrovnávací paměti, následovaný `ch`, pomocí omezující vlastnosti převodu souboru `fac` k volání `fac.out` podle potřeby. Každý prvek `ch` typu, který *je takto vytvořen* , je zapsán do přidruženého datového proudu určeného ukazatelem souboru `fp` jako if prostřednictvím následných volání formuláře `fputc` ( **ch**, **FP**). Pokud převod nebo zápis selže, funkce není úspěšná.

## <a name="pbackfail"></a>basic_filebuf::p neúspěšného selhání

Pokusí se vrátit prvek do vstupního datového proudu a potom ho nastavit jako aktuální. element (ukazuje na další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```

### <a name="parameters"></a>Parametry

*_Meta* \
Znak, který se má vložit do vyrovnávací paměti, nebo `traits_type::eof`.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí `traits_type::eof`. V opačném případě vrátí **traits_type::** [not_eof](../standard-library/char-traits-struct.md#not_eof)( *\_Meta*).

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí prvek do vstupní vyrovnávací paměti a poté nastaví aktuální prvek (ukazuje na další ukazatel). Pokud *\_Meta* **= = traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), element, který se má vrátit zpět, je efektivně ten, který už je v proudu před aktuálním prvkem. V opačném případě je tento prvek nahrazen prvkem **ch = traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_Meta*). Funkce může vložit element zpět různými způsoby:

- Pokud je k dispozici putback pozice a element, na který se ukládá, se rovná `ch`, může snížit další ukazatel pro vstupní vyrovnávací paměť.

- Pokud funkce může zpřístupnit `putback` pozici, může to udělat, nastavit další ukazatel na místo na této pozici a uložit `ch` na této pozici.

- Pokud funkce může přejít zpět na vstupní datový proud, může to provést, například voláním `ungetc` pro element typu **char**.

## <a name="pos_type"></a>basic_filebuf::p os_type

Nastaví tento typ v rámci oboru basic_filebuf's jako ekvivalent typu se stejným názvem v oboru `Tr`.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>basic_filebuf:: seekoff

Pokusí se změnit aktuální pozice pro řízené streamy.

```cpp
virtual pos_type seekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off* \
Pozice pro hledání vzhledem k *_Way*.

*_Way* \
Výchozí bod pro operace posunu. Možné hodnoty najdete v tématu [seekdir](../standard-library/ios-base-class.md#seekdir) .

*_Which* \
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo neplatnou pozici streamu.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce budoucna změnu aktuální pozice pro řízené streamy. V případě objektu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem`, `Tr` >, může být pozice datového proudu reprezentována objektem typu `fpos_t`, který ukládá posun a všechny informace o stavu potřebné k analýze datového proudu ve světě. Nula odsazení určuje první prvek streamu. (Objekt typu [pos_type](../standard-library/basic-streambuf-class.md#pos_type) ukládá alespoň objekt `fpos_t`.)

U souboru otevřeného pro čtení i zápis jsou vstupní i výstupní datové proudy umístěny společně. Chcete-li přepínat mezi vkládáním a extrahováním, je nutné zavolat buď [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) nebo [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Volání `pubseekoff` (a proto `seekoff`) mají různá omezení pro [textové streamy](../c-runtime-library/text-and-binary-streams.md), [binární proudy](../c-runtime-library/text-and-binary-streams.md)a [velké proudy](../c-runtime-library/byte-and-wide-streams.md).

Pokud je ukazatel na soubor `fp` ukazatel s hodnotou null, funkce se nezdařila. Jinak se budoucna na změnu pozice datového proudu voláním `fseek` ( **FP**, `_Off`, `_Way`). Pokud je tato funkce úspěšná a výsledná pozice `fposn` lze určit voláním `fgetpos` ( **FP**, **& fposn**), funkce bude úspěšná. Pokud je funkce úspěšná, vrátí hodnotu typu `pos_type` obsahující `fposn`. V opačném případě vrátí neplatnou pozici streamu.

## <a name="seekpos"></a>basic_filebuf:: seekpos

Pokusí se změnit aktuální pozice pro řízené streamy.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp* \
Pozice pro hledání.

*_Which* \
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Pokud je ukazatel na soubor `fp` ukazatel s hodnotou null, funkce se nezdařila. Jinak se budoucna na změnu pozice datového proudu voláním `fsetpos` ( **FP**, **& fposn**), kde `fposn` je objekt `fpos_t` uložený v `pos`. Pokud je tato funkce úspěšná, funkce vrátí `pos`. V opačném případě vrátí neplatnou pozici streamu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce budoucna změnu aktuální pozice pro řízené streamy. V případě objektu třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **TR**> může být pozice datového proudu reprezentována objektem typu `fpos_t`, který ukládá posun a všechny informace o stavu potřebné k analýze datového proudu v rámci celé řady. Nula odsazení určuje první prvek streamu. (Objekt typu `pos_type` ukládá alespoň `fpos_t` objekt.)

U souboru otevřeného pro čtení i zápis jsou vstupní i výstupní datové proudy umístěny společně. Chcete-li přepínat mezi vkládáním a extrahováním, je nutné zavolat buď [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff) nebo [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos). Volání `pubseekoff` (a proto `seekoff`) mají různá omezení pro textové streamy, binární proudy a velké proudy.

Pro velký proud, pokud k nějakému vložení došlo od otevření datového proudu nebo od posledního volání `streampos`, funkce volá [přetečení](#overflow). Vloží také jakoukoli sekvenci nutnou k obnovení stavu prvotního převodu pomocí `fac` omezující vlastnosti převodu souboru, aby v případě potřeby volala `.unshift` **FAC** . Každý prvek `byte` typu, který **je takto vytvořen** , je zapsán do přidruženého datového proudu, který je označen ukazatelem souboru `fp` jako if po následných voláních formuláře `fputc` ( **Byte**, **FP**). Pokud volání `fac.unshift` nebo jakýkoli zápis selže, funkce není úspěšná.

## <a name="setbuf"></a>basic_filebuf:: setbuf

Provede operaci specifickou pro každou vyrovnávací paměť odvozeného datového proudu.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer* \
Ukazatel na vyrovnávací paměť.

*počet* \
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Chráněná členská funkce vrátí hodnotu nula, pokud ukazatel na soubor `fp` je ukazatel s hodnotou null.

### <a name="remarks"></a>Poznámky

`setbuf` volá `setvbuf` ( **FP**, (`char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **elem**)) pro nabídnutí pole 1 prvků, které začínají v _ *vyrovnávací paměti* jako vyrovnávací paměť pro datový proud. Pokud tato funkce vrací nenulovou hodnotu, funkce vrátí ukazatel s hodnotou null. V opačném případě **ho vrátí k** úspěchu signálu.

## <a name="swap"></a>basic_filebuf:: swap

Vyměňuje obsah tohoto `basic_filebuf` pro obsah poskytnuté `basic_filebuf`.

```cpp
void swap(basic_filebuf& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
@No__t_0 odkaz na jiný `basic_filebuf`.

## <a name="sync"></a>basic_filebuf:: Sync

Pokusí se synchronizovat řízené streamy s případnými přidruženými externími proudy.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu nula, pokud ukazatel na soubor `fp` je ukazatel s hodnotou null. V opačném případě vrátí nulu pouze v případě, že volání do [přetečení](#overflow) i `fflush` ( **FP**) byla úspěšně vyprázdněna do datového proudu.

## <a name="traits_type"></a>basic_filebuf::traits_type

Přidruží název typu k parametru `Tr` šablony.

```cpp
typedef Tr traits_type;
```

## <a name="underflow"></a>basic_filebuf:: subflow

Extrahuje aktuální prvek ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof). V opačném případě vrátí `ch`, převedeno, jak je popsáno v části poznámky.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce budoucna extrakci aktuálního prvku `ch` ze vstupního datového proudu a vrátí prvek jako **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`ch`). Může tak učinit různými způsoby:

- Pokud je k dispozici pozice pro čtení, přebírá `ch` jako prvek uložený na pozici pro čtení a předává další ukazatel pro vstupní vyrovnávací paměť.

- Může číst jeden nebo více elementů typu **char**, jako by v případě následných volání formuláře `fgetc` (**FP**) a převést je na element **ch** typu `Elem` pomocí omezující vlastnosti převodu souboru FAC k volání `fac.in` podle potřeby. Pokud selže čtení nebo převod, funkce se nezdařila.

## <a name="see-also"></a>Viz také:

[\<fstream >](../standard-library/fstream.md) \
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
