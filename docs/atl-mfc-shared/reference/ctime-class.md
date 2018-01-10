---
title: "CTime – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82f3d4bf1d0c705d7712adb092a5f6d965099a26
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ctime-class"></a>CTime – třída
Představuje absolutní data a času.  
  
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
|[CTime::Format](#format)|Převede `CTime` objekt na řetězec formátovaný – podle místního časového pásma.|  
|[CTime::FormatGmt](#formatgmt)|Převede `CTime` objekt na řetězec formátovaný – založené na UTC.|  
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Převede čas informace uložené v `CTime` objekt pro strukturu DBTIMESTAMP Win32 kompatibilní.|  
|[CTime::GetAsSystemTime](#getassystemtime)|Převede čas informace uložené v `CTime` objekt, který chcete Win32 kompatibilní [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura.|  
|[CTime::GetCurrentTime](#getcurrenttime)|Vytvoří `CTime` objekt, který představuje aktuální čas (funkce statický člen).|  
|[CTime::GetDay](#getday)|Vrátí den představují pomocí `CTime` objektu.|  
|[CTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu reprezentována `CTime` objektu.|  
|[CTime::GetGmtTm](#getgmttm)|Dojde-li `CTime` objektu do komponenty – založené na UTC.|  
|[CTime::GetHour](#gethour)|Vrátí hodinu v reprezentována `CTime` objektu.|  
|[CTime::GetLocalTm](#getlocaltm)|Dojde-li `CTime` objektu do komponenty – podle místního časového pásma.|  
|[CTime::GetMinute](#getminute)|Vrátí minutu reprezentována `CTime` objektu.|  
|[CTime::GetMonth](#getmonth)|Vrátí měsíc reprezentována `CTime` objektu.|  
|[CTime::GetSecond](#getsecond)|Vrátí sekundu reprezentována `CTime` objektu.|  
|[CTime::GetTime](#gettime)|Vrátí **__time64_t –** hodnota danou `CTime` objektu.|  
|[CTime::GetYear](#getyear)|Vrátí rok reprezentována `CTime` objektu.|  
|[CTime::Serialize64](#serialize64)|Serializuje data do nebo z archivu.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor + -](#operator_add_-)|Tyto operátory sčítání a odečítání `CTimeSpan` a `CTime` objekty.|  
|[Operator +=-=](#operator_add_eq_-_eq)|Tyto operátory sčítání a odečítání `CTimeSpan` objekt do a z tohoto `CTime` objektu.|  
|[operátor =](#operator_eq)|Operátor přiřazení.|  
|[Operator ==, < atd.](#ctime_comparison_operators)|Operátory porovnání.|  
  
## <a name="remarks"></a>Poznámky  
 `CTime`nemá základní třídu.  
  
 `CTime`hodnoty jsou založené na koordinovaný světový čas (UTC), což je totéž jako koordinovaného světového času (greenwichský střední čas, GMT). V tématu [Správa času](../../c-runtime-library/time-management.md) informace o tom, jak je určen časové pásmo.  
  
 Při vytváření `CTime` objektu, nastavte `nDST` parametr na hodnotu 0, že je v platnosti (běžný čas), nebo na hodnotu větší než 0 označíte, že letní čas je v platnosti, nebo na hodnotu menší než nula tak, aby měl restart počíta C běhové knihovny kódu e jestli (běžný čas) nebo letní čas je v platnosti. `tm_isdst`je povinné pole. Pokud není nastavená, jeho hodnota může být definovaný a návratovou hodnotou z [mktime –](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) předpovědět. Pokud `timeptr` body pro strukturu tm vrácené z předchozího volání [asctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s –](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), nebo [localtime_s –](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), `tm_isdst` obsahuje pole správnou hodnotu.  
  
 Třídu doprovodné [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), představuje časovém intervalu.  
  
 `CTime` a `CTimeSpan` třídy nejsou navrženy pro odvození. Protože nejsou k dispozici žádné virtuální funkce velikost `CTime` a `CTimeSpan` objekty je přesně 8 bajtů. Většina členské funkce jsou vložené.  
  
> [!NOTE]
>  Datum horní limit je 12, 31/3000. Limit je 1/1/1970 12:00:00 AM GMT.  
  
 Další informace o používání `CTime`, najdete v článcích [datum a čas](../../atl-mfc-shared/date-and-time.md), a [Správa času](../../c-runtime-library/time-management.md) v referenci běhové knihovny.  
  
> [!NOTE]
>  `CTime` Struktura změněn z MFC 7.1 na MFC 8.0. Pokud jste serializaci `CTime` struktura pomocí `operator <<` pod MFC 8.0 nebo novější verze, bude výsledný soubor nebude možné číst ve starších verzích MFC.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atltime.h  
  
##  <a name="ctime_comparison_operators"></a>CTime – relační operátory  
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
 `time`  
 `CTime` Objekt, který má být porovnána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tyto operátory porovnání absolutní dvakrát a vrácení **true** Pokud je podmínka vyhodnocena jako true; jinak hodnota **false**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]  
  
##  <a name="ctime"></a>CTime::CTime  
 Vytvoří nový `CTime` objekt inicializovat pomocí zadané doby.  
  
```  
CTime() throw(); 
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts,int nDST = -1) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `timeSrc`  
 Označuje `CTime` objekt, který již existuje.  
  
 `time`  
 A **__time64_t –** čas hodnotu, která je počet sekund, po 1. ledna 1970 UTC. Všimněte si, že to bude upravena na místní čas. Například, pokud jsou v Brně a vytvořte `CTime` objekt předáním parametr 0, [CTime::GetMonth](#getmonth) vrátí 12.  

  
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Označuje hodnoty data a času, který se má zkopírovat do nové `CTime` objektu.  
  
 `nDST`  
 Určuje, zda letní čas je v platnosti. Může mít jednu ze tří hodnot:  
  
- `nDST`Sada 0Standard čas je v platnosti.  
  
- `nDST`Nastavte na hodnotu větší než 0Daylight čas je v platnosti.  
  
- `nDST`Nastavte na hodnotu menší než výchozí 0The. Automaticky vypočítá, zda (běžný čas) nebo letní čas je v platnosti.  
  
 `wDosDate`, `wDosTime`  
 Hodnoty data a času MS-DOS převést na hodnotu data a času a zkopírují do nové `CTime` objektu.  
  
 `st`  
 A [SYSTEMTIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d6609fff-1931-4818-8a26-f042630af0b0/locales/en-us) struktura převést na hodnotu data a času a zkopírují do nové `CTime` objektu.  
  
 `ft`  
 A [FILETIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/979ce746-dc17-4147-89f8-41d05c5fcc5f/locales/en-us) struktura převést na hodnotu data a času a zkopírují do nové `CTime` objektu.  
  
 dbts  
 Odkaz na DBTIMESTAMP struktura obsahující aktuální místní čas.  
  
### <a name="remarks"></a>Poznámky  
 Každý konstruktor je popsán dále:  
  
- **CTime();**  Vytvoří Neinicializovaný `CTime` objektu. Tento konstruktor vám umožňuje definovat `CTime` objektu pole. Měli byste inicializovat takovými poli s platnou časy před použitím.  
  
- **CTime – (const CTime &);**  Vytvoří `CTime` objekt z jiné `CTime` hodnotu.  
  
- **CTime – __time64_t (–);**  Vytvoří `CTime` objektu z **__time64_t –** typu. Tento konstruktor očekává čas UTC a převede výsledek na místní čas před ukládání výsledek.  
  
- **CTime – (int, int,...);**  Vytvoří `CTime` objektu ze součásti místní čas s jednotlivé komponenty omezené na následující oblasti:  
  
    |Součást|Rozsah|  
    |---------------|-----------|  
    |`nYear`|1970-3000|  
    |`nMonth`|1-12|  
    |`nDay`|1-31|  
    |`nHour`|0-23|  
    |`nMin`|0-59|  
    |`nSec`|0-59|  
  
     Tento konstruktor vytvoří odpovídající převod na čas UTC. Ladicí verze knihovny Microsoft Foundation Class vyhodnotí, pokud jeden nebo více součástí čas je mimo rozsah. Musíte ověřit argumenty před voláním. Tento konstruktor očekává místní čas.  
  
- **CTime – (WORD, WORD);**  Vytvoří `CTime` objektu ze zadané hodnoty data a času MS-DOS. Tento konstruktor očekává místní čas.  
  
- **CTime – (const SYSTEMTIME &);**  Vytvoří `CTime` objektu z `SYSTEMTIME` struktury. Tento konstruktor očekává místní čas.  
  
- **CTime – (const FILETIME &);**  Vytvoří `CTime` objektu z `FILETIME` struktury. Pravděpodobně nebudete používat `CTime FILETIME` inicializace přímo. Pokud používáte `CFile` objekt, který chcete upravit soubor `CFile::GetStatus` načte časové razítko souboru pro vás `CTime` objekt inicializován s `FILETIME` struktury. Tento konstruktor předpokládá čas ve formátu UTC a automaticky převede hodnotu na místní čas před ukládání výsledek.  
  
    > [!NOTE]
    >  Pomocí konstruktoru **DBTIMESTAMP** parametr je k dispozici, pouze když OLEDB.h je součástí.  
  
 Další informace najdete v tématu [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) a [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) struktura ve Windows SDK. Viz také [MS-DOS datum a čas](http://msdn.microsoft.com/library/windows/desktop/ms724503) položku v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]  
  
##  <a name="format"></a>CTime::Format  
 Volání této funkce člen vytvořit formátovaný reprezentace hodnoty data a času.  
  
```  
CString Format(LPCTSTR pszFormat) const; 
CString Format(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Formátování řetězce podobně jako `printf` formátování řetězce. Formátování kódy, před sebou procento ( `%`) přihlásit, se nahrazují odpovídající `CTime` součásti. Dalšími znaky v řetězci formátování se zkopírují na vrácený řetězec beze změny. Najdete v části funkce běhové [STRFTIME –](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) seznam formátování kódy.  
  
 `nFormatID`  
 ID řetězec, který identifikuje tento formát.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující formátovaný čas.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se stav tohoto `CTime` objekt má hodnotu null, vrácená hodnota je prázdný řetězec.  
  
 Tato metoda vyvolá výjimku, pokud hodnota data a času k formátování není v rozsahu od půlnoci 1. ledna 1970 až 31. prosince 3000 světového koordinovaného času (UTC).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]  
  
##  <a name="formatgmt"></a>CTime::FormatGmt  
 Generuje formátovaný řetězec, který odpovídá tomuto `CTime` objektu.  
  
```  
CString FormatGmt(LPCTSTR pszFormat) const; 
CString FormatGmt(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Určuje formátování řetězce, jako `printf` formátování řetězce. Najdete v části funkce běhové [STRFTIME –](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) podrobnosti.  
  
 `nFormatID`  
 ID řetězec, který identifikuje tento formát.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující formátovaný čas.  
  
### <a name="remarks"></a>Poznámky  
 Hodnoty time není převést a proto odráží UTC.  
  
 Tato metoda vyvolá výjimku, pokud hodnota data a času k formátování není v rozsahu od půlnoci 1. ledna 1970 až 31. prosince 3000 světového koordinovaného času (UTC).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CTime::Format](#format).  
  
##  <a name="getasdbtimestamp"></a>CTime::GetAsDBTIMESTAMP  
 Volání této funkce člen převést čas informace uložené v `CTime` objekt pro strukturu DBTIMESTAMP Win32 kompatibilní.  
  
```  
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `dbts`  
 Odkaz na DBTIMESTAMP struktura obsahující aktuální místní čas.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Ukládá výsledný čas v odkazovaná `dbts` struktura. **DBTIMESTAMP** nebude mít struktura dat inicializovat pomocí této funkce jeho **zlomek** člen nastavit na nulu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]  
  
##  <a name="getassystemtime"></a>CTime::GetAsSystemTime  
 Volání této funkce člen převést čas informace uložené v `CTime` objekt, který chcete Win32 kompatibilní [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura.  
  
```  
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *timeDest*  
 Odkaz na [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která bude obsahovat hodnota převedená data a času `CTime` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je úspěšné; jinak hodnota false.  
  
### <a name="remarks"></a>Poznámky  
 `GetAsSystemTime`ukládá výsledný čas v odkazovaná *timeDest* struktury. `SYSTEMTIME` Nebude mít struktura dat inicializovat pomocí této funkce jeho **wMilliseconds** člen nastavit na nulu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]  
  
##  <a name="getcurrenttime"></a>CTime::GetCurrentTime  
 Vrátí `CTime` objekt, který představuje aktuální čas.  
  
```  
static CTime WINAPI GetCurrentTime() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrátí aktuální systémový datum a čas v koordinovaný světový čas (UTC).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]  
  
##  <a name="getday"></a>CTime::GetDay  
 Vrátí den představují pomocí `CTime` objektu.  
  
```  
int GetDay() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí den v měsíci, podle místního času v rozsahu od 1 do 31.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá `GetLocalTm`, který používá k interní, staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti se přepíše kvůli volání do jiných `CTime` členské funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]  
  
##  <a name="getdayofweek"></a>CTime::GetDayOfWeek  
 Vrátí den v týdnu reprezentována `CTime` objektu.  
  
```  
int GetDayOfWeek() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí den v týdnu podle místního času; 1 = neděle, 2 = pondělí, 7 = sobota.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti se přepíše kvůli volání do jiných `CTime` členské funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]  
  
##  <a name="getgmttm"></a>CTime::GetGmtTm  
 Získá **struktura tm** obsahující rozložením času obsažené v tomto `CTime` objektu.  
  
```  
struct tm* GetGmtTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `ptm`  
 Body do vyrovnávací paměti, která bude přijímat data čas. Pokud je tento ukazatel **NULL**, je vyvolána výjimka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vyplněné **struktura tm** definovaným v souboru zahrnout čas. H. V tématu [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) struktura rozložení.  
  
### <a name="remarks"></a>Poznámky  
 `GetGmtTm`Vrátí UTC.  
  
 `ptm`nemůže být `NULL`. Pokud chcete obnovit původní chování, ve kterém `ptm` může být `NULL` k označení, že má být použita k interní, staticky přidělené vyrovnávací paměti, pak nedefinované `_SECURE_ATL`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]  
  
##  <a name="gethour"></a>CTime::GetHour  
 Vrátí hodinu v reprezentována `CTime` objektu.  
  
```  
int GetHour() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodinu, v závislosti na místní čas v rozsahu 0 až 23.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti se přepíše kvůli volání do jiných `CTime` členské funkce.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]  
  
##  <a name="getlocaltm"></a>CTime::GetLocalTm  
 Získá **struktura tm** obsahující rozložením času obsažené v tomto `CTime` objektu.  
  
```  
struct tm* GetLocalTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `ptm`  
 Body do vyrovnávací paměti, která bude přijímat data čas. Pokud je tento ukazatel **NULL**, je vyvolána výjimka.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vyplněné **struktura tm** definovaným v souboru zahrnout čas. H. V tématu [gmtime – _gmtime32 –, _gmtime64 –](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) struktura rozložení.  
  
### <a name="remarks"></a>Poznámky  
 `GetLocalTm`Vrátí místní čas.  
  
 `ptm`nemůže být `NULL`. Pokud chcete obnovit původní chování, ve kterém `ptm` může být `NULL` k označení, že má být použita k interní, staticky přidělené vyrovnávací paměti, pak nedefinované `_SECURE_ATL`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]  
  
##  <a name="getminute"></a>CTime::GetMinute  
 Vrátí minutu reprezentována `CTime` objektu.  
  
```  
int GetMinute() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí minutu, podle místního času v rozsahu 0 až 59.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti se přepíše kvůli volání do jiných `CTime` členské funkce.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetHour](#gethour).  
  
##  <a name="getmonth"></a>CTime::GetMonth  
 Vrátí měsíc reprezentována `CTime` objektu.  
  
```  
int GetMonth() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí měsíc, podle místního času v rozsahu od 1 do 12 (1 = leden).  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti se přepíše kvůli volání do jiných `CTime` členské funkce.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetDay](#getday).  
  
##  <a name="getsecond"></a>CTime::GetSecond  
 Vrátí sekundu reprezentována `CTime` objektu.  
  
```  
int GetSecond() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí sekundu, podle místního času v rozsahu 0 až 59.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti se přepíše kvůli volání do jiných `CTime` členské funkce.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetHour](#gethour).  
  
##  <a name="gettime"></a>CTime::GetTime  
 Vrátí **__time64_t –** hodnota danou `CTime` objektu.  
  
```  
__time64_t GetTime() const throw(); 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **GetTime –** vrátí počet sekund mezi aktuální `CTime` objekt a 1. ledna 1970.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]  
  
##  <a name="getyear"></a>CTime::GetYear  
 Vrátí rok reprezentována `CTime` objektu.  
  
```  
int GetYear();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí rok, podle místního času v rozsahu leden 1,1970 pro 18 leden 2038 (včetně).  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce volá `GetLocalTm`, který používá interní staticky přidělené vyrovnávací paměti. Data v této vyrovnávací paměti se přepíše kvůli volání do jiných `CTime` členské funkce.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetDay](#getday).  
  
##  <a name="operator_eq"></a>CTime::operator =  
 Operátor přiřazení.  
  
```  
CTime& operator=(__time64_t time) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `time`  
 Hodnota nové datum a čas.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizovaný `CTime` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tento operátor přetížené přiřazení zkopíruje do této době zdrojového `CTime` objektu. Interní čas úložiště v `CTime` objektu je nezávislý na časové pásmo. Při přiřazení není nutné převodu časového pásma.  
  
##  <a name="operator_add_-"></a>CTime::operator +, -  
 Tyto operátory sčítání a odečítání `CTimeSpan` a `CTime` objekty.  
  
```  
CTime operator+(CTimeSpan timeSpan) const throw(); 
CTime operator-(CTimeSpan timeSpan) const throw(); 
CTimeSpan operator-(CTime time) const throw(); 
```  
  
### <a name="parameters"></a>Parametry  
 *časový interval*  
 `CTimeSpan` Objekt, který má být přidán nebo odečten.  
  
 `time`  
 `CTime` Objekt, který má být odečtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CTime` nebo `CTimeSpan` objekt reprezentující výsledek operace.  
  
### <a name="remarks"></a>Poznámky  
 `CTime`objekty představují absolutním čase `CTimeSpan` objekty představují relativní čas. První dva operátory umožňují sčítání a odečítání `CTimeSpan` objekty do a z `CTime` objekty. Třetí operátor umožňuje odečtena jeden `CTime` objekt z jiné yield `CTimeSpan` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>CTime::operator +=-=  
 Tyto operátory sčítání a odečítání `CTimeSpan` objekt do a z tohoto `CTime` objektu.  
  
```  
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `span`  
 `CTimeSpan` Objekt, který má být přidán nebo odečten.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizovaný `CTime` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tyto operátory umožňují sčítání a odečítání `CTimeSpan` objekt do a z tohoto `CTime` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]  
  
##  <a name="serialize64"></a>CTime::Serialize64  
  
> [!NOTE]
>  Tato metoda je k dispozici v projektech MFC pouze.  
  
 Serializuje data přidružená k členské proměnné do nebo z archivu.  
  
```  
CArchive& Serialize64(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 `CArchive` Objekt, který chcete aktualizovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktualizovaný `CArchive` objektu.  
  
## <a name="see-also"></a>Viz také  
 [asctime_s –, _wasctime_s –](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [_ftime_s – _ftime32_s –, _ftime64_s –](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
 [gmtime_s – _gmtime32_s –, _gmtime64_s –](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s – _localtime32_s –, _localtime64_s –](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [STRFTIME –, wcsftime –, _strftime_l –, _wcsftime_l –](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [čas, _time32 –, _time64 –](../../c-runtime-library/reference/time-time32-time64.md)   
 [CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


