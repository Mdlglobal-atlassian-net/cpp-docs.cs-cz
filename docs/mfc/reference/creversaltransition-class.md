---
title: "Třída CReversalTransition | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fdce13f41e95cda592fec03fcedb01984fb34ab9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creversaltransition-class"></a>CReversalTransition – třída
Zapouzdří stornovací přechod.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CReversalTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CReversalTransition::CReversalTransition](#creversaltransition)|Vytvoří objekt přechod stornovací a inicializuje jeho trvání.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CReversalTransition::Create](#create)|Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM. (Přepisuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CReversalTransition::m_duration](#m_duration)|Doba trvání přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Přechod stornovací plynule změní směr na danou dobu trvání. Konečná hodnota bude stejné jako počáteční hodnota a bude konečné rychlosti záporné počáteční rychlosti. Protože všechny přechody jsou automaticky vymazány, se doporučuje přidělené je pomocí operátoru nové. Obsah zapouzdřeného objektu IUIAnimationTransition COM vytvoří CAnimationController::AnimateGroup, dokud, pak je NULL. Po vytvoření tohoto objektu COM nemá žádný vliv, změna proměnné členů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CReversalTransition](../../mfc/reference/creversaltransition-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="create"></a>CReversalTransition::Create  
 Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
 `pLibrary`  
 Ukazatel na přechod knihovny, která zodpovídá za vytvoření standardní přechodů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je přechod vytvořen úspěšně; jinak hodnota FALSE.  
  
##  <a name="creversaltransition"></a>CReversalTransition::CReversalTransition  
 Vytvoří objekt přechod stornovací a inicializuje jeho trvání.  
  
```  
CReversalTransition(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
##  <a name="m_duration"></a>CReversalTransition::m_duration  
 Doba trvání přechodu.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
