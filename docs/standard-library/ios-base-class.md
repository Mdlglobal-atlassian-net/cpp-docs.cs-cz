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
ms.openlocfilehash: 8911c3763e6a0c861c162611e1b2617ec26f0cf9
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333348"
---
# <a name="iosbase-class"></a>ios_base – třída

Tato třída popisuje úložiště a členské funkce společné pro vstupní a výstupní datové proudy, které nezávisí na parametry šablony. (Třída šablony [basic_ios –](../standard-library/basic-ios-class.md) popisuje, co je běžné a je závislý na parametry šablony.)

Ios_base – třída objektu ukládá informace o formátování, který se skládá z:

- Formátování v objektu typu příznaky [fmtflags](#fmtflags).

- Masku výjimky v objektu typu [iostate](#iostate).

- Šířka pole v objektu typu **int**.

- Přesností zobrazení v objektu typu **int**.

- Objekt národního prostředí v objektu typu `locale`.

- Dvě extensible pole s prvky typu **dlouhé** a **void** ukazatele.

Objekt ios_base – třída také ukládá informace o stavu datového proudu, v objektu typu [iostate](#iostate)a zásobník zpětného volání.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ios_base](#ios_base)|Vytvoří `ios_base` objekty.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[event_callback](#event_callback)|Popisuje funkci předán [register_call](#register_callback).|
|[fmtflags](#fmtflags)|Konstanty k určení vzhledu výstupu.|
|[iostate](#iostate)|Definuje konstanty popisující stav datového proudu.|
|[openmode](#openmode)|Popisuje, jak pracovat s datového proudu.|
|[seekdir](#seekdir)|Určuje počáteční bod pro operace.|

### <a name="enums"></a>Výčty

|||
|-|-|
|[event](#event)|Určuje typy událostí.|

### <a name="constants"></a>Konstanty

|||
|-|-|
|[adjustfield](#fmtflags)|Bitová maska definován jako `internal` &#124; `left` &#124; `right`.|
|[Aplikace](#openmode)|Určuje, hledání na konec datového proudu před každou vložení.|
|[data](#openmode)|Určuje, hledání na konec datového proudu při prvním vytvoření jeho řídící objekt.|
|[badbit](#iostate)|Zaznamenává ke ztrátě integrity vyrovnávací paměť datového proudu.|
|[basefield](#fmtflags)|Bitová maska definován jako `dec` &#124; `hex` &#124; `oct`.|
|[transakce od](#seekdir)|Určuje, vzhledem k začátku pořadí hledání.|
|[Binární](#openmode)|Určuje, že soubor byste si měli přečíst jako binární datový proud, nikoli jako textového datového proudu.|
|[boolalpha](#fmtflags)|Určuje vložení nebo extrakce objektů typu **bool** jako názvy (například **true** a **false**), nikoli jako číselné hodnoty.|
|[Měna](#seekdir)|Určuje, hledání vzhledem k aktuální pozici v rámci posloupnosti.|
|[DEC](#fmtflags)|Určuje, vložení nebo extrakce celočíselné hodnoty ve formátu desetinného čísla.|
|[ukončení](#seekdir)|Určuje, hledání vzhledem ke konci sekvence.|
|[eofbit](#iostate)|Záznamy end souboru při extrahování z datového proudu.|
|[failbit](#iostate)|Zaznamenává nepovedlo se extrahovat platné pole z datového proudu.|
|[Oprava](#fmtflags)|Určuje vložení hodnot s plovoucí desetinnou čárkou ve formátu s pevnou desetinnou čárkou (pomocí exponentu pole).|
|[floatfield](#fmtflags)|Bitová maska definován jako `fixed`&#124; `scientific`|
|[goodbit](#iostate)|Vymazat všechny bity stavu.|
|[Hex](#fmtflags)|Určuje vložení nebo extrakce celočíselných hodnot v šestnáctkovém formátu.|
|[in](#openmode)|Určuje extrakce z datového proudu.|
|[internal](#fmtflags)|Ladicí systém pro šířku pole vložením znaky výplně okamžiku interní generované číselné pole.|
|[doleva](#fmtflags)|Určuje zarovnání doleva.|
|[Říjen](#fmtflags)|Určuje vložení nebo extrakce celočíselných hodnot v osmičkovém formátu.|
|[out](#openmode)|Určuje vložení do datového proudu.|
|[doprava](#fmtflags)|Určuje zarovnání doprava.|
|[vědecké](#fmtflags)|Určuje vložení hodnot s plovoucí desetinnou čárkou v matematickém formátu (pomocí exponentu pole).|
|[showbase](#fmtflags)|Určuje vložení předponu, která odhaluje base generované číslo pole.|
|[showpoint](#fmtflags)|Určuje Nepodmíněný vložení od desetinné čárky v generované pole s plovoucí desetinnou čárkou.|
|[showpos](#fmtflags)|Určuje vložení znaménko plus v nezáporné generované číselné pole.|
|[skipws](#fmtflags)|Určuje, přeskočí úvodní mezery před určité extrakce.|
|[TRUNC –](#openmode)|Určuje odstranit obsah k existujícímu souboru při jeho řídící objektu.|
|[unitbuf](#fmtflags)|Způsobí, že výstup na vyprázdněním po jednotlivých vložení.|
|[velká písmena](#fmtflags)|Určuje vložení velká ekvivalenty malých písmen v určitých vložení.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[selhání](#failure)|Člen třídy slouží jako základní třída pro všechny výjimky vyvolané členskou funkci [vymazat](../standard-library/basic-ios-class.md#clear) v šabloně třídy [basic_ios –](../standard-library/basic-ios-class.md).|
|[příznaky](#flags)|Nastaví nebo vrátí aktuální nastavení příznaku.|
|[getloc –](#getloc)|Vrátí objekt uloženého národního prostředí.|
|[imbue –](#imbue)|Změní národní prostředí.|
|[Init](#init)|Vytvoří objekty standardní iostream – když vytvořený.|
|[iword –](#iword)|Přiřadí hodnotu, která má být uložena jako `iword`.|
|[Přesnost](#precision)|Určuje počet číslic, které mají zobrazit v číslo s plovoucí desetinnou čárkou.|
|[pword –](#pword)|Přiřadí hodnotu, která má být uložena jako `pword`.|
|[register_callback](#register_callback)|Určuje zpětné volání funkce.|
|[setf](#setf)|Nastaví zadané příznaky.|
|[sync_with_stdio](#sync_with_stdio)|Zajišťuje, že operace knihovny run-time jazyka C a iostream vyskytují v pořadí, ve kterém jsou uvedeny ve zdrojovém kódu.|
|[unsetf –](#unsetf)|Způsobí, že zadané příznaky bude vypnuto.|
|[Šířka](#width)|Nastaví délku výstupního datového proudu.|
|[xalloc –](#xalloc)|Určuje, že proměnné musí být součástí datového proudu.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_eq)|Operátor přiřazení pro `ios_base` objekty.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<ios >

**Namespace:** std

## <a name="event"></a>  ios_base::Event

Určuje typy událostí.

```cpp
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};
```

### <a name="remarks"></a>Poznámky

Typ je výčtového typu, který popisuje objekt, který lze uložit události zpětného volání použít jako argument pro funkci zaregistrovaného [register_callback –](#register_callback). Různá událost hodnoty jsou:

- `copyfmt_event`, k identifikaci zpětné volání, který se nachází na konci volání [copyfmt –](../standard-library/basic-ios-class.md#copyfmt), těsně před [masku výjimky](../standard-library/ios-base-class.md) zkopírován.

- `erase_event`, k identifikaci zpětné volání, který se nachází na začátku volání [copyfmt –](../standard-library/basic-ios-class.md#copyfmt), nebo na začátku volání destruktoru pro  **\*to**.

- `imbue_event`, k identifikaci zpětné volání, který se nachází na konci volání [imbue –](#imbue), těsně před plánovaným začátkem funkce vrátí.

### <a name="example"></a>Příklad

Zobrazit [register_callback –](#register_callback) příklad.

## <a name="event_callback"></a>  ios_base::event_callback

Popisuje funkci předán [register_call](#register_callback).

```cpp
typedef void (__cdecl *event_callback)(
    event _E,
    ios_base& _Base,
    int _I);
```

### <a name="parameters"></a>Parametry

*_E*<br/>
[Události](#event).

*_Základní*<br/>
Datový proud, ve kterém byla volána události.

*_I*<br/>
Uživatelem definované číslo.

### <a name="remarks"></a>Poznámky

Typ, který popisuje ukazatele na funkci, která lze dokument zaregistrovat u [register_callback –](#register_callback). Tento typ funkce nesmí vytvořit výjimku.

### <a name="example"></a>Příklad

Zobrazit [register_call](#register_callback) příklad, který používá `event_callback`.

## <a name="failure"></a>  ios_base::failure

Třída `failure` definuje základní třídu pro typy jako výjimky vyvolané funkcí ve všech objektů `iostreams` knihovny pro hlášení chyb zjištěných během operací vyrovnávací paměť datového proudu.

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

Hodnota vrácená `what()` je kopie `_Message`, může být rozšířená testu na základě `_Code`. Pokud `_Code` není zadán, výchozí hodnota je `make_error_code(io_errc::stream)`.

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

## <a name="flags"></a>  ios_base::Flags

Nastaví nebo vrátí aktuální nastavení příznaku.

```cpp
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```

### <a name="parameters"></a>Parametry

*fmtfl*<br/>
Nové `fmtflags` nastavení.

### <a name="return-value"></a>Návratová hodnota

Předchozí nebo aktuální `fmtflags` nastavení.

### <a name="remarks"></a>Poznámky

Zobrazit [ios_base::fmtflags](#fmtflags) seznam příznaky.

První členská funkce vrátí příznaky formátu uložené. Druhá funkce úložišť člen *fmtfl* příznaky formátu a vrátí jeho předchozí uloženou hodnotu.

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

## <a name="fmtflags"></a>  ios_base::fmtflags

Konstanty k určení vzhledu výstupu.

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

Podporuje manipulátory v [ios](../standard-library/ios.md).

Typ je typ bitové masky, který popisuje objekt, který může ukládat příznaky formátu. Distinct příznaku (prvky) jsou následující:

- `dec`, vložit nebo vyjmout celočíselné hodnoty ve formátu desetinného čísla.

- `hex`, vložit nebo vyjmout celočíselné hodnoty v šestnáctkovém formátu.

- `oct`, vložit nebo vyjmout celočíselných hodnot, v osmičkovém formátu.

- `showbase`, chcete-li vložit předponu, která odhaluje base generované číslo pole.

- `internal`, pro vyplnění šířku pole, podle potřeby vložením znaky výplně okamžiku interní generované číselné pole. (Informace o nastavení jako šířku pole zadáte najdete v tématu [setw](../standard-library/iomanip-functions.md#setw)).

- `left`, pro vyplnění šířku pole, podle potřeby vložením znaky výplně na konci generované pole (zarovnání doleva).

- `right`, pro vyplnění šířku pole, podle potřeby vložením výplně znaků na začátku generované pole (zarovnání doprava).

- `boolalpha`, vložit nebo vyjmout objekty typu **bool** jako názvy (například **true** a **false**), nikoli jako číselné hodnoty.

- `fixed`, chcete-li vložit hodnoty s plovoucí desetinnou čárkou ve formátu s pevnou desetinnou čárkou (pomocí exponentu pole).

- `scientific`, k vložení hodnoty s plovoucí desetinnou čárkou v matematickém formátu (pomocí exponentu pole).

- `showpoint`, vložte desetinné čárky bezpodmínečně generované pole s plovoucí desetinnou čárkou.

- `showpos`, vložte znaménko plus nezáporné generované číselné pole.

- `skipws`, chcete-li přeskočit počáteční prázdné znaky před určité extrakce.

- `unitbuf`, se nezdařil výstup po každé vložení.

- `uppercase`, chcete-li vložit velká ekvivalenty malých písmen v určitých vložení.

Kromě toho několik užitečných hodnoty jsou:

- `adjustfield`, bitová maska definován jako `internal` &#124; `left`&#124; `right`

- `basefield`, definovaná jako `dec` &#124; `hex`&#124; `oct`

- `floatfield`, definovaná jako `fixed`&#124; `scientific`

Příkladem funkce, které upravují toto formátování příznaky, najdete v části [ \<iomanip >](../standard-library/iomanip.md).

## <a name="getloc"></a>  ios_base::getloc

Vrátí objekt uloženého národního prostředí.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt, který uloženého národního prostředí.

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

## <a name="imbue"></a>  ios_base::imbue

Změní národní prostředí.

```cpp
locale imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*<br/>
Nové nastavení národního prostředí.

### <a name="return-value"></a>Návratová hodnota

Předchozí národní prostředí.

### <a name="remarks"></a>Poznámky

Členské funkce úložiště *_Loc* v objektu národního prostředí a oznamuje událost zpětného volání a `imbue_event`. Vrátí předchozí uložené hodnoty.

### <a name="example"></a>Příklad

Zobrazit [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) ukázku.

## <a name="init"></a>  ios_base::init

Vytvoří objekty standardní iostream – když vytvořený.

```cpp
class Init { };
```

### <a name="remarks"></a>Poznámky

Vnořené třídy popisuje objekt, jehož konstrukce zajistí, že standardní iostreams objekty jsou správně strukturován, ještě před spuštěním konstruktoru pro libovolný objekt statické.

## <a name="ios_base"></a>  ios_base::ios_base

Ios_base – objekty konstrukce.

```cpp
ios_base();
```

### <a name="remarks"></a>Poznámky

(Chráněný) konstruktor neprovede žádnou akci. Pozdější volání **basic_ios –::**[init](../standard-library/basic-ios-class.md#init) musí inicializovat objekt předtím, než může být bezpečně zničen. Proto je pouze bezpečné používání pro ios_base – třída jako základní třída pro třídu šablony [basic_ios –](../standard-library/basic-ios-class.md).

## <a name="iostate"></a>  ios_base::iostate

Typ konstanty, které popisují stav datového proudu.

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

Typ je typ bitové masky, který popisuje objekt, který může ukládat informace o stavu datového proudu. Distinct příznaku (prvky) jsou následující:

- `badbit`, k zaznamenání ke ztrátě integrity vyrovnávací paměť datového proudu.

- `eofbit`, k záznamu end souboru při extrahování z datového proudu.

- `failbit`, k zaznamenání nepovedlo se extrahovat platné pole z datového proudu.

Kromě toho je užitečné hodnota `goodbit`, pokud žádná z výše uvedených bity jsou nastaveny (`goodbit` je zaručeně nula).

## <a name="iword"></a>  ios_base::iword

Přiřadí hodnotu, která má být uložena jako `iword`.

```cpp
long& iword(int idx);
```

### <a name="parameters"></a>Parametry

*IDX*<br/>
Index hodnoty k ukládání jako `iword`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na prvek *idx* extensible pole s prvky typu **dlouhé**. Všechny prvky jsou efektivní a zpočátku uložit hodnotu nula. Vrácený odkaz není platný po dalším volání `iword` objektu po změně objektu voláním **basic_ios –::**[copyfmt –](../standard-library/basic-ios-class.md#copyfmt), nebo poté, co objekt zničen.

Pokud *idx* je záporné nebo pokud jedinečný úložiště není k dispozici pro element, volá funkci [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** a vrátí odkaz, který nemusí být jedinečný.

Získání jedinečného indexu, pro použití ve všech objektech typu `ios_base`, volání [xalloc –](#xalloc).

### <a name="example"></a>Příklad

Zobrazit [xalloc –](#xalloc) ukázku toho, jak používat `iword`.

## <a name="openmode"></a>  ios_base::openmode

Popisuje, jak pracovat s datového proudu.

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

Typ je `bitmask type` , který popisuje objekt, který může ukládat režim otevření více iostreams objektů. Distinct příznaku (prvky) jsou následující:

- `app`, hledání na konec datového proudu před každou vložení.

- `ate`, hledání na konec datového proudu při prvním vytvoření jeho řídící objekt.

- `binary`, ke čtení souboru jako binární datový proud, nikoli jako textového datového proudu.

- `in`, tak, aby povolovala extrakce z datového proudu.

- `out`, tak, aby povolovala vkládání do datového proudu.

- `trunc`, můžete odstranit obsah k existujícímu souboru, když je vytvořen objekt jeho řízení.

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

## <a name="op_eq"></a>  ios_base::Operator =

Operátor přiřazení pro ios_base – objekty.

```cpp
ios_base& operator=(const ios_base& right);
```

### <a name="parameters"></a>Parametry

*doprava*<br/>
Objekt typu `ios_base`.

### <a name="return-value"></a>Návratová hodnota

Objekt přiřazení.

### <a name="remarks"></a>Poznámky

Operátor, který se zkopíruje uložené informace o formátování provádění novou kopii všech extensible polí. Potom vrátí  **\*to**. Všimněte si, že zásobník zpětného volání není zkopírován.

Tento operátor se používá pouze třídami odvozenými z `ios_base`.

## <a name="precision"></a>  ios_base::Precision

Určuje počet číslic, které mají zobrazit v číslo s plovoucí desetinnou čárkou.

```cpp
streamsize precision() const;
streamsize precision(streamsize _Prec);
```

### <a name="parameters"></a>Parametry

*_Prec*<br/>
Počet platných číslic pro zobrazení, nebo počet číslic za desetinnou čárkou pevné notaci.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí uložený [přesnost zobrazení](../standard-library/ios-base-class.md). Druhá funkce úložišť člen *_Prec* na zobrazovanou přesnost a vrátí jeho předchozí uloženou hodnotu.

### <a name="remarks"></a>Poznámky

Čísla s plovoucí desetinnou čárkou jsou zobrazeny v pevné zápisu se [oprava](../standard-library/ios-functions.md#fixed).

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

## <a name="pword"></a>  ios_base::pword

Přiřadí hodnotu, která má být uložena jako `pword`.

```cpp
void *& pword(int _Idx);
```

### <a name="parameters"></a>Parametry

*_Idx*<br/>
Index hodnoty k uložení jako `pword`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí odkaz na element _ *Idx* extensible pole s prvky typu **void** ukazatele. Všechny prvky jsou efektivní a zpočátku uložte ukazatele s hodnotou null. Vrácený odkaz není platný po dalším volání `pword` objektu po změně objektu voláním **basic_ios –::**[copyfmt –](../standard-library/basic-ios-class.md#copyfmt), nebo poté, co objekt zničen.

Pokud _ *Idx* je záporný, nebo pokud jedinečný úložiště není k dispozici pro element, volá funkci [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** a vrátí odkaz, který nemusí být jedinečný.

Získání jedinečného indexu, pro použití ve všech objektech typu `ios_base`, volání [xalloc –](#xalloc).

### <a name="example"></a>Příklad

Zobrazit [xalloc –](#xalloc) pro příklad použití `pword`.

## <a name="register_callback"></a>  ios_base::register_callback

Určuje zpětné volání funkce.

```cpp
void register_callback(
    event_callback pfn, int idx);
```

### <a name="parameters"></a>Parametry

*pfn*<br/>
Ukazatel na funkci zpětného volání.

*IDX*<br/>
Uživatelem definované číslo.

### <a name="remarks"></a>Poznámky

Členská funkce nabízených oznámení pár `{pfn, idx}` do zásobníku uložené zpětného volání [zásobník zpětného volání](../standard-library/ios-base-class.md). Při zpětné volání události **ev** se použije v hlášení, funkce jsou volány, v opačném pořadí z registru, výraz `(*pfn)(ev, *this, idx)`.

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

## <a name="seekdir"></a> ios_base::seekdir

Určuje počáteční bod pro operace.

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

Typ je výčtového typu, který popisuje objekt, který můžete uložit hledání režim použít jako argument pro členské funkce třídy iostream – několik. Příznak odlišné hodnoty jsou:

- `beg`, hledání (změnit aktuální čtení ani zápis pozici) vzhledem k začátku sekvenci (pole, datového proudu nebo souboru).

- `cur`, hledání vzhledem k aktuální pozici v rámci posloupnosti.

- `end`, hledání vzhledem ke konci sekvence.

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

## <a name="setf"></a> ios_base::SETF

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

*_Podsítě*<br/>
Příznaky zapnout.

*_Unset*<br/>
Příznaky, chcete-li vypnout.

### <a name="return-value"></a>Návratová hodnota

Předchozí příznaky formátu

### <a name="remarks"></a>Poznámky

První členská funkce efektivně volá [příznaky](#flags)(  *\_maska* &#124;  *\_příznaky*) (nastavení vybrané bits) a potom se vrátí předchozí příznaky formátu. Druhá členská funkce efektivně volá `flags(_Mask & fmtfl, flags & ~_Mask)` (nahradit vybrané bity v části masku) a potom vrátí předchozí příznaky formátu.

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

## <a name="sync_with_stdio"></a> ios_base::sync_with_stdio

Zajišťuje, že operace knihovny run-time jazyka C a iostream vyskytují v pořadí, ve kterém jsou uvedeny ve zdrojovém kódu.

```cpp
static bool sync_with_stdio(
   bool _Sync = true
);
```

### <a name="parameters"></a>Parametry

*_Sync*<br/>
Určuje, zda jsou všechny datové proudy synchronizované s `stdio`.

### <a name="return-value"></a>Návratová hodnota

Předchozí nastavení pro tuto funkci.

### <a name="remarks"></a>Poznámky

Statické členské funkce úložiště `stdio` příznak, který budou synchronizovat **true**. Když **true**, tento příznak zajistí, že se operace se stejným souborem správně synchronizují mezi [iostreams](../standard-library/iostreams-conventions.md) funkce a jsou definované ve standardní knihovně jazyka C++. V opačném případě synchronizace může nebo nemusí být zaručena, ale může být výkon. Funkce úložiště *_Sync* v `stdio` synchronizovat příznak a vrátí jeho předchozí uložené hodnotě. Můžete ho spolehlivě volat pouze před provedením jakékoli operace u standardních streamů.

## <a name="unsetf"></a> ios_base::unsetf

Způsobí, že zadané příznaky bude vypnuto.

```cpp
void unsetf(
   fmtflags _Mask
);
```

### <a name="parameters"></a>Parametry

*_Podsítě*<br/>
Příznaky, které chcete vypnout.

### <a name="remarks"></a>Poznámky

Členská funkce efektivně volá [příznaky](#flags)(`~`*_podsítě* **& příznaky**) (Vymazat vybrané bits).

### <a name="example"></a>Příklad

Zobrazit [ios_base::setf](#setf) ukázku použití `unsetf`.

## <a name="width"></a> ios_base::Width

Nastaví délku výstupního datového proudu.

```cpp
streamsize width( ) const;
streamsize width(
   streamsize _Wide
);
```

### <a name="parameters"></a>Parametry

*_Wide*<br/>
Požadovaná velikost výstupního datového proudu.

### <a name="return-value"></a>Návratová hodnota

Aktuální nastavení šířky.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí šířku uloženého pole. Druhá funkce úložišť člen *_Wide* šířku pole a vrátí jeho předchozí uloženou hodnotu.

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

## <a name="xalloc"></a> ios_base::xalloc

Určuje, že proměnná je součástí datového proudu.

```cpp
static int xalloc( );
```

### <a name="return-value"></a>Návratová hodnota

Statická členská funkce vrátí uložené statické hodnoty, který zvýší hodnotu při každém volání.

### <a name="remarks"></a>Poznámky

Návratová hodnota můžete použít jako jedinečný index argument při volání členské funkce [iword –](#iword) nebo [pword –](#pword).

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

[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
