---
title: Cfiletimespan – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::CFileTimeSpan
- ATLTIME/ATL::CFileTimeSpan::GetTimeSpan
- ATLTIME/ATL::CFileTimeSpan::SetTimeSpan
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CFileTimeSpan
- CFileTimeSpan class
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27be228c735b667d76f1dc70d9ae36f4229acd01
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808963"
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

*značka span*<br/>
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

*značka span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTimeSpan` objekt představující výsledek rozdíl mezi dvěma časové úseky.

##  <a name="operator_neq"></a>  CFileTimeSpan::operator! =

Porovná dva `CFileTimeSpan` objekty nerovnost.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud položka, který se porovnává se nerovná `CFileTimeSpan` objektu; jinak hodnota FALSE.

##  <a name="operator_add"></a>  CFileTimeSpan::operator +

Provede přidání `CFileTimeSpan` objektu.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí `CFileTimeSpan` objekt, který obsahuje součet dvou čas zahrnuje.

##  <a name="operator_add_eq"></a>  CFileTimeSpan::operator +=

Provede přidání `CFileTimeSpan` objektu a přiřazuje výsledek aktuálního objektu.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt, který obsahuje součet dvou čas zahrnuje.

##  <a name="operator_lt"></a>  CFileTimeSpan::operator &lt;

Porovná dva `CFileTimeSpan` objekty k určení menší než.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt menší (to znamená, představuje kratší časové období) než druhé, jinak hodnota FALSE.

##  <a name="operator_lt_eq"></a>  CFileTimeSpan::operator &lt;=

Porovná dva `CFileTimeSpan` objekty k určení rovnosti, nebo menší.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud je první objekt menší než (to znamená, představuje kratší časové období) nebo roven druhému, jinak hodnota FALSE.

##  <a name="operator_eq"></a>  CFileTimeSpan::operator =

Operátor přiřazení.

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objektu.

##  <a name="operator_-_eq"></a>  CFileTimeSpan::operator-=

Provede odčítání `CFileTimeSpan` objektu a přiřazuje výsledek aktuálního objektu.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objektu.

##  <a name="operator_eq_eq"></a>  CFileTimeSpan::operator ==

Porovná dva `CFileTimeSpan` objekty pro rovnost.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud jsou objekty stejné; jinak hodnota FALSE.

##  <a name="operator_gt"></a>  CFileTimeSpan::operator &gt;

Porovná dva `CFileTimeSpan` objekty k určení větší.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
`CFileTimeSpan` Objekt k porovnání.

### <a name="return-value"></a>Návratová hodnota

Vrátí TRUE, pokud je první objekt větší než (to znamená, představuje delší časové období) než druhé, jinak hodnota FALSE.

##  <a name="operator_gt_eq"></a>  CFileTimeSpan::operator &gt;=

Porovná dva `CFileTimeSpan` objekty k určení rovnosti, nebo větší.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*značka span*<br/>
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

## <a name="see-also"></a>Viz také

[FILETIME –](https://msdn.microsoft.com/library/windows/desktop/ms724284)<br/>
[CFileTime – třída](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
