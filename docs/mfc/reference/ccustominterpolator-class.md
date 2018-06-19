---
title: Třída CCustomInterpolator | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b093ff87d7f2c8c52b6745be4e2a31580fce0fce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355796"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator – třída
Implementuje základní interpolator.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Přetíženo. Vytvoří objekt vlastní interpolator a inicializuje doba trvání a rychlosti zadané hodnoty.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|Získá interpolator závislosti.|  
|[CCustomInterpolator::GetDuration](#getduration)|Získá dobu trvání interpolator.|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Získá konečná hodnota, na který vede interpolator.|  
|[CCustomInterpolator::Init](#init)|Inicializuje doba trvání a konečná hodnota.|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Argument interpolaci hodnota na danou posunu.|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Argument interpolaci rychlosti v daným posunem.|  
|[CCustomInterpolator::SetDuration](#setduration)|Nastaví dobu trvání interpolator.|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Nastaví počáteční hodnotu interpolator a rychlosti.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|Interpolované hodnota.|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Interpolované rychlosti.|  
|[CCustomInterpolator::m_duration](#m_duration)|Doba trvání přechodu.|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|Konečná hodnota proměnné na konci přechodu.|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|Hodnota proměnné na začátku přechodu.|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|Rychlosti proměnnou na začátku přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Odvození třídy z CCustomInterpolator a přepsat všechny nezbytné metody k implementaci vlastních interpolace algoritmus. Ukazatel na tato třída by měla být jako parametr předaný CCustomTransition.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="ccustominterpolator"></a>  CCustomInterpolator::CCustomInterpolator  
 Vytvoří objekt vlastní interpolator a nastaví všechny hodnoty na výchozí hodnotu 0.  
  
```  
CCustomInterpolator();

 
CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
 `finalValue`  
  
### <a name="remarks"></a>Poznámky  
 Použijte CCustomInterpolator::Init k chybě při inicializaci doba trvání a konečná hodnota později v kódu.  
  
##  <a name="getdependencies"></a>  CCustomInterpolator::GetDependencies  
 Získá interpolator závislosti.  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValueDependencies`  
 Výstup. Aspekty interpolator, které jsou závislé na počáteční hodnota předaný SetInitialValueAndVelocity.  
  
 `initialVelocityDependencies`  
 Výstup. Aspekty interpolator, které závisí na rychlosti počáteční předaný SetInitialValueAndVelocity.  
  
 `durationDependencies`  
 Výstup. Aspekty interpolator, které jsou závislé na dobu trvání předaný SetDuration.  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní implementace vždy vrátí hodnotu TRUE. Vrátit FALSE od přepsaného implementace, pokud chcete události nezdaří.  
  
##  <a name="getduration"></a>  CCustomInterpolator::GetDuration  
 Získá dobu trvání interpolator.  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Výstup. Doba trvání přechodu, v sekundách.  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní implementace vždy vrátí hodnotu TRUE. Vrátit FALSE od přepsaného implementace, pokud chcete události nezdaří.  
  
##  <a name="getfinalvalue"></a>  CCustomInterpolator::GetFinalValue  
 Získá konečná hodnota, na který vede interpolator.  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Výstup. Konečná hodnota proměnné na konci přechodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní implementace vždy vrátí hodnotu TRUE. Vrátit FALSE od přepsaného implementace, pokud chcete události nezdaří.  
  
##  <a name="init"></a>  CCustomInterpolator::Init  
 Inicializuje doba trvání a konečná hodnota.  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
 `finalValue`  
 Konečná hodnota proměnné na konci přechodu.  
  
##  <a name="interpolatevalue"></a>  CCustomInterpolator::InterpolateValue  
 Argument interpolaci hodnota na danou posunu.  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>Parametry  
 `value`  
 Výstup. Interpolované hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní implementace vždy vrátí hodnotu TRUE. Vrátit FALSE od přepsaného implementace, pokud chcete události nezdaří.  
  
##  <a name="interpolatevelocity"></a>  CCustomInterpolator::InterpolateVelocity  
 Argument interpolaci rychlosti v daným posunem.  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>Parametry  
 `velocity`  
 Výstup. Rychlosti proměnnou na posunu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní implementace vždy vrátí hodnotu TRUE. Vrátit FALSE od přepsaného implementace, pokud chcete události nezdaří.  
  
##  <a name="m_currentvalue"></a>  CCustomInterpolator::m_currentValue  
 Interpolované hodnota.  
  
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
 Hodnota proměnné na začátku přechodu.  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>  CCustomInterpolator::m_initialVelocity  
 Rychlosti proměnnou na začátku přechodu.  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="setduration"></a>  CCustomInterpolator::SetDuration  
 Nastaví dobu trvání interpolator.  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní implementace vždy vrátí hodnotu TRUE. Vrátit FALSE od přepsaného implementace, pokud chcete události nezdaří.  
  
##  <a name="setinitialvalueandvelocity"></a>  CCustomInterpolator::SetInitialValueAndVelocity  
 Nastaví počáteční hodnotu interpolator a rychlosti.  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>Parametry  
 `initialValue`  
 Hodnota proměnné na začátku přechodu.  
  
 `initialVelocity`  
 Rychlosti proměnnou na začátku přechodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Základní implementace vždy vrátí hodnotu TRUE. Vrátit FALSE od přepsaného implementace, pokud chcete události nezdaří.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
