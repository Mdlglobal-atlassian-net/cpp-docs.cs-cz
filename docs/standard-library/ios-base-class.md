---
title: "ios_base – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 04605ec5df5512549822d0e585bf1b28eb0b42e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iosbase-class"></a>ios_base – třída
Třída popisuje úložiště a členské funkce společné pro vstupní a výstupní datové proudy, které jsou nezávislé na parametry šablony. (Šablony třídy [basic_ios](../standard-library/basic-ios-class.md) popisuje, co je běžné a závisí na parametry šablony.)  
  
 Objekt ios_base – třída ukládá informace o formátování, který se skládá z:  
  
-   Formátování příznaky v objektu typu [fmtflags –](#fmtflags).  
  
-   Maska k výjimce v objektu typu [iostate –](#iostate).  
  
-   Šířka pole v objektu typu `int`.  
  
-   Přesnost zobrazení v objektu typu `int`.  
  
-   Objekt národního prostředí v objektu typu **národního prostředí**.  
  
-   Dva extensible pole elementy typu **dlouho** a `void` ukazatel.  
  
 Objekt ios_base – třída také ukládá informace o stavu datový proud, v objektu typu [iostate –](#iostate)a zásobníku zpětného volání.  
  
### <a name="constructors"></a>Konstruktory  
  
|||  
|-|-|  
|[ios_base –](#ios_base)|Vytvoří `ios_base` objekty.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[event_callback –](#event_callback)|Popisuje funkce předaný [register_call](#register_callback).|  
|[fmtflags –](#fmtflags)|Konstanty k určení vzhledu výstupu.|  
|[iostate –](#iostate)|Definuje konstanty popisující stav datového proudu.|  
|[openmode –](#openmode)|Popisuje, jak pracovat s datového proudu.|  
|[seekdir –](#seekdir)|Určuje počáteční bod pro posunutí operace.|  
  
### <a name="enums"></a>Výčty  
  
|||  
|-|-|  
|[události](#event)|Určuje typy událostí.|  
  
### <a name="constants"></a>Konstanty  
  
|||  
|-|-|  
|[adjustfield](#fmtflags)|Bitová maska definován jako `internal` &#124; `left` &#124; `right`.|  
|[aplikace](#openmode)|Určuje, vyhledávání na konec datového proudu před každou vložení.|  
|[uje](#openmode)|Určuje, při prvním vytvoření jeho ovládání objekt vyhledávání na konec datového proudu.|  
|[badbit](#iostate)|Zaznamenává ke ztrátě integrity vyrovnávací paměti datového proudu.|  
|[basefield](#fmtflags)|Bitová maska definován jako `dec` &#124; `hex` &#124; `oct`.|  
|[transakce od](#seekdir)|Určuje, vzhledem k začátku pořadí.|  
|[binární](#openmode)|Určuje, že soubor byste si měli přečíst jako binárního datového proudu, nikoli jako datový proud text.|  
|[boolalpha](#fmtflags)|Určuje vložení nebo extrakce objekty typu `bool` jako názvy (například `true` a `false`) a nikoli jako číselné hodnoty.|  
|[Měna](#seekdir)|Určuje, vzhledem k aktuální pozici v rámci posloupnosti.|  
|[DEC](#fmtflags)|Určuje vložení nebo extrakce celočíselné hodnoty ve formátu desetinného čísla.|  
|[end](#seekdir)|Určuje, vzhledem k konec sekvenci.|  
|[eofbit](#iostate)|Zaznamenává end souboru při extrahování z datového proudu.|  
|[failbit](#iostate)|Zaznamenává selhání platné pole extrahovat z datového proudu.|  
|[Pevná](#fmtflags)|Určuje vložení hodnot s plovoucí desetinnou čárkou ve formátu s pevnou desetinnou čárkou (s žádné exponentu pole).|  
|[floatfield](#fmtflags)|Bitová maska definován jako `fixed` &#124;`scientific`|  
|[goodbit](#iostate)|Zrušte zaškrtnutí všech stavu bitů.|  
|[Hex](#fmtflags)|Určuje vložení nebo extrakce celočíselné hodnoty v šestnáctkovém formátu.|  
|[v](#openmode)|Určuje extrakci z datového proudu.|  
|[interní](#fmtflags)|Dotyková zařízení šířky pole vložením výplně znaků na bod interní generovaného číselné pole.|  
|[vlevo](#fmtflags)|Určuje zarovnání doleva.|  
|[OCT](#fmtflags)|Určuje vložení nebo extrakce celočíselné hodnoty ve formátu osmičková.|  
|[na více systémů](#openmode)|Určuje vložení do datového proudu.|  
|[vpravo](#fmtflags)|Určuje zarovnání doprava.|  
|[Scientific](#fmtflags)|Určuje vložení hodnot s plovoucí desetinnou čárkou v matematickém formátu (s exponentu pole).|  
|[showbase](#fmtflags)|Určuje vkládání předponu, která zjistí základní pole generovaný celé číslo.|  
|[showpoint](#fmtflags)|Určuje nepodmíněné vkládání desetinné čárky v generované pole s plovoucí desetinnou čárkou.|  
|[showpos](#fmtflags)|Určuje vkládání znaménko plus v nezáporné generovaného číselné pole.|  
|[skipws](#fmtflags)|Určuje, přeskočení úvodních mezer před určité extrakce.|  
|[TRUNC](#openmode)|Určuje odstraňuje obsah existující soubor při jeho řízení objektu.|  
|[unitbuf](#fmtflags)|Příčiny výstupní zapsány po každém vložení.|  
|[velká písmena](#fmtflags)|Určuje vkládání velkých ekvivalenty malých písmen v určitých vložení.|  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[selhání](#failure)|Třída členů slouží jako základní třída pro všechny výjimky vyvolané – členská funkce [vymazat](../standard-library/basic-ios-class.md#clear) ve třídě šablony [basic_ios](../standard-library/basic-ios-class.md).|  
|[příznaky](#flags)|Nastaví nebo vrátí aktuální nastavení příznaku.|  
|[getloc –](#getloc)|Vrací objekt uložené národního prostředí.|  
|[imbue –](#imbue)|Změní národní prostředí.|  
|[Init –](#init)|Standardní iostream objekty, když se vytvoří.|  
|[iword –](#iword)|Přiřadí hodnotu ukládaly jako `iword`.|  
|[přesnost](#precision)|Určuje počet číslic, které chcete zobrazit v číslo s plovoucí desetinnou čárkou.|  
|[pword –](#pword)|Přiřadí hodnotu ukládaly jako `pword`.|  
|[register_callback –](#register_callback)|Určuje funkce zpětného volání.|  
|[SETF](#setf)|Nastaví zadaný příznaků.|  
|[sync_with_stdio –](#sync_with_stdio)|Zajišťuje, že operace běhové knihovny jazyka C a iostream vyskytnout v pořadí, ve kterém se zobrazují ve zdrojovém kódu.|  
|[unsetf –](#unsetf)|Způsobí, že zadaný příznaky tak, aby být vypnutý.|  
|[Šířka](#width)|Nastaví délku do výstupního datového proudu.|  
|[xalloc –](#xalloc)|Určuje, že proměnná musí být součástí datového proudu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](#op_eq)|Operátor přiřazení pro `ios_base` objekty.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<ios >  
  
 **Namespace:** – std  
  
##  <a name="event"></a>ios_base::Event  
 Určuje typy událostí.  
  
```  
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};  
```  
  
### <a name="remarks"></a>Poznámky  
 Typ je výčtového typu, který popisuje objekt, který může ukládat události zpětného volání použít jako argument funkci zaregistrována [register_callback –](#register_callback). Různá událost hodnoty jsou:  
  
- **copyfmt_event**, k identifikaci zpětné volání, ke kterému dochází u konce volání [copyfmt –](../standard-library/basic-ios-class.md#copyfmt), těsně před [výjimka maska](../standard-library/ios-base-class.md) zkopírován.  
  
- **erase_event**, k identifikaci zpětného volání, které se objeví na začátku volání [copyfmt –](../standard-library/basic-ios-class.md#copyfmt), nebo od začátku volání destruktoru pro  **\*to**.  
  
- **imbue_event**, k identifikaci zpětného volání, který se nachází na konci volání [imbue –](#imbue), těsně před funkce vrátí hodnotu.  
  
### <a name="example"></a>Příklad  
  
  V tématu [register_callback –](#register_callback) příklad.  
  
##  <a name="event_callback"></a>ios_base::event_callback  

 Popisuje funkce předaný [register_call](#register_callback).  
  
```  
typedef void (__cdecl *event_callback)(
    event _E,  
    ios_base& _Base,  
    int _I);
```  
  
### <a name="parameters"></a>Parametry  
 *_STEJNÉ O*  
 [Událostí](#event).  
  
 `_Base`  
 Datový proud, ve kterém byla volána události.  
  
 *POTVRZUJ_I*  
 Uživatelem definované číslo.  
  
### <a name="remarks"></a>Poznámky  
  
 Popisuje typ ukazatel na funkci, která lze dokument zaregistrovat u [register_callback –](#register_callback). Tento typ funkce nesmí vyvolat výjimku.  
  
### <a name="example"></a>Příklad  
  
  V tématu [register_call](#register_callback) pro příklad, který používá `event_callback`.  
  
##  <a name="failure"></a>ios_base::failure  
  
 Třída `failure` definuje základní třídu pro typy jako výjimky, vyvolané funkce ve všech objektů `iostreams` knihovny, aby oznamovaly chyby zjistil během operace s datovými proudy vyrovnávací paměti.  
  
```  
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

 Hodnoty vrácené `what()` je kopie `_Message`, pravděpodobně Rozšířená s testu na základě `_Code`. Pokud `_Code` není určena, výchozí hodnota je `make_error_code(io_errc::stream)`.  
  
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
  
##  <a name="flags"></a>ios_base::Flags  
  
 Nastaví nebo vrátí aktuální nastavení příznaku.  
  
```  
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```  
  
### <a name="parameters"></a>Parametry  
 `fmtfl`  
 Nové `fmtflags` nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
  
 Aktuální nebo předchozí `fmtflags` nastavení.  
  
### <a name="remarks"></a>Poznámky  
  
 V tématu [ios_base::fmtflags](#fmtflags) seznam příznaků.  
  
 První člen funkce vrátí příznaky uložené formátu. Druhý člen funkce úložiště `fmtfl` ve formátu příznaky a vrátí jeho předchozí uložená hodnota.  
  
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
  
##  <a name="fmtflags"></a>ios_base::fmtflags  
  
 Konstanty k určení vzhledu výstupu.  
  
```
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
  
 Typ je typ bitová maska, který popisuje objekt, který může ukládat příznaky formátu. Příznak jedinečné hodnoty (prvky) jsou:  
  
- `dec`, vložit nebo extrahování celočíselné hodnoty ve formátu desetinného čísla.  
  
- `hex`, vložit nebo extrahování celočíselné hodnoty v šestnáctkovém formátu.  
  
- `oct`, vložit nebo extrahování celočíselné hodnoty ve formátu osmičková.  
  
- `showbase`, chcete-li vložit předponu, která zjistí základní pole generovaný celé číslo.  
  
- `internal`, k vyplnění pole šířky podle potřeby vložením výplně znaků na bod interní generovaného číselné pole. (Informace o nastavení šířka pole najdete v tématu [setw](../standard-library/iomanip-functions.md#setw)).  
  
- `left`, k vyplnění pole šířky podle potřeby vložením výplně znaků na konci generované pole (levém zarovnání do bloku).  
  
- `right`, k vyplnění pole šířky podle potřeby vložením výplně znaků od začátku generované pole (zarovnání doprava).  
  
- `boolalpha`, vložit nebo extrahování objekty typu `bool` jako názvy (například `true` a `false`) a nikoli jako číselné hodnoty.  
  
- `fixed`, chcete-li vložit hodnoty s plovoucí desetinnou čárkou ve formátu s pevnou desetinnou čárkou (s žádné exponentu pole).  
  
- `scientific`, Vložit hodnoty s plovoucí desetinnou čárkou v matematickém formátu (s exponentu pole).  
  
- `showpoint`, chcete-li vložit desetinné čárky bezpodmínečně v generované pole s plovoucí desetinnou čárkou.  
  
- `showpos`, chcete-li vložit znaménko plus v nezáporné generovaného číselné pole.  
  
- `skipws`, tak, aby přeskočil úvodních mezer před určité extrakce.  
  
- `unitbuf`, k vyprázdnění výstupní po každém vložení.  
  
- `uppercase`, vložit velká ekvivalenty malých písmen v určitých vložení.  
  
 Kromě toho několik užitečné hodnoty jsou:  
  
- `adjustfield`, bitová maska definován jako `internal` &#124; `left` &#124;`right`  
  
- `basefield`, definován jako `dec` &#124; `hex` &#124;`oct`  
  
- `floatfield`, definován jako `fixed` &#124;`scientific`  
  
 Příklady funkcí, které upravují tyto formátu příznaky, najdete v části [ \<iomanip – >](../standard-library/iomanip.md).  
  
##  <a name="getloc"></a>ios_base::getloc  
  
 Vrací objekt uložené národního prostředí.  
  
```  
locale getloc() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
 Objekt uložené národního prostředí.  
  
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
  
##  <a name="imbue"></a>ios_base::imbue  

 Změní národní prostředí.  
  
```  
locale imbue(const locale& _Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `_Loc`  
 Nové nastavení národního prostředí.  
  
### <a name="return-value"></a>Návratová hodnota  
  
 Předchozí národní prostředí.  
  
### <a name="remarks"></a>Poznámky  
  
 Členské funkce úložiště `_Loc` v objektu, národní prostředí a hlásí události zpětného volání a `imbue_event`. Vrátí předchozí uložené hodnoty.  
  
### <a name="example"></a>Příklad  
  
  V tématu [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) pro ukázku.  
  
##  <a name="init"></a>ios_base::init  
  
 Standardní iostream objekty, když se vytvoří.  
  
```  
class Init { };  
```
  
### <a name="remarks"></a>Poznámky  
  
 Vnořené třídy popisuje objekt, jehož konstrukce zajistí, že objekty standardní iostreams jsou správně strukturován, i před spuštěním konstruktoru pro libovolný objekt statické.  
  
##  <a name="ios_base"></a>ios_base::ios_base  
  
 Vytvoří ios_base objekty.  
  
```  
ios_base();
```  
  
### <a name="remarks"></a>Poznámky  
  
 V konstruktoru (chráněné) neprovede žádnou akci. Novější volání **basic_ios::**[init](../standard-library/basic-ios-class.md#init) musí inicializovat objekt, než může být bezpečně zničena. Proto je pouze bezpečné používání ios_base – třída jako základní třída pro třídu šablony [basic_ios](../standard-library/basic-ios-class.md).  
  
##  <a name="iostate"></a>ios_base::iostate  
  
 Typ konstanty, které popisují stav datového proudu.  
  
```  
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
  
 Typ je typ bitová maska, který popisuje objekt, který může ukládat informace o stavu datového proudu. Příznak jedinečné hodnoty (prvky) jsou:  
  
- `badbit`, k zaznamenání ke ztrátě integrity vyrovnávací paměti datového proudu.  
  
- `eofbit`, k záznamu end souboru při extrahování z datového proudu.  
  
- `failbit`, k zaznamenání selhání platné pole extrahovat z datového proudu.  
  
 Kromě toho je užitečné hodnota `goodbit`, kde jsou nastaveny žádné z výše uvedených bits ( `goodbit` představuje záruku nula).  
  
##  <a name="iword"></a>ios_base::iword  
  
 Přiřadí hodnotu ukládaly jako `iword`.  
  
```  
long& iword(int idx);
```  
  
### <a name="parameters"></a>Parametry  
 `idx`  
 Index hodnoty ukládání jako `iword`.  
  
### <a name="remarks"></a>Poznámky  
  
 Členská funkce vrátí odkaz na element `idx` extensible pole elementy typu **dlouho**. Všechny elementy jsou k dispozici efektivně a původně uložení hodnotu nula. Vrácený odkaz je neplatný po další volání `iword` pro objekt, po objektu je změnit voláním **basic_ios::**[copyfmt –](../standard-library/basic-ios-class.md#copyfmt), nebo po objekt zničena.  
  
 Pokud `idx` je záporný nebo pokud jedinečný úložiště není k dispozici pro element, zavolá funkci [setstate –](../standard-library/basic-ios-class.md#setstate)**(badbit)** a vrátí odkaz, který nemusí být jedinečný.  
  
 K získání jedinečný index pro použití ve všech objektech typu `ios_base`, volání [xalloc –](#xalloc).  
  
### <a name="example"></a>Příklad  
  
  V tématu [xalloc –](#xalloc) pro ukázkové použití `iword`.  
  
##  <a name="openmode"></a>ios_base::openmode  
  
 Popisuje, jak pracovat s datového proudu.  
  
```  
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
  
 Typ je `bitmask type` , který popisuje objekt, který může ukládat otevírání režimu pro několik iostreams objekty. Příznak jedinečné hodnoty (prvky) jsou:  
  
- **aplikace**, k vyhledání na konec datového proudu před každou vložení.  
  
- **uje**, k vyhledání na konec datového proudu při prvním vytvoření jeho ovládání objekt.  
  
- **binární**ke čtení souboru jako binární datový proud, nikoli jako datový proud text.  
  
- **v**, tak, aby povolovala extrakci z datového proudu.  
  
- **out**, tak, aby povolovala vložení do datového proudu.  
  
- **TRUNC**, můžete odstranit obsah existující soubor, když je vytvořen objekt jeho ovládání.  
  
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
  
##  <a name="op_eq"></a>ios_base::Operator =  

 Operátor přiřazení pro ios_base objekty.  
  
```  
ios_base& operator=(const ios_base& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Objekt typu `ios_base`.  
  
### <a name="return-value"></a>Návratová hodnota  
  
 Objekt přiřazeny.  
  
### <a name="remarks"></a>Poznámky  
  
 Operátor zkopíruje uložené informace o formátování provedení novou kopii všech extensible pole. Pak vrátí  **\*to**. Všimněte si, že není zkopírovali zásobníku zpětného volání.  
  
 Tento operátor. je používán pouze třídy odvozené od třídy `ios_base`.  
  
##  <a name="precision"></a>ios_base::Precision  
  
 Určuje počet číslic, které chcete zobrazit v číslo s plovoucí desetinnou čárkou.  
  
```  
streamsize precision() const;
streamsize precision(streamsize _Prec);
```  
  
### <a name="parameters"></a>Parametry  
 `_Prec`  
 Počet platných číslic k zobrazení, nebo počet číslic za desetinnou čárkou v pevné zápisu.  
  
### <a name="return-value"></a>Návratová hodnota  
  
 Vrátí první členská funkce uložené [přesnost zobrazení](../standard-library/ios-base-class.md). Druhý člen funkce úložiště `_Prec` v zobrazení přesnost a vrátí jeho předchozí uložené hodnoty.  
  
### <a name="remarks"></a>Poznámky  
  
 Čísla s plovoucí desetinnou čárkou jsou zobrazeny v pevné zápis se [pevné](../standard-library/ios-functions.md#fixed).  
  
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
  
##  <a name="pword"></a>ios_base::pword  
  
 Přiřadí hodnotu ukládaly jako `pword`.  
  
```  
void *& pword(int _Idx);
```  
  
### <a name="parameters"></a>Parametry  
 `_Idx`  
 Index hodnota, která má jako úložiště `pword`.  
  
### <a name="remarks"></a>Poznámky  
  
 Členská funkce vrátí odkaz na element _ *Idx* extensible pole elementy typu `void` ukazatel. Všechny elementy jsou k dispozici efektivně a původně uložení ukazatele null. Vrácený odkaz je neplatný po další volání `pword` pro objekt, po objektu je změnit voláním **basic_ios::**[copyfmt –](../standard-library/basic-ios-class.md#copyfmt), nebo po objekt zničena.  
  
 Pokud _ *Idx* záporné, nebo pokud je k dispozici pro element jedinečný úložiště, volá funkci [setstate –](../standard-library/basic-ios-class.md#setstate)**(badbit)** a vrátí odkaz, který nemusí být jedinečný.  
  
 K získání jedinečný index pro použití ve všech objektech typu `ios_base`, volání [xalloc –](#xalloc).  
  
### <a name="example"></a>Příklad  
  
  V tématu [xalloc –](#xalloc) příklad použití `pword`.  
  
##  <a name="register_callback"></a>ios_base::register_callback  
  
 Určuje funkce zpětného volání.  
  
```  
void register_callback(
    event_callback pfn, int idx);
```  
  
### <a name="parameters"></a>Parametry  
 `pfn`  
 Ukazatel na funkci zpětného volání.  
  
 `idx`  
 Uživatelem definované číslo.  
  
### <a name="remarks"></a>Poznámky  
  
 Členská funkce nabízených oznámení dvojici `{pfn, idx}` do zásobníku uložené zpětného volání [zpětného volání zásobníku](../standard-library/ios-base-class.md). Při zpětné volání událostí **ev** se použije v hlášení, funkce se nazývají, z registru, v opačném pořadí podle výrazu `(*pfn)(ev, *this, idx)`.  
 
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
 
##  <a name="seekdir"></a>ios_base::seekdir  
  
Určuje počáteční bod pro posunutí operace.  
  
```  
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
  
Typ je výčtového typu, který popisuje objekt, který může ukládat režimu seek použít jako argument pro členské funkce několik iostream – třídy. Příznak odlišné hodnoty jsou:  
 
- **transakce od**, k vyhledání (alter aktuální čtení nebo zápisu pozice) relativně k na začátek pořadí (pole, datový proud nebo soubor).  
 
- **Měna**, k vyhledání relativně k na aktuální pozici v sekvenci.  
 
- **end**, k vyhledání relativně ke konci pořadí.  
 
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
  
##  <a name="setf"></a>ios_base::SETF  
  
Nastaví zadaný příznaků.  

```    
fmtflags setf(  
    fmtflags _Mask  
);  
fmtflags setf(  
    fmtflags _Mask,  
    fmtflags _Unset  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Mask`  
    Příznaky tak, aby zapnout.  
 
 *_Unset* příznaky tak, aby vypnout.  
 
### <a name="return-value"></a>Návratová hodnota  
    The previous format flags  
 
### <a name="remarks"></a>Poznámky  
    The first member function effectively calls [flags](#flags)(_ *Mask* &#124; \_ *Flags*) (set selected bits) and then returns the previous format flags. The second member function effectively calls **flags**(\_ *Mask* **& fmtfl, flags& ~**`_Mask`) (replace selected bits under a mask) and then returns the previous format flags.  
 
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
 
##  <a name="sync_with_stdio"></a>ios_base::sync_with_stdio  
  
Zajišťuje, že operace běhové knihovny jazyka C a iostream vyskytnout v pořadí, ve kterém se zobrazují ve zdrojovém kódu.  
  
```  
static bool sync_with_stdio(  
   bool _Sync = true  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Sync`  
    Zda jsou všechny datové proudy synchronizované s **stdio**.  
 
### <a name="return-value"></a>Návratová hodnota  
    Previous setting for this function.  
 
### <a name="remarks"></a>Poznámky  
    The static member function stores a **stdio** sync flag, which is initially **true**. When **true**, this flag ensures that operations on the same file are properly synchronized between the [iostreams](../standard-library/iostreams-conventions.md) functions and those defined in the C++ Standard Library. Otherwise, synchronization may or may not be guaranteed, but performance may be improved. The function stores `_Sync` in the **stdio** sync flag and returns its previous stored value. You can call it reliably only before performing any operations on the standard streams.  
 
##  <a name="unsetf"></a>ios_base::unsetf  
  
Způsobí, že zadaný příznaky tak, aby být vypnutý.  
  
```  
void unsetf(  
   fmtflags _Mask  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Mask`  
    Příznaky, které chcete vypnout.  
 
### <a name="remarks"></a>Poznámky  
    The member function effectively calls [flags](#flags)(`~`*_Mask* **& flags**) (clear selected bits).  
 
### <a name="example"></a>Příklad  
    See [ios_base::setf](#setf) for a sample of using `unsetf`.  
 
##  <a name="width"></a>ios_base::Width  
  
Nastaví délku do výstupního datového proudu.  
  
```  
streamsize width( ) const;  
streamsize width(  
   streamsize _Wide  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Wide`  
    Požadovaná velikost výstupního datového proudu.  
 
### <a name="return-value"></a>Návratová hodnota  

    The current width setting.  
 
### <a name="remarks"></a>Poznámky  

    The first member function returns the stored field width. The second member function stores `_Wide` in the field width and returns its previous stored value.  
 
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
 
##  <a name="xalloc"></a>ios_base::xalloc  
  
    Specifies that a variable is part of the stream.  
  
```  
static int xalloc( );  
```  
 
### <a name="return-value"></a>Návratová hodnota  
    The static member function returns a stored static value, which it increments on each call.  
 
### <a name="remarks"></a>Poznámky  
    You can use the return value as a unique index argument when calling the member functions [iword](#iword) or [pword](#pword).  
 
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
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream – programování](../standard-library/iostream-programming.md)   
 [iostreams – konvence](../standard-library/iostreams-conventions.md)
