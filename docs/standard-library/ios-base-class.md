---
title: ios_base – třída
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
ms.openlocfilehash: e269028ff28b00586fd8d8dcef728f11037dfbc8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687893"
---
# <a name="ios_base-class"></a>ios_base – třída

Třída popisuje funkce úložiště a členů společné pro vstupní i výstupní proudy, které nezávisí na parametrech šablony. (Šablona třídy [basic_ios](../standard-library/basic-ios-class.md) popisuje, co je běžné a je závislé na parametrech šablony.)

Objekt třídy ios_base ukládá informace o formátování, které se skládají z:

- Formátovací příznaky v objektu typu [fmtflags](#fmtflags).

- Maska výjimky v objektu typu [iostate](#iostate).

- Šířka pole v objektu typu **int**.

- Přesnost zobrazení v objektu typu **int**.

- Objekt národního prostředí v objektu typu `locale`.

- Dvě rozšiřitelná pole s prvky typu **Long** a ukazatel typu **void** .

Objekt třídy ios_base také ukládá informace o stavu datového proudu, v objektu typu [iostate](#iostate)a zásobníku zpětného volání.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[ios_base](#ios_base)|Vytvoří objekty `ios_base`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[event_callback](#event_callback)|Popisuje funkci předanou do [register_call](#register_callback).|
|[fmtflags](#fmtflags)|Konstanty pro určení vzhledu výstupu.|
|[iostate](#iostate)|Definuje konstanty popisující stav datového proudu.|
|[openmode](#openmode)|Popisuje, jak pracovat s datovým proudem.|
|[seekdir](#seekdir)|Určuje počáteční bod pro operace posunu.|

### <a name="enums"></a>Výčty

|||
|-|-|
|[event](#event)|Určuje typy událostí.|

### <a name="constants"></a>Konstanty

|||
|-|-|
|[adjustfield](#fmtflags)|Bitová maska definovaná jako &#124; `internal` &#124; `left` `right`.|
|[aplikace](#openmode)|Určuje, že se má před každým vložením na konec datového proudu vyžádat.|
|[MUM](#openmode)|Určuje, že se při prvním vytvoření jeho řídicího objektu vyhledá konec datového proudu.|
|[badbit](#iostate)|Zaznamenává ztrátu integrity vyrovnávací paměti datového proudu.|
|[basefield](#fmtflags)|Bitová maska definovaná jako &#124; `dec` &#124; `hex` `oct`.|
|[beg](#seekdir)|Určuje hledání vzhledem k začátku sekvence.|
|[tvaru](#openmode)|Určuje, že by měl být soubor čten jako binární datový proud, nikoli jako textový Stream.|
|[boolalpha](#fmtflags)|Určuje vložení nebo extrakci objektů typu **bool** jako názvů (například **true** a **false**) spíše než jako číselné hodnoty.|
|[běžný](#seekdir)|Určuje hledání vzhledem k aktuální pozici v rámci sekvence.|
|[18.12](#fmtflags)|Určuje vložení nebo extrakci celočíselných hodnot v desítkovém formátu.|
|[účelu](#seekdir)|Určuje hledání vzhledem ke konci sekvence.|
|[eofbit](#iostate)|Zaznamenává konec souboru při extrakci z datového proudu.|
|[failbit](#iostate)|Zaznamenává selhání pro extrakci platného pole z datového proudu.|
|[určí](#fmtflags)|Určuje vložení hodnot s plovoucí desetinnou čárkou ve formátu s pevnou desetinnou čárkou (bez pole exponent).|
|[floatfield](#fmtflags)|Bitová maska definovaná jako &#124; `fixed` `scientific`|
|[goodbit](#iostate)|Všechny stavové bity nejsou jasné.|
|[soustavy](#fmtflags)|Určuje vložení nebo extrakci celočíselných hodnot v šestnáctkovém formátu.|
|[in](#openmode)|Určuje extrakci z datového proudu.|
|[internal](#fmtflags)|Doplňte na šířku pole vložením znaků do interního bodu k vygenerovanému číselnému poli.|
|[zbývá](#fmtflags)|Určuje zarovnání vlevo.|
|[mořská](#fmtflags)|Určuje vložení nebo extrakci celočíselných hodnot v osmičkovém formátu.|
|[out](#openmode)|Určuje vložení do datového proudu.|
|[Kliknutím](#fmtflags)|Určuje zarovnání vpravo.|
|[odbornou](#fmtflags)|Určuje vložení hodnot s plovoucí desetinnou čárkou do vědeckého formátu (s polem exponent).|
|[showbase](#fmtflags)|Určuje vložení předpony, která odhalí základ generovaného pole celé číslo.|
|[showpoint](#fmtflags)|Určuje nepodmíněné vložení desetinné čárky v generovaném poli s plovoucí desetinnou čárkou.|
|[showpos](#fmtflags)|Určuje vložení znaménka plus v nezáporném vygenerovaném číselném poli.|
|[skipws](#fmtflags)|Určuje, že se před určitými extrakci přeskočí počáteční prázdné znaky.|
|[TRUNC –](#openmode)|Určuje odstranění obsahu existujícího souboru, když je vytvořen jeho řídicí objekt.|
|[unitbuf](#fmtflags)|Způsobí vyprázdnění výstupu po každém vložení.|
|[všechna](#fmtflags)|Určuje vkládání velkých ekvivalentů malých písmen v určitých vloženích.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[poruše](#failure)|Třída member slouží jako základní třída pro všechny výjimky vyvolané členskou funkcí [clear](../standard-library/basic-ios-class.md#clear) v šabloně třídy [basic_ios](../standard-library/basic-ios-class.md).|
|[Flag](#flags)|Nastaví nebo vrátí aktuální nastavení příznaku.|
|[getloc](#getloc)|Vrátí uložený objekt národního prostředí.|
|[imbue –](#imbue)|Změní národní prostředí.|
|[Init](#init)|Vytvoří standardní objekty iostream – při sestavení.|
|[iword](#iword)|Přiřadí hodnotu, která se uloží jako `iword`.|
|[číslic](#precision)|Určuje počet číslic, které se mají zobrazit v čísle s plovoucí desetinnou čárkou.|
|[pword](#pword)|Přiřadí hodnotu, která se uloží jako `pword`.|
|[register_callback](#register_callback)|Určuje funkci zpětného volání.|
|[setf](#setf)|Nastaví zadané příznaky.|
|[sync_with_stdio](#sync_with_stdio)|Zajišťuje, aby operace knihovny run-time iostream – a jazyka C probíhaly v pořadí, ve kterém se zobrazují ve zdrojovém kódu.|
|[unsetf](#unsetf)|Způsobí, že zadané příznaky budou vypnuté.|
|[Délk](#width)|Nastaví délku výstupního datového proudu.|
|[xalloc](#xalloc)|Určuje, že proměnná musí být součástí datového proudu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení pro objekty `ios_base`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ios >

**Obor názvů:** std

## <a name="event"></a>událostí

Určuje typy událostí.

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Poznámky

Typ je výčtový typ, který popisuje objekt, který může ukládat událost zpětného volání používané jako argument do funkce zaregistrované v [register_callback](#register_callback). Hodnoty jedinečných událostí jsou:

- `copyfmt_event` pro identifikaci zpětného volání, které se nachází poblíž konce volání [copyfmt](../standard-library/basic-ios-class.md#copyfmt), těsně před zkopírováním [masky výjimky](../standard-library/ios-base-class.md) .

- `erase_event` pro identifikaci zpětného volání, ke kterému dochází na začátku volání [copyfmt](../standard-library/basic-ios-class.md#copyfmt)nebo na začátku volání destruktoru pro **\*this**.

- `imbue_event` k identifikaci zpětného volání, které se vyskytne na konci volání [imbue –](#imbue), těsně před vrácením funkce.

### <a name="example"></a>Příklad

Příklad najdete v tématu [register_callback](#register_callback) .

## <a name="event_callback"></a>event_callback

Popisuje funkci předanou do [register_call](#register_callback).

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>Parametry

*_E* \
[Událost](#event).

*_Base* \
Datový proud, ve kterém byla událost volána.

*_I* \
Uživatelem definované číslo.

### <a name="remarks"></a>Poznámky

Typ popisuje ukazatel na funkci, kterou lze zaregistrovat pomocí [register_callback](#register_callback). Tento typ funkce nesmí vyvolat výjimku.

### <a name="example"></a>Příklad

Příklad, který používá `event_callback`, naleznete v tématu [register_call](#register_callback) .

## <a name="failure"></a>poruše

Třída `failure` definuje základní třídu pro typy všech objektů, které jsou vyvolány jako výjimky, pomocí funkcí v knihovně `iostreams` a k hlášení chyb zjištěných během operací vyrovnávací paměti datového proudu.

```cpp
namespace std {
    class failure : public system_error {
    public:
        explicit failure(
            const string& _Message,
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,
            const error_code& _Code = io_errc::stream);
    };
}
```

### <a name="remarks"></a>Poznámky

Hodnota vrácená `what()` je kopie `_Message`, která může být rozšířena s testem na základě `_Code`. Pokud není zadán `_Code`, je výchozí hodnota `make_error_code(io_errc::stream)`.

### <a name="example"></a>Příklad

```cpp
// ios_base_failure.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.exceptions(ios::failbit);
    try
    {
        file.open( "rm.txt", ios_base::in );
        // Opens nonexistent file for reading
    }
    catch( ios_base::failure f )
    {
        cout << "Caught an exception: " << f.what() << endl;
    }
}
```

```Output
Caught an exception: ios_base::failbit set
```

## <a name="flags"></a>Flag

Nastaví nebo vrátí aktuální nastavení příznaku.

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>Parametry

*fmtfl* \
Nové nastavení `fmtflags`.

### <a name="return-value"></a>Návratová hodnota

Předchozí nebo aktuální nastavení `fmtflags`.

### <a name="remarks"></a>Poznámky

Seznam příznaků naleznete v tématu [ios_base:: fmtflags](#fmtflags) .

První členská funkce vrátí příznaky uloženého formátu. Druhá členská funkce ukládá *fmtfl* do příznaků formátu a vrátí její předchozí uloženou hodnotu.

### <a name="example"></a>Příklad

```cpp
// ios_base_flags.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    cout << cout.flags( ) << endl;
    cout.flags( ios::dec | ios::boolalpha );
    cout << cout.flags( );
}
```

```Output
513
16896
```

## <a name="fmtflags"></a>fmtflags

Konstanty pro určení vzhledu výstupu.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type fmtflags;
   static const fmtflags boolalpha;
   static const fmtflags dec;
   static const fmtflags fixed;
   static const fmtflags hex;
   static const fmtflags internal;
   static const fmtflags left;
   static const fmtflags oct;
   static const fmtflags right;
   static const fmtflags scientific;
   static const fmtflags showbase;
   static const fmtflags showpoint;
   static const fmtflags showpos;
   static const fmtflags skipws;
   static const fmtflags unitbuf;
   static const fmtflags uppercase;
   static const fmtflags adjustfield;
   static const fmtflags basefield;
   static const fmtflags floatfield;
   // ...
};
```

### <a name="remarks"></a>Poznámky

Podporuje manipulace v [iOS](../standard-library/ios.md).

Typ je typ maskování, který popisuje objekt, který může ukládat příznaky formátu. Jednotlivé hodnoty příznaku (elementy) jsou:

- `dec` pro vložení nebo extrakci celočíselných hodnot v desítkovém formátu.

- `hex` pro vložení nebo extrakci celočíselných hodnot v šestnáctkovém formátu.

- `oct` pro vložení nebo extrakci celočíselných hodnot v osmičkovém formátu.

- `showbase` pro vložení předpony, která odhalí základ generovaného pole celé číslo.

- `internal`, pokud chcete podle potřeby doplnit šířku pole, vložením znaků v interním poli do generovaného číselného pole. (Informace o nastavení šířky pole naleznete v tématu [setw](../standard-library/iomanip-functions.md#setw)).

- `left`, pokud chcete podle potřeby doplnit na šířku pole, vložením znaků na konci vygenerovaného pole (zarovnání doleva).

- `right`, pokud chcete podle potřeby doplnit na šířku pole, vložením znaků na začátku generovaného pole (zarovnání vpravo).

- `boolalpha` pro vložení nebo extrakci objektů typu **bool** jako názvů (například **true** a **false**) spíše než jako číselné hodnoty.

- `fixed` pro vkládání hodnot s plovoucí desetinnou čárkou ve formátu s pevnou desetinnou čárkou (bez pole exponent).

- `scientific` pro vložení hodnot s plovoucí desetinnou čárkou do vědeckého formátu (s polem exponent).

- `showpoint` pro vložení desetinné čárky do vygenerovaného pole s plovoucí desetinnou čárkou.

- `showpos` pro vložení znaménka plus pro nezáporné vygenerované číselné pole.

- `skipws`, chcete-li přeskočit počáteční prázdné znaky před určitými extrakcemi.

- `unitbuf` pro vyprázdnění výstupu po každém vložení.

- `uppercase` pro vkládání velkých ekvivalentů malých písmen do určitých vložení.

Kromě toho je několik užitečných hodnot:

- `adjustfield`, Bitová maska definovaná jako &#124; `internal` &#124; `left` `right`

- `basefield` definovaný jako `dec` &#124; `hex` `oct` &#124;

- `floatfield` definovaný jako `fixed` &#124; `scientific`

Příklady funkcí upravujících tyto příznaky formátu naleznete v tématu [\<iomanip >](../standard-library/iomanip.md).

## <a name="getloc"></a>getloc

Vrátí uložený objekt národního prostředí.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Návratová hodnota

Uložený objekt národního prostředí.

### <a name="example"></a>Příklad

```cpp
// ios_base_getlock.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    cout << cout.getloc( ).name( ).c_str( ) << endl;
}
```

```Output
C
```

## <a name="imbue"></a>imbue –

Změní národní prostředí.

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc* \
Nové nastavení národního prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí národní prostředí.

### <a name="remarks"></a>Poznámky

Členská funkce ukládá *_Loc* do objektu locale a pak hlásí událost zpětného volání a `imbue_event`. Vrátí předchozí uloženou hodnotu.

### <a name="example"></a>Příklad

Ukázku naleznete v tématu [basic_ios:: imbue –](../standard-library/basic-ios-class.md#imbue) .

## <a name="init"></a>For

Vytvoří standardní objekty iostream – při sestavení.

```cpp
class Init { };
```

### <a name="remarks"></a>Poznámky

Vnořená Třída popisuje objekt, jehož konstrukce zajišťuje správné sestavení standardních objektů iostreams, dokonce i před spuštěním konstruktoru pro libovolný statický objekt.

## <a name="ios_base"></a>ios_base

Sestaví objekty ios_base.

```cpp
ios_base();
```

### <a name="remarks"></a>Poznámky

Konstruktor (Protected) nedělá nic. Pozdější volání **basic_ios::** [init](../standard-library/basic-ios-class.md#init) musí objekt inicializovat před tím, než může být bezpečně zničeno. Proto jediné bezpečné použití pro třídu ios_base je jako základní třída pro šablonu třídy [basic_ios](../standard-library/basic-ios-class.md).

## <a name="iostate"></a>iostate

Typ konstant, které popisují stav datového proudu.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Poznámky

Typ je typ maskování, který popisuje objekt, který může ukládat informace o stavu datového proudu. Jednotlivé hodnoty příznaku (elementy) jsou:

- `badbit` pro záznam ztráty integrity vyrovnávací paměti datového proudu.

- `eofbit` pro záznam konce souboru při extrakci z datového proudu.

- `failbit`, chcete-li zaznamenat selhání pro extrakci platného pole z datového proudu.

Navíc je užitečná hodnota `goodbit`, kde není nastavena žádná z výše uvedených bitů (`goodbit` je zaručena jako nula).

## <a name="iword"></a>iword

Přiřadí hodnotu, která se uloží jako `iword`.

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>Parametry

\ *IDX*
Index hodnoty, která má být uložena jako `iword`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na element *IDX* rozšiřitelného pole s elementy typu **Long**. Všechny prvky jsou účinně přítomné a zpočátku ukládají hodnotu nula. Vrácený odkaz je neplatný po dalším volání `iword` objektu, po změně objektu voláním metody **basic_ios::** [copyfmt](../standard-library/basic-ios-class.md#copyfmt)nebo po zničení objektu.

Pokud je hodnota *IDX* záporná nebo pokud není k dispozici jedinečné úložiště pro daný prvek, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate) **(badbit)** a vrátí odkaz, který nemusí být jedinečný.

Chcete-li získat jedinečný index pro použití ve všech objektech typu `ios_base`, zavolejte [xalloc](#xalloc).

### <a name="example"></a>Příklad

Ukázku použití `iword` naleznete v tématu [xalloc](#xalloc) .

## <a name="openmode"></a>openmode

Popisuje, jak pracovat s datovým proudem.

```cpp
class ios_base {
public:
   typedef implementation-defined-bitmask-type iostate;
   static const iostate badbit;
   static const iostate eofbit;
   static const iostate failbit;
   static const iostate goodbit;
   // ...
};
```

### <a name="remarks"></a>Poznámky

Typ je `bitmask type`, který popisuje objekt, který může uložit režim otevírání pro několik objektů iostreams. Jednotlivé hodnoty příznaku (elementy) jsou:

- `app` pro hledání na konci datového proudu před každým vložením.

- `ate` pro hledání na konci datového proudu při prvním vytvoření jeho řídicího objektu.

- `binary` pro čtení souboru jako binárního datového proudu, nikoli jako textový Stream.

- `in` pro povolení extrakce z datového proudu.

- `out`, aby bylo možné vložit do datového proudu.

- `trunc` pro odstranění obsahu existujícího souboru, když je vytvořen jeho řídicí objekt.

### <a name="example"></a>Příklad

```cpp
// ios_base_openmode.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
}
```

## <a name="op_eq"></a>operátor =

Operátor přiřazení pro objekty ios_base

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>Parametry

*pravé* \
Objekt typu `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Objekt, ke kterému se přiřazuje.

### <a name="remarks"></a>Poznámky

Operátor kopíruje uložené informace o formátování a vytváří novou kopii všech rozšiřitelných polí. Pak vrátí **\*this**. Všimněte si, že zásobník zpětného volání není zkopírován.

Tento operátor je používán pouze třídami odvozenými z `ios_base`.

## <a name="precision"></a>číslic

Určuje počet číslic, které se mají zobrazit v čísle s plovoucí desetinnou čárkou.

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>Parametry

*_Prec* \
Počet platných číslic, které se mají zobrazit, nebo počet číslic za desetinnou čárkou v poli pevný zápis.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí přesnost uloženého [zobrazení](../standard-library/ios-base-class.md). Druhá členská funkce ukládá *_Prec* do přesnosti zobrazení a vrátí její předchozí uloženou hodnotu.

### <a name="remarks"></a>Poznámky

Čísla s plovoucí desetinnou čárkou jsou zobrazena v pevně zanotaci s [pevným](../standard-library/ios-functions.md#fixed)řetězcem.

### <a name="example"></a>Příklad

```cpp
// ios_base_precision.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    float i = 31.31234F;

    cout.precision( 3 );
    cout << i << endl;          // display three significant digits
    cout << fixed << i << endl; // display three digits after decimal
                                // point
}
```

```Output
31.3
31.312
```

## <a name="pword"></a>pword

Přiřadí hodnotu, která se uloží jako `pword`.

```cpp
void *& pword(int _Idx);
```

### <a name="parameters"></a>Parametry

*_Idx* \
Index hodnoty, která má být uložena jako `pword`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na element _ *IDX* rozšiřitelného pole s prvky typu **void** Pointer. Všechny prvky jsou účinně přítomny a zpočátku ukládají ukazatel s hodnotou null. Vrácený odkaz je neplatný po dalším volání `pword` objektu, po změně objektu voláním metody **basic_ios::** [copyfmt](../standard-library/basic-ios-class.md#copyfmt)nebo po zničení objektu.

Pokud je _ *IDX* záporné, nebo pokud není k dispozici jedinečné úložiště pro daný prvek, funkce volá [setstate](../standard-library/basic-ios-class.md#setstate) **(badbit)** a vrátí odkaz, který nemusí být jedinečný.

Chcete-li získat jedinečný index pro použití ve všech objektech typu `ios_base`, zavolejte [xalloc](#xalloc).

### <a name="example"></a>Příklad

Příklad použití `pword` naleznete v tématu [xalloc](#xalloc) .

## <a name="register_callback"></a>register_callback

Určuje funkci zpětného volání.

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>Parametry

*pfn* \
Ukazatel na funkci zpětného volání.

\ *IDX*
Uživatelem definované číslo.

### <a name="remarks"></a>Poznámky

Členská funkce posune dvojici `{pfn, idx}` do uloženého zásobníku zpětného [volání](../standard-library/ios-base-class.md)zásobníku zpětného volání. Když je hlášena **událost** zpětného volání, jsou tyto funkce volány v opačném pořadí registru `(*pfn)(ev, *this, idx)` výrazu.

### <a name="example"></a>Příklad

```cpp
// ios_base_register_callback.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void callback1( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback1" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

void callback2( ios_base::event e, ios_base& stream, int arg )
{
    cout << "in callback2" << endl;
    switch ( e )
    {
    case ios_base::erase_event:
        cout << "an erase event" << endl;
        break;
    case ios_base::imbue_event:
        cout << "an imbue event" << endl;
        break;
    case ios_base::copyfmt_event:
        cout << "an copyfmt event" << endl;
        break;
    };
}

int main( )
{
    // Make sure the imbue will not throw an exception
    // assert( setlocale( LC_ALL, "german" )!=NULL );

    cout.register_callback( callback1, 0 );
    cin.register_callback( callback2, 0 );

    try
    {
        // If no exception because the locale's not found,
        // generate an imbue_event on callback1
        cout.imbue(locale("german"));
    }
    catch(...)
    {
        cout << "exception" << endl;
    }

    // This will
    // (1) erase_event on callback1
    // (2) copyfmt_event on callback2
    cout.copyfmt(cin);

    // We get two erase events from callback2 at the end because
    // both cin and cout have callback2 registered when cin and cout
    // are destroyed at the end of program.
}
```

```Output
in callback1
an imbue event
in callback1
an erase event
in callback2
an copyfmt event
in callback2
an erase event
in callback2
an erase event
```

## <a name="seekdir"></a>seekdir

Určuje počáteční bod pro operace posunu.

```cpp
namespace std {
    class ios_base {
    public:
        typedef implementation-defined-enumerated-type seekdir;
        static const seekdir beg;
        static const seekdir cur;
        static const seekdir end;
        // ...
    };
}
```

### <a name="remarks"></a>Poznámky

Typ je výčtový typ, který popisuje objekt, který může uložit režim hledání použitý jako argument pro členské funkce několika tříd iostream –. Jednotlivé hodnoty příznaku jsou:

- `beg` pro hledání (změnu aktuální pozice pro čtení nebo zápis) vzhledem k začátku sekvence (pole, datový proud nebo soubor).

- `cur` pro hledání vzhledem k aktuální pozici v rámci sekvence.

- `end` pro hledání vzhledem k konci sekvence.

### <a name="example"></a>Příklad

```cpp
// ios_base_seekdir.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
    using namespace std;
    fstream file;
    file.open( "rm.txt", ios_base::out | ios_base::trunc );

    file << "testing";
    file.seekp( 0, ios_base::beg );
    file << "a";
    file.seekp( 0, ios_base::end );
    file << "a";
}
```

## <a name="setf"></a>setf

Nastaví zadané příznaky.

```cpp
fmtflags setf(
    fmtflags _Mask
);
fmtflags setf(
    fmtflags _Mask,
    fmtflags _Unset
);
```

### <a name="parameters"></a>Parametry

*_Mask* \
Příznaky, které mají být zapnuly.

*_Unset* \
Příznaky pro vypnutí.

### <a name="return-value"></a>Návratová hodnota

Předchozí příznaky formátu

### <a name="remarks"></a>Poznámky

První členská funkce efektivně volá [příznaky](#flags)( *\_Mask* &#124; *\_Flags*) (nastaví vybrané bity) a potom vrátí předchozí příznaky formátu. Druhá členská funkce efektivně volá `flags(_Mask & fmtfl, flags & ~_Mask)` (nahradí vybrané bity pod maskou) a potom vrátí předchozí příznaky formátu.

### <a name="example"></a>Příklad

```cpp
// ios_base_setf.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
    using namespace std;
    int i = 10;
    cout << i << endl;

    cout.unsetf( ios_base::dec );
    cout.setf( ios_base::hex );
    cout << i << endl;

    cout.setf( ios_base::dec );
    cout << i << endl;
    cout.setf( ios_base::hex, ios_base::dec );
    cout << i << endl;
}
```

## <a name="sync_with_stdio"></a>sync_with_stdio

Zajišťuje, aby operace knihovny run-time iostream – a jazyka C probíhaly v pořadí, ve kterém se zobrazují ve zdrojovém kódu.

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>Parametry

*_Sync* \
Zda jsou všechny datové proudy synchronizované s `stdio`.

### <a name="return-value"></a>Návratová hodnota

Předchozí nastavení této funkce

### <a name="remarks"></a>Poznámky

Statická členská funkce ukládá příznak `stdio` Sync, který je zpočátku **true**. V případě **hodnoty true**tento příznak zajistí, že operace se stejným souborem budou správně synchronizovány mezi [iostreams](../standard-library/iostreams-conventions.md) funkcemi a s definicemi C++ ve standardní knihovně. V opačném případě se synchronizace může nebo nemusí zaručit, ale může se zlepšit výkon. Funkce ukládá *_Sync* do příznaku synchronizace `stdio` a vrátí jeho předchozí uloženou hodnotu. Můžete ji spolehlivě volat pouze před provedením jakýchkoli operací se standardními datovými proudy.

## <a name="unsetf"></a>unsetf

Způsobí, že zadané příznaky budou vypnuté.

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>Parametry

*_Mask* \
Příznaky, které mají být vypnuty.

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [příznaky](#flags)(`~` *_Mask* **& příznaků**) (Vymazat vybrané bity).

### <a name="example"></a>Příklad

Ukázku použití `unsetf` naleznete v tématu [ios_base:: setf](#setf) .

## <a name="width"></a>Délk

Nastaví délku výstupního datového proudu.

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>Parametry

*_Wide* \
Požadovaná velikost výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nastavení aktuální šířky

### <a name="remarks"></a>Poznámky

První členská funkce vrátí šířku uloženého pole. Druhá členská funkce ukládá *_Wide* do šířky pole a vrátí její předchozí uloženou hodnotu.

### <a name="example"></a>Příklad

```cpp
// ios_base_width.cpp
// compile with: /EHsc
#include <iostream>

int main( ) {
    using namespace std;

    cout.width( 20 );
    cout << cout.width( ) << endl;
    cout << cout.width( ) << endl;
}
```

```Output
20
0
```

## <a name="xalloc"></a>xalloc

Určuje, že proměnná je součástí datového proudu.

```cpp
static int xalloc( );
```

### <a name="return-value"></a>Návratová hodnota

Statická členská funkce vrátí uloženou statickou hodnotu, která se zvýší na každé volání.

### <a name="remarks"></a>Poznámky

Vrácenou hodnotu lze použít jako jedinečný argument index při volání členských funkcí [iword](#iword) nebo [pword](#pword).

### <a name="example"></a>Příklad

```cpp
// ios_base_xalloc.cpp
// compile with: /EHsc
// Lets you store user-defined information.
// iword, jword, xalloc
#include <iostream>

int main( )
{
    using namespace std;

    static const int i = ios_base::xalloc();
    static const int j = ios_base::xalloc();
    cout.iword( i ) = 11;
    cin.iword( i ) = 13;
    cin.pword( j ) = "testing";
    cout << cout.iword( i ) << endl;
    cout << cin.iword( i ) << endl;
    cout << ( char * )cin.pword( j ) << endl;
}
```

```Output
11
13
testing
```

## <a name="see-also"></a>Viz také:

[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
