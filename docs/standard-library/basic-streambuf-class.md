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
ms.openlocfilehash: 0cf7b61bde86a4643836346dafd36680fb8cf302
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376732"
---
# <a name="basic_streambuf-class"></a>basic_streambuf – třída

Popisuje abstraktní základní třídu pro odvození vyrovnávací paměti datového proudu, která řídí přenos prvků do a z určité reprezentace datového proudu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parametry

*Elem*\
A [char_type](#char_type).

*Tr*\
Znak [traits_type](#traits_type).

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje abstraktní základní třídu pro odvození vyrovnávací paměti datového proudu, která řídí přenos prvků do a z určité reprezentace datového proudu. Objekt třídy `basic_streambuf` pomáhá řídit datový proud s prvky typu *Tr*, označované také jako [char_type](#char_type), jejichž znakové vlastnosti jsou určeny třídou [char_traits](../standard-library/char-traits-struct.md), označovanou také jako [traits_type](#traits_type).

Každá vyrovnávací paměť datového proudu koncepčně řídí dva nezávislé datové proudy: jeden pro extrakce (vstup) a jeden pro vložení (výstup). Konkrétní reprezentace však může znepřístupnit jeden nebo oba tyto datové proudy. Obvykle udržuje některé vztahy mezi dvěma datovými proudy. Co vložíte do výstupního datového proudu [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> objekt, například je to, co později extrahujete z jeho vstupního datového proudu. Když umístíte jeden [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`proud `Tr` basic_filebuf ,> objektu, umístíte druhý datový proud do tandemu.

Veřejné rozhraní šablony `basic_streambuf` třídy poskytuje operace, které jsou společné pro všechny vyrovnávací paměti datového proudu, ale specializované. Chráněné rozhraní poskytuje operace potřebné pro konkrétní reprezentaci datového proudu k jeho práci. Chráněné virtuální členské funkce umožňují přizpůsobit chování vyrovnávací paměti odvozeného datového proudu pro konkrétní reprezentaci datového proudu. Každá vyrovnávací paměť odvozeného datového proudu v této knihovně popisuje, jak se specializuje na chování svých chráněných virtuálních členských funkcí. Výchozí chování pro základní třídy, která je často nedělat nic, je popsánv tomto tématu.

Zbývající chráněné členské funkce řídí kopírování do a z libovolného úložiště dodaného do vyrovnávací paměti přenosů do a z datových proudů. Vstupní vyrovnávací paměť je například charakterizována:

- [eback](#eback), ukazatel na začátek vyrovnávací paměti.

- [gptr](#gptr), ukazatel na další prvek ke čtení.

- [egptr](#egptr), ukazatel těsně za koncem vyrovnávací paměti.

Podobně je výstupní vyrovnávací paměť charakterizována:

- [pbase](#pbase), ukazatel na začátek vyrovnávací paměti.

- [pptr](#pptr), ukazatel na další prvek k zápisu.

- [epptr](#epptr), ukazatel těsně za koncem vyrovnávací paměti.

Pro všechny vyrovnávací paměti se používá následující protokol:

- Pokud je další ukazatel null, neexistuje žádná vyrovnávací paměť. V opačném případě všechny tři ukazatele přejděte do stejné sekvence. Mohou být bezpečně porovnány s objednávkou.

- Pro výstupní vyrovnávací paměti, pokud další ukazatel porovná méně než ukazatel konce, můžete uložit prvek na pozici zápisu určené další ukazatel.

- Pro vstupní vyrovnávací paměti, pokud další ukazatel porovná méně než ukazatel konce, můžete číst prvek na pozici pro čtení určené další ukazatel.

- Pro vstupní vyrovnávací paměti, pokud počáteční ukazatel porovná méně než další ukazatel, můžete umístit zpět prvek na pozici putback určené dekremented další ukazatel.

Všechny chráněné virtuální členské funkce, které `basic_streambuf` <  `Elem`zapisujete pro třídu odvozenou z aplikace , `Tr`> musí spolupracovat při údržbě tohoto protokolu.

Objekt třídy `basic_streambuf` <  `Elem` `Tr` ,> ukládá šest ukazatele dříve popsané. Také ukládá objekt národního prostředí v objektu typu [národní prostředí](../standard-library/locale-class.md) pro potenciální použití ve vyrovnávací paměti odvozeného datového proudu.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_streambuf](#basic_streambuf)|Vytvoří objekt typu `basic_streambuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Přidruží název `Elem` typu k parametru šablony.|
|[int_type](#int_type)|Přidruží název `basic_streambuf` typu `Elem` v rámci oboru k parametru šablony.|
|[off_type](#off_type)|Přidruží název `basic_streambuf` typu `Elem` v rámci oboru k parametru šablony.|
|[pos_type](#pos_type)|Přidruží název `basic_streambuf` typu `Elem` v rámci oboru k parametru šablony.|
|[traits_type](#traits_type)|Přidruží název `Tr` typu k parametru šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[eback](#eback)|Chráněná funkce, která vrací ukazatel na začátek vstupní vyrovnávací paměti.|
|[egptr](#egptr)|Chráněná funkce, která vrací ukazatel těsně za koncem vstupní vyrovnávací paměti.|
|[epptr](#epptr)|Chráněná funkce, která vrací ukazatel těsně za koncem výstupní vyrovnávací paměti.|
|[gbump](#gbump)|Chráněná funkce, `count` která přidá další ukazatel pro vstupní vyrovnávací paměť.|
|[getloc](#getloc)|Získá `basic_streambuf` národní prostředí objektu.|
|[gptr](#gptr)|Chráněná funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměti.|
|[Naplnit](#imbue)|Chráněná virtuální funkce volaná [pubimbue](#pubimbue).|
|[in_avail](#in_avail)|Vrátí počet prvků, které jsou připraveny ke čtení z vyrovnávací paměti.|
|[Přetečení](#overflow)|Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.|
|[pbackfail](#pbackfail)|Chráněná virtuální členská funkce, která se pokusí vrátit prvek zpět do vstupního datového proudu, pak z něj udělejte aktuální prvek (na který odkazuje další ukazatel).|
|[Pbase](#pbase)|Chráněná funkce, která vrací ukazatel na začátek výstupní vyrovnávací paměti.|
|[pbump](#pbump)|Chráněná funkce, `count` která přidá k dalšímu ukazateli pro výstupní vyrovnávací paměť.|
|[pptr](#pptr)|Chráněná funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměti.|
|[pubimbue](#pubimbue)|Nastaví `basic_streambuf` národní prostředí objektu.|
|[pubseekoff](#pubseekoff)|Volání [seekoff](#seekoff), chráněné virtuální funkce, která je přepsána v odvozené třídě.|
|[pubseekpos](#pubseekpos)|Volání [seekpos](#seekpos), chráněné virtuální funkce, která je přepsána v odvozené třídě a obnoví aktuální pozici ukazatele.|
|[pubsetbuf](#pubsetbuf)|Volání [setbuf](#setbuf), chráněné virtuální funkce, která je přepsána v odvozené třídě.|
|[pubsync](#pubsync)|[Volání synchronizace](#sync), chráněné virtuální funkce, která je přepsána v odvozené třídě a aktualizuje externí datový proud přidružený k této vyrovnávací paměti.|
|[sbumpc](#sbumpc)|Přečte a vrátí aktuální prvek přesunutím ukazatele datového proudu.|
|[seekoff](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[seekpos](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice pro řízené datové proudy.|
|[setbuf](#setbuf)|Chráněná virtuální členská funkce provádí konkrétní operaci pro každou vyrovnávací paměť odvozeného datového proudu.|
|[setg](#setg)|Chráněná funkce, `_Gbeg` která ukládá `_Gnext` v počáteční ukazatel, `_Gend` v dalším ukazatel i v ukazatel i koncový ukazatel pro vstupní vyrovnávací paměti.|
|[setp](#setp)|Chráněná funkce, `_Pbeg` která ukládá `_Pend` v počáteční ukazatel a v ukazatel na konci pro výstupní vyrovnávací paměti.|
|[sgetc](#sgetc)|Vrátí aktuální prvek bez změny polohy v datovém proudu.|
|[sgetn](#sgetn)|Vrátí počet přečtených prvků.|
|[showmanyc](#showmanyc)|Chráněná virtuální členská funkce, která vrací počet znaků, které lze extrahovat ze vstupního datového proudu, a zajišťuje, že program nebude podléhat neurčitému čekání.|
|[snextc](#snextc)|Přečte aktuální prvek a vrátí následující prvek.|
|[sputbackc](#sputbackc)|Vloží `char_type` do proudu.|
|[sputc](#sputc)|Vloží znak do datového proudu.|
|[sputn](#sputn)|Vloží řetězec znaků do datového proudu.|
|[stossc](#stossc)|Přesuňte se za aktuální prvek v datovém proudu.|
|[sungetc](#sungetc)|Získá znak z datového proudu.|
|[Swap](#swap)|Vymění hodnoty v tomto objektu za `basic_streambuf` hodnoty v parametru zadaný objekt.|
|[synchronizace](#sync)|Chráněná virtuální funkce, která se pokusí synchronizovat řízené datové proudy se všemi přidruženými externími datovými proudy.|
|[uflow](#uflow)|Chráněná virtuální funkce, která extrahuje aktuální prvek ze vstupního datového proudu.|
|[Podtečení](#underflow)|Chráněná virtuální funkce, která extrahuje aktuální prvek ze vstupního datového proudu.|
|[xsgetn](#xsgetn)|Chráněná virtuální funkce, která extrahuje prvky ze vstupního datového proudu.|
|[xsputn](#xsputn)|Chráněná virtuální funkce, která vloží prvky do výstupního datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnoty tohoto objektu `basic_streambuf` z jiného objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<streambuf>

**Obor názvů:** std

## <a name="basic_streambufbasic_streambuf"></a><a name="basic_streambuf"></a>basic_streambuf::basic_streambuf

Vytvoří objekt typu `basic_streambuf`.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Lvalue odkaz na `basic_streambuf` objekt, který se používá `basic_streambuf` k nastavení hodnot pro tento objekt.

### <a name="remarks"></a>Poznámky

První chráněný konstruktor ukládá nulový ukazatel ve všech ukazatelích ovládajících vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Ukládá také `locale::classic` v objektu národního prostředí. Další informace naleznete v [tématu locale::classic](../standard-library/locale-class.md#classic).

Druhý chráněný konstruktor zkopíruje ukazatele a národní prostředí z *prava .*

## <a name="basic_streambufchar_type"></a><a name="char_type"></a>basic_streambuf::char_type

Přidruží název typu k parametru šablony **Elem.**

```cpp
typedef Elem char_type;
```

## <a name="basic_streambufeback"></a><a name="eback"></a>basic_streambuf::eback

Chráněná funkce, která vrací ukazatel na začátek vstupní vyrovnávací paměti.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek vstupní vyrovnávací paměti.

## <a name="basic_streambufegptr"></a><a name="egptr"></a>basic_streambuf::egptr

Chráněná funkce, která vrací ukazatel těsně za koncem vstupní vyrovnávací paměti.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel těsně za koncem vstupní vyrovnávací paměti.

## <a name="basic_streambufepptr"></a><a name="epptr"></a>basic_streambuf::epptr

Chráněná funkce, která vrací ukazatel těsně za koncem výstupní vyrovnávací paměti.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel těsně za koncem výstupní vyrovnávací paměti.

## <a name="basic_streambufgbump"></a><a name="gbump"></a>basic_streambuf::gbump

Chráněná funkce, která přidá *počet* k dalšímu ukazateli vstupní vyrovnávací paměti.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parametry

*Počet*\
Částka, o kterou předem ukazatel.

## <a name="basic_streambufgetloc"></a><a name="getloc"></a>basic_streambuf::getloc

Získá národní prostředí objektu basic_streambuf.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt národního prostředí.

### <a name="remarks"></a>Poznámky

Související informace naleznete [v tématu ios_base::getloc](../standard-library/ios-base-class.md#getloc).

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

## <a name="basic_streambufgptr"></a><a name="gptr"></a>basic_streambuf::gptr

Chráněná funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměti.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další prvek vstupní vyrovnávací paměti.

## <a name="basic_streambufimbue"></a><a name="imbue"></a>basic_streambuf::imbue

Chráněná virtuální funkce volaná [pubimbue](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Odkaz na národní prostředí.

### <a name="remarks"></a>Poznámky

Výchozí chování je nedělat nic.

## <a name="basic_streambufin_avail"></a><a name="in_avail"></a>basic_streambuf::in_avail

Vrátí počet prvků, které jsou připraveny ke čtení z vyrovnávací paměti.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které jsou připraveny ke čtení z vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici [pozice pro čtení,](../standard-library/basic-streambuf-class.md) členská funkce vrátí [egptr](#egptr) - [gptr](#gptr). V opačném případě vrátí [showmanyc](#showmanyc).

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

## <a name="basic_streambufint_type"></a><a name="int_type"></a>basic_streambuf::int_type

Přidruží název typu v rámci basic_streambuf oboru k jednomu z typů v parametru šablony.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_streambufoff_type"></a><a name="off_type"></a>basic_streambuf::off_type

Přidruží název typu v rámci basic_streambuf oboru k jednomu z typů v parametru šablony.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_streambufoperator"></a><a name="op_eq"></a>basic_streambuf::operátor=

Přiřadí hodnoty tohoto objektu `basic_streambuf` z jiného objektu.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*Právo*\
Lvalue odkaz na `basic_streambuf` objekt, který se používá k přiřazení hodnot k tomuto objektu.

### <a name="remarks"></a>Poznámky

Operátor chráněného člena zkopíruje *zpravé* ukazatele, které řídí vstupní vyrovnávací paměti a výstupní vyrovnávací paměti. Ukládá také `right.` [getloc()](#getloc) `locale object`v . Vrátí `*this`.

## <a name="basic_streambufoverflow"></a><a name="overflow"></a>basic_streambuf:přetečení

Chráněná virtuální funkce, která může být volána při vložení nového znaku do úplné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který chcete vložit do vyrovnávací paměti nebo **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof** nebo vyvolá výjimku. V opačném případě vrátí **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). Výchozí chování je vrátit **traits_type::eof**.

### <a name="remarks"></a>Poznámky

Pokud * \_Meta* neporovnává rovno **traits_type::eof**, chráněná virtuální členská funkce se snaží vložit prvek **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) do výstupního datového proudu. Může tak učinit různými způsoby:

- Pokud `write position` a je k dispozici, můžete uložit prvek do pozice zápisu a přírůstek další ukazatel pro výstupní vyrovnávací paměti.

- Může zpřístupnit pozici zápisu přidělením nového nebo dalšího úložiště pro výstupní vyrovnávací paměť.

- Může zpřístupnit pozici zápisu zápisem do některého externího cíle, některé nebo všechny prvky mezi počáteční a další ukazatele pro výstupní vyrovnávací paměti.

Virtuální funkce přetečení spolu s funkcemi [synchronizace](#sync) a [podtečení](#underflow) definuje charakteristiky třídy odvozené od streambuf. Každá odvozená třída může implementovat přetečení jinak, ale rozhraní s volající třídou datového proudu je stejné.

Funkce `overflow` je nejčastěji volána `streambuf` veřejnými funkcemi, jako `sputc` je a `sputn` když je oblast put `overflow` plná, ale jiné třídy, včetně tříd datového proudu, mohou volat kdykoli.

Funkce spotřebovává znaky v oblasti put `pbase` mezi `pptr` a ukazatele a potom znovu inicializuje put oblasti. Funkce `overflow` musí také `nCh` spotřebovat `nCh` `EOF`(pokud není ), nebo může zvolit, aby tento znak v nové oblasti put tak, aby byly spotřebovány při dalším volání.

Definice spotřebovávat se liší mezi odvozené třídy. Například `filebuf` třída zapíše své znaky do `strstreambuf` souboru, zatímco třída je udržuje ve vyrovnávací paměti a (pokud je vyrovnávací paměť označena jako dynamická) rozšiřuje vyrovnávací paměť v reakci na volání k přetečení. Tohoto rozšíření je dosaženo uvolněním staré vyrovnávací paměti a jeho nahrazením novým, větším. Ukazatele jsou podle potřeby upraveny.

## <a name="basic_streambufpbackfail"></a><a name="pbackfail"></a>basic_streambuf::pbackfail

Chráněná virtuální členská funkce, která se pokusí vrátit prvek zpět do vstupního datového proudu, pak z něj udělejte aktuální prvek (na který odkazuje další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, který chcete vložit do vyrovnávací paměti nebo **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof** nebo vyvolá výjimku. V opačném případě vrátí některé jiné hodnoty. Výchozí chování je vrátit **traits_type::eof**.

### <a name="remarks"></a>Poznámky

Pokud * \_Meta* porovná rovná **traits_type::eof**, prvek push back je efektivně jeden již v datovém proudu před aktuální prvek. V opačném případě se tento prvek nahradí **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*). Funkce může vrátit prvek různými způsoby:

- Pokud putback pozice je k dispozici, může uložit prvek do putback pozice a snížení další ukazatel pro vstupní vyrovnávací paměti.

- Může zpřístupnit pozici putback přidělením nového nebo dalšího úložiště pro vstupní vyrovnávací paměť.

- Pro vyrovnávací paměť datového proudu s běžnými vstupními a výstupními datovými proudy může zpřístupnit pozici putback zápisem do některého externího cíle některé nebo všechny prvky mezi počáteční a další ukazatele pro výstupní vyrovnávací paměť.

## <a name="basic_streambufpbase"></a><a name="pbase"></a>basic_streambuf::pzákladna

Chráněná funkce, která vrací ukazatel na začátek výstupní vyrovnávací paměti.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátek výstupní vyrovnávací paměti.

## <a name="basic_streambufpbump"></a><a name="pbump"></a>basic_streambuf::pbump

Chráněná funkce, která přidá *počet* k dalšímu ukazateli pro výstupní vyrovnávací paměť.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet znaků, o které chcete přesunout pozici zápisu dopředu.

## <a name="basic_streambufpos_type"></a><a name="pos_type"></a>basic_streambuf::pos_type

Přidruží název typu v rámci basic_streambuf oboru k jednomu z typů v parametru šablony.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_streambufpptr"></a><a name="pptr"></a>basic_streambuf::pptr

Chráněná funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměti.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další prvek výstupní vyrovnávací paměti.

## <a name="basic_streambufpubimbue"></a><a name="pubimbue"></a>basic_streambuf::pubimbue

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

Členská funkce ukládá _ *Loc* v objektu národního prostředí a volání [imbue](#imbue).

### <a name="example"></a>Příklad

Viz [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) pro příklad, který používá `pubimbue`.

## <a name="basic_streambufpubseekoff"></a><a name="pubseekoff"></a>basic_streambuf::pubseekoff

Volání [seekoff](#seekoff), chráněné virtuální funkce, která je přepsána v odvozené třídě.

```cpp
pos_type pubseekoff(off_type _Off,
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

Vrátí novou pozici nebo neplatnou pozici datového `_Way` `_Which`proudu ( [seekoff](#seekoff)(_ *Off*, ), ).

### <a name="remarks"></a>Poznámky

Přesune ukazatel vzhledem k *_Way*.

## <a name="basic_streambufpubseekpos"></a><a name="pubseekpos"></a>basic_streambuf::pubseekpos

Volání [seekpos](#seekpos), chráněné virtuální funkce, která je přepsána v odvozené třídě a obnoví aktuální pozici ukazatele.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice, o kterou se můžete snažit.

*_Which*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Nová pozice nebo neplatná pozice datového proudu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [seekpos](#seekpos) `_Which`(_ *Sp*, ).

## <a name="basic_streambufpubsetbuf"></a><a name="pubsetbuf"></a>basic_streambuf::pubsetbuf

Volání [setbuf](#setbuf), chráněné virtuální funkce, která je přepsána v odvozené třídě.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Ukazatel pro `char_type` tuto inkoniaci.

*Počet*\
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí [setbuf](#setbuf)( `_Buffer`, `count`).

## <a name="basic_streambufpubsync"></a><a name="pubsync"></a>basic_streambuf::pubsync

Volání [synchronizace](#sync), chráněné virtuální funkce, která je přepsána v odvozené třídě a aktualizuje externí datový proud přidružený k této vyrovnávací paměti.

```cpp
int pubsync();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [synchronizaci](#sync) nebo -1 v případě selhání.

## <a name="basic_streambufsbumpc"></a><a name="sbumpc"></a>basic_streambuf::sbumpc

Přečte a vrátí aktuální prvek přesunutím ukazatele datového proudu.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici pozice pro čtení, vrátí <strong>\*</strong>členská funkce **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( [gptr](#gptr)) a nastaví další ukazatel pro vstupní vyrovnávací paměť. V opačném případě vrátí [uflow](#uflow).

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

## <a name="basic_streambufseekoff"></a><a name="seekoff"></a>basic_streambuf::seekoff

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.

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

Vrátí novou pozici nebo neplatnou pozici datového `seekoff` proudu ( (_ *Vypnuto*, `_Way`), `_Which`).

### <a name="remarks"></a>Poznámky

Nová pozice je určena takto:

- `_Way`  == Pokud `ios_base::beg`je nová pozice začátkem datového proudu plus _ *Off*.

- `_Way`  == Pokud `ios_base::cur`je nová pozice aktuální pozice datového proudu plus _ *Vypnuto*.

- `_Way`  == Pokud `ios_base::end`je nová pozice koncem datového proudu plus _ *Off*.

Obvykle, **pokud, které & ios_base::in** je nenulová, vstupní datový proud je ovlivněna a pokud **které & ios_base::out** je nenulová, výstupní datový proud je ovlivněna. Skutečné použití tohoto parametru se však u odvozených vyrovnávacích pamětí datového proudu liší.

Pokud funkce uspěje při změně pozice datového proudu nebo pozice, vrátí výslednou pozici datového proudu nebo jednu z výsledných pozic datového proudu. V opačném případě vrátí pozici neplatného datového proudu. Výchozí chování je vrátit neplatné pozice datového proudu.

## <a name="basic_streambufseekpos"></a><a name="seekpos"></a>basic_streambuf::seekpos

Chráněná virtuální členská funkce, která se pokusí změnit aktuální pozice pro řízené datové proudy.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozice, o kterou se můžete snažit.

*_Which*\
Určuje režim pro polohu ukazatele. Ve výchozím nastavení je umožnit úpravu pozic pro čtení a zápis.

### <a name="return-value"></a>Návratová hodnota

Nová pozice nebo neplatná pozice datového proudu. Chcete-li zjistit, zda je pozice datového proudu neplatná, porovnejte vrácenou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Nová pozice je _ *Sp*.

Obvykle, **pokud, které & ios_base::in** je nenulová, vstupní datový proud je ovlivněna a pokud **které & ios_base::out** je nenulová, výstupní datový proud je ovlivněna. Skutečné použití tohoto parametru se však u odvozených vyrovnávacích pamětí datového proudu liší.

Pokud funkce uspěje při změně pozice datového proudu nebo pozice, vrátí výslednou pozici datového proudu nebo jednu z výsledných pozic datového proudu. V opačném případě vrátí neplatný datový proud pozice (-1). Výchozí chování je vrátit neplatné pozice datového proudu.

## <a name="basic_streambufsetbuf"></a><a name="setbuf"></a>basic_streambuf::setbuf

Chráněná virtuální členská funkce, která provádí konkrétní operaci pro každou vyrovnávací paměť odvozeného datového proudu.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Ukazatel na vyrovnávací paměť.

*Počet*\
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Výchozí chování je vrátit **toto**.

### <a name="remarks"></a>Poznámky

Viz [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf`poskytuje oblast paměti pro `streambuf` objekt k použití. Jak se vyrovnávací paměť používá v definované v odvozené třídy.

## <a name="basic_streambufsetg"></a><a name="setg"></a>basic_streambuf::setg

Chráněná funkce, která ukládá _ *Gbeg* v počátečníukazatel, `_Gnext` v dalším ukazateli a `_Gend` v ukazateli na konci pro vstupní vyrovnávací paměť.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parametry

*_Gbeg*\
Ukazatel na začátek vyrovnávací paměti.

*_Gnext*\
Ukazatel někde uprostřed vyrovnávací paměti.

*_Gend*\
Ukazatel na konec vyrovnávací paměti.

## <a name="basic_streambufsetp"></a><a name="setp"></a>basic_streambuf::setp

Chráněná funkce, která ukládá *_Pbeg* v počátečníukazatel a *_Pend* v ukazatel i koncový ukazatel pro výstupní vyrovnávací paměti.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parametry

*_Pbeg*\
Ukazatel na začátek vyrovnávací paměti.

*_Pend*\
Ukazatel na konec vyrovnávací paměti.

## <a name="basic_streambufsgetc"></a><a name="sgetc"></a>basic_streambuf::sgetc

Vrátí aktuální prvek bez změny polohy v datovém proudu.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici pozice pro čtení, vrátí `*`členská funkce **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( [gptr](#gptr)). V opačném případě vrátí [podtečení](#underflow).

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

## <a name="basic_streambufsgetn"></a><a name="sgetn"></a>basic_streambuf::sgetn

Extrahuje *se,* aby se počítaly znaky ze vstupní vyrovnávací paměti a ukládá je do zadané vyrovnávací paměti *ptr*.

Tato metoda je potenciálně nebezpečné, protože spoléhá na volajícího zkontrolovat, že předané hodnoty jsou správné.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Vyrovnávací paměť obsahující extrahované znaky.

*Počet*\
Počet prvků ke čtení.

### <a name="return-value"></a>Návratová hodnota

Počet prvků číst. Další informace najdete v [tématu velikost datového](../standard-library/ios-typedefs.md#streamsize) proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [hodnotu xsgetn](#xsgetn)( `ptr`, `count`).

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

## <a name="basic_streambufshowmanyc"></a><a name="showmanyc"></a>basic_streambuf::showmanyc

Chráněná virtuální členská funkce, která vrací počet znaků, které lze extrahovat ze vstupního datového proudu, a zajišťuje, že program nebude podléhat neurčitému čekání.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí chování je vrátit nulu.

## <a name="basic_streambufsnextc"></a><a name="snextc"></a>basic_streambuf::snextc

Přečte aktuální prvek a vrátí následující prvek.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Návratová hodnota

Další prvek v datovém proudu.

### <a name="remarks"></a>Poznámky

Členská funkce volá [sbumpc](#sbumpc) a pokud tato funkce vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), vrátí **traits_type::eof**. V opačném případě vrátí [sgetc](#sgetc).

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

## <a name="basic_streambufsputbackc"></a><a name="sputbackc"></a>basic_streambuf::sputbackc

Vloží char_type do datového proudu.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Postava.

### <a name="return-value"></a>Návratová hodnota

Vrátí znak nebo selhání.

### <a name="remarks"></a>Poznámky

Pokud putback pozice je k dispozici a *_Ch* porovná rovná znak uložený v této pozici, členská funkce sníží další `_Ch`ukazatel pro vstupní vyrovnávací paměti a vrátí **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( ). V opačném případě vrátí `_Ch` [pbackfail](#pbackfail)( ).

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

## <a name="basic_streambufsputc"></a><a name="sputc"></a>basic_streambuf::sputc

Vloží znak do datového proudu.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Postava.

### <a name="return-value"></a>Návratová hodnota

Vrátí znak, pokud je úspěšný.

### <a name="remarks"></a>Poznámky

Pokud `write position` je k dispozici a, členská funkce ukládá *_Ch* v pozici zápisu, zintáží `_Ch`další ukazatel výstupní vyrovnávací paměti a vrátí **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( ). V opačném případě vrátí `_Ch` [přetečení](#overflow)( ).

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

## <a name="basic_streambufsputn"></a><a name="sputn"></a>basic_streambuf::sputn

Vloží řetězec znaků do datového proudu.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Řetězec znaků.

*Počet*\
Počet znaků.

### <a name="return-value"></a>Návratová hodnota

Počet znaků skutečně vložendo datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [hodnotu xsputn](#xsputn)( `ptr`, `count`). Další informace naleznete v části Poznámky tohoto člena.

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

## <a name="basic_streambufstossc"></a><a name="stossc"></a>basic_streambuf::stossc

Přesuňte se za aktuální prvek v datovém proudu.

```cpp
void stossc();
```

### <a name="remarks"></a>Poznámky

Členská funkce volá [sbumpc](#sbumpc). Všimněte si, že implementace není nutné zadat tuto člennou funkci.

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

## <a name="basic_streambufsungetc"></a><a name="sungetc"></a>basic_streambuf::sungetc

Získá znak z datového proudu.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí znak nebo selhání.

### <a name="remarks"></a>Poznámky

Pokud putback pozice je k dispozici, členská funkce sníží další ukazatel `traits_type::`pro `*`vstupní vyrovnávací paměti a vrátí [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( [gptr](#gptr)). Není však vždy možné určit poslední znak číst tak, aby jej lze zachytit ve stavu aktuální vyrovnávací paměti. Pokud je to pravda, funkce vrátí [pbackfail](#pbackfail). Chcete-li se této situaci vyhnout, sledujte `sputbackc(ch)`znak, který má být odložen a volán , což se nenezdaří, pokud jej nezavoláte na začátku datového proudu a nepokusíte se vrátit více než jeden znak.

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

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::swap

Vymění hodnoty v tomto objektu za `basic_streambuf` hodnoty v zadaný objekt.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Právo*|Lvalue odkaz na `basic_streambuf` objekt, který se používá k výměně hodnot.|

### <a name="remarks"></a>Poznámky

Chráněná členská funkce výměny s *právem* všechny ukazatele ovládání `input buffer` a `output buffer`. Také výměny `right.` [getloc()](#getloc) `locale` s objektem.

## <a name="basic_streambufsync"></a><a name="sync"></a>basic_streambuf::synchronizace

Chráněná virtuální funkce, která se pokusí synchronizovat řízené datové proudy se všemi přidruženými externími datovými proudy.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí hodnotu -1. Výchozí chování je vrátit nulu.

### <a name="remarks"></a>Poznámky

`sync`zahrnuje zápis všechny prvky mezi začátku a další ukazatele pro výstupní vyrovnávací paměti. Nezahrnuje vrácení všech prvků mezi další a koncové ukazatele pro vstupní vyrovnávací paměť.

## <a name="basic_streambuftraits_type"></a><a name="traits_type"></a>basic_streambuf::traits_type

Přidruží název typu k parametru šablony **Tr.**

```cpp
typedef Tr traits_type;
```

## <a name="basic_streambufuflow"></a><a name="uflow"></a>basic_streambuf::uflow

Chráněná virtuální funkce, která extrahuje aktuální prvek ze vstupního datového proudu.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí extrahovat aktuální prvek **ch** ze vstupního datového proudu, potom posunout aktuální pozici datového proudu a vrátit prvek jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Může tak učinit různými způsoby:

- Pokud je k dispozici pozice pro čtení, trvá **ch** jako prvek uložený v pozici pro čtení a posune další ukazatel pro vstupní vyrovnávací paměti.

- Může číst prvek přímo z některého externího zdroje a doručit jej jako hodnotu **ch**.

- Pro vyrovnávací paměť datového proudu s běžnými vstupními a výstupními datovými proudy může zpřístupnit pozici pro čtení zápisem do některého externího cíle některé nebo všechny prvky mezi počáteční a další ukazatele pro výstupní vyrovnávací paměti. Nebo může přidělit nové nebo další úložiště pro vstupní vyrovnávací paměť. Funkce pak čte v, z některého externího zdroje, jeden nebo více prvků.

Pokud funkce nemůže být úspěšná, vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)nebo vyvolá výjimku. V opačném případě vrátí `ch` aktuální prvek ve vstupním datovém proudu, převedený, jak je popsáno výše, a posune další ukazatel pro vstupní vyrovnávací paměť. Výchozí chování je volání [podtečení](#underflow) a pokud tato funkce vrátí **traits_type::eof**, vrátit **traits_type::eof**. Jinak funkce vrátí aktuální prvek **ch** ve vstupním datovém proudu, převedený, jak bylo popsáno dříve, a posune další ukazatel pro vstupní vyrovnávací paměť.

## <a name="basic_streambufunderflow"></a><a name="underflow"></a>basic_streambuf::podtočení

Chráněné, virtuální funkce extrahovat aktuální prvek ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální prvek.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se snaží extrahovat aktuální prvek **ch** ze vstupního datového proudu, aniž by došlo k posunu aktuální pozice datového proudu, a vrátit jej jako `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type) **(ch**). Může tak učinit různými způsoby:

- Pokud je k dispozici pozice pro čtení, **ch** je prvek uložený v pozici pro čtení. Další informace naleznete v části Poznámky [třídy basic_streambuf .](../standard-library/basic-streambuf-class.md)

- Může zpřístupnit pozici pro čtení přidělením nového nebo dalšího úložiště pro vstupní vyrovnávací paměť a čtením z některého externího zdroje z jednoho nebo více prvků. Další informace naleznete v části Poznámky [třídy basic_streambuf .](../standard-library/basic-streambuf-class.md)

Pokud funkce nemůže být `traits_type::`úspěšná, vrátí [eof](../standard-library/char-traits-struct.md#eof) `()` nebo vyvolá výjimku. V opačném případě vrátí aktuální prvek ve vstupním datovém proudu, převedený, jak bylo popsáno dříve. Výchozí chování je `traits_type::eof()`vrátit .

Virtuální `underflow` funkce s funkcemi [synchronizace](#sync) a [přetečení](#overflow) `streambuf`definuje charakteristiky -derived třídy. Každá odvozená třída `underflow` může implementovat jinak, ale rozhraní s volající stream třídy je stejný.

Funkce `underflow` je nejčastěji volána `streambuf` veřejnými funkcemi, jako je [sgetc](#sgetc) a [sgetn,](#sgetn) když je `underflow` oblast get prázdná, ale jiné třídy, včetně tříd datového proudu, mohou volat kdykoli.

Funkce `underflow` dodává oblast get se znaky ze vstupního zdroje. Pokud oblast get obsahuje `underflow` znaky, vrátí první znak. Pokud je oblast get prázdná, vyplní oblast get a vrátí další znak (který opustí v oblasti get). Pokud nejsou k dispozici žádné `underflow` `EOF` další znaky, vrátí se a ponechá oblast get prázdnou.

Ve `strstreambuf` třídě `underflow` upraví ukazatel [egptr](#egptr) pro přístup k úložišti, který `overflow`byl dynamicky přidělen voláním .

## <a name="basic_streambufxsgetn"></a><a name="xsgetn"></a>basic_streambuf::xsgetn

Chráněné, virtuální funkce extrahovat prvky ze vstupního datového proudu.

Tato metoda je potenciálně nebezpečné, protože spoléhá na volajícího zkontrolovat, že předané hodnoty jsou správné.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Vyrovnávací paměť obsahující extrahované znaky.

*Počet*\
Počet prvků extrahovat.

### <a name="return-value"></a>Návratová hodnota

Počet extrahovaných prvků.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce extrahuje až *počítat* prvky ze vstupního datového proudu, jako by opakovanými [voláními sbumpc](#sbumpc)a ukládá je do pole začínající na *ptr*. Vrátí počet prvků skutečně extrahované.

## <a name="basic_streambufxsputn"></a><a name="xsputn"></a>basic_streambuf::xsputn

Chráněná, virtuální funkce pro vložení prvků do výstupního datového proudu.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Ukazatel na prvky vložit.

*Počet*\
Počet prvků, které chcete vložit.

### <a name="return-value"></a>Návratová hodnota

Počet prvků skutečně vložendo datového proudu.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vloží *až* počet prvků do výstupního datového proudu, jako by opakovanými [voláními sputc](#sputc), z pole začínajícího na *ptr*. Vkládání znaků do výstupního datového proudu *count* se zastaví, jakmile byly `sputc( count)` zapsány všechny znaky počtu nebo pokud by se volání vrátilo `traits::eof()`. Vrátí počet prvků skutečně vložených.

## <a name="see-also"></a>Viz také

[Bezpečnost vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[programování iostreamu](../standard-library/iostream-programming.md)\
[iostreams úmluvy](../standard-library/iostreams-conventions.md)
