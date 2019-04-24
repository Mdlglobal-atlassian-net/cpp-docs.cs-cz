---
title: Cfiletimespan – třída
ms.date: 10/18/2018
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
ms.openlocfilehash: 001e6ddc78a41e118949e9b750b78609f3ff9e92
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235299"
---
# <a name="cfiletimespan-class"></a>Cfiletimespan – třída

Tato třída poskytuje metody pro správu relativní hodnoty data a času přidružených k souboru.

## <a name="syntax"></a>Syntaxe

```
class CFileTimeSpan
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFileTimeSpan::GetTimeSpan](#gettimespan)|Volejte tuto metodu za účelem načtení časový rozsah od `CFileTimeSpan` objektu.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Volání této metody nastavte časový rozsah `CFileTimeSpan` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFileTimeSpan::operator-](#operator_-)|Provede odčítání `CFileTimeSpan` objektu.|
|[CFileTimeSpan::operator! =](#operator_neq)|Porovná dva `CFileTimeSpan` objekty nerovnost.|
|[CFileTimeSpan::operator +](#operator_add)|Provede přidání `CFileTimeSpan` objektu.|
|[CFileTimeSpan::operator +=](#operator_add_eq)|Provede přidání `CFileTimeSpan` objektu a výsledek přiřaďte do aktuálního objektu.|
|[CFileTimeSpan::operator &lt;](#operator_lt)|Porovná dva `CFileTimeSpan` objekty k určení menší než.|
|[CFileTimeSpan::operator &lt;=](#operator_lt_eq)|Porovná dva `CFileTimeSpan` objekty k určení rovnosti, nebo menší.|
|[CFileTimeSpan::operator =](#operator_eq)|Operátor přiřazení.|
|[CFileTimeSpan::operator-=](#operator_-_eq)|Provede odčítání `CFileTimeSpan` objektu a výsledek přiřaďte do aktuálního objektu.|
|[CFileTimeSpan::operator ==](#operator_eq_eq)|Porovná dva `CFileTimeSpan` objekty pro rovnost.|
|[CFileTimeSpan::operator &gt;](#operator_gt)|Porovná dva `CFileTimeSpan` objekty k určení větší.|
|[CFileTimeSpan::operator &gt;=](#operator_gt_eq)|Porovná dva `CFileTimeSpan` objekty k určení rovnosti, nebo větší.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro správu relativní období dobu vyskytující se při provádění operací, kdy bylo vytvořené, posledního přístupu k nebo poslední změny souboru. Metody této třídy jsou často používána ve spojení s [cfiletime – třída](../../atl-mfc-shared/reference/cfiletime-class.md) objekty.

## <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime::Millisecond](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime.h

##  <a name="cfiletimespan"></a>  CFileTimeSpan::CFileTimeSpan

Konstruktor

```
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
Existující objekt `CFileTimeSpan`.

*nSpan*<br/>
Určitou dobu v milisekundách.

### <a name="remarks"></a>Poznámky

`CFileTimeSpan` Objektu lze vytvořit pomocí existující `CFileTimeSpan` objektu nebo vyjádřené jako hodnotu 64-bit. Výchozí konstruktor nastaví časový interval na hodnotu 0.

##  <a name="gettimespan"></a>  CFileTimeSpan::GetTimeSpan

Volejte tuto metodu za účelem načtení časový rozsah od `CFileTimeSpan` objektu.

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí časový interval v milisekundách.

##  <a name="operator_-"></a>  CFileTimeSpan::operator-

Provede odčítání `CFileTimeSpan` objektu.

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTimeSpan` objekt představující výsledek rozdíl mezi dvěma časové úseky.

##  <a name="operator_neq"></a>  CFileTimeSpan::operator! =

Porovná dva `CFileTimeSpan` objekty nerovnost.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud položka, který se porovnává se nerovná `CFileTimeSpan` objektu; jinak hodnota FALSE.

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

Provede přidání `CFileTimeSpan` objektu.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTimeSpan` objekt, který obsahuje součet dvou čas zahrnuje.

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Provede přidání `CFileTimeSpan` objektu a přiřazuje výsledek aktuálního objektu.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt, který obsahuje součet dvou čas zahrnuje.

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Porovná dva `CFileTimeSpan` objekty k určení menší než.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt menší (to znamená, představuje kratší časové období) než druhé, jinak hodnota FALSE.

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Porovná dva `CFileTimeSpan` objekty k určení rovnosti, nebo menší.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší než (to znamená, představuje kratší časové období) nebo roven druhému, jinak hodnota FALSE.

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

Operátor přiřazení.

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objektu.

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator-=

Provede odčítání `CFileTimeSpan` objektu a přiřazuje výsledek aktuálního objektu.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objektu.

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Porovná dva `CFileTimeSpan` objekty pro rovnost.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou objekty stejné; jinak hodnota FALSE.

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Porovná dva `CFileTimeSpan` objekty k určení větší.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt větší než (to znamená, představuje delší časové období) než druhé, jinak hodnota FALSE.

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Porovná dva `CFileTimeSpan` objekty k určení rovnosti, nebo větší.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt větší než (to znamená, představuje delší časové období) nebo roven druhému, jinak hodnota FALSE.

##  <a name="settimespan"></a>  CFileTimeSpan::SetTimeSpan

Volání této metody nastavte časový rozsah `CFileTimeSpan` objektu.

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan*<br/>
Nová hodnota pro časový interval v milisekundách.

## <a name="see-also"></a>Viz také:

[FILETIME –](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime – třída](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
