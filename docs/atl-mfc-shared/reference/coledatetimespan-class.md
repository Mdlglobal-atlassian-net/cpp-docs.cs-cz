---
title: COleDateTimeSpan – třída
ms.date: 03/27/2019
f1_keywords:
- COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::COleDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::Format
- ATLCOMTIME/ATL::COleDateTimeSpan::GetDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::GetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalDays
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalHours
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalMinutes
- ATLCOMTIME/ATL::COleDateTimeSpan::GetTotalSeconds
- ATLCOMTIME/ATL::COleDateTimeSpan::SetDateTimeSpan
- ATLCOMTIME/ATL::COleDateTimeSpan::SetStatus
- ATLCOMTIME/ATL::COleDateTimeSpan::m_span
- ATLCOMTIME/ATL::COleDateTimeSpan::m_status
helpviewer_keywords:
- timespan
- time span
- shared classes, COleDateTimeSpan
- Date data type, MFC encapsulation of
- COleDateTimeSpan class
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
ms.openlocfilehash: 7173fa0b6261ea718a02d399d944a1b5bb98b9f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317730"
---
# <a name="coledatetimespan-class"></a>COleDateTimeSpan – třída

Představuje relativní čas, časové rozpětí.

## <a name="syntax"></a>Syntaxe

```
class COleDateTimeSpan
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Vytvoří `COleDateTimeSpan` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleDateTimeSpan::Formát](#format)|Generuje formátovaný řetězec reprezentace `COleDateTimeSpan` objektu.|
|[COleDateTimeSpan::GetDays](#getdays)|Vrátí denní část rozsahu, `COleDateTimeSpan` který tento objekt představuje.|
|[COleDateTimeSpan::GetHours](#gethours)|Vrátí hodinovou část rozsahu, `COleDateTimeSpan` který tento objekt představuje.|
|[COleDateTimeSpan::GetMinutes](#getminutes)|Vrátí minutovou část rozsahu, `COleDateTimeSpan` který tento objekt představuje.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Vrátí druhou část rozsahu, `COleDateTimeSpan` který tento objekt představuje.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Získá stav (platnost) tohoto `COleDateTimeSpan` objektu.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Vrátí počet dní, `COleDateTimeSpan` které tento objekt představuje.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Vrátí počet hodin, `COleDateTimeSpan` které tento objekt představuje.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Vrátí počet minut, `COleDateTimeSpan` které tento objekt představuje.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Vrátí počet sekund, `COleDateTimeSpan` které tento objekt představuje.|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Nastaví hodnotu `COleDateTimeSpan` tohoto objektu.|
|[COleDateTimeSpan::SetStatus](#setstatus)|Nastaví stav (platnost) `COleDateTimeSpan` tohoto objektu.|

### <a name="public-operators"></a>Veřejné operátory

|||
|-|-|
|[operátor +, -](#operator_add_-)|Sečtením, odečtením `COleDateTimeSpan` a změnou znaménku pro hodnoty|
|[operátor +=, -=](#operator_add_eq_-_eq)|Sečtěte a `COleDateTimeSpan` odečtěte hodnotu z této `COleDateTimeSpan` hodnoty.|
|[operátor =](#operator_eq)|Zkopíruje `COleDateTimeSpan` hodnotu.|
|[operátor ==, <, <=](#coledatetimespan_relational_operators)|Porovnejte dvě `COleDateTimeSpan` hodnoty.|
|[operátor double](#operator_double)|Převede `COleDateTimeSpan` tuto hodnotu na **dvojitou**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Obsahuje základní **double** `COleDateTimeSpan` pro tento objekt.|
|[COleDateTimeSpan::m_status](#m_status)|Obsahuje stav tohoto `COleDateTimeSpan` objektu.|

## <a name="remarks"></a>Poznámky

`COleDateTimeSpan`nemá základní třídu.

Udržuje `COleDateTimeSpan` čas ve dnech.

`COleDateTimeSpan`používá se s doprovodnou třídou [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime`zapouzdřuje `DATE` datový typ automatizace OLE. `COleDateTime`představuje absolutní časové hodnoty. Všechny `COleDateTime` výpočty `COleDateTimeSpan` zahrnují hodnoty. Vztah mezi těmito třídami je obdobou vztahu mezi [CTime](../../atl-mfc-shared/reference/ctime-class.md) a [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).

Další informace o `COleDateTime` `COleDateTimeSpan` a třídy naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** ATLComTime.h

## <a name="coledatetimespan-relational-operators"></a><a name="coledatetimespan_relational_operators"></a>Relační operátory COleDateTimeSpan

Operátory porovnání.

```
bool operator==(const COleDateTimeSpan& dateSpan) const throw();
bool operator!=(const COleDateTimeSpan& dateSpan) const throw();
bool operator<(const COleDateTimeSpan& dateSpan) const throw();
bool operator>(const COleDateTimeSpan& dateSpan) const throw();
bool operator<=(const COleDateTimeSpan& dateSpan) const throw();
bool operator>=(const COleDateTimeSpan& dateSpan) const throw();
```

### <a name="parameters"></a>Parametry

*dateSpan*<br/>
Porovnat. `COleDateTimeSpan`

### <a name="return-value"></a>Návratová hodnota

Tyto operátory porovnávají dvě hodnoty data a časového rozpětí a vrátí hodnotu TRUE, pokud je podmínka splněna; jinak FALSE.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> AtLASSERT dojde, pokud je neplatný operand.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

## <a name="coledatetimespancoledatetimespan"></a><a name="coledatetimespan"></a>COleDateTimeSpan::COleDateTimeSpan

Vytvoří `COleDateTimeSpan` objekt.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*dblSpanSrc*<br/>
Počet dní, které mají být `COleDateTimeSpan` zkopírovány do nového objektu.

*lDny*, *nHodiny*, *nMins*, *nSecs*<br/>
Označte denní a časové hodnoty, `COleDateTimeSpan` které mají být zkopírovány do nového objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory `COleDateTimeSpan` vytvořit nové objekty inicializovány na zadanou hodnotu. Stručný popis každého z těchto konstruktorů je následující:

- **COleDateTimeSpan( )** Vytvoří `COleDateTimeSpan` objekt inicializovaný na 0.

- **COleDateTimeSpan(** `dblSpanSrc` **)** Vytvoří `COleDateTimeSpan` objekt z hodnoty s plovoucí desetinnou tácem.

- **COleDateTimeSpan(** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)** Vytvoří `COleDateTimeSpan` objekt inicializovaný na zadané číselné hodnoty.

Stav nového `COleDateTimeSpan` objektu je nastaven na platný.

Další informace o mezích `COleDateTimeSpan` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

## <a name="coledatetimespanformat"></a><a name="format"></a>COleDateTimeSpan::Formát

Generuje formátovaný řetězec reprezentace `COleDateTimeSpan` objektu.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormát*<br/>
Formátovací řetězec podobný řetězci `printf` formátování. Kódy formátování, před nimiž`%`je podepsáno procento ( `COleDateTimeSpan` ) , jsou nahrazeny odpovídající komponentou. Ostatní znaky ve formátovacím řetězci jsou zkopírovány beze změny do vráceného řetězce. Hodnota a význam formátovacích kódů pro jsou uvedeny `Format` níže:

- **%H** Hodiny v aktuálním dni

- **%M** Minuty v aktuální hodině

- **%S** Sekundy v aktuální minutě

- **%%** Znak procenta

Čtyři formátkódy uvedené výše jsou pouze kódy, které formát bude akceptovat.

-

*Nid*<br/>
ID prostředku pro řetězec řízení formátu.

### <a name="return-value"></a>Návratová hodnota

A, `CString` který obsahuje formátovanou hodnotu data a časového rozpětí.

### <a name="remarks"></a>Poznámky

Volání těchto funkcí k vytvoření formátované reprezentace hodnoty časového rozpětí. Pokud je stav `COleDateTimeSpan` tohoto objektu null, vrácená hodnota je prázdný řetězec. Pokud je stav neplatný, je návratový řetězec určen IDS_INVALID_DATETIMESPAN prostředků řetězce.

Stručný popis formulářů pro tuto funkci je následující:

**Formát(** *pFormat* **)**<br/>
Tento formulář formátuje hodnotu pomocí formátovacího řetězce, který obsahuje speciální formátovací kódy, před nimiž je znaménko procenta (%), jako v `printf`. Formátovací řetězec je předán jako parametr funkce.

**Formát(** *nID* **)**<br/>
Tento formulář formátuje hodnotu pomocí formátovacího řetězce, který obsahuje speciální formátovací kódy, před nimiž je znaménko procenta (%), jako v `printf`. Formátovací řetězec je prostředek. ID tohoto řetězce prostředku je předán jako parametr.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

## <a name="coledatetimespangetdays"></a><a name="getdays"></a>COleDateTimeSpan::GetDays

Načte denní část této hodnoty data a časového rozpětí.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Denní část této hodnoty data a časového rozpětí.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi přibližně - 3,615,000 a 3,615,000.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

## <a name="coledatetimespangethours"></a><a name="gethours"></a>COleDateTimeSpan::GetHours

Načte hodinovou část této hodnoty data a časového rozpětí.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Část hodin této hodnoty data a časového rozpětí.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi - 23 a 23.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

## <a name="coledatetimespangetminutes"></a><a name="getminutes"></a>COleDateTimeSpan::GetMinutes

Načte minutovou část této hodnoty data a časového rozpětí.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Minutová část této hodnoty data a časového rozpětí.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi - 59 a 59.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

## <a name="coledatetimespangetseconds"></a><a name="getseconds"></a>COleDateTimeSpan::GetSeconds

Načte druhou část této hodnoty data a časového rozpětí.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Část sekund této hodnoty data a časového rozpětí.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi - 59 a 59.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

## <a name="coledatetimespangetstatus"></a><a name="getstatus"></a>COleDateTimeSpan::GetStatus

Získá stav (platnost) tohoto `COleDateTimeSpan` objektu.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Stav této `COleDateTimeSpan` hodnoty.

### <a name="remarks"></a>Poznámky

Vrácená hodnota je `DateTimeSpanStatus` definována ve výčtu typu, `COleDateTimeSpan` který je definován v rámci třídy.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleDateTimeSpan::valid`Označuje, `COleDateTimeSpan` že tento objekt je platný.

- `COleDateTimeSpan::invalid`Označuje, `COleDateTimeSpan` že tento objekt je neplatný; to znamená, že jeho hodnota může být nesprávná.

- `COleDateTimeSpan::null`Označuje, `COleDateTimeSpan` že tento objekt je null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Toto je "null" ve smyslu databáze "s žádnou hodnotu," na rozdíl od C++ NULL.)

Stav objektu `COleDateTimeSpan` je neplatný v následujících případech:

- Pokud tento objekt došlo k přetečení nebo podtečení během operace `+=` `-=`aritmetické přiřazení, a to nebo .

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na neplatný pomocí `SetStatus`.

Další informace o operacích, které mohou nastavit stav na neplatný, naleznete v [tématu COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) a [COleDateTimeSpan::operator ==, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Další informace o mezích `COleDateTimeSpan` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespangettotaldays"></a><a name="gettotaldays"></a>COleDateTimeSpan::GetTotalDays

Načte tuto hodnotu data a časového rozpětí vyjádřenou ve dnech.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota data a časového rozpětí vyjádřená ve dnech. Přestože tato funkce je prototypován vrátit double, vždy vrátí hodnotu celé číslo.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi přibližně - 3.65e6 a 3.65e6.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

## <a name="coledatetimespangettotalhours"></a><a name="gettotalhours"></a>COleDateTimeSpan::GetTotalHours

Načte tuto hodnotu data a časového rozpětí vyjádřenou v hodinách.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota data a časového rozpětí vyjádřená v hodinách. Přestože tato funkce je prototypován vrátit double, vždy vrátí hodnotu celé číslo.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi přibližně - 8.77e7 a 8.77e7.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

Viz příklad [gettotaldays](#gettotaldays).

## <a name="coledatetimespangettotalminutes"></a><a name="gettotalminutes"></a>COleDateTimeSpan::GetTotalMinutes

Načte tuto hodnotu data a časového rozpětí vyjádřenou v minutách.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota data a časového rozpětí vyjádřená v minutách. Přestože tato funkce je prototypován vrátit double, vždy vrátí hodnotu celé číslo.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi přibližně - 5.26e9 a 5.26e9.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

Viz příklad [gettotaldays](#gettotaldays).

## <a name="coledatetimespangettotalseconds"></a><a name="gettotalseconds"></a>COleDateTimeSpan::GetTotalSeconds

Načte tuto hodnotu data a časového rozpětí vyjádřenou v sekundách.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota data a časového rozpětí vyjádřená v sekundách. Přestože tato funkce je prototypován vrátit double, vždy vrátí hodnotu celé číslo.

### <a name="remarks"></a>Poznámky

Vrácené hodnoty z této funkce rozsahu mezi přibližně - 3.16e11 do 3.16e11.

Další funkce, které dotaz `COleDateTimeSpan` hodnotu objektu, naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Příklad

Viz příklad [gettotaldays](#gettotaldays).

## <a name="coledatetimespanm_span"></a><a name="m_span"></a>COleDateTimeSpan::m_span

Základní **dvojitá** hodnota `COleDateTime` pro tento objekt.

```
double m_span;
```

### <a name="remarks"></a>Poznámky

Tato hodnota vyjadřuje datum a časové rozpětí ve dnech.

> [!CAUTION]
> Změna hodnoty v **dvojitém** datovém členu `COleDateTimeSpan` změní hodnotu tohoto objektu. Nezmění stav tohoto `COleDateTimeSpan` objektu.

## <a name="coledatetimespanm_status"></a><a name="m_status"></a>COleDateTimeSpan::m_status

Typ pro tento datový člen je výčtový typ `DateTimeSpanStatus`, `COleDateTimeSpan` který je definován v rámci třídy.

```
DateTimeSpanStatus m_status;
```

### <a name="remarks"></a>Poznámky

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleDateTimeSpan::valid`Označuje, `COleDateTimeSpan` že tento objekt je platný.

- `COleDateTimeSpan::invalid`Označuje, `COleDateTimeSpan` že tento objekt je neplatný; to znamená, že jeho hodnota může být nesprávná.

- `COleDateTimeSpan::null`Označuje, `COleDateTimeSpan` že tento objekt je null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Toto je "null" ve smyslu databáze "s žádnou hodnotu," na rozdíl od C++ NULL.)

Stav objektu `COleDateTimeSpan` je neplatný v následujících případech:

- Pokud tento objekt došlo k přetečení nebo podtečení během operace `+=` `-=`aritmetické přiřazení, a to nebo .

- Pokud byla tomuto objektu přiřazena neplatná hodnota.

- Pokud byl stav tohoto objektu explicitně nastaven na neplatný pomocí [funkce SetStatus](#setstatus).

Další informace o operacích, které mohou nastavit stav na neplatný, naleznete v [tématu COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) a [COleDateTimeSpan::operator ==, -=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
> Tento datový člen je určen pro pokročilé programovací situace. Měli byste použít včleněné členské funkce [GetStatus](#getstatus) a [SetStatus](#setstatus). Viz `SetStatus` další upozornění týkající se explicitní nastavení tohoto datového člena.

Další informace o mezích `COleDateTimeSpan` pro hodnoty naleznete v článku [Datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="coledatetimespanoperator-"></a><a name="operator_eq"></a>COleDateTimeSpan::operátor =

Zkopíruje `COleDateTimeSpan` hodnotu.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor přetíženého přiřazení zkopíruje zdrojovou hodnotu `COleDateTimeSpan` data a časového rozpětí do tohoto objektu.

## <a name="coledatetimespanoperator---"></a><a name="operator_add_-"></a>COleDateTimeSpan::operátor +, -

Sečtením, odečtením `COleDateTimeSpan` a změnou znaménku pro hodnoty

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Poznámky

První dva operátory umožňují přidat a odečíst hodnoty data a časového rozpětí. Třetí umožňuje změnit znaménko hodnoty data a časového rozpětí.

Pokud některý z operandů je null, stav `COleDateTimeSpan` výsledné hodnoty je null.

Pokud je některý z operandů neplatný a druhý není null, je stav výsledné `COleDateTimeSpan` hodnoty neplatný.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

## <a name="coledatetimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>COleDateTimeSpan::operátor +=, -=

Sečtěte a `COleDateTimeSpan` odečtěte hodnotu z této `COleDateTimeSpan` hodnoty.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují přidat a odečíst hodnoty data `COleDateTimeSpan` a časového rozpětí z tohoto objektu. Pokud některý z operandů je null, stav `COleDateTimeSpan` výsledné hodnoty je null.

Pokud je některý z operandů neplatný a druhý není null, je stav výsledné `COleDateTimeSpan` hodnoty neplatný.

Další informace o platných, neplatných a nulových hodnotách stavu naleznete v [proměnné m_status](#m_status) člena.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

## <a name="coledatetimespanoperator-double"></a><a name="operator_double"></a>COleDateTimeSpan::operátor double

Převede `COleDateTimeSpan` tuto hodnotu na **dvojitou**.

```
operator double() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí hodnotu této `COleDateTimeSpan` hodnoty jako počet dní s plovoucí desetinnou desetinnou.

## <a name="coledatetimespansetdatetimespan"></a><a name="setdatetimespan"></a>COleDateTimeSpan::SetDateTimeSpan

Nastaví hodnotu této hodnoty data a časového rozpětí.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*lDny*, *nHodiny*, *nMins*, *nSecs*<br/>
Označte hodnoty data a časového rozpětí, které mají `COleDateTimeSpan` být zkopírovány do tohoto objektu.

### <a name="remarks"></a>Poznámky

Funkce, které dotaz hodnotu objektu, `COleDateTimeSpan` naleznete v následujících členských funkcí:

- [GetDays](#getdays)

- [GetHours](#gethours)

- [GetMinutes](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

## <a name="coledatetimespansetstatus"></a><a name="setstatus"></a>COleDateTimeSpan::SetStatus

Nastaví stav (platnost) `COleDateTimeSpan` tohoto objektu.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Nová hodnota stavu `COleDateTimeSpan` pro tento objekt.

### <a name="remarks"></a>Poznámky

Hodnota parametru *Stav* je `DateTimeSpanStatus` definována ve výčtu typu, který je definován v rámci třídy. `COleDateTimeSpan`

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Stručný popis těchto hodnot stavu naleznete v následujícím seznamu:

- `COleDateTimeSpan::valid`Označuje, `COleDateTimeSpan` že tento objekt je platný.

- `COleDateTimeSpan::invalid`Označuje, `COleDateTimeSpan` že tento objekt je neplatný; to znamená, že jeho hodnota může být nesprávná.

- `COleDateTimeSpan::null`Označuje, `COleDateTimeSpan` že tento objekt je null, to znamená, že pro tento objekt nebyla zadána žádná hodnota. (Toto je "null" ve smyslu databáze "s žádnou hodnotu," na rozdíl od C++ NULL.)

   > [!CAUTION]
   > Tato funkce je určena pro pokročilé programovací situace. Tato funkce nemění data v tomto objektu. Nejčastěji se používá k nastavení stavu **na hodnotu null** nebo **neplatné**. Všimněte si, že operátor přiřazení ([operátor =](#operator_eq)) a [SetDateTimeSpan](#setdatetimespan) nastavit stav objektu na základě zdrojové hodnoty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Viz také

[COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime – třída](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
