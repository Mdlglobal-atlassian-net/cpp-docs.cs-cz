---
title: "Třída CLinearTransition | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::CLinearTransition
- AFXANIMATIONCONTROLLER/CLinearTransition::Create
- AFXANIMATIONCONTROLLER/CLinearTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CLinearTransition [MFC], CLinearTransition
- CLinearTransition [MFC], Create
- CLinearTransition [MFC], m_dblFinalValue
- CLinearTransition [MFC], m_duration
ms.assetid: 7fcb2dba-beb8-4933-9f5d-3b7fb1585ef0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7379c49ef54a86d68e5b9f47a35437befc53d8d8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="clineartransition-class"></a>CLinearTransition – třída
Zapouzdří lineárního přechodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CLinearTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CLinearTransition::CLinearTransition](#clineartransition)|Vytvoří objekt lineárního přechodu a inicializuje se doba trvání a konečná hodnota.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CLinearTransition::Create](#create)|Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM. (Přepisuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CLinearTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|  
|[CLinearTransition::m_duration](#m_duration)|Doba trvání přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Během lineárního přechodu hodnota proměnné animace přechází lineárně od počáteční hodnoty do zadaného konečná hodnota. Protože všechny přechody jsou automaticky vymazány, se doporučuje přidělené je pomocí operátoru nové. Obsah zapouzdřeného objektu IUIAnimationTransition COM vytvoří CAnimationController::AnimateGroup, dokud, pak je NULL. Po vytvoření tohoto objektu COM nemá žádný vliv, změna proměnné členů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CLinearTransition](../../mfc/reference/clineartransition-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="clineartransition"></a>CLinearTransition::CLinearTransition  
 Vytvoří objekt lineárního přechodu a inicializuje se doba trvání a konečná hodnota.  
  
```  
CLinearTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
 `dblFinalValue`  
 Hodnota proměnné animace na konci přechodu.  
  
##  <a name="create"></a>CLinearTransition::Create  
 Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
`pLibrary`  
 Ukazatel na [IUIAnimationTransitionLibrary rozhraní](https://msdn.microsoft.com/library/windows/desktop/dd371897), která definuje knihovnu standardní přechodů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je přechod vytvořen úspěšně; jinak hodnota FALSE.  
  
##  <a name="m_dblfinalvalue"></a>CLinearTransition::m_dblFinalValue  
 Hodnota proměnné animace na konci přechodu.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_duration"></a>CLinearTransition::m_duration  
 Doba trvání přechodu.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
