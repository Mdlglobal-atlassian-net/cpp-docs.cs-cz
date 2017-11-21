---
title: "basic_streambuf – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
dev_langs: C++
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0586de707bb015e21df5c7975b98be6966cd0262
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="basicstreambuf-class"></a>basic_streambuf – třída
Popisuje abstraktní základní třídu pro odvození datového proudu vyrovnávací paměti řídí přenos elementů do a z konkrétní reprezentace datového proudu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_streambuf;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 A [char_type –](#char_type).  
  
 `Tr`  
 Znak [traits_type –](#traits_type).  
  
## <a name="remarks"></a>Poznámky  
 Šablony třídy popisuje abstraktní základní třídu pro odvození datového proudu vyrovnávací paměti řídí přenos elementů do a z konkrétní reprezentace datového proudu. Třída objektu `basic_streambuf` pomáhá řídit datový proud s elementy typu `Tr`, také známé jako [char_type –](#char_type), jehož vlastnosti znak určuje třídu [char_traits –](../standard-library/char-traits-struct.md), označované také jako [traits_type –](#traits_type).  
  
 Každý datový proud vyrovnávací paměti koncepčně řídí dva nezávislé datové proudy: jednu pro extrakce (vstup) a jeden pro vložení (výstup). Znázornění konkrétní může, ale být jedné nebo obou těchto datových proudů nedostupné. Obvykle udržuje některé vztah mezi dvěma datovými proudy. Vložit do výstupního datového proudu [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> objekt, je třeba, co je později extrahovat z jeho vstupního datového proudu. Při umístění jednoho datového proudu [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> objektu, umístit datový proud současně.  
  
 Veřejné rozhraní pro třídu šablony `basic_streambuf` poskytuje operace, které jsou společné pro všechny vyrovnávací paměti datového proudu, ale specializuje. Chráněné rozhraní poskytuje operace potřebné pro konkrétní reprezentace datového proudu ke své práci. Chráněný člen virtuální funkce umožňují přizpůsobit chování odvozené datového proudu vyrovnávací paměť pro konkrétní reprezentace datového proudu. Každý datový proud odvozené vyrovnávací paměti v této knihovně popisuje, jak se specializuje chování jeho chráněné virtuální členské funkce. Výchozí chování pro základní třídu, což se často stává se nic nestane, je popsaný v tomto tématu.  
  
 Zbývající chráněný členské funkce ovládacího prvku kopírování do a z jakékoli úložiště zadaný do vyrovnávací paměti přenosů do a z datových proudů. Vstupní vyrovnávací paměť, například je charakterizovaná:  
  
- [eback –](#eback), ukazatel na začátku vyrovnávací paměti.  
  
- [gptr –](#gptr), ukazatel na další prvek ke čtení.  
  
- [egptr –](#egptr), ukazatel právě za koncem vyrovnávací paměti.  
  
 Podobně je vyrovnávací paměť výstupu charakterizovaná:  
  
- [pbase –](#pbase), ukazatel na začátku vyrovnávací paměti.  
  
- [pptr –](#pptr), ukazatel na další prvek k zápisu.  
  
- [epptr –](#epptr), ukazatel právě za koncem vyrovnávací paměti.  
  
 Pro všechny vyrovnávací paměť se používá protokol následující:  
  
-   Pokud další ukazatel má hodnotu null, existuje bez vyrovnávací paměti. Všechny tři odkazy, jinak hodnota bodu do stejné pořadí. Budou můžete bezpečně srovnávat pořadí.  
  
-   Pro výstupní vyrovnávací paměť další ukazatel porovná nižší než koncový ukazatele, můžete uložit element na pozici zápisu určené další ukazatel.  
  
-   Pro vstupní vyrovnávací paměť další ukazatel porovná nižší než ukazatele end může číst element na pozici čtení určené další ukazatel.  
  
-   Pro vstupní vyrovnávací paměť Pokud ukazatel začátku porovná nižší než další ukazatele, můžete umístit zpět element na pozici putback – určené odečte další ukazatel.  
  
 Všechny chráněné virtuální členské funkce zápisu pro třídu odvozenou z `basic_streambuf` <  `Elem`, `Tr`> musí spolupracovat zachování tento protokol.  
  
 Třída objektu `basic_streambuf` <  `Elem`, `Tr`> ukládá šest ukazatele popsaných výše. Ukládá také objekt národního prostředí v objektu typu [národního prostředí](../standard-library/locale-class.md) potenciální používané vyrovnávací paměť odvozené datového proudu.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[basic_streambuf –](#basic_streambuf)|Vytvoří objekt typu `basic_streambuf`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type –](#char_type)|Přidruží název typu s `Elem` parametr šablony.|  
|[int_type –](#int_type)|Přidruží název typu v rámci `basic_streambuf` obor s `Elem` parametr šablony.|  
|[off_type –](#off_type)|Přidruží název typu v rámci `basic_streambuf` obor s `Elem` parametr šablony.|  
|[pos_type –](#pos_type)|Přidruží název typu v rámci `basic_streambuf` obor s `Elem` parametr šablony.|  
|[traits_type –](#traits_type)|Přidruží název typu s `Tr` parametr šablony.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[eback –](#eback)|Chráněné funkce, která vrací ukazatel na začátku vstupní vyrovnávací paměť.|  
|[egptr –](#egptr)|Chráněné funkce, která vrací ukazatel právě za koncem vstupní vyrovnávací paměť.|  
|[epptr –](#epptr)|Chráněné funkce, která vrací ukazatel právě za koncem výstupní vyrovnávací paměť.|  
|[gbump –](#gbump)|Chráněné funkci, která přidá `count` na další ukazatele pro vstupní vyrovnávací paměť.|  
|[getloc –](#getloc)|Získá `basic_streambuf` objektu národního prostředí.|  
|[gptr –](#gptr)|Chráněné funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměť.|  
|[imbue –](#imbue)|A chráněné, virtuální funkce volá [pubimbue –](#pubimbue).|  
|[in_avail –](#in_avail)|Vrátí počet prvků, které jsou připravené k číst z vyrovnávací paměti.|  
|[přetečení](#overflow)|Chráněné virtuální funkce, která lze volat, když nové znak je vložen do plné vyrovnávací paměti.|  
|[pbackfail –](#pbackfail)|Chráněný člen virtuální funkci, která se pokusí vrátit zpět element do vstupního datového proudu, proveďte ho aktuálního elementu (ukazuje další ukazatel).|  
|[pbase –](#pbase)|Chráněné funkce, která vrací ukazatel na začátku výstupní vyrovnávací paměť.|  
|[pbump –](#pbump)|Chráněné funkci, která přidá `count` na další ukazatele pro výstupní vyrovnávací paměť.|  
|[pptr –](#pptr)|Chráněné funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměť.|  
|[pubimbue –](#pubimbue)|Nastaví `basic_streambuf` objektu národního prostředí.|  
|[pubseekoff –](#pubseekoff)|Volání [seekoff –](#seekoff), chráněné virtuální funkce, která je přepsání v odvozené třídě.|  
|[pubseekpos –](#pubseekpos)|Volání [seekpos –](#seekpos), chráněné virtuální funkce, která je přepsání v odvozené třídě a obnoví aktuální umístění ukazatele.|  
|[pubsetbuf –](#pubsetbuf)|Volání [setbuf –](#setbuf), chráněné virtuální funkce, která je přepsání v odvozené třídě.|  
|[pubsync –](#pubsync)|Volání [synchronizace](#sync), chráněné virtuální funkce, která je přepsání v odvozené třídě a aktualizuje externí datový proud přidružené k této vyrovnávací paměti.|  
|[sbumpc –](#sbumpc)|Přečte a vrátí aktuálního elementu, ukazatele datového proudu.|  
|[seekoff –](#seekoff)|Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|  
|[seekpos –](#seekpos)|Chráněný člen virtuální funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|  
|[setbuf –](#setbuf)|Chráněný člen virtuální funkce provádí konkrétní operace do vyrovnávací paměti jednotlivých odvozené datového proudu.|  
|[setg –](#setg)|Chráněné funkci, která ukládá `_Gbeg` v ukazatele začátku `_Gnext` v další ukazatel a `_Gend` v end ukazatele pro vstupní vyrovnávací paměť.|  
|[setp –](#setp)|Chráněné funkci, která ukládá `_Pbeg` v ukazatele začátku a `_Pend` v end ukazatele pro výstupní vyrovnávací paměť.|  
|[sgetc –](#sgetc)|Vrátí aktuální element beze změny pozici v datovém proudu.|  
|[sgetn –](#sgetn)|Vrátí počet prvků číst.|  
|[showmanyc –](#showmanyc)|Chráněný člen virtuální funkce, která vrátí počet znaků, které mohou být extrahovány ze vstupního proudu a ujistěte se, že program nebude platit neomezené čekání.|  
|[snextc –](#snextc)|Přečte aktuálního elementu a vrátí následující element.|  
|[sputbackc –](#sputbackc)|Vloží `char_type` v datovém proudu.|  
|[sputc –](#sputc)|Vloží znak do datového proudu.|  
|[sputn –](#sputn)|Řetězec znaků se zařadí do datového proudu.|  
|[stossc –](#stossc)|Přesun za aktuálního elementu v datovém proudu.|  
|[sungetc –](#sungetc)|Získá znak z datového proudu.|  
|[swap](#swap)|Výměny hodnoty v tomto objektu pro hodnoty v zadaných `basic_streambuf` parametru objektu.|  
|[synchronizace](#sync)|Chráněné virtuální funkce, která se pokusí synchronizovat řízené datové proudy s všechny přidružené externí datové proudy.|  
|[uflow –](#uflow)|Chráněné virtuální funkce, která extrahuje aktuálního elementu ze vstupního datového proudu.|  
|[podtečení](#underflow)|Chráněné virtuální funkce, která extrahuje aktuálního elementu ze vstupního datového proudu.|  
|[xsgetn –](#xsgetn)|Chráněné virtuální funkce, která extrahuje prvky ze vstupního datového proudu.|  
|[xsputn –](#xsputn)|Chráněné virtuální funkce, která vloží elementy do výstupního datového proudu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#op_eq)|Přiřadí hodnoty tohoto objektu z jiné `basic_streambuf` objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<streambuf – >  
  
 **Namespace:** – std  
  
##  <a name="basic_streambuf"></a>basic_streambuf::basic_streambuf  
 Vytvoří objekt typu `basic_streambuf`.  
  
```  
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odkaz na lvalue `basic_streambuf` objekt, který se používá k nastavení hodnot pro tento `basic_streambuf` objektu.  
  
### <a name="remarks"></a>Poznámky  
 První chráněný konstruktor ukládá ukazatele null v všechny ukazatele řízení vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Ukládá také `locale::classic` v objektu, národní prostředí. Další informace najdete v tématu [locale::classic](../standard-library/locale-class.md#classic).  
  
 Druhý chráněný konstruktor zkopíruje ukazatelů a národního prostředí z `right`.  
  
##  <a name="char_type"></a>basic_streambuf::char_type  
 Přidruží název typu s **Elem** parametr šablony.  
  
```  
typedef Elem char_type;  
```  
  
##  <a name="eback"></a>basic_streambuf::eback  
 Chráněné funkce, která vrací ukazatel na začátku vstupní vyrovnávací paměť.  
  
```  
char_type *eback() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na začátek vstupní vyrovnávací paměť.  
  
##  <a name="egptr"></a>basic_streambuf::egptr  
 Chráněné funkce, která vrací ukazatel právě za koncem vstupní vyrovnávací paměť.  
  
```  
char_type *egptr() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel právě za koncem vstupní vyrovnávací paměť.  
  
##  <a name="epptr"></a>basic_streambuf::epptr  
 Chráněné funkce, která vrací ukazatel právě za koncem výstupní vyrovnávací paměť.  
  
```  
char_type *epptr() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel právě za koncem výstupní vyrovnávací paměť.  
  
##  <a name="gbump"></a>basic_streambuf::gbump  
 Chráněné funkci, která přidá `count` na další ukazatele pro vstupní vyrovnávací paměť.  
  
```  
void gbump(int count);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Hodnota, o kterou posunut ukazatele.  
  
##  <a name="getloc"></a>basic_streambuf::getloc  
 Získá objekt basic_streambuf národního prostředí.  
  
```  
locale getloc() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt uložené národního prostředí.  
  
### <a name="remarks"></a>Poznámky  
 Související informace najdete v tématu [ios_base::getloc](../standard-library/ios-base-class.md#getloc).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_getloc.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;  
}  
```  
  
```Output  
C  
```  
  
##  <a name="gptr"></a>basic_streambuf::gptr  
 Chráněné funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměť.  
  
```  
char_type *gptr() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další prvek vstupní vyrovnávací paměť.  
  
##  <a name="imbue"></a>basic_streambuf::imbue  
 A chráněná virtuální funkce volá [pubimbue –](#pubimbue).  
  
```  
virtual void imbue(const locale& _Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `_Loc`  
 Odkaz na národního prostředí.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí chování je se nic nestane.  
  
##  <a name="in_avail"></a>basic_streambuf::in_avail  
 Vrátí počet prvků, které jsou připravené k číst z vyrovnávací paměti.  
  
```  
streamsize in_avail();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů, kteří jsou připravení číst z vyrovnávací paměti.  
  
### <a name="remarks"></a>Poznámky  
 Pokud [číst pozice](../standard-library/basic-streambuf-class.md) je k dispozici, vrátí funkce člena [egptr –](#egptr) - [gptr –](#gptr). Funkce [showmanyc –](#showmanyc).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_in_avail.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char c;  
   // cin's buffer is empty, in_avail will return 0  
   cout << cin.rdbuf( )->in_avail( ) << endl;  
   cin >> c;  
   cout << cin.rdbuf( )->in_avail( ) << endl;  
}  
```  
  
##  <a name="int_type"></a>basic_streambuf::int_type  
 Název typu v rámci oboru basic_streambuf přidruží jeden z typů v parametru šablony.  
  
```  
typedef typename traits_type::int_type int_type;  
```  
  
##  <a name="off_type"></a>basic_streambuf::off_type  
 Název typu v rámci oboru basic_streambuf přidruží jeden z typů v parametru šablony.  
  
```  
typedef typename traits_type::off_type off_type;  
```  
  
##  <a name="op_eq"></a>basic_streambuf::Operator =  
 Přiřadí hodnoty tohoto objektu z jiné `basic_streambuf` objektu.  
  
```  
basic_streambuf& operator=(const basic_streambuf& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odkaz na lvalue `basic_streambuf` objekt, který slouží k přiřazení hodnoty k tomuto objektu.  
  
### <a name="remarks"></a>Poznámky  
 Operátor chráněného člena zkopíruje z `right` ukazatele, které řídí vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Ukládá také `right.` [getloc()](#getloc) v `locale object`. Vrátí `*this`.  
  
##  <a name="overflow"></a>basic_streambuf::Overflow  
 Chráněné virtuální funkce, která lze volat, když nové znak je vložen do plné vyrovnávací paměti.  
  
```  
virtual int_type overflow(int_type _Meta = traits_type::eof());
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak, který má vložit do vyrovnávací paměti, nebo **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof** nebo vyvolá výjimku. Funkce **traits_type –::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). Výchozí chování je vrátit **traits_type::eof**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud _ *Meta* porovnat není rovno **traits_type::eof**, chráněného člena virtuální funkce endeavors vložení prvku **traits_type –::**[to_ char_type –](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) do výstupního datového proudu. Můžete tak učinit různými způsoby:  
  
-   Pokud `write position` je k dispozici, ho můžete uložit prvek na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.  
  
-   K dispozici na pozici zápisu mohl zajistit přidělí nové nebo další úložiště pro výstupní vyrovnávací paměť.  
  
-   Ji zpřístupnit zápisu pozice tak, že zápisy out, některé externí cílové, některé nebo všechny prvky mezi začátky a další ukazatele pro výstupní vyrovnávací paměť.  
  
 Funkce virtuální přetečení společně s [synchronizace](#sync) a [podtečení](#underflow) funkce, určuje charakteristiky streambuf – odvozené třídy. Každá odvozená třída může implementovat přetečení odlišně, ale rozhraní s volání stream – třída je stejný.  
  
 `overflow` Funkce nejčastěji volá veřejná `streambuf` funguje jako `sputc` a `sputn` při vložení oblast je plná, ale můžete volat jiné třídy, včetně třídy pro datové proudy `overflow` kdykoliv.  
  
 Funkce využívá znaky v oblasti vložení mezi `pbase` a `pptr` ukazatelů a pak znovu inicializuje oblasti vložení. `overflow` Musí také využívat funkce `nCh` (Pokud `nCh` není `EOF`), nebo ji můžete uvést, že znak v novém put oblasti tak, že budou na další volání.  
  
 Definice spotřebě se liší mezi odvozené třídy. Například `filebuf` třída zapisuje do souboru, jeho znaků při `strstreambuf` třídy zajišťuje jejich jeho vyrovnávací paměti a (Pokud vyrovnávací paměť je určený jako dynamické) rozšíří v reakci na hovor přetečení vyrovnávací paměti. Toto rozšíření se dosahuje uvolnění vyrovnávací paměť původního a nahraďte ji nové, větší jeden. Následující ukazatele jsou upravena podle potřeby.  
  
##  <a name="pbackfail"></a>basic_streambuf::pbackfail  
 Chráněný člen virtuální funkci, která se pokusí vrátit zpět element do vstupního datového proudu, proveďte ho aktuálního elementu (ukazuje další ukazatel).  
  
```  
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak, který má vložit do vyrovnávací paměti, nebo **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof** nebo vyvolá výjimku. Jinak vrátí jinou hodnotu. Výchozí chování je vrátit **traits_type::eof**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud _ *Meta* porovná rovno **traits_type::eof**, element tak, aby nabízel zpět je efektivně už v datovém proudu před aktuálního elementu. Jinak je nahrazena daný element **traits_type –::**[to_char_type –](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Funkce může vrátit zpět element různými způsoby:  
  
-   Pokud pozice putback – je dostupný, ho můžete uložit prvek na pozici putback – a snížení další ukazatele pro vstupní vyrovnávací paměť.  
  
-   K dispozici na pozici putback – mohl zajistit přidělí nové nebo další úložiště pro vstupní vyrovnávací paměť.  
  
-   Datový proud vyrovnávací paměti s společné vstupní a výstupní datové proudy ho můžete zpřístupnit pozice putback – zápisy out, některé externí cílové, některé nebo všechny prvky mezi začátky a další ukazatele pro výstupní vyrovnávací paměť.  
  
##  <a name="pbase"></a>basic_streambuf::pbase  
 Chráněné funkce, která vrací ukazatel na začátku výstupní vyrovnávací paměť.  
  
```  
char_type *pbase() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na začátek výstupní vyrovnávací paměť.  
  
##  <a name="pbump"></a>basic_streambuf::pbump  
 Chráněné funkci, která přidá `count` na další ukazatele pro výstupní vyrovnávací paměť.  
  
```  
void pbump(int count);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Počet znaků, pomocí kterého přejdete na pozici zápis na následující.  
  
##  <a name="pos_type"></a>basic_streambuf::pos_type  
 Název typu v rámci oboru basic_streambuf přidruží jeden z typů v parametru šablony.  
  
```  
typedef typename traits_type::pos_type pos_type;  
```  
  
##  <a name="pptr"></a>basic_streambuf::pptr  
 Chráněné funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměť.  
  
```  
char_type *pptr() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na další prvek výstupní vyrovnávací paměť.  
  
##  <a name="pubimbue"></a>basic_streambuf::pubimbue  
 Nastaví objekt basic_streambuf národního prostředí.  
  
```  
locale pubimbue(const locale& _Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `_Loc`  
 Odkaz na národního prostředí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí hodnota uložená v objektu, národní prostředí.  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce ukládá _ *umístění* v objektu národního prostředí a volání [imbue –](#imbue).  
  
### <a name="example"></a>Příklad  
  V tématu [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) pro příklad, který používá `pubimbue`.  
  
##  <a name="pubseekoff"></a>basic_streambuf::pubseekoff  
 Volání [seekoff –](#seekoff), chráněné virtuální funkce, která je přepsání v odvozené třídě.  
  
```  
pos_type pubseekoff(off_type _Off,
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
 Vrátí nový pozici nebo pozice neplatný datový proud ( [seekoff –](#seekoff)(_ *vypnout*, `_Way`, `_Which`)).  
  
### <a name="remarks"></a>Poznámky  
 Přesune ukazatel vzhledem k `_Way`.  
  
##  <a name="pubseekpos"></a>basic_streambuf::pubseekpos  
 Volání [seekpos –](#seekpos), chráněné virtuální funkce, která je přepsání v odvozené třídě a obnoví aktuální umístění ukazatele.  
  
```  
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Sp`  
 Pozice k vyhledání pro.  
  
 `_Which`  
 Určuje režim pro umístění ukazatele. Ve výchozím nastavení se vám umožní změnit čtení a zápis pozic.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové umístění nebo umístění neplatný datový proud. Pokud chcete zjistit, pokud pozice datový proud je neplatný, porovnat návratovou hodnotu s `pos_type(off_type(-1))`.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [seekpos –](#seekpos)(_ *Sp*, `_Which`).  
  
##  <a name="pubsetbuf"></a>basic_streambuf::pubsetbuf  
 Volání [setbuf –](#setbuf), chráněné virtuální funkce, která je přepsání v odvozené třídě.  
  
```  
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `_Buffer`  
 Ukazatel na `char_type` pro vytvoření této instance.  
  
 `count`  
 Velikost vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí [setbuf –](#setbuf)( `_Buffer`, `count`).  
  
##  <a name="pubsync"></a>basic_streambuf::pubsync  
 Volání [synchronizace](#sync), chráněné virtuální funkce, která je přepsání v odvozené třídě a aktualizuje externí datový proud přidružené k této vyrovnávací paměti.  
  
```  
int pubsync();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí [synchronizace](#sync) nebo -1, pokud selhání.  
  
##  <a name="sbumpc"></a>basic_streambuf::sbumpc  
 Přečte a vrátí aktuálního elementu, ukazatele datového proudu.  
  
```  
int_type sbumpc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální element.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je k dispozici pro čtení pozice, vrátí funkce člen **traits_type –::**[to_int_type –](../standard-library/char-traits-struct.md#to_int_type)(  **\***  [gptr –](#gptr)) a zvýší další ukazatele pro vstupní vyrovnávací paměť. Funkce [uflow –](#uflow).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_sbumpc.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 0;  
   i = cin.rdbuf( )->sbumpc( );  
   cout << i << endl;  
}  
```  
  
```Output  
  
3  
  
```  
  
```Output  
  
      33  
51  
```  
  
##  <a name="seekoff"></a>basic_streambuf::seekoff  
 Chráněný člen virtuální funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.  
  
```  
virtual pos_type seekoff(
    off_type _Off,  
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
 Vrátí nový pozici nebo pozice neplatný datový proud ( `seekoff` (_ *vypnout*, `_Way`, `_Which`)).  
  
### <a name="remarks"></a>Poznámky  
 Nové místo je stanoven následujícím způsobem:  
  
-   Pokud `_Way`  ==  `ios_base::beg`, nové pozice se začátkem datového proudu plus _ *vypnout*.  
  
-   Pokud `_Way`  ==  `ios_base::cur`, nové místo je aktuální pozici datového proudu plus _ *vypnout*.  
  
-   Pokud `_Way`  ==  `ios_base::end`, nové pozice se konec datového proudu plus _ *vypnout*.  
  
 Obvykle Pokud **který & ios_base::in** je nenulové hodnoty, Vstupní datový proud má vliv a pokud **který & ios_base::out** je nenulové hodnoty, do výstupního datového proudu má vliv. Skutečné použití tohoto parametru se liší podle odvozené datového proudu vyrovnávací paměti, ale.  
  
 Pokud funkci podaří Změna datového proudu pozici nebo pozice, vrátí výsledný datový proud pozici nebo jeden z pozice výsledný datový proud. Jinak vrátí pozici neplatný datový proud. Výchozí chování je vrátit pozici neplatný datový proud.  
  
##  <a name="seekpos"></a>basic_streambuf::seekpos  
 Chráněný člen virtuální funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.  
  
```  
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Sp`  
 Pozice k vyhledání pro.  
  
 `_Which`  
 Určuje režim pro umístění ukazatele. Ve výchozím nastavení se vám umožní změnit čtení a zápis pozic.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové pozici nebo pozice neplatný datový proud. Pokud chcete zjistit, pokud pozice datový proud je neplatný, porovnat návratovou hodnotu s `pos_type(off_type(-1))`.  
  
### <a name="remarks"></a>Poznámky  
 Nové místo je _ *Sp*.  
  
 Obvykle Pokud **který & ios_base::in** je nenulové hodnoty, Vstupní datový proud má vliv a pokud **který & ios_base::out** je nenulové hodnoty, do výstupního datového proudu má vliv. Skutečné použití tohoto parametru se liší podle odvozené datového proudu vyrovnávací paměti, ale.  
  
 Pokud funkci podaří Změna datového proudu pozici nebo pozice, vrátí výsledný datový proud pozici nebo jeden z pozice výsledný datový proud. Jinak vrátí pozici neplatný datový proud (-1). Výchozí chování je vrátit pozici neplatný datový proud.  
  
##  <a name="setbuf"></a>basic_streambuf::setbuf  
 Chráněný člen virtuální funkce, která provádí konkrétní operace do vyrovnávací paměti jednotlivých odvozené datového proudu.  
  
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
 Výchozí chování je vrátit **to**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf`poskytuje oblast paměti pro `streambuf` objekt, který chcete použít. Použití vyrovnávací paměti v definován v odvozených třídách.  
  
##  <a name="setg"></a>basic_streambuf::setg  
 Chráněné funkci, která ukládá _ *Gbeg* v ukazatele začátku `_Gnext` v další ukazatel a `_Gend` v end ukazatele pro vstupní vyrovnávací paměť.  
  
```  
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```  
  
### <a name="parameters"></a>Parametry  
 *_Gbeg*  
 Ukazatel na začátku vyrovnávací paměti.  
  
 `_Gnext`  
 Ukazatel na někde uprostřed vyrovnávací paměti.  
  
 `_Gend`  
 Ukazatel na konce vyrovnávací paměti.  
  
##  <a name="setp"></a>basic_streambuf::setp  
 Chráněné funkci, která ukládá `_Pbeg` v ukazatele začátku a `_Pend` v end ukazatele pro výstupní vyrovnávací paměť.  
  
```  
void setp(char_type* _Pbeg, char_type* _Pend);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pbeg`  
 Ukazatel na začátku vyrovnávací paměti.  
  
 `_Pend`  
 Ukazatel na konce vyrovnávací paměti.  
  
##  <a name="sgetc"></a>basic_streambuf::sgetc  
 Vrátí aktuální element beze změny pozici v datovém proudu.  
  
```  
int_type sgetc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální element.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je k dispozici pro čtení pozice, vrátí funkce člen **traits_type –::**[to_int_type –](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr –](#gptr)). Funkce [podtečení](#underflow).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_sgetc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );  
  
   char i = myfile.rdbuf( )->sgetc( );  
   cout << i << endl;  
   i = myfile.rdbuf( )->sgetc( );  
   cout << i << endl;  
}  
```  
  
##  <a name="sgetn"></a>basic_streambuf::sgetn  
 Extrahuje až `count` znaků ze vstupní vyrovnávací paměť a ukládá je do zadané vyrovnávací paměti `ptr`.  
  
 Tato metoda je potenciálně nebezpečné, jako je závislé na volajícího, aby zkontrolujte správnost předané hodnoty.  
  
```  
streamsize sgetn(
    char_type* ptr,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Vyrovnávací paměť tak, aby obsahovala extrahované znaky.  
  
 `count`  
 Počet elementů ke čtení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů přečíst. V tématu [streamsize](../standard-library/ios-typedefs.md#streamsize) Další informace.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [xsgetn –](#xsgetn)( `ptr`, `count`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_sgetn.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
#include <fstream>  
  
int main()  
{  
    using namespace std;  
  
    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);  
    char a[10];  
  
    // Extract 3 characters from myfile and store them in a.  
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996  
    a[i] = myfile.widen('\0');  
  
    // Display the size and contents of the buffer passed to sgetn.  
    cout << i << " " << a << endl;  
  
    // Display the contents of the original input buffer.  
    cout << myfile.rdbuf() << endl;  
}  
```  
  
##  <a name="showmanyc"></a>basic_streambuf::showmanyc  
 Chráněný člen virtuální funkce, která vrátí počet znaků, které mohou být extrahovány ze vstupního proudu a ujistěte se, že program nebude platit neomezené čekání.  
  
```  
virtual streamsize showmanyc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí chování je vrátit nula.  
  
##  <a name="snextc"></a>basic_streambuf::snextc  
 Přečte aktuálního elementu a vrátí následující element.  
  
```  
int_type snextc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Na další prvek v datovém proudu.  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [sbumpc –](#sbumpc) a v případě, že funkce vrací **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof), vrátí **traits_type::eof**. Funkce [sgetc –](#sgetc).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_snextc.cpp  
// compile with: /EHsc  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   int i = 0;  
   i = cin.rdbuf( )->snextc( );  
   // cout << ( int )char_traits<char>::eof << endl;  
   cout << i << endl;  
}  
```  
  
```Output  
  
aa  
  
```  
  
```Output  
  
aa97  
```  
  
##  <a name="sputbackc"></a>basic_streambuf::sputbackc  
 Vloží char_type – datového proudu.  
  
```  
int_type sputbackc(char_type _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí znak nebo selhání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je k dispozici na pozici putback – a `_Ch` porovná rovno znak uložené v této pozici, snižuje funkce člen další ukazatele pro vstupní vyrovnávací paměť a vrátí **traits_type –::**[to_int_ typ](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). Funkce [pbackfail –](#pbackfail)( `_Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_sputbackc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )  
{  
    using namespace std;  
  
    ifstream myfile("basic_streambuf_sputbackc.txt",  
        ios::in);  
  
    int i = myfile.rdbuf()->sbumpc();  
    cout << (char)i << endl;  
    int j = myfile.rdbuf()->sputbackc('z');  
    if (j == 'z')  
    {  
        cout << "it worked" << endl;  
    }  
    i = myfile.rdbuf()->sgetc();  
    cout << (char)i << endl;  
}  
```  
  
##  <a name="sputc"></a>basic_streambuf::sputc  
 Vloží znak do datového proudu.  
  
```  
int_type sputc(char_type _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí znak, pokud bylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `write position` je k dispozici, členské funkce úložiště `_Ch` v pozici zápisu zvýší další ukazatele pro výstupní vyrovnávací paměť a vrátí **traits_type –::**[to_int_type –](../standard-library/char-traits-struct.md#to_int_type)() `_Ch`). Funkce [přetečení](#overflow)( `_Ch`).  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_sputc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
  
   int i = cout.rdbuf( )->sputc( 'a' );  
   cout << endl << ( char )i << endl;  
}  
```  
  
```Output  
a  
a  
```  
  
##  <a name="sputn"></a>basic_streambuf::sputn  
 Řetězec znaků se zařadí do datového proudu.  
  
```  
streamsize sputn(const char_type* ptr, streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Řetězcem znaků.  
  
 `count`  
 Počet znaků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet znaků, které jsou ve skutečnosti vloženy do datového proudu.  
  
### <a name="remarks"></a>Poznámky  
 Členské funkce vrátí hodnotu [xsputn –](#xsputn)( `ptr`, `count`). Najdete v části poznámky tohoto člena pro další informace.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_sputn.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main()  
{  
    using namespace std;  
  
    streamsize i = cout.rdbuf()->sputn("test", 4);  
    cout << endl << i << endl;  
}  
```  
  
```Output  
test  
4  
```  
  
##  <a name="stossc"></a>basic_streambuf::stossc  
 Přesun za aktuálního elementu v datovém proudu.  
  
```  
void stossc();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání členských funkcí [sbumpc –](#sbumpc). Všimněte si, že implementace není požádáni o zadání této – členská funkce.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_stossc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );  
  
   myfile.rdbuf( )->stossc( );  
   char i = myfile.rdbuf( )->sgetc( );  
   cout << i << endl;  
}  
```  
  
##  <a name="sungetc"></a>basic_streambuf::sungetc  
 Získá znak z datového proudu.  
  
```  
int_type sungetc();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí znak nebo selhání.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je k dispozici putback – pozice, člen funkce sníží další ukazatele pro vstupní vyrovnávací paměť a vrátí `traits_type::` [to_int_type –](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr –](#gptr)). Však není vždy možné určit poslední znak čtení tak, aby ho bylo možné zaznamenat ve stavu aktuální vyrovnávací paměti. Pokud je tato hodnota true, pak funkce vrátí hodnotu [pbackfail –](#pbackfail). Abyste předešli této situaci, udržování přehledu o znak, který má vrátit zpět a volání `sputbackc(ch)`, které nebudou zadané nemůžete ji volat na začátku datového proudu a nemáte pokusíte vrátit zpět více než jeden znak.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// basic_streambuf_sungetc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
  
   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );  
  
   // Read and increment  
   int i = myfile.rdbuf( )->sbumpc( );  
   cout << ( char )i << endl;  
  
   // Read and increment  
   i = myfile.rdbuf( )->sbumpc( );  
   cout << ( char )i << endl;  
  
   // Decrement, read, and do not increment  
   i = myfile.rdbuf( )->sungetc( );  
   cout << ( char )i << endl;  
  
   i = myfile.rdbuf( )->sungetc( );   
   cout << ( char )i << endl;  
  
   i = myfile.rdbuf( )->sbumpc( );  
   cout << ( char )i << endl;  
}  
```  
  
##  <a name="swap"></a>basic_streambuf::swap  
 Výměny hodnoty v tomto objektu pro hodnoty v zadaných `basic_streambuf` objektu.  
  
```  
void swap(basic_streambuf& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`right`|Odkaz na lvalue `basic_streambuf` objekt, který se používá k výměně hodnoty.|  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen funkce výměny se `right` všechny ukazatele řízení `input buffer` a `output buffer`. Také výměny `right.` [getloc()](#getloc) s `locale` objektu.  
  
##  <a name="sync"></a>basic_streambuf::Sync  
 Chráněné virtuální funkce, která se pokusí synchronizovat řízené datové proudy s všechny přidružené externí datové proudy.  
  
```  
virtual int sync();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkce nemůže být úspěšná, vrátí hodnotu -1. Výchozí chování je vrátit nula.  
  
### <a name="remarks"></a>Poznámky  
 `sync`zahrnuje zápis se všechny prvky mezi počáteční a další ukazatele pro výstupní vyrovnávací paměť. Nezahrnuje jak vrátit zpátky všechny elementy mezi na další a končit ukazatele pro vstupní vyrovnávací paměť.  
  
##  <a name="traits_type"></a>basic_streambuf::traits_type  
 Přidruží název typu s **Tr** parametr šablony.  
  
```  
typedef Tr traits_type;  
```  
  
##  <a name="uflow"></a>basic_streambuf::uflow  
 Chráněné virtuální funkce, která extrahuje aktuálního elementu ze vstupního datového proudu.  
  
```  
virtual int_type uflow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální element.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce pokusí extrahovat aktuálního elementu **ch** ze vstupního streamu s, pak zálohy na aktuální pozici datového proudu a vrátí prvek jako **traits_type –::** [ to_int_type –](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Můžete tak učinit různými způsoby:  
  
-   Pokud je k dispozici pro čtení pozice, trvá **ch** jako element uložené ve čtení pozici a přejde na další ukazatele pro vstupní vyrovnávací paměť.  
  
-   Umožňuje čtení element přímo, některé externí zdroj a její doručení jako hodnota **ch**.  
  
-   Datový proud vyrovnávací paměti s společné vstupní a výstupní datové proudy ho můžete zpřístupnit čtení pozice zápisy out, některé externí cílové, některé nebo všechny prvky mezi začátky a další ukazatele pro výstupní vyrovnávací paměť. Nebo ji můžete přidělit nové nebo další úložiště pro vstupní vyrovnávací paměť. Funkce potom načte, některé externí zdroj, jeden či více elementů.  
  
 Pokud funkce nemůže být úspěšná, vrátí **traits_type –::**[eof](../standard-library/char-traits-struct.md#eof), nebo vyvolá výjimku. Jinak vrátí aktuálního elementu `ch` v vstupního datového proudu, převést, jak je popsáno výše a přejde na další ukazatele pro vstupní vyrovnávací paměť. Výchozí chování je volat [podtečení](#underflow) a v případě, že funkce vrací **traits_type::eof**, vrátit **traits_type::eof**. Funkce, jinak vrátí hodnotu aktuálního elementu **ch** v vstupního datového proudu, převést, jak se popisuje výš a přejde na další ukazatele pro vstupní vyrovnávací paměť.  
  
##  <a name="underflow"></a>basic_streambuf::underflow  
 Chráněný, virtuální funkce k extrakci aktuálního elementu ze vstupního datového proudu.  
  
```  
virtual int_type underflow();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální element.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce endeavors k extrakci aktuálního elementu **ch** ze vstupního proudu bez posunutí aktuální stream pozice a vrátit jej jako `traits_type::` [to_int_type –](../standard-library/char-traits-struct.md#to_int_type)() **ch**). Můžete tak učinit různými způsoby:  
  
-   Pokud je k dispozici, přečtěte si pozice **ch** je element uložené v pozici pro čtení. Další informace o to, najdete v části poznámky [basic_streambuf – třída](../standard-library/basic-streambuf-class.md).  
  
-   K dispozici pro čtení pozice mohl zajistit přidělí nové nebo další úložiště pro vstupní vyrovnávací paměť, pak se čte, některé externí zdroj, jeden či více elementů. Další informace o to, najdete v části poznámky [basic_streambuf – třída](../standard-library/basic-streambuf-class.md).  
  
 Pokud funkce nemůže být úspěšná, vrátí `traits_type::` [eof](../standard-library/char-traits-struct.md#eof) `()` nebo vyvolá výjimku. Jinak vrátí aktuálního elementu ve vstupní datový proud, převést výše popsané. Výchozí chování je vrátit `traits_type::eof()`.  
  
 Virtuální `underflow` funkce, se [synchronizace](#sync) a [přetečení](#overflow) funkce, definuje vlastnosti `streambuf`-odvozené třídy. Každá odvozená třída může implementovat `underflow` odlišně, ale rozhraní s volání stream – třída je stejný.  
  
 `underflow` Funkce nejčastěji volá veřejná `streambuf` funguje jako [sgetc –](#sgetc) a [sgetn –](#sgetn) při oblasti get je prázdný, ale můžete volat jiné třídy, včetně třídy pro datové proudy `underflow` kdykoliv.  
  
 `underflow` Funkce poskytuje oblasti get s znaky ze vstupního zdroje. Pokud oblasti get obsahuje znaky, `underflow` vrátí první znak. Pokud oblasti get je prázdná, vyplní celé oblasti get a vrátí další znak (což je ponechá v oblasti get). Pokud nejsou žádné další znaky k dispozici, pak `underflow` vrátí `EOF` a zůstane prázdný oblasti get.  
  
 V `strstreambuf` třídy, `underflow` upraví [egptr –](#egptr) ukazatel na přístup k úložišti, dynamicky přidělenou voláním `overflow`.  
  
##  <a name="xsgetn"></a>basic_streambuf::xsgetn  
 Chráněný, virtuální funkce do extrahuje prvky ze vstupního proudu.  
  
 Tato metoda je potenciálně nebezpečné, jako je závislé na volajícího, aby zkontrolujte správnost předané hodnoty.  
  
```  
virtual streamsize xsgetn(
    char_type* ptr,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Vyrovnávací paměť tak, aby obsahovala extrahované znaky.  
  
 `count`  
 Počet elementů k extrakci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů extrahovat.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce extrahuje až `count` elementy ze vstupního datového proudu jako Pokud podle opakovaná volání [sbumpc –](#sbumpc)a ukládá je do pole počínaje `ptr`. Vrátí počet elementů ve skutečnosti extrahovat.  
  
##  <a name="xsputn"></a>basic_streambuf::xsputn  
 Chráněný, virtuální funkce vložení elementy do výstupního datového proudu.  
  
```  
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ukazatel na elementy k vložení.  
  
 `count`  
 Počet elementů k vložení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet elementů ve skutečnosti vloženy do datového proudu.  
  
### <a name="remarks"></a>Poznámky  
 Chráněný člen virtuální funkce vloží až `count` elementy do výstupu datového proudu, jako kdyby podle opakovaná volání [sputc –](#sputc), z pole počínaje `ptr`. Vložení znaků do výstupního datového proudu zastaví jednou všechny `count` vytvořilo znaků nebo pokud volání `sputc( count)` by vrátit `traits::eof()`. Vrátí počet elementů ve skutečnosti vložit.  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)

