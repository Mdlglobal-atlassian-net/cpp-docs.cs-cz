---
title: CFileTimeSpan – třída
description: Třída knihovny ATL (Active Template Library) a knihovna MFC (Microsoft Foundation Classes) CFileTimeSpan spravuje časové intervaly v jednotkách časových jednotek.
ms.date: 01/10/2020
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
ms.openlocfilehash: 89d95759b11ff7e52c2a8fa75cf94f7b7b81fa36
ms.sourcegitcommit: c3283062ce4e382aec7f11626d358a37caf8cdbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75914384"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan – třída

Tato třída poskytuje metody pro správu relativních hodnot data a času přidružených k souboru.

## <a name="syntax"></a>Syntaxe

```cpp
class CFileTimeSpan
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFileTimeSpan::CFileTimeSpan](#cfiletimespan)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFileTimeSpan:: GetTimeSpan](#gettimespan)|Voláním této metody načtete časové rozpětí z objektu `CFileTimeSpan`.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Zavolejte tuto metodu pro nastavení časového rozsahu objektu `CFileTimeSpan`.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CFileTimeSpan:: operator-](#operator_-)|Provede odčítání u objektu `CFileTimeSpan`.|
|[CFileTimeSpan:: operator! =](#operator_neq)|Porovná dva objekty `CFileTimeSpan` pro nerovnost.|
|[CFileTimeSpan:: operator + – operátor](#operator_add)|Provede přidání do objektu `CFileTimeSpan`.|
|[CFileTimeSpan:: operator + =](#operator_add_eq)|Provede přidání do objektu `CFileTimeSpan` a přiřadí výsledek k aktuálnímu objektu.|
|[CFileTimeSpan:: operator &lt;](#operator_lt)|Porovná dva objekty `CFileTimeSpan` k určení menšího.|
|[CFileTimeSpan:: operator &lt;=](#operator_lt_eq)|Porovná dva objekty `CFileTimeSpan` k určení rovnosti nebo menšího.|
|[CFileTimeSpan:: operator =](#operator_eq)|Operátor přiřazení|
|[CFileTimeSpan:: operator-=](#operator_-_eq)|Provede odčítání u objektu `CFileTimeSpan` a přiřadí výsledek k aktuálnímu objektu.|
|[CFileTimeSpan:: operator = = – operátor](#operator_eq_eq)|Porovná dva objekty `CFileTimeSpan` k rovnosti.|
|[CFileTimeSpan:: operator &gt;](#operator_gt)|Porovná dva objekty `CFileTimeSpan` a určí větší.|
|[CFileTimeSpan:: operator &gt;=](#operator_gt_eq)|Porovná dva objekty `CFileTimeSpan` a určí rovnost nebo větší.|

## <a name="remarks"></a>Poznámky

Třída `CFileTimeSpan` poskytuje metody pro zpracování relativních časových období v jednotkách, které systém souborů používá. Tyto jednotky se často používají při operacích se soubory, jako je například vytvoření souboru, poslední otevření nebo Poslední změna. Metody této třídy se často používají ve spojení s objekty [třídy CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: milisekund](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime. h

## <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

Konstruktor

```cpp
CFileTimeSpan() throw();
CFileTimeSpan(const CFileTimeSpan& span) throw();
CFileTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
Existující objekt `CFileTimeSpan`.

*nSpan*\
Časové období v jednotkách časových jednotek.

### <a name="remarks"></a>Poznámky

Objekt `CFileTimeSpan` lze vytvořit pomocí existujícího objektu `CFileTimeSpan` nebo vyjádřený jako 64 hodnota v 100-nanosekund časových jednotek. Další informace najdete v tématu [CFileTime](cfiletime-class.md). Výchozí konstruktor nastaví časový rozsah na 0.

## <a name="gettimespan"></a>CFileTimeSpan:: GetTimeSpan

Voláním této metody načtete časové rozpětí z objektu `CFileTimeSpan`.

```cpp
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí časové rozpětí v jednotkách času 100-nanosekund. Další informace najdete v tématu [CFileTime](cfiletime-class.md).

## <a name="operator_-"></a>CFileTimeSpan:: operator-

Provede odčítání u objektu `CFileTimeSpan`.

```cpp
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt `CFileTimeSpan` reprezentující výsledek rozdílu mezi dvěma časovými rozsahy.

## <a name="operator_neq"></a>CFileTimeSpan:: operator! =

Porovná dva objekty `CFileTimeSpan` pro nerovnost.

```cpp
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
Objekt `CFileTimeSpan`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud se porovnávané položka rovná objektu `CFileTimeSpan`; v opačném případě FALSE.

## <a name="operator_add"></a>CFileTimeSpan:: operator + – operátor

Provede přidání do objektu `CFileTimeSpan`.

```cpp
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí objekt `CFileTimeSpan`, který obsahuje součet dvou časových rozsahů.

## <a name="operator_add_eq"></a>CFileTimeSpan:: operator + =

Provede přidání do objektu `CFileTimeSpan` a přiřadí výsledek k aktuálnímu objektu.

```cpp
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný objekt `CFileTimeSpan`, který obsahuje součet dvou časových rozsahů.

## <a name="operator_lt"></a>CFileTimeSpan:: operator &lt;

Porovná dva objekty `CFileTimeSpan` k určení menšího.

```cpp
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
Objekt `CFileTimeSpan`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší (tj. představuje kratší časové období) než druhý, jinak FALSE.

## <a name="operator_lt_eq"></a>CFileTimeSpan:: operator &lt;=

Porovná dva objekty `CFileTimeSpan` k určení rovnosti nebo menšího.

```cpp
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
Objekt `CFileTimeSpan`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší než (tj. představuje kratší časové období) nebo se rovná druhému, jinak FALSE.

## <a name="operator_eq"></a>CFileTimeSpan:: operator =

Operátor přiřazení

```cpp
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný objekt `CFileTimeSpan`.

## <a name="operator_-_eq"></a>CFileTimeSpan:: operator-=

Provede odčítání u objektu `CFileTimeSpan` a přiřadí výsledek k aktuálnímu objektu.

```cpp
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný objekt `CFileTimeSpan`.

## <a name="operator_eq_eq"></a>CFileTimeSpan:: operator = = – operátor

Porovná dva objekty `CFileTimeSpan` k rovnosti.

```cpp
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
Objekt `CFileTimeSpan`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud jsou objekty stejné, jinak FALSE.

## <a name="operator_gt"></a>CFileTimeSpan:: operator &gt;

Porovná dva objekty `CFileTimeSpan` a určí větší.

```cpp
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
Objekt `CFileTimeSpan`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší než (tj. představuje delší časové období) než druhý, jinak FALSE.

## <a name="operator_gt_eq"></a>CFileTimeSpan:: operator &gt;=

Porovná dva objekty `CFileTimeSpan` a určí rovnost nebo větší.

```cpp
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

\ *rozpětí*
Objekt `CFileTimeSpan`, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší než (tj. představuje delší časové období) nebo se rovná druhému, jinak FALSE.

## <a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

Zavolejte tuto metodu pro nastavení časového rozsahu objektu `CFileTimeSpan`.

```cpp
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan*\
Nová hodnota pro časové období v jednotkách času v 100. nanosekund. Další informace najdete v tématu [CFileTime](cfiletime-class.md).

## <a name="see-also"></a>Viz také:

\ v [době běhu](/windows/win32/api/minwinbase/ns-minwinbase-filetime)
\ [třídy CFileTime](cfiletime-class.md)
\ [diagramu hierarchie](../../mfc/hierarchy-chart.md)
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
