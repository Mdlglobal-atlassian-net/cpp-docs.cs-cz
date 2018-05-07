---
title: CAccelerateDecelerateTransition Class1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
dev_langs:
- C++
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1dac40e91dd7b0a91c5d76b0d665d075e562267
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition – třída
Implementuje accelerate-zpomalení přechodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAccelerateDecelerateTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Vytvoří objekt přechodu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::Create](#create)|Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM. (Přepisuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|Poměr čas strávený urychlení na dobu trvání.|  
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|Poměr čas strávený zpomaluje na dobu trvání.|  
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|Doba trvání přechodu.|  
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|Hodnota proměnné animace na konci přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Během accelerate-zpomalení přechodu, proměnnou animace urychluje a pak zpomaluje za celou dobu přechodu, končí zadanou hodnotou. Můžete řídit, jak rychle proměnnou zrychluje a zpomaluje nezávisle, zadáním jiné akcelerace a zpomalení poměry. Při počáteční rychlost je nulová, poměr akcelerace je podíl dobu, která bude proměnná tráví urychlení; Podobně se zpomalení poměr. Pokud počáteční rychlosti je nulová, je zlomek času mezi rychlosti dosažení nula a na konci přechodu. Akcelerace poměr a zpomalení poměr by měl součet, kterou se maximálně 1.0. Protože všechny přechody jsou automaticky vymazány, se doporučuje přidělené je pomocí operátoru nové. Obsah zapouzdřeného objektu IUIAnimationTransition COM vytvoří CAnimationController::AnimateGroup, dokud, pak je NULL. Po vytvoření tohoto objektu COM nemá žádný vliv, změna proměnné členů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CAccelerateDecelerateTransition`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition  
 Vytvoří objekt přechodu.  
  
```  
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE accelerationRatio = 0.3,  
    DOUBLE decelerationRatio = 0.3);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
 `finalValue`  
 Hodnota proměnné animace na konci přechodu.  
  
 `accelerationRatio`  
 Poměr čas strávený urychlení na dobu trvání.  
  
 `decelerationRatio`  
 Poměr čas strávený zpomaluje na dobu trvání.  
  
##  <a name="create"></a>  CAccelerateDecelerateTransition::Create  
 Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* *\not used*\);
```  
  
### <a name="parameters"></a>Parametry  
`pLibrary`  
 Ukazatel na [IUIAnimationTransitionLibrary rozhraní](https://msdn.microsoft.com/library/windows/desktop/dd371897), která definuje knihovnu standardní přechodů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je přechod vytvořen úspěšně; jinak hodnota FALSE.  
  
##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio  
 Poměr čas strávený urychlení na dobu trvání.  
  
```  
DOUBLE m_accelerationRatio;  
```  
  
##  <a name="m_decelerationratio"></a>  CAccelerateDecelerateTransition::m_decelerationRatio  
 Poměr čas strávený zpomaluje na dobu trvání.  
  
```  
DOUBLE m_decelerationRatio;  
```  
  
##  <a name="m_duration"></a>  CAccelerateDecelerateTransition::m_duration  
 Doba trvání přechodu.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue  
 Hodnota proměnné animace na konci přechodu.  
  
```  
DOUBLE m_finalValue;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
