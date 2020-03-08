---
title: basic_streambuf – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 1b43c2291499af87f2be1e5bec25717a30c28bfd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856498"
---
# <a name="basic_streambuf-class"></a>basic_streambuf – třída

Popisuje abstraktní základní třídu pro odvození vyrovnávací paměti datového proudu, který řídí přenos prvků do a z konkrétní reprezentace datového proudu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parametry

*Elem*\
[Char_type](#char_type).

*Tr*\
Znak [traits_type](#traits_type).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje abstraktní základní třídu pro odvození vyrovnávací paměti datového proudu, který řídí přenos prvků do a z konkrétní reprezentace datového proudu. Objekt třídy `basic_streambuf` pomáhá řídit datový proud pomocí prvků typu *TR*, označovaného také jako [char_type](#char_type), jejichž znaková vlastnost je určena třídou [char_traits](../standard-library/char-traits-struct.md), označovanou také jako [traits_type](#traits_type).

Každý datový proud vyrovnávací paměti koncepční řízení dvou nezávislých datových proudů: jeden pro extrakci (vstup) a jeden pro vložení (výstup). Konkrétní reprezentace však může být buď nepřístupná, nebo oběma datovými proudy. Obvykle udržuje určitou relaci mezi dvěma datovými proudy. Obsah, který vložíte do výstupního datového proudu [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, například objekt `Tr`>, je to, co později extrahujete ze vstupního proudu. Když umístíte jeden datový proud [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`objekt >, umístí se druhý datový proud do společné části.

Veřejné rozhraní pro šablonu třídy `basic_streambuf` poskytuje operace, které jsou společné pro všechny vyrovnávací paměti datového proudu, ale specializované. Chráněné rozhraní poskytuje operace potřebné k tomu, aby konkrétní reprezentace datového proudu fungovala. Chráněné virtuální členské funkce umožňují přizpůsobit chování odvozené vyrovnávací paměti datového proudu pro konkrétní reprezentace datového proudu. Jednotlivé vyrovnávací paměti v odvozeném datovém proudu v této knihovně popisují, jak specializují chování svých chráněných virtuálních členských funkcí. Výchozí chování základní třídy, která často nedělá nic, je popsáno v tomto tématu.

Zbývající chráněné členské funkce řídí kopírování do a z jakéhokoli úložiště dodaného pro přenos vyrovnávací paměti do a z datových proudů. Vstupní vyrovnávací paměť je například charakterizována:

- [eback](#eback), ukazatel na začátek vyrovnávací paměti.

- [GPTR](#gptr), ukazatel na další prvek, který se má přečíst.

- [egptr](#egptr), ukazatel hned za koncem vyrovnávací paměti.

Podobně výstupní vyrovnávací paměť je charakterizována:

- [pbase](#pbase), ukazatel na začátek vyrovnávací paměti.

- [pptr](#pptr), ukazatel na další prvek, který se má zapsat.

- [epptr](#epptr), ukazatel hned za koncem vyrovnávací paměti.

Pro jakoukoli vyrovnávací paměť se používá následující protokol:

- Pokud má další ukazatel hodnotu null, neexistuje žádná vyrovnávací paměť. Jinak všechny tři ukazatele ukazují na stejnou sekvenci. Můžou být v porovnání s jejich pořadím bezpečné.

- V případě výstupní vyrovnávací paměti, pokud další ukazatel porovnává méně než koncový ukazatel, můžete uložit element na pozici zápisu určenou dalším ukazatelem.

- V případě vstupní vyrovnávací paměti, pokud další ukazatel porovnává méně než koncový ukazatel, můžete číst element na pozici pro čtení určenou dalším ukazatelem.

- V případě vstupní vyrovnávací paměti, pokud počáteční ukazatel porovnává méně než další ukazatel, můžete převést element na putback pozici určenou sníženým dalším ukazatelem.

Všechny chráněné virtuální členské funkce, které zapisujete pro třídu odvozenou z `basic_streambuf`< `Elem`, `Tr`> musí spolupracovat na zachování tohoto protokolu.

Objekt třídy `basic_streambuf`< `Elem``Tr`> ukládá šest ukazatelů dříve popsaných v předchozích krocích. Také ukládá objekt národního prostředí do objektu typu [locale](../standard-library/locale-class.md) pro potenciální použití v odvozené vyrovnávací paměti datového proudu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_streambuf](#basic_streambuf)|Vytvoří objekt typu `basic_streambuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Přidruží název typu k parametru `Elem` šablony.|
|[int_type](#int_type)|Přidruží název typu v rámci rozsahu `basic_streambuf` s parametrem šablony `Elem`.|
|[off_type](#off_type)|Přidruží název typu v rámci rozsahu `basic_streambuf` s parametrem šablony `Elem`.|
|[pos_type](#pos_type)|Přidruží název typu v rámci rozsahu `basic_streambuf` s parametrem šablony `Elem`.|
|[traits_type](#traits_type)|Přidruží název typu k parametru `Tr` šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[eback](#eback)|Chráněná funkce, která vrací ukazatel na začátek vstupní vyrovnávací paměti.|
|[egptr](#egptr)|Chráněná funkce, která vrací ukazatel hned za koncem vstupní vyrovnávací paměti.|
|[epptr](#epptr)|Chráněná funkce, která vrací ukazatel hned za koncem výstupní vyrovnávací paměti.|
|[gbump](#gbump)|Chráněná funkce, která přidá `count` k dalšímu ukazateli pro vstupní vyrovnávací paměť.|
|[getloc](#getloc)|Získá národní prostředí objektu `basic_streambuf`.|
|[gptr](#gptr)|Chráněná funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměti.|
|[imbue –](#imbue)|Chráněná virtuální funkce volaná funkcí [pubimbue](#pubimbue).|
|[in_avail](#in_avail)|Vrátí počet prvků, které jsou připraveny ke čtení z vyrovnávací paměti.|
|[plně](#overflow)|Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce, která se pokusí vrátit prvek do vstupního datového proudu, pak jej nastaví na aktuální prvek (ukazuje na další ukazatel).|
|[pbase](#pbase)|Chráněná funkce, která vrací ukazatel na začátek výstupní vyrovnávací paměti.|
|[pbump](#pbump)|Chráněná funkce, která přidá `count` k dalšímu ukazateli pro výstupní vyrovnávací paměť.|
|[pptr](#pptr)|Chráněná funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměti.|
|[pubimbue](#pubimbue)|Nastaví národní prostředí objektu `basic_streambuf`.|
|[pubseekoff](#pubseekoff)|Volá [seekoff](#seekoff), chráněnou virtuální funkci, která je přepsána v odvozené třídě.|
|[pubseekpos](#pubseekpos)|Volá [seekpos](#seekpos), chráněnou virtuální funkci, která je přepsána v odvozené třídě a obnoví aktuální pozici ukazatele.|
|[pubsetbuf](#pubsetbuf)|Volá [setbuf](#setbuf), chráněnou virtuální funkci, která je přepsána v odvozené třídě.|
|[pubsync](#pubsync)|Volá [synchronizaci](#sync), chráněnou virtuální funkci, která je přepsána v odvozené třídě a aktualizuje externí datový proud přidružený k této vyrovnávací paměti.|
|[sbumpc –](#sbumpc)|Přečte a vrátí aktuální prvek a přesune ukazatel na datový proud.|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené streamy.|
|[setbuf](#setbuf)|Chráněná virtuální členská funkce provádí operaci specifickou pro každou odvozenou vyrovnávací paměť datového proudu.|
|[setg](#setg)|Chráněná funkce, která ukládá `_Gbeg` do počátečního ukazatele, `_Gnext` v dalším ukazateli a `_Gend` na koncovém ukazateli pro vstupní vyrovnávací paměť.|
|[setp](#setp)|Chráněná funkce, která ukládá `_Pbeg` do počátečního ukazatele a `_Pend` v koncovém ukazateli výstupní vyrovnávací paměti.|
|[sgetc –](#sgetc)|Vrátí aktuální element beze změny pozice v datovém proudu.|
|[sgetn](#sgetn)|Vrátí počet čtených prvků.|
|[showmanyc](#showmanyc)|Chráněná virtuální členská funkce, která vrací počet znaků, které mohou být extrahovány ze vstupního datového proudu a zajišťují, že program nebude podléhat neurčitému čekání.|
|[snextc](#snextc)|Přečte aktuální prvek a vrátí následující element.|
|[sputbackc](#sputbackc)|Vloží `char_type` do datového proudu.|
|[sputc](#sputc)|Vloží znak do datového proudu.|
|[sputn](#sputn)|Vloží řetězec znaků do datového proudu.|
|[stossc](#stossc)|Přesunout za aktuální prvek v datovém proudu.|
|[sungetc](#sungetc)|Získá znak z datového proudu.|
|[adresu](#swap)|Vyměňuje hodnoty v tomto objektu pro hodnoty v zadaném parametru objektu `basic_streambuf`.|
|[brání](#sync)|Chráněná virtuální funkce, která se pokouší synchronizovat řízené streamy s libovolnými přidruženými externími proudy.|
|[uflow](#uflow)|Chráněná virtuální funkce, která extrahuje aktuální prvek ze vstupního datového proudu.|
|[podtečení](#underflow)|Chráněná virtuální funkce, která extrahuje aktuální prvek ze vstupního datového proudu.|
|[xsgetn](#xsgetn)|Chráněná virtuální funkce, která extrahuje prvky ze vstupního datového proudu.|
|[xsputn](#xsputn)|Chráněná virtuální funkce, která vloží prvky do výstupního datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnoty tohoto objektu z jiného objektu `basic_streambuf`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<streambuf >

**Obor názvů:** std

## <a name="basic_streambuf"></a>basic_streambuf:: basic_streambuf

Vytvoří objekt typu `basic_streambuf`.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Odkaz lvalue na objekt `basic_streambuf`, který se používá k nastavení hodnot tohoto objektu `basic_streambuf`.

### <a name="remarks"></a>Poznámky

První chráněný konstruktor ukládá ukazatel s hodnotou null ve všech ukazatelích řídících vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Také ukládá `locale::classic` do objektu locale. Další informace naleznete v tématu [locale:: Classic](../standard-library/locale-class.md#classic).

Druhý chráněný konstruktor zkopíruje ukazatele a národní prostředí *zprava*.

## <a name="char_type"></a>basic_streambuf:: char_type

Přidruží název typu k parametru šablony **elem** .

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>basic_streambuf:: eback

Chráněná funkce, která vrací ukazatel na začátek vstupní vyrovnávací paměti.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek vstupní vyrovnávací paměti.

## <a name="egptr"></a>basic_streambuf:: egptr

Chráněná funkce, která vrací ukazatel hned za koncem vstupní vyrovnávací paměti.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel hned za koncem vstupní vyrovnávací paměti.

## <a name="epptr"></a>basic_streambuf:: epptr

Chráněná funkce, která vrací ukazatel hned za koncem výstupní vyrovnávací paměti.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel hned za koncem výstupní vyrovnávací paměti.

## <a name="gbump"></a>basic_streambuf:: gbump

Chráněná funkce, která přičítá *počet* k dalšímu ukazateli pro vstupní vyrovnávací paměť.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parametry

*počet*\
Hodnota, o kterou má být ukazatel posunut.

## <a name="getloc"></a>basic_streambuf:: getloc

Získá národní prostředí objektu basic_streambuf.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt národního prostředí.

### <a name="remarks"></a>Poznámky

Související informace najdete v tématu [ios_base:: getloc](../standard-library/ios-base-class.md#getloc).

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

## <a name="gptr"></a>basic_streambuf:: GPTR

Chráněná funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměti.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další prvek vstupní vyrovnávací paměti.

## <a name="imbue"></a>basic_streambuf:: imbue –

Chráněná virtuální funkce volaná funkcí [pubimbue](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Odkaz na národní prostředí.

### <a name="remarks"></a>Poznámky

Výchozím chováním je Neprovádět žádnou akci.

## <a name="in_avail"></a>basic_streambuf:: in_avail

Vrátí počet prvků, které jsou připraveny ke čtení z vyrovnávací paměti.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které jsou připraveny ke čtení z vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici [pozice pro čtení](../standard-library/basic-streambuf-class.md) , vrátí členská funkce [egptr](#egptr) - [GPTR](#gptr). V opačném případě vrátí [showmanyc](#showmanyc).

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

## <a name="int_type"></a>basic_streambuf:: int_type

Přidruží název typu v rámci rozsahu basic_streambuf k jednomu z typů v parametru šablony.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>basic_streambuf:: off_type

Přidruží název typu v rámci rozsahu basic_streambuf k jednomu z typů v parametru šablony.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>basic_streambuf:: operator =

Přiřadí hodnoty tohoto objektu z jiného objektu `basic_streambuf`.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*pravé*\
Odkaz lvalue na objekt `basic_streambuf`, který se používá k přiřazení hodnot tomuto objektu.

### <a name="remarks"></a>Poznámky

Chráněný členský operátor kopíruje z *pravého* ukazatele, který řídí vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Také v `locale object`ukládá `right.`[getloc ()](#getloc) . Vrátí `*this`.

## <a name="overflow"></a>basic_streambuf:: přetečení

Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který má být vložen do vyrovnávací paměti, nebo **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type:: EOF** nebo vyvolá výjimku. V opačném případě vrátí **traits_type::** [Not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *meta*). Výchozím chováním je vrácení **traits_type:: EOF**.

### <a name="remarks"></a>Poznámky

Pokud *\_meta* nerovná se **traits_type:: EOF**, budoucna chráněná virtuální členská funkce pro vložení elementu **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_meta*) do výstupního datového proudu. To lze provést různými způsoby:

- Pokud je `write position` k dispozici, může uložit element do pozice pro zápis a zvýšit další ukazatel pro výstupní vyrovnávací paměť.

- Dá se k dispozici pozice pro zápis přidělením nového nebo dalšího úložiště pro výstupní vyrovnávací paměť.

- Dá se použít k dispozici k umístění zápisu, a to v některém externím cíli, některých nebo všech prvcích mezi začátkem a dalšími ukazateli pro výstupní vyrovnávací paměť.

Virtuální funkce přetečení společně s funkcemi [Sync](#sync) a [subflow](#underflow) definuje charakteristiky třídy odvozené od streambuf. Každá odvozená třída může implementovat přetečení odlišně, ale rozhraní se třídou volajícího datového proudu je stejné.

Funkce `overflow` je nejčastěji volána funkcemi veřejné `streambuf` jako `sputc` a `sputn`, když je oblast Put zaplněna, ale jiné třídy, včetně tříd datového proudu, mohou volat `overflow` kdykoli.

Funkce využívá znaky v oblasti vložení mezi `pbase` a ukazateli `pptr` a pak znovu inicializuje oblast PUT. Funkce `overflow` musí také spotřebovávat `nCh` (Pokud `nCh` není `EOF`), nebo se může rozhodnout vložit tento znak do nové oblasti Put tak, aby se při dalším volání využíval.

Definice spotřebování se liší mezi odvozenými třídami. Například třída `filebuf` zapisuje své znaky do souboru, zatímco třída `strstreambuf` je zachovává do vyrovnávací paměti a (Pokud je vyrovnávací paměť určena jako dynamická), rozšiřuje vyrovnávací paměť v reakci na volání přetečení. Toto rozšíření se dosahuje uvolněním staré vyrovnávací paměti a jejím nahrazením novým, větším. Ukazatelé se upraví podle potřeby.

## <a name="pbackfail"></a>basic_streambuf::p selže.

Chráněná virtuální členská funkce, která se pokusí vrátit prvek do vstupního datového proudu, pak jej nastaví na aktuální prvek (ukazuje na další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který má být vložen do vyrovnávací paměti, nebo **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type:: EOF** nebo vyvolá výjimku. V opačném případě vrátí jinou hodnotu. Výchozím chováním je vrácení **traits_type:: EOF**.

### <a name="remarks"></a>Poznámky

Je-li *\_meta* porovnávána rovna **traits_type:: EOF**, element, který se má vrátit zpět, je efektivně ten, který je již v datovém proudu před aktuálním prvkem. V opačném případě je tento prvek nahrazen **traits_type::** [To_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_meta*). Funkce může vložit element zpět různými způsoby:

- Pokud je k dispozici putback pozice, může uložit prvek do putback pozice a snížit další ukazatel pro vstupní vyrovnávací paměť.

- Může zpřístupnit putback pozici přidělením nového nebo dalšího úložiště pro vstupní vyrovnávací paměť.

- V případě vyrovnávací paměti datového proudu s běžnými vstupními a výstupními proudy může být putback pozice k dispozici při zapisování, do některých externích cílů, některých nebo všech prvků mezi začátkem a dalšími ukazateli pro výstupní vyrovnávací paměť.

## <a name="pbase"></a>basic_streambuf: základ:p

Chráněná funkce, která vrací ukazatel na začátek výstupní vyrovnávací paměti.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek výstupní vyrovnávací paměti.

## <a name="pbump"></a>basic_streambuf::p nárazník

Chráněná funkce, která přičítá *počet* k dalšímu ukazateli pro výstupní vyrovnávací paměť.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parametry

*počet*\
Počet znaků, o které má být pozice zápisu přesunuta vpřed.

## <a name="pos_type"></a>basic_streambuf::p os_type

Přidruží název typu v rámci rozsahu basic_streambuf k jednomu z typů v parametru šablony.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>basic_streambuf::p PTR

Chráněná funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměti.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další prvek výstupní vyrovnávací paměti.

## <a name="pubimbue"></a>basic_streambuf::p ubimbue

Nastaví národní prostředí objektu basic_streambuf.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Odkaz na národní prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota uložená v objektu národního prostředí.

### <a name="remarks"></a>Poznámky

Členská funkce ukládá _ *Loc* do objektu locale a volá [imbue –](#imbue).

### <a name="example"></a>Příklad

Příklad, který používá `pubimbue`, naleznete v tématu [basic_ios:: imbue –](../standard-library/basic-ios-class.md#imbue) .

## <a name="pubseekoff"></a>basic_streambuf::p ubseekoff

Volá [seekoff](#seekoff), chráněnou virtuální funkci, která je přepsána v odvozené třídě.

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozice pro hledání relativně od *_Way*.

*_Way*\
Výchozí bod pro operace posunu. Možné hodnoty najdete v tématu [seekdir](../standard-library/ios-base-class.md#seekdir) .

*_Which*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo neplatnou pozici streamu ( [seekoff](#seekoff)(_ *off*, `_Way`, `_Which`)).

### <a name="remarks"></a>Poznámky

Přesune ukazatel relativně k *_Way*.

## <a name="pubseekpos"></a>basic_streambuf::p ubseekpos

Volá [seekpos](#seekpos), chráněnou virtuální funkci, která je přepsána v odvozené třídě, a obnoví aktuální pozici ukazatele.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice pro hledání.

*_Which*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Nová pozice nebo neplatná pozice v datovém proudu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [seekpos](#seekpos)(_ *SP*, `_Which`).

## <a name="pubsetbuf"></a>basic_streambuf::p ubsetbuf

Volá [setbuf](#setbuf), chráněnou virtuální funkci, která je přepsána v odvozené třídě.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Ukazatel na `char_type` pro tuto instanci.

*počet*\
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí [setbuf](#setbuf)(`_Buffer`, `count`).

## <a name="pubsync"></a>basic_streambuf::p ubsync

Volá [synchronizaci](#sync), chráněnou virtuální funkci, která je přepsána v odvozené třídě, a aktualizuje externí datový proud přidružený k této vyrovnávací paměti.

```cpp
int pubsync();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [synchronizaci](#sync) nebo-1, pokud selže.

## <a name="sbumpc"></a>basic_streambuf:: sbumpc –

Přečte a vrátí aktuální prvek a přesune ukazatel na datový proud.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici pozice pro čtení, vrátí členská funkce **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong> [GPTR](#gptr)) a zvýší další ukazatel pro vstupní vyrovnávací paměť. V opačném případě vrátí [uflow](#uflow).

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

```Input
3
```

```Output
33
51
```

## <a name="seekoff"></a>basic_streambuf:: seekoff

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené streamy.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozice pro hledání relativně od *_Way*.

*_Way*\
Výchozí bod pro operace posunu. Možné hodnoty najdete v tématu [seekdir](../standard-library/ios-base-class.md#seekdir) .

*_Which*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Vrátí novou pozici nebo neplatnou pozici streamu (`seekoff` (_ *off*, `_Way`, `_Which`)).

### <a name="remarks"></a>Poznámky

Nová pozice je určena následujícím způsobem:

- Pokud `_Way` == `ios_base::beg`, nová pozice je začátek datového proudu *plus _.*

- Pokud `_Way` == `ios_base::cur`, nová pozice je aktuální pozice v datovém proudu plus *_.*

- Pokud `_Way` == `ios_base::end`, nová pozice je konec datového proudu *plus _.*

Obvykle platí, že pokud **& ios_base:: v** je nenulová, je vstupní datový proud ovlivněn a pokud **& ios_base:: out** je nenulová, je ovlivněn výstupní datový proud. Skutečné použití tohoto parametru se ale liší mezi odvozenými vyrovnávacími paměťmi streamu.

Pokud funkce uspěje při změně pozice nebo pozice datového proudu, vrátí výslednou pozici v datovém proudu nebo jednu z výsledných datových míst. V opačném případě vrátí neplatnou pozici streamu. Výchozím chováním je vrácení neplatné pozice streamu.

## <a name="seekpos"></a>basic_streambuf:: seekpos

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené streamy.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice pro hledání.

*_Which*\
Určuje režim pro pozici ukazatele. Ve výchozím nastavení je to, aby bylo možné upravovat pozice pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Nová pozice nebo neplatná pozice datového proudu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Nová pozice je _ *SP*.

Obvykle platí, že pokud **& ios_base:: v** je nenulová, je vstupní datový proud ovlivněn a pokud **& ios_base:: out** je nenulová, je ovlivněn výstupní datový proud. Skutečné použití tohoto parametru se ale liší mezi odvozenými vyrovnávacími paměťmi streamu.

Pokud funkce uspěje při změně pozice nebo pozice datového proudu, vrátí výslednou pozici v datovém proudu nebo jednu z výsledných datových míst. V opačném případě vrátí neplatnou pozici streamu (-1). Výchozím chováním je vrácení neplatné pozice streamu.

## <a name="setbuf"></a>basic_streambuf:: setbuf

Chráněná virtuální členská funkce, která provádí operaci specifickou pro každou odvozenou vyrovnávací paměť datového proudu.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Ukazatel na vyrovnávací paměť.

*počet*\
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Výchozím chováním **je vrácení.**

### <a name="remarks"></a>Poznámky

Viz [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf` poskytuje oblast paměti pro použití objektu `streambuf`. Jak se používá vyrovnávací paměť v definovaném v odvozených třídách.

## <a name="setg"></a>basic_streambuf:: setg

Chráněná funkce, která ukládá _ *Gbeg* do počátečního ukazatele, `_Gnext` v dalším ukazateli a `_Gend` na koncovém ukazateli pro vstupní vyrovnávací paměť.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parametry

*_Gbeg*\
Ukazatel na začátek vyrovnávací paměti.

*_Gnext*\
Ukazatel na někde uprostřed vyrovnávací paměti.

*_Gend*\
Ukazatel na konec vyrovnávací paměti.

## <a name="setp"></a>basic_streambuf:: setp

Chráněná funkce, která ukládá *_Pbeg* do počátečního ukazatele a *_Pend* v koncovém ukazateli výstupní vyrovnávací paměti.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parametry

*_Pbeg*\
Ukazatel na začátek vyrovnávací paměti.

*_Pend*\
Ukazatel na konec vyrovnávací paměti.

## <a name="sgetc"></a>basic_streambuf:: sgetc –

Vrátí aktuální element beze změny pozice v datovém proudu.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Je-li k dispozici pozice pro čtení, vrátí členská funkce **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`*`[GPTR](#gptr)). V opačném případě vrátí [podtečení](#underflow).

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

## <a name="sgetn"></a>basic_streambuf:: sgetn

Extrahuje *počet* znaků ze vstupní vyrovnávací paměti a uloží je do zadané vyrovnávací paměti *PTR*.

Tato metoda je potenciálně nebezpečná, protože spoléhá volajícího na kontrolu správnosti předaných hodnot.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Vyrovnávací paměť obsahující extrahované znaky.

*počet*\
Počet prvků, které mají být čteny.

### <a name="return-value"></a>Návratová hodnota

Počet přečtených prvků. Další informace najdete v tématu [StreamSize](../standard-library/ios-typedefs.md#streamsize) .

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [xsgetn](#xsgetn)(`ptr`, `count`).

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

## <a name="showmanyc"></a>basic_streambuf:: showmanyc

Chráněná virtuální členská funkce, která vrací počet znaků, které mohou být extrahovány ze vstupního datového proudu a zajišťují, že program nebude podléhat neurčitému čekání.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Návratová hodnota

Výchozím chováním je vrácení nuly.

## <a name="snextc"></a>basic_streambuf:: snextc

Přečte aktuální prvek a vrátí následující element.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Návratová hodnota

Další prvek v datovém proudu.

### <a name="remarks"></a>Poznámky

Členská funkce volá [sbumpc –](#sbumpc) a, pokud tato funkce vrací **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), vrátí **traits_type:: EOF**. V opačném případě vrátí [sgetc –](#sgetc).

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

```Input
aa
```

```Output
aa97
```

## <a name="sputbackc"></a>basic_streambuf:: sputbackc

Vloží char_type do datového proudu.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak

### <a name="return-value"></a>Návratová hodnota

Vrátí znak nebo chybu.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici putback pozice a *_Ch* porovná se znakem uloženým na této pozici, členská funkce sníží další ukazatel pro vstupní vyrovnávací paměť a vrátí **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`_Ch`). V opačném případě vrátí [pbackfail](#pbackfail)(`_Ch`).

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

## <a name="sputc"></a>basic_streambuf:: sputc

Vloží znak do datového proudu.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak

### <a name="return-value"></a>Návratová hodnota

Vrátí znak, pokud bylo úspěšné.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici `write position`, členská funkce uloží *_Ch* v umístění pro zápis, zvýší další ukazatel pro výstupní vyrovnávací paměť a vrátí **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`_Ch`). V opačném případě vrátí [přetečení](#overflow)(`_Ch`).

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

## <a name="sputn"></a>basic_streambuf:: sputn

Vloží řetězec znaků do datového proudu.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Řetězec znaků.

*počet*\
Počet znaků.

### <a name="return-value"></a>Návratová hodnota

Počet znaků, které jsou ve skutečnosti vloženy do datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [xsputn](#xsputn)(`ptr`, `count`). Další informace najdete v části s poznámkami tohoto člena.

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

## <a name="stossc"></a>basic_streambuf:: stossc

Přesunout za aktuální prvek v datovém proudu.

```cpp
void stossc();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [sbumpc –](#sbumpc). Všimněte si, že k poskytnutí této členské funkce není nutná implementace.

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

## <a name="sungetc"></a>basic_streambuf:: sungetc

Získá znak z datového proudu.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí buď znak, nebo selhání.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici putback pozice, členská funkce sníží další ukazatel vstupní vyrovnávací paměti a vrátí `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(`*`[GPTR](#gptr)). Není však vždy možné určit poslední přečtený znak, aby mohl být zachycen ve stavu aktuální vyrovnávací paměti. Pokud je to pravda, funkce vrátí [pbackfail](#pbackfail). Chcete-li se této situaci vyhnout, Sledujte znak, který vrátí zpět a zavolejte `sputbackc(ch)`, což neselže, pokud ho nebudete volat na začátku datového proudu a nepokusíte se vrátit více než jeden znak.

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

## <a name="swap"></a>basic_streambuf:: swap

Vyměňuje hodnoty v tomto objektu pro hodnoty v zadaném objektu `basic_streambuf`.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Kliknutím*|Odkaz lvalue na objekt `basic_streambuf`, který se používá k výměně hodnot.|

### <a name="remarks"></a>Poznámky

Chráněná členská funkce se bude *napravit* pomocí všech ukazatelů řídících `input buffer` a `output buffer`. Také vyměňuje `right.`[getloc ()](#getloc) s objektem `locale`.

## <a name="sync"></a>basic_streambuf:: Sync

Chráněná virtuální funkce, která se pokouší synchronizovat řízené streamy s libovolnými přidruženými externími proudy.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí-1. Výchozím chováním je vrácení nuly.

### <a name="remarks"></a>Poznámky

`sync` zahrnuje zápis všech prvků mezi začátkem a dalšími ukazateli pro výstupní vyrovnávací paměť. Nezahrnuje vkládání všech prvků mezi dalšími a koncovými ukazateli pro vstupní vyrovnávací paměť.

## <a name="traits_type"></a>basic_streambuf:: traits_type

Přidruží název typu k parametru šablony **TR** .

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>basic_streambuf:: uflow

Chráněná virtuální funkce, která extrahuje aktuální prvek ze vstupního datového proudu.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí extrahovat aktuální prvek **ch** ze vstupního datového proudu, potom posunout aktuální pozici datového proudu a vrátit prvek jako **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). To lze provést různými způsoby:

- Pokud je k dispozici pozice pro čtení, je objekt **ch** jako element uložený na pozici pro čtení a přesune další ukazatel pro vstupní vyrovnávací paměť.

- Může číst element přímo z nějakého externího zdroje a dodat je jako hodnota **ch**.

- V případě vyrovnávací paměti datového proudu s běžnými vstupními a výstupními proudy může být pozice pro čtení k dispozici při zapisování, do některých externích cílů, některých nebo všech prvků mezi začátkem a dalšími ukazateli pro výstupní vyrovnávací paměť. Nebo může přidělit nové nebo dodatečné úložiště pro vstupní vyrovnávací paměť. Funkce poté čte z nějakého externího zdroje, jednoho nebo více prvků.

Pokud funkce nemůže být úspěšná, vrátí **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof)nebo vyvolá výjimku. V opačném případě vrátí aktuální prvek `ch` ve vstupním datovém proudu, převedený jak je popsáno výše, a posune další ukazatel pro vstupní vyrovnávací paměť. Výchozím chováním je volání [podtečení](#underflow) a, pokud tato funkce vrací **traits_type:: eof**pro vrácení **traits_type:: EOF**. V opačném případě funkce vrátí aktuální element **ch** ve vstupním streamu, převedený jak je popsáno výše, a přesune další ukazatel pro vstupní vyrovnávací paměť.

## <a name="underflow"></a>basic_streambuf:: subflow

Chráněná virtuální funkce pro extrakci aktuálního prvku ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce budoucna extrakci aktuálního prvku **ch** ze vstupního datového proudu, aniž by došlo k posunutí aktuální pozice datového proudu, a vrátí ho jako `traits_type::`[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). To lze provést různými způsoby:

- Pokud je k dispozici pozice pro čtení, **ch** je prvek uložený na pozici pro čtení. Další informace o tomto tématu naleznete v části poznámky [třídy basic_streambuf](../standard-library/basic-streambuf-class.md).

- Dá se k dispozici pozice pro čtení přidělením nového nebo dalšího úložiště pro vstupní vyrovnávací paměť a následným čtením z nějakého externího zdroje, jednoho nebo více prvků. Další informace o tomto tématu naleznete v části poznámky [třídy basic_streambuf](../standard-library/basic-streambuf-class.md).

Pokud funkce nemůže být úspěšná, vrátí `traits_type::`[eof](../standard-library/char-traits-struct.md#eof)`()` nebo vyvolá výjimku. V opačném případě vrátí aktuální prvek ve vstupním datovém proudu, který je převeden tak, jak je popsáno výše. Výchozím chováním je vrácení `traits_type::eof()`.

Funkce Virtual `underflow` s funkcemi [Sync](#sync) a [přetečení](#overflow) definuje vlastnosti třídy odvozené od `streambuf`. Každá odvozená třída může implementovat `underflow` odlišně, ale rozhraní s třídou volajícího datového proudu je stejné.

Funkce `underflow` je nejčastěji volána funkcemi veřejné `streambuf`, jako je [sgetc –](#sgetc) a [sgetn](#sgetn) , pokud je oblast Get prázdná, ale jiné třídy, včetně tříd datového proudu, mohou volat `underflow` kdykoli.

Funkce `underflow` poskytuje oblast získat se znaky ze vstupního zdroje. Pokud oblast get obsahuje znaky, `underflow` vrátí první znak. Je-li oblast získat prázdná, vyplní oblast získat a vrátí další znak (který je v oblasti Get). Pokud nejsou k dispozici žádné další znaky, `underflow` vrátí `EOF` a ponechá oblast získat prázdnou.

Ve třídě `strstreambuf` `underflow` upravuje ukazatel [egptr](#egptr) pro přístup k úložišti, které bylo dynamicky přiděleno voláním `overflow`.

## <a name="xsgetn"></a>basic_streambuf:: xsgetn

Chráněná virtuální funkce pro extrakci prvků ze vstupního datového proudu.

Tato metoda je potenciálně nebezpečná, protože spoléhá volajícího na kontrolu správnosti předaných hodnot.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Vyrovnávací paměť obsahující extrahované znaky.

*počet*\
Počet prvků, které mají být extrahovány.

### <a name="return-value"></a>Návratová hodnota

Počet extrahovaných elementů

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce extrahuje *Celkový počet* prvků ze vstupního datového proudu, jako by to opakovalo opakovaná volání [sbumpc –](#sbumpc)a ukládá je do pole začínajícího na *PTR*. Vrátí počet prvků, které jsou ve skutečnosti extrahovány.

## <a name="xsputn"></a>basic_streambuf:: xsputn

Chráněná virtuální funkce pro vkládání prvků do výstupního datového proudu.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel na prvky, které chcete vložit.

*počet*\
Počet prvků, které mají být vloženy.

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které jsou ve skutečnosti vloženy do datového proudu.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vloží do výstupního datového proudu až do *počtu* elementů, jako by to opakovali volání [sputc](#sputc), od pole začínajícího na *PTR*. Vložení znaků do výstupního proudu zastaví po zapsání všech znaků *Count* nebo volání `sputc( count)` vrátilo `traits::eof()`. Vrátí počet prvků, které jsou skutečně vloženy.

## <a name="see-also"></a>Viz také

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream – programování](../standard-library/iostream-programming.md)\
[iostreams – konvence](../standard-library/iostreams-conventions.md)
