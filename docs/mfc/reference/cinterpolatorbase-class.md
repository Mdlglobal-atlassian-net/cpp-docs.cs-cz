---
title: Cinterpolatorbase – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5287c54aad0a4ec41145f8241123489ea74d19f7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407895"
---
# <a name="cinterpolatorbase-class"></a>Cinterpolatorbase – třída

Implementuje zpětné volání, které je voláno rozhraním API animace, když má vypočítat nové hodnoty proměnné animace.

## <a name="syntax"></a>Syntaxe

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Vytvoří `CInterpolatorBase` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Vytvoří instanci `CInterpolatorBase` a uchovává ukazatel na vlastní interpolator, který bude zpracovávat události.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Získá závislosti interpolator. (Přepíše `CUIAnimationInterpolatorBase::GetDependencies`.)|
|[CInterpolatorBase::GetDuration](#getduration)|Získá dobu trvání interpolator. (Přepíše `CUIAnimationInterpolatorBase::GetDuration`.)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Získá konečnou hodnotu, na který vede interpolator. (Přepíše `CUIAnimationInterpolatorBase::GetFinalValue`.)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Argument interpolaci hodnotu daného posunem (přepíše `CUIAnimationInterpolatorBase::InterpolateValue`.)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Argument interpolaci rychlosti na dané pozici (přepíše `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Uchovává ukazatel na vlastní interpolator, který bude zpracovávat události.|
|[CInterpolatorBase::SetDuration](#setduration)|Nastaví dobu trvání interpolator (přepíše `CUIAnimationInterpolatorBase::SetDuration`.)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Nastaví počáteční hodnotu interpolator a rychlost. (Přepíše `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina je vytvořen a předán `IUIAnimationTransitionFactory::CreateTransition` při `CCustomTransition` objekt vytváří jako součást procesu inicializace animace (tím, že `CAnimationController::AnimateGroup`). Obvykle není nutné k použití této třídy přímo, stačí routs všech událostí `CCustomInterpolator`-odvozené třídy, jejíž ukazatel je předán konstruktoru `CCustomTransition`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>  CInterpolatorBase::CInterpolatorBase

Vytvoří objekt cinterpolatorbase –.

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance

Vytvoří instanci cinterpolatorbase – a uchovává ukazatel na vlastní interpolator, který bude zpracovávat události.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Ukazatel na vlastní interpolator.

*ppHandler*<br/>
Výstup. Ukazatel na instanci cinterpolatorbase – obsahuje po návratu funkce.

### <a name="return-value"></a>Návratová hodnota

##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies

Získá závislosti interpolator.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Výstup. Aspekty interpolator, které jsou závislé na počáteční hodnota předána SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Výstup. Aspekty interpolator, které jsou závislé na počáteční předán SetInitialValueAndVelocity.

*durationDependencies*<br/>
Výstup. Aspekty interpolator, které jsou závislé na době trvání předán SetDuration.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. Pokud není nastaven ccustominterpolator – nebo vlastní implementace vrací hodnotu FALSE z metody GetDependencies vrátí E_FAIL.

##  <a name="getduration"></a>  CInterpolatorBase::GetDuration

Získá dobu trvání interpolator.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Výstup. Doba trvání přechodu během několika sekund.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. Pokud není nastaven ccustominterpolator – nebo vlastní implementace vrací hodnotu FALSE z metody GetDuration vrátí E_FAIL.

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

Získá konečnou hodnotu, na který vede interpolator.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výstup. Konečná hodnota proměnné na konci přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. Pokud není nastaven ccustominterpolator – nebo vlastní implementace vrací hodnotu FALSE z metody GetFinalValue vrátí E_FAIL.

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

Argument interpolaci hodnotu na dané pozici

```
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*Posun*<br/>
Posun od začátku přechod. Posun je vždy větší než nebo rovna nule a menší než doba trvání přechodu. Tato metoda není volána, pokud doba trvání přechodu je nula.

*value*<br/>
Výstup. Interpolované hodnotu.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. Pokud není nastaven ccustominterpolator – nebo vlastní implementace vrací hodnotu FALSE z metody InterpolateValue vrátí E_FAIL.

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

Argument interpolaci rychlosti na dané pozici

```
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*Posun*<br/>
Posun od začátku přechod. Posun je vždy větší nebo rovna nule a menší než doba trvání přechodu. Tato metoda není volána, pokud doba trvání přechodu je nula.

*Rychlost*<br/>
Výstup. Rychlost proměnnou na posunu.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. Pokud není nastaven ccustominterpolator – nebo vlastní implementace vrací hodnotu FALSE z metody InterpolateVelocity vrátí E_FAIL.

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

Uchovává ukazatel na vlastní interpolator, který bude zpracovávat události.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolator*<br/>
Ukazatel na vlastní interpolator.

##  <a name="setduration"></a>  CInterpolatorBase::SetDuration

Nastaví dobu trvání interpolator.

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. Pokud není nastaven ccustominterpolator – nebo vlastní implementace vrací hodnotu FALSE z metody SetDuration vrátí E_FAIL.

##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity

Nastaví počáteční hodnotu interpolator a rychlost.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue,
  __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*Počáteční hodnota*<br/>
Hodnota proměnné na začátku přechod.

*initialVelocity*<br/>
Rychlost proměnnou na začátku přechod.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. Pokud není nastaven ccustominterpolator – nebo vlastní implementace vrací hodnotu FALSE z metody SetInitialValueAndVelocity vrátí E_FAIL.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
