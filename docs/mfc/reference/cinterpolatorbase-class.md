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
ms.openlocfilehash: efa08aa5dd556d7e136323c31451a9f33bd72ec6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754957"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase – třída

Implementuje zpětné volání, které je voláno rozhraním API animace, když má vypočítat novou hodnotu proměnné animace.

## <a name="syntax"></a>Syntaxe

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Vytvoří `CInterpolatorBase` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Vytvoří instanci `CInterpolatorBase` a uloží ukazatel na vlastní interpolátor, který bude zpracovávat události.|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Získá závislosti interpolátoru. (Přepíše `CUIAnimationInterpolatorBase::GetDependencies`.)|
|[CInterpolatorBase::GetDuration](#getduration)|Získá dobu trvání interpolátoru. (Přepíše `CUIAnimationInterpolatorBase::GetDuration`.)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Získá konečnou hodnotu, na kterou interpolátor vede. (Přepíše `CUIAnimationInterpolatorBase::GetFinalValue`.)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpoluje hodnotu při daném odsazení (přepíše `CUIAnimationInterpolatorBase::InterpolateValue`.)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpoluje rychlost při daném odsazení (Přepsání `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Ukládá ukazatel na vlastní interpolátor, který bude zpracovávat události.|
|[CInterpolatorBase::SetDuration](#setduration)|Nastaví dobu trvání interpolátoru `CUIAnimationInterpolatorBase::SetDuration`(Přepíše .)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Nastaví počáteční hodnotu a rychlost interpolátoru. (Přepíše `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|

## <a name="remarks"></a>Poznámky

Tato obslužná `IUIAnimationTransitionFactory::CreateTransition` rutina je vytvořena a předána při vytváření `CCustomTransition` `CAnimationController::AnimateGroup`objektu jako součást procesu inicializace animace (spuštěno). Obvykle není nutné použít tuto třídu přímo, je to jen `CCustomInterpolator`routs všechny události -derived `CCustomTransition`třídy, jehož ukazatel je předán konstruktoru .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase

Vytvoří objekt CInterpolatorBase.

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a>CInterpolatorBase::CreateInstance

Vytvoří instanci CInterpolatorBase a uloží ukazatel na vlastní interpolátor, který bude zpracování událostí.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parametry

*pInterpolátor*<br/>
Ukazatel na vlastní interpolátor.

*ppHandler*<br/>
Výstup. Obsahuje ukazatel na instanci CInterpolatorBase při návratu funkce.

### <a name="return-value"></a>Návratová hodnota

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a>CInterpolatorBase::GetDependencies

Získá závislosti interpolátoru.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parametry

*initialValueDependencies*<br/>
Výstup. Aspekty interpolátoru, které závisí na počáteční hodnotě předané SetInitialValueAndVelocity.

*initialVelocityDependencies*<br/>
Výstup. Aspekty interpolátoru, které závisí na počáteční rychlost předána SetInitialValueAndVelocity.

*durationDependencies*<br/>
Výstup. Aspekty interpolátoru, které závisí na trvání předána SetDuration.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL pokud Není nastaven CCustomInterpolator nebo vlastní implementace vrátí FALSE z GetDependencies metoda.

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a>CInterpolatorBase::GetDuration

Získá dobu trvání interpolátoru.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Výstup. Doba trvání přechodu v sekundách.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL pokud Není nastaven CCustomInterpolator nebo vlastní implementace vrátí FALSE z GetDuration metoda.

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue

Získá konečnou hodnotu, na kterou interpolátor vede.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*value*<br/>
Výstup. Konečná hodnota proměnné na konci přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL pokud Není nastaven CCustomInterpolator nebo vlastní implementace vrátí FALSE z GetFinalValue metoda.

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue

Interpoluje hodnotu při daném posunu

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Parametry

*Posun*<br/>
Posun od začátku přechodu. Posun je vždy větší než nebo rovna nule a menší než doba trvání přechodu. Tato metoda není volána, pokud je doba trvání přechodu nula.

*value*<br/>
Výstup. Interpolovaná hodnota.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL pokud není nastaven CCustomInterpolator nebo vlastní implementace vrátí HODNOTU NEPRAVDA z metody InterpolateValue.

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity

Interpoluje rychlost při daném posunu

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parametry

*Posun*<br/>
Posun od začátku přechodu. Posun je vždy větší než nebo rovno nule a menší než nebo rovno trvání přechodu. Tato metoda není volána, pokud je doba trvání přechodu nula.

*Rychlost*<br/>
Výstup. Rychlost proměnné na posun.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL pokud Není nastaven CCustomInterpolator nebo vlastní implementace vrátí FALSE z Metody InterpolateVelocity.

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator

Ukládá ukazatel na vlastní interpolátor, který bude zpracovávat události.

```cpp
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parametry

*pInterpolátor*<br/>
Ukazatel na vlastní interpolátor.

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a>CInterpolatorBase::SetDuration

Nastaví dobu trvání interpolátoru.

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parametry

*Doba trvání*<br/>
Doba trvání přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL pokud není nastaven CCustomInterpolator nebo vlastní implementace vrátí hodnotu NEPRAVDA z metody SetDuration.

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity

Nastaví počáteční hodnotu a rychlost interpolátoru.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parametry

*Initialvalue*<br/>
Hodnota proměnné na začátku přechodu.

*počáteční rychlost*<br/>
Rychlost proměnné na začátku přechodu.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. Vrátí E_FAIL pokud není nastaven CCustomInterpolator nebo vlastní implementace vrátí hodnotu FALSE z metody SetInitialValueAndVelocity.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
