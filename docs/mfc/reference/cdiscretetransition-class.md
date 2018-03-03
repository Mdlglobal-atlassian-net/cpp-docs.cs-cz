---
title: "Třída CDiscreteTransition | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
dev_langs:
- C++
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd4b1b7c868c13176d2cd99204b0bae1e2b9992d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition – třída
Zapouzdří diskrétní přechod.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|Vytvoří objekt diskrétní přechod a inicializuje jeho parametry.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDiscreteTransition::Create](#create)|Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM. (Přepisuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|  
|[CDiscreteTransition::m_delay](#m_delay)|Množství času, podle kterého zpoždění okamžitou přepínač tak, aby konečná hodnota.|  
|[CDiscreteTransition::m_hold](#m_hold)|Množství času, podle kterého pro uložení proměnné v jeho konečná hodnota.|  
  
## <a name="remarks"></a>Poznámky  
 Během diskrétní přechodu proměnnou animace zůstává na počáteční hodnotu pro zadaný zpoždění a pak přepne okamžitě do zadaného konečná hodnota a zůstane na tuto hodnotu po dobu uchování dané. Protože všechny přechody jsou automaticky vymazány, se doporučuje přidělené je pomocí operátoru nové. Obsah zapouzdřeného objektu IUIAnimationTransition COM vytvoří CAnimationController::AnimateGroup, dokud, pak je NULL. Po vytvoření tohoto objektu COM nemá žádný vliv, změna proměnné členů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="cdiscretetransition"></a>CDiscreteTransition::CDiscreteTransition  
 Vytvoří objekt diskrétní přechod a inicializuje jeho parametry.  
  
```  
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,  
    DOUBLE dblFinalValue,  
    UI_ANIMATION_SECONDS hold);
```  
  
### <a name="parameters"></a>Parametry  
 `delay`  
 Množství času, podle kterého zpoždění okamžitou přepínač tak, aby konečná hodnota.  
  
 `dblFinalValue`  
 Hodnota proměnné animace na konci přechodu.  
  
 `hold`  
 Množství času, podle kterého pro uložení proměnné v jeho konečná hodnota.  
  
##  <a name="create"></a>CDiscreteTransition::Create  
 Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
`pLibrary`  
 Ukazatel na [IUIAnimationTransitionLibrary rozhraní](https://msdn.microsoft.com/library/windows/desktop/dd371897), která definuje knihovnu standardní přechodů.  

  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je přechod vytvořen úspěšně; jinak hodnota FALSE.  
  
##  <a name="m_dblfinalvalue"></a>CDiscreteTransition::m_dblFinalValue  
 Hodnota proměnné animace na konci přechodu.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_delay"></a>CDiscreteTransition::m_delay  
 Množství času, podle kterého zpoždění okamžitou přepínač tak, aby konečná hodnota.  
  
```  
UI_ANIMATION_SECONDS m_delay;  
```  
  
##  <a name="m_hold"></a>CDiscreteTransition::m_hold  
 Množství času, podle kterého pro uložení proměnné v jeho konečná hodnota.  
  
```  
UI_ANIMATION_SECONDS m_hold;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
