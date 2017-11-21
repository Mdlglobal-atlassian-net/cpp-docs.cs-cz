---
title: "strstreambuf – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- strstream/std::strstreambuf::freeze
- strstream/std::strstreambuf::overflow
- strstream/std::strstreambuf::pbackfail
- strstream/std::strstreambuf::pcount
- strstream/std::strstreambuf::seekoff
- strstream/std::strstreambuf::seekpos
- strstream/std::strstreambuf::str
- strstream/std::strstreambuf::underflow
dev_langs: C++
helpviewer_keywords:
- std::strstreambuf [C++], freeze
- std::strstreambuf [C++], overflow
- std::strstreambuf [C++], pbackfail
- std::strstreambuf [C++], pcount
- std::strstreambuf [C++], seekoff
- std::strstreambuf [C++], seekpos
- std::strstreambuf [C++], str
- std::strstreambuf [C++], underflow
ms.assetid: b040b8ea-0669-4eba-8908-6a9cc159c54b
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c7515ba8f90cfc60cce84f8bd5c59fba6d3dc1d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strstreambuf-class"></a>strstreambuf – třída
Popisuje datový proud vyrovnávací paměť, která řídí přenos elementů do a z pořadí prvků, které jsou uložené v `char` objekt array.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class strstreambuf : public streambuf  
```  
  
## <a name="remarks"></a>Poznámky  
 V závislosti na tom, jak je objekt vytvořený může být přidělen, rozšířené a vydání podle potřeby pro přizpůsobení změny v pořadí.  
  
 Třída objektu `strstreambuf` ukládá několik bity informace o režimu jako jeho `strstreambuf` režimu. Tyto služby bits znamenat zda řízené sekvenci:  
  
-   Byl přidělen a musí být uvolněno nakonec.  
  
-   Lze upravovat.  
  
-   Je možné rozšířit změna přidělování úložiště.  
  
-   Má byly pozastaveny a proto musí být subjektem než objekt nefixované před objekt zničený, nebo vydání (Pokud přidělené).  
  
 Řízené sekvenci, který nereaguje nelze změnit ani rozšířené, bez ohledu na stav tyto samostatné režimu bitů.  
  
 Objekt také ukládá ukazatele na dvě funkce, které řídí `strstreambuf` přidělení. Pokud jsou ukazatelé s hodnotou null, objekt devises vlastní metoda přidělování a uvolnění úložiště pro řízené sekvenci.  
  
> [!NOTE]
>  Tato třída je zastaralá. Zvažte použití [stringbuf –](../standard-library/sstream-typedefs.md#stringbuf) nebo [wstringbuf –](../standard-library/sstream-typedefs.md#wstringbuf) místo.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[strstreambuf –](#strstreambuf)|Vytvoří objekt typu `strstreambuf`.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[zablokování](#freeze)|Způsobí, že vyrovnávací paměť datového proudu být k dispozici prostřednictvím operace s datovými proudy vyrovnávací paměti.|  
|[přetečení](#overflow)|Chráněné virtuální funkce, která lze volat, když nové znak je vložen do plné vyrovnávací paměti.|  
|[pbackfail –](#pbackfail)|Chráněný člen virtuální funkci, která se pokusí umístit zpět element do vstupního datového proudu a proveďte aktuálního elementu (ukazuje další ukazatel).|  
|[pcount –](#pcount)|Vrátí počet prvků zapsána do řízené sekvenci.|  
|[seekoff –](#seekoff)|Chráněný člen virtuální funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.|  
|[seekpos –](#seekpos)|Chráněný člen virtuální funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.|  
|[str –](#str)|Volání [freeze](#freeze)a vrátí ukazatel na začátek řízené sekvenci.|  
|[podtečení](#underflow)|Chráněné virtuální funkce k extrakci aktuálního elementu ze vstupního datového proudu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<strstream – >  
  
 **Namespace:** – std  
  
##  <a name="freeze"></a>strstreambuf::freeze  
 Způsobí, že vyrovnávací paměť datového proudu být k dispozici prostřednictvím operace s datovými proudy vyrovnávací paměti.  
  
```  
void freeze(bool _Freezeit = true);
```  
  
### <a name="parameters"></a>Parametry  
 `_Freezeit`  
 A `bool` označující, zda chcete datového proudu k zablokováno.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `_Freezeit` má hodnotu true, funkce mění uložené `strstreambuf` režimu, aby řízené sekvenci pozastaveny. Jinak umožní řízené sekvenci není pozastaveny.  
  
 [Str](#str) znamená `freeze`.  
  
> [!NOTE]
>  Ukotvené vyrovnávací paměti neuvolní během `strstreambuf` odstraňování. Vyrovnávací paměti musí uvolnit, než je uvolněno aby se zabránilo nevrácenou pamětí.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// strstreambuf_freeze.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <strstream>  
  
using namespace std;  
  
void report(strstream &x)  
{  
    if (!x.good())  
        cout << "stream bad" << endl;  
    else  
        cout << "stream good" << endl;  
}  
  
int main()  
{  
    strstream x;  
  
    x << "test1";  
    cout << "before freeze: ";  
    report(x);  
  
    // Calling str freezes stream.  
    cout.write(x.rdbuf()->str(), 5) << endl;  
    cout << "after freeze: ";  
    report(x);  
  
    // Stream is bad now, wrote on frozen stream  
    x << "test1.5";  
    cout << "after write to frozen stream: ";  
    report(x);  
  
    // Unfreeze stream, but it is still bad  
    x.rdbuf()->freeze(false);  
    cout << "after unfreezing stream: ";  
    report(x);  
  
    // Clear stream  
    x.clear();  
    cout << "after clearing stream: ";  
    report(x);  
  
    x << "test3";  
    cout.write(x.rdbuf()->str(), 10) << endl;  
  
    // Clean up.  Failure to unfreeze stream will cause a  
    // memory leak.  
    x.rdbuf()->freeze(false);  
}  
```  
  
```Output  
before freeze: stream good  
test1  
after freeze: stream good  
after write to frozen stream: stream bad  
after unfreezing stream: stream bad  
after clearing stream: stream good  
test1test3  
```  
  
##  <a name="overflow"></a>strstreambuf::Overflow  
 Chráněné virtuální funkce, která lze volat, když nové znak je vložen do plné vyrovnávací paměti.  
  
```  
virtual int overflow(int _Meta = EOF);
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak, který má vložit do vyrovnávací paměti, nebo `EOF`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí `EOF`. Jinak pokud _ *Meta* == `EOF`, vrátí některé hodnoty jiné než `EOF`. Funkce \_ *Meta*.  
  
### <a name="remarks"></a>Poznámky  
 Pokud _ *Meta* ! = `EOF`, chráněného člena virtuální funkce pokusí vložit elementu ( `char`)\_ *Meta* do výstupní vyrovnávací paměť. Můžete tak učinit různými způsoby:  
  
-   Pokud pozice zápisu je k dispozici, může uložit prvek na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.  
  
-   Pokud režimu uložené strstreambuf informacemi o tom, že je řízené sekvenci upravitelnými rozšiřitelná a není ukotvené, funkce zpřístupnit zápisu pozice přidělí nové pro výstupní vyrovnávací paměť. Rozšíření výstupní vyrovnávací paměť tímto způsobem taky ji rozšiřuje na všechny přidružené vstupní vyrovnávací paměť.  
  
##  <a name="pbackfail"></a>strstreambuf::pbackfail  
 Chráněný člen virtuální funkce, která se pokusí vrátit zpět element do vstupního datového proudu a pak jej aktuálního elementu (ukazuje další ukazatel).  
  
```  
virtual int pbackfail(int _Meta = EOF);
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak, který má vložit do vyrovnávací paměti, nebo `EOF`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí `EOF`. Jinak pokud _ *Meta* == `EOF`, vrátí některé hodnoty jiné než `EOF`. Funkce \_ *Meta*.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce se pokusí vrátit zpět element do vstupní vyrovnávací paměť a proveďte aktuálního elementu (ukazuje další ukazatel).  
  
 Pokud _ *Meta* == `EOF`, element tak, aby nabízel zpět je efektivně už v datovém proudu před aktuálního elementu. Jinak je nahrazena daný element **ch** = ( `char`)\_ *Meta*. Funkce může vrátit zpět element různými způsoby:  
  
-   Pokud je k dispozici na pozici putback – a element v ní uloženy porovná rovna **ch**, ho můžete snížení další ukazatele pro vstupní vyrovnávací paměť.  
  
-   Pokud pozice putback – je k dispozici, a pokud je režim strstreambuf zobrazeno řízené sekvenci lze upravovat, můžete ukládat funkce **ch** do pozice putback – a snížení další ukazatele pro vstupní vyrovnávací paměť.  
  
##  <a name="pcount"></a>strstreambuf::pcount  
 Vrátí počet prvků zapsána do řízené sekvenci.  
  
```  
streamsize pcount() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet počet elementů zapsána do řízené sekvenci.  
  
### <a name="remarks"></a>Poznámky  
 Konkrétně Pokud [pptr –](../standard-library/basic-streambuf-class.md#pptr) je ukazatel s hodnotou null, funkce vrátí hodnotu nula. Funkce `pptr`  -  [pbase –](../standard-library/basic-streambuf-class.md#pbase).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// strstreambuf_pcount.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <strstream>  
using namespace std;  
  
int main( )  
{  
   strstream x;  
   x << "test1";  
   cout << x.rdbuf( )->pcount( ) << endl;  
   x << "test2";  
   cout << x.rdbuf( )->pcount( ) << endl;  
}  
```  
  
##  <a name="seekoff"></a>strstreambuf::seekoff  
 Chráněný člen virtuální funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.  
  
```  
virtual streampos seekoff(streamoff _Off,
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
 Pokud neproběhne úspěšně funkce v změna buď nebo obě stream pozic, vrátí pozici výsledné datového proudu. Jinak selže a vrátí pozici neplatný datový proud.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce endeavors ke změně aktuální pozice pro řízené datové proudy. Pro objekt strstreambuf – třída pozice datového proudu je tvořený čistě posun datového proudu. Posunutí nula označí první prvek řízené sekvenci.  
  
 Nové místo je stanoven následujícím způsobem:  
  
-   Pokud `_Way`  ==  `ios_base::beg`, nové pozice se začátkem datového proudu plus _ *vypnout*.  
  
-   Pokud `_Way`  ==  `ios_base::cur`, nové místo je aktuální pozici datového proudu plus _ *vypnout*.  
  
-   Pokud `_Way`  ==  `ios_base::end`, nové pozice se konec datového proudu plus _ *vypnout*.  
  
 Pokud `_Which`  &  **ios_base::in** nenulový a existují vstupní vyrovnávací paměť, funkce mění další pozice číst vstupní vyrovnávací paměti. Pokud `_Which`  &  **ios_base::out** je také nenulové hodnoty, `_Way` ! = **ios_base::cur**a existuje výstupní vyrovnávací paměť, funkce také nastaví další pozici zapsat tak, aby odpovídala Další pozice ke čtení.  
  
 Jinak Pokud `_Which`  &  `ios_base::out` nenulový a existuje výstupní vyrovnávací paměť, funkce mění další pozice se zapisovat do výstupní vyrovnávací paměť. V opačném umísťovací operace se nezdaří. Umísťovací operace úspěšná výsledný datový proud pozice musí ležet v řízené sekvenci.  
  
##  <a name="seekpos"></a>strstreambuf::seekpos  
 Chráněný člen virtuální funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.  
  
```  
virtual streampos seekpos(streampos _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Sp`  
 Pozice k vyhledání pro.  
  
 `_Which`  
 Určuje režim pro umístění ukazatele. Ve výchozím nastavení se vám umožní změnit čtení a zápis pozic.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud neproběhne úspěšně funkce v změna buď nebo obě stream pozic, vrátí pozici výsledné datového proudu. Jinak selže a vrátí pozici neplatný datový proud. Pokud chcete zjistit, pokud pozice datový proud je neplatný, porovnat návratovou hodnotu s `pos_type(off_type(-1))`.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce endeavors ke změně aktuální pozice pro řízené datové proudy. Pro objekt strstreambuf – třída pozice datového proudu je tvořený čistě posun datového proudu. Posunutí nula označí první prvek řízené sekvenci. Nové místo je dáno _ *Sp*.  
  
 Pokud `_Which`  &  **ios_base::in** nenulový a existuje vstupní vyrovnávací paměť, funkce mění další pozice číst vstupní vyrovnávací paměti. Pokud `_Which`  &  `ios_base::out` nenulový a existuje výstupní vyrovnávací paměť, funkce také nastaví další pozici zapsat tak, aby odpovídaly další pozice ke čtení. Jinak Pokud `_Which`  &  `ios_base::out` nenulový a existuje výstupní vyrovnávací paměť, funkce mění další pozice se zapisovat do výstupní vyrovnávací paměť. V opačném umísťovací operace se nezdaří. Umísťovací operace úspěšná výsledný datový proud pozice musí ležet v řízené sekvenci.  
  
##  <a name="str"></a>strstreambuf::str  
 Volání [freeze](#freeze)a vrátí ukazatel na začátek řízené sekvenci.  
  
```  
char *str();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na začátek řízené sekvenci.  
  
### <a name="remarks"></a>Poznámky  
 Existuje žádné ukončující element s hodnotou null, pokud explicitně vložte disk.  
  
### <a name="example"></a>Příklad  
  V tématu [strstreambuf::freeze](#freeze) příklad, který používá **str**.  
  
##  <a name="strstreambuf"></a>strstreambuf::strstreambuf  
 Vytvoří objekt typu `strstreambuf`.  
  
```  
explicit strstreambuf(streamsize count = 0);

strstreambuf(void (* _Allocfunc)(size_t),
    void (* _Freefunc)(void*));

strstreambuf(char* _Getptr,
    streamsize count,
    char* _Putptr = 0);

strstreambuf(signed char* _Getptr,
    streamsize count,
    signed char* _Putptr = 0);

strstreambuf(unsigned char* _Getptr,
    streamsize count,
    unsigned char* _Putptr = 0);

strstreambuf(const char* _Getptr,
    streamsize count);

strstreambuf(const signed char* _Getptr,
    streamsize count);

strstreambuf(const unsigned char* _Getptr,
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 *_Allocfunc*  
 Funkce používá k přidělení vyrovnávací paměti.  
  
 `count`  
 Určuje délka vyrovnávací paměti, na kterou odkazuje `_Getptr`. Pokud `_Getptr` není argument (první formulář konstruktor), velikost navrhované přidělení vyrovnávací paměti.  
  
 *_Freefunc*  
 Funkce použitá k bezplatným vyrovnávací paměti.  
  
 `_Getptr`  
 Vyrovnávací paměť pro vstup.  
  
 `_Putptr`  
 Vyrovnávací paměť, používá pro výstup.  
  
### <a name="remarks"></a>Poznámky  
 První konstruktor ukládá v následující ukazatele řízení vstupní vyrovnávací paměť, výstupní vyrovnávací paměť a přidělení strstreambuf ukazatele null. Nastaví režim uložené strstreambuf aby řízené sekvenci upravitelnými a rozšiřitelná. Přijme také `count` jako velikost navrhované počáteční přidělení.  
  
 Druhý konstruktor chová jako první, s tím rozdílem, že ho ukládá _ *Allocfunc* jako ukazatel na funkci volat pro přidělení úložiště a \_ *Freefunc* jako ukazatel na funkci pro volání na uvolnění tohoto úložiště.  
  
 Tři konstruktory:  
  
```  
strstreambuf(char *_Getptr,
    streamsize count,  
    char *putptr = 0);
  
strstreambuf(signed char *_Getptr,
    streamsize count,  
    signed char *putptr = 0);
  
strstreambuf(unsigned char *_Getptr,
    streamsize count,  
    unsigned char *putptr = 0);
```  
  
 také se chovat jako první, s tím rozdílem, že `_Getptr` označí pole objekt použitý k uložení řízené sekvenci. (Proto ho nesmí být nulový ukazatel.) Počet elementů *N* v poli je stanoven následujícím způsobem:  
  
-   Pokud (`count` > 0), pak *N* je `count`.  
  
-   Pokud (`count` == 0), pak *N* je `strlen`(( **const** `char` *) `_Getptr` ).  
  
-   Pokud (`count` < 0), pak *N* je **INT_MAX**.  
  
 Pokud `_Putptr` je ukazatel s hodnotou null, funkce vytváří jenom vstupní vyrovnávací paměť spuštěním:  
  
```  
setg(_Getptr,
    _Getptr,
    _Getptr + N);
```  
  
 Jinak určuje vstupní a výstupní vyrovnávací paměti spuštěním:  
  
```  
setg(_Getptr,
    _Getptr,
    _Putptr);

setp(_Putptr,
    _Getptr + N);
```  
  
 V takovém případě `_Putptr` musí být v intervalu [ `_Getptr`, `_Getptr`  +  *N*].  
  
 Nakonec tři konstruktory:  
  
```  
strstreambuf(const char *_Getptr,
    streamsize count);

strstreambuf(const signed char *_Getptr,
    streamsize count);

strstreambuf(const unsigned char *_Getptr,
    streamsize count);
```  
  
 všechny chovají stejně jako:  
  
```  
streambuf((char *)_Getptr, count);
```  
  
 Kromě toho, že uložené režim umožňuje řízené sekvenci upravitelnými ani rozšiřitelná.  
  
##  <a name="underflow"></a>strstreambuf::underflow  
 Chráněné virtuální funkce k extrakci aktuálního elementu ze vstupního datového proudu.  
  
```  
virtual int underflow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí `EOF`. Funkce aktuálního elementu ve vstupní datový proud, převést, jak je popsáno výše.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce endeavors k extrakci aktuálního elementu **ch** ze vstupní vyrovnávací paměť, pak zálohy na aktuální pozici datového proudu a vrátí prvek jako (`int`) (`unsigned char`) **ch** . Je to lze provést pouze jedním způsobem: na pozici pro čtení je k dispozici, pak má **ch** jako element uložené ve čtení pozici a přejde na další ukazatele pro vstupní vyrovnávací paměť.  
  
## <a name="see-also"></a>Viz také  
 [streambuf –](../standard-library/streambuf-typedefs.md#streambuf)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)

