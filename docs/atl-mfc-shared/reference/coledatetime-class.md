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
ms.openlocfilehash: 46b5f15a2f6048745a12b8c3a8c8a63404f71aa2
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565932"
---
# <a name="coledatetime-class"></a>COleDateTime – třída

Zapouzdřuje `DATE` datový typ, který se používá v automatizace OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDateTime
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|Vytvoří `COleDateTime` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDateTime::Format](#format)|Generuje formátovaný řetězec představující `COleDateTime` objektu.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Volejte tuto metodu za účelem získání čas v `COleDateTime` objektu jako `DBTIMESTAMP` datové struktury.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Volat tuto metodu za účelem získání čas v `COleDateTime` objektu jako [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) datové struktury.|
|[COleDateTime::GetAsUDATE](#getasudate)|Volejte tuto metodu za účelem získání čas v `COleDateTime` jako `UDATE` datové struktury.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Vytvoří `COleDateTime` objekt, který představuje aktuální čas (statické členské funkce).|
|[COleDateTime::GetDay](#getday)|Vrátí den `COleDateTime` objekt představuje (1-31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu, to `COleDateTime` objekt představuje (neděli = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Vrátí den v roce to `COleDateTime` objekt představuje (1. ledna = 1).|
|[COleDateTime::GetHour](#gethour)|Vrátí hodinu `COleDateTime` objekt představuje (0 - 23).|
|[COleDateTime::GetMinute](#getminute)|Vrátí minuty `COleDateTime` objekt představuje (0 – 59).|
|[COleDateTime::GetMonth](#getmonth)|Vrátí měsíc `COleDateTime` objekt představuje (1-12).|
|[COleDateTime::GetSecond](#getsecond)|Vrátí sekundy `COleDateTime` objekt představuje (0 – 59).|
|[COleDateTime::GetStatus](#getstatus)|Získá stav (platnosti) to `COleDateTime` objektu.|
|[COleDateTime::GetYear](#getyear)|Vrátí rok `COleDateTime` objekt představuje.|
|[COleDateTime::ParseDateTime](#parsedatetime)|Načte hodnotu data a času z řetězce a nastaví hodnotu `COleDateTime`.|
|[COleDateTime::SetDate](#setdate)|Nastaví hodnotu tohoto `COleDateTime` objekt se zadanou hodnotou, pouze datum.|
|[COleDateTime::SetDateTime](#setdatetime)|Nastaví hodnotu tohoto `COleDateTime` objektu na hodnotu zadaného data a času.|
|[COleDateTime::SetStatus](#setstatus)|Nastaví stav (platnosti) to `COleDateTime` objektu.|
|[COleDateTime::SetTime](#settime)|Nastaví hodnotu tohoto `COleDateTime` objekt se zadanou hodnotou časové.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[COleDateTime::operator == COleDateTime::operator < atd.](#coledatetime_relational_operators)|Porovnat dva `COleDateTime` hodnoty.|
|[COleDateTime::operator + COleDateTime::operator-](#operator_add_-)|Sčítání a odečítání `COleDateTime` hodnoty.|
|[COleDateTime::operator +=, COleDateTime::operator-=](#operator_add_eq_-_eq)|Sčítání a odečítání `COleDateTime` hodnotu z této `COleDateTime` objektu.|
|[COleDateTime::operator =](#operator_eq)|Zkopíruje `COleDateTime` hodnotu.|
|[COleDateTime::operator DATE, Date COleDateTime::operator *](#operator_date)|Převede `COleDateTime` hodnoty do `DATE` nebo `DATE*`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Obsahuje základní `DATE` to `COleDateTime` objektu.|
|[COleDateTime::m_status](#m_status)|Obsahuje stav tohoto `COleDateTime` objektu.|

## <a name="remarks"></a>Poznámky

`COleDateTime` nemá základní třídu.

Je jedním z možných typů [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) datovým typem automatizace OLE. A `COleDateTime` hodnota představuje absolutní hodnotu data a času.

`DATE` Typ je implementován jako hodnotu s plovoucí desetinnou čárkou. Dny jsou měřená od 30. prosince 1899 půlnoci. V následující tabulce jsou uvedeny některé kalendářních dat a jejich přidružené hodnoty:

|Datum|Hodnota|
|----------|-----------|
|29. prosince 1899 půlnoci|-1.0|
|29. prosince 1899, dvanáctihodinového 6|-1.25|
|30. prosince 1899 půlnoci|0.0|
|31. prosince 1899 půlnoci|1.0|
|1. ledna 1900, 6: 00|2.25|

> [!CAUTION]
> V tabulce výše, i když v hodnotách dní záporný before midnight 30. prosince 1899, denní dobu hodnoty to nejde. Příklad 6:00:00 je vždy označena desetinná hodnota 0,25 bez ohledu na to, zda je celé číslo představující den (po 30. prosince 1899) kladná nebo záporná (před 30. prosince 1899). To znamená, že by jednoduché porovnání s plovoucí desetinnou čárkou bodu chybně řazení `COleDateTime` představující 6:00:00 na 12/29 nebo 1899 jako **později** než jedna představující 7:00 stejného dne.

`COleDateTime` Třídy kalendářní data od 1. leden 100, do 31. prosince 9999. `COleDateTime` Třída používá gregoriánský kalendář; nepodporuje juliánský data. `COleDateTime` ignoruje letního času. (Viz [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).)

> [!NOTE]
> Můžete použít `%y` formátu k načtení dvoumístný rok pouze pro data od 1900. Pokud používáte `%y` formát na datum před 1900, kód generuje chybu vyhodnocení.

Tento typ se používá také aby reprezentoval pouze datum nebo časové hodnoty. Podle konvence data 0 (30. prosince 1899) se používá pro časové hodnoty a čase 00:00 (půlnoc) se používá pro hodnoty určené pouze pro datum.

Pokud jste vytvořili `COleDateTime` s použitím datum méně než 100, datum je přijatý, ale následné volání `GetYear`, `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, a `GetSecond` selže a vrátí hodnotu -1. Dříve můžete použít data dvěma číslicemi, ale data musí být 100 nebo větší v MFC 4.2 nebo novější.

Aby nedocházelo k problémům, zadejte čtyřmístný datum. Příklad:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Pro základní aritmetické operace `COleDateTime` hodnoty použijte třídě doprovodných prvků [coledatetimespan –](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan` definování hodnoty časového intervalu. Vztah mezi tyto třídy je podobná mezi [CTime](../../atl-mfc-shared/reference/ctime-class.md) a [ctimespan –](../../atl-mfc-shared/reference/ctimespan-class.md).

Další informace o `COleDateTime` a `COleDateTimeSpan` třídy, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>  COleDateTime – relační operátory

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
`COleDateTime` Objekt k porovnání.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  ATLASSERT se vrátí jednu z dvou operandů je neplatný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Příklad

Operátory **>=**, **\< =**, **>**, a **<**, bude-li uplatnit `COleDateTime` objekt je nastaven na hodnotu null.

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>  COleDateTime::COleDateTime

Vytvoří `COleDateTime` objektu.

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
Existující `COleDateTime` objektu, které se mají zkopírovat do nové `COleDateTime` objektu.

*varSrc*<br/>
Existující `VARIANT` datovou strukturu (pravděpodobně `COleVariant` objekt) převést na hodnotu data a času (VT_DATE) a zkopírovány do nového `COleDateTime` objektu.

*dtSrc*<br/>
Datum/čas (`DATE`) hodnota, která má být zkopírován do nové `COleDateTime` objektu.

*timeSrc*<br/>
A `time_t` nebo `__time64_t` hodnota, která má být převedena na hodnotu data a času a zkopírovány do nového `COleDateTime` objektu.

*systimeSrc*<br/>
A `SYSTEMTIME` struktura bude převeden na hodnotu data a času a zkopírovány do nového `COleDateTime` objektu.

*filetimeSrc*<br/>
A `FILETIME` struktura bude převeden na hodnotu data a času a zkopírovány do nového `COleDateTime` objektu. A `FILETIME` používá koordinovaný světový čas (UTC), takže pokud předáte místní čas ve struktuře, vaše výsledky budou nesprávné. Zobrazit [časy](/windows/desktop/SysInfo/file-times) v sadě Windows SDK pro další informace.

*nYear*, *nMonth*, *Nden*, *Nhodina*, *Nminimum*, *nSec*<br/>
Označení hodnoty data a času, které se mají zkopírovat do nové `COleDateTime` objektu.

*wDosDate*, *wDosTime*<br/>
Hodnoty data a času zástupného kódu MS-DOS převést na hodnotu data a času a zkopírovány do nového `COleDateTime` objektu.

*timeStamp*<br/>
Odkaz na [DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktury obsahující aktuální místní čas.

### <a name="remarks"></a>Poznámky

Tyto konstruktory vytvořit nový `COleDateTime` objekty inicializovány na zadanou hodnotu. V následující tabulce jsou uvedeny platné rozsahy pro každou komponentu data a času:

|Komponenta data a času|Platný rozsah|
|--------------------------|-----------------|
|rok|100 - 9999|
|měsíc|0 - 12|
|den|0 - 31|
|Hodina|0 - 23|
|Minuta|0 - 59|
|Sekundy|0 - 59|

Všimněte si, že skutečné horní mez pro komponentu dne se liší podle součásti měsíci a roce. Podrobnosti najdete v tématu `SetDate` nebo `SetDateTime` členské funkce.

Tady je stručný popis jednotlivých konstruktor:

- `COleDateTime(` **)** Sestaví `COleDateTime` objekt je inicializován na hodnotu 0 (půlnoc, 1899 30. prosince).

- `COleDateTime(` `dateSrc` **)** Sestaví `COleDateTime` objekt z existující `COleDateTime` objektu.

- `COleDateTime(` *varSrc* **)** sestaví `COleDateTime` objektu. Se pokusí převést `VARIANT` struktury nebo [COleVariant](../../mfc/reference/colevariant-class.md) objektu na datum/čas ( `VT_DATE`) hodnotu. Pokud tento převod je úspěšný, převedená hodnota zkopírován do nové `COleDateTime` objektu. Pokud ne, je hodnota `COleDateTime` objektu je nastavena na 0 (půlnoc, 1899 30. prosince) a její stav na neplatný.

- `COleDateTime(` `dtSrc` **)** Sestaví `COleDateTime` objektu z `DATE` hodnotu.

- `COleDateTime(` `timeSrc` **)** Sestaví `COleDateTime` objektu z `time_t` hodnotu.

- `COleDateTime(` *systimeSrc* **)** sestaví `COleDateTime` objektu z `SYSTEMTIME` hodnotu.

- `COleDateTime(` `filetimeSrc` **)** Sestaví `COleDateTime` objektu z `FILETIME` hodnotu. . A `FILETIME` používá koordinovaný světový čas (UTC), takže pokud předáte místní čas ve struktuře, vaše výsledky budou nesprávné. Další informace najdete v tématu [časy](/windows/desktop/SysInfo/file-times) v sadě Windows SDK.

- `COleDateTime(` `nYear``nMonth`, `nDay`, `nHour`, `nMin`, `nSec` **)** Sestaví `COleDateTime` objekt ze zadaného číselné hodnoty.

- `COleDateTime(` `wDosDate``wDosTime` **)** Sestaví `COleDateTime` objekt ze zadané hodnoty data a času zástupného kódu MS-DOS.

Další informace o `time_t` datový typ, najdete v článku [čas](../../c-runtime-library/reference/time-time32-time64.md) fungovat v *Run-Time Library Reference*.

Další informace najdete v tématu [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) a [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury v sadě Windows SDK.

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

> [!NOTE]
> Pomocí konstruktoru `DBTIMESTAMP` parametr je k dispozici, pouze když OLEDB.h je součástí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>  COleDateTime::Format

Vytvoří formátovaný reprezentace hodnoty data a času.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Určuje jeden z následujících příznaků národní prostředí:

- LOCALE_NOUSEROVERRIDE použít výchozí systému v nastavení národního prostředí namísto vlastní uživatelská nastavení.

- Ignorovat VAR_TIMEVALUEONLY části datum během analýzy.

- VAR_DATEVALUEONLY ignorovat Časová část během analýzy.

*lcid*<br/>
Určuje ID národního prostředí pro převod. Další informace o identifikátorech jazyka najdete v tématu [identifikátory jazyka](/windows/desktop/Intl/language-identifiers).

*lpszFormat*<br/>
Formátování řetězců podobně jako `printf` formátovací řetězec. Každý formátování kódu, předchází procento ( `%`) podepsat, se nahradí odpovídající `COleDateTime` komponenty. Jiné znaky v řetězci formátování se zkopírují do vráceném řetězci beze změny. Další informace najdete v tématu funkci run-time [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). Hodnota a význam kódů formátování pro `Format` jsou:

- `%H` Hodin aktuálního dne

- `%M` Minut do aktuální hodiny

- `%S` Sekundy do aktuální minuty

- `%%` Znak procent

*nFormatID*<br/>
ID prostředku pro řetězec řízení formátu.

### <a name="return-value"></a>Návratová hodnota

A `CString` , který obsahuje hodnotu formátovaná data a času.

### <a name="remarks"></a>Poznámky

Pokud se stav tohoto `COleDateTime` objekt má hodnotu null, vrácená hodnota je prázdný řetězec. Pokud je neplatný stav, vrácený řetězec je určená ATL_IDS_DATETIME_INVALID prostředek řetězce.

Následuje stručný popis tři formuláře pro tuto funkci:

`Format`( *dwFlags*, *lcid*)<br/>
Tento formulář naformátuje hodnotu s použitím specifikace jazyka (ID národních prostředí) pro data a času. Použití výchozích parametrů, tento formulář vytiskne se datum a čas, pokud jako čas se 0 (půlnoc), v takovém případě vytiskne pouze datum nebo datum část je 0 (30 1899 dne), v takovém případě vytiskne jenom čas. Pokud hodnota data a času je 0 (30. prosince 1899, půlnoc), vytiskne tento formulář s výchozími parametry půlnoc.

`Format`( *lpszFormat*)<br/>
Tento formulář naformátuje hodnotu pomocí formátovacího řetězce, který obsahuje speciální formátovacích kódech, které jsou uvozená znakem procent (%), stejně jako v `printf`. Formátovací řetězec je předat jako parametr funkce. Další informace o formátovacích kódech viz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) v referenční dokumentace knihoven Run-Time.

`Format`( *nFormatID*)<br/>
Tento formulář naformátuje hodnotu pomocí formátovacího řetězce, který obsahuje speciální formátovacích kódech, které jsou uvozená znakem procent (%), stejně jako v `printf`. Formátovací řetězec je prostředek. ID prostředku tento řetězec je předán jako parametr. Další informace o formátovacích kódech viz [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) v *Run-Time Library Reference*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP

Volejte tuto metodu za účelem získání čas v `COleDateTime` objektu jako `DBTIMESTAMP` datové struktury.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parametry

*timeStamp*<br/>
Odkaz na [DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktury.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Uloží výsledný čas v odkazované *časové razítko* struktury. `DBTIMESTAMP` Datová struktura inicializovat touto funkcí bude mít jeho `fraction` člen nastaven na hodnotu nula.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime

Volejte tuto metodu za účelem získání čas v `COleDateTime` objektu jako `SYSTEMTIME` datové struktury.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parametry

*sysTime*<br/>
Odkaz na [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) strukturu pro příjem hodnota převedená data a času z `COleDateTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; FALSE, pokud převod selže nebo pokud `COleDateTime` objekt je NULL nebo je neplatný.

### <a name="remarks"></a>Poznámky

`GetAsSystemTime` uloží výsledný čas v odkazované *systime –* objektu. `SYSTEMTIME` Datová struktura inicializovat touto funkcí bude mít jeho `wMilliseconds` člen nastaven na hodnotu nula.

Pro další informace o informace o stavu uložené v `COleDateTime` objektu, najdete v článku [GetStatus](#getstatus).

##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE

Volejte tuto metodu za účelem získání čas v `COleDateTime` objektu jako `UDATE` datové struktury.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parametry

*uDate*<br/>
Odkaz na `UDATE` strukturu pro příjem hodnota převedená data a času z `COleDateTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE v případě úspěchu; FALSE, pokud převod selže nebo pokud `COleDateTime` objekt je NULL nebo je neplatný.

### <a name="remarks"></a>Poznámky

A `UDATE` struktura představuje "rozbalené" datum.

##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime

Voláním této funkce statický člen vrátit hodnotu aktuálního data a času.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>  COleDateTime::GetDay

Načte den v měsíci, reprezentovaný této hodnotě data/času.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v měsíci, reprezentovaný hodnotou tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud nebylo možné získat dne.

### <a name="remarks"></a>Poznámky

Platný návratové hodnoty spadají do rozsahu od 1 do 31.

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek

Načte den v měsíci, reprezentovaný této hodnotě data/času.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v týdnu reprezentovaný hodnotou tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud nebylo možné získat den v týdnu.

### <a name="remarks"></a>Poznámky

Platný vrátit hodnoty v rozsahu od 1 do 7, kde 1 = neděle, 2 = pondělí a tak dále.

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear

Načte den v roce reprezentována této hodnotě data/času.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v roce reprezentovaný hodnotou tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud nebylo možné získat den v roce.

### <a name="remarks"></a>Poznámky

Platný vrácení hodnoty v rozsahu od 1 do 366, kde 1. ledna = 1.

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>  COleDateTime::GetHour

Získá hodinu představovanou této hodnotě data/času.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Hodinu představovanou hodnota tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud nebylo možné získat hodiny.

### <a name="remarks"></a>Poznámky

Platný návratový hodnoty spadají do rozsahu od 0 do 23.

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>  COleDateTime::GetMinute

Získá minutu reprezentována této hodnotě data/času.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Minuta reprezentovaný hodnotou tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud nebylo možné získat minuty.

### <a name="remarks"></a>Poznámky

Platný návratový hodnoty spadají do rozsahu od 0 do 59.

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetHour](#gethour).

##  <a name="getmonth"></a>  COleDateTime::GetMonth

Získá měsíc reprezentována této hodnotě data/času.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Měsíc reprezentovaný hodnotou tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud nebylo možné získat měsíce.

### <a name="remarks"></a>Poznámky

Platný návratové hodnoty spadají do rozsahu od 1 do 12.

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetDay](#getday).

##  <a name="getsecond"></a>  COleDateTime::GetSecond

Získá druhý reprezentována této hodnotě data/času.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Druhá reprezentovaný hodnotou tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud druhá nebylo možné získat.

### <a name="remarks"></a>Poznámky

Platný návratový hodnoty spadají do rozsahu od 0 do 59.

> [!NOTE]
>  `COleDateTime` Třída nepodporuje přestupné sekundy.

Další informace o implementaci pro `COleDateTime`, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetHour](#gethour).

##  <a name="getstatus"></a>  COleDateTime::GetStatus

Získá stav (platnosti) daném `COleDateTime` objektu.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí stav této `COleDateTime` hodnotu. Při volání `GetStatus` na `COleDateTime` objekt vytvořen s výchozím, vrátí platný. Při volání `GetStatus` na `COleDateTime` objekt je inicializován pomocí konstruktoru nastavený na hodnotu null, `GetStatus` vrátí hodnotu null.

### <a name="remarks"></a>Poznámky

Návratová hodnota je definována `DateTimeStatus` Výčtový typ, který je definován v rámci `COleDateTime` třídy.

```
enum DateTimeStatus
{
   error = -1,
   valid = 0,
   invalid = 1,    // Invalid date (out of range, etc.)
   null = 2,       // Literally has no value
};
```

Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:

- `COleDateTime::error` Označuje, že došlo k chybě při pokusu získat část z hodnoty data/času.

- `COleDateTime::valid` Označuje, že tento `COleDateTime` objektu je neplatný.

- `COleDateTime::invalid` Označuje, že tento `COleDateTime` objekt je neplatný; to znamená, jeho hodnota může být nesprávný.

- `COleDateTime::null` Označuje, že tento `COleDateTime` objekt má hodnotu null, to znamená, že byla zadána žádná hodnota pro tento objekt. (To je v tom smyslu databáze "mít žádnou hodnotu" na rozdíl od C++ NULL "null".)

Stav `COleDateTime` objekt není platný v následujících případech:

- Pokud je jeho hodnota v rozsahu od `VARIANT` nebo `COleVariant` hodnotu, která nelze převést na hodnotu data/času.

- Pokud je jeho hodnota v rozsahu od `time_t`, `SYSTEMTIME`, nebo `FILETIME` hodnotu, která nelze převést na hodnotu platné datum/čas.

- Pokud je jeho hodnota nastavená `SetDateTime` pomocí neplatné hodnoty parametrů.

- Pokud tento objekt došlo přetečení nebo podtečení během přiřazení aritmetické operace, jmenovitě `+=` nebo `-=`.

- Pokud na tento objekt byl přiřazen neplatnou hodnotu.

- Pokud se stav tohoto objektu explicitně nastavit na neplatné použití `SetStatus`.

Další informace o operacích, které může nastavit stav na neplatné, viz následující členské funkce:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operátor +, -](#operator_add_-)

- [Operator +=-=](#operator_add_eq_-_eq)

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>  COleDateTime::GetYear

Získá rok reprezentována této hodnotě data/času.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Rok, reprezentovaný hodnotou tohoto `COleDateTime` objektu nebo `COleDateTime::error` Pokud nebylo možné získat rok.

### <a name="remarks"></a>Poznámky

Platný návratové hodnoty v rozmezí 100 až 9999, zahrnující století.

Informace o dalších členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetDay](#getday).

##  <a name="m_dt"></a>  COleDateTime::m_dt

Základní `DATE` strukturu pro to `COleDateTime` objektu.

```
DATE m_dt;
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Změna hodnoty v `DATE` objekt vrácený touto funkcí ukazatel se změní hodnota tohoto `COleDateTime` objektu. Nezmění stav této `COleDateTime` objektu.

Další informace o provádění `DATE` objektu, přečtěte si článek [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="m_status"></a>  COleDateTime::m_status

Obsahuje stav tohoto `COleDateTime` objektu.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Poznámky

Typ tomuto datovému členu je výčtového typu `DateTimeStatus`, který je definován v rámci `COleDateTime` třídy. Další informace najdete v tématu [COleDateTime::GetStatus](#getstatus).

> [!CAUTION]
>  Pro pokročilé situacích programování je tomuto datovému členu. Používejte vložené členské funkce [GetStatus](#getstatus) a [SetStatus](#setstatus). Zobrazit `SetStatus` pro další upozornění týkající se explicitním nastavením tomuto datovému členu.

##  <a name="operator_eq"></a>  COleDateTime::operator =

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

Zkopírování těchto přetížených operátorech přiřazení zdrojová hodnota data a času do tohoto `COleDateTime` objektu. Stručný popis jednotlivých tyto přetížené následující operátory přiřazení:

- **Operator = (** `dateSrc` **)** hodnotu a stav operandu jsou zkopírovány do tohoto `COleDateTime` objektu.

- **operátor = (** *varSrc* **)** Pokud převodu [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) hodnotu (nebo [COleVariant](../../mfc/reference/colevariant-class.md) objekt) pro datum/čas (typ VT_ DATUM) proběhne úspěšně, převedená hodnota se zkopíruje do tohoto `COleDateTime` objektu a jeho stav je nastaven na platný. Pokud převod není úspěšné, je hodnota tohoto objektu nastavena na nula (30. prosince 1899, půlnoc) a její stav na neplatný.

- **Operator = (** `dtSrc` **)** `DATE` zkopírování hodnoty do tohoto `COleDateTime` objektu a jeho stav je nastaven na platný.

- **Operator = (** `timeSrc` **)** `time_t` nebo `__time64_t` hodnota převedena a zkopírovány do tohoto `COleDateTime` objektu. Pokud převod není úspěšné, stav tohoto objektu nastavena platná. Pokud úspěšné, je nastaven na neplatný.

- **Operator = (** *systimeSrc* **)** [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) hodnota převedena a zkopírovány do tohoto `COleDateTime` objektu. Pokud převod není úspěšné, stav tohoto objektu nastavena platná. Pokud úspěšné, je nastaven na neplatný.

- **Operator = (** `uDate` **)** `UDATE` hodnota převedena a zkopírovány do tohoto `COleDateTime` objektu. Pokud převod není úspěšné, stav tohoto objektu nastavena platná. Pokud úspěšné, je nastaven na neplatný. A `UDATE` struktura představuje "rozbalené" datum. Další informace najdete v tématu funkce [VarDateFromUdate](/windows/desktop/api/oleauto/nf-oleauto-vardatefromudate).

- **Operator = (** `filetimeSrc` **)** [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) hodnota převedena a zkopírovány do tohoto `COleDateTime` objektu. Pokud převod není úspěšné, stav tohoto objektu nastavena platná. v opačném případě je nastavena na neplatný. `FILETIME` Koordinovaný světový čas (UTC), používá, pokud předáte čas UTC ve struktuře, vaše výsledky se převedou na místní čas od času UTC, takže se budou ukládat jako varianty čas. Toto chování je stejné jako v aplikaci Visual C++ 6.0 a Visual C++ .NET 2003 SP2. Další informace najdete v tématu [časy](/windows/desktop/SysInfo/file-times) v sadě Windows SDK.

Další informace najdete v tématu [VARIANT](/windows/desktop/api/oaidl/ns-oaidl-tagvariant) položku v sadě Windows SDK.

Další informace o `time_t` datový typ, najdete v článku [čas](../../c-runtime-library/reference/time-time32-time64.md) fungovat v *Run-Time Library Reference*.

Další informace najdete v tématu [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime) a [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury v sadě Windows SDK.

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_add_-"></a>  COleDateTime::operator +, -

Sčítání a odečítání `ColeDateTime` hodnoty.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Poznámky

`COleDateTime` objekty představují časy absolutní. [Coledatetimespan –](../../atl-mfc-shared/reference/coledatetimespan-class.md) objekty představují časy relativní. První dva operátory umožňují operátorů sčítání a odečítání `COleDateTimeSpan` hodnotu `COleDateTime` hodnotu. Operátor třetí umožňuje odečte jeden `COleDateTime` hodnotu z druhého pozastavit `COleDateTimeSpan` hodnotu.

Pokud platí některá z operandů s hodnotou null, výsledný stav `COleDateTime` hodnotu null.

Pokud výsledná `COleDateTime` hodnota spadá mimo rozsah přijatelných hodnot, stav, který `COleDateTime` hodnota není platná.

Pokud jeden z operandů je neplatný a druhá nemá hodnotu null, výsledný stav `COleDateTime` hodnota není platná.

**+** a **-** operátory se uplatnit, pokud `COleDateTime` objekt je nastaven na hodnotu null. Zobrazit [COleDateTime – relační operátory](#coledatetime_relational_operators) příklad.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTime::operator +=-=

Sčítání a odečítání `ColeDateTime` hodnotu z této `COleDateTime` objektu.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují operátorů sčítání a odečítání `COleDateTimeSpan` hodnotu do a z tohoto `COleDateTime`. Pokud platí některá z operandů s hodnotou null, výsledný stav `COleDateTime` hodnotu null.

Pokud výsledná `COleDateTime` hodnota spadá mimo rozsah přijatelných hodnot, stav této `COleDateTime` je hodnota nastavena na neplatný.

Pokud jeden z operandů je neplatný a dalších nemá hodnotu null, výsledný stav `COleDateTime` hodnota není platná.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

**+=** a **-=** operátory se uplatnit, pokud `COleDateTime` objekt je nastaven na hodnotu null. Zobrazit [COleDateTime – relační operátory](#coledatetime_relational_operators) příklad.

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_date"></a>  COleDateTime::operator datum

Převede `ColeDateTime` hodnoty do `DATE`.

```
operator DATE() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí hodnotu `DATE` objekt, jehož hodnota je zkopírován z tohoto `COleDateTime` objektu. Další informace o provádění `DATE` objektu, přečtěte si článek [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

`DATE` Operátor se uplatnit, pokud `COleDateTime` objekt je nastaven na hodnotu null. Zobrazit [COleDateTime – relační operátory](#coledatetime_relational_operators) příklad.

##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime

Analyzuje řetězec k načtení hodnoty data a času.

```
bool ParseDateTime(
    LPCTSTR lpszDate,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT) throw();
```

### <a name="parameters"></a>Parametry

*lpszDate*<br/>
Ukazatel na řetězec zakončený hodnotou null, který má být analyzován. Podrobnosti najdete v tématu poznámky.

*dwFlags*<br/>
Určuje příznaky pro nastavení národního prostředí a analýzu. Jeden nebo více z následujících příznaků:

- LOCALE_NOUSEROVERRIDE použijte výchozí nastavení národního prostředí systému, raději vlastní uživatelská nastavení.

- Ignorovat VAR_TIMEVALUEONLY části datum během analýzy.

- VAR_DATEVALUEONLY ignorovat Časová část během analýzy.

*lcid*<br/>
Určuje ID národního prostředí pro převod.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byl úspěšně daný řetězec převést na hodnotu data a času, jinak hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud řetězec byl úspěšně převeden na datum/čas hodnotu, hodnota tohoto `COleDateTime` objekt je nastaven na tuto hodnotu a její stav na platný.

> [!NOTE]
>  Hodnoty rok musí ležet v rozsahu od 100 do 9999 (včetně).

*LpszDate* parametr můžete využít širokou škálu formátů. Formáty data a času přijatelné obsahovat například následující řetězce:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

ID národního prostředí ovlivní také, zda řetězec formát je přijatelné pro převod na hodnotu data/času.

V případě VAR_DATEVALUEONLY časová hodnota nastavena na 0 nebo půlnoc. V případě VAR_TIMEVALUEONLY hodnoty date nastavena na data 0, což znamená 30 1899 dne.

Pokud řetězec nelze převést na hodnotu data a času, nebo pokud došlo k číselné přetečení, stav této `COleDateTime` objekt je neplatný.

Další informace o omezení a implementaci pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="setdate"></a>  COleDateTime::SetDate

Nastaví datum tohoto `COleDateTime` objektu.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parametry

*nYear*, *nMonth*, *Nden*<br/>
Označení datum komponent, které mají být zkopírovány do tohoto `COleDateTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Nula v případě hodnoty této třídy `COleDateTime` objekt byl nastaven úspěšně; v opačném případě 1. Podle tohoto návratová hodnota `DateTimeStatus` výčtového typu. Další informace najdete v tématu [SetStatus](#setstatus) členskou funkci.

### <a name="remarks"></a>Poznámky

Datum je nastavena na zadané hodnoty. Čas je nastavena na čase 0, o půlnoci.

V následující tabulce najdete hranice pro hodnoty parametrů:

|Parametr|Hranice|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

Pokud přetečení den v měsíci, je převeden na správný den následujícího měsíce a měsíc nebo rok se zvýší odpovídajícím způsobem. Den hodnota nula znamená poslední den předchozího měsíce. Chování je stejné jako `SystemTimeToVariantTime`.

Pokud data hodnotu zadanou pomocí parametrů není platná, je nastaven stav tohoto objektu `COleDateTime::invalid`. Měli byste použít [GetStatus](#getstatus) ke kontrole platnosti `DATE` hodnota a nesmí se předpokládá, že hodnota [m_dt](#m_dt) zůstanou beze změny.

Tady jsou některé příklady s hodnotami kalendářních dat:

|*nYear*|*nMonth*|*nDay*|Hodnota|
|-------------|--------------|------------|-----------|
|2000|2|29|29. února 2000|
|1776|7|4|4. července 1776|
|1925|4|35|35 1925 dne (neplatné datum)|
|10000|1|1|1. ledna 10000 (neplatné datum)|

Pokud chcete nastavit datum a čas, najdete v článku [COleDateTime::SetDateTime](#setdatetime).

Informace o členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>  COleDateTime::SetDateTime

Nastaví datum a čas tohoto `COleDateTime` objektu.

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

*nYear*, *nMonth*, *Nden*, *Nhodina*, *Nminimum*, *nSec*<br/>
Označení součásti datum a čas, které se mají zkopírovat do tohoto `COleDateTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Nula v případě hodnoty této třídy `COleDateTime` objekt byl nastaven úspěšně; v opačném případě 1. Podle tohoto návratová hodnota `DateTimeStatus` výčtového typu. Další informace najdete v tématu [SetStatus](#setstatus) členskou funkci.

### <a name="remarks"></a>Poznámky

V následující tabulce najdete hranice pro hodnoty parametrů:

|Parametr|Hranice|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Pokud přetečení den v měsíci, je převeden na správný den následujícího měsíce a měsíc nebo rok se zvýší odpovídajícím způsobem. Den hodnota nula znamená poslední den předchozího měsíce. Chování je stejné jako [SystemTimeToVariantTime](/windows/desktop/api/oleauto/nf-oleauto-systemtimetovarianttime).

Pokud hodnota data nebo času zadanou parametry není platná, že stav tohoto objektu nastavena na platný a hodnota tohoto objektu se nemění.

Tady jsou některé příklady hodnot času:

|*nHour*|*nMin*|*nSec*|Hodnota|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Neplatný|
|9|60|0|Neplatný|

Tady jsou některé příklady s hodnotami kalendářních dat:

|*nYear*|*nMonth*|*nDay*|Hodnota|
|-------------|--------------|------------|-----------|
|1995|4|15|15. dubna 1995|
|1789|7|14|17. července 1789|
|1925|2|30|Neplatný|
|10000|1|1|Neplatný|

Chcete-li nastavit pouze datum, naleznete v tématu [COleDateTime::SetDate](#setdate). Chcete-li nastavit pouze čas, naleznete v tématu [COleDateTime::SetTime](#settime).

Informace o členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetStatus](#getstatus).

##  <a name="setstatus"></a>  COleDateTime::SetStatus

Nastaví stav této `COleDateTime` objektu.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parametry

*status*<br/>
Nová hodnota pro tento stav `COleDateTime` objektu.

### <a name="remarks"></a>Poznámky

*Stav* hodnota parametru je definována `DateTimeStatus` Výčtový typ, který je definován v rámci `COleDateTime` třídy. Zobrazit [COleDateTime::GetStatus](#getstatus) podrobnosti.

> [!CAUTION]
>  Tato funkce je pro pokročilé situacích programování. Tato funkce nezmění data v tomto objektu. Nejčastěji se používají se nastavit stav na **null** nebo **neplatný**. Operátor přiřazení ([operátoru =](#operator_eq)) a [SetDateTime](#setdatetime) nastavit stav objektu podle hodnoty, které zdroj.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetStatus](#getstatus).

##  <a name="settime"></a>  COleDateTime::SetTime

Nastaví čas tohoto `COleDateTime` objektu.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*nHour*, *nMin*, *nSec*<br/>
Označuje čas komponent, které mají být zkopírovány do tohoto `COleDateTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Nula v případě hodnoty této třídy `COleDateTime` objekt byl nastaven úspěšně; v opačném případě 1. Podle tohoto návratová hodnota `DateTimeStatus` výčtového typu. Další informace najdete v tématu [SetStatus](#setstatus) členskou funkci.

### <a name="remarks"></a>Poznámky

Čas je nastavena na zadané hodnoty. Datum bylo nastaveno na datum 0, což znamená 30 1899 dne.

V následující tabulce najdete hranice pro hodnoty parametrů:

|Parametr|Hranice|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Pokud čas, který není platný, hodnoty určené parametry stav tohoto objektu nastavena na platný a hodnota tohoto objektu se nemění.

Tady jsou některé příklady hodnot času:

|*nHour*|*nMin*|*nSec*|Hodnota|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Neplatný|
|9|60|0|Neplatný|

Pokud chcete nastavit datum a čas, najdete v článku [COleDateTime::SetDateTime](#setdatetime).

Informace o členských funkcí, které se dotazují hodnota tohoto `COleDateTime` objektu, najdete v následujících členské funkce:

- [GetDay](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetMinute](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [SetDate](#setdate).

## <a name="see-also"></a>Viz také:

[COleVariant – třída](../../mfc/reference/colevariant-class.md)<br/>
[CTime – třída](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
