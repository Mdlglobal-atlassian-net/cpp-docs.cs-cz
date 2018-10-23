---
title: Ctimespan – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTimeSpan
- ATLTIME/ATL::CTimeSpan
- ATLTIME/ATL::CTimeSpan::CTimeSpan
- ATLTIME/ATL::CTimeSpan::Format
- ATLTIME/ATL::CTimeSpan::GetDays
- ATLTIME/ATL::CTimeSpan::GetHours
- ATLTIME/ATL::CTimeSpan::GetMinutes
- ATLTIME/ATL::CTimeSpan::GetSeconds
- ATLTIME/ATL::CTimeSpan::GetTimeSpan
- ATLTIME/ATL::CTimeSpan::GetTotalHours
- ATLTIME/ATL::CTimeSpan::GetTotalMinutes
- ATLTIME/ATL::CTimeSpan::GetTotalSeconds
- ATLTIME/ATL::CTimeSpan::Serialize64
dev_langs:
- C++
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32e6599fa19c23751beaf3545696a90a2d117248
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49809080"
---
# <a name="ctimespan-class"></a>Ctimespan – třída

Časový úsek, který interně uložená jako počet sekund v časové období.

## <a name="syntax"></a>Syntaxe

```
class CTimeSpan
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Vytvoří `CTimeSpan` objekty různými způsoby.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CTimeSpan::Format](#format)|Převede `CTimeSpan` do formátovaného řetězce.|
|[CTimeSpan::GetDays](#getdays)|Vrátí hodnotu, která představuje počet dnů dokončení v tomto `CTimeSpan`.|
|[CTimeSpan::GetHours](#gethours)|Vrátí hodnotu, která představuje počet hodin aktuálního dne (až 23 -23).|
|[CTimeSpan::GetMinutes](#getminutes)|Vrátí hodnotu, která představuje počet minut do aktuální hodiny (-59 až 59).|
|[CTimeSpan::GetSeconds](#getseconds)|Vrátí hodnotu, která představuje počet sekund do aktuální minuty (-59 až 59).|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Vrátí hodnotu `CTimeSpan` objektu.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Vrátí hodnotu, která představuje celkový počet hodin dokončeno v tomto `CTimeSpan`.|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Vrátí hodnotu, která představuje celkový počet kompletní minutách v tomto `CTimeSpan`.|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Vrátí hodnotu, která představuje celkový počet sekund dokončena v tomto `CTimeSpan`.|
|[CTimeSpan::Serialize64](#serialize64)|Serializuje data do nebo z archivu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[Operator + –](#operator_add_-)|Přidá a odečte `CTimeSpan` objekty.|
|[+= – operátor-=](#operator_add_eq_-_eq)|Přidá a odečte `CTimeSpan` objektů do a z tohoto `CTimeSpan`.|
|[Operator == < atd.](#ctimespan_comparison_operators)|Porovná dvě relativní časové hodnoty.|

## <a name="remarks"></a>Poznámky

`CTimeSpan` nemá základní třídu.

`CTimeSpan` Funkce převádějí sekund různé kombinace dny, hodiny, minuty a sekundy.

`CTimeSpan` Objekt uložen v **__time64_t –** struktury, což je 8 bajtů.

Třídě doprovodných prvků [CTime](../../atl-mfc-shared/reference/ctime-class.md), představuje absolutní čas.

`CTime` a `CTimeSpan` třídy nejsou určeny pro odvození. Vzhledem k tomu, že neexistují žádné virtuální funkce, velikost obou `CTime` a `CTimeSpan` objekty je přesně 8 bajtů. Většina členské funkce jsou vložené.

Další informace o používání `CTimeSpan`, najdete v článcích [datum a čas](../../atl-mfc-shared/date-and-time.md), a [Správa času](../../c-runtime-library/time-management.md) v *Run-Time Library Reference*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

##  <a name="ctimespan_comparison_operators"></a>  Ctimespan – relační operátory

Operátory porovnání.

```
bool operator==(CTimeSpan span) const throw();
bool operator!=(CTimeSpan span) const throw();
bool operator<(CTimeSpan span) const throw();
bool operator>(CTimeSpan span) const throw();
bool operator<=(CTimeSpan span) const throw();
bool operator>=(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Tyto operátory porovnávají dva relativní časové hodnoty. Vrátí hodnotu TRUE Pokud je podmínka true. v opačném případě FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

##  <a name="ctimespan"></a>  CTimeSpan::CTimeSpan

Vytvoří `CTimeSpan` objekty různými způsoby.

```
CTimeSpan() throw();
CTimeSpan(__time64_t time) throw();

CTimeSpan(
    LONG lDays,
    int nHours,
    int nMins,
    int nSecs) throw();
```

### <a name="parameters"></a>Parametry

*timeSpanSrc*<br/>
A `CTimeSpan` objekt, který již existuje.

*čas*<br/>
A **__time64_t –** časovou hodnotu, což je počet sekund v časové období.

*lDays*, *nHours*, *nMins*, *nSecs*<br/>
Dny, hodiny minuty a sekundy, v uvedeném pořadí.

### <a name="remarks"></a>Poznámky

Tyto konstruktory vytvořte nový `CTimeSpan` objekt je inicializován s relativní určený čas. Níže je popsána jednotlivých konstruktor:

- `CTimeSpan( );` Vytvoří neinicializované `CTimeSpan` objektu.

- `CTimeSpan( const CTimeSpan& );` Vytvoří `CTimeSpan` objektu z jiného `CTimeSpan` hodnotu.

- `CTimeSpan( __time64_t );` Vytvoří `CTimeSpan` objektu z **__time64_t –** typu.

- `CTimeSpan( LONG, int, int, int );` Vytvoří `CTimeSpan` objekt z komponent pomocí jednotlivých komponent omezen na tyto rozsahy:

   |Součást|Rozsah|
   |---------------|-----------|
   |*lDays*|0 – 25 000 (přibližně)|
   |*nHours*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Všimněte si, že ladicí verze knihovny Microsoft Foundation Class vyhodnotí, pokud jeden nebo více součástí hodiny je mimo rozsah. Je vaší odpovědností, abyste ověřte argumenty před voláním.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

##  <a name="format"></a>  CTimeSpan::Format

Generuje formátovaný řetězec, který odpovídá tomuto `CTimeSpan`.

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*, *pszFormat*<br/>
Formátování řetězců podobně jako `printf` formátovací řetězec. Formátování kódů předchází procento (`%`) podepsat, jsou nahrazeny odpovídajícím `CTimeSpan` komponenty. Jiné znaky v řetězci formátování se zkopírují do vráceném řetězci beze změny. Hodnota a význam kódů formátování pro `Format` jsou uvedeny níže:

- **%D** celkový počet dní v tomto `CTimeSpan`

- **%H** hodin aktuálního dne

- **%M** minut do aktuální hodiny

- **%S** sekund do aktuální minuty

- **%%** Znak procent

*nID*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

A `CString` objekt, který obsahuje formátovaný čas.

### <a name="remarks"></a>Poznámky

Ladicí verze knihovny kontroluje formátovacích kódech a vyhodnotí, pokud kód není v seznamu výše.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

##  <a name="getdays"></a>  CTimeSpan::GetDays

Vrátí hodnotu, která představuje počet dnů dokončení v tomto `CTimeSpan`.

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet dní, dokončení 24 hodin v časové období. Tato hodnota může být záporná, pokud je záporný časový interval.

### <a name="remarks"></a>Poznámky

Všimněte si, že letní čas může způsobit `GetDays` potenciálně překvapivé výsledek. Například když letního času je v platnosti, `GetDays` hlásí počet dnů mezi 1. dubna do 1. května jako 29, 30, protože jeden den v dubnu na trh se zkrátila o hodinu a proto nepočítají jako celý den.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

##  <a name="gethours"></a>  CTimeSpan::GetHours

Vrátí hodnotu, která představuje počet hodin aktuálního dne (až 23 -23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet hodin po aktuálním dni. Jsou v rozsahu -23 až 23.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

##  <a name="getminutes"></a>  CTimeSpan::GetMinutes

Vrátí hodnotu, která představuje počet minut do aktuální hodiny (-59 až 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet minut do aktuální hodiny. Jsou v rozsahu -59 do 59.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetHours](#gethours).

##  <a name="getseconds"></a>  CTimeSpan::GetSeconds

Vrátí hodnotu, která představuje počet sekund do aktuální minuty (-59 až 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet sekund do aktuální minuty. Jsou v rozsahu -59 do 59.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetHours](#gethours).

##  <a name="gettimespan"></a>  CTimeSpan::GetTimeSpan

Vrátí hodnotu `CTimeSpan` objektu.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální hodnotu `CTimeSpan` objektu.

##  <a name="gettotalhours"></a>  CTimeSpan::GetTotalHours

Vrátí hodnotu, která představuje celkový počet hodin dokončeno v tomto `CTimeSpan`.

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celkový počet hodin dokončeno v tomto `CTimeSpan`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

##  <a name="gettotalminutes"></a>  CTimeSpan::GetTotalMinutes

Vrátí hodnotu, která představuje celkový počet kompletní minutách v tomto `CTimeSpan`.

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celkový počet minut na dokončení v tomto `CTimeSpan`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetTotalHours](#gettotalhours).

##  <a name="gettotalseconds"></a>  CTimeSpan::GetTotalSeconds

Vrátí hodnotu, která představuje celkový počet sekund dokončena v tomto `CTimeSpan`.

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celkový počet sekund dokončena v tomto `CTimeSpan`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetTotalHours](#gettotalhours).

##  <a name="operator_add_-"></a>  CTimeSpan::operator +, -

Přidá a odečte `CTimeSpan` objekty.

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
Hodnota k přidání do `CTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

A `CTimeSpan` objekt představující výsledek operace.

### <a name="remarks"></a>Poznámky

Tyto dva operátory umožňují operátorů sčítání a odečítání `CTimeSpan` objektů do a od sebe navzájem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

##  <a name="operator_add_eq_-_eq"></a>  CTimeSpan::operator +=-=

Přidá a odečte `CTimeSpan` objektů do a z tohoto `CTimeSpan`.

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
Hodnota k přidání do `CTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTimeSpan` objektu.

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují operátorů sčítání a odečítání `CTimeSpan` objektů do a z tohoto `CTimeSpan`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

##  <a name="serialize64"></a>  CTimeSpan::Serialize64

> [!NOTE]
>  Tato metoda je pouze k dispozici v projektech knihovny MFC.

Serializuje data přidružená k členské proměnné do nebo z archivu.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
`CArchive` Objekt, který chcete aktualizovat.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CArchive` objektu.

## <a name="see-also"></a>Viz také

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

