---
title: Cfiletime – třída
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
ms.openlocfilehash: 07b888b031a38dc2f09404a14e729e26b3eaa019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235130"
---
# <a name="cfiletime-class"></a>Cfiletime – třída

Tato třída poskytuje metody pro správu přidružené k souboru hodnoty data a času.

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
|[CFileTime::GetCurrentTime](#getcurrenttime)|Voláním této funkce statických načíst `CFileTime` objekt, který představuje aktuální systémový datum a čas.|
|[CFileTime::GetTime](#gettime)|Volejte tuto metodu za účelem načtení čas `CFileTime` objektu.|
|[CFileTime::LocalToUTC](#localtoutc)|Voláním této metody lze převést místního souboru čas na čas souboru založené na koordinovaný univerzální čas (UTC).|
|[CFileTime::SetTime](#settime)|Volání této metody nastavte datum a čas, které jsou uložené `CFileTime` objektu.|
|[CFileTime::UTCToLocal](#utctolocal)|Volání této metody pro převod času na základě na na koordinovaný univerzální čas (UTC) na místní čas.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFileTime::operator-](#operator_-)|Tento operátor se používá k provedení odečtení na `CFileTime` nebo `CFileTimeSpan` objektu.|
|[CFileTime::operator! =](#operator_neq)|Tento operátor porovná dva `CFileTime` objekty nerovnost.|
|[CFileTime::operator +](#operator_add)|Tento operátor se používá k provedení sčítání na `CFileTimeSpan` objektu.|
|[CFileTime::operator +=](#operator_add_eq)|Tento operátor se používá k provedení sčítání na `CFileTimeSpan` objektu a výsledek přiřaďte do aktuálního objektu.|
|[CFileTime::operator &lt;](#operator_lt)|Tento operátor porovná dva `CFileTime` objekty k určení menší než.|
|[CFileTime::operator &lt;=](#operator_lt_eq)|Tento operátor porovná dva `CFileTime` objekty k určení rovnosti, nebo menší.|
|[CFileTime::operator =](#operator_eq)|Operátor přiřazení.|
|[CFileTime::operator-=](#operator_-_eq)|Tento operátor se používá k provedení odečtení na `CFileTimeSpan` objektu a výsledek přiřaďte do aktuálního objektu.|
|[CFileTime::operator ==](#operator_eq_eq)|Tento operátor porovná dva `CFileTime` objekty pro rovnost.|
|[CFileTime::operator &gt;](#operator_gt)|Tento operátor porovná dva `CFileTime` objekty k určení větší.|
|[CFileTime::operator &gt;=](#operator_gt_eq)|Tento operátor porovná dva `CFileTime` objekty k určení rovnosti, nebo větší.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[CFileTime::Day](#day)|Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které tvoří jeden den.|
|[CFileTime::Hour](#hour)|Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které společně tvoří jednu hodinu.|
|[CFileTime::Millisecond](#millisecond)|Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které tvoří jeden milisekund.|
|[CFileTime::Minute](#minute)|Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které společně tvoří jednu minutu.|
|[CFileTime::Second](#second)|Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které společně tvoří jednu sekundu.|
|[CFileTime::Week](#week)|Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které tvoří jeden týden.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro správu přidružené k vytváření, přístup a úpravy souborů hodnoty data a času. Metodám a datovým této třídy jsou často používána ve spojení s `CFileTimeSpan` objekty, které se zabývají relativní časové hodnoty.

Hodnota data a času se ukládá jako 64bitová hodnota reprezentující počet 100nanosekundových intervalů o délce od 1. ledna 1601. To je formát koordinovaný univerzální čas (UTC).

Pro zjednodušení výpočtů, jsou k dispozici následující statické konstantní členské proměnné:

|Členské proměnné|Počet intervalů o délce 100 nanosekund|
|---------------------|-----------------------------------------|
|Milisekundy|10,000|
|Sekunda|Milisekundy \* 1 000|
|Minuta|Druhý \* 60|
|Hodina|Minuta \* 60|
|Den|Hodina \* 24|
|Týden|Den \* 7|

**Poznámka:** všechny systémy souborů lze zaznamenat vytvoření a čas posledního přístupu a ne všechny systémy souborů je zaznamenat stejným způsobem. Vytvořte například v systému souborů FAT Windows NT, čas s rozlišením 10 milisekund, čas zápisu rozlišením 2 sekundy a čas přístupu s rozlišením 1 den (data access). V systému souborů NTFS čas přístupu s rozlišením 1 hodina. Kromě toho FAT zaznamenává časy na disku v místním čase, ale systém souborů NTFS zaznamenává ve standardu UTC, časy na disku. Další informace najdete v tématu [časy](/windows/desktop/SysInfo/file-times).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`FILETIME`

`CFileTime`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

##  <a name="cfiletime"></a>  CFileTime::CFileTime

Konstruktor

```
CFileTime() throw();
CFileTime(const FILETIME& ft) throw();
CFileTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
A [hodnota FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime) struktury.

*nTime*<br/>
Datum a čas vyjádřený jako hodnotu 64-bit.

### <a name="remarks"></a>Poznámky

`CFileTime` Objektu lze vytvořit pomocí existující data a času `FILETIME` struktury nebo vyjádřené jako hodnotu 64-bit (v místním nebo formáty času koordinovaný univerzální čas (UTC)). Výchozí konstruktor nastaví čas na hodnotu 0.

##  <a name="day"></a>  CFileTime::Day

Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které tvoří jeden den.

```
static const ULONGLONG Day = Hour* 24;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).

##  <a name="getcurrenttime"></a>  CFileTime::GetCurrentTime

Voláním této funkce statických načíst `CFileTime` objekt, který představuje aktuální systémový datum a čas.

```
static CFileTime GetCurrentTime() throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální systémový datum a čas ve formátu koordinovaného univerzálního času (UTC).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#41](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_1.cpp)]

##  <a name="gettime"></a>  CFileTime::GetTime

Volejte tuto metodu za účelem načtení čas `CFileTime` objektu.

```
ULONGLONG GetTime() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí datum a čas jako 64bitové číslo, které mohou být ve formátu koordinovaného univerzálního času (UTC) nebo místní.

##  <a name="hour"></a>  CFileTime::Hour

Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které společně tvoří jednu hodinu.

```
static const ULONGLONG Hour = Minute* 60;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).

##  <a name="localtoutc"></a>  CFileTime::LocalToUTC

Voláním této metody lze převést místního souboru čas na čas souboru založené na koordinovaný univerzální čas (UTC).

```
CFileTime LocalToUTC() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objekt, který obsahuje čas ve formátu UTC.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime::UTCToLocal](#utctolocal).

##  <a name="millisecond"></a>  CFileTime::Millisecond

Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které tvoří jeden milisekund.

```
static const ULONGLONG Millisecond = 10000;
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#44](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_2.cpp)]

##  <a name="minute"></a>  CFileTime::Minute

Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které společně tvoří jednu minutu.

```
static const ULONGLONG Minute = Second* 60;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).

##  <a name="operator_-"></a>  CFileTime::operator-

Tento operátor se používá k provedení odečtení na `CFileTime` nebo `CFileTimeSpan` objektu.

```
CFileTime operator-(CFileTimeSpan span) const throw();
CFileTimeSpan operator-(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

*FT*<br/>
A `CFileTime` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objektu nebo `CFileTimeSpan` objekt představující výsledek časový rozdíl mezi dvěma objekty.

##  <a name="operator_neq"></a>  CFileTime::operator! =

Tento operátor porovná dva `CFileTime` objekty nerovnost.

```
bool operator!=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud položka, který se porovnává se nerovná `CFileTime` objektu, jinak hodnota FALSE.

##  <a name="operator_add"></a>  CFileTime::operator +

Tento operátor se používá k provedení sčítání na `CFileTimeSpan` objektu.

```
CFileTime operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objekt představující výsledek původní čas a relativní časové.

##  <a name="operator_add_eq"></a>  CFileTime::operator +=

Tento operátor se používá k provedení sčítání na `CFileTimeSpan` objektu a výsledek přiřaďte do aktuálního objektu.

```
CFileTime& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objekt představující výsledek původní čas a relativní časové.

##  <a name="operator_lt"></a>  CFileTime::operator &lt;

Tento operátor porovná dva `CFileTime` objekty k určení menší než.

```
bool operator<(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší (dříve v čase) než druhé, FALSE jinak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#43](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_3.cpp)]

##  <a name="operator_lt_eq"></a>  CFileTime::operator &lt;=

Tento operátor porovná dva `CFileTime` objekty k určení rovnosti, nebo menší.

```
bool operator<=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt menší než (dříve v čase) nebo roven druhému, jinak hodnota FALSE.

##  <a name="operator_eq"></a>  CFileTime::operator =

Operátor přiřazení.

```
CFileTime& operator=(const FILETIME& ft) throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
A `CFileTime` objekt, který obsahuje nový čas a datum.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objektu.

##  <a name="operator_-_eq"></a>  CFileTime::operator-=

Tento operátor se používá k provedení odečtení na `CFileTimeSpan` objektu a výsledek přiřaďte do aktuálního objektu.

```
CFileTime& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objekt, který obsahuje relativní časové se má odečíst.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTime` objektu.

##  <a name="operator_eq_eq"></a>  CFileTime::operator ==

Tento operátor porovná dva `CFileTime` objekty pro rovnost.

```
bool operator==(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou objekty stejné; jinak hodnota FALSE.

##  <a name="operator_gt"></a>  CFileTime::operator &gt;

Tento operátor porovná dva `CFileTime` objekty k určení větší.

```
bool operator>(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt větší než (později v čase) než druhé, jinak hodnota FALSE.

##  <a name="operator_gt_eq"></a>  CFileTime::operator &gt;=

Tento operátor porovná dva `CFileTime` objekty k určení rovnosti, nebo větší.

```
bool operator>=(CFileTime ft) const throw();
```

### <a name="parameters"></a>Parametry

*FT*<br/>
`CFileTime` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt (později v čase) větší než nebo roven druhému, jinak hodnota FALSE.

##  <a name="second"></a>  CFileTime::Second

Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které tvoří jeden den.

```
static const ULONGLONG Second = Millisecond* 1000;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).

##  <a name="settime"></a>  CFileTime::SetTime

Volání této metody nastavte datum a čas, které jsou uložené `CFileTime` objektu.

```
void SetTime(ULONGLONG nTime) throw();
```

### <a name="parameters"></a>Parametry

*nTime*<br/>
64 bitů hodnotu představující datum a čas ve formátu koordinovaného univerzálního času (UTC) nebo místní.

##  <a name="utctolocal"></a>  CFileTime::UTCToLocal

Volání této metody pro převod času na základě na na koordinovaný univerzální čas (UTC) na místní čas.

```
CFileTime UTCToLocal() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTime` objekt, který obsahuje čas ve formátu času místního souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#42](../../atl-mfc-shared/reference/codesnippet/cpp/cfiletime-class_4.cpp)]

##  <a name="week"></a>  CFileTime::Week

Statický datový člen ukládání počet intervalů o délce 100 nanosekund, které tvoří jeden týden.

```
static const ULONGLONG Week = Day* 7;
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime::Millisecond](#millisecond).

## <a name="see-also"></a>Viz také:

[FILETIME –](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTimeSpan – třída](../../atl-mfc-shared/reference/cfiletimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
