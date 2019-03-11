---
title: Coledatetimespan – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: feef238be96d9a04c2c41e6955efec8b23cf6a89
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748486"
---
# <a name="coledatetimespan-class"></a>Coledatetimespan – třída

Představuje relativní časové rozpětí času.

## <a name="syntax"></a>Syntaxe

```
class COleDateTimeSpan
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleDateTimeSpan::COleDateTimeSpan](#coledatetimespan)|Vytvoří `COleDateTimeSpan` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDateTimeSpan::Format](#format)|Generuje formátovaný řetězec představující `COleDateTimeSpan` objektu.|
|[COleDateTimeSpan::GetDays](#getdays)|Vrátí část pro den rozpětí to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::GetHours](#gethours)|Vrátí část pro hodinu rozpětí to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::GetMinutes](#getminutes)|Vrátí část pro minuty rozpětí to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::GetSeconds](#getseconds)|Vrátí část pro sekundy rozpětí to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::GetStatus](#getstatus)|Získá stav (platnosti) to `COleDateTimeSpan` objektu.|
|[COleDateTimeSpan::GetTotalDays](#gettotaldays)|Vrátí počet dní, to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::GetTotalHours](#gettotalhours)|Vrátí počet hodin, to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::GetTotalMinutes](#gettotalminutes)|Vrátí počet minut, to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::GetTotalSeconds](#gettotalseconds)|Vrátí počet sekund, to `COleDateTimeSpan` objekt představuje.|
|[COleDateTimeSpan::SetDateTimeSpan](#setdatetimespan)|Nastaví hodnotu tohoto `COleDateTimeSpan` objektu.|
|[COleDateTimeSpan::SetStatus](#setstatus)|Nastaví stav (platnosti) to `COleDateTimeSpan` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|||
|-|-|
|[operátor +, -](#operator_add_-)|Přidat odečíst a změnit zaregistrujte `COleDateTimeSpan` hodnoty.|
|[Operator +=-=](#operator_add_eq_-_eq)|Sčítání a odečítání `COleDateTimeSpan` hodnotu z této `COleDateTimeSpan` hodnotu.|
|[operátor =](#operator_eq)|Zkopíruje `COleDateTimeSpan` hodnotu.|
|[operátor ==, <, < =](#coledatetimespan_relational_operators)|Porovnat dva `COleDateTimeSpan` hodnoty.|
|[operátor double](#operator_double)|Převede `COleDateTimeSpan` hodnota, která se **double**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleDateTimeSpan::m_span](#m_span)|Obsahuje základní **double** to `COleDateTimeSpan` objektu.|
|[COleDateTimeSpan::m_status](#m_status)|Obsahuje stav tohoto `COleDateTimeSpan` objektu.|

## <a name="remarks"></a>Poznámky

`COleDateTimeSpan` nemá základní třídu.

A `COleDateTimeSpan` udržuje času ve dnech.

`COleDateTimeSpan` se používá s jeho třídě doprovodných prvků [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md). `COleDateTime` zapouzdřuje `DATE` datovým typem automatizace OLE. `COleDateTime` představuje absolutní časové hodnoty. Všechny `COleDateTime` výpočty zahrnují `COleDateTimeSpan` hodnoty. Vztah mezi tyto třídy je podobná té mezi [CTime](../../atl-mfc-shared/reference/ctime-class.md) a [ctimespan –](../../atl-mfc-shared/reference/ctimespan-class.md).

Další informace o `COleDateTime` a `COleDateTimeSpan` třídy, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** ATLComTime.h

##  <a name="coledatetimespan_relational_operators"></a>  Coledatetimespan – relační operátory

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
`COleDateTimeSpan` k porovnání.

### <a name="return-value"></a>Návratová hodnota

Tyto operátory porovnávají dvě hodnoty Datum/čas rozpětí a vrátí hodnotu, pokud je podmínka true. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  ATLASSERT dojde, pokud jeden z operandů je neplatný.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#25](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_1.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#26](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_2.cpp)]

##  <a name="coledatetimespan"></a>  COleDateTimeSpan::COleDateTimeSpan

Vytvoří `COleDateTimeSpan` objektu.

```
COleDateTimeSpan() throw();
COleDateTimeSpan(double dblSpanSrc) throw();
COleDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*dblSpanSrc*<br/>
Počet dní, které se mají zkopírovat do nové `COleDateTimeSpan` objektu.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Označení dne a času hodnot, které se mají zkopírovat do nové `COleDateTimeSpan` objektu.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory vytvořit nový `COleDateTimeSpan` objekty inicializovány na zadanou hodnotu. Následuje stručný popis každého z těchto konstruktorů:

- **() Coledatetimespan –** sestaví `COleDateTimeSpan` objekt je inicializován na hodnotu 0.

- **Coledatetimespan – (** `dblSpanSrc` **)** sestaví `COleDateTimeSpan` objekt z hodnoty s plovoucí desetinnou čárkou.

- **Coledatetimespan – (** `lDays` **,** `nHours` **,** `nMins` **,** `nSecs` **)**  Vytvoří `COleDateTimeSpan` objekt je inicializován na zadané číselné hodnoty.

Stav nového `COleDateTimeSpan` objekt je nastaven na platný.

Další informace o hranice pro `COleDateTimeSpan` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#14](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_3.cpp)]

##  <a name="format"></a>  COleDateTimeSpan::Format

Generuje formátovaný řetězec představující `COleDateTimeSpan` objektu.

```
CString Format(LPCTSTR pFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*<br/>
Formátování řetězců podobně jako `printf` formátovací řetězec. Formátování kódů předchází procento (`%`) podepsat, jsou nahrazeny odpovídajícím `COleDateTimeSpan` komponenty. Jiné znaky v řetězci formátování se zkopírují do vráceném řetězci beze změny. Hodnota a význam kódů formátování pro `Format` jsou uvedeny níže:

- **%H** hodin aktuálního dne

- **%M** minut do aktuální hodiny

- **%S** sekund do aktuální minuty

- **%%** Znak procent

Čtyři kódy výše uvedené jsou pouze kódy, které bude přijímat formátu.

-

*nID*<br/>
ID prostředku pro řetězec řízení formátu.

### <a name="return-value"></a>Návratová hodnota

A `CString` obsahující formátovanou hodnotu data/času rozpětí.

### <a name="remarks"></a>Poznámky

Volání těchto funkcí k vytvoření formátovaného reprezentace hodnoty časové období. Pokud se stav tohoto `COleDateTimeSpan` objekt má hodnotu null, vrácená hodnota je prázdný řetězec. Pokud je neplatný stav, vrácený řetězec je určená IDS_INVALID_DATETIMESPAN prostředek řetězce.

Následuje stručný popis formulářů pro tuto funkci:

**Format(** *pFormat* **)**<br/>
Tento formulář naformátuje hodnotu pomocí řetězce formátu, který obsahuje speciální formátovacích kódech, které jsou uvozená znakem procent (%), stejně jako v `printf`. Formátovací řetězec je předat jako parametr funkce.

**Formát (** *nID* **)**<br/>
Tento formulář naformátuje hodnotu pomocí řetězce formátu, který obsahuje speciální formátovacích kódech, které jsou uvozená znakem procent (%), stejně jako v `printf`. Formátovací řetězec je prostředek. ID prostředku tento řetězec je předán jako parametr.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#15](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_4.cpp)]

##  <a name="getdays"></a>  COleDateTimeSpan::GetDays

Načte část pro den z této hodnoty Datum/čas rozpětí.

```
LONG GetDays() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Část dne z této hodnoty Datum/čas rozpětí.

### <a name="remarks"></a>Poznámky

Vrácení hodnoty z této funkce rozsahu přibližně - 3,615,000 a 3,615,000.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [Gethours –](#gethours)

- [Getminutes –](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#16](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_5.cpp)]

##  <a name="gethours"></a>  COleDateTimeSpan::GetHours

Načte část pro hodinu z této hodnoty Datum/čas rozpětí.

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Části hodin této hodnoty Datum/čas rozpětí.

### <a name="remarks"></a>Poznámky

Návratové hodnoty z tohoto rozsahu funkce, mezi - 23 a 23.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Getminutes –](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#17](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_6.cpp)]

##  <a name="getminutes"></a>  COleDateTimeSpan::GetMinutes

Načte část pro minuty z této hodnoty Datum/čas rozpětí.

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Část minut této hodnoty Datum/čas rozpětí.

### <a name="remarks"></a>Poznámky

Návratové hodnoty z tohoto rozsahu funkce, mezi - 59 a 59.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Gethours –](#gethours)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#18](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_7.cpp)]

##  <a name="getseconds"></a>  COleDateTimeSpan::GetSeconds

Načte část pro sekundy z této hodnoty Datum/čas rozpětí.

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Část sekund této hodnoty Datum/čas rozpětí.

### <a name="remarks"></a>Poznámky

Návratové hodnoty z tohoto rozsahu funkce, mezi - 59 a 59.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Gethours –](#gethours)

- [Getminutes –](#getminutes)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#19](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_8.cpp)]

##  <a name="getstatus"></a>  COleDateTimeSpan::GetStatus

Získá stav (platnosti) to `COleDateTimeSpan` objektu.

```
DateTimeSpanStatus GetStatus() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Stav této `COleDateTimeSpan` hodnotu.

### <a name="remarks"></a>Poznámky

Návratová hodnota je definována `DateTimeSpanStatus` Výčtový typ, který je definován v rámci `COleDateTimeSpan` třídy.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
};
```

Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:

- `COleDateTimeSpan::valid` Označuje, že tento `COleDateTimeSpan` objektu je neplatný.

- `COleDateTimeSpan::invalid` Označuje, že tento `COleDateTimeSpan` objekt je neplatný; to znamená, jeho hodnota může být nesprávný.

- `COleDateTimeSpan::null` Označuje, že tento `COleDateTimeSpan` objekt má hodnotu null, to znamená, že byla zadána žádná hodnota pro tento objekt. (To je v tom smyslu databáze "mít žádnou hodnotu" na rozdíl od C++ NULL "null".)

Stav `COleDateTimeSpan` objekt není platný v následujících případech:

- Pokud tento objekt došlo přetečení nebo podtečení během přiřazení aritmetické operace, jmenovitě `+=` nebo `-=`.

- Pokud na tento objekt byl přiřazen neplatnou hodnotu.

- Pokud se stav tohoto objektu explicitně nastavit na neplatné použití `SetStatus`.

Další informace o operacích, které může nastavit stav na neplatný najdete v tématu [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) a [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

Další informace o hranice pro `COleDateTimeSpan` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="gettotaldays"></a>  COleDateTimeSpan::GetTotalDays

Tato hodnota datum/čas rozpětí dní vyjádřeny načte.

```
double GetTotalDays() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota datum/čas – značka span, dní vyjádřeny. I když je tato funkce prototypem vrátí typ double, vždy vrátí celočíselnou hodnotu.

### <a name="remarks"></a>Poznámky

Návratové hodnoty z této funkce rozsahu přibližně - 3.65e6 a 3.65e6.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Gethours –](#gethours)

- [Getminutes –](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#20](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_9.cpp)]

##  <a name="gettotalhours"></a>  COleDateTimeSpan::GetTotalHours

Načte tato hodnota datum/čas rozpětí vyjádřené v hodinách.

```
double GetTotalHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota datum/čas – značka span, vyjádřené v hodinách. I když je tato funkce prototypem vrátí typ double, vždy vrátí celočíselnou hodnotu.

### <a name="remarks"></a>Poznámky

Návratové hodnoty z této funkce rozsahu přibližně - 8.77e7 a 8.77e7.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Gethours –](#gethours)

- [Getminutes –](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetTotalDays](#gettotaldays).

##  <a name="gettotalminutes"></a>  COleDateTimeSpan::GetTotalMinutes

Načte tato hodnota datum/čas rozpětí vyjádřené v minutách.

```
double GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota datum/čas – značka span, vyjádřené v minutách. I když je tato funkce prototypem vrátí typ double, vždy vrátí celočíselnou hodnotu.

### <a name="remarks"></a>Poznámky

Návratové hodnoty z této funkce rozsahu přibližně - 5.26e9 a 5.26e9.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Gethours –](#gethours)

- [Getminutes –](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetTotalDays](#gettotaldays).

##  <a name="gettotalseconds"></a>  COleDateTimeSpan::GetTotalSeconds

Načte tato hodnota datum/čas – interval v sekundách.

```
double GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Tato hodnota datum/čas – značka span, v sekundách. I když je tato funkce prototypem vrátí typ double, vždy vrátí celočíselnou hodnotu.

### <a name="remarks"></a>Poznámky

Návratové hodnoty z této funkce v rozsahu mezi přibližně – 3.16e11 k 3.16e11.

Pro další funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Gethours –](#gethours)

- [Getminutes –](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetTotalDays](#gettotaldays).

##  <a name="m_span"></a>  COleDateTimeSpan::m_span

Základní **double** hodnota `COleDateTime` objektu.

```
double m_span;
```

### <a name="remarks"></a>Poznámky

Tato hodnota představuje datum nebo období ve dnech.

> [!CAUTION]
>  Změna hodnoty v **double** datový člen se změní hodnota tohoto `COleDateTimeSpan` objektu. Nezmění stav této `COleDateTimeSpan` objektu.

##  <a name="m_status"></a>  COleDateTimeSpan::m_status

Typ pro tento datový člen je výčtového typu `DateTimeSpanStatus`, který je definován v rámci `COleDateTimeSpan` třídy.

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

Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:

- `COleDateTimeSpan::valid` Označuje, že tento `COleDateTimeSpan` objektu je neplatný.

- `COleDateTimeSpan::invalid` Označuje, že tento `COleDateTimeSpan` objekt je neplatný; to znamená, jeho hodnota může být nesprávný.

- `COleDateTimeSpan::null` Označuje, že tento `COleDateTimeSpan` objekt má hodnotu null, to znamená, že byla zadána žádná hodnota pro tento objekt. (To je v tom smyslu databáze "mít žádnou hodnotu" na rozdíl od C++ NULL "null".)

Stav `COleDateTimeSpan` objekt není platný v následujících případech:

- Pokud tento objekt došlo přetečení nebo podtečení během přiřazení aritmetické operace, jmenovitě `+=` nebo `-=`.

- Pokud na tento objekt byl přiřazen neplatnou hodnotu.

- Pokud se stav tohoto objektu explicitně nastavit na neplatné použití [SetStatus](#setstatus).

Další informace o operacích, které může nastavit stav na neplatný najdete v tématu [COleDateTimeSpan::operator +, -](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_-) a [COleDateTimeSpan::operator +=,-=](../../atl-mfc-shared/reference/coledatetime-class.md#operator_add_eq_-_eq).

> [!CAUTION]
>  Pro pokročilé situacích programování je tomuto datovému členu. Používejte vložené členské funkce [GetStatus](#getstatus) a [SetStatus](#setstatus). Zobrazit `SetStatus` pro další upozornění týkající se explicitním nastavením tomuto datovému členu.

Další informace o hranice pro `COleDateTimeSpan` hodnoty, najdete v článku [datum a čas: Podpora automatizace](../../atl-mfc-shared/date-and-time-automation-support.md).

##  <a name="operator_eq"></a>  COleDateTimeSpan::operator =

Zkopíruje `COleDateTimeSpan` hodnotu.

```
COleDateTimeSpan& operator=(double dblSpanSrc) throw();
```

### <a name="remarks"></a>Poznámky

Operátoru přiřazení. přetížení zkopíruje zdrojová hodnota datum/čas rozpětí do této `COleDateTimeSpan` objektu.

##  <a name="operator_add_-"></a>  COleDateTimeSpan::operator +, -

Přidat odečíst a změnit zaregistrujte `COleDateTimeSpan` hodnoty.

```
COleDateTimeSpan operator+(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-(const COleDateTimeSpan& dateSpan) const throw();
COleDateTimeSpan operator-() const throw();
```

### <a name="remarks"></a>Poznámky

První dva operátory umožňují operátorů sčítání a odečítání hodnoty Datum/čas rozpětí. Třetí umožňuje změnit na znaménko hodnoty Datum/čas rozpětí.

Pokud platí některá z operandů s hodnotou null, výsledný stav `COleDateTimeSpan` hodnotu null.

Pokud jeden z operandů je neplatný a druhá nemá hodnotu null, výsledný stav `COleDateTimeSpan` hodnota není platná.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#23](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_10.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  COleDateTimeSpan::operator +=-=

Sčítání a odečítání `COleDateTimeSpan` hodnotu z této `COleDateTimeSpan` hodnotu.

```
COleDateTimeSpan& operator+=(const COleDateTimeSpan dateSpan) throw();
COleDateTimeSpan& operator-=(const COleDateTimeSpan dateSpan) throw();
```

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují operátorů sčítání a odečítání hodnoty Datum/čas rozpětí z tohoto `COleDateTimeSpan` objektu. Pokud platí některá z operandů s hodnotou null, výsledný stav `COleDateTimeSpan` hodnotu null.

Pokud jeden z operandů je neplatný a druhá nemá hodnotu null, výsledný stav `COleDateTimeSpan` hodnota není platná.

Další informace o stavu platný, neplatné a null hodnoty, najdete v článku [m_status](#m_status) členské proměnné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#24](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_11.cpp)]

##  <a name="operator_double"></a>  COleDateTimeSpan::operator double

Převede `COleDateTimeSpan` hodnota, která se **double**.

```
operator double() const throw();
```

### <a name="remarks"></a>Poznámky

Tento operátor vrátí hodnotu tohoto `COleDateTimeSpan` hodnotu jako číslo s plovoucí desetinnou čárkou dnů.

##  <a name="setdatetimespan"></a>  COleDateTimeSpan::SetDateTimeSpan

Nastaví hodnotu z této hodnoty Datum/čas rozpětí.

```
void SetDateTimeSpan(LONG lDays, int nHours, int nMins, int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Označení rozsahu data a časový rozsah hodnot, které se mají zkopírovat do tohoto `COleDateTimeSpan` objektu.

### <a name="remarks"></a>Poznámky

Pro funkce, které se dotazují hodnotu `COleDateTimeSpan` objektu, najdete v následujících členské funkce:

- [GetDays](#getdays)

- [Gethours –](#gethours)

- [Getminutes –](#getminutes)

- [GetSeconds](#getseconds)

- [GetTotalDays](#gettotaldays)

- [GetTotalHours](#gettotalhours)

- [GetTotalMinutes](#gettotalminutes)

- [GetTotalSeconds](#gettotalseconds)

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#21](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_12.cpp)]

##  <a name="setstatus"></a>  COleDateTimeSpan::SetStatus

Nastaví stav (platnosti) to `COleDateTimeSpan` objektu.

```
void SetStatus(DateTimeSpanStatus status) throw();
```

### <a name="parameters"></a>Parametry

*status*<br/>
Nová hodnota pro tento stav `COleDateTimeSpan` objektu.

### <a name="remarks"></a>Poznámky

*Stav* hodnota parametru je definována `DateTimeSpanStatus` Výčtový typ, který je definován v rámci `COleDateTimeSpan` třídy.

```
enum DateTimeSpanStatus{
   valid = 0,
   invalid = 1,
   null = 2,
   };
```

Stručný popis tyto hodnoty stavu najdete v následujícím seznamu:

- `COleDateTimeSpan::valid` Označuje, že tento `COleDateTimeSpan` objektu je neplatný.

- `COleDateTimeSpan::invalid` Označuje, že tento `COleDateTimeSpan` objekt je neplatný; to znamená, jeho hodnota může být nesprávný.

- `COleDateTimeSpan::null` Označuje, že tento `COleDateTimeSpan` objekt má hodnotu null, to znamená, že byla zadána žádná hodnota pro tento objekt. (To je v tom smyslu databáze "mít žádnou hodnotu" na rozdíl od C++ NULL "null".)

   > [!CAUTION]
   > Tato funkce je pro pokročilé situacích programování. Tato funkce nezmění data v tomto objektu. Nejčastěji se používají se nastavit stav na **null** nebo **neplatný**. Všimněte si, že operátor přiřazení ( [operátoru =](#eq)) a [SetDateTimeSpan](#setdatetimespan) nastavit stav objektu podle hodnoty, které zdroj.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#22](../../atl-mfc-shared/codesnippet/cpp/coledatetimespan-class_13.cpp)]

## <a name="see-also"></a>Viz také:

[COleDateTime – třída](../../atl-mfc-shared/reference/coledatetime-class.md)<br/>
[CTime – třída](../../atl-mfc-shared/reference/ctime-class.md)<br/>
[CTimeSpan – třída](../../atl-mfc-shared/reference/ctimespan-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
