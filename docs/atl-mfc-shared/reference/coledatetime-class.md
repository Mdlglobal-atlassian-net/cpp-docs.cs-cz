---
title: COleDateTime – třída
ms.date: 03/27/2019
f1_keywords:
- COleDateTime
- ATLCOMTIME/ATL::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::COleDateTime
- ATLCOMTIME/ATL::COleDateTime::Format
- ATLCOMTIME/ATL::COleDateTime::GetAsDBTIMESTAMP
- ATLCOMTIME/ATL::COleDateTime::GetAsSystemTime
- ATLCOMTIME/ATL::COleDateTime::GetAsUDATE
- ATLCOMTIME/ATL::COleDateTime::GetCurrentTime
- ATLCOMTIME/ATL::COleDateTime::GetDay
- ATLCOMTIME/ATL::COleDateTime::GetDayOfWeek
- ATLCOMTIME/ATL::COleDateTime::GetDayOfYear
- ATLCOMTIME/ATL::COleDateTime::GetHour
- ATLCOMTIME/ATL::COleDateTime::GetMinute
- ATLCOMTIME/ATL::COleDateTime::GetMonth
- ATLCOMTIME/ATL::COleDateTime::GetSecond
- ATLCOMTIME/ATL::COleDateTime::GetStatus
- ATLCOMTIME/ATL::COleDateTime::GetYear
- ATLCOMTIME/ATL::COleDateTime::ParseDateTime
- ATLCOMTIME/ATL::COleDateTime::SetDate
- ATLCOMTIME/ATL::COleDateTime::SetDateTime
- ATLCOMTIME/ATL::COleDateTime::SetStatus
- ATLCOMTIME/ATL::COleDateTime::SetTime
- ATLCOMTIME/ATL::COleDateTime::m_dt
- ATLCOMTIME/ATL::COleDateTime::m_status
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
ms.openlocfilehash: 8ba09430427b6ece8ae5956912cbcc40fb33fcf2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747168"
---
# <a name="coledatetime-class"></a>COleDateTime – třída

Zapouzdřuje `DATE` datový typ, který se používá v automatizaci OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDateTime
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Vytvoří `COleDateTime` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDateTime::Formát](#format)|Generuje formátovaný řetězec reprezentace `COleDateTime` objektu.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Volání této metody získat čas `COleDateTime` v `DBTIMESTAMP` objektu jako datové struktury.|
|[COleDateTime::GetasSystemTime](#getassystemtime)|Volání této metody získat čas `COleDateTime` v objektu jako [systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) datové struktury.|
|[COleDateTime::GetasuDATE](#getasudate)|Volání této metody získat čas `COleDateTime` v `UDATE` jako datové struktury.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Vytvoří `COleDateTime` objekt, který představuje aktuální čas (statickou člennou funkci).|
|[COleDateTime::GetDay](#getday)|Vrátí den, `COleDateTime` který tento objekt představuje (1 - 31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu, který tento `COleDateTime` objekt představuje (neděle = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Vrátí den v roce, který tento `COleDateTime` objekt představuje (Jan 1 = 1).|
|[COleDateTime::GetHour](#gethour)|Vrátí hodinu, kterou tento `COleDateTime` objekt představuje (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Vrátí minutu, `COleDateTime` kterou tento objekt představuje (0 - 59).|
|[COleDateTime::GetMonth](#getmonth)|Vrátí měsíc, `COleDateTime` který tento objekt představuje (1 - 12).|
|[COleDateTime::GetSecond](#getsecond)|Vrátí druhý `COleDateTime` tento objekt představuje (0 - 59).|
|[COleDateTime::GetStatus](#getstatus)|Získá stav (platnost) tohoto `COleDateTime` objektu.|
|[COleDateTime::GetYear](#getyear)|Vrátí rok, `COleDateTime` který tento objekt představuje.|
|[COleDateTime::PArseDateTime](#parsedatetime)|Přečte hodnotu data a času z `COleDateTime`řetězce a nastaví hodnotu .|
|[COleDateTime::SetDate](#setdate)|Nastaví hodnotu `COleDateTime` tohoto objektu na zadanou hodnotu pouze pro datum.|
|[COleDateTime::SetDateTime](#setdatetime)|Nastaví hodnotu `COleDateTime` tohoto objektu na zadanou hodnotu data a času.|
|[COleDateTime::SetStatus](#setstatus)|Nastaví stav (platnost) `COleDateTime` tohoto objektu.|
|[COleDateTime::SetTime](#settime)|Nastaví hodnotu `COleDateTime` tohoto objektu na zadanou hodnotu pouze pro čas.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[COleDateTime::operator ==, COleDateTime::operátor < atd.](#coledatetime_relational_operators)|Porovnejte dvě `COleDateTime` hodnoty.|
|[COleDateTime::operátor +, COleDateTime::operátor -](#operator_add_-)|Přidejte a `COleDateTime` odečtěte hodnoty.|
|[COleDateTime::operátor +=, COleDateTime::operator -=](#operator_add_eq_-_eq)|Přidejte a `COleDateTime` odečtěte `COleDateTime` hodnotu od tohoto objektu.|
|[COleDateTime::operátor =](#operator_eq)|Zkopíruje `COleDateTime` hodnotu.|
|[COleDateTime::datum operátora, cOleDateTime::datum operátora*](#operator_date)|Převede `COleDateTime` hodnotu `DATE` na `DATE*`nebo nebo .|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Obsahuje podkladpro `DATE` `COleDateTime` tento objekt.|
|[COleDateTime::m_status](#m_status)|Obsahuje stav tohoto `COleDateTime` objektu.|

## <a name="remarks"></a>Poznámky

`COleDateTime`nemá základní třídu.

Jedná se o jeden z možných typů pro datový typ [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) automatizace OLE. Hodnota `COleDateTime` představuje absolutní hodnotu data a času.

Typ `DATE` je implementován jako hodnota s plovoucí desetinnou tácem. Dny se měří od 30.12.1899, o půlnoci. V následující tabulce jsou uvedena některá data a jejich přidružené hodnoty:

|Datum|Hodnota|
|----------|-----------|
|29. prosince 1899, půlnoc|-1.0|
|29. prosince 1899, 6:00|-1.25|
|30. prosince 1899, půlnoc|0,0|
|31. prosince 1899, půlnoc|1.0|
|1. ledna 1900, 6:00|2.25|

> [!CAUTION]
> Ve výše uvedené tabulce, i když hodnoty dne stanou záporné před půlnocí 30. Například 6:00 AM je vždy reprezentován zlomkové hodnoty 0,25 bez ohledu na to, zda celé číslo představující den je kladný (po 30. prosinci 1899) nebo negativní (před 30. prosince 1899). To znamená, že jednoduché porovnání s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou desetinnou `COleDateTime` desetinnou a malou a kratší než 7:00 ve stejný den. **later**

Třída `COleDateTime` zpracovává data od 1.1.100 do 31.12.9999. Třída `COleDateTime` používá gregoriánský kalendář; nepodporuje juliánské termíny. `COleDateTime`ignoruje letní čas. (Viz [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Formát můžete `%y` použít k načtení dvoumístného roku pouze pro data začínající na 1900. Pokud použijete `%y` formát k datu před rokem 1900, kód vygeneruje selhání ASSERT.

Tento typ se také používá k reprezentaci pouze datum nebo pouze čas hodnoty. Podle konvence datum 0 (30. prosince 1899) se používá pro hodnoty pouze čas a čas 00:00 (půlnoc) se používá pro hodnoty pouze datum.

Pokud vytvoříte `COleDateTime` objekt pomocí data menšího než 100, datum je `GetYear` `GetMonth`přijato, ale následná `GetDay`volání do , `GetHour`, , `GetMinute`a `GetSecond` nezdaří a vrátí -1. Dříve bylo možné použít dvouciferná data, ale data musí být 100 nebo větší v knihovně MFC 4.2 a novější.

Chcete-li se vyhnout problémům, zadejte čtyřmístné datum. Příklad:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Základní aritmetické operace `COleDateTime` pro hodnoty používají doprovodnou třídu [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`hodnoty definují časový interval. Vztah mezi těmito třídami je podobný vztahu mezi [CTime](../../atl-mfc-shared/reference/ctime-class.md) a [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Další informace o `COleDateTime` `COleDateTimeSpan` a třídy naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** ATLComTime.h

## <a name="coledatetime-relational-operators"></a><a name="coledatetime_relational_operators"></a>Relační operátory COleDateTime

Operátory porovnání.

```
bool operator==(const COleDateTime& date) const throw();
bool operator!=(const COleDateTime& date) const throw();
bool operator<(const COleDateTime& date) const throw();
bool operator>(const COleDateTime& date) const throw();
bool operator<=(const COleDateTime& date) const throw();
bool operator>=(const COleDateTime& date) const throw();
```

### <a name="parameters"></a>Parametry

*Datum*<br/>
Objekt, `COleDateTime` který má být porovnán.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> ATLASSERT dojde, pokud jeden ze dvou operandů je neplatný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Příklad

Operátory **>=** ** \< **, **>**, **<** a , `COleDateTime` bude uplatňovat, pokud je objekt nastaven na hodnotu null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

## <a name="coledatetimecoledatetime"></a><a name="coledatetime"></a>COleDateTime::COleDateTime

Vytvoří `COleDateTime` objekt.

```
COleDateTime() throw();
COleDateTime(const VARIANT& varSrc) throw();
COleDateTime(DATE dtSrc) throw();
COleDateTime(time_t timeSrc) throw();
COleDateTime(__time64_t timeSrc) throw();
COleDateTime(const SYSTEMTIME& systimeSrc) throw();
COleDateTime(const FILETIME& filetimeSrc) throw();

COleDateTime(int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();

COleDateTime(WORD wDosDate,
    WORD wDosTime) throw();
COleDateTime(const DBTIMESTAMP& timeStamp) throw();
```

### <a name="parameters"></a>Parametry

*dateSrc*<br/>
Existující `COleDateTime` objekt, který má být `COleDateTime` zkopírován do nového objektu.

*varSrc*<br/>
Existující `VARIANT` datová struktura `COleVariant` (případně objekt), která má být převedena na hodnotu data `COleDateTime` a času (VT_DATE) a zkopírována do nového objektu.

*dtSrc*<br/>
Hodnota data a`DATE`času ( ), která `COleDateTime` má být zkopírována do nového objektu.

*timeSrc*<br/>
A `time_t` `__time64_t` nebo hodnota, která má být převedena na hodnotu data a času a zkopírována do nového `COleDateTime` objektu.

*systimeSrc*<br/>
Struktura, `SYSTEMTIME` která má být převedena na hodnotu data `COleDateTime` a času a zkopírována do nového objektu.

*filetimeSrc*<br/>
Struktura, `FILETIME` která má být převedena na hodnotu data `COleDateTime` a času a zkopírována do nového objektu. A `FILETIME` používá univerzální koordinovaný čas (UTC), takže pokud předáte místní čas ve struktuře, vaše výsledky budou nesprávné. Další informace naleznete v [části Časy souborů](/windows/win32/SysInfo/file-times) v sadě Windows SDK.

*nRok*, *nMěsíc*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Označte hodnoty data a času, `COleDateTime` které mají být zkopírovány do nového objektu.

*wDosDate*, *wDosTime*<br/>
Hodnoty data a času služby MS-DOS, které mají být převedeny na hodnotu data a času a zkopírovány do nového `COleDateTime` objektu.

*Časové razítko*<br/>
Odkaz na strukturu [DBTimeStamp](/dotnet/api/system.data.oledb.oledbtype) obsahující aktuální místní čas.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory `COleDateTime` vytvořit nové objekty inicializovány na zadanou hodnotu. V následující tabulce jsou uvedeny platné rozsahy pro každou komponentu data a času:

|Komponenta Datum a čas|Platný rozsah|
|--------------------------|-----------------|
|year|100 - 9999|
|month|0 - 12|
|day|0 - 31|
|hour|0 - 23|
|minute|0 - 59|
|second|0 - 59|

Všimněte si, že skutečná horní mez pro komponentu den se liší v závislosti na komponentách měsíc a rok. Podrobnosti naleznete `SetDate` v `SetDateTime` nebo členské funkce.

Následuje stručný popis každého konstruktoru:

- `COleDateTime(`**)** Vytvoří `COleDateTime` objekt inicializovaný na 0 (půlnoc, 30. prosince 1899).

- `COleDateTime(``dateSrc` **)** Vytvoří `COleDateTime` objekt z `COleDateTime` existujícího objektu.

- `COleDateTime(`*varSrc* **)** Vytvoří `COleDateTime` objekt. Pokusí se převést `VARIANT` strukturu nebo [colevariantobjekt](../../mfc/reference/colevariant-class.md) na `VT_DATE`hodnotu data a času ( ). Pokud je tento převod úspěšný, převedená hodnota `COleDateTime` se zkopíruje do nového objektu. Pokud tomu tak není, `COleDateTime` hodnota objektu je nastavena na 0 (půlnoc, 30 prosinec 1899) a jeho stav neplatný.

- `COleDateTime(``dtSrc` **)** Vytvoří `COleDateTime` objekt z `DATE` hodnoty.

- `COleDateTime(``timeSrc` **)** Vytvoří `COleDateTime` objekt z `time_t` hodnoty.

- `COleDateTime(`*systimeSrc* **)** Vytvoří `COleDateTime` objekt `SYSTEMTIME` z hodnoty.

- `COleDateTime(``filetimeSrc` **)** Vytvoří `COleDateTime` objekt z `FILETIME` hodnoty. . A `FILETIME` používá univerzální koordinovaný čas (UTC), takže pokud předáte místní čas ve struktuře, vaše výsledky budou nesprávné. Další informace naleznete v [tématu Časy souborů](/windows/win32/SysInfo/file-times) v sadě Windows SDK.

- `COleDateTime(``nYear`, `nMonth` `nDay`, `nHour` `nMin`, `nSec` , , `COleDateTime` **)** Vytvoří objekt ze zadaných číselných hodnot.

- `COleDateTime(``wDosDate`, `wDosTime` **)** Vytvoří `COleDateTime` objekt ze zadaných hodnot data a času ms-dos.

Další informace o `time_t` datovém typu naleznete [v](../../c-runtime-library/reference/time-time32-time64.md) časové funkci v *odkazu knihovny run-time*.

Další informace naleznete [v systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) a [filetime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) struktury v sadě Windows SDK.

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> Konstruktor pomocí `DBTIMESTAMP` parametru je k dispozici pouze v případě, že je součástí balení OLEDB.h.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

## <a name="coledatetimeformat"></a><a name="format"></a>COleDateTime::Formát

Vytvoří formátovanou reprezentaci hodnoty data a času.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Označuje jeden z následujících příznaků národního prostředí:

- LOCALE_NOUSEROVERRIDE Místo vlastních uživatelských nastavení použijte výchozí nastavení národního prostředí systému.

- VAR_TIMEVALUEONLY Ignorovat datovou část během analýzy.

- VAR_DATEVALUEONLY Ignorovat časovou část během analýzy.

*lcid*<br/>
Označuje ID národního prostředí, které má být pro převod používáno. Další informace o identifikátorech jazyků naleznete v [tématu Identifikátory jazyka](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Formátovací řetězec podobný řetězci `printf` formátování. Každý kód formátování, před nímž je `%`uvedeno znaménko `COleDateTime` procenta ( ), je nahrazen odpovídající komponentou. Ostatní znaky ve formátovacím řetězci jsou zkopírovány beze změny do vráceného řetězce. Další informace naleznete v tématu run-time funkce [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). Hodnota a význam kódů formátování `Format` pro jsou:

- `%H`Hodiny v aktuálním dni

- `%M`Minuty v aktuální hodině

- `%S`Sekundy v aktuální minutě

- `%%`Znak procenta

*nID formátu*<br/>
ID prostředku pro řetězec řízení formátu.

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje formátovanou hodnotu data a času.

### <a name="remarks"></a>Poznámky

Pokud je stav `COleDateTime` tohoto objektu null, vrácená hodnota je prázdný řetězec. Pokud je stav neplatný, je návratový řetězec určen ATL_IDS_DATETIME_INVALID prostředků řetězce.

Následuje stručný popis tří formulářů pro tuto funkci:

`Format`( *dwFlags*, *lcid*)<br/>
Tento formulář zformátuje hodnotu pomocí jazykových specifikací (ID národního prostředí) pro datum a čas. Pomocí výchozích parametrů bude tento formulář tisknout datum a čas, pokud není časová část 0 (půlnoc), v takovém případě se vytiskne pouze datum nebo část data je 0 (30. prosince 1899), v takovém případě se vytiskne pouze čas. Pokud je hodnota data a času 0 (30. prosince 1899, půlnoc), bude tento formulář s výchozími parametry vytištěn půlnoc.

`Format`( *lpszFormat*)<br/>
Tento formulář zformátuje hodnotu pomocí formátovacího řetězce, který obsahuje speciální formátovací kódy, před nimiž je znaménko procenta (%), jako v `printf`. Formátovací řetězec je předán jako parametr funkce. Další informace o kódech formátování naleznete v [tématu strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) v referenční příručce knihovny run-time.

`Format`( *nFormatID*)<br/>
Tento formulář zformátuje hodnotu pomocí formátovacího řetězce, který obsahuje speciální formátovací kódy, před nimiž je znaménko procenta (%), jako v `printf`. Formátovací řetězec je prostředek. ID tohoto řetězce prostředku je předán jako parametr. Další informace o kódech formátování naleznete v [tématu strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) v *referenční příručce knihovny run-time*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

## <a name="coledatetimegetasdbtimestamp"></a><a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP

Volání této metody získat čas `COleDateTime` v `DBTIMESTAMP` objektu jako datové struktury.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parametry

*Časové razítko*<br/>
Odkaz na strukturu [DBTimeStamp.](/dotnet/api/system.data.oledb.oledbtype)

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Ukládá výsledný čas v odkazované *timeStamp* struktury. Datová `DBTIMESTAMP` struktura inicializovaná `fraction` touto funkcí bude mít svůj člen nastaven na nulu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

## <a name="coledatetimegetassystemtime"></a><a name="getassystemtime"></a>COleDateTime::GetasSystemTime

Volání této metody získat čas `COleDateTime` v `SYSTEMTIME` objektu jako datové struktury.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parametry

*sysTime*<br/>
Odkaz na strukturu [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pro příjem převedené hodnoty `COleDateTime` data a času z objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšná. FALSE, pokud se převod `COleDateTime` nezdaří nebo pokud je objekt null nebo neplatný.

### <a name="remarks"></a>Poznámky

`GetAsSystemTime`ukládá výsledný čas v *odkazovaném objektu sysTime.* Datová `SYSTEMTIME` struktura inicializovaná `wMilliseconds` touto funkcí bude mít svůj člen nastaven na nulu.

Další informace o informacích o `COleDateTime` stavu uchovávaných v objektu naleznete v tématu [GetStatus](#getstatus).

## <a name="coledatetimegetasudate"></a><a name="getasudate"></a>COleDateTime::GetasuDATE

Volání této metody získat čas `COleDateTime` v `UDATE` objektu jako datové struktury.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parametry

*uDatum*<br/>
Odkaz na `UDATE` strukturu pro příjem převedené hodnoty data `COleDateTime` a času z objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je úspěšná. FALSE, pokud se převod `COleDateTime` nezdaří nebo pokud je objekt null nebo neplatný.

### <a name="remarks"></a>Poznámky

Struktura `UDATE` představuje "nezabalené" datum.

## <a name="coledatetimegetcurrenttime"></a><a name="getcurrenttime"></a>COleDateTime::GetCurrentTime

Volání této statické členské funkce vrátí aktuální hodnotu data a času.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

## <a name="coledatetimegetday"></a><a name="getday"></a>COleDateTime::GetDay

Získá den v měsíci reprezentované této hodnoty data a času.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v měsíci představovaný hodnotou `COleDateTime` tohoto `COleDateTime::error` objektu nebo pokud den nelze získat.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 1 a 31.

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

## <a name="coledatetimegetdayofweek"></a><a name="getdayofweek"></a>COleDateTime::GetDayOfWeek

Získá den v měsíci reprezentované této hodnoty data a času.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v týdnu představovaný hodnotou `COleDateTime` `COleDateTime::error` tohoto objektu nebo pokud nebylo možné získat den v týdnu.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 1 a 7, kde 1 = neděle, 2 = pondělí a tak dále.

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

## <a name="coledatetimegetdayofyear"></a><a name="getdayofyear"></a>COleDateTime::GetDayOfYear

Získá den v roce reprezentované této hodnoty data a času.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v roce představovaný hodnotou `COleDateTime` tohoto `COleDateTime::error` objektu nebo pokud nebylo možné získat den v roce.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 1 a 366, kde leden 1 = 1.

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

## <a name="coledatetimegethour"></a><a name="gethour"></a>COleDateTime::GetHour

Získá hodinu reprezentovanou touto hodnotou data a času.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Hodina reprezentovaná `COleDateTime` hodnotou tohoto objektu nebo `COleDateTime::error` pokud hodinu nebylo možné získat.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 0 a 23.

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

## <a name="coledatetimegetminute"></a><a name="getminute"></a>COleDateTime::GetMinute

Získá minutu reprezentován tuto hodnotu data a času.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Minuta reprezentovaná `COleDateTime` hodnotou tohoto objektu nebo `COleDateTime::error` pokud ji nebylo možné získat.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 0 a 59.

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Viz příklad pro [GetHour](#gethour).

## <a name="coledatetimegetmonth"></a><a name="getmonth"></a>COleDateTime::GetMonth

Získá měsíc reprezentované této hodnoty data a času.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Měsíc reprezentované `COleDateTime` hodnotou `COleDateTime::error` tohoto objektu nebo pokud měsíc nelze získat.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 1 a 12.

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Viz příklad pro [GetDay](#getday).

## <a name="coledatetimegetsecond"></a><a name="getsecond"></a>COleDateTime::GetSecond

Získá druhý reprezentované této hodnoty data a času.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Druhý reprezentované `COleDateTime` hodnotou `COleDateTime::error` tohoto objektu nebo pokud druhý nelze získat.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 0 a 59.

> [!NOTE]
> Třída `COleDateTime` nepodporuje přestupných sekund.

Další informace o implementaci `COleDateTime`pro , naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Viz příklad pro [GetHour](#gethour).

## <a name="coledatetimegetstatus"></a><a name="getstatus"></a>COleDateTime::GetStatus

Získá stav (platnost) daného `COleDateTime` objektu.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí stav této `COleDateTime` hodnoty. Pokud voláte `GetStatus` `COleDateTime` objekt vytvořený s výchozím, vrátí platný. Pokud zavoláte `GetStatus` `COleDateTime` objekt inicializovaný s konstruktorem nastaveným na hodnotu null, `GetStatus` vrátí hodnotu null.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je `DateTimeStatus` definována ve výčtu typu, `COleDateTime` který je definován v rámci třídy.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleDateTime::error`Označuje, že došlo k chybě při pokusu o získání části hodnoty data a času.

- `COleDateTime::valid`Označuje, `COleDateTime` že tento objekt je platný.

- `COleDateTime::invalid`Označuje, `COleDateTime` že tento objekt je neplatný; to znamená, že jeho hodnota může být nesprávná.

- `COleDateTime::null`Označuje, `COleDateTime` že tento objekt je null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Toto je "null" ve smyslu databáze "s žádnou hodnotu," na rozdíl od C++ NULL.)

Stav objektu `COleDateTime` je neplatný v následujících případech:

- Pokud je jeho hodnota `VARIANT` `COleVariant` nastavena z hodnoty nebo, kterou nelze převést na hodnotu data a času.

- Pokud je jeho hodnota `time_t` `SYSTEMTIME`nastavena `FILETIME` z , nebo hodnota, která nemohla být převedena na platnou hodnotu data a času.

- Pokud je jeho `SetDateTime` hodnota nastavena pomocí neplatných hodnot parametrů.

- Pokud tento objekt došlo k přetečení nebo podtečení během operace `+=` `-=`aritmetické přiřazení, a to nebo .

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na neplatný pomocí `SetStatus`.

Další informace o operacích, které mohou nastavit stav na neplatný, naleznete v následujících členských funkcích:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operátor +, -](#operator_add_-)

- [operátor +=, -=](#operator_add_eq_-_eq)

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

## <a name="coledatetimegetyear"></a><a name="getyear"></a>COleDateTime::GetYear

Získá rok reprezentované této hodnoty data a času.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Rok reprezentované `COleDateTime` hodnotou `COleDateTime::error` tohoto objektu nebo pokud rok nelze získat.

### <a name="remarks"></a>Poznámky

Platné vrácené hodnoty se pohybují mezi 100 a 9999, která zahrnuje století.

Informace o dalších členských funkcích, `COleDateTime` které dotazna hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

Viz příklad pro [GetDay](#getday).

## <a name="coledatetimem_dt"></a><a name="m_dt"></a>COleDateTime::m_dt

Základní `DATE` struktura pro `COleDateTime` tento objekt.

```
DATE m_dt;
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
> Změna hodnoty v `DATE` objektu, ke které má přístup ukazatel vrácený touto funkcí, změní hodnotu tohoto `COleDateTime` objektu. Nezmění stav tohoto `COleDateTime` objektu.

Další informace o implementaci `DATE` objektu naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimem_status"></a><a name="m_status"></a>COleDateTime::m_status

Obsahuje stav tohoto `COleDateTime` objektu.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Poznámky

Typ tohoto datového člena je výčtový typ `DateTimeStatus`, `COleDateTime` který je definován v rámci třídy. Další informace naleznete v tématu [COleDateTime::GetStatus](#getstatus).

> [!CAUTION]
> Tento datový člen je určen pro pokročilé programovací situace. Měli byste použít včleněné členské funkce [GetStatus](#getstatus) a [SetStatus](#setstatus). Viz `SetStatus` další upozornění týkající se explicitní nastavení tohoto datového člena.

## <a name="coledatetimeoperator-"></a><a name="operator_eq"></a>COleDateTime::operátor =

Zkopíruje `COleDateTime` hodnotu.

```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& uDate) throw();
```

### <a name="remarks"></a>Poznámky

Tyto přetížené operátory přiřazení zkopírují zdrojovou hodnotu data a času do tohoto `COleDateTime` objektu. Stručný popis každého z těchto operátorů přetíženého přiřazení následuje:

- **operátor =(** `dateSrc` **)** Hodnota a stav operandu jsou zkopírovány do tohoto `COleDateTime` objektu.

- **operátor =(** *varSrc* **)** Pokud je úspěšný převod hodnoty [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) (nebo [objektu COleVariant)](../../mfc/reference/colevariant-class.md) na datum a čas (VT_DATE), `COleDateTime` převedená hodnota je zkopírována do tohoto objektu a její stav je nastaven na platný. Pokud převod není úspěšný, hodnota tohoto objektu je nastavena na nulu (30. prosince 1899, půlnoc) a jeho stav neplatný.

- **operátor =(** `dtSrc` **)** Hodnota `DATE` je zkopírována do tohoto `COleDateTime` objektu a její stav je nastaven na platný.

- **operátor =(** `timeSrc` **)** Hodnota `time_t` `__time64_t` or je převedena a `COleDateTime` zkopírována do tohoto objektu. Pokud je převod úspěšný, je stav tohoto objektu nastaven na platný; pokud se nepodaří, je nastavena na neplatnou.

- **operátor =(** *systimeSrc* **)** Hodnota [SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) je převedena a `COleDateTime` zkopírována do tohoto objektu. Pokud je převod úspěšný, je stav tohoto objektu nastaven na platný; pokud se nepodaří, je nastavena na neplatnou.

- **operátor =(** `uDate` **)** Hodnota `UDATE` je převedena a zkopírována do tohoto `COleDateTime` objektu. Pokud je převod úspěšný, je stav tohoto objektu nastaven na platný; pokud se nepodaří, je nastavena na neplatnou. Struktura `UDATE` představuje "nezabalené" datum. Další informace naleznete v části funkce [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **operátor =(** `filetimeSrc` **)** Hodnota [FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime) je převedena a `COleDateTime` zkopírována do tohoto objektu. Pokud je převod úspěšný, je stav tohoto objektu nastaven na platný; v opačném případě je nastavena na neplatnou. `FILETIME`používá univerzální koordinovaný čas (UTC), takže pokud předáte čas UTC ve struktuře, výsledky budou převedeny z času UTC na místní čas a budou uloženy jako variantní čas. Toto chování je stejné jako v jazyce Visual C++ 6.0 a Visual C++.NET 2003 SP2. Další informace naleznete v [tématu Časy souborů](/windows/win32/SysInfo/file-times) v sadě Windows SDK.

Další informace naleznete v položce [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) v sadě Windows SDK.

Další informace o `time_t` datovém typu naleznete [v](../../c-runtime-library/reference/time-time32-time64.md) časové funkci v *odkazu knihovny run-time*.

Další informace naleznete [v systemtime](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) a [filetime](/windows/win32/api/minwinbase/ns-minwinbase-filetime) struktury v sadě Windows SDK.

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator---"></a><a name="operator_add_-"></a>COleDateTime::operátor +, -

Přidejte a `ColeDateTime` odečtěte hodnoty.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Poznámky

`COleDateTime`objekty představují absolutní časy. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) objekty představují relativní časy. První dva operátory umožňují přidat a `COleDateTimeSpan` odečíst `COleDateTime` hodnotu od hodnoty. Třetí operátor umožňuje odečíst `COleDateTime` jednu hodnotu `COleDateTimeSpan` od druhé výnos hodnoty.

Pokud některý z operandů je null, stav `COleDateTime` výsledné hodnoty je null.

Pokud výsledná `COleDateTime` hodnota spadá mimo hranice přijatelných hodnot, `COleDateTime` stav této hodnoty je neplatný.

Pokud je některý z operandů neplatný a druhý není null, je stav výsledné `COleDateTime` hodnoty neplatný.

A **+** **-** operátory budou `COleDateTime` uplatněny, pokud je objekt nastaven na hodnotu null. Viz [COleDateTime Relační operátory](#coledatetime_relational_operators) pro příklad.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

## <a name="coledatetimeoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTime::operátor +=, -=

Přidejte a `ColeDateTime` odečtěte `COleDateTime` hodnotu od tohoto objektu.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují přidat a `COleDateTimeSpan` odečíst hodnotu do a od tohoto `COleDateTime`. Pokud některý z operandů je null, stav `COleDateTime` výsledné hodnoty je null.

Pokud výsledná `COleDateTime` hodnota spadá mimo hranice přijatelných hodnot, `COleDateTime` je stav této hodnoty nastaven na neplatný.

Pokud je některý z operandů neplatný a druhý není `COleDateTime` null, je stav výsledné hodnoty neplatný.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

A **+=** **-=** operátory budou `COleDateTime` uplatněny, pokud je objekt nastaven na hodnotu null. Viz [COleDateTime Relační operátory](#coledatetime_relational_operators) pro příklad.

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimeoperator-date"></a><a name="operator_date"></a>COleDateTime::DATUM operátora

Převede `ColeDateTime` hodnotu `DATE`na .

```
operator DATE() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor `DATE` vrátí objekt, jehož `COleDateTime` hodnota je zkopírována z tohoto objektu. Další informace o implementaci `DATE` objektu naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

Operátor `DATE` bude uplatňovat, `COleDateTime` pokud je objekt nastaven na hodnotu null. Viz [COleDateTime Relační operátory](#coledatetime_relational_operators) pro příklad.

## <a name="coledatetimeparsedatetime"></a><a name="parsedatetime"></a>COleDateTime::PArseDateTime

Analyzuje řetězec pro čtení hodnoty data a času.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*lpszDatum*<br/>
Ukazatel na řetězec ukončený hodnotou null, který má být analyzován. Podrobnosti naleznete v tématu Poznámky.

*dwFlags*<br/>
Označuje příznaky pro nastavení národního prostředí a analýzu. Jeden nebo více z následujících příznaků:

- LOCALE_NOUSEROVERRIDE Místo vlastního uživatelského nastavení použijte výchozí nastavení národního prostředí systému.

- VAR_TIMEVALUEONLY Ignorovat datovou část během analýzy.

- VAR_DATEVALUEONLY Ignorovat časovou část během analýzy.

*lcid*<br/>
Označuje ID národního prostředí, které má být pro převod používáno.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl řetězec úspěšně převeden na hodnotu data a času, jinak HODNOTU NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud byl řetězec úspěšně převeden na hodnotu data a `COleDateTime` času, je hodnota tohoto objektu nastavena na tuto hodnotu a jeho stav je platný.

> [!NOTE]
> Roční hodnoty musí ležet mezi 100 a 9999, včetně.

Parametr *lpszDate* může mít různé formáty. Například následující řetězce obsahují přijatelné formáty data a času:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

ID národního prostředí bude mít také vliv na to, zda je formát řetězce přijatelný pro převod na hodnotu data a času.

V případě VAR_DATEVALUEONLY je hodnota času nastavena na čas 0 nebo půlnoc. V případě VAR_TIMEVALUEONLY je hodnota data nastavena na datum 0, tedy 30.

Pokud řetězec nelze převést na hodnotu data a času nebo pokud došlo k `COleDateTime` číselnému přetečení, je stav tohoto objektu neplatný.

Další informace o mezích a `COleDateTime` implementaci hodnot naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimesetdate"></a><a name="setdate"></a>COleDateTime::SetDate

Nastaví datum `COleDateTime` tohoto objektu.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parametry

*nRok*, *nMěsíc*, *nDen*<br/>
Označte součásti data, které `COleDateTime` mají být do tohoto objektu zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud `COleDateTime` byla hodnota tohoto objektu úspěšně nastavena; jinak 1. Tato vrácená hodnota `DateTimeStatus` je založena na výčtu typu. Další informace naleznete v členské funkci [SetStatus.](#setstatus)

### <a name="remarks"></a>Poznámky

Datum je nastaveno na zadané hodnoty. Čas je nastaven na čas 0, půlnoc.

Hodnoty parametrů naleznete v následující tabulce pro hranice:

|Parametr|Hranice|
|---------------|------------|
|*nRok*|100 - 9999|
|*nMěsíc*|1 - 12|
|*nDen*|0 - 31|

Pokud den v měsíci přeteče, je převeden na správný den následujícího měsíce a měsíc a / nebo rok se odpovídajícím způsobem zintátážli. Hodnota dne nula označuje poslední den předchozího měsíce. Chování je stejné `SystemTimeToVariantTime`jako .

Pokud hodnota data zadaná parametry není platná, je stav `COleDateTime::invalid`tohoto objektu nastaven na hodnotu . Měli byste použít [GetStatus](#getstatus) ke kontrole `DATE` platnosti hodnoty a neměl předpokládat, že hodnota [m_dt](#m_dt) zůstane nezměněna.

Zde je několik příkladů hodnot kalendářních dat:

|*nRok*|*nMěsíc*|*nDen*|Hodnota|
|-------------|--------------|------------|-----------|
|2000|2|29|29. února 2000|
|1776|7|4|4. července 1776 (4. července 1776)|
|1925|4|35|35. dubna 1925 (neplatné datum)|
|10000|1|1|1. ledna 10000 (neplatné datum)|

Chcete-li nastavit datum i čas, přečtěte si informace o datu i čase v tématu [COleDateTime::SetDateTime](#setdatetime).

Informace o členských funkcích, které `COleDateTime` dotazují na hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

## <a name="coledatetimesetdatetime"></a><a name="setdatetime"></a>COleDateTime::SetDateTime

Nastaví datum a `COleDateTime` čas tohoto objektu.

```
int SetDateTime(
    int nYear,
    int nMonth,
    int nDay,
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*nRok*, *nMěsíc*, *nDay*, *nHour*, *nMin*, *nSec*<br/>
Označte součásti data a času, `COleDateTime` které mají být do tohoto objektu zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud `COleDateTime` byla hodnota tohoto objektu úspěšně nastavena; jinak 1. Tato vrácená hodnota `DateTimeStatus` je založena na výčtu typu. Další informace naleznete v členské funkci [SetStatus.](#setstatus)

### <a name="remarks"></a>Poznámky

Hodnoty parametrů naleznete v následující tabulce pro hranice:

|Parametr|Hranice|
|---------------|------------|
|*nRok*|100 - 9999|
|*nMěsíc*|1 - 12|
|*nDen*|0 - 31|
|*nHodina*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Pokud den v měsíci přeteče, je převeden na správný den následujícího měsíce a měsíc a / nebo rok se odpovídajícím způsobem zintátážli. Hodnota dne nula označuje poslední den předchozího měsíce. Chování je stejné jako [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Pokud hodnota data nebo času určená parametry není platná, je stav tohoto objektu nastaven na neplatný a hodnota tohoto objektu se nezmění.

Zde je několik příkladů hodnot času:

|*nHodina*|*nMin*|*nSec*|Hodnota|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Neplatný|
|9|60|0|Neplatný|

Zde je několik příkladů hodnot kalendářních dat:

|*nRok*|*nMěsíc*|*nDen*|Hodnota|
|-------------|--------------|------------|-----------|
|1995|4|15|15. dubna 1995|
|1789|7|14|17. července 1789 (17. července 1789)|
|1925|2|30|Neplatný|
|10000|1|1|Neplatný|

Chcete-li nastavit pouze datum, přečtěte si informace [o cOleDateTime::SetDate](#setdate). Chcete-li nastavit pouze čas, viz [COleDateTime::SetTime](#settime).

Informace o členských funkcích, které `COleDateTime` dotazují na hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

Viz příklad pro [GetStatus](#getstatus).

## <a name="coledatetimesetstatus"></a><a name="setstatus"></a>COleDateTime::SetStatus

Nastaví stav `COleDateTime` tohoto objektu.

```cpp
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Nová hodnota stavu `COleDateTime` pro tento objekt.

### <a name="remarks"></a>Poznámky

Hodnota *parametru stavu* je `DateTimeStatus` definována ve výčtovém `COleDateTime` typu, který je definován v rámci třídy. Viz [COleDateTime::GetStatus](#getstatus) podrobnosti.

> [!CAUTION]
> Tato funkce je určena pro pokročilé programovací situace. Tato funkce nemění data v tomto objektu. Nejčastěji se používá k nastavení stavu **na hodnotu null** nebo **neplatné**. Operátor přiřazení ([operátor =](#operator_eq)) a [SetDateTime](#setdatetime) nastavují stav objektu na základě zdrojové hodnoty.

### <a name="example"></a>Příklad

Viz příklad pro [GetStatus](#getstatus).

## <a name="coledatetimesettime"></a><a name="settime"></a>COleDateTime::SetTime

Nastaví čas `COleDateTime` tohoto objektu.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*nHodina*, *nMin*, *nSec*<br/>
Označte časové součásti, které `COleDateTime` mají být do tohoto objektu zkopírovány.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud `COleDateTime` byla hodnota tohoto objektu úspěšně nastavena; jinak 1. Tato vrácená hodnota `DateTimeStatus` je založena na výčtu typu. Další informace naleznete v členské funkci [SetStatus.](#setstatus)

### <a name="remarks"></a>Poznámky

Čas je nastaven na zadané hodnoty. Datum je stanoveno na datum 0, což znamená 30.

Hodnoty parametrů naleznete v následující tabulce pro hranice:

|Parametr|Hranice|
|---------------|------------|
|*nHodina*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Pokud hodnota času zadaná parametry není platná, je stav tohoto objektu nastaven na neplatný a hodnota tohoto objektu se nezmění.

Zde je několik příkladů hodnot času:

|*nHodina*|*nMin*|*nSec*|Hodnota|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Neplatný|
|9|60|0|Neplatný|

Chcete-li nastavit datum i čas, přečtěte si informace o datu i čase v tématu [COleDateTime::SetDateTime](#setdatetime).

Informace o členských funkcích, které `COleDateTime` dotazují na hodnotu tohoto objektu, naleznete v následujících členských funkcích:

- [GetDay](#getday)

- [GetMonth](#getmonth)

- [GetYear](#getyear)

- [Hodina get](#gethour)

- [GetMinute](#getminute)

- [Získatsekundu](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o mezích `COleDateTime` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

Viz příklad pro [SetDate](#setdate).

## <a name="see-also"></a>Viz také

[COleVariant třída](../../mfc/reference/colevariant-class.md)<br/>
[CTime – třída](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
