---
title: CTime – třída
ms.date: 10/18/2018
f1_keywords:
- CTime
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
ms.openlocfilehash: df86d35e52ea386d2750a4af7357e66a8d08f79f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744708"
---
# <a name="ctime-class"></a>CTime – třída

Představuje datum a absolutní čas.

## <a name="syntax"></a>Syntaxe

```
class CTime
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CTime::CTime](#ctime)|Vytvoří `CTime` objekty různými způsoby.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTime::Format](#format)|Převede `CTime` do formátovaný řetězec objektu – podle místního časového pásma.|
|[CTime::FormatGmt](#formatgmt)|Převede `CTime` do formátovaný řetězec objektu – podle standardu UTC.|
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Převede čas informací uložených v `CTime` objektu na strukturu DBTIMESTAMP Win32 kompatibilní.|
|[CTime::GetAsSystemTime](#getassystemtime)|Převede čas informací uložených v `CTime` objekt Win32 kompatibilní [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktury.|
|[CTime::GetCurrentTime](#getcurrenttime)|Vytvoří `CTime` objekt, který představuje aktuální čas (statické členské funkce).|
|[CTime::GetDay](#getday)|Vrátí den představují podle `CTime` objektu.|
|[CTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu, reprezentovaný `CTime` objektu.|
|[CTime::GetGmtTm](#getgmttm)|Rozdělí `CTime` objekt do součásti – podle standardu UTC.|
|[CTime::GetHour](#gethour)|Vrátí hodinu představovanou `CTime` objektu.|
|[CTime::GetLocalTm](#getlocaltm)|Rozdělí `CTime` objekt do součásti – podle místního časového pásma.|
|[CTime::GetMinute](#getminute)|Vrátí minutu reprezentována `CTime` objektu.|
|[CTime::GetMonth](#getmonth)|Vrátí měsíc reprezentována `CTime` objektu.|
|[CTime::GetSecond](#getsecond)|Vrátí sekundu reprezentována `CTime` objektu.|
|[CTime::GetTime](#gettime)|Vrátí **__time64_t –** hodnota daný `CTime` objektu.|
|[CTime::GetYear](#getyear)|Vrátí rok reprezentována `CTime` objektu.|
|[CTime::Serialize64](#serialize64)|Serializuje data do nebo z archivu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[Operator + –](#operator_add_-)|Tyto operátory sčítání a odečítání `CTimeSpan` a `CTime` objekty.|
|[Operator +=-=](#operator_add_eq_-_eq)|Tyto operátory sčítání a odečítání `CTimeSpan` objektů do a z tohoto `CTime` objektu.|
|[operátor =](#operator_eq)|Operátor přiřazení.|
|[operátor ==, < apod.](#ctime_comparison_operators)|Operátory porovnání.|

## <a name="remarks"></a>Poznámky

`CTime` nemá základní třídu.

`CTime` hodnoty jsou založeny na koordinovaný světový čas (UTC), což je totéž jako koordinovaný univerzální čas (greenwichský střední čas, GMT). Zobrazit [Správa času](../../c-runtime-library/time-management.md) informace o tom, jak se určuje časové pásmo.

Při vytváření `CTime` objektu, nastaven `nDST` parametr na hodnotu 0 označující, že je v platnosti (běžný čas), nebo na hodnotu větší než 0, která znamená že letního času je v platnosti, nebo na hodnotu menší než nula, která mají restart počíta C run-time knihovna kódu e, jestli (běžný čas) nebo letního času je v platnosti. `tm_isdst` je povinné pole. Pokud není nastavený, jeho hodnota není definována a návratovou hodnotu z [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) nepředvídatelné. Pokud `timeptr` odkazuje na strukturu tm vrácený z předchozího volání [asctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s –](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), nebo [localtime_s –](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), `tm_isdst` pole obsahuje správnou hodnotu.

Třídě doprovodných prvků [ctimespan –](../../atl-mfc-shared/reference/ctimespan-class.md), představuje časový interval.

`CTime` a `CTimeSpan` třídy nejsou určeny pro odvození. Vzhledem k tomu, že neexistují žádné virtuální funkce, velikost `CTime` a `CTimeSpan` objekty je přesně 8 bajtů. Většina členské funkce jsou vložené.

> [!NOTE]
>  Datum horní limit je 12/31/3000. Dolní mez je 1/1/1970 12:00:00 AM GMT.

Další informace o používání `CTime`, najdete v článcích [datum a čas](../../atl-mfc-shared/date-and-time.md), a [Správa času](../../c-runtime-library/time-management.md) v referenční dokumentace knihoven Run-Time.

> [!NOTE]
>  `CTime` Struktura se změnila z knihovny MFC 7.1 na 8.0 knihovny MFC. Pokud serializujete `CTime` struktury pomocí **operátor <<** v rámci MFC 8.0 nebo novější, výsledný soubor nebude možné číst ke starším verzím rozhraní knihovny MFC.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

##  <a name="ctime_comparison_operators"></a>  CTime – relační operátory

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

*čas*<br/>
`CTime` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Tyto operátory porovnávají dva absolutní časy a vrátí hodnotu, pokud je podmínka true. v opačném případě FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>  CTime::CTime

Vytvoří novou `CTime` objekt je inicializován s určený čas.

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

*čas*<br/>
A `__time64_t` časovou hodnotu, což je počet sekund, po 1. ledna 1970 UTC. Všimněte si, že to bude upravena na místní čas. Například, pokud jsou v New Yorku a vytvořit `CTime` objekt tím, že předáte parametr 0, [CTime::GetMonth](#getmonth) vrátí 12.

*nYear*, *nMonth*, *Nden*, *Nhodina*, *Nminimum*, *nSec*<br/>
Označuje hodnoty data a času, které se mají zkopírovat do nové `CTime` objektu.

*nDST*<br/>
Určuje, zda je v platnosti letní čas. Může mít jednu ze tří hodnot:

- *nDST* sada 0Standard čas je v platnosti.

- *nDST* nastaven na hodnotu větší než 0Daylight čas je v platnosti.

- *nDST* nastavena na hodnotu menší než výchozí 0The. Vypočítá automaticky, zda (běžný čas) nebo letní čas je v platnosti.

*wDosDate*, *wDosTime*<br/>
Hodnoty data a času zástupného kódu MS-DOS převést na hodnotu data a času a zkopírovány do nového `CTime` objektu.

*st*<br/>
A [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktura bude převeden na hodnotu data a času a zkopírovány do nového `CTime` objektu.

*FT*<br/>
A [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktura bude převeden na hodnotu data a času a zkopírovány do nového `CTime` objektu.

*dbts*<br/>
Odkaz na DBTIMESTAMP strukturu obsahující aktuální místní čas.

### <a name="remarks"></a>Poznámky

Níže je popsána jednotlivých konstruktor:

- `CTime();` Vytvoří neinicializované `CTime` objektu. Tento konstruktor umožňuje definovat `CTime` objektu pole. Takovými poli s platnou dobou před použitím měly by být inicializovány.

- `CTime( const CTime& );` Vytvoří `CTime` objektu z jiného `CTime` hodnotu.

- `CTime( __time64_t );` Vytvoří `CTime` objektu z **__time64_t –** typu. Tento konstruktor očekává, že čas UTC a převádí výsledek na místní čas před uložením výsledku.

- `CTime( int, int, ...);` Vytvoří `CTime` objekt z komponent místní čas pomocí jednotlivých komponent omezen na tyto rozsahy:

   |Součást|Rozsah|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Tento konstruktor vytvoří odpovídající převod na standard UTC. Ladicí verze knihovny Microsoft Foundation Class vyhodnotí, pokud jeden nebo více součástí času jsou mimo rozsah. Musíte ověřit argumenty před voláním. Tento konstruktor očekává, že místní čas.

- `CTime( WORD, WORD );` Vytvoří `CTime` objekt ze zadané hodnoty data a času zástupného kódu MS-DOS. Tento konstruktor očekává, že místní čas.

- `CTime( const SYSTEMTIME& );` Vytvoří `CTime` objektu z `SYSTEMTIME` struktury. Tento konstruktor očekává, že místní čas.

- `CTime( const FILETIME& );` Vytvoří `CTime` objektu z `FILETIME` struktury. Pravděpodobně nebude používat `CTime FILETIME` inicializace přímo. Pokud používáte `CFile` objekt pro manipulaci s souboru, `CFile::GetStatus` načte časové razítko souboru pro vás `CTime` objekt inicializován s `FILETIME` struktury. Tento konstruktor předpokládá čas ve standardu UTC a automaticky převede hodnotu na místní čas před uložením výsledku.

   > [!NOTE]
   > Pomocí konstruktoru `DBTIMESTAMP` parametr je k dispozici, pouze když OLEDB.h je součástí.

Další informace najdete v tématu [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) a [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktura v sadě Windows SDK. Viz také [zástupného kódu MS-DOS datum a čas](/windows/desktop/SysInfo/ms-dos-date-and-time) položku v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>  CTime::Format

Voláním této členské funkce k vytvoření formátovaného reprezentace hodnoty data a času.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Formátování řetězců podobně jako `printf` formátovací řetězec. Formátování kódů předchází procento (`%`) podepsat, jsou nahrazeny odpovídajícím `CTime` komponenty. Jiné znaky v řetězci formátování se zkopírují do vráceném řetězci beze změny. Zobrazit funkci run-time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) seznam formátovacích kódech.

*nFormatID*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který obsahuje formátovaný čas.

### <a name="remarks"></a>Poznámky

Pokud se stav tohoto `CTime` objekt má hodnotu null, vrácená hodnota je prázdný řetězec.

Tato metoda vyvolá výjimku, pokud hodnota data a času pro formátování není v rozsahu od půlnoci 1. ledna 1970 do 31. prosince 3000 koordinovaný světový čas (UTC).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>  CTime::FormatGmt

Generuje formátovaný řetězec, který odpovídá tomuto `CTime` objektu.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Určuje formátování řetězce podobné tomuto: `printf` formátovací řetězec. Zobrazit funkci run-time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) podrobnosti.

*nFormatID*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který obsahuje formátovaný čas.

### <a name="remarks"></a>Poznámky

Časová hodnota není převedena a proto odráží UTC.

Tato metoda vyvolá výjimku, pokud hodnota data a času pro formátování není v rozsahu od půlnoci 1. ledna 1970 do 31. prosince 3000 koordinovaný světový čas (UTC).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CTime::Format](#format).

##  <a name="getasdbtimestamp"></a>  CTime::GetAsDBTIMESTAMP

Voláním této členské funkce pro převod čas informací uložených v `CTime` objektu na strukturu DBTIMESTAMP Win32 kompatibilní.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parametry

*dbts*<br/>
Odkaz na DBTIMESTAMP strukturu obsahující aktuální místní čas.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Uloží výsledný čas v odkazované *dbts* struktury. `DBTIMESTAMP` Datová struktura inicializovat touto funkcí bude mít jeho `fraction` člen nastaven na hodnotu nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>  CTime::GetAsSystemTime

Voláním této členské funkce pro převod čas informací uložených v `CTime` objekt Win32 kompatibilní [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktura.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
Odkaz na [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) struktura, která bude obsahovat hodnota převedená data a času `CTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`GetAsSystemTime` uloží výsledný čas v odkazované *timeDest* struktury. `SYSTEMTIME` Datová struktura inicializovat touto funkcí bude mít jeho `wMilliseconds` člen nastaven na hodnotu nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>  CTime::GetCurrentTime

Vrátí `CTime` objekt, který představuje aktuální čas.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí aktuální systémový datum a čas v koordinovaný univerzální čas (UTC).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>  CTime::GetDay

Vrátí den představují podle `CTime` objektu.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí den v měsíci, na základě místního času v rozsahu od 1 do 31.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, je interní staticky přidělenou vyrovnávací paměť, který používá. Data v této vyrovnávací paměti je přepsána kvůli volání do jiných `CTime` členské funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>  CTime::GetDayOfWeek

Vrátí den v týdnu, reprezentovaný `CTime` objektu.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí den v týdnu založené na místní čas; 1 = neděle, 2 = pondělí, 7 = sobota.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti je přepsána kvůli volání do jiných `CTime` členské funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>  CTime::GetGmtTm

Získá **struktura tm** , který obsahuje dekompozice času obsaženému v tomto `CTime` objektu.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*<br/>
Body do vyrovnávací paměti, která bude dostávat časové údaje. Pokud tento ukazatel je NULL, je vyvolána výjimka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel vyplněné **struktura tm** jak jsou definovány ve vloženém souboru čas. H. Zobrazit [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) rozložení struktury.

### <a name="remarks"></a>Poznámky

`GetGmtTm` Vrátí čas UTC.

*druh* nemůže mít hodnotu NULL. Pokud chcete vrátit na původní chování, ve kterém *druh* může mít hodnotu NULL k označení, že interní, by měla sloužit staticky přidělené vyrovnávací paměti, pak nedefinované _SECURE_ATL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>  CTime::GetHour

Vrátí hodinu představovanou `CTime` objektu.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodinu na základě místního času v rozsahu 0 až 23.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti je přepsána kvůli volání do jiných `CTime` členské funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>  CTime::GetLocalTm

Získá **struktura tm** obsahující dekompozice času obsaženému v tomto `CTime` objektu.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*<br/>
Body do vyrovnávací paměti, která bude dostávat časové údaje. Pokud tento ukazatel je NULL, je vyvolána výjimka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel vyplněné **struktura tm** jak jsou definovány ve vloženém souboru čas. H. Zobrazit [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) rozložení struktury.

### <a name="remarks"></a>Poznámky

`GetLocalTm` Vrátí místní čas.

*druh* nemůže mít hodnotu NULL. Pokud chcete vrátit na původní chování, ve kterém *druh* může mít hodnotu NULL k označení, že interní, by měla sloužit staticky přidělené vyrovnávací paměti, pak nedefinované _SECURE_ATL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>  CTime::GetMinute

Vrátí minutu reprezentována `CTime` objektu.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí minuty, na základě místního času v rozsahu od 0 do 59.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti je přepsána kvůli volání do jiných `CTime` členské funkce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetHour](#gethour).

##  <a name="getmonth"></a>  CTime::GetMonth

Vrátí měsíc reprezentována `CTime` objektu.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí měsíc na základě místního času v rozsahu od 1 do 12 (1. ledna =).

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti je přepsána kvůli volání do jiných `CTime` členské funkce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetDay](#getday).

##  <a name="getsecond"></a>  CTime::GetSecond

Vrátí sekundu reprezentována `CTime` objektu.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí sekundy, na základě místního času v rozsahu od 0 do 59.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti je přepsána kvůli volání do jiných `CTime` členské funkce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetHour](#gethour).

##  <a name="gettime"></a>  CTime::GetTime

Vrátí **__time64_t –** hodnota daný `CTime` objektu.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Návratová hodnota

`GetTime` Vrátí počet sekund mezi aktuálním `CTime` objektu a 1. ledna 1970.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>  CTime::GetYear

Vrátí rok reprezentována `CTime` objektu.

```
int GetYear();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí rok, na základě místního času v rozsahu od 1,1970 pro 18 leden 2038 (včetně).

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti je přepsána kvůli volání do jiných `CTime` členské funkce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetDay](#getday).

##  <a name="operator_eq"></a>  CTime::operator =

Operátor přiřazení.

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parametry

*čas*<br/>
Hodnota nová data a času.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTime` objektu.

### <a name="remarks"></a>Poznámky

Operátoru přiřazení. přetížení zkopíruje do této doby zdroj `CTime` objektu. Čas vnitřního úložiště `CTime` objekt je nezávislé na časové pásmo. Převod časového pásma není nutné během přiřazení.

##  <a name="operator_add_-"></a>  CTime::operator +, -

Tyto operátory sčítání a odečítání `CTimeSpan` a `CTime` objekty.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*timeSpan*<br/>
`CTimeSpan` Objekt, který se má přičíst nebo odečíst.

*čas*<br/>
`CTime` Objekt má být odečtena.

### <a name="return-value"></a>Návratová hodnota

A `CTime` nebo `CTimeSpan` objekt představující výsledek operace.

### <a name="remarks"></a>Poznámky

`CTime` objekty představují absolutní časové `CTimeSpan` představovat relativní časové. První dva operátory umožňují operátorů sčítání a odečítání `CTimeSpan` objektů do a z `CTime` objekty. Operátor třetí umožňuje odečte jeden `CTime` objektu z jiného pozastavit `CTimeSpan` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTime::operator +=-=

Tyto operátory sčítání a odečítání `CTimeSpan` objektů do a z tohoto `CTime` objektu.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CTimeSpan` Objekt, který se má přičíst nebo odečíst.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTime` objektu.

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují operátorů sčítání a odečítání `CTimeSpan` objektů do a z tohoto `CTime` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>  CTime::Serialize64

> [!NOTE]
> Tato metoda je pouze k dispozici v projektech knihovny MFC.

Serializuje data přidružená k členské proměnné do nebo z archivu.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
`CArchive` Objekt, který chcete aktualizovat.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CArchive` objektu.

## <a name="see-also"></a>Viz také:

[asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)<br/>
[_ftime_s, _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)<br/>
[gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
