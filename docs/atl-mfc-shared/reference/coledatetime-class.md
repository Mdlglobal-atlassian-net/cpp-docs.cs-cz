---
title: Třída COleDateTime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- shared classes, COleDateTime
- time-only values
- Date data type, MFC encapsulation of
- COleDateTime class
- dates, handling in MFC
- time, handling in MFC
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ac939714eff9473397cbe50075f3082f38cdf23
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="coledatetime-class"></a>COleDateTime – třída
Zapouzdří `DATE` datový typ, který se používá v automatizace OLE.  
  
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
|[COleDateTime::Format](#format)|Generuje formátovaný řetězcovou reprezentaci `COleDateTime` objektu.|  
|[COleDateTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Volat tuto metodu za účelem získání čas v `COleDateTime` objekt jako **DBTIMESTAMP** datové struktury.|  
|[COleDateTime::GetAsSystemTime](#getassystemtime)|Volat tuto metodu za účelem získání čas v `COleDateTime` objekt jako [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) datové struktury.|  
|[COleDateTime::GetAsUDATE](#getasudate)|Volat tuto metodu za účelem získání čas v `COleDateTime` jako **AKT.rev.AUKCE** datové struktury.|  
|[COleDateTime::GetCurrentTime](#getcurrenttime)|Vytvoří `COleDateTime` objekt, který představuje aktuální čas (funkce statický člen).|  
|[COleDateTime::GetDay](#getday)|Vrátí den `COleDateTime` objekt představuje (1-31).|  
|[COleDateTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu, to `COleDateTime` objektu představuje (neděle = 1).|  
|[COleDateTime::GetDayOfYear](#getdayofyear)|Vrátí den v roce to `COleDateTime` objektu představuje (od 1 = 1).|  
|[COleDateTime::GetHour](#gethour)|Vrátí hodinu, toto `COleDateTime` objektu představuje (0 - 23).|  
|[COleDateTime::GetMinute](#getminute)|Vrátí minutu to `COleDateTime` objektu představuje (0 - 59).|  
|[COleDateTime::GetMonth](#getmonth)|Vrátí měsíc `COleDateTime` objekt představuje (1-12).|  
|[COleDateTime::GetSecond](#getsecond)|Vrátí druhou to `COleDateTime` objektu představuje (0 - 59).|  
|[COleDateTime::GetStatus](#getstatus)|Získá stav (platnosti) to `COleDateTime` objektu.|  
|[COleDateTime::GetYear](#getyear)|Vrátí rok `COleDateTime` objekt představuje.|  
|[COleDateTime::ParseDateTime](#parsedatetime)|Načte hodnotu data a času v řetězci a nastaví hodnotu `COleDateTime`.|  
|[COleDateTime::SetDate](#setdate)|Nastaví hodnotu této `COleDateTime` objekt se zadanou hodnotou jen data.|  
|[COleDateTime::SetDateTime](#setdatetime)|Nastaví hodnotu této `COleDateTime` objekt k hodnotě zadané datum a čas.|  
|[COleDateTime::SetStatus](#setstatus)|Nastaví stav (platnosti) tohoto `COleDateTime` objektu.|  
|[COleDateTime::SetTime](#settime)|Nastaví hodnotu této `COleDateTime` objekt se zadanou hodnotou časových.|  
  
### <a name="public-operators"></a>Veřejné operátory  

|Název|Popis|  
|----------|-----------------|  
|[COleDateTime::operator == COleDateTime::operator < atd.](#coledatetime_relational_operators)|Porovnat `COleDateTime` hodnoty.|  
|[COleDateTime::operator + COleDateTime::operator-](#operator_add_-)|Sčítání a odečítání `COleDateTime` hodnoty.|  
|[+= COleDateTime::operator, COleDateTime::operator-=](#operator_add_eq_-_eq)|Sčítání a odečítání `COleDateTime` hodnotu z tohoto `COleDateTime` objektu.|  
|[COleDateTime::operator =](#operator_eq)|Kopie `COleDateTime` hodnotu.|  
|[DATUM, COleDateTime::operator COleDateTime::operator datum *](#operator_date)|Převede `COleDateTime` hodnotu do `DATE` nebo `DATE*`.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleDateTime::m_dt](#m_dt)|Obsahuje základní **datum** pro tento `COleDateTime` objektu.|  
|[COleDateTime::m_status](#m_status)|Obsahuje stav tohoto `COleDateTime` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `COleDateTime` nemá základní třídu.  
  
 Je jedním z možných typů pro [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) datový typ automatizace OLE. A `COleDateTime` hodnota představuje absolutní datum a čas.  
  
 `DATE` Typ je implementovaný jako hodnotu s plovoucí desetinnou čárkou. Počet dnů se měří z 30 prosinec 1899 půlnoci. V následující tabulce jsou uvedeny některé kalendářních dat a jejich přidružené hodnoty:  
  
|Datum|Hodnota|  
|----------|-----------|  
|29 prosinec 1899 půlnoc|-1.0|  
|29 prosinec 1899, dvanáctihodinového 6|-1.25|  
|30 prosinec 1899 půlnoc|0.0|  
|31. prosince 1899, půlnoc|1.0|  
|1. ledna 1900, 6 hodin ráno|2.25|  
  
> [!CAUTION]
>  V předchozí tabulce Upozorňujeme, že i když se stane před půlnoc na 30 prosinec 1899 záporné hodnoty den hodnoty času dne nepodporují. Například 6:00:00 je vždy označena desetinnou hodnotu 0,25 bez ohledu na to, jestli je celé číslo představující den (po 30 prosinec 1899) kladné a záporné (před 30. prosince 1899). To znamená, že by jednoduché plovoucí porovnání bodu chybnou informací řazení `COleDateTime` představující 6:00 AM na 12/29 nebo 1899 jako **později** než jeden představující 7:00 AM ve stejný den.  
  
 `COleDateTime` Třída kalendářní data z 1. leden 100, až 31. prosince 9999. `COleDateTime` Třída používá gregoriánský kalendář; nepodporuje juliánský data. `COleDateTime` ignoruje letní čas. (Viz [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).)  
  
> [!NOTE]
>  Můžete použít `%y` formátu načíst letopočty roku pouze pro data od 1900. Pokud použijete `%y` formát na datum před 1900, kód generuje chybu vyhodnocení.  
  
 Tento typ se také používá k reprezentaci hodnoty jen data nebo času. Podle konvence datum 0 (30 prosinec 1899) se používá pro časových hodnoty a 00:00 času (půlnoc) se používá pouze hodnoty.  
  
 Pokud vytvoříte `COleDateTime` objekt pomocí datum méně než 100, datum je přijatý, ale následné volání `GetYear`, `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, a `GetSecond` selhat a vrátí hodnotu -1. Dříve můžete použít letopočty data, ale data musí být 100 nebo větší v MFC 4.2 a vyšší.  
  
 Aby nedocházelo k problémům, zadejte čtyřmístný datum. Příklad:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_1.cpp)]  
  
 Pro základní aritmetické operace `COleDateTime` hodnoty použít třídu doprovodné [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md). `COleDateTimeSpan` určení hodnoty časového intervalu. Vztah mezi tyto třídy je podobné mezi [CTime](../../atl-mfc-shared/reference/ctime-class.md) a [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Další informace o `COleDateTime` a `COleDateTimeSpan` třídy, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ATLComTime.h  
  
##  <a name="coledatetime_relational_operators"></a>  Relační operátory COleDateTime  
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
 `date`  
 **COleDateTime** objekt, který má být porovnána.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  ATLASSERT dojde, pokud buď dva operandy je neplatný.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#13](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_2.cpp)]  
  
### <a name="example"></a>Příklad  
 Operátory **>=**, **\< =**, **>**, a **<**, bude assert, pokud `COleDateTime` je nastavena na hodnotu null.  
  
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
COleDateTime(const DBTIMESTAMP& dbts) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dateSrc`  
 Existující `COleDateTime` objekt, který má být zkopírován do nové `COleDateTime` objektu.  
  
 *varSrc*  
 Existující **VARIANT** datové struktury (pravděpodobně `COleVariant` objektu) má být převeden na hodnotu data a času ( `VT_DATE`) a zkopírovat do nové `COleDateTime` objektu.  
  
 `dtSrc`  
 Datum a čas ( **datum**) hodnota, která má být zkopírován do nové `COleDateTime` objektu.  
  
 `timeSrc`  
 A `time_t` nebo **__time64_t –** hodnota, která má být převedena na hodnotu data a času a zkopírují do nové `COleDateTime` objektu.  
  
 *systimeSrc*  
 A `SYSTEMTIME` struktura převést na hodnotu data a času a zkopírují do nové `COleDateTime` objektu.  
  
 `filetimeSrc`  
 A `FILETIME` struktura převést na hodnotu data a času a zkopírují do nové `COleDateTime` objektu. Všimněte si, že `FILETIME` používá světového koordinovaného času (UTC), takže pokud předáte místní čas ve struktuře, výsledky budou nesprávné. V tématu [časy](http://msdn.microsoft.com/library/windows/desktop/ms724290) ve Windows SDK pro další informace.  
  
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Určení hodnoty datum a čas, který se má zkopírovat do nové `COleDateTime` objektu.  
  
 `wDosDate`, `wDosTime`  
 Hodnoty data a času MS-DOS převést na hodnotu data a času a zkopírují do nové `COleDateTime` objektu.  
  
 `dbts`  
 Odkaz na [DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktura obsahující aktuální místní čas.  
  
### <a name="remarks"></a>Poznámky  
 Všechny tyto konstruktory vytvořit nový `COleDateTime` objekty inicializovat se zadanou hodnotou. V následující tabulce jsou uvedeny platné rozsahy pro každou součást datum a čas:  
  
|Součást datum a čas|Platný rozsah|  
|--------------------------|-----------------|  
|Rok|100 - 9999|  
|Měsíc|0 - 12|  
|Den|0 - 31|  
|Hodina|0 - 23|  
|Minuta|0 - 59|  
|Sekundu|0 - 59|  
  
 Všimněte si, že se liší podle skutečné horní mez pro komponentu den založené na součástech měsíci a roce. Podrobnosti najdete v tématu **SetDate** nebo `SetDateTime` členské funkce.  
  
 Toto je stručný popis jednotlivých konstruktor:  
  
- `COleDateTime(` **)** Vytvoří `COleDateTime` objekt hodnotu 0 (půlnoc, 30 1899 prosince).  
  
- `COleDateTime(` `dateSrc` **)** Vytvoří `COleDateTime` objekt z existující `COleDateTime` objektu.  
  
- `COleDateTime(` *varSrc* **)** vytvoří `COleDateTime` objektu. Pokusí se převést `VARIANT` struktura nebo [COleVariant](../../mfc/reference/colevariant-class.md) objekt, který chcete data a času ( `VT_DATE`) hodnotu. Pokud tento převod je úspěšné, převedená hodnota je zkopírovat do nové `COleDateTime` objektu. Pokud ne, je hodnota `COleDateTime` objektu je nastavena na 0 (půlnoc, 30 prosinec 1899) a její stav na neplatný.  
  
- `COleDateTime(` `dtSrc` **)** Vytvoří `COleDateTime` objektu z **datum** hodnotu.  
  
- `COleDateTime(` `timeSrc` **)** Vytvoří `COleDateTime` objektu z `time_t` hodnotu.  
  
- `COleDateTime(` *systimeSrc* **)** vytvoří `COleDateTime` objektu z `SYSTEMTIME` hodnotu.  
  
- `COleDateTime(` `filetimeSrc` **)** Vytvoří `COleDateTime` objektu z `FILETIME` hodnotu. . Všimněte si, že `FILETIME` používá světového koordinovaného času (UTC), takže pokud předáte místní čas ve struktuře, výsledky budou nesprávné. V tématu [časy](http://msdn.microsoft.com/library/windows/desktop/ms724290) ve Windows SDK pro další informace.  
  
- `COleDateTime(` `nYear``nMonth`, `nDay`, `nHour`, `nMin`, `nSec` **)** Vytvoří `COleDateTime` objektu ze zadané číselné hodnoty.  
  
- `COleDateTime(` `wDosDate``wDosTime` **)** Vytvoří `COleDateTime` objektu ze zadané hodnoty data a času MS-DOS.  
  
 Další informace o `time_t` datový typ, najdete v článku [čas](../../c-runtime-library/reference/time-time32-time64.md) fungovat v *referenční dokumentace běhové knihovny*.  
  
 Další informace najdete v tématu [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) a [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury v sadě Windows SDK.  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
> [!NOTE]
>  Pomocí konstruktoru **DBTIMESTAMP** parametr je k dispozici, pouze když OLEDB.h je součástí.  
  
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
 `dwFlags`  
 Určuje jeden z následujících příznaků národního prostředí:  
  
- `LOCALE_NOUSEROVERRIDE` Použijte nastavení systému výchozí národní prostředí místo vlastní uživatelská nastavení.  
  
- `VAR_TIMEVALUEONLY` Ignorujte část data během analýzy.  
  
- `VAR_DATEVALUEONLY` Při analýze ignorujte část času.  
  
 `lcid`  
 Určuje ID národního prostředí pro převod. Další informace o identifikátorech jazyků najdete v tématu [identifikátory jazyka](http://msdn.microsoft.com/library/windows/desktop/dd318691).  
  
 `lpszFormat`  
 Formátování řetězce podobně jako `printf` formátování řetězce. Každý formátování kódu, před sebou procento ( `%`) přihlášení, budou nahrazeny v odpovídajícím `COleDateTime` součásti. Dalšími znaky v řetězci formátování se zkopírují na vrácený řetězec beze změny. Najdete v části funkce běhové [STRFTIME –](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) Další informace. Hodnota a význam formátování kódy pro `Format` jsou:  
  
- `%H` Čas do aktuálního dne  
  
- `%M` Minut do aktuální hodiny  
  
- `%S` Sekund do aktuální minuty  
  
- `%%` Znak procenta  
  
 `nFormatID`  
 ID prostředku pro řetězec formát ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` obsahující hodnotu formátovaná data a času.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se stav tohoto `COleDateTime` objekt má hodnotu null, vrácená hodnota je prázdný řetězec. Pokud je neplatný stav, vrácený řetězec určeného řetězce prostředků `ATL_IDS_DATETIME_INVALID`.  
  
 Následuje stručný popis tři formuláře pro tuto funkci:  
  
 `Format`( `dwFlags`, `lcid`)  
 Tento formulář naformátuje hodnotu pomocí specifikace jazyka (ID národního prostředí) pro datum a čas. Použití výchozích parametrů, tento formulář tisknou datum a čas, pokud čas část je 0 (půlnoc), v takovém případě vypíše jenom datum nebo datum část je 0 (30 prosinec 1899), v takovém případě budou vytištěny právě čas. Pokud hodnota data a času je 0 (30 prosinec 1899, půlnoc), bude tento formulář s parametry výchozí tisk půlnoc.  
  
 `Format`( `lpszFormat`)  
 Tento formulář naformátuje hodnotu pomocí řetězec formátu, který obsahuje speciální formátování kódy, které jsou uvozená znakem procent (%), jako v `printf`. Formátovací řetězec je jako parametr předaný funkci. Další informace o kódech formátování najdete v tématu [strftime wcsftime –](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) v referenci běhové knihovny.  
  
 `Format`( `nFormatID`)  
 Tento formulář naformátuje hodnotu pomocí řetězec formátu, který obsahuje speciální formátování kódy, které jsou uvozená znakem procent (%), jako v `printf`. Formátovací řetězec je prostředek. ID prostředku tento řetězec je předán jako parametr. Další informace o kódech formátování najdete v tématu [strftime wcsftime –](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) v *referenční dokumentace běhové knihovny*.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#3](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_5.cpp)]  
  
##  <a name="getasdbtimestamp"></a>  COleDateTime::GetAsDBTIMESTAMP  
 Volat tuto metodu za účelem získání čas v `COleDateTime` objekt jako **DBTIMESTAMP** datové struktury.  
  
```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dbts`  
 Odkaz na [DBTimeStamp](https://msdn.microsoft.com/library/system.data.oledb.oledbtype) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Ukládá výsledný čas v odkazovaná `dbts` struktura. **DBTIMESTAMP** nebude mít struktura dat inicializovat pomocí této funkce jeho **zlomek** člen nastavit na nulu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#4](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_6.cpp)]  
  
##  <a name="getassystemtime"></a>  COleDateTime::GetAsSystemTime  
 Volat tuto metodu za účelem získání čas v `COleDateTime` objekt jako `SYSTEMTIME` datové struktury.  
  
```
bool GetAsSystemTime(SYSTEMTIME& sysTime) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *sysTime*  
 Odkaz na [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura přijímat hodnotu převedená data a času `COleDateTime` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** v případě úspěšného; **false** Pokud převod selže, nebo pokud `COleDateTime` objekt **NULL** nebo je neplatný.  
  
### <a name="remarks"></a>Poznámky  
 `GetAsSystemTime` ukládá výsledný čas v odkazovaná *sysTime* objektu. `SYSTEMTIME` Nebude mít struktura dat inicializovat pomocí této funkce jeho **wMilliseconds** člen nastavit na nulu.  
  
 V tématu [GetStatus](#getstatus) pro další informace o informace o stavu uchovávat v `COleDateTime` objektu.  
  
##  <a name="getasudate"></a>  COleDateTime::GetAsUDATE  
 Volat tuto metodu za účelem získání čas v `COleDateTime` objekt jako **AKT.rev.AUKCE** datové struktury.  
  
```
bool GetAsUDATE(UDATE& udate) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `udate`  
 Odkaz na **AKT.rev.AUKCE** struktura přijímat hodnotu převedená data a času `COleDateTime` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** v případě úspěšného; **false** Pokud převod selže, nebo pokud `COleDateTime` objekt **NULL** nebo je neplatný.  
  
### <a name="remarks"></a>Poznámky  
 A **AKT.rev.AUKCE** struktura představuje datum "rozbalené".  
  
##  <a name="getcurrenttime"></a>  COleDateTime::GetCurrentTime  
 Volání této funkce statický člen vrátit hodnotu aktuální datum a čas.  
  
```
static COleDateTime WINAPI GetCurrentTime() throw();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#5](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_7.cpp)]  
  
##  <a name="getday"></a>  COleDateTime::GetDay  
 Získá den v měsíci, které jsou reprezentována tuto hodnotu data a času.  
  
```
int GetDay() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Den v měsíci, které jsou reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat dne.  
  
### <a name="remarks"></a>Poznámky  
 Platný návratové hodnoty v rozsahu od 1 do 31.  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#6](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_8.cpp)]  
  
##  <a name="getdayofweek"></a>  COleDateTime::GetDayOfWeek  
 Získá den v měsíci, které jsou reprezentována tuto hodnotu data a času.  
  
```
int GetDayOfWeek() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Den týdnu reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat den v týdnu.  
  
### <a name="remarks"></a>Poznámky  
 Platný návratové hodnoty rozsahu od 1 do 7, kde 1 = neděle, 2 = pondělí a tak dále.  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#7](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_9.cpp)]  
  
##  <a name="getdayofyear"></a>  COleDateTime::GetDayOfYear  
 Získá den v roce reprezentována tuto hodnotu data a času.  
  
```
int GetDayOfYear() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Den v roce reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat den v roce.  
  
### <a name="remarks"></a>Poznámky  
 Platný návratové hodnoty rozsahu od 1 do 366, kde 1. ledna = 1.  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#8](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_10.cpp)]  
  
##  <a name="gethour"></a>  COleDateTime::GetHour  
 Získá hodinu reprezentována tuto hodnotu data a času.  
  
```
int GetHour() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodina reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat za hodinu.  
  
### <a name="remarks"></a>Poznámky  
 Platný návratové hodnoty v rozsahu od 0 do 23.  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#9](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_11.cpp)]  
  
##  <a name="getminute"></a>  COleDateTime::GetMinute  
 Získá minutu reprezentována tuto hodnotu data a času.  
  
```
int GetMinute() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Minutu reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat minutu.  
  
### <a name="remarks"></a>Poznámky  
 Platný návratové hodnoty v rozsahu od 0 do 59.  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetHour](#gethour).  
  
##  <a name="getmonth"></a>  COleDateTime::GetMonth  
 Získá měsíc reprezentována tuto hodnotu data a času.  
  
```
int GetMonth() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Měsíc reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat v měsíci.  
  
### <a name="remarks"></a>Poznámky  
 Platný návratové hodnoty v rozsahu od 1 do 12.  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetDay](#getday).  
  
##  <a name="getsecond"></a>  COleDateTime::GetSecond  
 Získá druhý reprezentována tuto hodnotu data a času.  
  
```
int GetSecond() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Druhý reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat druhý.  
  
### <a name="remarks"></a>Poznámky  
 Platný návratové hodnoty v rozsahu od 0 do 59.  
  
> [!NOTE]
>  `COleDateTime` Třída nepodporuje přestupného sekund.  
  
 Další informace o implementaci pro `COleDateTime`, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetHour](#gethour).  
  
##  <a name="getstatus"></a>  COleDateTime::GetStatus  
 Získá stav (platnosti) danou `COleDateTime` objektu.  
  
```
DateTimeStatus GetStatus() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí stav tohoto `COleDateTime` hodnotu. Když zavoláte **GetStatus** na `COleDateTime` objekt zkonstruován s výchozím, vrátí platný. Při volání **GetStatus** na `COleDateTime` objekt inicializován s konstruktor nastavenou na hodnotu null, **GetStatus** vrátí hodnotu null. V tématu **poznámky** Další informace.  
  
### <a name="remarks"></a>Poznámky  
 Návratová hodnota je definované **DateTimeStatus** výčtového typu, která je definována v rámci `COleDateTime` třídy.  
  
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
  
- `COleDateTime::error` Označuje, že došlo k chybě při pokusu o získání část hodnoty data a času.  
  
- **COleDateTime::valid** -označuje, že tato `COleDateTime` je objekt platný.  
  
- **COleDateTime::invalid** -označuje, že tato `COleDateTime` objektu je neplatné, který je jeho hodnota může být nesprávný.  
  
- **COleDateTime::null** -označuje, že tato `COleDateTime` objekt má hodnotu null, to znamená, že má žádná hodnota zadaná pro tento objekt. (Toto je "null" v tom smyslu, databáze "použití žádná hodnota" a C++ **NULL**.)  
  
 Stav `COleDateTime` objekt je neplatný v následujících případech:  
  
-   Pokud je jeho hodnota v rozsahu **VARIANT** nebo `COleVariant` hodnotu, kterou nelze převést na hodnotu data a času.  
  
-   Pokud je jeho hodnota v rozsahu `time_t`, `SYSTEMTIME`, nebo `FILETIME` hodnotu, kterou nelze převést na hodnotu platné datum a čas.  
  
-   Pokud je nastavena `SetDateTime` s hodnotami neplatný parametr.  
  
-   Pokud tento objekt došlo přetečení nebo podtečení během operace aritmetické přiřazení, konkrétně, `+=` nebo `-=`.  
  
-   Pokud je neplatná hodnota byl přiřazen k tomuto objektu.  
  
-   Pokud se stav tohoto objektu se explicitně nastavit na neplatné použití `SetStatus`.  
  
 Další informace o operacích, které může nastavit stav na neplatné najdete následující členské funkce:  
  
- [COleDateTime](#coledatetime)  
  
- [SetDateTime](#setdatetime)  
  
- [operátor +, -](#operator_add_-)  
  
- [Operator +=-=](#operator_add_eq_-_eq)  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#10](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_12.cpp)]  
  
##  <a name="getyear"></a>  COleDateTime::GetYear  
 Získá v roce reprezentována tuto hodnotu data a času.  
  
```
int GetYear() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V roce reprezentována hodnotu této `COleDateTime` objekt nebo `COleDateTime::error` Pokud nebylo možné získat v roce.  
  
### <a name="remarks"></a>Poznámky  
 Platné návratové hodnoty rozsahu 100 až 9999, zahrnující století.  
  
 Informace o dalších členských funkcí, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetDay](#getday).  
  
##  <a name="m_dt"></a>  COleDateTime::m_dt  
 Základní **datum** struktury pro tuto `COleDateTime` objektu.  
  
```
DATE m_dt;
```  
  
### <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Změna hodnoty v **datum** objekt ukazatele, vrátí tato funkce se změní hodnota této `COleDateTime` objektu. Nezmění stav tohoto `COleDateTime` objektu.  
  
 Další informace o provádění **datum** objektu, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="m_status"></a>  COleDateTime::m_status  
 Obsahuje stav tohoto `COleDateTime` objektu.  
  
```
DateTimeStatus m_status;
```  
  
### <a name="remarks"></a>Poznámky  
 Typ této – datový člen je Výčtový typ **DateTimeStatus**, která je definována v rámci `COleDateTime` třídy. V tématu [COleDateTime::GetStatus](#getstatus) podrobnosti.  
  
> [!CAUTION]
>  Tento člen dat je pro pokročilé programovací situace. Měli byste použít vložené funkce člen [GetStatus](#getstatus) a [SetStatus](#setstatus). V tématu `SetStatus` pro další upozornění týkající se explicitně nastavení tohoto člena data.  
  
##  <a name="operator_eq"></a>  COleDateTime::operator =  
 Kopie `COleDateTime` hodnotu.  
  
```
COleDateTime& operator=(const VARIANT& varSrc) throw();
COleDateTime& operator=(DATE dtSrc) throw();
COleDateTime& operator=(const time_t& timeSrc) throw();
COleDateTime& operator=(const __time64_t& timeSrc) throw();
COleDateTime& operator=(const SYSTEMTIME& systimeSrc) throw();
COleDateTime& operator=(const FILETIME& filetimeSrc) throw();
COleDateTime& operator=(const UDATE& udate) throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tyto operátory přetížené přiřazení zkopírujte zdrojové hodnoty data a času do této `COleDateTime` objektu. Stručný popis jednotlivých tyto přetížený způsobem operátory přiřazení:  
  
- **Operator = (** `dateSrc` **)** hodnotu a stav operand se zkopírují do této `COleDateTime` objektu.  
  
- **operátor = (** *varSrc* **)** Pokud převod [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) hodnotu (nebo [COleVariant](../../mfc/reference/colevariant-class.md) objekt) pro data a času ( `VT_DATE`) je úspěšné, převedená hodnota se zkopíruje do této `COleDateTime` nastavena na platný objekt a jeho stav. Pokud převod není úspěšné, hodnota tohoto objektu nastavená na nulovou (30 prosinec 1899, půlnoc) a její stav na neplatný.  
  
- **operátor = (** `dtSrc` **)** **datum** hodnota je zkopírována do této `COleDateTime` nastavena na platný objekt a jeho stav.  
  
- **Operator = (** `timeSrc` **)** `time_t` nebo **__time64_t –** hodnota převedena a zkopírovali do této `COleDateTime` objektu. Pokud převod úspěšný, je stav tohoto objektu nastaven platný; Jestliže úspěšné, bude nastaveno na neplatný.  
  
- **operátor = (** *systimeSrc* **)** [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) hodnota převedena a zkopírovali do této `COleDateTime` objektu. Pokud převod úspěšný, je stav tohoto objektu nastaven platný; Jestliže úspěšné, bude nastaveno na neplatný.  
  
- **Operator = (** `udate` **)** **AKT.rev.AUKCE** hodnota převedena a zkopírovali do této `COleDateTime` objektu. Pokud převod úspěšný, je stav tohoto objektu nastaven platný; Jestliže úspěšné, bude nastaveno na neplatný. A **AKT.rev.AUKCE** struktura představuje datum "rozbalené". Najdete v části funkce [VarDateFromUdate](http://msdn.microsoft.com/en-us/1c924ac5-b896-49e1-9ccf-825ac7a030c8) další podrobnosti.  
  
- **Operator = (** `filetimeSrc` **)** [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) hodnota převedena a zkopírovali do této `COleDateTime` objektu. Pokud převod úspěšný, je stav tohoto objektu nastaven platný; jinak je nastavená na neplatné. `FILETIME` používá světového koordinovaného času (UTC), takže pokud předáte čas UTC ve struktuře, výsledky budou převedeny od času UTC na místní čas a bude uložena jako variant čas. Toto chování je stejné jako Visual C++ verze 6.0 a Visual C++ .NET 2003 SP2. V tématu [časy](http://msdn.microsoft.com/library/windows/desktop/ms724290) ve Windows SDK pro další informace.  
  
 Další informace najdete v tématu [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) položku v sadě Windows SDK.  
  
 Další informace o `time_t` datový typ, najdete v článku [čas](../../c-runtime-library/reference/time-time32-time64.md) fungovat v *referenční dokumentace běhové knihovny*.  
  
 Další informace najdete v tématu [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) a [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktury v sadě Windows SDK.  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_add_-"></a>  COleDateTime::operator +, -  
 Sčítání a odečítání **ColeDateTime** hodnoty.  
  
```
COleDateTime operator+(COleDateTimeSpan dateSpan) const throw();
COleDateTime operator-(COleDateTimeSpan dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTime& date) const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 `COleDateTime` objekty představují absolutní časy. [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md) představovat relativní časy. První dva operátory umožňují sčítání a odečítání `COleDateTimeSpan` z hodnoty `COleDateTime` hodnotu. Třetí operátor umožňuje odečtena jeden `COleDateTime` hodnotu z jiné yield `COleDateTimeSpan` hodnotu.  
  
 Pokud některá z operandy null, stav výsledná `COleDateTime` hodnota je null.  
  
 Pokud výsledná `COleDateTime` hodnota spadá mimo rozsah přijatelných hodnot, který stav `COleDateTime` hodnota je neplatná.  
  
 Pokud některý z operandy je neplatný a dalších nemá hodnotu null, stav výsledná `COleDateTime` hodnota je neplatná.  
  
 **+** a **-** operátory bude assert, pokud `COleDateTime` je nastavena na hodnotu null. V tématu [COleDateTime relační operátory](#coledatetime_relational_operators) příklad.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#12](../../atl-mfc-shared/codesnippet/cpp/coledatetime-class_13.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>  COleDateTime::operator +=-=  
 Sčítání a odečítání **ColeDateTime** hodnotu z tohoto `COleDateTime` objektu.  
  
```
COleDateTime& operator+=(COleDateTimeSpan dateSpan) throw();
COleDateTime& operator-=(COleDateTimeSpan dateSpan) throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tyto operátory umožňují sčítání a odečítání `COleDateTimeSpan` hodnotu do a z tohoto `COleDateTime`. Pokud některá z operandy null, stav výsledná `COleDateTime` hodnota je null.  
  
 Pokud výsledná `COleDateTime` hodnota spadá mimo rozsah přijatelných hodnot, stav tohoto `COleDateTime` hodnota nastavená na neplatné.  
  
 Pokud některý z operandy je neplatný a dalších nemá hodnotu null, stav výsledná `COleDateTime` hodnota je neplatná.  
  
 Další informace o stavu platná, neplatný a hodnotu null. hodnoty, najdete v článku [m_status](#m_status) členské proměnné.  
  
 **+=** a **-=** operátory bude assert, pokud `COleDateTime` je nastavena na hodnotu null. V tématu [COleDateTime relační operátory](#coledatetime_relational_operators) příklad.  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="operator_date"></a>  COleDateTime::operator datum  
 Převede **ColeDateTime** hodnotu do **datum**.  
  
```
operator DATE() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor vrací **datum** objekt, jehož hodnota je zkopírována z tohoto `COleDateTime` objektu. Další informace o provádění **datum** objektu, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
 **Datum** operátor bude assert, pokud `COleDateTime` je nastavena na hodnotu null. V tématu [COleDateTime relační operátory](#coledatetime_relational_operators) příklad.  
  
##  <a name="parsedatetime"></a>  COleDateTime::ParseDateTime  
 Analyzuje řetězec k načtení hodnoty data a času.  
  
```
bool ParseDateTime(  
 LPCTSTR lpszDate,
 DWORD dwFlags = 0,
 LCID lcid = LANG_USER_DEFAULT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpszDate`  
 Ukazatel na řetězce ukončené hodnotou null, který má být analyzován. Podrobnosti najdete v tématu poznámky.  
  
 `dwFlags`  
 Určuje příznaky pro nastavení národního prostředí a analýzu. Jeden nebo více z následujících příznaků:  
  
- **LOCALE_NOUSEROVERRIDE** používá výchozí nastavení národního prostředí systému, namísto vlastní uživatelská nastavení.  
  
- **VAR_TIMEVALUEONLY** ignorovat část data během analýzy.  
  
- **VAR_DATEVALUEONLY** ignorovat části času při analýze.  
  
 `lcid`  
 Určuje ID národního prostředí pro převod.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud řetězec byl úspěšně převést na hodnotu data a času, jinak **false**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud řetězec byl úspěšně převeden na datum a čas hodnotu, hodnotu této `COleDateTime` objektu je nastaven na tuto hodnotu a její stav na platný.  
  
> [!NOTE]
>  Hodnoty roku musí ležet v rozsahu od 100 do 9999, (včetně).  
  
 `lpszDate` Jako parametr lze zadat různých formátech. Například následující řetězce obsahovat formátů přijatelné data a času:  
  
 `"25 January 1996"`  
  
 `"8:30:00"`  
  
 `"20:30:00"`  
  
 `"January 25, 1996 8:30:00"`  
  
 `"8:30:00 Jan. 25, 1996"`  
  
 `"1/25/1996 8:30:00"  // always specify the full year, even in a 'short date' format`  
  
 Všimněte si, že ID národního prostředí ovlivní také zda formát řetězce je přijatelné pro převod na hodnotu data a času.  
  
 U **VAR_DATEVALUEONLY**, hodnota nastavena na čas 0 nebo půlnoci času. U **VAR_TIMEVALUEONLY**, hodnota je nastaven na date 0, což znamená 30 prosinec 1899 datum.  
  
 Pokud řetězec nelze převést na hodnotu data a času nebo pokud došlo k přetečení číselné, stav tohoto `COleDateTime` objekt je neplatný.  
  
 Další informace o hranice a implementací `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
##  <a name="setdate"></a>  COleDateTime::SetDate  
 Nastaví datum tohoto `COleDateTime` objektu.  
  
```
int SetDate(  
 int nYear,
 int nMonth,
 int nDay) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nYear`, `nMonth`, `nDay`  
 Označuje datum součásti, které budou zkopírovány do to `COleDateTime` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula v případě hodnoty této třídy `COleDateTime` objekt byl nastaven úspěšně; jinak hodnota 1. Podle této návratovou hodnotu **DateTimeStatus** výčtového typu. Další informace najdete v tématu [SetStatus](#setstatus) – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 Datum je nastavena na zadané hodnoty. Čas je nastavený čas 0, půlnoci.  
  
 V následující tabulce najdete hranice hodnoty parametrů:  
  
|Parametr|Hranice|  
|---------------|------------|  
|`nYear`|100 - 9999|  
|`nMonth`|1 - 12|  
|`nDay`|0 - 31|  
  
 Pokud přesahuje den v měsíci, jsou převedeny na správný den do následujícího měsíce a měsíc nebo rok se zvýší odpovídajícím způsobem. Den hodnota nula znamená poslední den předchozího měsíce. Chování je stejné jako `SystemTimeToVariantTime`.  
  
 Pokud zadanou parametry hodnoty date není platný, je nastaven stav tohoto objektu **COleDateTime::invalid**. Měli byste použít [getStatus –](#getstatus) ke kontrole platnosti **datum** hodnota a nesmí předpokládat, že hodnota [m_dt](#m_dt) zůstanou beze změny.  
  
 Tady jsou některé příklady hodnot data:  
  
|`nYear`|`nMonth`|`nDay`|Hodnota|  
|-------------|--------------|------------|-----------|  
|2000|2|29|29. února 2000|  
|1776|7|4|4 1776 července|  
|1925|4|35|35 duben 1925 (neplatné datum)|  
|10000|1|1|1. ledna 10000 (neplatné datum)|  
  
 Pokud chcete nastavit datum a čas, najdete v části [COleDateTime::SetDateTime](#setdatetime).  
  
 Informace o členské funkce, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
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
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Označuje komponenty datum a čas, který se má zkopírovat do této `COleDateTime` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula v případě hodnoty této třídy `COleDateTime` objekt byl nastaven úspěšně; jinak hodnota 1. Podle této návratovou hodnotu **DateTimeStatus** výčtového typu. Další informace najdete v tématu [SetStatus](#setstatus) – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 V následující tabulce najdete hranice hodnoty parametrů:  
  
|Parametr|Hranice|  
|---------------|------------|  
|`nYear`|100 - 9999|  
|`nMonth`|1 - 12|  
|`nDay`|0 - 31|  
|`nHour`|0 - 23|  
|`nMin`|0 - 59|  
|`nSec`|0 - 59|  
  
 Pokud přesahuje den v měsíci, jsou převedeny na správný den do následujícího měsíce a měsíc nebo rok se zvýší odpovídajícím způsobem. Den hodnota nula znamená poslední den předchozího měsíce. Chování je stejné jako [SystemTimeToVariantTime](http://msdn.microsoft.com/en-us/d9d69521-9b33-4fc5-8a1c-929f216db450).  
  
 Pokud se hodnoty data nebo času zadanou parametry není platný, že a neplatná hodnota tohoto objektu je nastaven stav tohoto objektu se nezmění.  
  
 Tady jsou některé příklady hodnot času:  
  
|`nHour`|`nMin`|`nSec`|Hodnota|  
|-------------|------------|------------|-----------|  
|1|3|3|01:03:03|  
|23|45|0|23:45:00|  
|25|30|0|Neplatný|  
|9|60|0|Neplatný|  
  
 Tady jsou některé příklady hodnot data:  
  
|`nYear`|`nMonth`|`nDay`|Hodnota|  
|-------------|--------------|------------|-----------|  
|1995|4|15|15. dubna 1995|  
|1789|7|14|17. července 1789|  
|1925|2|30|Neplatný|  
|10000|1|1|Neplatný|  
  
 Pouze data, naleznete v tématu [COleDateTime::SetDate](#setdate). Pouze čas, naleznete v tématu [COleDateTime::SetTime](#settime).  
  
 Informace o členské funkce, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetStatus](#getstatus).  
  
##  <a name="setstatus"></a>  COleDateTime::SetStatus  
 Nastaví stav tohoto `COleDateTime` objektu.  
  
```
void SetStatus(DateTimeStatus status) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *Stav*  
 Nová hodnota stav pro tento `COleDateTime` objektu.  
  
### <a name="remarks"></a>Poznámky  
 *Stav* hodnota parametru je definováno **DateTimeStatus** výčtového typu, která je definována v rámci `COleDateTime` třídy. V tématu [COleDateTime::GetStatus](#getstatus) podrobnosti.  
  
> [!CAUTION]
>  Tato funkce je pro pokročilé programovací situace. Tato funkce nezmění data v tomto objektu. Použije nejčastěji nastavit stav na `null` nebo **neplatný**. Všimněte si, že operátor přiřazení ( [operátor =](#eq)) a [SetDateTime](#setdatetime) nastavit stav objektu podle hodnoty zdroje.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetStatus](#getstatus).  
  
##  <a name="settime"></a>  COleDateTime::SetTime  
 Nastaví dobu tohoto `COleDateTime` objektu.  
  
```
int SetTime(  
 int nHour,
 int nMin,
 int nSec) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nHour`, `nMin`, `nSec`  
 Označuje čas součásti, které budou zkopírují do této `COleDateTime` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nula v případě hodnoty této třídy `COleDateTime` objekt byl nastaven úspěšně; jinak hodnota 1. Podle této návratovou hodnotu **DateTimeStatus** výčtového typu. Další informace najdete v tématu [SetStatus](#setstatus) – členská funkce.  
  
### <a name="remarks"></a>Poznámky  
 Čas je nastavena na zadané hodnoty. Datum je nastaven na date 0, což znamená 30 prosinec 1899.  
  
 V následující tabulce najdete hranice hodnoty parametrů:  
  
|Parametr|Hranice|  
|---------------|------------|  
|`nHour`|0 - 23|  
|`nMin`|0 - 59|  
|`nSec`|0 - 59|  
  
 Pokud v době hodnotu zadanou pomocí parametrů není platný, stav tohoto objektu je nastavena na neplatné a hodnota tohoto objektu se nezmění.  
  
 Tady jsou některé příklady hodnot času:  
  
|`nHour`|`nMin`|`nSec`|Hodnota|  
|-------------|------------|------------|-----------|  
|1|3|3|01:03:03|  
|23|45|0|23:45:00|  
|25|30|0|Neplatný|  
|9|60|0|Neplatný|  
  
 Pokud chcete nastavit datum a čas, najdete v části [COleDateTime::SetDateTime](#setdatetime).  
  
 Informace o členské funkce, které dotaz na hodnotu této `COleDateTime` objektu, viz následující členské funkce:  
  
- [Getday –](#getday)  
  
- [GetMonth –](#getmonth)  
  
- [GetYear –](#getyear)  
  
- [GetHour](#gethour)  
  
- [GetMinute](#getminute)  
  
- [GetSecond](#getsecond)  
  
- [Metodu GetDayOfWeek](#getdayofweek)  
  
- [GetDayOfYear](#getdayofyear)  
  
 Další informace o hranice pro `COleDateTime` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [SetDate](#setdate).  
  
## <a name="see-also"></a>Viz také  
 [COleVariant – třída](../../mfc/reference/colevariant-class.md)   
 [CTime – třída](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)



