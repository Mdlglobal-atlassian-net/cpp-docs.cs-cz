---
title: CInterpolatorBase – třída
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: d1fc675b1014ab9a099e8310b52b7458f2bff65f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916198"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase – třída

Implementuje zpětné volání, které je voláno rozhraním API animace, když má vypočítat novou hodnotu proměnné animace.

## <a name="syntax"></a>Syntaxe

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|`CInterpolatorBase` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CInterpolatorBase:: CreateInstance](#createinstance)|Vytvoří instanci `CInterpolatorBase` a ukládá ukazatel na vlastní interpolaci, která bude zpracovávat události.|
|[CInterpolatorBase:: getzávislosti](#getdependencies)|Získá závislosti interpolace. (Overrides `CUIAnimationInterpolatorBase::GetDependencies`.)|
|[CInterpolatorBase:: GetDuration](#getduration)|Získá dobu trvání interpolace. (Overrides `CUIAnimationInterpolatorBase::GetDuration`.)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Získá konečnou hodnotu, na kterou interpoluje vedoucí. (Overrides `CUIAnimationInterpolatorBase::GetFinalValue`.)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpoluje hodnotu u daného posunu (Overrides `CUIAnimationInterpolatorBase::InterpolateValue`.).|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpoluje rychlost na daném posunu (potlačení `CUIAnimationInterpolatorBase::InterpolateVelocity`).|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Ukládá ukazatel na vlastní interpolaci, která bude zpracovávat události.|
|[CInterpolatorBase::SetDuration](#setduration)|Nastaví dobu trvání hodnoty interpolace (přepsání `CUIAnimationInterpolatorBase::SetDuration`.)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Nastaví počáteční hodnotu a rychlost interpolace. (Overrides `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina je vytvořena a `IUIAnimationTransitionFactory::CreateTransition` předána `CCustomTransition` do okamžiku, kdy je objekt vytvořen jako součást procesu `CAnimationController::AnimateGroup`inicializace animace (spuštěno). Obvykle tuto třídu nemusíte používat přímo, stačí routs všechny události na `CCustomInterpolator`odvozenou třídu, jejíž ukazatel je předán `CCustomTransition`konstruktoru třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase

Vytvoří objekt CInterpolatorBase.

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>CInterpolatorBase:: CreateInstance

Vytvoří instanci třídy CInterpolatorBase a ukládá ukazatel na vlastní interpolaci, která bude zpracovávat události.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Ukazatel na vlastní interpolaci.

*ppHandler*<br/>
Výkonem. Obsahuje ukazatel na instanci CInterpolatorBase, když se funkce vrátí.

### <a name="return-value"></a>Návratová hodnota

##  <a name="getdependencies"></a>CInterpolatorBase:: getzávislosti

Získá závislosti interpolace.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Výkonem. Aspekty interpolování, které závisí na počáteční hodnotě předané do SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Výkonem. Aspekty interpolování, které závisí na počáteční rychlosti předané do SetInitialValueAndVelocity.

*durationDependencies*<br/>
Výkonem. Aspekty interpolace, které závisejí na době trvání předané do SetDuration.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL, pokud CCustomInterpolator není nastaven, nebo vlastní implementace vrátí hodnotu FALSE z metody getzávislosti.

##  <a name="getduration"></a>CInterpolatorBase:: GetDuration

Získá dobu trvání interpolace.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Výkonem. Doba trvání přechodu v sekundách.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL, pokud CCustomInterpolator není nastaven, nebo vlastní implementace vrátí hodnotu FALSE z metody GetDuration.

##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue

Získá konečnou hodnotu, na kterou interpoluje vedoucí.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výkonem. Poslední hodnota proměnné na konci přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL, pokud CCustomInterpolator není nastaven, nebo vlastní implementace vrátí FALSE z metody GetFinalValue.

##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue

Interpoluje hodnotu u daného posunutí.

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*polohy*<br/>
Posun od začátku přechodu. Posun je vždy větší nebo roven nule a menší než doba trvání přechodu. Tato metoda není volána, pokud je doba trvání přechodu nulová.

*value*<br/>
Výkonem. Interpolovaná hodnota.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL, pokud CCustomInterpolator není nastaven, nebo vlastní implementace vrátí FALSE z metody InterpolateValue.

##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity

Interpoluje rychlost na daném posunu.

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*polohy*<br/>
Posun od začátku přechodu. Posun je vždy větší nebo roven nule a menší nebo roven délce trvání přechodu. Tato metoda není volána, pokud je doba trvání přechodu nulová.

*rychlostí*<br/>
Výkonem. Rychlost proměnné na posunu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL, pokud CCustomInterpolator není nastaven, nebo vlastní implementace vrátí FALSE z metody InterpolateVelocity.

##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator

Ukládá ukazatel na vlastní interpolaci, která bude zpracovávat události.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Ukazatel na vlastní interpolaci.

##  <a name="setduration"></a>CInterpolatorBase::SetDuration

Nastaví dobu trvání interpolace.

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL, pokud CCustomInterpolator není nastaven, nebo vlastní implementace vrátí FALSE z metody SetDuration.

##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity

Nastaví počáteční hodnotu a rychlost interpolace.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*initialValue*<br/>
Hodnota proměnné na začátku přechodu.

*initialVelocity*<br/>
Rychlost proměnné na začátku přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL, pokud CCustomInterpolator není nastaven, nebo vlastní implementace vrátí FALSE z metody SetInitialValueAndVelocity.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
