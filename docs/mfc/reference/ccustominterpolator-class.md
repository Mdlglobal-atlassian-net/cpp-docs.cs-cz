---
title: CCustomInterpolator Class
ms.date: 11/04/2016
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
ms.openlocfilehash: 8d3f2ed95cfb9e7e885713252171c98834ae5c0a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303089"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator Class

Implementuje základní interpolator.

## <a name="syntax"></a>Syntaxe

```
class CCustomInterpolator;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Přetíženo. Vytvoří objekt vlastní interpolator a inicializuje doba trvání a rychlost pro zadané hodnoty.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCustomInterpolator::GetDependencies](#getdependencies)|Získá závislosti interpolator.|
|[CCustomInterpolator::GetDuration](#getduration)|Získá dobu trvání interpolator.|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Získá konečnou hodnotu, na který vede interpolator.|
|[CCustomInterpolator::Init](#init)|Inicializuje dobu trvání a konečná hodnota.|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Argument interpolaci hodnotu na dané pozici.|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Argument interpolaci rychlosti na dané pozici|
|[CCustomInterpolator::SetDuration](#setduration)|Nastaví dobu trvání interpolator.|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Nastaví počáteční hodnotu interpolator a rychlost.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|Interpolované hodnotu.|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Interpolované rychlosti.|
|[CCustomInterpolator::m_duration](#m_duration)|Doba trvání přechodu.|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|Konečná hodnota proměnné na konci přechodu.|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|Hodnota proměnné na začátku přechod.|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|Rychlost proměnnou na začátku přechod.|

## <a name="remarks"></a>Poznámky

Odvodit třídu z ccustominterpolator – a aby bylo možné implementovat vlastní interpolace algoritmus přepsat všechny nezbytné metody. Ukazatel na tato třída by měla předat jako parametr ccustomtransition –.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CCustomInterpolator`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="ccustominterpolator"></a>  CCustomInterpolator::CCustomInterpolator

Vytvoří vlastní interpolator objekt a nastaví všechny hodnoty na výchozí hodnotu 0.

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

*finalValue*

### <a name="remarks"></a>Poznámky

Použijte CCustomInterpolator::Init k inicializaci trvání a konečná hodnota později v kódu.

##  <a name="getdependencies"></a>  CCustomInterpolator::GetDependencies

Získá závislosti interpolator.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Výstup. Aspekty interpolator, které jsou závislé na počáteční hodnota předána SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Výstup. Aspekty interpolator, které jsou závislé na počáteční předán SetInitialValueAndVelocity.

*durationDependencies*<br/>
Výstup. Aspekty interpolator, které jsou závislé na době trvání předán SetDuration.

### <a name="return-value"></a>Návratová hodnota

Základní implementaci vždy vrátí hodnotu TRUE. Vrátí FALSE od přepsané implementace, pokud chcete selhání události.

##  <a name="getduration"></a>  CCustomInterpolator::GetDuration

Získá dobu trvání interpolator.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Výstup. Doba trvání přechodu během několika sekund.

### <a name="return-value"></a>Návratová hodnota

Základní implementaci vždy vrátí hodnotu TRUE. Vrátí FALSE od přepsané implementace, pokud chcete selhání události.

##  <a name="getfinalvalue"></a>  CCustomInterpolator::GetFinalValue

Získá konečnou hodnotu, na který vede interpolator.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výstup. Konečná hodnota proměnné na konci přechodu.

### <a name="return-value"></a>Návratová hodnota

Základní implementaci vždy vrátí hodnotu TRUE. Vrátí FALSE od přepsané implementace, pokud chcete selhání události.

##  <a name="init"></a>  CCustomInterpolator::Init

Inicializuje dobu trvání a konečná hodnota.

```
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

*finalValue*<br/>
Konečná hodnota proměnné na konci přechodu.

##  <a name="interpolatevalue"></a>  CCustomInterpolator::InterpolateValue

Argument interpolaci hodnotu na dané pozici.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výstup. Interpolované hodnotu.

### <a name="return-value"></a>Návratová hodnota

Základní implementaci vždy vrátí hodnotu TRUE. Vrátí FALSE od přepsané implementace, pokud chcete selhání události.

##  <a name="interpolatevelocity"></a>  CCustomInterpolator::InterpolateVelocity

Argument interpolaci rychlosti na dané pozici

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*velocity*<br/>
Výstup. Rychlost proměnnou na posunu.

### <a name="return-value"></a>Návratová hodnota

Základní implementaci vždy vrátí hodnotu TRUE. Vrátí FALSE od přepsané implementace, pokud chcete selhání události.

##  <a name="m_currentvalue"></a>  CCustomInterpolator::m_currentValue

Interpolované hodnotu.

```
DOUBLE m_currentValue;
```

##  <a name="m_currentvelocity"></a>  CCustomInterpolator::m_currentVelocity

Interpolované rychlosti.

```
DOUBLE m_currentVelocity;
```

##  <a name="m_duration"></a>  CCustomInterpolator::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CCustomInterpolator::m_finalValue

Konečná hodnota proměnné na konci přechodu.

```
DOUBLE m_finalValue;
```

##  <a name="m_initialvalue"></a>  CCustomInterpolator::m_initialValue

Hodnota proměnné na začátku přechod.

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomInterpolator::m_initialVelocity

Rychlost proměnnou na začátku přechod.

```
DOUBLE m_initialVelocity;
```

##  <a name="setduration"></a>  CCustomInterpolator::SetDuration

Nastaví dobu trvání interpolator.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

### <a name="return-value"></a>Návratová hodnota

Základní implementaci vždy vrátí hodnotu TRUE. Vrátí FALSE od přepsané implementace, pokud chcete selhání události.

##  <a name="setinitialvalueandvelocity"></a>  CCustomInterpolator::SetInitialValueAndVelocity

Nastaví počáteční hodnotu interpolator a rychlost.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*initialValue*<br/>
Hodnota proměnné na začátku přechod.

*initialVelocity*<br/>
Rychlost proměnnou na začátku přechod.

### <a name="return-value"></a>Návratová hodnota

Základní implementaci vždy vrátí hodnotu TRUE. Vrátí FALSE od přepsané implementace, pokud chcete selhání události.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
