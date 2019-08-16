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
ms.openlocfilehash: a254019d1efe916365799affa3d2c5271883bafb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491262"
---
# <a name="coledatetime-class"></a>COleDateTime – třída

Zapouzdřuje `DATE` datový typ, který se používá v automatizaci OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDateTime
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleDateTime::COleDateTime](#coledatetime)|`COleDateTime` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleDateTime:: Format](#format)|Generuje formátovanou řetězcovou reprezentaci `COleDateTime` objektu.|
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Voláním této metody získáte čas v `COleDateTime` objektu `DBTIMESTAMP` jako datovou strukturu.|
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Voláním této metody získáte čas v `COleDateTime` objektu jako strukturu dat [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) .|
|[COleDateTime::GetAsUDATE](#getasudate)|Voláním této metody získáte čas v rámci `COleDateTime` `UDATE` struktury dat.|
|[COleDateTime::GetCurrentTime](#getcurrenttime)|`COleDateTime` Vytvoří objekt, který představuje aktuální čas (statickou členskou funkci).|
|[COleDateTime:: getDay –](#getday)|Vrátí den, který `COleDateTime` tento objekt představuje (1-31).|
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu, který tento `COleDateTime` objekt představuje (neděle = 1).|
|[COleDateTime::GetDayOfYear](#getdayofyear)|Vrátí den v roce, který tento `COleDateTime` objekt představuje (1. ledna = 1).|
|[COleDateTime:: GetHour](#gethour)|Vrátí hodinu, kterou `COleDateTime` tento objekt představuje (0-23).|
|[COleDateTime:: GetMinute](#getminute)|Vrátí minutu, který `COleDateTime` tento objekt představuje (0-59).|
|[COleDateTime:: GetMonth](#getmonth)|Vrátí měsíc, který `COleDateTime` tento objekt představuje (1-12).|
|[COleDateTime::GetSecond](#getsecond)|Vrátí druhý, který `COleDateTime` tento objekt představuje (0-59).|
|[COleDateTime:: GetStatus](#getstatus)|Získá stav (platnost) tohoto `COleDateTime` objektu.|
|[COleDateTime:: GetYear](#getyear)|Vrátí rok, který `COleDateTime` tento objekt představuje.|
|[COleDateTime::P arseDateTime](#parsedatetime)|Přečte hodnotu data a času z řetězce a nastaví hodnotu `COleDateTime`.|
|[COleDateTime:: SetDate –](#setdate)|Nastaví hodnotu tohoto `COleDateTime` objektu na zadanou hodnotu pouze data.|
|[COleDateTime::SetDateTime](#setdatetime)|Nastaví hodnotu tohoto `COleDateTime` objektu na zadanou hodnotu data a času.|
|[COleDateTime:: SetStatus](#setstatus)|Nastaví stav (platnost) tohoto `COleDateTime` objektu.|
|[COleDateTime:: SetTime –](#settime)|Nastaví hodnotu tohoto `COleDateTime` objektu na zadanou pouze časovou hodnotu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[COleDateTime:: operator = =, COleDateTime:: operator < atd.](#coledatetime_relational_operators)|Porovná `COleDateTime` dvě hodnoty.|
|[COleDateTime:: operator +, COleDateTime:: operator-](#operator_add_-)|Sčítání a odečítání `COleDateTime` hodnot.|
|[COleDateTime:: operator + =, COleDateTime:: operator-=](#operator_add_eq_-_eq)|Přidat a odečíst `COleDateTime` hodnotu z tohoto `COleDateTime` objektu.|
|[COleDateTime:: operator =](#operator_eq)|`COleDateTime` Zkopíruje hodnotu.|
|[COleDateTime:: operator – datum, COleDateTime:: operator Date *](#operator_date)|`COleDateTime` Převede hodnotu`DATE` na nebo `DATE*`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleDateTime::m_dt](#m_dt)|Obsahuje podklad `DATE` pro tento `COleDateTime` objekt.|
|[COleDateTime::m_status](#m_status)|Obsahuje stav tohoto `COleDateTime` objektu.|

## <a name="remarks"></a>Poznámky

`COleDateTime`nemá základní třídu.

Je jedním z možných typů datového typu [variant](/windows/win32/api/oaidl/ns-oaidl-variant) automatizace OLE. `COleDateTime` Hodnota představuje absolutní hodnotu data a času.

`DATE` Typ je implementován jako hodnota s plovoucí desetinnou čárkou. Dny se měří od 30. prosince 1899 po půlnoci. V následující tabulce jsou uvedena některá data a jejich přidružené hodnoty:

|Datum|Value|
|----------|-----------|
|29. prosince 1899, půlnoc|-1.0|
|29. prosince 1899, 6. M|-1.25|
|30. prosince 1899, půlnoc|0.0|
|31. prosince 1899, půlnoc|1.0|
|1\. ledna 1900, 6 dop.|2.25|

> [!CAUTION]
> V tabulce výše se hodnoty denních hodnot neprojeví po 30. prosinci 1899, ale hodnoty dnů budou záporné. Například 6:00 AM je vždy vyjádřena jako zlomková hodnota 0,25 bez ohledu na to, zda celé číslo představující den je kladné (po 30. prosinci 1899) nebo záporné (před 30. prosince, 1899). To znamená, že jednoduché porovnání s plovoucí desetinnou čárkou by `COleDateTime` omylem seřadilo představující 6:00 dop. 12/29/1899 jako **pozdější** než jedna, která představuje 7:00 dop.

`COleDateTime` Třída zpracovává data od 1. ledna 100 do 31. prosince 9999. `COleDateTime` Třída používá gregoriánský kalendář; nepodporuje juliánské data. `COleDateTime`ignoruje letní čas. (Viz [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.)

> [!NOTE]
> Pomocí `%y` formátu můžete načíst dvoumístný rok jenom pro data začínající na 1900. Použijete-li `%y` formát pro datum před 1900, kód vygeneruje chybu kontrolního výrazu.

Tento typ se používá také k vyjádření hodnot pouze data a času. Podle konvence je datum 0 (30. prosince 1899) použito pouze pro časové hodnoty a čas 00:00 (půlnoc) je použit pouze pro hodnoty data.

`COleDateTime` Vytvoříte-li objekt pomocí data menšího než 100, bude datum přijato, ale následné `GetMinute` `GetYear`volání, `GetHour` `GetMonth` `GetDay`,,, a `GetSecond` selžou a vrátí-1. Dřív jste mohli použít dvoumístné datum, ale data musí být 100 nebo větší v knihovně MFC 4,2 a novější.

Chcete-li se vyhnout problémům, zadejte čtyřmístné datum. Příklad:

[!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]

Základní aritmetické operace pro `COleDateTime` hodnoty používají doprovodnou třídu [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan`hodnoty definují časový interval. Vztah mezi těmito třídami je podobný jako ten mezi [CTime –](../../atl-mfc-shared/reference/ctime-class.md) a [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Další informace o `COleDateTime` třídách a `COleDateTimeSpan` naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

## <a name="requirements"></a>Požadavky

**Hlaviček** ATLComTime.h

##  <a name="coledatetime_relational_operators"></a>Relační operátory COleDateTime

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
`COleDateTime` Objekt, který má být porovnán.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  K ATLASSERT dojde, pokud některý z těchto dvou operandů není platný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]

### <a name="example"></a>Příklad

Operátory **>=** , **,\<a, budou vyhodnotit, pokud je objekt nastaven na hodnotu null. =** **>** **<** `COleDateTime`

[!code-cpp[NVC_ATLMFC_Utilities#170](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_3.cpp)]

##  <a name="coledatetime"></a>COleDateTime::COleDateTime

`COleDateTime` Vytvoří objekt.

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
Existující `COleDateTime` objekt, který má být zkopírován do nového `COleDateTime` objektu.

*varSrc*<br/>
Existující `VARIANT` datová struktura ( `COleVariant` pravděpodobně objekt), která má být převedena na hodnotu data a času (VT_DATE) a zkopírována do nového `COleDateTime` objektu.

*dtSrc*<br/>
Hodnota data a času (`DATE`), která se má zkopírovat do nového `COleDateTime` objektu.

*timeSrc*<br/>
Hodnota `time_t` `COleDateTime` nebo `__time64_t` , která má být převedena na hodnotu data a času a zkopírována do nového objektu.

*systimeSrc*<br/>
Struktura, která má být převedena na hodnotu data a času a zkopírována do `COleDateTime` nového objektu. `SYSTEMTIME`

*filetimeSrc*<br/>
Struktura, která má být převedena na hodnotu data a času a zkopírována do `COleDateTime` nového objektu. `FILETIME` `FILETIME` Používá univerzální koordinovaný čas (UTC), takže pokud předáte místní čas ve struktuře, vaše výsledky budou nesprávné. Další informace najdete v tématu [časy souborů](/windows/win32/SysInfo/file-times) v Windows SDK.

*nYear*, *nMonth*, *nden*, *nhodina*, *nminimum*, *NSEC*<br/>
Označuje hodnoty data a času, které mají být zkopírovány do `COleDateTime` nového objektu.

*wDosDate*, *wDosTime*<br/>
Hodnoty data a času systému MS-DOS mají být převedeny na hodnotu data a času a zkopírovány do nového `COleDateTime` objektu.

*timeStamp*<br/>
Odkaz na strukturu [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) obsahující aktuální místní čas.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvoří nové `COleDateTime` objekty inicializované na zadanou hodnotu. V následující tabulce jsou uvedeny platné rozsahy pro každou komponentu data a času:

|Komponenta data a času|Platný rozsah|
|--------------------------|-----------------|
|rok|100 - 9999|
|měsíc|0 - 12|
|den|0 - 31|
|hodiny|0 - 23|
|za|0 - 59|
|první|0 - 59|

Všimněte si, že skutečná horní mez pro denní součást se liší v závislosti na komponentách pro měsíc a rok. Podrobnosti naleznete v tématu `SetDate` členské funkce nebo. `SetDateTime`

Následuje stručný popis každého konstruktoru:

- `COleDateTime(` **)** Vytvoří objekt inicializovaný `COleDateTime` jako 0 (půlnoc, 30. prosince 1899).

- `COleDateTime(`) Vytvoří objekt`COleDateTime` z existujícího`COleDateTime`objektu. `dateSrc`

- `COleDateTime(`*varSrc* **)** Vytvoří `COleDateTime` objekt. Pokusí se převést `VARIANT` strukturu nebo objekt [COleVariant](../../mfc/reference/colevariant-class.md) na hodnotu data a času ( `VT_DATE`). Pokud je tento převod úspěšný, převedená hodnota se zkopíruje do nového `COleDateTime` objektu. Pokud není, hodnota `COleDateTime` objektu je nastavena na 0 (půlnoc, 30. prosince 1899) a jeho stav na neplatné.

- `COleDateTime(`) Vytvoří objektz`DATE` hodnoty. `dtSrc` `COleDateTime`

- `COleDateTime(`) Vytvoří objektz`time_t` hodnoty. `timeSrc` `COleDateTime`

- `COleDateTime(`*systimeSrc* **) Vytvoří objekt z** `SYSTEMTIME`hodnoty. `COleDateTime`

- `COleDateTime(`) Vytvoří objektz`FILETIME` hodnoty. `filetimeSrc` `COleDateTime` . `FILETIME` Používá univerzální koordinovaný čas (UTC), takže pokud předáte místní čas ve struktuře, vaše výsledky budou nesprávné. Další informace najdete v tématu [časy souborů](/windows/win32/SysInfo/file-times) v Windows SDK.

- `COleDateTime(``nYear`, ,`nMonth` ,,`nMin`, ) Vytvoří objektzezadaných`COleDateTime` číselných hodnot. `nHour` `nDay` `nSec`

- `COleDateTime(`) Vytvoří objekt z určených hodnot data a času systému MS-DOS. `wDosDate` `wDosTime` `COleDateTime`

Další informace o `time_t` datovém typu najdete v tématu [Časová](../../c-runtime-library/reference/time-time32-time64.md) funkce v *Referenční příručce ke knihovně run-time*.

Další informace najdete v tématu struktury [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) a [Time](/windows/win32/api/minwinbase/ns-minwinbase-filetime) v Windows SDK.

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

> [!NOTE]
> Konstruktor using je `DBTIMESTAMP` k dispozici pouze v případě, že je použit OLEDB. h.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#2](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_4.cpp)]

##  <a name="format"></a>COleDateTime:: Format

Vytvoří formátovaná reprezentace hodnoty data a času.

```
CString Format(DWORD dwFlags = 0,  LCID lcid = LANG_USER_DEFAULT) const;
CString Format(LPCTSTR lpszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Označuje jeden z následujících příznaků národního prostředí:

- LOCALE_NOUSEROVERRIDE místo vlastního uživatelského nastavení použít výchozí nastavení národního prostředí systému.

- VAR_TIMEVALUEONLY ignoruje část data během analýzy.

- VAR_DATEVALUEONLY ignoruje časovou část při analýze.

*lcid*<br/>
Označuje ID národního prostředí, které se má použít pro převod. Další informace o identifikátorech jazyků naleznete v tématu [jazykové identifikátory](/windows/win32/Intl/language-identifiers).

*lpszFormat*<br/>
Řetězec formátování podobný `printf` řetězci formátování. Každý formátovací kód, před kterým je znak procenta ( `%`), je nahrazen odpovídající `COleDateTime` komponentou. Jiné znaky v řetězci formátování jsou zkopírovány beze změny do vráceného řetězce. Další informace najdete v tématu Běhová funkce [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md). Hodnota a význam kódů formátování pro `Format` jsou:

- `%H`Hodiny v aktuálním dni

- `%M`Minuty v aktuální hodině

- `%S`Sekundy v aktuální minutě

- `%%`Symbol procenta

*nFormatID*<br/>
ID prostředku pro řetězec řízení formátu.

### <a name="return-value"></a>Návratová hodnota

`CString` Obsahující formát hodnoty data a času.

### <a name="remarks"></a>Poznámky

Pokud je stav tohoto `COleDateTime` objektu null, vrácená hodnota je prázdný řetězec. Pokud je stav neplatný, vrácený řetězec je určen řetězcovým prostředkem ATL_IDS_DATETIME_INVALID.

Následuje stručný popis tří forem této funkce:

`Format`( *dwFlags*, *lcid*)<br/>
Tato forma formátuje hodnotu pomocí specifikací jazyka (ID národního prostředí) pro datum a čas. Pomocí výchozích parametrů tento formulář vytiskne datum a čas, pokud je časová část 0 (půlnoc). v takovém případě bude vytištěno pouze datum, nebo je část data 0 (30. prosince 1899). v takovém případě bude vytištěna přesně čas. Pokud je hodnota datum/čas 0 (30. prosince 1899, půlnoc), bude tento formulář s výchozími parametry tisknout půlnoc.

`Format`( *lpszFormat*)<br/>
Tento formulář formátuje hodnotu pomocí formátovacího řetězce, který obsahuje kódy speciálního formátování, které předcházejí znak procenta (%), jako v `printf`. Formátovací řetězec je předán do funkce jako parametr. Další informace o kódech formátování naleznete v tématu [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) in Runtime Library Reference.

`Format`( *nFormatID*)<br/>
Tento formulář formátuje hodnotu pomocí formátovacího řetězce, který obsahuje kódy speciálního formátování, které předcházejí znak procenta (%), jako v `printf`. Formátovací řetězec je prostředek. ID tohoto prostředku řetězce se předává jako parametr. Další informace o kódech formátování naleznete v tématu [strftime, wcsftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) in *Runtime Library Reference*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]

##  <a name="getasdbtimestamp"></a>COleDateTime::GetAsDBTIMESTAMP

Voláním této metody získáte čas v `COleDateTime` objektu `DBTIMESTAMP` jako datovou strukturu.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& timeStamp) const throw();
```

### <a name="parameters"></a>Parametry

*timeStamp*<br/>
Odkaz na strukturu [DBTIMESTAMP](/dotnet/api/system.data.oledb.oledbtype) .

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Ukládá výsledný čas v odkazované struktuře *časového razítka* . Datová struktura inicializovaná touto funkcí bude `fraction` mít člena nastavenou na nulu. `DBTIMESTAMP`

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]

##  <a name="getassystemtime"></a>COleDateTime::GetAsSystemTime

Voláním této metody získáte čas v `COleDateTime` objektu `SYSTEMTIME` jako datovou strukturu.

```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```

### <a name="parameters"></a>Parametry

*sysTime –*<br/>
Odkaz na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) pro příjem převedené hodnoty data a času z `COleDateTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je úspěšná; FALSE, pokud převod neproběhne úspěšně, nebo `COleDateTime` Pokud je objekt null nebo neplatný.

### <a name="remarks"></a>Poznámky

`GetAsSystemTime`Ukládá výsledný čas do odkazovaného *sysTime –* objektu. Datová struktura inicializovaná touto funkcí bude `wMilliseconds` mít člena nastavenou na nulu. `SYSTEMTIME`

Další informace o stavu informací uložených v `COleDateTime` objektu naleznete v tématu GetStatus [](#getstatus).

##  <a name="getasudate"></a>COleDateTime::GetAsUDATE

Voláním této metody získáte čas v `COleDateTime` objektu `UDATE` jako datovou strukturu.

```
bool GetAsUDATE(UDATE& uDate) const throw();
```

### <a name="parameters"></a>Parametry

*uDate*<br/>
Odkaz na `UDATE` strukturu pro příjem převedené hodnoty data a času `COleDateTime` z objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je úspěšná; FALSE, pokud převod neproběhne úspěšně, nebo `COleDateTime` Pokud je objekt null nebo neplatný.

### <a name="remarks"></a>Poznámky

`UDATE` Struktura představuje datum "unpackd".

##  <a name="getcurrenttime"></a>COleDateTime::GetCurrentTime

Zavolejte tuto statickou členskou funkci, která vrátí aktuální hodnotu data a času.

```
static COleDateTime WINAPI GetCurrentTime() throw();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]

##  <a name="getday"></a>COleDateTime:: getDay –

Vrátí den v měsíci reprezentovaný touto hodnotou data a času.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v měsíci reprezentovaný hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud není možné získat den.

### <a name="remarks"></a>Poznámky

Platné návratové hodnoty jsou v rozsahu od 1 do 31.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]

##  <a name="getdayofweek"></a>COleDateTime:: metodu GetDayOfWeek

Vrátí den v měsíci reprezentovaný touto hodnotou data a času.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v týdnu reprezentovaný hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud se nepovedlo získat den v týdnu.

### <a name="remarks"></a>Poznámky

Platné návratové hodnoty v rozsahu od 1 do 7, kde 1 = neděle, 2 = pondělí atd.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]

##  <a name="getdayofyear"></a>COleDateTime::GetDayOfYear

Vrátí den v roce reprezentovaný touto hodnotou data a času.

```
int GetDayOfYear() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Den v roce reprezentovaný hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud není možné získat den v roce.

### <a name="remarks"></a>Poznámky

Platné návratové hodnoty v rozsahu od 1 do 366, přičemž 1. ledna = 1.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]

##  <a name="gethour"></a>COleDateTime:: GetHour

Získá hodinu reprezentovanou touto hodnotou data a času.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Hodina reprezentovaná hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud nebyla získána hodina.

### <a name="remarks"></a>Poznámky

Platné návratové hodnoty v rozsahu od 0 do 23.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]

##  <a name="getminute"></a>COleDateTime:: GetMinute

Vrátí minutu reprezentovanou touto hodnotou data a času.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Minuta reprezentovaná hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud nebyla získána minuta.

### <a name="remarks"></a>Poznámky

Platný návratové hodnoty v rozsahu od 0 do 59.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Podívejte se na příklad [](#gethour)pro GetHour.

##  <a name="getmonth"></a>COleDateTime:: GetMonth

Načte měsíc reprezentovaný touto hodnotou data a času.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Měsíc reprezentovaný hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud nelze získat měsíc.

### <a name="remarks"></a>Poznámky

Platné návratové hodnoty jsou v rozsahu od 1 do 12.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [getDay –](#getday).

##  <a name="getsecond"></a>COleDateTime:: GetSecond

Získá druhý reprezentovaný touto hodnotou data a času.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Druhý reprezentovaný hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud druhý nelze získat.

### <a name="remarks"></a>Poznámky

Platný návratové hodnoty v rozsahu od 0 do 59.

> [!NOTE]
>  `COleDateTime` Třída nepodporuje přestupné sekundy.

Další informace o implementaci pro `COleDateTime`najdete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

### <a name="example"></a>Příklad

Podívejte se na příklad [](#gethour)pro GetHour.

##  <a name="getstatus"></a>COleDateTime:: GetStatus

Získá stav (platnost) daného `COleDateTime` objektu.

```
DateTimeStatus GetStatus() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí stav této `COleDateTime` hodnoty. Pokud voláte `GetStatus` `COleDateTime` na objekt vytvořený s výchozím nastavením, bude vrácena platná. Pokud voláte `GetStatus` `COleDateTime` na objekt inicializovaný s konstruktorem nastaveným na hodnotu null, `GetStatus` bude vrácena hodnota null.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je definována `DateTimeStatus` výčtovým typem, který je definován `COleDateTime` v rámci třídy.

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

- `COleDateTime::error`Indikuje, že došlo k chybě při pokusu o získání části hodnoty data a času.

- `COleDateTime::valid`Označuje, že `COleDateTime` tento objekt je platný.

- `COleDateTime::invalid`Indikuje, že `COleDateTime` tento objekt je neplatný. to znamená, že jeho hodnota může být nesprávná.

- `COleDateTime::null`Označuje, že `COleDateTime` tento objekt má hodnotu null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Jedná se o hodnotu null ve smyslu databáze "bez hodnoty", a to na rozdíl od C++ hodnoty null.)

Stav `COleDateTime` objektu je neplatný v následujících případech:

- Je- `VARIANT` li jeho hodnota nastavena z hodnoty `COleVariant` nebo, která nemohla být převedena na hodnotu data a času.

- Je- `time_t`li jeho hodnota nastavena z hodnoty `SYSTEMTIME`, nebo `FILETIME` , která nemohla být převedena na platnou hodnotu data a času.

- Je-li jeho hodnota nastavena `SetDateTime` s neplatnými hodnotami parametrů.

- V případě, `+=` že v tomto objektu došlo k přetečení nebo podtečení během operace aritmetického přiřazení `-=`, konkrétně nebo.

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na neplatné pomocí `SetStatus`.

Další informace o operacích, které můžou nastavit stav na neplatné, najdete v následujících členských funkcích:

- [COleDateTime](#coledatetime)

- [SetDateTime](#setdatetime)

- [operator +,-](#operator_add_-)

- [operator + =,-=](#operator_add_eq_-_eq)

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]

##  <a name="getyear"></a>COleDateTime:: GetYear

Získá rok reprezentovaný touto hodnotou data a času.

```
int GetYear() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Rok reprezentovaný hodnotou tohoto `COleDateTime` objektu, nebo `COleDateTime::error` Pokud nelze získat rok.

### <a name="remarks"></a>Poznámky

Platné návratové hodnoty jsou v rozsahu od 100 do 9999, což zahrnuje století.

Informace o dalších členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [getDay –](#getday).

##  <a name="m_dt"></a>COleDateTime::m_dt

Podkladová `DATE` struktura tohoto `COleDateTime` objektu.

```
DATE m_dt;
```

### <a name="remarks"></a>Poznámky

> [!CAUTION]
>  Změna hodnoty v `DATE` objektu, ke kterému se přistupovalo pomocí ukazatele vráceného touto funkcí, změní hodnotu `COleDateTime` tohoto objektu. Nemění stav tohoto `COleDateTime` objektu.

Další informace o implementaci `DATE` objektu naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

##  <a name="m_status"></a>  COleDateTime::m_status

Obsahuje stav tohoto `COleDateTime` objektu.

```
DateTimeStatus m_status;
```

### <a name="remarks"></a>Poznámky

Typ tohoto datového členu je výčtový typ `DateTimeStatus`, který je definován `COleDateTime` v rámci třídy. Další informace naleznete v tématu [COleDateTime:: GetStatus](#getstatus).

> [!CAUTION]
>  Tento datový člen slouží k pokročilým programovacím situacím. Měli byste použít funkce GetStatus a [](#getstatus) [SetStatus](#setstatus)vložených členů. Další `SetStatus` upozornění týkající se explicitního nastavení tohoto datového člena najdete v tématu.

##  <a name="operator_eq"></a>COleDateTime:: operator =

`COleDateTime` Zkopíruje hodnotu.

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

Tyto přetížené operátory přiřazení kopírují hodnotu zdrojového data a času do tohoto `COleDateTime` objektu. Stručný popis každého z těchto přetížených operátorů přiřazení je následující:

- **operator = (** `dateSrc` **)** hodnota a stav operandu jsou zkopírovány do tohoto `COleDateTime` objektu.

- **operator = (** *varSrc* **)** – operátor Je-li převod hodnoty [variant](/windows/win32/api/oaidl/ns-oaidl-variant) (nebo objektu [COleVariant](../../mfc/reference/colevariant-class.md) ) na datum a čas (VT_DATE) úspěšný, převedená hodnota je zkopírována do tohoto `COleDateTime` objektu a její stav je nastaven na hodnotu platné. Pokud převod není úspěšný, hodnota tohoto objektu je nastavena na nulu (30. prosince 1899, půlnoc) a jeho stav na neplatné.

- **operator = (** `dtSrc` `COleDateTime` )`DATE` hodnota je zkopírována do tohoto objektu a její stav je nastaven na hodnotu platné.

- **operator = (** `timeSrc` `COleDateTime` **)** `time_t` hodnota nebo`__time64_t` je převedena a zkopírována do tohoto objektu. Pokud je převod úspěšný, stav tohoto objektu je nastaven na platná; Pokud je to neúspěšné, je nastavené na neplatné.

- **operator = (** *systimeSrc* **)** – operátor Hodnota [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) je převedena a zkopírována do `COleDateTime` tohoto objektu. Pokud je převod úspěšný, stav tohoto objektu je nastaven na platná; Pokud je to neúspěšné, je nastavené na neplatné.

- **operator = (** `uDate` `COleDateTime` )`UDATE` hodnota je převedena a zkopírována do tohoto objektu. Pokud je převod úspěšný, stav tohoto objektu je nastaven na platná; Pokud je to neúspěšné, je nastavené na neplatné. `UDATE` Struktura představuje datum "unpackd". Další informace najdete v tématu funkce [VarDateFromUdate](/windows/win32/api/oleauto/nf-oleauto-vardatefromudate).

- **operator = (** `filetimeSrc` **)** hodnota [doby běhu](/windows/win32/api/minwinbase/ns-minwinbase-filetime) je převedena do tohoto objektu a `COleDateTime` zkopírována do tohoto objektu. Pokud je převod úspěšný, stav tohoto objektu je nastaven na platná; v opačném případě je nastaveno na neplatné. `FILETIME`používá světový koordinovaný čas (UTC), takže pokud předáte čas UTC ve struktuře, výsledky budou převedeny z času UTC na místní čas a budou uloženy jako čas varianty. Toto chování je stejné jako v jazyce Visual C++ 6,0 a visual C++.NET 2003 SP2. Další informace najdete v tématu [časy souborů](/windows/win32/SysInfo/file-times) v Windows SDK.

Další informace naleznete v položce [variant](/windows/win32/api/oaidl/ns-oaidl-variant) v Windows SDK.

Další informace o `time_t` datovém typu najdete v tématu [Časová](../../c-runtime-library/reference/time-time32-time64.md) funkce v *Referenční příručce ke knihovně run-time*.

Další informace najdete v tématu struktury [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) a [Time](/windows/win32/api/minwinbase/ns-minwinbase-filetime) v Windows SDK.

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

##  <a name="operator_add_-"></a>COleDateTime:: operator +,-

Sčítání a odečítání `ColeDateTime` hodnot.

```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```

### <a name="remarks"></a>Poznámky

`COleDateTime`objekty reprezentují absolutní časy. Objekty [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) reprezentují relativní časy. První dva operátory umožňují přidat a odečíst `COleDateTimeSpan` hodnotu `COleDateTime` z hodnoty. Třetí operátor vám umožní odečíst jednu `COleDateTime` hodnotu od druhé, aby se `COleDateTimeSpan` vydávala hodnota.

Pokud je jeden z operandů null, stav výsledné `COleDateTime` hodnoty je null.

Pokud výsledná `COleDateTime` hodnota spadá mimo hranice přípustných hodnot, stav `COleDateTime` této hodnoty je neplatný.

Pokud je jeden z operandů neplatný a druhý není null, stav výsledné `COleDateTime` hodnoty je neplatný.

Operátory a **budou-** uplatněny, pokud je objektnastavennahodnotunull.`COleDateTime` **+** Příklad najdete v tématu [relační operátory COleDateTime](#coledatetime_relational_operators) .

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v části členské proměnné [m_status](#m_status) .

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>COleDateTime:: operator + =,-=

Přidat a odečíst `ColeDateTime` hodnotu z tohoto `COleDateTime` objektu.

```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují přidat a odečíst `COleDateTimeSpan` hodnotu `COleDateTime`z. Pokud je jeden z operandů null, stav výsledné `COleDateTime` hodnoty je null.

Pokud výsledná `COleDateTime` hodnota spadá mimo hranice přípustných hodnot, je stav této `COleDateTime` hodnoty nastaven na neplatné.

Pokud je jeden z operandů neplatný a druhý není null, stav výsledné `COleDateTime` hodnoty je neplatný.

Další informace o platných, neplatných a hodnotách stavu s hodnotou null naleznete v části členské proměnné [m_status](#m_status) .

Operátory a **budou-=** uplatněny, pokud je objektnastavennahodnotunull.`COleDateTime` **+=** Příklad najdete v tématu [relační operátory COleDateTime](#coledatetime_relational_operators) .

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

##  <a name="operator_date"></a>COleDateTime:: operator – datum

`ColeDateTime` Převede hodnotu`DATE`na.

```
operator DATE() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí `DATE` objekt, jehož hodnota je zkopírována z `COleDateTime` tohoto objektu. Další informace o implementaci `DATE` objektu naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

Operátor `DATE` uplatní, `COleDateTime` Pokud je objekt nastaven na hodnotu null. Příklad najdete v tématu [relační operátory COleDateTime](#coledatetime_relational_operators) .

##  <a name="parsedatetime"></a>COleDateTime::P arseDateTime

Analyzuje řetězec pro čtení hodnoty data a času.

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
Označuje příznaky pro nastavení národního prostředí a analýzu. Jeden nebo více následujících příznaků:

- LOCALE_NOUSEROVERRIDE místo vlastního nastavení uživatele použít výchozí nastavení národního prostředí systému.

- VAR_TIMEVALUEONLY ignoruje část data během analýzy.

- VAR_DATEVALUEONLY ignoruje časovou část při analýze.

*lcid*<br/>
Označuje ID národního prostředí, které se má použít pro převod.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byl řetězec úspěšně převeden na hodnotu data a času, v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud byl řetězec úspěšně převeden na hodnotu data a času, hodnota tohoto `COleDateTime` objektu je nastavena na tuto hodnotu a její stav na platná.

> [!NOTE]
>  Hodnoty roku musí být v rozmezí od 100 do 9999 (včetně).

Parametr *lpszDate* může mít různé formáty. Například následující řetězce obsahují přijatelné formáty data a času:

`"25 January 1996"`

`"8:30:00"`

`"20:30:00"`

`"January 25, 1996 8:30:00"`

`"8:30:00 Jan. 25, 1996"`

`"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`

ID národního prostředí má vliv také na to, zda je formát řetězce přijatelný pro převod na hodnotu data a času.

V případě VAR_DATEVALUEONLY je hodnota Time nastavená na hodnotu Time 0 nebo půlnoc. V případě VAR_TIMEVALUEONLY je hodnota Date nastavená na Date 0, což znamená 30. prosince 1899.

Pokud řetězec nelze převést na hodnotu data a času nebo pokud došlo k numerickému přetečení, je stav tohoto `COleDateTime` objektu neplatný.

Další informace o hranicích a implementaci pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

##  <a name="setdate"></a>COleDateTime:: SetDate –

Nastaví datum tohoto `COleDateTime` objektu.

```
int SetDate(
    int nYear,
    int nMonth,
    int nDay) throw();
```

### <a name="parameters"></a>Parametry

*nYear*, *nMonth*, *nden*<br/>
Určete komponenty data, které mají být zkopírovány `COleDateTime` do tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud byla hodnota tohoto `COleDateTime` objektu nastavena úspěšně. v opačném případě 1. Tato návratová hodnota vychází `DateTimeStatus` z výčtového typu. Další informace naleznete v tématu členská funkce [SetStatus](#setstatus) .

### <a name="remarks"></a>Poznámky

Datum je nastaveno na zadané hodnoty. Čas je nastaven na hodnotu čas 0, půlnoc.

V následující tabulce najdete meze pro hodnoty parametrů:

|Parametr|Hranice|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|

Pokud se den v měsíci přesměruje, převede se na správný den příštího měsíce a v měsíci a/nebo roce se odpovídajícím způsobem zvýší. Nulová hodnota dne označuje poslední den v předchozím měsíci. Chování je stejné jako `SystemTimeToVariantTime`.

Pokud hodnota data zadaná parametry není platná, je stav tohoto objektu nastaven na `COleDateTime::invalid`hodnotu. Měli byste použít [GetStatus](#getstatus) ke kontrole platnosti `DATE` hodnoty a neměli byste předpokládat, že hodnota [m_dt](#m_dt) zůstane beze změny.

Tady je několik příkladů hodnot data:

|*nYear*|*nMonth*|*nDay*|Value|
|-------------|--------------|------------|-----------|
|2000|2|29|29. února 2000|
|1776|7|4|4\. července 1776|
|1925|4|35|35. dubna 1925 (neplatné datum)|
|10000|1|1|1\. ledna 10000 (neplatné datum)|

Chcete-li nastavit datum a čas, viz [COleDateTime:: SetDateTime](#setdatetime).

Informace o členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#11](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_14.cpp)]

##  <a name="setdatetime"></a>COleDateTime::SetDateTime

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

*nYear*, *nMonth*, *nden*, *nhodina*, *nminimum*, *NSEC*<br/>
Označte komponenty data a času, které mají být zkopírovány `COleDateTime` do tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud byla hodnota tohoto `COleDateTime` objektu nastavena úspěšně. v opačném případě 1. Tato návratová hodnota vychází `DateTimeStatus` z výčtového typu. Další informace naleznete v tématu členská funkce [SetStatus](#setstatus) .

### <a name="remarks"></a>Poznámky

V následující tabulce najdete meze pro hodnoty parametrů:

|Parametr|Hranice|
|---------------|------------|
|*nYear*|100 - 9999|
|*nMonth*|1 - 12|
|*nDay*|0 - 31|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Pokud se den v měsíci přesměruje, převede se na správný den příštího měsíce a v měsíci a/nebo roce se odpovídajícím způsobem zvýší. Nulová hodnota dne označuje poslední den v předchozím měsíci. Chování je stejné jako [SystemTimeToVariantTime](/windows/win32/api/oleauto/nf-oleauto-systemtimetovarianttime).

Pokud hodnota data nebo času zadaná parametry není platná, stav tohoto objektu je nastaven na hodnotu neplatné a hodnota tohoto objektu se nezmění.

Tady je několik příkladů časových hodnot:

|*nHour*|*nMin*|*nSec*|Value|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Neplatný|
|9|60|0|Neplatný|

Tady je několik příkladů hodnot data:

|*nYear*|*nMonth*|*nDay*|Value|
|-------------|--------------|------------|-----------|
|1995|4|15|15. dubna 1995|
|1789|7|14|17. července 1789|
|1925|2|30|Neplatný|
|10000|1|1|Neplatný|

Chcete-li nastavit pouze datum, viz [COleDateTime:: SetDate –](#setdate). Chcete-li nastavit pouze čas, viz [COleDateTime:: SetTime –](#settime).

Informace o členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

### <a name="example"></a>Příklad

Podívejte se na příklad [](#getstatus)pro GetStatus.

##  <a name="setstatus"></a>COleDateTime:: SetStatus

Nastaví stav tohoto `COleDateTime` objektu.

```
void SetStatus(DateTimeStatus status) throw();
```

### <a name="parameters"></a>Parametry

*status*<br/>
Nová hodnota stavu pro tento `COleDateTime` objekt.

### <a name="remarks"></a>Poznámky

Hodnota parametru *status* je definována `DateTimeStatus` výčtovým typem, který `COleDateTime` je definován v rámci třídy. Podrobnosti naleznete v tématu [COleDateTime:: GetStatus](#getstatus) .

> [!CAUTION]
>  Tato funkce je určena pro pokročilé programovací situace. Tato funkce nemění data v tomto objektu. Nejčastěji se použije k nastavení stavu na **hodnotu null** nebo **neplatný**. Operátor přiřazení ([Operator =](#operator_eq)) a [SetDateTime](#setdatetime) nastaví stav objektu na základě zdrojových hodnot (y).

### <a name="example"></a>Příklad

Podívejte se na příklad [](#getstatus)pro GetStatus.

##  <a name="settime"></a>COleDateTime:: SetTime –

Nastaví čas tohoto `COleDateTime` objektu.

```
int SetTime(
    int nHour,
    int nMin,
    int nSec) throw();
```

### <a name="parameters"></a>Parametry

*nHour*, *nMin*, *nSec*<br/>
Určete časové komponenty, které se mají zkopírovat do `COleDateTime` tohoto objektu.

### <a name="return-value"></a>Návratová hodnota

Nula, pokud byla hodnota tohoto `COleDateTime` objektu nastavena úspěšně. v opačném případě 1. Tato návratová hodnota vychází `DateTimeStatus` z výčtového typu. Další informace naleznete v tématu členská funkce [SetStatus](#setstatus) .

### <a name="remarks"></a>Poznámky

Čas je nastaven na zadané hodnoty. Datum je nastavené na datum 0, což znamená 30. prosince 1899.

V následující tabulce najdete meze pro hodnoty parametrů:

|Parametr|Hranice|
|---------------|------------|
|*nHour*|0 - 23|
|*nMin*|0 - 59|
|*nSec*|0 - 59|

Pokud hodnota času zadaná parametry není platná, stav tohoto objektu je nastaven na hodnotu neplatné a hodnota tohoto objektu se nezmění.

Tady je několik příkladů časových hodnot:

|*nHour*|*nMin*|*nSec*|Value|
|-------------|------------|------------|-----------|
|1|3|3|01:03:03|
|23|45|0|23:45:00|
|25|30|0|Neplatný|
|9|60|0|Neplatný|

Chcete-li nastavit datum a čas, viz [COleDateTime:: SetDateTime](#setdatetime).

Informace o členských funkcích, které dotazují hodnotu tohoto `COleDateTime` objektu, naleznete v následujících členských funkcích:

- [GetDay –](#getday)

- [GetMonth –](#getmonth)

- [GetYear –](#getyear)

- [GetHour](#gethour)

- [Getminuta](#getminute)

- [GetSecond](#getsecond)

- [GetDayOfWeek](#getdayofweek)

- [GetDayOfYear](#getdayofyear)

Další informace o hranicích pro `COleDateTime` hodnoty naleznete v článku [datum a čas: Podpora](../../atl-mfc-shared/date-and-time-automation-support.md)automatizace.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [SetDate –](#setdate).

## <a name="see-also"></a>Viz také:

[COleVariant – třída](../../mfc/reference/colevariant-class.md)<br/>
[CTime – třída](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
