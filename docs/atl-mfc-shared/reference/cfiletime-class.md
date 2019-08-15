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
ms.openlocfilehash: b24d1e4d3e670a820c41735617b7db6780ff137c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491482"
---
# <a name="cfiletime-class"></a>CFileTime – třída

Tato třída poskytuje metody pro správu hodnot data a času přidružených k souboru.

## <a name="syntax"></a>Syntaxe

```
class CFileTime :  public FILETIME
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFileTime::CFileTime](#cfiletime)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFileTime::GetCurrentTime](#getcurrenttime)|Voláním této statické funkce načtěte `CFileTime` objekt, který představuje aktuální systémové datum a čas.|
|[CFileTime:: GetTime](#gettime)|Voláním této metody načtete čas z `CFileTime` objektu.|
|[CFileTime::LocalToUTC](#localtoutc)|Voláním této metody můžete převést čas místního souboru na čas souboru na základě koordinovaného univerzálního času (UTC).|
|[CFileTime:: SetTime –](#settime)|Voláním této metody nastavte datum a čas uložený `CFileTime` objektem.|
|[CFileTime::UTCToLocal](#utctolocal)|Voláním této metody můžete převést čas na základě koordinovaného univerzálního času (UTC) na čas místního souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CFileTime:: operator-](#operator_-)|Tento operátor slouží k provedení odečítání `CFileTime` objektu nebo. `CFileTimeSpan`|
|[CFileTime:: operator! =](#operator_neq)|Tento operátor porovná `CFileTime` dva objekty pro nerovnost.|
|[CFileTime:: operator + – operátor](#operator_add)|Tento operátor slouží k přidání `CFileTimeSpan` objektu.|
|[CFileTime:: operator + =](#operator_add_eq)|Tento operátor slouží k doplnění `CFileTimeSpan` objektu a přiřazení výsledku k aktuálnímu objektu.|
|[CFileTime:: operator&lt;](#operator_lt)|Tento operátor porovná `CFileTime` dva objekty a určí menší.|
|[CFileTime:: operator&lt;=](#operator_lt_eq)|Tento operátor porovná `CFileTime` dva objekty a určí rovnost nebo menší.|
|[CFileTime:: operator =](#operator_eq)|Operátor přiřazení|
|[CFileTime:: operator-=](#operator_-_eq)|Tento operátor slouží k provedení odčítání u `CFileTimeSpan` objektu a přiřazení výsledku k aktuálnímu objektu.|
|[CFileTime:: operator = = – operátor](#operator_eq_eq)|Tento operátor porovná `CFileTime` dva objekty pro rovnost.|
|[CFileTime:: operator&gt;](#operator_gt)|Tento operátor porovná `CFileTime` dva objekty a určí větší.|
|[CFileTime:: operator&gt;=](#operator_gt_eq)|Tento operátor porovná `CFileTime` dva objekty a určí rovnost nebo větší.|

### <a name="public-constants"></a>Veřejné konstanty

|Name|Popis|
|----------|-----------------|
|[CFileTime::D Ay](#day)|Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jeden den.|
|[CFileTime:: Hour](#hour)|Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jednu hodinu.|
|[CFileTime:: milisekund](#millisecond)|Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jednu milisekundu.|
|[CFileTime:: min](#minute)|Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jednu minutu.|
|[CFileTime:: Second](#second)|Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jednu sekundu.|
|[CFileTime:: Week](#week)|Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jeden týden.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro správu hodnot data a času spojených s vytvářením, přístupem a úpravou souborů. Metody a data této třídy se často používají ve spojení s `CFileTimeSpan` objekty, které se týkají relativních časových hodnot.

Hodnota data a času je uložena jako 64 hodnota, která představuje počet intervalů 100-nanosekund od 1. ledna 1601. Toto je formát koordinovaného světového času (UTC).

Pro zjednodušení výpočtů jsou k dispozici následující statické členské proměnné const:

|Členská proměnná|Počet intervalů 100 – nanosekund|
|---------------------|-----------------------------------------|
|Komponentu|10,000|
|Sekunda|Milisekunda \* 1 000|
|Minuta|Druhý \* 60|
|Hodina|Minutová \* 60|
|Den|Hodina \* 24|
|Týden|Den \* 7|

**Poznámka:** Ne všechny systémy souborů mohou nahrávat vytvoření a čas posledního přístupu a ne všechny systémy souborů nahrávat stejným způsobem. Například v systému souborů Windows NT FAT má čas vytvoření rozlišení 10 milisekund, doba zápisu má rozlišení 2 sekundy a doba přístupu má hodnotu 1 den (datum přístupu). V systému souborů NTFS má doba přístupu hodnotu 1 hodina. Kromě toho systém souborů FAT zaznamenává čas na disku v místním čase, ale zaznamenává čas na disku v UTC. Další informace najdete v tématu [časy souborů](/windows/win32/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime. h

##  <a name="cfiletime"></a>CFileTime::CFileTime

Konstruktor

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
Struktura [času](/windows/win32/api/minwinbase/ns-minwinbase-filetime) .

*nČasový*<br/>
Datum a čas vyjádřený jako hodnota 64.

### <a name="remarks"></a>Poznámky

Objekt lze vytvořit pomocí stávajícího data a času `FILETIME` ze struktury nebo vyjádřen jako 64 hodnota (v místním nebo koordinovaném formátu času UTC). `CFileTime` Výchozí konstruktor nastaví čas na 0.

##  <a name="day"></a>CFileTime::D Ay

Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jeden den.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: milisekund](#millisecond).

##  <a name="getcurrenttime"></a>CFileTime::GetCurrentTime

Voláním této statické funkce načtěte `CFileTime` objekt, který představuje aktuální systémové datum a čas.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální systémové datum a čas ve formátu koordinovaného světového času (UTC).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>CFileTime:: GetTime

Voláním této metody načtete čas z `CFileTime` objektu.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí datum a čas jako 64 číslo, které může být buď ve formátu místního nebo koordinovaného univerzálního času (UTC).

##  <a name="hour"></a>CFileTime:: Hour

Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jednu hodinu.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: milisekund](#millisecond).

##  <a name="localtoutc"></a>CFileTime::LocalToUTC

Voláním této metody můžete převést čas místního souboru na čas souboru na základě koordinovaného univerzálního času (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Návratová hodnota

`CFileTime` Vrátí objekt, který obsahuje čas ve formátu UTC.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: UTCToLocal](#utctolocal).

##  <a name="millisecond"></a>CFileTime:: milisekund

Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jednu milisekundu.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>CFileTime:: min

Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jednu minutu.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: milisekund](#millisecond).

##  <a name="operator_-"></a>CFileTime:: operator-

Tento operátor slouží k provedení odečítání `CFileTime` objektu nebo. `CFileTimeSpan`

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

*leva*<br/>
A `CFileTime` objektu.

### <a name="return-value"></a>Návratová hodnota

`CFileTime` Vrátí objekt`CFileTimeSpan` nebo objekt představující výsledek časového rozdílu mezi těmito dvěma objekty.

##  <a name="operator_neq"></a>CFileTime:: operator! =

Tento operátor porovná `CFileTime` dva objekty pro nerovnost.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
`CFileTime` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud položka, která je porovnána, `CFileTime` není rovna objektu, jinak false.

##  <a name="operator_add"></a>CFileTime:: operator + – operátor

Tento operátor slouží k přidání `CFileTimeSpan` objektu.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

`CFileTime` Vrátí objekt představující výsledek původního času a relativního času.

##  <a name="operator_add_eq"></a>CFileTime:: operator + =

Tento operátor slouží k doplnění `CFileTimeSpan` objektu a přiřazení výsledku k aktuálnímu objektu.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objekt představující výsledek původního času a relativního času.

##  <a name="operator_lt"></a>CFileTime:: operator&lt;

Tento operátor porovná `CFileTime` dva objekty a určí menší.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
`CFileTime` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší (dříve v čase) než druhý, v opačném případě FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>CFileTime:: operator&lt;=

Tento operátor porovná `CFileTime` dva objekty a určí rovnost nebo menší.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
`CFileTime` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší než (dříve v čase) nebo rovno druhé, jinak FALSE.

##  <a name="operator_eq"></a>CFileTime:: operator =

Operátor přiřazení

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
`CFileTime` Objekt, který obsahuje nový čas a datum.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objekt.

##  <a name="operator_-_eq"></a>CFileTime:: operator-=

Tento operátor slouží k provedení odčítání u `CFileTimeSpan` objektu a přiřazení výsledku k aktuálnímu objektu.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt obsahující relativní čas, který má být odečten.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objekt.

##  <a name="operator_eq_eq"></a>CFileTime:: operator = = – operátor

Tento operátor porovná `CFileTime` dva objekty pro rovnost.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
`CFileTime` Objekt, který chcete porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud jsou objekty stejné, jinak FALSE.

##  <a name="operator_gt"></a>CFileTime:: operator&gt;

Tento operátor porovná `CFileTime` dva objekty a určí větší.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
`CFileTime` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší než (později v čase) než druhý, jinak FALSE.

##  <a name="operator_gt_eq"></a>CFileTime:: operator&gt;=

Tento operátor porovná `CFileTime` dva objekty a určí rovnost nebo větší.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*leva*<br/>
`CFileTime` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší než (později v čase) nebo rovno druhé, jinak FALSE.

##  <a name="second"></a>CFileTime:: Second

Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jeden den.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: milisekund](#millisecond).

##  <a name="settime"></a>CFileTime:: SetTime –

Voláním této metody nastavte datum a čas uložený `CFileTime` objektem.

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*nČasový*<br/>
Hodnota 64 představující datum a čas v místním nebo koordinovaném formátu času (UTC).

##  <a name="utctolocal"></a>CFileTime::UTCToLocal

Voláním této metody můžete převést čas na základě koordinovaného univerzálního času (UTC) na čas místního souboru.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Návratová hodnota

`CFileTime` Vrátí objekt obsahující čas v místním formátu času souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>CFileTime:: Week

Statický datový člen ukládá počet intervalů 100 – nanosekund, které tvoří jeden týden.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: milisekund](#millisecond).

## <a name="see-also"></a>Viz také:

[FILETIME –](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan – třída](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
