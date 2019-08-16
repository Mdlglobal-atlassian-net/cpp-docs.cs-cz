---
title: CTime – – třída
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
ms.openlocfilehash: daf2a0d884a6b7a74b5edde2ed7db3b6aeea368d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491578"
---
# <a name="ctime-class"></a>CTime – – třída

Představuje absolutní datum a čas.

## <a name="syntax"></a>Syntaxe

```
class CTime
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CTime –:: CTime –](#ctime)|Sestaví `CTime` objekty různými způsoby.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CTime –:: Format](#format)|`CTime` Převede objekt na formátovaný řetězec, který je založen na místním časovém pásmu.|
|[CTime::FormatGmt](#formatgmt)|`CTime` Převede objekt na formátovaný řetězec založený na času UTC.|
|[CTime –:: GetAsDBTIMESTAMP](#getasdbtimestamp)|Převede informace o čase uložené v `CTime` objektu do struktury DBTIMESTAMP kompatibilní s Win32.|
|[CTime –:: GetAsSystemTime](#getassystemtime)|Převede informace o čase uložené v `CTime` objektu do struktury [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) kompatibilní s Win32.|
|[CTime –:: GetCurrentTime](#getcurrenttime)|`CTime` Vytvoří objekt, který představuje aktuální čas (statickou členskou funkci).|
|[CTime –:: getDay –](#getday)|Vrátí den reprezentovaný `CTime` objektem.|
|[CTime::GetDayOfWeek](#getdayofweek)|Vrátí den v týdnu reprezentovaný `CTime` objektem.|
|[CTime::GetGmtTm](#getgmttm)|Rozdělí objekt na `CTime` komponenty, a to na základě standardu UTC.|
|[CTime –:: GetHour](#gethour)|Vrátí hodinu reprezentovanou `CTime` objektem.|
|[CTime –:: GetLocalTm](#getlocaltm)|Rozdělí objekt na `CTime` komponenty, a to na základě místního časového pásma.|
|[CTime –:: GetMinute](#getminute)|Vrátí minutu reprezentovanou `CTime` objektem.|
|[CTime –:: GetMonth](#getmonth)|Vrátí měsíc reprezentovaný `CTime` objektem.|
|[CTime::GetSecond](#getsecond)|Vrátí druhý reprezentovaný `CTime` objektem.|
|[CTime –:: GetTime](#gettime)|Vrátí hodnotu **__time64_t** pro daný `CTime` objekt.|
|[CTime –:: GetYear](#getyear)|Vrátí rok reprezentovaný `CTime` objektem.|
|[CTime –:: Serialize64](#serialize64)|Serializace dat do archivu nebo z něj.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor + –](#operator_add_-)|Tyto operátory přidávají a `CTimeSpan` odčítání a `CTime` objekty.|
|[operator + =,-=](#operator_add_eq_-_eq)|Tyto operátory přidávají a odčítání `CTimeSpan` objekt do a z tohoto `CTime` objektu.|
|[operátor =](#operator_eq)|Operátor přiřazení|
|[operator = =, < atd.](#ctime_comparison_operators)|Operátory porovnání.|

## <a name="remarks"></a>Poznámky

`CTime`nemá základní třídu.

`CTime`hodnoty jsou založené na koordinovaném světový čas (UTC), který je ekvivalentem koordinovaného světového času (střední čas, GMT). Informace o tom, jak se určuje časové pásmo, najdete v tématu [Správa času](../../c-runtime-library/time-management.md) .

Při vytváření `CTime` objektu `nDST` nastavte parametr na hodnotu 0, aby označoval, že standardní čas je platný, nebo na hodnotu větší než 0, která označuje, že je letní čas v platnosti, nebo na hodnotu menší než nula, která má vypočítat kód knihovny runtime jazyka C. e, zda je v platnosti standardní čas nebo letní čas. `tm_isdst`je povinné pole. Pokud není nastavena, jeho hodnota není definována a návratová hodnota z [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) je nepředvídatelné. Pokud `timeptr` odkazuje na strukturu TM vrácenou předchozím voláním [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [_gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)nebo [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), `tm_isdst` pole obsahuje správnou hodnotu.

Doprovodná třída [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)představuje časový interval.

Třídy `CTime` a`CTimeSpan` nejsou navrženy pro odvození. Vzhledem k tomu, že neexistují žádné virtuální funkce `CTime` , `CTimeSpan` velikost objektů a je přesně 8 bajtů. Většina členských funkcí je vložená.

> [!NOTE]
>  Horní limit data je 12/31/3000. Dolní limit je 1/1/1970 12:00:00 GMT.

Další informace o použití `CTime`naleznete v článcích [data a čas](../../atl-mfc-shared/date-and-time.md)a [Správa času](../../c-runtime-library/time-management.md) v tématu reference ke knihovně run-time.

> [!NOTE]
>  Struktura `CTime` se změnila z knihovny MFC 7,1 na knihovnu MFC 8,0. Pokud serializaci `CTime` struktury pomocí **operátoru < <** v rámci knihovny MFC 8,0 nebo novější verze, výsledný soubor nebude čitelný ve starších verzích knihovny MFC.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime. h

##  <a name="ctime_comparison_operators"></a>CTime – operátory porovnání

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
`CTime` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Tyto operátory porovnávají dvě absolutní časy a vrátí hodnotu TRUE, pokud je podmínka pravdivá. v opačném případě FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]

##  <a name="ctime"></a>CTime –:: CTime –

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
`CTime` Označuje objekt, který již existuje.

*čas*<br/>
Hodnota `__time64_t` času, což je počet sekund od 1. ledna 1970 UTC. Všimněte si, že tato akce bude upravena na místní čas. Například pokud jste v New Yorku a vytvoříte `CTime` objekt předáním parametru 0, [CTime –:: GetMonth](#getmonth) vrátí 12.

*nYear*, *nMonth*, *nden*, *nhodina*, *nminimum*, *NSEC*<br/>
Označuje hodnoty data a času, které mají být zkopírovány do `CTime` nového objektu.

*nDST*<br/>
Označuje, zda je aktivní letní čas. Může mít jednu ze tří hodnot:

- *ndst* nastavené na 0Standard čas je v platnosti.

- *ndst* nastaveno na hodnotu větší, než je čas úspory 0Daylight.

- *ndst* nastaveno na hodnotu nižší než 0The výchozí. Automaticky počítá, zda platí standardní čas nebo letní čas.

*wDosDate*, *wDosTime*<br/>
Hodnoty data a času systému MS-DOS mají být převedeny na hodnotu data a času a zkopírovány do nového `CTime` objektu.

*st*<br/>
Struktura [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , která má být převedena na hodnotu data a času a zkopírována do `CTime` nového objektu.

*leva*<br/>
Struktura [](/windows/win32/api/minwinbase/ns-minwinbase-filetime) data a času, která má být převedena na hodnotu data a času a zkopírována `CTime` do nového objektu.

*dbts*<br/>
Odkaz na strukturu DBTIMESTAMP obsahující aktuální místní čas.

### <a name="remarks"></a>Poznámky

Jednotlivé konstruktory jsou popsány níže:

- `CTime();`Vytvoří Neinicializovaný `CTime` objekt. Tento konstruktor umožňuje definovat `CTime` pole objektů. Tato pole byste měli před použitím inicializovat pomocí platných časů.

- `CTime( const CTime& );`Vytvoří objekt z jiné `CTime`hodnoty. `CTime`

- `CTime( __time64_t );`Vytvoří objekt z __time64_t typu. `CTime` Tento konstruktor očekává čas UTC a převede výsledek na místní čas před uložením výsledku.

- `CTime( int, int, ...);`Sestaví `CTime` objekt z místních časových komponent s každou komponentou omezený na následující rozsahy:

   |Součást|Rozsah|
   |---------------|-----------|
   |*nYear*|1970-3000|
   |*nMonth*|1-12|
   |*nDay*|1-31|
   |*nHour*|0-23|
   |*nMin*|0-59|
   |*nSec*|0-59|

   Tento konstruktor provede odpovídající převod na čas UTC. Ladicí verze knihovna Microsoft Foundation Class vyhodnotí, pokud jedna nebo více komponent jsou mimo rozsah. Před voláním je nutné ověřit argumenty. Tento konstruktor očekává místní čas.

- `CTime( WORD, WORD );``CTime` Vytvoří objekt z určených hodnot data a času systému MS-DOS. Tento konstruktor očekává místní čas.

- `CTime( const SYSTEMTIME& );``CTime` Vytvoří objekt`SYSTEMTIME` ze struktury. Tento konstruktor očekává místní čas.

- `CTime( const FILETIME& );``CTime` Vytvoří objekt`FILETIME` ze struktury. Pravděpodobně nebudete používat `CTime FILETIME` inicializaci přímo. Použijete `CFile` -li objekt k manipulaci se souborem, `CFile::GetStatus` získá časové `CTime` razítko souboru pro vás objektem inicializovaným se `FILETIME` strukturou. Tento konstruktor předpokládá čas založený na UTC a automaticky převede hodnotu na místní čas před uložením výsledku.

   > [!NOTE]
   > Konstruktor using je `DBTIMESTAMP` k dispozici pouze v případě, že je použit OLEDB. h.

Další informace najdete v tématu struktura [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) a [doba běhu](/windows/win32/api/minwinbase/ns-minwinbase-filetime) v Windows SDK. V Windows SDK se také zobrazí položka [Datum a čas systému MS-DOS](/windows/win32/SysInfo/ms-dos-date-and-time) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]

##  <a name="format"></a>CTime –:: Format

Zavolejte tuto členskou funkci pro vytvoření formátované reprezentace hodnoty data a času.

```
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Řetězec formátování podobný `printf` řetězci formátování. Formátovací kódy, před kterými je znak procenta (`%`), jsou nahrazeny odpovídající `CTime` komponentou. Jiné znaky v řetězci formátování jsou zkopírovány beze změny do vráceného řetězce. Seznam kódů formátování najdete v [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) běhové funkce.

*nFormatID*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující formátovaný čas.

### <a name="remarks"></a>Poznámky

Pokud je stav tohoto `CTime` objektu null, vrácená hodnota je prázdný řetězec.

Tato metoda vyvolá výjimku, pokud hodnota data a času k formátování není v rozsahu od půlnoci, od 1. ledna 1970 do 31. prosince, 3000 Universal koordinovaný čas (UTC).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]

##  <a name="formatgmt"></a>CTime –:: FormatGmt

Generuje formátovaný řetězec, který odpovídá tomuto `CTime` objektu.

```
CString FormatGmt(LPCTSTR pszFormat) const;
CString FormatGmt(UINT nFormatID) const;
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Určuje řetězec formátování podobný `printf` řetězci formátování. Podrobnosti najdete v tématu [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) běhové funkce.

*nFormatID*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

[CString](../../atl-mfc-shared/reference/cstringt-class.md) obsahující formátovaný čas.

### <a name="remarks"></a>Poznámky

Hodnota času není převedena, takže odráží čas UTC.

Tato metoda vyvolá výjimku, pokud hodnota data a času k formátování není v rozsahu od půlnoci, od 1. ledna 1970 do 31. prosince, 3000 Universal koordinovaný čas (UTC).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CTime –:: Format](#format).

##  <a name="getasdbtimestamp"></a>CTime –:: GetAsDBTIMESTAMP

Zavolejte tuto členskou funkci pro převod informací o čase uložených v `CTime` objektu do struktury DBTIMESTAMP kompatibilní s Win32.

```
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```

### <a name="parameters"></a>Parametry

*dbts*<br/>
Odkaz na strukturu DBTIMESTAMP obsahující aktuální místní čas.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Ukládá výsledný čas v odkazované *dbts* struktuře. Datová struktura inicializovaná touto funkcí bude `fraction` mít člena nastavenou na nulu. `DBTIMESTAMP`

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]

##  <a name="getassystemtime"></a>CTime –:: GetAsSystemTime

Zavolejte tuto členskou funkci pro převod informací o čase uložených v `CTime` objektu do struktury [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) kompatibilní s Win32.

```
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```

### <a name="parameters"></a>Parametry

*timeDest*<br/>
Odkaz na strukturu [SYSTEMTIME –](/windows/win32/api/minwinbase/ns-minwinbase-systemtime) , která bude obsahovat převedenou hodnotu `CTime` data a času objektu.

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

`GetAsSystemTime`Ukládá výsledný čas do odkazované *časované* struktury. Datová struktura inicializovaná touto funkcí bude `wMilliseconds` mít člena nastavenou na nulu. `SYSTEMTIME`

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]

##  <a name="getcurrenttime"></a>CTime –:: GetCurrentTime

`CTime` Vrátí objekt, který představuje aktuální čas.

```
static CTime WINAPI GetCurrentTime() throw();
```

### <a name="remarks"></a>Poznámky

Vrátí aktuální systémové datum a čas ve standardu UTC (Coordinated Universal Time).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]

##  <a name="getday"></a>CTime –:: getDay –

Vrátí den reprezentovaný `CTime` objektem.

```
int GetDay() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí den v měsíci na základě místního času v rozsahu od 1 do 31.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, která používá interní staticky přidělenou vyrovnávací paměť. Data v této vyrovnávací paměti jsou přepsána z důvodu volání dalších `CTime` členských funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]

##  <a name="getdayofweek"></a>CTime –:: metodu GetDayOfWeek

Vrátí den v týdnu reprezentovaný `CTime` objektem.

```
int GetDayOfWeek() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí den v týdnu v závislosti na místním čase; 1 = neděle, 2 = pondělí, až 7 = sobota.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, která používá interní staticky přidělenou vyrovnávací paměť. Data v této vyrovnávací paměti jsou přepsána z důvodu volání dalších `CTime` členských funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]

##  <a name="getgmttm"></a>CTime –:: GetGmtTm

Získá **strukturu TM** obsahující dekompozici času obsaženého v tomto `CTime` objektu.

```
struct tm* GetGmtTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*<br/>
Odkazuje na vyrovnávací paměť, která bude přijímat data času. Pokud je tento ukazatel NULL, je vyvolána výjimka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyplněnou **strukturu TM** , jak je definováno v poli čas zahrnutí souboru. Y. Rozložení struktury najdete v tématu [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) .

### <a name="remarks"></a>Poznámky

`GetGmtTm`Vrátí hodnotu UTC.

*PTM* nemůže mít hodnotu null. Pokud se chcete vrátit k původnímu chování, ve kterém by *PTM* mohl mít hodnotu null, aby označovala, že by měla být použita interní, staticky přidělená vyrovnávací paměť, a pak zrušit definici _SECURE_ATL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]

##  <a name="gethour"></a>CTime –:: GetHour

Vrátí hodinu reprezentovanou `CTime` objektem.

```
int GetHour() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodinu na základě místního času v rozsahu 0 až 23.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, která používá interní staticky přidělenou vyrovnávací paměť. Data v této vyrovnávací paměti jsou přepsána z důvodu volání dalších `CTime` členských funkcí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]

##  <a name="getlocaltm"></a>CTime –:: GetLocalTm

Získá **strukturu TM** obsahující dekompozici času obsaženého v tomto `CTime` objektu.

```
struct tm* GetLocalTm(struct tm* ptm) const;
```

### <a name="parameters"></a>Parametry

*ptm*<br/>
Odkazuje na vyrovnávací paměť, která bude přijímat data času. Pokud je tento ukazatel NULL, je vyvolána výjimka.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyplněnou **strukturu TM** , jak je definováno v poli čas zahrnutí souboru. Y. Rozložení struktury najdete v tématu [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) .

### <a name="remarks"></a>Poznámky

`GetLocalTm`Vrátí místní čas.

*PTM* nemůže mít hodnotu null. Pokud se chcete vrátit k původnímu chování, ve kterém by *PTM* mohl mít hodnotu null, aby označovala, že by měla být použita interní, staticky přidělená vyrovnávací paměť, a pak zrušit definici _SECURE_ATL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]

##  <a name="getminute"></a>CTime –:: GetMinute

Vrátí minutu reprezentovanou `CTime` objektem.

```
int GetMinute() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí minutu na základě místního času v rozsahu 0 až 59.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, která používá interní staticky přidělenou vyrovnávací paměť. Data v této vyrovnávací paměti jsou přepsána z důvodu volání dalších `CTime` členských funkcí.

### <a name="example"></a>Příklad

Podívejte se na příklad [](#gethour)pro GetHour.

##  <a name="getmonth"></a>CTime –:: GetMonth

Vrátí měsíc reprezentovaný `CTime` objektem.

```
int GetMonth() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí měsíc na základě místního času v rozsahu od 1 do 12 (1 = leden).

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, která používá interní staticky přidělenou vyrovnávací paměť. Data v této vyrovnávací paměti jsou přepsána z důvodu volání dalších `CTime` členských funkcí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [getDay –](#getday).

##  <a name="getsecond"></a>CTime –:: GetSecond

Vrátí druhý reprezentovaný `CTime` objektem.

```
int GetSecond() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí sekundu v závislosti na místním čase v rozsahu 0 až 59.

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, která používá interní staticky přidělenou vyrovnávací paměť. Data v této vyrovnávací paměti jsou přepsána z důvodu volání dalších `CTime` členských funkcí.

### <a name="example"></a>Příklad

Podívejte se na příklad [](#gethour)pro GetHour.

##  <a name="gettime"></a>CTime –:: GetTime

Vrátí hodnotu **__time64_t** pro daný `CTime` objekt.

```
__time64_t GetTime() const throw();
```

### <a name="return-value"></a>Návratová hodnota

`GetTime`Vrátí počet sekund mezi aktuálním `CTime` objektem a 1. ledna 1970.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]

##  <a name="getyear"></a>CTime –:: GetYear

Vrátí rok reprezentovaný `CTime` objektem.

```
int GetYear();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí rok na základě místního času v rozsahu od 1. ledna 1970 do 18. ledna 2038 (včetně).

### <a name="remarks"></a>Poznámky

Tato funkce volá `GetLocalTm`, která používá interní staticky přidělenou vyrovnávací paměť. Data v této vyrovnávací paměti jsou přepsána z důvodu volání dalších `CTime` členských funkcí.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [getDay –](#getday).

##  <a name="operator_eq"></a>CTime –:: operator =

Operátor přiřazení

```
CTime& operator=(__time64_t time) throw();
```

### <a name="parameters"></a>Parametry

*čas*<br/>
Nová hodnota data a času.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTime` objekt.

### <a name="remarks"></a>Poznámky

Tento přetížený operátor přiřazení kopíruje zdrojový čas do tohoto `CTime` objektu. Interní časové úložiště v `CTime` objektu je nezávislé na časovém pásmu. Při přiřazování není nutné konverzi časového pásma.

##  <a name="operator_add_-"></a>CTime –:: operator +,-

Tyto operátory přidávají a `CTimeSpan` odčítání a `CTime` objekty.

```
CTime operator+(CTimeSpan timeSpan) const throw();
CTime operator-(CTimeSpan timeSpan) const throw();
CTimeSpan operator-(CTime time) const throw();
```

### <a name="parameters"></a>Parametry

*timeSpan*<br/>
`CTimeSpan` Objekt, který má být přidán nebo odečten.

*čas*<br/>
`CTime` Objekt, který má být odečten.

### <a name="return-value"></a>Návratová hodnota

Objekt `CTime` nebo`CTimeSpan` představující výsledek operace.

### <a name="remarks"></a>Poznámky

`CTime`objekty reprezentují absolutní `CTimeSpan` čas, objekty reprezentují relativní čas. První dva operátory umožňují přidat objekty do objektů a z `CTimeSpan` `CTime` nich odčítání. Třetí operátor vám umožňuje odečíst jeden `CTime` objekt od druhého objektu a získat `CTimeSpan` objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]

##  <a name="operator_add_eq_-_eq"></a>CTime –:: operator + =,-=

Tyto operátory přidávají a odčítání `CTimeSpan` objekt do a z tohoto `CTime` objektu.

```
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CTimeSpan` Objekt, který má být přidán nebo odečten.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTime` objekt.

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují přidat a odečíst `CTimeSpan` objekt do a z tohoto `CTime` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]

##  <a name="serialize64"></a>CTime –:: Serialize64

> [!NOTE]
> Tato metoda je k dispozici pouze v projektech MFC.

Serializace dat přidružených k členské proměnné do nebo z archivu.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*snížen*<br/>
`CArchive` Objekt, který chcete aktualizovat.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CArchive` objekt.

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
