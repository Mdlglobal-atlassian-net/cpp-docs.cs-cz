---
title: CTimeSpan – třída
ms.date: 10/18/2018
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
helpviewer_keywords:
- elapsed time, CTimeSpan object
- timespan
- time span
- CTimeSpan class
- shared classes, CTimeSpan
- time, elapsed
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
ms.openlocfilehash: 14aa5eb52e2c631a92e40ae7053c566284e00e57
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317506"
---
# <a name="ctimespan-class"></a>CTimeSpan – třída

Množství času, který je interně uložen jako počet sekund v časovém rozpětí.

## <a name="syntax"></a>Syntaxe

```
class CTimeSpan
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CTimeSpan::CTimeSpan](#ctimespan)|Vytváří `CTimeSpan` objekty různými způsoby.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CTimeSpan::Formát](#format)|Převede `CTimeSpan` na formátovaný řetězec.|
|[CTimeSpan::GetDays](#getdays)|Vrátí hodnotu, která představuje počet `CTimeSpan`dnů dokončení v tomto .|
|[CTimeSpan::GetHours](#gethours)|Vrátí hodnotu, která představuje počet hodin v aktuálním dni (-23 až 23).|
|[CTimeSpan::GetMinutes](#getminutes)|Vrátí hodnotu, která představuje počet minut v aktuální hodině (-59 až 59).|
|[CTimeSpan::GetSeconds](#getseconds)|Vrátí hodnotu, která představuje počet sekund v aktuální minutě (-59 až 59).|
|[CTimeSpan::GetTimeSpan](#gettimespan)|Vrátí hodnotu `CTimeSpan` objektu.|
|[CTimeSpan::GetTotalHours](#gettotalhours)|Vrátí hodnotu, která představuje celkový počet `CTimeSpan`hodin dokončení v tomto .|
|[CTimeSpan::GetTotalMinutes](#gettotalminutes)|Vrátí hodnotu, která představuje celkový počet `CTimeSpan`minut dokončení v tomto .|
|[CTimeSpan::GetTotalSeconds](#gettotalseconds)|Vrátí hodnotu, která představuje celkový počet `CTimeSpan`celých sekund v tomto .|
|[CTimeSpan::Serialize64](#serialize64)|Serializuje data do nebo z archivu.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operátor + -](#operator_add_-)|Přidá a odečte objekty. `CTimeSpan`|
|[operátor += -=](#operator_add_eq_-_eq)|Přidá a odečte `CTimeSpan` objekt a `CTimeSpan`od tohoto .|
|[operátor == < atd.](#ctimespan_comparison_operators)|Porovná dvě relativní časové hodnoty.|

## <a name="remarks"></a>Poznámky

`CTimeSpan`nemá základní třídu.

`CTimeSpan`funkce převádějí sekundy na různé kombinace dnů, hodin, minut a sekund.

Objekt `CTimeSpan` je uložen v **__time64_t** struktury, což je 8 bajtů.

Doprovodná třída [CTime](../../atl-mfc-shared/reference/ctime-class.md)představuje absolutní čas.

`CTime` Třídy `CTimeSpan` a nejsou určeny pro odvození. Vzhledem k tomu, že neexistují `CTime` `CTimeSpan` žádné virtuální funkce, velikost obou a objektů je přesně 8 bajtů. Většina členských funkcí je včleněná.

Další informace o `CTimeSpan`použití naleznete v článcích [Datum a čas](../../atl-mfc-shared/date-and-time.md)a Správa [času](../../c-runtime-library/time-management.md) v *referenční příručce knihovny za běhu*.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

## <a name="ctimespan-comparison-operators"></a><a name="ctimespan_comparison_operators"></a>Operátory porovnání CTimeSpan

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

*Span*<br/>
Objekt k porovnání

### <a name="return-value"></a>Návratová hodnota

Tyto operátory porovnat dvě relativní časové hodnoty. Vrátí hodnotu PRAVDA, pokud je podmínka pravdivá; jinak FALSE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#169](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_1.cpp)]

## <a name="ctimespanctimespan"></a><a name="ctimespan"></a>CTimeSpan::CTimeSpan

Vytváří `CTimeSpan` objekty různými způsoby.

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
Objekt, `CTimeSpan` který již existuje.

*Čas*<br/>
Hodnota **__time64_t** času, což je počet sekund v časovém rozpětí.

*lDny*, *nHodiny*, *nMins*, *nSecs*<br/>
Dny, hodiny, minuty a sekundy.

### <a name="remarks"></a>Poznámky

Všechny tyto konstruktory `CTimeSpan` vytvořit nový objekt inicializován s zadaným relativní čas. Každý konstruktor je popsán níže:

- `CTimeSpan( );`Vytvoří neinicializovaný `CTimeSpan` objekt.

- `CTimeSpan( const CTimeSpan& );`Vytvoří `CTimeSpan` objekt z `CTimeSpan` jiné hodnoty.

- `CTimeSpan( __time64_t );`Vytvoří `CTimeSpan` objekt z **typu __time64_t.**

- `CTimeSpan( LONG, int, int, int );`Vytvoří `CTimeSpan` objekt z komponent s každou součástí omezena na následující oblasti:

   |Komponenta|Rozsah|
   |---------------|-----------|
   |*lDny*|0-25 000 (přibližně)|
   |*nHodiny*|0-23|
   |*nMins*|0-59|
   |*nSecs*|0-59|

Všimněte si, že ladicí verze knihovny tříd Microsoft Foundation uplatňuje, pokud je jedna nebo více součástí denního dne mimo rozsah. Je vaší odpovědností ověřit argumenty před voláním.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#162](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_2.cpp)]

## <a name="ctimespanformat"></a><a name="format"></a>CTimeSpan::Formát

Generuje formátovaný řetězec, který odpovídá `CTimeSpan`tomuto .

```
CString Format(LPCSTR pFormat) const;
CString Format(LPCTSTR pszFormat) const;
CString Format(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*pFormat*, *pszFormat*<br/>
Formátovací řetězec podobný řetězci `printf` formátování. Kódy formátování, před nimiž`%`je podepsáno procento ( `CTimeSpan` ) , jsou nahrazeny odpovídající komponentou. Ostatní znaky ve formátovacím řetězci jsou zkopírovány beze změny do vráceného řetězce. Hodnota a význam formátovacích kódů pro jsou uvedeny `Format` níže:

- **%D** Celkový počet dní v tomto`CTimeSpan`

- **%H** Hodiny v aktuálním dni

- **%M** Minuty v aktuální hodině

- **%S** Sekundy v aktuální minutě

- **%%** Znak procenta

*Nid*<br/>
ID řetězce, který identifikuje tento formát.

### <a name="return-value"></a>Návratová hodnota

Objekt, `CString` který obsahuje formátovaný čas.

### <a name="remarks"></a>Poznámky

Ladicí verze knihovny zkontroluje kódy formátování a uplatní, pokud kód není ve výše uvedeném seznamu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#163](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_3.cpp)]

## <a name="ctimespangetdays"></a><a name="getdays"></a>CTimeSpan::GetDays

Vrátí hodnotu, která představuje počet `CTimeSpan`dnů dokončení v tomto .

```
LONGLONG GetDays() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet dokončených 24 hodin v časovém rozpětí. Tato hodnota může být záporná, pokud je časové rozpětí záporné.

### <a name="remarks"></a>Poznámky

Všimněte si, že `GetDays` letní čas může způsobit vrácení potenciálně překvapivého výsledku. Například při letního časově `GetDays` rozvaděčje, hlásí počet dní mezi 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#164](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_4.cpp)]

## <a name="ctimespangethours"></a><a name="gethours"></a>CTimeSpan::GetHours

Vrátí hodnotu, která představuje počet hodin v aktuálním dni (-23 až 23).

```
LONG GetHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet hodin v aktuálním dni. Rozsah je -23 až 23.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#165](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_5.cpp)]

## <a name="ctimespangetminutes"></a><a name="getminutes"></a>CTimeSpan::GetMinutes

Vrátí hodnotu, která představuje počet minut v aktuální hodině (-59 až 59).

```
LONG GetMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet minut v aktuální hodině. Rozsah je -59 až 59.

### <a name="example"></a>Příklad

Viz příklad pro [GetHours](#gethours).

## <a name="ctimespangetseconds"></a><a name="getseconds"></a>CTimeSpan::GetSeconds

Vrátí hodnotu, která představuje počet sekund v aktuální minutě (-59 až 59).

```
LONG GetSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet sekund v aktuální minutě. Rozsah je -59 až 59.

### <a name="example"></a>Příklad

Viz příklad pro [GetHours](#gethours).

## <a name="ctimespangettimespan"></a><a name="gettimespan"></a>CTimeSpan::GetTimeSpan

Vrátí hodnotu `CTimeSpan` objektu.

```
__ time64_t GetTimeSpan() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí aktuální hodnotu `CTimeSpan` objektu.

## <a name="ctimespangettotalhours"></a><a name="gettotalhours"></a>CTimeSpan::GetTotalHours

Vrátí hodnotu, která představuje celkový počet `CTimeSpan`hodin dokončení v tomto .

```
LONGLONG GetTotalHours() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celkový počet hodin dokončení `CTimeSpan`v tomto .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#166](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_6.cpp)]

## <a name="ctimespangettotalminutes"></a><a name="gettotalminutes"></a>CTimeSpan::GetTotalMinutes

Vrátí hodnotu, která představuje celkový počet `CTimeSpan`minut dokončení v tomto .

```
LONGLONG GetTotalMinutes() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celkový počet minut dokončení `CTimeSpan`v tomto .

### <a name="example"></a>Příklad

Viz příklad [gettotalhours](#gettotalhours).

## <a name="ctimespangettotalseconds"></a><a name="gettotalseconds"></a>CTimeSpan::GetTotalSeconds

Vrátí hodnotu, která představuje celkový počet `CTimeSpan`celých sekund v tomto .

```
LONGLONG GetTotalSeconds() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí celkový počet celých `CTimeSpan`sekund v tomto .

### <a name="example"></a>Příklad

Viz příklad [gettotalhours](#gettotalhours).

## <a name="ctimespanoperator---"></a><a name="operator_add_-"></a>CTimeSpan::operátor +, -

Přidá a odečte objekty. `CTimeSpan`

```
CTimeSpan operator+(CTimeSpan span) const throw();
CTimeSpan operator-(CTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Hodnota, kterou chcete `CTimeSpan` přidat k objektu.

### <a name="return-value"></a>Návratová hodnota

Objekt `CTimeSpan` představující výsledek operace.

### <a name="remarks"></a>Poznámky

Tyto dva operátory umožňují přidávat `CTimeSpan` a odečítat objekty mezi sebou a od sebe navzájem.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#167](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_7.cpp)]

## <a name="ctimespanoperator---"></a><a name="operator_add_eq_-_eq"></a>CTimeSpan::operátor +=, -=

Přidá a odečte `CTimeSpan` objekt a `CTimeSpan`od tohoto .

```
CTimeSpan& operator+=(CTimeSpan span) throw();
CTimeSpan& operator-=(CTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*Span*<br/>
Hodnota, kterou chcete `CTimeSpan` přidat k objektu.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CTimeSpan` objekt.

### <a name="remarks"></a>Poznámky

Tyto operátory umožňují přidat a `CTimeSpan` odečíst objekt `CTimeSpan`a od tohoto .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATLMFC_Utilities#168](../../atl-mfc-shared/codesnippet/cpp/ctimespan-class_8.cpp)]

## <a name="ctimespanserialize64"></a><a name="serialize64"></a>CTimeSpan::Serialize64

> [!NOTE]
> Tato metoda je k dispozici pouze v projektech knihovny MFC.

Serializuje data přidružená k členské proměnné do nebo z archivu.

```
CArchive& Serialize64(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Objekt, `CArchive` který chcete aktualizovat.

### <a name="return-value"></a>Návratová hodnota

Aktualizovaný `CArchive` objekt.

## <a name="see-also"></a>Viz také

[asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)<br/>
[_ftime, _ftime32, _ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy KNIHOVNY ATL/Knihovny MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
