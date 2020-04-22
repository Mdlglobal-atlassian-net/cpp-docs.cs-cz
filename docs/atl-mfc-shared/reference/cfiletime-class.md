---
title: CFileTime – třída
ms.date: 10/18/2018
f1_keywords:
- CFileTime
- ATLTIME/ATL::CFileTime
- ATLTIME/ATL::CFileTime::CFileTime
- ATLTIME/ATL::CFileTime::GetCurrentTime
- ATLTIME/ATL::CFileTime::GetTime
- ATLTIME/ATL::CFileTime::LocalToUTC
- ATLTIME/ATL::CFileTime::SetTime
- ATLTIME/ATL::CFileTime::UTCToLocal
- ATLTIME/ATL::CFileTime::Day
- ATLTIME/ATL::CFileTime::Hour
- ATLTIME/ATL::CFileTime::Millisecond
- ATLTIME/ATL::CFileTime::Minute
- ATLTIME/ATL::CFileTime::Second
- ATLTIME/ATL::CFileTime::Week
helpviewer_keywords:
- CFileTime class
- shared classes, CFileTime
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
ms.openlocfilehash: fd19d941365c7772363417ce3e9225bd9b0300b2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748839"
---
# <a name="cfiletime-class"></a>CFileTime – třída

Tato třída poskytuje metody pro správu hodnot data a času přidružených k souboru.

## <a name="syntax"></a>Syntaxe

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|Volání této statické funkce `CFileTime` načíst objekt, který představuje aktuální systémové datum a čas.|
|[CFileTime::GetTime](#gettime)|Volání této metody načíst `CFileTime` čas z objektu.|
|[CFileTime::LocalTouTC](#localtoutc)|Volání této metody převést čas místního souboru na čas souboru na základě koordinovaného univerzálního času (UTC).|
|[CFileTime::SetTime](#settime)|Volání této metody nastavit datum a `CFileTime` čas uložený objektem.|
|[CFileTime::UTCToLocal](#utctolocal)|Volání této metody převést čas na základě koordinovaného univerzálního času (UTC) na místní čas souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFileTime::operátor -](#operator_-)|Tento operátor se používá k `CFileTime` provádění `CFileTimeSpan` odčítání na nebo objektu.|
|[CFileTime::operátor !=](#operator_neq)|Tento operátor porovnává `CFileTime` dva objekty pro nerovnost.|
|[CFileTime::operátor +](#operator_add)|Tento operátor se používá k `CFileTimeSpan` provedení sčítání na objekt.|
|[CFileTime::operátor +=](#operator_add_eq)|Tento operátor se používá k `CFileTimeSpan` provedení sčítání na objekt a přiřadit výsledek aktuálníobjekt.|
|[CFileTime::operátor&lt;](#operator_lt)|Tento operátor porovná `CFileTime` dva objekty k určení menší.|
|[CFileTime::operátor&lt;=](#operator_lt_eq)|Tento operátor porovná `CFileTime` dva objekty k určení rovnosti nebo menší.|
|[CFileTime::operátor =](#operator_eq)|Operátor přiřazení.|
|[CFileTime::operátor -=](#operator_-_eq)|Tento operátor se používá k `CFileTimeSpan` provedení odčítání objektu a přiřazení výsledku aktuálnímu objektu.|
|[CFileTime::operátor ==](#operator_eq_eq)|Tento operátor porovnává `CFileTime` dva objekty rovnosti.|
|[CFileTime::operátor&gt;](#operator_gt)|Tento operátor porovná `CFileTime` dva objekty k určení větší.|
|[CFileTime::operátor&gt;=](#operator_gt_eq)|Tento operátor porovnává `CFileTime` dva objekty k určení rovnosti nebo větší.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[CFileTime::Day](#day)|Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jeden den.|
|[CFileTime::Hodina](#hour)|Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jednu hodinu.|
|[CFileTime::Milisekunda](#millisecond)|Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jednu milisekundu.|
|[CFileTime::Minuta](#minute)|Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jednu minutu.|
|[CFileTime::Druhý](#second)|Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jednu sekundu.|
|[CFileTime::Týden](#week)|Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jeden týden.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro správu hodnot data a času spojených s vytvářením, přístupem a úpravou souborů. Metody a data této třídy se často `CFileTimeSpan` používají ve spojení s objekty, které se zabývají relativními časovými hodnotami.

Hodnota data a času je uložena jako 64bitová hodnota představující počet 100 nanosekundových intervalech od 1. Toto je formát Koordinovaný světový čas (UTC).

Pro zjednodušení výpočtů jsou k dispozici následující statické proměnné členů const:

|Členská proměnná|Počet 100nanosekundových intervalů|
|---------------------|-----------------------------------------|
|Milisekund|10 000|
|1 sekunda|Milisekunda \* 1 000|
|Minuta|Druhý \* ch60|
|Hodina|Minuta \* 60|
|Den|Hodina \* 24|
|Týden|Den \* 7|

**Poznámka:** Ne všechny systémy souborů mohou zaznamenávat vytváření a poslední přístupový čas a ne všechny systémy souborů je zaznamenávají stejným způsobem. Například v systému souborů Windows NT FAT má čas vytvoření rozlišení 10 milisekund, čas zápisu má rozlišení 2 sekundy a doba přístupu má rozlišení 1 den (datum přístupu). V systému souborů NTFS má doba přístupu rozlišení 1 hodina. Kromě toho systém SOUBORŮ FAT zaznamenává časy na disku v místním čase, ale systém souborů NTFS zaznamenává časy na disku v časech UTC. Další informace naleznete [v tématu Časy souborů](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

## <a name="cfiletimecfiletime"></a><a name="cfiletime"></a>CFileTime::CFileTime

Konstruktor

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Struktura [FILETIME.](/windows/win32/api/minwinbase/ns-minwinbase-filetime)

*nČas*<br/>
Datum a čas vyjádřený jako 64bitová hodnota.

### <a name="remarks"></a>Poznámky

Objekt `CFileTime` lze vytvořit pomocí existujícího data `FILETIME` a času ze struktury nebo vyjádřena jako 64bitová hodnota (v místních nebo koordinovaných formátech času u světového času (UTC). Výchozí konstruktor nastaví čas na 0.

## <a name="cfiletimeday"></a><a name="day"></a>CFileTime::Day

Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jeden den.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Příklad

Viz příklad [cfiletime::Millisecond](#millisecond).

## <a name="cfiletimegetcurrenttime"></a><a name="getcurrenttime"></a>CFileTime::GetCurrentTime

Volání této statické funkce `CFileTime` načíst objekt, který představuje aktuální systémové datum a čas.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální systémové datum a čas ve formátu UTC (Coordinated Universal Time).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

## <a name="cfiletimegettime"></a><a name="gettime"></a>CFileTime::GetTime

Volání této metody načíst `CFileTime` čas z objektu.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí datum a čas jako 64bitové číslo, které může být ve formátu místního nebo koordinovaného světového času (UTC).

## <a name="cfiletimehour"></a><a name="hour"></a>CFileTime::Hodina

Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jednu hodinu.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Příklad

Viz příklad [cfiletime::Millisecond](#millisecond).

## <a name="cfiletimelocaltoutc"></a><a name="localtoutc"></a>CFileTime::LocalTouTC

Volání této metody převést čas místního souboru na čas souboru na základě koordinovaného univerzálního času (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objekt obsahující čas ve formátu UTC.

### <a name="example"></a>Příklad

Viz příklad [cfiletime::UTCToLocal](#utctolocal).

## <a name="cfiletimemillisecond"></a><a name="millisecond"></a>CFileTime::Milisekunda

Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jednu milisekundu.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

## <a name="cfiletimeminute"></a><a name="minute"></a>CFileTime::Minuta

Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jednu minutu.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Příklad

Viz příklad [cfiletime::Millisecond](#millisecond).

## <a name="cfiletimeoperator--"></a><a name="operator_-"></a>CFileTime::operátor -

Tento operátor se používá k `CFileTime` provádění `CFileTimeSpan` odčítání na nebo objektu.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Objekt. `CFileTimeSpan`

*Ft*<br/>
Objekt. `CFileTime`

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objekt nebo `CFileTimeSpan` objekt představující výsledek časového rozdílu mezi těmito dvěma objekty.

## <a name="cfiletimeoperator-"></a><a name="operator_neq"></a>CFileTime::operátor !=

Tento operátor porovnává `CFileTime` dva objekty pro nerovnost.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Objekt, `CFileTime` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud se porovnávaná položka nerovná objektu, `CFileTime` jinak NEPRAVDA.

## <a name="cfiletimeoperator-"></a><a name="operator_add"></a>CFileTime::operátor +

Tento operátor se používá k `CFileTimeSpan` provedení sčítání na objekt.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Objekt. `CFileTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objekt představující výsledek původního času plus relativní čas.

## <a name="cfiletimeoperator-"></a><a name="operator_add_eq"></a>CFileTime::operátor +=

Tento operátor se používá k `CFileTimeSpan` provedení sčítání na objekt a přiřadit výsledek aktuálníobjekt.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Objekt. `CFileTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objekt představující výsledek původního času plus relativní čas.

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt"></a>CFileTime::operátor&lt;

Tento operátor porovná `CFileTime` dva objekty k určení menší.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Objekt, `CFileTime` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší (dříve v čase) než druhý NEPRAVDA jinak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

## <a name="cfiletimeoperator-lt"></a><a name="operator_lt_eq"></a>CFileTime::operátor&lt;=

Tento operátor porovná `CFileTime` dva objekty k určení rovnosti nebo menší.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Objekt, `CFileTime` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší než (dříve v čase) nebo rovna druhému, jinak NEPRAVDA.

## <a name="cfiletimeoperator-"></a><a name="operator_eq"></a>CFileTime::operátor =

Operátor přiřazení.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Objekt `CFileTime` obsahující nový čas a datum.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objekt.

## <a name="cfiletimeoperator--"></a><a name="operator_-_eq"></a>CFileTime::operátor -=

Tento operátor se používá k `CFileTimeSpan` provedení odčítání objektu a přiřazení výsledku aktuálnímu objektu.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Objekt `CFileTimeSpan` obsahující relativní čas odečíst.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objekt.

## <a name="cfiletimeoperator-"></a><a name="operator_eq_eq"></a>CFileTime::operátor ==

Tento operátor porovnává `CFileTime` dva objekty rovnosti.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Objekt `CFileTime` porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou objekty stejné, jinak NEPRAVDA.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt"></a>CFileTime::operátor&gt;

Tento operátor porovná `CFileTime` dva objekty k určení větší.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Objekt, `CFileTime` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt větší než (později v čase) než druhý, jinak NEPRAVDA.

## <a name="cfiletimeoperator-gt"></a><a name="operator_gt_eq"></a>CFileTime::operátor&gt;=

Tento operátor porovnává `CFileTime` dva objekty k určení rovnosti nebo větší.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*Ft*<br/>
Objekt, `CFileTime` který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt větší než (později v čase) nebo rovna druhému, jinak NEPRAVDA.

## <a name="cfiletimesecond"></a><a name="second"></a>CFileTime::Druhý

Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jeden den.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Příklad

Viz příklad [cfiletime::Millisecond](#millisecond).

## <a name="cfiletimesettime"></a><a name="settime"></a>CFileTime::SetTime

Volání této metody nastavit datum a `CFileTime` čas uložený objektem.

```cpp
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*nČas*<br/>
64bitová hodnota představující datum a čas ve formátu místního nebo koordinovaného světového času (UTC).

## <a name="cfiletimeutctolocal"></a><a name="utctolocal"></a>CFileTime::UTCToLocal

Volání této metody převést čas na základě koordinovaného univerzálního času (UTC) na místní čas souboru.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objekt obsahující čas v místním formátu času souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

## <a name="cfiletimeweek"></a><a name="week"></a>CFileTime::Týden

Statický datový člen ukládající počet 100 nanosekundových intervalů, které tvoří jeden týden.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Příklad

Viz příklad [cfiletime::Millisecond](#millisecond).

## <a name="see-also"></a>Viz také

[ČAS SOUBORU](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan – třída](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
