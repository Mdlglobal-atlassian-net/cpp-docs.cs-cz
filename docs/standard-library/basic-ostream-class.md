---
title: "basic_ostream – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ostream/std::basic_ostream
- ostream/std::basic_ostream::flush
- ostream/std::basic_ostream::put
- ostream/std::basic_ostream::seekp
- ostream/std::basic_ostream::sentry
- ostream/std::basic_ostream::swap
- ostream/std::basic_ostream::tellp
- ostream/std::basic_ostream::write
dev_langs: C++
helpviewer_keywords:
- std::basic_ostream [C++]
- std::basic_ostream [C++], flush
- std::basic_ostream [C++], put
- std::basic_ostream [C++], seekp
- std::basic_ostream [C++], sentry
- std::basic_ostream [C++], swap
- std::basic_ostream [C++], tellp
- std::basic_ostream [C++], write
ms.assetid: 5baadc65-b662-4fab-8c9f-94457c58cda1
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d08410c68a2cff5a1c85733c4a2a2ed1775754b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="basicostream-class"></a>basic_ostream – třída
Tato třída šablony popisuje objekt, který řídí vložení elementů a kódovaného objekty do vyrovnávací paměti datového proudu elementy typu **Elem**, také známé jako [char_type –](../standard-library/basic-ios-class.md#char_type), jehož vlastnosti znak jsou Určuje třídu **Tr**, také známé jako [traits_type –](../standard-library/basic-ios-class.md#traits_type).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_ostream : virtual public basic_ios<Elem, Tr>  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 A `char_type`.  
  
 `Tr`  
 Znak `traits_type`.  
  
## <a name="remarks"></a>Poznámky  
 Většina člena funkce této přetížení [operátor <<](#op_lt_lt) jsou funkce formátovaný výstup. Budou vyhovovat vzoru:  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (ok)  
 {try  
 {<convert and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
width(0);
// Except for operator<<(Elem)  
setstate(state);

return (*this);
```  
  
 Dva další členské funkce jsou funkce neformátovaný výstup. Budou vyhovovat vzoru:  
  
```  
iostate state = goodbit;  
const sentry ok(*this);

if (!ok)  
    state |= badbit;  
else  
 {try  
 {<obtain and insert elements  
    accumulate flags in state> }  
    catch (...)  
 {try  
 {setstate(badbit);

}  
    catch (...)  
 {}  
    if ((exceptions()& badbit) != 0)  
    throw; }}  
setstate(state);

return (*this);
```  
  
 Obě skupiny volání funkce [setstate –](../standard-library/basic-ios-class.md#setstate)**(badbit)** pokud jejich dojde k chybě při vkládání elementy.  
  
 Objekt basic_istream – třída\< **Elem**, **Tr**> ukládá pouze virtuální veřejné základní objekt třídy [basic_ios](../standard-library/basic-ios-class.md)  **\<Elem**, **Tr >**.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [basic_ofstream – třída](../standard-library/basic-ofstream-class.md) Další informace o výstupní datové proudy.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_ostream –](#basic_ostream)|Vytvoří `basic_ostream` objektu.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[vyprázdnění](#flush)|Vyprázdní vyrovnávací paměť.|  
|[PUT](#put)|Vloží znak v datovém proudu.|  
|[seekp –](#seekp)|Resetování pozice v výstupního datového proudu.|  
|[SENTRY](#sentry)|Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný výstup funkce a funkce neformátovaný výstup.|  
|[swap](#op_eq)|Výměny hodnoty tohoto `basic_ostream` objekt pro ty poskytnutého `basic_ostream` objektu.|  
|[tellp –](#tellp)|Umístění sestavy ve výstupní datový proud.|  
|[write](#write)|Převádí znaky v datovém proudu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#basic_ostream_operator_eq)|Přiřadí hodnota poskytnutého `basic_ostream` objektu parametr k tomuto objektu.|  
|[operátor <<](#basic_ostream_operator_lt_lt)|Zapíše do datového proudu.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<ostream – >  
  
 **Namespace:** – std  
  
##  <a name="basic_ostream"></a>basic_ostream::basic_ostream  
 Vytvoří `basic_ostream` objektu.  
  
```  
explicit basic_ostream(
    basic_streambuf<Elem, Tr>* strbuf,  
    bool _Isstd = false);

basic_ostream(basic_ostream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `strbuf`  
 Objekt typu [basic_streambuf](../standard-library/basic-streambuf-class.md).  
  
 `_Isstd`  
 `true`Pokud se jedná o standardní datový proud; v opačném `false`.  
  
 `right`  
 Rvalue odkaz na objekt typu `basic_ostream`.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje základní třídu voláním [init](../standard-library/basic-ios-class.md#init)(`strbuf`). Druhý konstruktor inicializuje základní třídu voláním [basic_ios::move](../standard-library/basic-ios-class.md#move)`(right)`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) Další informace o výstupní datové proudy.  
  
##  <a name="flush"></a>basic_ostream::Flush  
 Vyprázdní vyrovnávací paměť.  
  
```  
basic_ostream<Elem, Tr>& flush();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt basic_ostream.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [rdbuf –](../standard-library/basic-ios-class.md#rdbuf) není ukazatele null volání funkce **-> rdbuf –**[pubsync –](../standard-library/basic-streambuf-class.md#pubsync). Pokud, vrátí hodnotu -1, zavolá funkci [setstate –](../standard-library/basic-ios-class.md#setstate)(**badbit**). Vrátí  **\*to**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_ostream_flush.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << "test";  
   cout.flush();  
}  
```  
  
```Output  
test  
```  
  
##  <a name="basic_ostream_operator_lt_lt"></a>basic_ostream::Operator&lt;&lt;  
 Zapíše do datového proudu.  
  
```  
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& (* Pfn)(basic_ostream<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(
    ios_base& (* Pfn)(ios_base&));

basic_ostream<Elem, Tr>& operator<<(
    basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));

basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
basic_ostream<Elem, Tr>& operator<<(bool val);
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int __w64  val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long __w64  val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
### <a name="parameters"></a>Parametry  
 `Pfn`  
 Ukazatel na funkci.  
  
 `strbuf`  
 Ukazatel **stream_buf** objektu.  
  
 `val`  
 Element k zápisu do datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt basic_ostream.  
  
### <a name="remarks"></a>Poznámky  
 `<ostream>` Záhlaví také definuje několik operátorů globální vložení. Další informace najdete v tématu [operátor <<](../standard-library/ostream-operators.md#op_lt_lt).  
  
 První člen funkce zajišťuje, že výrazu ve formátu **ostr << endl** volání [endl](../standard-library/ostream-functions.md#endl)**(ostr)**a vrátí  **\*to** . Druhý a třetí funkce, jako zajistěte, aby další manipulátory [šestnáctkových](../standard-library/ios-functions.md#hex), chovají podobně. Zbývající funkce jsou všechny funkce formátovaný výstup.  
  
 Funkce  
  
```  
basic_ostream<Elem, Tr>& operator<<(basic_streambuf<Elem, Tr>* strbuf);
```  
  
 Extrahuje prvky z `strbuf`, pokud `strbuf` není nulový ukazatel a vloží je. Extrakce zastaví na konci souboru, nebo pokud extrakci vyvolá výjimku, (což je znovu vyvolány). Zastaví také, bez extrahování dotyčná, pokud selže vložení. Pokud funkce vloží žádné elementy, nebo pokud extrakci vyvolá výjimku, zavolá funkci [setstate –](../standard-library/basic-ios-class.md#setstate)(**failbit**). V každém případě funkce vrátí hodnotu  **\*to**.  
  
 Funkce  
  
```  
basic_ostream<Elem, Tr>& operator<<(bool val);
```  
  
 Převede `_Val` na booleovskou hodnotu pole a vloží ho voláním [use_facet](../standard-library/basic-filebuf-class.md#open)**< num_put\<Elem, OutIt >**`(`[getloc –](../standard-library/ios-base-class.md#getloc)). [uveďte](#put)(**OutIt**([rdbuf –](../standard-library/basic-ios-class.md#rdbuf)),  **\*to**, `getloc`, **val**). Zde **OutIt** je definován jako [ostreambuf_iterator](../standard-library/ostreambuf-iterator-class.md)**\<Elem, Tr >**. Funkce vrátí hodnotu  **\*to**.  
  
 Funkce  
  
```  
basic_ostream<Elem, Tr>& operator<<(short val);
basic_ostream<Elem, Tr>& operator<<(unsigned short val);
basic_ostream<Elem, Tr>& operator<<(int val);
basic_ostream<Elem, Tr>& operator<<(unsigned int __w64  val);
basic_ostream<Elem, Tr>& operator<<(long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long val);
basic_ostream<Elem, Tr>& operator<<(long long val);
basic_ostream<Elem, Tr>& operator<<(unsigned long long val);
basic_ostream<Elem, Tr>& operator<<(const void* val);
```  
  
 Každý převést `val` číselného pole a jejím vložením voláním **use_facet < num_put\<Elem, OutIt >**(`getloc`). **uveďte**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). Zde **OutIt** je definován jako **ostreambuf_iterator\<Elem, Tr >**. Funkce vrátí hodnotu  **\*to**.  
  
 Funkce  
  
```  
basic_ostream<Elem, Tr>& operator<<(float val);
basic_ostream<Elem, Tr>& operator<<(double val);
basic_ostream<Elem, Tr>& operator<<(long double val);
```  
  
 Každý převést `val` číselného pole a jejím vložením voláním **use_facet < num_put\<Elem, OutIt >**(`getloc`)**. put**(**OutIt**(`rdbuf`),  **\*to**, `getloc`, **val**). Zde **OutIt** je definován jako **ostreambuf_iterator\<Elem, Tr >**. Funkce vrátí hodnotu  **\*to**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_ostream_op_write.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
ios_base& hex2( ios_base& ib )  
{  
   ib.unsetf( ios_base::dec );  
   ib.setf( ios_base::hex );  
   return ib;  
}  
  
basic_ostream<char, char_traits<char> >& somefunc(basic_ostream<char, char_traits<char> > &i)
{
    if (i == cout)
    {
        i << "i is cout" << endl;
    }
    return i;
}

class CTxtStreambuf : public basic_streambuf< char, char_traits< char > >
{
public:
    CTxtStreambuf(char *_pszText)
    {
        pszText = _pszText;
        setg(pszText, pszText, pszText + strlen(pszText));
    };
    char *pszText;
};

int main()
{
    cout << somefunc;
    cout << 21 << endl;

    hex2(cout);
    cout << 21 << endl;

    CTxtStreambuf f("text in streambuf");
    cout << &f << endl;
}
```  
  
##  <a name="op_eq"></a>basic_ostream::Operator =  
 Přiřadí hodnoty pro poskytnutého `basic_ostream` objektu parametr k tomuto objektu.  
  
```  
basic_ostream& operator=(basic_ostream&& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 `rvalue` Odkaz na `basic_ostream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Operátor členů volá swap `(right)`.  
  
##  <a name="put"></a>basic_ostream::Put  
 Vloží znak v datovém proudu.  
  
```  
basic_ostream<Elem, Tr>& put(char_type _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt basic_ostream.  
  
### <a name="remarks"></a>Poznámky  
 Neformátovaný tvar výstup funkce vloží element `_Ch`. Vrátí  **\*to**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_ostream_put.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout.put( 'v' );  
   cout << endl;  
   wcout.put( L'l' );  
}  
```  
  
```Output  
v  
l  
```  
  
##  <a name="seekp"></a>basic_ostream::seekp  
 Resetovat pozice v výstupního datového proudu.  
  
```  
basic_ostream<Elem, Tr>& seekp(pos_type _Pos);

basic_ostream<Elem, Tr>& seekp(off_type _Off, ios_base::seekdir _Way);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pos`  
 Pozice v datovém proudu.  
  
 `_Off`  
 Posun vzhledem k `_Way`.  
  
 `_Way`  
 Jeden z [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) výčty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt basic_ostream.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [nezdaří](../standard-library/basic-ios-class.md#fail) je **false**, první volání funkce člen **newpos =** [rdbuf –](../standard-library/basic-ios-class.md#rdbuf)  **->**  [pubseekpos –](../standard-library/basic-streambuf-class.md#pubseekpos)(*_Pos*), pro některé `pos_type` dočasný objekt **newpos**. Pokud **nezdaří** je nastavena hodnota false, druhé volání funkce **newpos = rdbuf – - >** [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff)(*_Off _Way*). V obou případech Pokud (`off_type`)**newpos ==** (`off_type`)(-1) (umísťovací operace selže), pak funkce volá **istr.** [setstate –](../standard-library/basic-ios-class.md#setstate)(**failbit**). Obě funkce vrátí  **\*to**.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_ostream_seekp.cpp  
// compile with: /EHsc  
#include <fstream>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    ofstream x("basic_ostream_seekp.txt");  
    streamoff i = x.tellp();  
    cout << i << endl;  
    x << "testing";  
    i = x.tellp();  
    cout << i << endl;  
    x.seekp(2);   // Put char in third char position in file  
    x << " ";  
  
    x.seekp(2, ios::end);   // Put char two after end of file  
    x << "z";  
}  
```  
  
```Output  
0  
7  
```  
  
##  <a name="sentry"></a>basic_ostream::SENTRY  
 Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný výstup funkce a funkce neformátovaný výstup.  
  
{sentry – třída  
   veřejná:  
   explicitní sentry (basic_ostream\<Elem, Tr > & _Ostr); operátor bool() const; ~ sentry();};  
  
### <a name="remarks"></a>Poznámky  
 Vnořené třídy popisuje objekt, jehož deklarace struktur formátovaný výstup funkce a funkce neformátovaný výstup. Pokud **ostr.** [dobrý](../standard-library/basic-ios-class.md#good) je **true** a **ostr.** [tie](../standard-library/basic-ios-class.md#tie) není ukazatele null volá konstruktor **-> ostr.tie**[vyprázdnění](#flush). Konstruktor pak uloží hodnoty vrácené **ostr.good** v **stav**. Novější volání **operátor bool** přináší tato uložené hodnoty.  
  
 Pokud `uncaught_exception` vrátí **false** a [příznaky](../standard-library/ios-base-class.md#flags)  **&**  [unitbuf](../standard-library/ios-functions.md#unitbuf) nenulový, volání destruktoru [vyprázdnění](#flush).  
  
##  <a name="swap"></a>basic_ostream::swap  
 Výměny hodnoty tohoto `basic_ostream` objekt pro hodnoty poskytnutého `basic_ostream`.  
  
```  
void swap(basic_ostream& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odkaz na `basic_ostream` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [basic_ios::swap](../standard-library/basic-ios-class.md#swap) `(right)` k výměně obsahu tohoto objektu pro obsah `right`.  
  
##  <a name="tellp"></a>basic_ostream::tellp  
 Umístění sestavy ve výstupní datový proud.  
  
```  
pos_type tellp();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice v výstupního datového proudu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [nezdaří](../standard-library/basic-ios-class.md#fail) je **false**, vrátí funkce člena [rdbuf –](../standard-library/basic-ios-class.md#rdbuf)  **->**  [pubseekoff –](../standard-library/basic-streambuf-class.md#pubseekoff) (0, `cur`, **v**). Funkce `pos_type`(-1).  
  
### <a name="example"></a>Příklad  
  V tématu [seekp –](#seekp) pro příklad použití `tellp`.  
  
##  <a name="write"></a>basic_ostream::Write  
 Uveďte znaků v datovém proudu.  
  
```  
basic_ostream<Elem, Tr>& write(const char_type* str, streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Počet znaků k uvedení do datového proudu.  
  
 `str`  
 Znaky se umístí do datového proudu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na objekt basic_ostream.  
  
### <a name="remarks"></a>Poznámky  
 [Neformátovaný výstup funkce](../standard-library/basic-ostream-class.md) vloží pořadí `count` elementy začínající na `str`.  
  
### <a name="example"></a>Příklad  
  V tématu [streamsize](../standard-library/ios-typedefs.md#streamsize) pro příklad použití `write`.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)

