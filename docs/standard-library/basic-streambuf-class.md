---
title: basic_streambuf – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bc4fa8da5d9fa2d15febc3c7b016622e614129a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100960"
---
# <a name="basicstreambuf-class"></a>basic_streambuf – třída

Popisuje abstraktní základní třída pro odvození vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z konkrétní reprezentace datového proudu.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
A [char_type](#char_type).

*tr*<br/>
Znak [traits_type](#traits_type).

## <a name="remarks"></a>Poznámky

Třída šablony popisuje abstraktní základní třída pro odvození vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z konkrétní reprezentace datového proudu. Objekt třídy `basic_streambuf` pomáhá řídit datový proud s prvky typu *Tr*, označované také jako [char_type](#char_type), jehož vlastnosti znaků určuje třídu [char_traits](../standard-library/char-traits-struct.md), označované také jako [traits_type](#traits_type).

Každý datový proud vyrovnávací paměti koncepčně řídí dvě streamy: jeden pro extrakce (vstup) a jeden pro vložení (výstup). Konkrétní reprezentace mohou, ale vytvořit jeden nebo oba z těchto datových proudů nepřístupný. Obvykle udržuje některé vztah mezi dvěma datovými proudy. Vložit do výstupního datového proudu [basic_stringbuf –](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> objekt, je třeba, co je později extrahovat z jeho vstupního datového proudu. Při umístění jeden datový proud [basic_filebuf –](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> objekt, umístěte jiný datový proud současně.

Veřejné rozhraní třídy šablony `basic_streambuf` poskytuje operace, které jsou společné pro všechny vyrovnávací paměť datového proudu, ale specializovaný. Chráněné rozhraní poskytuje operace nutné pro konkrétní reprezentace datového proudu ke své práci. Chráněná virtuální členská funkce umožňují přizpůsobit chování odvozené datový proud vyrovnávací paměti pro konkrétní reprezentace datového proudu. Každé odvozené datový proud vyrovnávací paměti v této knihovně popisuje, jak se specializuje chování jeho chráněná virtuální členská funkce. Výchozí chování pro základní třídu, která je často Neprovádět žádnou akci, je popsaný v tomto tématu.

Zbývající chráněné členské funkce ovládacího prvku kopírování do a z jakékoli úložiště, zadaný do vyrovnávací paměti přenosů do a z datových proudů. Vstupní vyrovnávací paměť, je třeba charakterizují ji:

- [eback –](#eback), ukazatel na začátek vyrovnávací paměti.

- [gptr –](#gptr), ukazatel na další prvek ke čtení.

- [egptr –](#egptr), ukazatel právě za koncem vyrovnávací paměti.

Podobně je výstupní mezipaměti charakteristické:

- [pbase –](#pbase), ukazatel na začátek vyrovnávací paměti.

- [pptr –](#pptr), ukazatel na další prvek k zápisu.

- [epptr –](#epptr), ukazatel právě za koncem vyrovnávací paměti.

Pro všechny vyrovnávací paměť používá následující protokol:

- Je-li další ukazatel null, neexistuje žádný vyrovnávací paměti. Všechny tři ukazatele v opačném případě přejděte do stejné pořadí. Můžete bezpečně neporovnávají objednávky.

- Pro výstupní mezipaměti Porovná další ukazatel menší než koncový ukazatel, můžete uložit element na pozici zápisu určené další ukazatel.

- Pro vstupní vyrovnávací paměť Porovná další ukazatel menší než koncový ukazatel, můžete číst prvek na pozici pro čtení uvedených další ukazatel.

- Vstupní vyrovnávací paměti Pokud ukazatel na začátku porovnává méně než ukazatel next můžete vložit zpět element na pozici putback – určeno snížen další ukazatel.

Všechny chráněné virtuální členské funkce zápisu pro třídu odvozenou z `basic_streambuf` <  `Elem`, `Tr`> musí spolupracovat při zachování tohoto protokolu.

Objekt třídy `basic_streambuf` <  `Elem`, `Tr`> ukládá šest ukazatele popsaných výše. Také ukládá objekt národního prostředí v objektu typu [národní prostředí](../standard-library/locale-class.md) potenciální používají vyrovnávací paměť datového proudu odvozený.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[basic_streambuf](#basic_streambuf)|Vytvoří objekt typu `basic_streambuf`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Přidruží název typu se `Elem` parametr šablony.|
|[int_type](#int_type)|Přidruží název typu v rámci `basic_streambuf` oboru s `Elem` parametr šablony.|
|[off_type](#off_type)|Přidruží název typu v rámci `basic_streambuf` oboru s `Elem` parametr šablony.|
|[pos_type](#pos_type)|Přidruží název typu v rámci `basic_streambuf` oboru s `Elem` parametr šablony.|
|[traits_type](#traits_type)|Přidruží název typu se `Tr` parametr šablony.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[eback –](#eback)|Chráněné funkce, která vrací ukazatel na začátku vstupní vyrovnávací paměť.|
|[egptr –](#egptr)|Chráněné funkce vracející ukazatel právě za koncem vstupní vyrovnávací paměť.|
|[epptr –](#epptr)|Chráněné funkce, která vrací ukazatel právě za koncem výstupní vyrovnávací paměť.|
|[gbump –](#gbump)|Chráněné funkce, která přidá `count` další ukazatele pro vstupní vyrovnávací paměť.|
|[getloc –](#getloc)|Získá `basic_streambuf` objektu národního prostředí.|
|[gptr –](#gptr)|Chráněné funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměť.|
|[imbue –](#imbue)|Chráněná, virtuální funkce volány [pubimbue –](#pubimbue).|
|[in_avail –](#in_avail)|Vrátí počet prvků, které jsou připravené ke čtení z vyrovnávací paměti.|
|[přetečení](#overflow)|Chráněné virtuální funkce, která může být volána při vložení nového znaku do plné vyrovnávací paměti.|
|[pbackfail –](#pbackfail)|Chráněná virtuální členská funkce, který se pokusí vrátit elementu do vstupního datového proudu, a pak si všechno aktuálního elementu (ukazuje další ukazatel).|
|[pbase](#pbase)|Chráněné funkce, která vrací ukazatel na začátku výstupní vyrovnávací paměť.|
|[pbump –](#pbump)|Chráněné funkce, která přidá `count` další ukazatele pro výstupní vyrovnávací paměť.|
|[pptr](#pptr)|Chráněné funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměť.|
|[pubimbue –](#pubimbue)|Nastaví `basic_streambuf` objektu národního prostředí.|
|[pubseekoff –](#pubseekoff)|Volání [seekoff –](#seekoff), chránit virtuální funkce, která je přepsání v odvozené třídě.|
|[pubseekpos –](#pubseekpos)|Volání [seekpos –](#seekpos), chránit virtuální funkce, která je přepsání v odvozené třídě a obnoví aktuální pozici ukazatele.|
|[pubsetbuf](#pubsetbuf)|Volání [setbuf –](#setbuf), chránit virtuální funkce, která je přepsání v odvozené třídě.|
|[pubsync](#pubsync)|Volání [synchronizace](#sync), chránit virtuální funkce, která je přepsání v odvozené třídě a aktualizuje externí datový proud přidružený k této vyrovnávací paměti.|
|[sbumpc –](#sbumpc)|Přečte a vrátí aktuální prvek ukazatele datového proudu.|
|[seekoff –](#seekoff)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.|
|[seekpos –](#seekpos)|Chráněná virtuální členská funkce se pokusí změnit aktuální pozice řízené datových proudů.|
|[setbuf](#setbuf)|Chráněná virtuální členská funkce se provede konkrétní operace pro každou odvozené datový proud vyrovnávací paměti.|
|[setg –](#setg)|Do chráněné funkce, která ukládá `_Gbeg` v ukazateli začátek `_Gnext` v další ukazatele a `_Gend` v koncový ukazatel pro vstupní vyrovnávací paměť.|
|[setp –](#setp)|Do chráněné funkce, která ukládá `_Pbeg` v ukazateli na začátku a `_Pend` v koncový ukazatel do vyrovnávací paměti výstupních.|
|[sgetc –](#sgetc)|Vrátí aktuální prvek beze změny pozice v proudu.|
|[sgetn](#sgetn)|Vrátí počet prvků číst.|
|[showmanyc –](#showmanyc)|Chráněná virtuální členská funkce, která vrátí počet znaků, které může být extrahována ze vstupního datového proudu a ujistěte se, že program nebude podléhat neomezené čekání.|
|[snextc](#snextc)|Načte aktuální prvek a vrátí následující element.|
|[sputbackc](#sputbackc)|Vloží `char_type` v datovém proudu.|
|[sputc –](#sputc)|Vloží znak do datového proudu.|
|[sputn –](#sputn)|Převede řetězec znaků do datového proudu.|
|[stossc –](#stossc)|Přesunout za aktuální prvek v datovém proudu.|
|[sungetc –](#sungetc)|Získá znak z datového proudu.|
|[Prohození](#swap)|Vymění hodnoty v tomto objektu pro hodnoty v zadaných `basic_streambuf` parametru objektu.|
|[sync](#sync)|Chráněné virtuální funkce, který se pokouší synchronizovat řízené datové proudy s jakékoli přidružené externích datových proudů.|
|[uflow –](#uflow)|Chráněné virtuální funkce, která extrahuje aktuálního elementu ze vstupního datového proudu.|
|[podtečení](#underflow)|Chráněné virtuální funkce, která extrahuje aktuálního elementu ze vstupního datového proudu.|
|[xsgetn](#xsgetn)|Chráněné virtuální funkce, která extrahuje prvky ze vstupního datového proudu.|
|[xsputn –](#xsputn)|Chráněné virtuální funkce, která vloží prvky do výstupního datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Přiřadí hodnoty tohoto objektu z jiného `basic_streambuf` objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<streambuf – >

**Namespace:** std

## <a name="basic_streambuf"></a>  basic_streambuf::basic_streambuf

Vytvoří objekt typu `basic_streambuf`.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Odkaz na lvalue k `basic_streambuf` objekt, který slouží k nastavení hodnot pro tento `basic_streambuf` objektu.

### <a name="remarks"></a>Poznámky

První chráněný konstruktor uloží ukazatel s hodnotou null v všechny ukazatele řízení vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Také ukládá `locale::classic` v objektu národního prostředí. Další informace najdete v tématu [locale::classic](../standard-library/locale-class.md#classic).

Druhý konstruktor chráněný zkopíruje ukazatele a národní prostředí z *správné*.

## <a name="char_type"></a>  basic_streambuf::char_type

Přidruží název typu se **Elem** parametr šablony.

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>  basic_streambuf::eback

Chráněné funkce, která vrací ukazatel na začátku vstupní vyrovnávací paměť.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátku vstupní vyrovnávací paměť.

## <a name="egptr"></a>  basic_streambuf::egptr

Chráněné funkce vracející ukazatel právě za koncem vstupní vyrovnávací paměť.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel právě za koncem vstupní vyrovnávací paměť.

## <a name="epptr"></a>  basic_streambuf::epptr

Chráněné funkce, která vrací ukazatel právě za koncem výstupní vyrovnávací paměť.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel právě za koncem výstupní vyrovnávací paměť.

## <a name="gbump"></a>  basic_streambuf::gbump

Chráněné funkce, která přidá *počet* další ukazatele pro vstupní vyrovnávací paměť.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parametry

*Počet*<br/>
Rozsah, pomocí kterého přejdete ukazatel.

## <a name="getloc"></a>  basic_streambuf::getloc

Získá objekt basic_streambuf národní prostředí.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt, který uloženého národního prostředí.

### <a name="remarks"></a>Poznámky

Související informace naleznete v tématu [ios_base::getloc](../standard-library/ios-base-class.md#getloc).

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

## <a name="gptr"></a>  basic_streambuf::gptr

Chráněné funkce, která vrací ukazatel na další prvek vstupní vyrovnávací paměť.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další prvek vstupní vyrovnávací paměť.

## <a name="imbue"></a>  basic_streambuf::imbue

Chráněná virtuální funkce volány [pubimbue –](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*<br/>
Odkaz na národním prostředí.

### <a name="remarks"></a>Poznámky

Výchozí chování je Neprovádět žádnou akci.

## <a name="in_avail"></a>  basic_streambuf::in_avail

Vrátí počet prvků, které jsou připravené ke čtení z vyrovnávací paměti.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které jsou připravené ke čtení z vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Pokud [čtení pozice](../standard-library/basic-streambuf-class.md) je k dispozici, členská funkce vrátí [egptr –](#egptr) - [gptr –](#gptr). V opačném případě vrátí [showmanyc –](#showmanyc).

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

## <a name="int_type"></a>  basic_streambuf::int_type

Název typu v rámci oboru basic_streambuf přidruží jeden z typů v parametru šablony.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_streambuf::off_type

Název typu v rámci oboru basic_streambuf přidruží jeden z typů v parametru šablony.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>  basic_streambuf::Operator =

Přiřadí hodnoty tohoto objektu z jiného `basic_streambuf` objektu.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Odkaz na lvalue k `basic_streambuf` objekt, který slouží k přiřazení hodnoty k tomuto objektu.

### <a name="remarks"></a>Poznámky

Operátor chráněný člen zkopíruje z *správné* ukazatele, které určují vstupní vyrovnávací paměť a výstupní vyrovnávací paměť. Také ukládá `right.` [getloc()](#getloc) v `locale object`. Vrátí `*this`.

## <a name="overflow"></a>  basic_streambuf::Overflow

Chráněné virtuální funkce, která může být volána při vložení nového znaku do plné vyrovnávací paměti.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti, nebo **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof** nebo vyvolá výjimku. V opačném případě vrátí **traits_type::**[not_eof –](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). Výchozím chováním **traits_type::eof**.

### <a name="remarks"></a>Poznámky

Pokud _ *Meta* není výsledkem porovnání **traits_type::eof**, chcete-li vložit element endeavors chráněná virtuální členská funkce **traits_type::**[k_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) do výstupního datového proudu. To lze provést různými způsoby:

- Pokud `write position` je k dispozici, může ukládat element na pozici zápisu a zvýšit další ukazatele pro výstupní vyrovnávací paměť.

- To může zpřístupnit pozici zápisu přidělením nové nebo další úložiště pro výstupní vyrovnávací paměť.

- To můžete zpřístupnit pozici zápisu psaní navýšení kapacity, některé externí cílové, některé nebo všechny prvky mezi začátky a další ukazatele pro výstupní vyrovnávací paměť.

Funkce virtuální přetečení, společně s [synchronizace](#sync) a [podtečení](#underflow) funkce, určuje charakteristiky streambuf – odvozené třídy. Každá odvozená třída může implementovat přetečení jinak, ale rozhraní se volání třídy datového proudu je stejný.

`overflow` Nejčastěji volána veřejností `streambuf` funkce jako `sputc` a `sputn` při vložení oblast je plná, ale můžete volat jiné třídy, včetně tříd stream `overflow` kdykoli.

Funkce využívá znaky v oblasti put mezi `pbase` a `pptr` ukazatele a pak znovu inicializuje oblasti put. `overflow` Musí také využívat funkce `nCh` (Pokud `nCh` není `EOF`), nebo se rozhodnout, že chcete změnit, vložit znak v nové oblasti tak, aby se bude spotřebovávat na další volání.

Definice využívání liší odvozené třídy. Například `filebuf` třídy zapíše jeho znaky do souboru, zatímco `strstreambuf` třídy zůstanou ve vyrovnávací paměti a (Pokud je vyrovnávací paměť je označen jako dynamické) rozbalí v reakci na hovor přetečení vyrovnávací paměti. Toto rozšíření se dosahuje prostřednictvím uvolnění vyrovnávací paměť původního a jeho nahrazení atributem nové, větší jeden. Ukazatelů jsou upravena podle potřeby.

## <a name="pbackfail"></a>  basic_streambuf::pbackfail

Chráněná virtuální členská funkce, který se pokusí vrátit elementu do vstupního datového proudu, a pak si všechno aktuálního elementu (ukazuje další ukazatel).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak k vložení do vyrovnávací paměti, nebo **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí **traits_type::eof** nebo vyvolá výjimku. V opačném případě vrátí jinou hodnotu. Výchozím chováním **traits_type::eof**.

### <a name="remarks"></a>Poznámky

Pokud _ *Meta* porovná rovno **traits_type::eof**, elementu, který chcete vložit zpět je v podstatě je již ve službě stream před aktuální prvek. V opačném případě se nahrazuje tento prvek **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Funkci lze vrátit zpět element různými způsoby:

- Pokud putback – pozice je k dispozici, můžete uložit prvek na místo putback – a snížení další ukazatele pro vstupní vyrovnávací paměť.

- To může zpřístupnit putback – pozice přidělením nové nebo další úložiště pro vstupní vyrovnávací paměť.

- Pro vyrovnávací paměť datového proudu s společné vstupní a výstupní datové proudy ho můžete zpřístupnit putback – pozice psaní navýšení kapacity, některé externí cílové, některé nebo všechny prvky mezi začátky a další ukazatele pro výstupní vyrovnávací paměť.

## <a name="pbase"></a>  basic_streambuf::pbase

Chráněné funkce, která vrací ukazatel na začátku výstupní vyrovnávací paměť.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na začátku výstupní vyrovnávací paměť.

## <a name="pbump"></a>  basic_streambuf::pbump

Chráněné funkce, která přidá *počet* další ukazatele pro výstupní vyrovnávací paměť.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parametry

*Počet*<br/>
Počet znaků, o které se má posunout vpřed pozici pro zápis.

## <a name="pos_type"></a>  basic_streambuf::pos_type

Název typu v rámci oboru basic_streambuf přidruží jeden z typů v parametru šablony.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>  basic_streambuf::pptr

Chráněné funkce, která vrací ukazatel na další prvek výstupní vyrovnávací paměť.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na další prvek výstupní vyrovnávací paměť.

## <a name="pubimbue"></a>  basic_streambuf::pubimbue

Nastaví národní prostředí basic_streambuf objektu.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*<br/>
Odkaz na národním prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnotu uloženou v objektu národního prostředí.

### <a name="remarks"></a>Poznámky

Členská funkce ukládá _ *Loc* objekt národního prostředí a volání [imbue –](#imbue).

### <a name="example"></a>Příklad

Zobrazit [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) příklad, který používá `pubimbue`.

## <a name="pubseekoff"></a>  basic_streambuf::pubseekoff

Volání [seekoff –](#seekoff), chránit virtuální funkce, která je přepsání v odvozené třídě.

```cpp
pos_type pubseekoff(off_type _Off,
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

Vrátí novou pozici nebo pozice neplatný datový proud ( [seekoff –](#seekoff)(_ *vypnout*, `_Way`, `_Which`)).

### <a name="remarks"></a>Poznámky

Přesune ukazatel vzhledem k *_Way*.

## <a name="pubseekpos"></a>  basic_streambuf::pubseekpos

Volání [seekpos –](#seekpos), chránit virtuální funkce, která je přepsání v odvozené třídě a obnoví aktuální pozici ukazatele.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Pozice k vyhledání pro.

*_Which*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Nové umístění nebo umístění neplatný datový proud. Chcete-li zjistit, zda pozici v datovém proudu je neplatný, porovnejte návratovou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [seekpos –](#seekpos)(_ *Sp*, `_Which`).

## <a name="pubsetbuf"></a>  basic_streambuf::pubsetbuf

Volání [setbuf –](#setbuf), chránit virtuální funkce, která je přepsání v odvozené třídě.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*<br/>
Ukazatel na `char_type` pro vytvoření této instance.

*Počet*<br/>
Velikost vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Vrátí [setbuf –](#setbuf)( `_Buffer`, `count`).

## <a name="pubsync"></a>  basic_streambuf::pubsync

Volání [synchronizace](#sync), chránit virtuální funkce, která je přepsání v odvozené třídě a aktualizuje externí datový proud přidružený k této vyrovnávací paměti.

```cpp
int pubsync();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí [synchronizace](#sync) nebo -1, pokud selhání.

## <a name="sbumpc"></a>  basic_streambuf::sbumpc

Přečte a vrátí aktuální prvek ukazatele datového proudu.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální element.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici pozici pro čtení, členská funkce vrátí **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong> [gptr –](#gptr)) a zvýší další ukazatele pro vstupní vyrovnávací paměť. V opačném případě vrátí [uflow –](#uflow).

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

## <a name="seekoff"></a>  basic_streambuf::seekoff

Chráněná virtuální členská funkce, který se pokouší změnit aktuální pozice řízené datových proudů.

```cpp
virtual pos_type seekoff(
    off_type _Off,
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

Vrátí novou pozici nebo pozice neplatný datový proud ( `seekoff` (_ *vypnout*, `_Way`, `_Which`)).

### <a name="remarks"></a>Poznámky

Na nové pozici je stanoven následujícím způsobem:

- Pokud `_Way`  ==  `ios_base::beg`, na nové pozici je začátku datového proudu a _ *vypnout*.

- Pokud `_Way`  ==  `ios_base::cur`, na nové pozici je aktuální pozici v datovém proudu a _ *vypnout*.

- Pokud `_Way`  ==  `ios_base::end`, na nové pozici je konec datového proudu a _ *vypnout*.

Obvykle Pokud **& ios_base::in** je nenulová, je vliv vstupního datového proudu a pokud **& ios_base::out** je nenulovou hodnotu, má vliv výstupní datový proud. Skutečnému použití tohoto parametru se liší mezi odvozené datový proud vyrovnávací paměti, ale.

Pokud je funkce úspěšná v změnu datového proudu pozici nebo pozice, vrátí výsledný pozici v datovém proudu nebo jeden z výsledné pozice datového proudu. V opačném případě vrátí pozici neplatný datový proud. Výchozí chování je pozici neplatný datový proud.

## <a name="seekpos"></a>  basic_streambuf::seekpos

Chráněná virtuální členská funkce, který se pokouší změnit aktuální pozice řízené datových proudů.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Pozice k vyhledání pro.

*_Which*<br/>
Určuje režim pro ukazatel pozice. Výchozí hodnota je můžete změnit čtení a zápis pozic.

### <a name="return-value"></a>Návratová hodnota

Na nové pozici nebo pozice neplatný datový proud. Chcete-li zjistit, zda pozici v datovém proudu je neplatný, porovnejte návratovou hodnotu s `pos_type(off_type(-1))`.

### <a name="remarks"></a>Poznámky

Na nové pozici je _ *Sp*.

Obvykle Pokud **& ios_base::in** je nenulová, je vliv vstupního datového proudu a pokud **& ios_base::out** je nenulovou hodnotu, má vliv výstupní datový proud. Skutečnému použití tohoto parametru se liší mezi odvozené datový proud vyrovnávací paměti, ale.

Pokud je funkce úspěšná v změnu datového proudu pozici nebo pozice, vrátí výsledný pozici v datovém proudu nebo jeden z výsledné pozice datového proudu. V opačném případě vrátí pozici neplatný datový proud (-1). Výchozí chování je pozici neplatný datový proud.

## <a name="setbuf"></a>  basic_streambuf::setbuf

Chráněná virtuální členská funkce, která provádí konkrétní operace pro každou odvozené datový proud vyrovnávací paměti.

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

Výchozím chováním **to**.

### <a name="remarks"></a>Poznámky

Zobrazit [basic_filebuf –](../standard-library/basic-filebuf-class.md). `setbuf` poskytuje oblast paměti pro `streambuf` objektu, který chcete použít. Využití vyrovnávací paměti v definované v odvozených třídách.

## <a name="setg"></a>  basic_streambuf::setg

Do chráněné funkce, která ukládá _ *Gbeg* v ukazateli začátek `_Gnext` v další ukazatele a `_Gend` v koncový ukazatel pro vstupní vyrovnávací paměť.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parametry

*_Gbeg*<br/>
Ukazatel na začátek vyrovnávací paměti.

*_Gnext*<br/>
Ukazatel na někde uprostřed vyrovnávací paměti.

*_Gend*<br/>
Ukazatel na konec vyrovnávací paměti.

## <a name="setp"></a>  basic_streambuf::setp

Do chráněné funkce, která ukládá *_Pbeg* v ukazateli na začátku a *_Pend* v koncový ukazatel do vyrovnávací paměti výstupních.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parametry

*_Pbeg*<br/>
Ukazatel na začátek vyrovnávací paměti.

*_Pend*<br/>
Ukazatel na konec vyrovnávací paměti.

## <a name="sgetc"></a>  basic_streambuf::sgetc

Vrátí aktuální prvek beze změny pozice v proudu.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální element.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici pozici pro čtení, členská funkce vrátí **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr –](#gptr)). V opačném případě vrátí [podtečení](#underflow).

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

## <a name="sgetn"></a>  basic_streambuf::sgetn

Extrahuje až *počet* znaků ze vstupní vyrovnávací paměť a ukládá je do zadané vyrovnávací paměti *ptr*.

Tato metoda je potenciálně nebezpečná, protože spoléhá na že volající zkontroluje správnost předaných hodnot.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Vyrovnávací paměť obsahující extrahované znaků.

*Počet*<br/>
Počet prvků ke čtení.

### <a name="return-value"></a>Návratová hodnota

Počet prvků, které umožňuje číst. Zobrazit [streamsize](../standard-library/ios-typedefs.md#streamsize) Další informace.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [xsgetn –](#xsgetn)( `ptr`, `count`).

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

## <a name="showmanyc"></a>  basic_streambuf::showmanyc

Chráněná virtuální členská funkce, která vrátí počet znaků, které může být extrahována ze vstupního datového proudu a ujistěte se, že program nebude podléhat neomezené čekání.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Návratová hodnota

Výchozí chování je k vrácení nuly.

## <a name="snextc"></a>  basic_streambuf::snextc

Načte aktuální prvek a vrátí následující element.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Návratová hodnota

Další prvek v datovém proudu.

### <a name="remarks"></a>Poznámky

Volání členských funkcí [sbumpc –](#sbumpc) a tato funkce vrátí-li **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), vrátí **traits_type::eof**. V opačném případě vrátí [sgetc –](#sgetc).

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

## <a name="sputbackc"></a>  basic_streambuf::sputbackc

Vloží char_type v datovém proudu.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*<br/>
Znak.

### <a name="return-value"></a>Návratová hodnota

Vrátí znak nebo selhání.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici putback – pozice a *_Ch* porovná rovno znak uložené na této pozici, sníží členské funkce pro vstupní vyrovnávací paměti a vrátí ukazatel next **traits_type::** [ to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). V opačném případě vrátí [pbackfail –](#pbackfail)( `_Ch`).

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

## <a name="sputc"></a>  basic_streambuf::sputc

Vloží znak do datového proudu.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*<br/>
Znak.

### <a name="return-value"></a>Návratová hodnota

Vrátí znak, pokud je úspěšná.

### <a name="remarks"></a>Poznámky

Pokud `write position` je k dispozici, členské funkce úložiště *_Ch* v pozici pro zápis, zvýší další ukazatel do vyrovnávací paměti výstupních a vrátí **traits_type::**[to_int_type ](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). V opačném případě vrátí [přetečení](#overflow)( `_Ch`).

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

## <a name="sputn"></a>  basic_streambuf::sputn

Převede řetězec znaků do datového proudu.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Řetězec znaků.

*Počet*<br/>
Počet znaků.

### <a name="return-value"></a>Návratová hodnota

Počet znaků ve skutečnosti vložen do datového proudu.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [xsputn –](#xsputn)( `ptr`, `count`). V části poznámky tohoto člena pro další informace.

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

## <a name="stossc"></a>  basic_streambuf::stossc

Přesunout za aktuální prvek v datovém proudu.

```cpp
void stossc();
```

### <a name="remarks"></a>Poznámky

Volání členských funkcí [sbumpc –](#sbumpc). Všimněte si, že implementace není požádáni o zadání tato členská funkce.

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

## <a name="sungetc"></a>  basic_streambuf::sungetc

Získá znak z datového proudu.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí znak nebo selhání.

### <a name="remarks"></a>Poznámky

Pokud je k dispozici putback – pozici, členské funkce sníží další ukazatele pro vstupní vyrovnávací paměti a vrátí `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr –](#gptr)). Však není vždy možné určit poslední znak čtení tak, že je možné uložit do vyrovnávací paměti pro aktuální stav. Pokud je hodnota true, vrátí funkce [pbackfail –](#pbackfail). Abyste předešli této situaci, udržovat přehled o znak, který má vrátit zpět a volat `sputbackc(ch)`, které nebudou zadané nebudete ji volat na začátku datového proudu a není pokusí vrátit více než jeden znak.

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

## <a name="swap"></a>  basic_streambuf::swap

Vymění hodnoty v tomto objektu pro hodnoty v zadaných `basic_streambuf` objektu.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*doprava*|Odkaz na lvalue k `basic_streambuf` objekt, který se používá k výměně hodnot.|

### <a name="remarks"></a>Poznámky

Chráněný člen funkce vyměňuje s *správné* všechny ukazatele řízení `input buffer` a `output buffer`. Také vymění `right.` [getloc()](#getloc) s `locale` objektu.

## <a name="sync"></a>  basic_streambuf::Sync

Chráněné virtuální funkce, který se pokouší synchronizovat řízené datové proudy s jakékoli přidružené externích datových proudů.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Návratová hodnota

Pokud funkce nemůže být úspěšná, vrátí hodnotu -1. Výchozí chování je k vrácení nuly.

### <a name="remarks"></a>Poznámky

`sync` zahrnuje výpisu všechny prvky mezi počáteční a další ukazatele pro výstupní vyrovnávací paměť. Nezahrnuje vložení zpět všechny prvky mezi na další a end ukazatele pro vstupní vyrovnávací paměť.

## <a name="traits_type"></a>  basic_streambuf::traits_type

Přidruží název typu se **Tr** parametr šablony.

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>  basic_streambuf::uflow

Chráněné virtuální funkce, která extrahuje aktuálního elementu ze vstupního datového proudu.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální element.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí extrahovat aktuálního elementu **ch** ze vstupního datového proudu, pak přejděte aktuální pozici v datovém proudu a vrátí prvek jako **traits_type::** [ to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). To lze provést různými způsoby:

- Pokud je k dispozici pozici pro čtení, trvá **ch** jako element uložené v pozici pro čtení a přejde na další ukazatele pro vstupní vyrovnávací paměť.

- Může číst prvek přímo z některých externího zdroje a poskytování jako hodnota **ch**.

- Pro vyrovnávací paměť datového proudu s společné vstupní a výstupní datové proudy ho můžete zpřístupnit pozici pro čtení psaní navýšení kapacity, některé externí cílové, některé nebo všechny prvky mezi začátky a další ukazatele pro výstupní vyrovnávací paměť. Nebo ji přidělení nové nebo další úložiště pro vstupní vyrovnávací paměť. Funkce pak přečte, z některých externího zdroje, jeden nebo více prvků.

Pokud funkce nemůže být úspěšná, vrátí **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), nebo vyvolá výjimku. V opačném případě vrátí aktuální prvek `ch` v vstupního datového proudu, převést, jak je popsáno výše a přejde na další ukazatele pro vstupní vyrovnávací paměť. Výchozí chování je volat [podtečení](#underflow) a tato funkce vrátí-li **traits_type::eof**, který vrátí **traits_type::eof**. V opačném případě vrátí aktuální prvek **ch** v vstupního datového proudu, převést, jak je uvedeno výše a přejde na další ukazatele pro vstupní vyrovnávací paměť.

## <a name="underflow"></a>  basic_streambuf::underflow

Chráněná, virtuální funkce se extrahovat aktuálního elementu ze vstupního datového proudu.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Návratová hodnota

Aktuální element.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce endeavors extrahovat aktuálního elementu **ch** ze vstupního datového proudu, bez posunutí aktuální pozici datový proud stream a vraťte jej jako `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)() **ch**). To lze provést různými způsoby:

- Pokud je k dispozici, pozici pro čtení **ch** je prvek uložený v pozici pro čtení. Další informace o to, najdete v části poznámky [basic_streambuf – třída](../standard-library/basic-streambuf-class.md).

- To může zpřístupnit pozici pro čtení přidělením nové nebo další úložiště pro vstupní vyrovnávací paměť, pak se čte, z některých externího zdroje, jeden nebo více prvků. Další informace o to, najdete v části poznámky [basic_streambuf – třída](../standard-library/basic-streambuf-class.md).

Pokud funkce nemůže být úspěšná, vrátí `traits_type::` [eof](../standard-library/char-traits-struct.md#eof) `()` nebo vyvolá výjimku. V opačném případě vrátí aktuální prvek vstupního datového proudu, převést jak je uvedeno výše. Výchozím chováním `traits_type::eof()`.

Virtuální `underflow` funkce, se [synchronizace](#sync) a [přetečení](#overflow) funkce, definuje vlastnosti `streambuf`-odvozené třídy. Každá odvozená třída může implementovat `underflow` jinak, ale rozhraní se volání třídy datového proudu je stejný.

`underflow` Nejčastěji volána veřejností `streambuf` funkce jako [sgetc –](#sgetc) a [sgetn –](#sgetn) při oblasti get je prázdný, ale můžete volat jiné třídy, včetně tříd datového proudu `underflow` kdykoli.

`underflow` Funkce poskytuje oblast get s znaků ze vstupního zdroje. Pokud v oblasti get obsahuje znaky, `underflow` vrátí první znak. Pokud je prázdný oblast get, vyplní oblast get a vrátí následující znak (což ponechá v oblasti get). Pokud je k dispozici žádné další znaky, pak `underflow` vrátí `EOF` a zůstane prázdné oblasti get.

V `strstreambuf` třídy `underflow` upraví [egptr –](#egptr) ukazatel na úložiště, která byla přidělena dynamicky voláním `overflow`.

## <a name="xsgetn"></a>  basic_streambuf::xsgetn

Chráněná, virtuální funkce se extrahovat prvky ze vstupního datového proudu.

Tato metoda je potenciálně nebezpečná, protože spoléhá na že volající zkontroluje správnost předaných hodnot.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Vyrovnávací paměť obsahující extrahované znaků.

*Počet*<br/>
Počet elementů k extrakci.

### <a name="return-value"></a>Návratová hodnota

Počet prvků extrahovat.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce extrahuje až *počet* prvky ze vstupního datového proudu, jako by opakovaná volání [sbumpc –](#sbumpc)a ukládá je do pole počínaje *ptr*. Vrátí počet prvků ve skutečnosti extrahovat.

## <a name="xsputn"></a>  basic_streambuf::xsputn

Chráněná, virtuální funkce Vložit prvky do výstupního datového proudu.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Ukazatel na elementy vložit.

*Počet*<br/>
Počet elementů k vložení.

### <a name="return-value"></a>Návratová hodnota

Počet prvků ve skutečnosti vložen do datového proudu.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se vloží až *počet* prvky do výstupní datový proud stejně, jako by opakovaná volání [sputc –](#sputc), od začátku pole na *ptr*. Vložení znaků do výstupního datového proudu zastaví jednou všechny *počet* napsaná znaků nebo pokud volat `sputc( count)` vracel `traits::eof()`. Vrátí počet prvků ve skutečnosti vložen.

## <a name="see-also"></a>Viz také:

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
