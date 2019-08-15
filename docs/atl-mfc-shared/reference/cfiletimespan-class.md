---
title: CFileTimeSpan – třída
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
ms.openlocfilehash: f9bb42ba4c142f671a83dcfa7e99cff940fff047
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491283"
---
# <a name="cfiletimespan-class"></a>CFileTimeSpan – třída

Tato třída poskytuje metody pro správu relativních hodnot data a času přidružených k souboru.

## <a name="syntax"></a>Syntaxe

```
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
|[CFileTimeSpan:: GetTimeSpan](#gettimespan)|Zavolejte tuto metodu pro načtení časového rozsahu z `CFileTimeSpan` objektu.|
|[CFileTimeSpan::SetTimeSpan](#settimespan)|Zavolejte tuto metodu pro nastavení časového rozsahu `CFileTimeSpan` objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CFileTimeSpan:: operator-](#operator_-)|Provede odčítání `CFileTimeSpan` objektu.|
|[CFileTimeSpan:: operator! =](#operator_neq)|Porovná `CFileTimeSpan` dva objekty pro nerovnost.|
|[CFileTimeSpan:: operator + – operátor](#operator_add)|Provede přidání do `CFileTimeSpan` objektu.|
|[CFileTimeSpan:: operator + =](#operator_add_eq)|Provede přidání `CFileTimeSpan` do objektu a přiřadí výsledek k aktuálnímu objektu.|
|[CFileTimeSpan:: operator&lt;](#operator_lt)|Porovná `CFileTimeSpan` dva objekty a určí menší.|
|[CFileTimeSpan:: operator&lt;=](#operator_lt_eq)|Porovná `CFileTimeSpan` dva objekty a určí rovnost nebo menší.|
|[CFileTimeSpan:: operator =](#operator_eq)|Operátor přiřazení|
|[CFileTimeSpan:: operator-=](#operator_-_eq)|Provede odčítání `CFileTimeSpan` objektu a přiřadí výsledek k aktuálnímu objektu.|
|[CFileTimeSpan:: operator = = – operátor](#operator_eq_eq)|Porovná `CFileTimeSpan` dva objekty pro rovnost.|
|[CFileTimeSpan:: operator&gt;](#operator_gt)|Porovná `CFileTimeSpan` dva objekty a určí větší.|
|[CFileTimeSpan:: operator&gt;=](#operator_gt_eq)|Porovná `CFileTimeSpan` dva objekty a určí rovnost nebo větší.|

## <a name="remarks"></a>Poznámky

Tato třída poskytuje metody pro správu relativních časových období, které se často vyskytují při provádění operací týkajících se vytvoření souboru, posledního použití nebo poslední změny. Metody této třídy se často používají ve spojení s objekty [třídy CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md) .

## <a name="example"></a>Příklad

Podívejte se na příklad pro [CFileTime:: milisekund](../../atl-mfc-shared/reference/cfiletime-class.md#millisecond).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atltime. h

##  <a name="cfiletimespan"></a>CFileTimeSpan::CFileTimeSpan

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
Časové období v milisekundách.

### <a name="remarks"></a>Poznámky

Objekt lze vytvořit pomocí existujícího `CFileTimeSpan` objektu nebo vyjádřen jako hodnota 64. `CFileTimeSpan` Výchozí konstruktor nastaví časový rozsah na 0.

##  <a name="gettimespan"></a>CFileTimeSpan:: GetTimeSpan

Zavolejte tuto metodu pro načtení časového rozsahu z `CFileTimeSpan` objektu.

```
LONGLONG GetTimeSpan() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí časové rozpětí v milisekundách.

##  <a name="operator_-"></a>CFileTimeSpan:: operator-

Provede odčítání `CFileTimeSpan` objektu.

```
CFileTimeSpan operator-(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

`CFileTimeSpan` Vrátí objekt představující výsledek rozdílu mezi dvěma časovými rozsahy.

##  <a name="operator_neq"></a>CFileTimeSpan:: operator! =

Porovná `CFileTimeSpan` dva objekty pro nerovnost.

```
bool operator!=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu true, pokud je položka, která je porovnána `CFileTimeSpan` , nerovná objektu; v opačném případě false.

##  <a name="operator_add"></a>CFileTimeSpan:: operator + – operátor

Provede přidání do `CFileTimeSpan` objektu.

```
CFileTimeSpan operator+(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

`CFileTimeSpan` Vrátí objekt, který obsahuje součet dvou časových rozsahů.

##  <a name="operator_add_eq"></a>CFileTimeSpan:: operator + =

Provede přidání na `CFileTimeSpan` objekt a přiřadí výsledek k aktuálnímu objektu.

```
CFileTimeSpan& operator+=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt, který obsahuje součet dvou časových rozsahů.

##  <a name="operator_lt"></a>CFileTimeSpan:: operator&lt;

Porovná `CFileTimeSpan` dva objekty a určí menší.

```
bool operator<(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší (tj. představuje kratší časové období) než druhý, jinak FALSE.

##  <a name="operator_lt_eq"></a>CFileTimeSpan:: operator&lt;=

Porovná `CFileTimeSpan` dva objekty a určí rovnost nebo menší.

```
bool operator<=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt menší než (tj. představuje kratší časové období) nebo se rovná druhému, jinak FALSE.

##  <a name="operator_eq"></a>CFileTimeSpan:: operator =

Operátor přiřazení

```
CFileTimeSpan& operator=(const CFileTimeSpan& span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt.

##  <a name="operator_-_eq"></a>CFileTimeSpan:: operator-=

Provede odčítání `CFileTimeSpan` objektu a přiřadí výsledek k aktuálnímu objektu.

```
CFileTimeSpan& operator-=(CFileTimeSpan span) throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
A `CFileTimeSpan` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí aktualizovaný `CFileTimeSpan` objekt.

##  <a name="operator_eq_eq"></a>CFileTimeSpan:: operator = = – operátor

Porovná `CFileTimeSpan` dva objekty pro rovnost.

```
bool operator==(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud jsou objekty stejné, jinak FALSE.

##  <a name="operator_gt"></a>CFileTimeSpan:: operator&gt;

Porovná `CFileTimeSpan` dva objekty a určí větší.

```
bool operator>(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší než (tj. představuje delší časové období) než druhý, jinak FALSE.

##  <a name="operator_gt_eq"></a>CFileTimeSpan:: operator&gt;=

Porovná `CFileTimeSpan` dva objekty a určí rovnost nebo větší.

```
bool operator>=(CFileTimeSpan span) const throw();
```

### <a name="parameters"></a>Parametry

*span*<br/>
`CFileTimeSpan` Objekt, který má být porovnán.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud je první objekt větší než (tj. představuje delší časové období) nebo se rovná druhému, jinak FALSE.

##  <a name="settimespan"></a>CFileTimeSpan::SetTimeSpan

Zavolejte tuto metodu pro nastavení časového rozsahu `CFileTimeSpan` objektu.

```
void SetTimeSpan(LONGLONG nSpan) throw();
```

### <a name="parameters"></a>Parametry

*nSpan*<br/>
Nová hodnota časového intervalu v milisekundách

## <a name="see-also"></a>Viz také:

[FILETIME –](/windows/win32/api/minwinbase/ns-minwinbase-filetime)<br/>
[CFileTime – třída](../../atl-mfc-shared/reference/cfiletime-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
