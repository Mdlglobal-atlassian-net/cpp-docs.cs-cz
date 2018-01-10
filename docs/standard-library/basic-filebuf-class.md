---
title: "basic_filebuf – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c5ec1881695c80c8f493ac2a2848d0349f430aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="basicfilebuf-class"></a>basic_filebuf – třída
Popisuje datový proud vyrovnávací paměť, která řídí přenos elementy typu `Elem`, jehož vlastnosti znak určuje třídu `Tr`, do a z pořadí prvků, které jsou uložené v souboru externích.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_filebuf : public basic_streambuf<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 Základní prvek vyrovnávací paměti souboru.  
  
 `Tr`  
 Vlastnosti základní elementu vyrovnávací paměti souboru (obvykle `char_traits` <  `Elem`>).  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje datový proud vyrovnávací paměť, která řídí přenos elementy typu `Elem`, jehož vlastnosti znak určuje třídu `Tr`, do a z pořadí prvků, které jsou uložené v souboru externích.  
  
> [!NOTE]
>  Objekty typu `basic_filebuf` jsou vytvořeny pomocí vnitřní vyrovnávací paměť typu `char *` bez ohledu na to `char_type` určeného parametr typu `Elem`. To znamená, že řetězec znaků Unicode (obsahující `wchar_t` znaků) se převede na řetězec ANSI (obsahující `char` znaků) před zápisem na vnitřní vyrovnávací paměť. K ukládání ve vyrovnávací paměti řetězců v kódu Unicode, vytvořit vyrovnávací paměť nového typu `wchar_t` a nastavte ji pomocí [basic_streambuf::pubsetbuf](../standard-library/basic-streambuf-class.md#pubsetbuf) `()` metoda. Pokud chcete zobrazit příklad, který ukazuje, toto chování, najdete níže.  
  
 Třída objektu `basic_filebuf` <  `Elem`, `Tr`> ukládá ukazatele souboru, který vytváří `FILE` objekt, který řídí datový proud přidružený otevření souboru. Ukládá také ukazatele na dva převod omezující vlastnosti souboru pro použití ve chráněném členské funkce [přetečení](#overflow) a [podtečení](#underflow). Další informace najdete v tématu [basic_filebuf::open](#open).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vynutit objekt typu `basic_filebuf<wchar_t>` k uložení znaky kódování Unicode v jeho vnitřní vyrovnávací paměť voláním `pubsetbuf()` metoda.  
  
```  
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
  
|||  
|-|-|  
|[basic_filebuf –](#basic_filebuf)|Vytvoří objekt typu `basic_filebuf`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type –](#char_type)|Přidruží název typu s `Elem` parametr šablony.|  
|[int_type –](#int_type)|Umožňuje v rámci tohoto typu `basic_filebuf`je ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|  
|[off_type –](#off_type)|Umožňuje v rámci tohoto typu `basic_filebuf`je ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|  
|[pos_type –](#pos_type)|Umožňuje v rámci tohoto typu `basic_filebuf`je ekvivalentem typu se stejným názvem v oboru `Tr` oboru.|  
|[traits_type –](#traits_type)|Přidruží název typu s `Tr` parametr šablony.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[close](#close)|Zavře soubor.|  
|[is_open –](#is_open)|Určuje, zda je soubor otevřít.|  
|[open](#open)|Otevře soubor.|  
|[přetečení](#overflow)|Chráněné virtuální funkce, která lze volat, když nové znak je vložen do plné vyrovnávací paměti.|  
|[pbackfail –](#pbackfail)|Chráněný člen virtuální funkce pokusí vrátit zpět element do vstupního datového proudu, ujistěte se, jeho aktuálního elementu (ukazuje další ukazatel).|  
|[seekoff –](#seekoff)|Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|  
|[seekpos –](#seekpos)|Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|  
|[setbuf](#setbuf)|Chráněný člen virtuální funkce provádí konkrétní operace do vyrovnávací paměti jednotlivých odvozené datového proudu.|  
|[Swap](#swap)|Obsah této výměny `basic_filebuf` pro obsah ze zadaných `basic_filebuf` parametr.|  
|[synchronizace](#sync)|Chráněné, virtuální funkce se pokusí synchronizovat řízené datové proudy s všechny přidružené externí datové proudy.|  
|[uflow –](../standard-library/basic-streambuf-class.md#uflow)|Chráněný, virtuální funkce k extrakci aktuálního elementu ze vstupního datového proudu.|  
|[podtečení](#underflow)|Chráněný, virtuální funkce k extrakci aktuálního elementu ze vstupního datového proudu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<fstream >  
  
 **Namespace:** – std  
  
##  <a name="basic_filebuf"></a>basic_filebuf::basic_filebuf  
 Vytvoří objekt typu `basic_filebuf`.  
  
```  
basic_filebuf();

basic_filebuf(basic_filebuf&& right);
```  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor ukládá ukazatele null v následující ukazatele řízení vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Také ukládá ukazatele null v ukazatele souboru.  
  
 Druhý konstruktor inicializuje objekt s obsahem `right`, považován za deklarátor odkazu.  
  
##  <a name="char_type"></a>basic_filebuf::char_type  
 Přidruží název typu s **Elem** parametr šablony.  
  
```  
typedef Elem char_type;  
```  
  
##  <a name="close"></a>basic_filebuf::Close  
 Zavře soubor.  
  
```  
basic_filebuf<Elem, Tr> *close();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Členská funkce vrátí ukazatel s hodnotou null, pokud je ukazatel souboru ukazatele null.  
  
### <a name="remarks"></a>Poznámky  
 **Zavřete** volání `fclose`( **fp**). Pokud tento funkce vrátí nenulovou hodnotu, funkce vrátí hodnotu ukazatele null. Funkce **to** indikující, že soubor byl úspěšně zavřel.  
  
 Pro celou datového proudu, pokud žádné vložení došlo od datový proud byl otevřen nebo od posledního volání `streampos`, volání funkce [přetečení](#overflow). Také vloží všechny pořadí potřebné k obnovení stavu počáteční převod pomocí omezující vlastnost převod souborů **fac** volat **fac.unshift** podle potřeby. Každý prvek **bajtů** typu `char` proto vytvořeného je zapsán do související datový proud určený hodnotou ukazatele souboru **fp** jako Pokud podle následných voláních formuláře `fputc`( **bajtů**, **fp**). Pokud volání **fac.unshift** nebo žádné zápisu selže, funkce neproběhne úspěšně.  
  
### <a name="example"></a>Příklad  
  Následující příklad předpokládá dva soubory v aktuálním adresáři: basic_filebuf_close.txt (obsah je "testování") a iotest.txt (obsah je "ssss").  
  
```  
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
  
##  <a name="int_type"></a>basic_filebuf::int_type  
 Umožňuje tento typ v rámci oboru basic_filebuf je ekvivalentem typu se stejným názvem v **Tr** oboru.  
  
```  
typedef typename traits_type::int_type int_type;  
```  
  
##  <a name="is_open"></a>basic_filebuf::is_open  
 Určuje, zda je soubor otevřít.  
  
```  
bool is_open() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud ukazatele souboru není nulový ukazatel.  
  
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
  
##  <a name="off_type"></a>basic_filebuf::off_type  
 Umožňuje tento typ v rámci oboru basic_filebuf je ekvivalentem typu se stejným názvem v **Tr** oboru.  
  
```  
typedef typename traits_type::off_type off_type;  
```  
  
##  <a name="open"></a>basic_filebuf::Open  
 Otevře soubor.  
  
```  
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
 `_Filename`  
 Název souboru, který se otevřít.  
  
 `_Mode`  
 Jeden z výčtů ve [ios_base::openmode](../standard-library/ios-base-class.md#openmode).  
  
 `_Prot`  
 Výchozí soubor otevírání ochrany, odpovídá `shflag` parametr v [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud je ukazatel souboru ukazatele null, funkce vrátí hodnotu ukazatele null. Funkce **to**.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce otevře soubor s názvem souboru *filename*, voláním [fopen –](../c-runtime-library/reference/fopen-wfopen.md)( *filename*, **strmode**). **strmode** se určí na základě **režimu &**~ ( [uje](../standard-library/ios-base-class.md#openmode) & &#124; [binární](../standard-library/ios-base-class.md#openmode)):  
  
- **ios_base::in** stane **"r"** (otevřít existující soubor pro čtení).  
  
- [ios_base::Out](../standard-library/ios-base-class.md#fmtflags) nebo **ios_base::out &#124; ios_base::trunc** stane **"w"** (zkrátit existující soubor nebo vytvořit pro zápis).  
  
- **ios_base::Out &#124; aplikace** stane **"a"** (otevřít existující soubor pro připojování všech zápisů).  
  
- **ios_base::in &#124; ios_base::Out** stane **"r +"** (otevřít existující soubor pro čtení a zápis).  
  
- **ios_base::in &#124; ios_base::Out &#124; ios_base::TRUNC** stane **"w +"** (zkrátit existující soubor nebo vytvořit pro čtení a zápis).  
  
- **ios_base::in &#124; ios_base::Out &#124; ios_base::App** stane **"+"** (otevřít existující soubor pro čtení a pro připojování všech zápisů).  
  
 Pokud **režimu & ios_base::binary** je nenulové hodnoty, připojí funkce **b** k **strmode** otevřete binární datový proud místo textu datového proudu. Poté uloží hodnoty vrácené `fopen` v ukazatele souboru **fp**. Pokud **režimu & ios_base::ate** nenulový a ukazatele souboru není ukazatele null volání funkce `fseek`( **fp**, 0, `SEEK_END`) na pozici datový proud na konci souboru. Pokud tento umísťovací operace selže, volání funkce [zavřete](#close)( **fp**) a ukládá ukazatele null v ukazatele souboru.  
  
 Pokud ukazatele souboru není ukazatele null, funkce určuje omezující vlastnost převod souborů: `use_facet` <  `codecvt` <  **Elem**, `char`, **traits_type –::** [ state_type –](../standard-library/char-traits-struct.md#state_type)>> ( [getloc –](../standard-library/basic-streambuf-class.md#getloc)), za účelem použití [podtečení](#underflow) a [přetečení](#overflow).  
  
 Pokud je ukazatel souboru ukazatele null, funkce vrátí hodnotu ukazatele null. Funkce **to**.  
  
### <a name="example"></a>Příklad  
  V tématu [basic_filebuf::close](#close) pro příklad, který používá **otevřete**.  
  
##  <a name="op_eq"></a>basic_filebuf::Operator =  
 Přiřazení obsahu tohoto objektu vyrovnávací paměti datového proudu. Toto je přiřazení přesunutí zahrnující rvalue kopii nenechává za sebou.  
  
```  
basic_filebuf& operator=(basic_filebuf&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Rvalue odkaz na [basic_filebuf](../standard-library/basic-filebuf-class.md) objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí * to.  
  
### <a name="remarks"></a>Poznámky  
 Operátor členů nahradí obsah objektu s použitím obsah `right`, považován za deklarátor odkazu. Další informace najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
##  <a name="overflow"></a>basic_filebuf::Overflow  
 Volá se při nové znak je vložen do plné vyrovnávací paměti.  
  
```  
virtual int_type overflow(int_type _Meta = traits_type::eof);
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak, který má vložit do vyrovnávací paměti nebo **traits_type::eof**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof**. Funkce **traits_type –::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).  
  
### <a name="remarks"></a>Poznámky  
 Pokud _ *Meta***! = traits_type –::**[eof](../standard-library/char-traits-struct.md#eof), chráněného člena virtuální funkce endeavors vložení prvku **ch = traits_type –::** [ to_char_type –](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) do výstupní vyrovnávací paměť. Můžete tak učinit různými způsoby:  
  
-   Pokud pozice zápisu je k dispozici, může uložit prvek na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.  
  
-   K dispozici na pozici zápisu mohl zajistit přidělí nové nebo další úložiště pro výstupní vyrovnávací paměť.  
  
-   Může převést všechny čekající výstupu v výstupní vyrovnávací paměť, za nímž následuje **ch**, pomocí omezující vlastnost převod souborů **fac** volat **fac.out** podle potřeby. Každý prvek `ch` typu *char* proto vytvořeného je zapsán do související datový proud určený hodnotou ukazatele souboru **fp** jako Pokud podle následných voláních formuláře `fputc`( **ch**, **fp**). Pokud žádné převod nebo zápis selže, funkce úspěšné.  
  
##  <a name="pbackfail"></a>basic_filebuf::pbackfail  
 Pokusí se vrátit zpět element do vstupního datového proudu, ujistěte se, jeho aktuálního elementu (ukazuje další ukazatel).  
  
```  
virtual int_type pbackfail(int_type _Meta = traits_type::eof);
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak, který má vložit do vyrovnávací paměti, nebo **traits_type::eof**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof**. Funkce **traits_type –::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce element vrátí zpět do vstupní vyrovnávací paměť a pak jej aktuálního elementu (ukazuje další ukazatel). Pokud _ *Meta* **== traits_type –::**[eof](../standard-library/char-traits-struct.md#eof), element tak, aby nabízel zpět je efektivně už v datovém proudu před aktuálního elementu. Jinak je nahrazena daný element **ch = traits_type –::**[to_char_type –](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Funkce může vrátit zpět element různými způsoby:  
  
-   Pokud je k dispozici na pozici putback – a element v ní uloženy porovná rovna **ch**, ho můžete snížení další ukazatele pro vstupní vyrovnávací paměť.  
  
-   Pokud je funkce mohou provádět `putback` pozici k dispozici, můžete tak učinit, nastavte na další ukazatel na pozice a ukládání **ch** v této poloze.  
  
-   Pokud funkce můžete umístěn zpět element vstupního datového proudu, ho můžete to udělat, například voláním `ungetc` pro element typu `char`.  
  
##  <a name="pos_type"></a>basic_filebuf::pos_type  
 Umožňuje tento typ v rámci oboru basic_filebuf je ekvivalentem typu se stejným názvem v **Tr** oboru.  
  
```  
typedef typename traits_type::pos_type pos_type;  
```  
  
##  <a name="seekoff"></a>basic_filebuf::seekoff  
 Se pokusí změnit aktuální pozice pro řízené datové proudy.  
  
```  
virtual pos_type seekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Pozice k vyhledání pro vzhledem k `_Way`.  
  
 `_Way`  
 Výchozí bod pro posunutí operace. V tématu [seekdir –](../standard-library/ios-base-class.md#seekdir) pro možné hodnoty.  
  
 `_Which`  
 Určuje režim pro umístění ukazatele. Ve výchozím nastavení se vám umožní změnit čtení a zápis pozic.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nový pozici nebo pozice neplatný datový proud.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce endeavors ke změně aktuální pozice pro řízené datové proudy. Pro objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`>, pozice datového proudu může být reprezentovaný objektem typu `fpos_t`, která ukládá posun a musel žádné informace o stavu analyzovat širokou datového proudu. Posunutí nula označí první prvek datového proudu. (Objekt typu [pos_type –](../standard-library/basic-streambuf-class.md#pos_type) ukládá alespoň k `fpos_t` objektu.)  
  
 Pro soubor otevřít pro čtení a zápis jsou obě vstupní a výstupní datové proudy umístěný v kombinaci. Přepínat mezi vkládání a extrahování, musí volat buď [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff) nebo [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos). Volání `pubseekoff` (a tím i k `seekoff`) mají různé omezení pro [textové datové proudy](../c-runtime-library/text-and-binary-streams.md), [binární proudy](../c-runtime-library/text-and-binary-streams.md), a [široké proudy](../c-runtime-library/byte-and-wide-streams.md).  
  
 Pokud ukazatele souboru **fp** je ukazatel s hodnotou null, funkce selže. Jinak ji endeavors ke změně pozice datového proudu voláním `fseek`( **fp**, `_Off`, `_Way`). Pokud se podaří této funkce a výsledný pozice **fposn** voláním se dá určit `fgetpos`( **fp**, **& fposn**), funkce úspěšné. Pokud funkci úspěšné, vrátí hodnotu typu **pos_type –** obsahující **fposn**. Jinak vrátí pozici neplatný datový proud.  
  
##  <a name="seekpos"></a>basic_filebuf::seekpos  
 Se pokusí změnit aktuální pozice pro řízené datové proudy.  
  
```  
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Sp`  
 Pozice k vyhledání pro.  
  
 `_Which`  
 Určuje režim pro umístění ukazatele. Ve výchozím nastavení se vám umožní změnit čtení a zápis pozic.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud ukazatele souboru **fp** je ukazatel s hodnotou null, funkce selže. Jinak ji endeavors ke změně pozice datového proudu voláním `fsetpos`( **fp**, **& fposn**), kde **fposn** je `fpos_t` objektu uloženého ve `pos`. Pokud bude úspěšné této funkce, funkce vrátí hodnotu `pos`. Jinak vrátí pozici neplatný datový proud. Pokud chcete zjistit, pokud pozice datový proud je neplatný, porovnat návratovou hodnotu s `pos_type(off_type(-1))`.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce endeavors ke změně aktuální pozice pro řízené datové proudy. Pro objekt třídy [basic_filebuf](../standard-library/basic-filebuf-class.md) \< **Elem**, **Tr**>, pozice datového proudu může být reprezentovaný objektem typu `fpos_t`, která ukládá Posun a žádné informace o stavu, který je potřeba analyzovat širokou datového proudu. Posunutí nula označí první prvek datového proudu. (Objekt typu `pos_type` ukládá alespoň k `fpos_t` objektu.)  
  
 Pro soubor otevřít pro čtení a zápis jsou obě vstupní a výstupní datové proudy umístěný v kombinaci. Přepínat mezi vkládání a extrahování, musí volat buď [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff) nebo [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos). Volání `pubseekoff` (a tím i k `seekoff`) mají různé omezení pro textové datové proudy, binární datové proudy a široké proudy.  
  
 Pro celou datového proudu, pokud žádné vložení došlo od datový proud byl otevřen nebo od posledního volání `streampos`, volání funkce [přetečení](#overflow). Také vloží všechny pořadí potřebné k obnovení stavu počáteční převod pomocí omezující vlastnost převod souborů **fac** volat **fac** `.unshift` podle potřeby. Každý prvek **bajtů** typu `char` proto vytvořeného je zapsán do související datový proud určený hodnotou ukazatele souboru **fp** jako Pokud podle následných voláních formuláře `fputc`( **bajtů**, **fp**). Pokud volání **fac.unshift** nebo žádné zápisu selže, funkce neproběhne úspěšně.  
  
##  <a name="setbuf"></a>basic_filebuf::setbuf  
 Provede konkrétní operace do vyrovnávací paměti jednotlivých odvozené datového proudu.  
  
```  
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `_Buffer`  
 Ukazatel na vyrovnávací paměti.  
  
 `count`  
 Velikost vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Chráněný člen funkce vrátí hodnotu nula v případě ukazatele souboru `fp` je ukazatel s hodnotou null.  
  
### <a name="remarks"></a>Poznámky  
 `setbuf`volání `setvbuf`( **fp**, ( `char` \*) `_Buffer`, `_IOFBF`, `count` \* `sizeof` ( **Elem**)) a nabídnout pole `count` elementy začínající na _ *vyrovnávací paměti* jako vyrovnávací paměť pro datový proud. Pokud tento funkce vrátí nenulovou hodnotu, funkce vrátí hodnotu ukazatele null. Funkce **to** na úspěšné provedení signál.  
  
##  <a name="swap"></a>basic_filebuf::swap  
 Obsah tohoto výměny `basic_filebuf` pro obsah ze zadaných `basic_filebuf`.  
  
```  
void swap(basic_filebuf& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `lvalue` Odkaz na jiný `basic_filebuf`.  
  
##  <a name="sync"></a>basic_filebuf::Sync  
 Pokusí se synchronizovat řízené datové proudy s všechny přidružené externí datové proudy.  
  
```  
virtual int sync();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí nula v případě ukazatele souboru **fp** je ukazatel s hodnotou null. Funkce nula pouze v případě volá na obojí [přetečení](#overflow) a `fflush`( **fp**) nepodaří vyprázdnění žádný výstup čekající na datový proud.  
  
##  <a name="traits_type"></a>basic_filebuf::traits_type  
 Přidruží název typu s **Tr** parametr šablony.  
  
```  
typedef Tr traits_type;  
```  
  
##  <a name="underflow"></a>basic_filebuf::underflow  
 Extrahuje aktuálního elementu ze vstupního datového proudu.  
  
```  
virtual int_type underflow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof). Funkce **ch**, převedený, jak je popsáno v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce endeavors k extrakci aktuálního elementu **ch** ze vstupu stream a vrátí prvek jako **traits_type –::**[to_int_type –](../standard-library/char-traits-struct.md#to_int_type)() **ch**). Můžete tak učinit různými způsoby:  
  
-   Pokud je k dispozici pro čtení pozice, trvá **ch** jako element uložené ve čtení pozici a přejde na další ukazatele pro vstupní vyrovnávací paměť.  
  
-   Může zobrazit jeden či více elementů typu `char`, jako kdyby podle následných voláních formuláře `fgetc`(**fp**) a je převést na element **ch** typu **Elem**pomocí fac omezující vlastnost převod souborů k vyvolání **fac.in** podle potřeby. Pokud se všechny pro čtení nebo převod nezdaří, funkce úspěšné.  
  
## <a name="see-also"></a>Viz také  
 [\<fstream >](../standard-library/fstream.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)

