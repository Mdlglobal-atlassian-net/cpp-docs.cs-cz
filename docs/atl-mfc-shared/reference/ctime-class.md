---
title: CTime – třída
ms.date: 10/18/2018
f1_keywords:
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
ms.openlocfilehash: e6e471fe648c5fa370cce750e8569e158eb1ffe4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317573"
---
# <a name="ctime-class"></a>CTime – třída

Představuje absolutní čas a datum.

## <a name="syntax"></a>Syntaxe

```
class CTime
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CTime::CTime](#ctime)|Vytváří `CTime` objekty různými způsoby.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTime::Formát](#format)|Převede `CTime` objekt na formátovaný řetězec na základě místního časového pásma.|
|[CTime::FormátGmt](#formatgmt)|Převede `CTime` objekt na formátovaný řetězec – založený na utc.|
|[Ctime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Převede informace o čase `CTime` uložené v objektu na strukturu DBTIMESTAMP kompatibilní s win32.|
|[Ctime::GetasSystemTime](#getassystemtime)|Převede informace o čase `CTime` uložené v objektu na strukturu [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) kompatibilní s win32.|
|[CTime::GetCurrentTime](#getcurrenttime)|Vytvoří `CTime` objekt, který představuje aktuální čas (statickou člennou funkci).|
|[CTime::GetDay](#getday)|Vrátí den představující `CTime` objektem.|
|[CTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu `CTime` reprezentované objektem.|
|[CTime::GetGmtTm](#getgmttm)|Rozdělí `CTime` objekt na součásti – na základě UTC.|
|[CTime::GetHour](#gethour)|Vrátí hodinu reprezentovanou objektem. `CTime`|
|[CTime::GetLocalTm](#getlocaltm)|Rozdělí `CTime` objekt na součásti – na základě místního časového pásma.|
|[CTime::GetMinute](#getminute)|Vrátí minutu reprezentovanou objektem. `CTime`|
|[CTime::GetMonth](#getmonth)|Vrátí měsíc reprezentované objektem. `CTime`|
|[CTime::GetSecond](#getsecond)|Vrátí druhý reprezentované objektem. `CTime`|
|[CTime::GetTime](#gettime)|Vrátí **hodnotu __time64_t** `CTime` pro daný objekt.|
|[CTime::GetYear](#getyear)|Vrátí rok reprezentované objektem. `CTime`|
|[CTime::Serializovat64](#serialize64)|Serializuje data do nebo z archivu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor + -](#operator_add_-)|Tyto operátory přičítat a odečítat `CTimeSpan` a `CTime` objekty.|
|[operátor +=, -=](#operator_add_eq_-_eq)|Tyto operátory přidat `CTimeSpan` a odečíst `CTime` objekt a od tohoto objektu.|
|[operátor =](#operator_eq)|Operátor přiřazení.|
|[operátor ==, < atd.](#ctime_comparison_operators)|Operátory porovnání.|

## <a name="remarks"></a>Poznámky

`CTime`nemá základní třídu.

`CTime`hodnoty jsou založeny na koordinovaném univerzálním čase (UTC), což odpovídá koordinovanému univerzálnímu času (Greenwichský střední čas, GMT). Informace o tom, jak je časové pásmo určeno, naleznete v tématu [Time Management.](../../c-runtime-library/time-management.md)

Při vytváření `CTime` objektu nastavte `nDST` parametr na hodnotu 0, která označuje, že je platný standardní čas, nebo na hodnotu větší než 0, která označuje, že platí letní čas, nebo na hodnotu menší než nula, aby kód knihovny běhu C počítal, zda je v platnosti standardní čas nebo letní čas. `tm_isdst`je povinné pole. Pokud není nastavena, jeho hodnota je nedefinovaná a vrácená hodnota z [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) je nepředvídatelná. Pokud `timeptr` odkazuje na strukturu tm vrácenou předchozím voláním [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md) `tm_isdst` , [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)nebo [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), pole obsahuje správnou hodnotu.

Doprovodná třída [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)představuje časový interval.

`CTime` Třídy `CTimeSpan` a nejsou určeny pro odvození. Vzhledem k tomu, že `CTime` neexistují `CTimeSpan` žádné virtuální funkce, velikost a objekty je přesně 8 bajtů. Většina členských funkcí je včleněná.

> [!NOTE]
> Horní limit data je 12/31/3000. Dolní limit je 1/1/1970 12:00:00 GMT.

Další informace o `CTime`použití naleznete v článcích [Datum a čas](../../atl-mfc-shared/date-and-time.md)a Správa [času](../../c-runtime-library/time-management.md) v referenční knihovně za běhu.

> [!NOTE]
> Struktura `CTime` se změnila z mfc 7.1 na MFC 8.0. Pokud serializujete `CTime` strukturu pomocí **operátoru <<** pod knihovnou MFC 8.0 nebo novější verzí, výsledný soubor nebude čitelný ve starších verzích knihovny MFC.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

## <a name="ctime-comparison-operators"></a><a name="ctime_comparison_operators"></a>Operátory porovnání CTime

Operátory porovnání.

```
bool operator==(CTime time) const throw();
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*Čas*<br/>
Objekt, `CTime` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Tyto operátory porovnat dva absolutní časy a vrátit TRUE, pokud je podmínka true; jinak FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

## <a name="ctimectime"></a><a name="ctime"></a>CTime::CTime

Vytvoří nový `CTime` objekt inicializovaný se zadaným časem.

```
CTime() throw();
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts, int nDST = -1) throw();
```

### <a name="parameters"></a>Parametry

*timeSrc*<br/>
Označuje `CTime` objekt, který již existuje.

*Čas*<br/>
Časová `__time64_t` hodnota, což je počet sekund po 1. Všimněte si, že to bude upraveno podle místního času. Například pokud jste v New Yorku a vytvořit `CTime` objekt předáním parametr 0, [CTime::GetMonth](#getmonth) vrátí 12.

*nRok*, *nMěsíc*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Označuje hodnoty data a času, které `CTime` mají být zkopírovány do nového objektu.

*nDST*<br/>
Označuje, zda je letní čas v platnosti. Může mít jednu ze tří hodnot:

- *nDST* nastavena na 0Standardní čas je v platnosti.

- *nDST* nastavena na hodnotu větší než 0Letní čas úspory je v platnosti.

- *nDST* nastavena na hodnotu menší než 0Výchozí hodnota. Automaticky vypočítá, zda je v platnosti standardní čas nebo letní čas.

*wDosDate*, *wDosTime*<br/>
Hodnoty data a času služby MS-DOS, které mají být převedeny na hodnotu data a času a zkopírovány do nového `CTime` objektu.

*St*<br/>
Struktura [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) která má být převedena na hodnotu `CTime` data a času a zkopírována do nového objektu.

*Ft*<br/>
Struktura [FILETIME,](/windows/win32/api/minwinbase/ns-minwinbase-filetime) která má být převedena na hodnotu `CTime` data a času a zkopírována do nového objektu.

*dbts*<br/>
Odkaz na strukturu DBTIMESTAMP obsahující aktuální místní čas.

### <a name="remarks"></a>Poznámky

Každý konstruktor je popsán níže:

- `CTime();`Vytvoří neinicializovaný `CTime` objekt. Tento konstruktor umožňuje `CTime` definovat pole objektů. Před použitím byste měli inicializovat tato pole s platnými časy.

- `CTime( const CTime& );`Vytvoří `CTime` objekt z `CTime` jiné hodnoty.

- `CTime( __time64_t );`Vytvoří `CTime` objekt z **typu __time64_t.** Tento konstruktor očekává čas UTC a převede výsledek na místní čas před uložením výsledku.

- `CTime( int, int, ...);`Vytvoří `CTime` objekt z komponent místního času s každou součástí omezena na následující oblasti:

   |Komponenta|Rozsah|
   |---------------|-----------|
   |*nRok*|1970-3000|
   |*nMěsíc*|1-12|
   |*nDen*|1-31|
   |*nHodina*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Tento konstruktor provede příslušný převod na UTC. Ladicí verze knihovny tříd Microsoft Foundation uplatňuje, pokud jedna nebo více časových součástí jsou mimo rozsah. Před voláním je nutné ověřit argumenty. Tento konstruktor očekává místní čas.

- `CTime( WORD, WORD );`Vytvoří `CTime` objekt ze zadaných hodnot data a času ms-dos. Tento konstruktor očekává místní čas.

- `CTime( const SYSTEMTIME& );`Vytvoří `CTime` objekt ze `SYSTEMTIME` struktury. Tento konstruktor očekává místní čas.

- `CTime( const FILETIME& );`Vytvoří `CTime` objekt ze `FILETIME` struktury. S největší pravděpodobností `CTime FILETIME` nebudete používat inicializaci přímo. Pokud použijete `CFile` objekt k manipulaci `CFile::GetStatus` se souborem, načte `CTime` časové razítko `FILETIME` souboru pro vás prostřednictvím objektu inicializovaného se strukturou. Tento konstruktor předpokládá čas založený na UTC a automaticky převede hodnotu na místní čas před uložením výsledku.

   > [!NOTE]
   > Konstruktor pomocí `DBTIMESTAMP` parametru je k dispozici pouze v případě, že je součástí balení OLEDB.h.

Další informace naleznete v [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) a [filetime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) struktury v sadě Windows SDK. Viz také položka [Datum a čas systému MS-DOS](/windows/win32/SysInfo/ms-dos-date-and-time) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

## <a name="ctimeformat"></a><a name="format"></a>CTime::Formát

Volání této členské funkce vytvořit formátované reprezentace hodnoty data a času.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Formátovací řetězec podobný řetězci `printf` formátování. Kódy formátování, před nimiž`%`je podepsáno procento ( `CTime` ) , jsou nahrazeny odpovídající komponentou. Ostatní znaky ve formátovacím řetězci jsou zkopírovány beze změny do vráceného řetězce. Seznam kódů formátování naleznete v [době](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) běhu.

*nID formátu*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který obsahuje formátovaný čas.

### <a name="remarks"></a>Poznámky

Pokud je stav `CTime` tohoto objektu null, vrácená hodnota je prázdný řetězec.

Tato metoda vyvolá výjimku, pokud hodnota data a času formátne v rozsahu od půlnoci, 1 leden 1970 do 31 prosince 3000 univerzální koordinovaný čas (UTC).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

## <a name="ctimeformatgmt"></a><a name="formatgmt"></a>CTime::FormátGmt

Generuje formátovaný řetězec, který odpovídá `CTime` tomuto objektu.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Určuje formátovací řetězec podobný řetězci `printf` formátování. Podrobnosti naleznete v době běhu [funkce strftime.](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)

*nID formátu*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

[CString,](../../atl-mfc-shared/reference/cstringt-class.md) který obsahuje formátovaný čas.

### <a name="remarks"></a>Poznámky

Hodnota času není převedena a odráží tedy čas UTC.

Tato metoda vyvolá výjimku, pokud hodnota data a času formátne v rozsahu od půlnoci, 1 leden 1970 do 31 prosince 3000 univerzální koordinovaný čas (UTC).

### <a name="example"></a>Příklad

Viz příklad [ctime::Format](#format).

## <a name="ctimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>Ctime::GetAsDBTIMESTAMP

Volání této členské funkce převést informace `CTime` o čase uložené v objektu na Win32 kompatibilní DBTIMESTAMP struktury.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parametry

*dbts*<br/>
Odkaz na strukturu DBTIMESTAMP obsahující aktuální místní čas.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Uloží výsledný čas do odkazované struktury *dbts.* Datová `DBTIMESTAMP` struktura inicializovaná `fraction` touto funkcí bude mít svůj člen nastaven na nulu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

## <a name="ctimegetassystemtime"></a><a name="getassystemtime"></a>Ctime::GetasSystemTime

Volání této členské funkce převést informace `CTime` o čase uložené v objektu na Win32 kompatibilní [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) struktury.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
Odkaz na strukturu [SYSTEMTIME,](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) která bude obsahovat převedenou `CTime` hodnotu data a času objektu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

`GetAsSystemTime`ukládá výsledný čas v odkazované *struktuře timeDest.* Datová `SYSTEMTIME` struktura inicializovaná `wMilliseconds` touto funkcí bude mít svůj člen nastaven na nulu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

## <a name="ctimegetcurrenttime"></a><a name="getcurrenttime"></a>CTime::GetCurrentTime

Vrátí `CTime` objekt, který představuje aktuální čas.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí aktuální systémové datum a čas v koordinovaném univerzálním čase (UTC).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

## <a name="ctimegetday"></a><a name="getday"></a>CTime::GetDay

Vrátí den představující `CTime` objektem.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí den v měsíci na základě místního času v rozsahu 1 až 31.

### <a name="remarks"></a>Poznámky

Tato funkce `GetLocalTm`volá , který používá vnitřní, staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti jsou přepsána z důvodu volání jiných `CTime` členských funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

## <a name="ctimegetdayofweek"></a><a name="getdayofweek"></a>CTime::GetDayOfWeek

Vrátí den v týdnu `CTime` reprezentované objektem.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí den v týdnu na základě místního času; 1 = neděle, 2 = pondělí, až 7 = sobota.

### <a name="remarks"></a>Poznámky

Tato funkce `GetLocalTm`volá , který používá vnitřní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti jsou přepsána z důvodu volání jiných `CTime` členských funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

## <a name="ctimegetgmttm"></a><a name="getgmttm"></a>CTime::GetGmtTm

Získá **strukturu tm,** která obsahuje rozklad času obsaženého v tomto `CTime` objektu.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Odkazuje na vyrovnávací paměť, která obdrží data času. Pokud tento ukazatel je NULL, je vyvolána výjimka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyplněnou **strukturu tm,** jak je definována v souboru zahrnutí TIME. H. Rozložení struktury naleznete v [_gmtime64 gmtime, _gmtime32, _gmtime64.](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)

### <a name="remarks"></a>Poznámky

`GetGmtTm`vrátí UTC.

*ptm* nemůže být null. Pokud se chcete vrátit ke starému chování, ve kterém *ptm* může být NULL označuje, že vnitřní, staticky přidělené vyrovnávací paměti by měly být použity, pak nedefinovat _SECURE_ATL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

## <a name="ctimegethour"></a><a name="gethour"></a>CTime::GetHour

Vrátí hodinu reprezentovanou objektem. `CTime`

```
int GetHour() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodinu na základě místního času v rozsahu 0 až 23.

### <a name="remarks"></a>Poznámky

Tato funkce `GetLocalTm`volá , který používá vnitřní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti jsou přepsána z důvodu volání jiných `CTime` členských funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

## <a name="ctimegetlocaltm"></a><a name="getlocaltm"></a>CTime::GetLocalTm

Získá **strukturu tm** obsahující rozklad času obsaženého v `CTime` tomto objektu.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*Ptm*<br/>
Odkazuje na vyrovnávací paměť, která obdrží data času. Pokud tento ukazatel je NULL, je vyvolána výjimka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyplněnou **strukturu tm,** jak je definována v souboru zahrnutí TIME. H. Rozložení struktury naleznete v [_gmtime64 gmtime, _gmtime32, _gmtime64.](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)

### <a name="remarks"></a>Poznámky

`GetLocalTm`vrátí místní čas.

*ptm* nemůže být null. Pokud se chcete vrátit ke starému chování, ve kterém *ptm* může být NULL označuje, že vnitřní, staticky přidělené vyrovnávací paměti by měly být použity, pak nedefinovat _SECURE_ATL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

## <a name="ctimegetminute"></a><a name="getminute"></a>CTime::GetMinute

Vrátí minutu reprezentovanou objektem. `CTime`

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí minutu na základě místního času v rozsahu 0 až 59.

### <a name="remarks"></a>Poznámky

Tato funkce `GetLocalTm`volá , který používá vnitřní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti jsou přepsána z důvodu volání jiných `CTime` členských funkcí.

### <a name="example"></a>Příklad

Viz příklad pro [GetHour](#gethour).

## <a name="ctimegetmonth"></a><a name="getmonth"></a>CTime::GetMonth

Vrátí měsíc reprezentované objektem. `CTime`

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí měsíc na základě místního času v rozsahu 1 až 12 (1 = leden).

### <a name="remarks"></a>Poznámky

Tato funkce `GetLocalTm`volá , který používá vnitřní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti jsou přepsána z důvodu volání jiných `CTime` členských funkcí.

### <a name="example"></a>Příklad

Viz příklad pro [GetDay](#getday).

## <a name="ctimegetsecond"></a><a name="getsecond"></a>CTime::GetSecond

Vrátí druhý reprezentované objektem. `CTime`

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí druhý, na základě místního času v rozsahu 0 až 59.

### <a name="remarks"></a>Poznámky

Tato funkce `GetLocalTm`volá , který používá vnitřní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti jsou přepsána z důvodu volání jiných `CTime` členských funkcí.

### <a name="example"></a>Příklad

Viz příklad pro [GetHour](#gethour).

## <a name="ctimegettime"></a><a name="gettime"></a>CTime::GetTime

Vrátí **hodnotu __time64_t** `CTime` pro daný objekt.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Návratová hodnota

`GetTime`vrátí počet sekund mezi aktuální `CTime` objekt a 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

## <a name="ctimegetyear"></a><a name="getyear"></a>CTime::GetYear

Vrátí rok reprezentované objektem. `CTime`

```
int GetYear();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí rok na základě místního času v rozsahu leden 1,1970, do 18 leden 2038 (včetně).

### <a name="remarks"></a>Poznámky

Tato funkce `GetLocalTm`volá , který používá vnitřní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti jsou přepsána z důvodu volání jiných `CTime` členských funkcí.

### <a name="example"></a>Příklad

Viz příklad pro [GetDay](#getday).

## <a name="ctimeoperator-"></a><a name="operator_eq"></a>CTime::operátor =

Operátor přiřazení.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parametry

*Čas*<br/>
Nová hodnota data a času.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTime` objekt.

### <a name="remarks"></a>Poznámky

Tento operátor přetíženého přiřazení zkopíruje `CTime` zdrojový čas do tohoto objektu. Vnitřní časové úložiště `CTime` v objektu je nezávislé na časovém pásmu. Převod časového pásma není nutný během přiřazení.

## <a name="ctimeoperator---"></a><a name="operator_add_-"></a>CTime::operátor +, -

Tyto operátory přičítat a odečítat `CTimeSpan` a `CTime` objekty.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*Timespan*<br/>
Objekt, `CTimeSpan` který má být přidán nebo odečten.

*Čas*<br/>
Objekt, `CTime` který má být odečten.

### <a name="return-value"></a>Návratová hodnota

A `CTime` `CTimeSpan` nebo objekt představující výsledek operace.

### <a name="remarks"></a>Poznámky

`CTime`objekty představují `CTimeSpan` absolutní čas, objekty představují relativní čas. První dva operátory umožňují přidávat `CTimeSpan` a odečítat objekty do objektů a od `CTime` nich. Třetí operátor umožňuje odečíst `CTime` jeden objekt od `CTimeSpan` druhého výnos objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

## <a name="ctimeoperator---"></a><a name="operator_add_eq_-_eq"></a>CTime::operátor +=, -=

Tyto operátory přidat `CTimeSpan` a odečíst `CTime` objekt a od tohoto objektu.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Objekt, `CTimeSpan` který má být přidán nebo odečten.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTime` objekt.

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují přidat a `CTimeSpan` odečíst objekt `CTime` a od tohoto objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

## <a name="ctimeserialize64"></a><a name="serialize64"></a>CTime::Serializovat64

> [!NOTE]
> Tato metoda je k dispozici pouze v projektech knihovny MFC.

Serializuje data přidružená k členské proměnné do nebo z archivu.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Objekt, `CArchive` který chcete aktualizovat.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CArchive` objekt.

## <a name="see-also"></a>Viz také

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
