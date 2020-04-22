---
title: CCustomInterpolator – třída
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
ms.openlocfilehash: 00ce0661fa3fbde714a7299ecbbd54df7c9bcc36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749170"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator – třída

Implementuje základní interpolátor.

## <a name="syntax"></a>Syntaxe

```
class CCustomInterpolator;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Přetíženo. Vytvoří vlastní objekt interpolátoru a inicializuje dobu trvání a rychlost na zadané hodnoty.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCustomInterpolator::GetDependencies](#getdependencies)|Získá závislosti interpolátoru.|
|[CCustomInterpolator::GetDuration](#getduration)|Získá dobu trvání interpolátoru.|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Získá konečnou hodnotu, na kterou interpolátor vede.|
|[CCustomInterpolator::Init](#init)|Inicializuje dobu trvání a konečnou hodnotu.|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpoluje hodnotu v daném posunu.|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpoluje rychlost při daném posunu|
|[CCustomInterpolator::SetDuration](#setduration)|Nastaví dobu trvání interpolátoru.|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Nastaví počáteční hodnotu a rychlost interpolátoru.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|Interpolovaná hodnota.|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Interpolovaná rychlost.|
|[CCustomInterpolator::m_duration](#m_duration)|Doba trvání přechodu.|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|Konečná hodnota proměnné na konci přechodu.|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|Hodnota proměnné na začátku přechodu.|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|Rychlost proměnné na začátku přechodu.|

## <a name="remarks"></a>Poznámky

Odvodit třídu z CCustomInterpolator a přepsat všechny nezbytné metody k implementaci vlastní interpolační algoritmus. Ukazatel na tuto třídu by měl být předán jako parametr CCustomTransition.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CCustomInterpolator`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator

Vytvoří vlastní objekt interpolátoru a nastaví všechny hodnoty na výchozí hodnotu 0.

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

Použijte CCustomInterpolator::Init k inicializaci doby trvání a konečné hodnoty později v kódu.

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustomInterpolator::GetDependencies

Získá závislosti interpolátoru.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Výstup. Aspekty interpolátoru, které závisí na počáteční hodnotě předané SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Výstup. Aspekty interpolátoru, které závisí na počáteční rychlost předána SetInitialValueAndVelocity.

*durationDependencies*<br/>
Výstup. Aspekty interpolátoru, které závisí na trvání předána SetDuration.

### <a name="return-value"></a>Návratová hodnota

Základní implementace vždy vrátí hodnotu PRAVDA. Vrátí false z přepsané implementace, pokud chcete selhání události.

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustomInterpolator::GetDuration

Získá dobu trvání interpolátoru.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Výstup. Doba trvání přechodu v sekundách.

### <a name="return-value"></a>Návratová hodnota

Základní implementace vždy vrátí hodnotu PRAVDA. Vrátí false z přepsané implementace, pokud chcete selhání události.

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue

Získá konečnou hodnotu, na kterou interpolátor vede.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výstup. Konečná hodnota proměnné na konci přechodu.

### <a name="return-value"></a>Návratová hodnota

Základní implementace vždy vrátí hodnotu PRAVDA. Vrátí false z přepsané implementace, pokud chcete selhání události.

## <a name="ccustominterpolatorinit"></a><a name="init"></a>CCustomInterpolator::Init

Inicializuje dobu trvání a konečnou hodnotu.

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

*finalValue*<br/>
Konečná hodnota proměnné na konci přechodu.

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue

Interpoluje hodnotu v daném posunu.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výstup. Interpolovaná hodnota.

### <a name="return-value"></a>Návratová hodnota

Základní implementace vždy vrátí hodnotu PRAVDA. Vrátí false z přepsané implementace, pokud chcete selhání události.

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity

Interpoluje rychlost při daném posunu

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*Rychlost*<br/>
Výstup. Rychlost proměnné na posun.

### <a name="return-value"></a>Návratová hodnota

Základní implementace vždy vrátí hodnotu PRAVDA. Vrátí false z přepsané implementace, pokud chcete selhání události.

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue

Interpolovaná hodnota.

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity

Interpolovaná rychlost.

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a>CCustomInterpolator::m_duration

Doba trvání přechodu.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue

Konečná hodnota proměnné na konci přechodu.

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue

Hodnota proměnné na začátku přechodu.

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity

Rychlost proměnné na začátku přechodu.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a>CCustomInterpolator::SetDuration

Nastaví dobu trvání interpolátoru.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

### <a name="return-value"></a>Návratová hodnota

Základní implementace vždy vrátí hodnotu PRAVDA. Vrátí false z přepsané implementace, pokud chcete selhání události.

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity

Nastaví počáteční hodnotu a rychlost interpolátoru.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*Initialvalue*<br/>
Hodnota proměnné na začátku přechodu.

*počáteční rychlost*<br/>
Rychlost proměnné na začátku přechodu.

### <a name="return-value"></a>Návratová hodnota

Základní implementace vždy vrátí hodnotu TRUE. Vrátí false z přepsané implementace, pokud chcete selhání události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
