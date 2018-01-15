---
title: "Třída CInterpolatorBase | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
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
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 79cea720391127f52d441de8f02c53756790d4b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase – třída
Implementuje zpětné volání, která je volána rozhraním API animace, když má k výpočtu novou hodnotu proměnné animace.  
  
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
|[CInterpolatorBase::CreateInstance](#createinstance)|Vytvoří instanci `CInterpolatorBase` a ukládá ukazatel na vlastní interpolator, který bude zpracovávat události.|  
|[CInterpolatorBase::GetDependencies](#getdependencies)|Získá interpolator závislosti. (Přepisuje `CUIAnimationInterpolatorBase::GetDependencies`.)|  
|[CInterpolatorBase::GetDuration](#getduration)|Získá dobu trvání interpolator. (Přepisuje `CUIAnimationInterpolatorBase::GetDuration`.)|  
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Získá konečná hodnota, na který vede interpolator. (Přepisuje `CUIAnimationInterpolatorBase::GetFinalValue`.)|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Argument interpolaci hodnota na danou posunu (přepíše `CUIAnimationInterpolatorBase::InterpolateValue`.)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Argument interpolaci rychlosti na danou posunu (přepíše `CUIAnimationInterpolatorBase::InterpolateVelocity`.)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Ukládá ukazatel na vlastní interpolator, který bude zpracovávat události.|  
|[CInterpolatorBase::SetDuration](#setduration)|Nastaví dobu trvání interpolator (přepíše `CUIAnimationInterpolatorBase::SetDuration`.)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Nastaví počáteční hodnotu interpolator a rychlosti. (Přepisuje `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|  
  
## <a name="remarks"></a>Poznámky  
 Tato obslužná rutina se vytvoří a předaný `IUIAnimationTransitionFactory::CreateTransition` při `CCustomTransition` objekt se vytváří jako součást procesu inicializace animace (spustí `CAnimationController::AnimateGroup`). Obvykle nemusíte používat tato třída přímo, je právě routs všechny události `CCustomInterpolator`-odvozené třídy, jejichž ukazatel předaný konstruktoru `CCustomTransition`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase  
 Vytvoří objekt CInterpolatorBase.  
  
```  
CInterpolatorBase();
```  
  
##  <a name="createinstance"></a>CInterpolatorBase::CreateInstance  
 Vytvoří instanci CInterpolatorBase a ukládá ukazatel na vlastní interpolator, který bude zpracovávat události.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,  
    IUIAnimationInterpolator** ppHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pInterpolator`  
 Ukazatel na vlastní interpolator.  
  
 `ppHandler`  
 Výstup. Ukazatel na instanci CInterpolatorBase obsahuje po návratu funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies  
 Získá interpolator závislosti.  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValueDependencies`  
 Výstup. Aspekty interpolator, které jsou závislé na počáteční hodnota předaný SetInitialValueAndVelocity.  
  
 `initialVelocityDependencies`  
 Výstup. Aspekty interpolator, které závisí na rychlosti počáteční předaný SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Výstup. Aspekty interpolator, které jsou závislé na dobu trvání předaný SetDuration.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Pokud není nastavena CCustomInterpolator, nebo vlastní implementace vrací hodnotu FALSE, GetDependencies metoda vrátí E_FAIL.  
  
##  <a name="getduration"></a>CInterpolatorBase::GetDuration  
 Získá dobu trvání interpolator.  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Výstup. Doba trvání přechodu, v sekundách.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Pokud není nastavena CCustomInterpolator, nebo vlastní implementace vrací hodnotu FALSE, GetDuration metoda vrátí E_FAIL.  
  
##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue  
 Získá konečná hodnota, na který vede interpolator.  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Výstup. Konečná hodnota proměnné na konci přechodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Pokud není nastavena CCustomInterpolator, nebo vlastní implementace vrací hodnotu FALSE, GetFinalValue metoda vrátí E_FAIL.  
  
##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue  
 Argument interpolaci hodnota na daným posunem.  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `offset`  
 Posun od začátku přechodu. Posun je vždy větší než nebo roven nule a menší než doba trvání přechodu. Tato metoda není volána, pokud trvání přechodu je nulová.  
  
 `value`  
 Výstup. Interpolované hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Pokud není nastavena CCustomInterpolator, nebo vlastní implementace vrací hodnotu FALSE, InterpolateValue metoda vrátí E_FAIL.  
  
##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity  
 Argument interpolaci rychlosti v daným posunem.  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parametry  
 `offset`  
 Posun od začátku přechodu. Posun je vždy větší než nebo roven nule a menší než nebo rovna trvání přechodu. Tato metoda není volána, pokud trvání přechodu je nulová.  
  
 `velocity`  
 Výstup. Rychlosti proměnnou na posunu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Pokud není nastavena CCustomInterpolator, nebo vlastní implementace vrací hodnotu FALSE, InterpolateVelocity metoda vrátí E_FAIL.  
  
##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator  
 Ukládá ukazatel na vlastní interpolator, který bude zpracovávat události.  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>Parametry  
 `pInterpolator`  
 Ukazatel na vlastní interpolator.  
  
##  <a name="setduration"></a>CInterpolatorBase::SetDuration  
 Nastaví dobu trvání interpolator  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Pokud není nastavena CCustomInterpolator, nebo vlastní implementace vrací hodnotu FALSE, SetDuration metoda vrátí E_FAIL.  
  
##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity  
 Nastaví počáteční hodnotu interpolator a rychlosti.  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValue`  
 Hodnota proměnné na začátku přechodu.  
  
 `initialVelocity`  
 Rychlosti proměnnou na začátku přechodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Pokud není nastavena CCustomInterpolator, nebo vlastní implementace vrací hodnotu FALSE, SetInitialValueAndVelocity metoda vrátí E_FAIL.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
