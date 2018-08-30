---
title: Cconstanttransition – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::CConstantTransition
- AFXANIMATIONCONTROLLER/CConstantTransition::Create
- AFXANIMATIONCONTROLLER/CConstantTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CConstantTransition [MFC], CConstantTransition
- CConstantTransition [MFC], Create
- CConstantTransition [MFC], m_duration
ms.assetid: f6fa4780-a71b-4cd6-80aa-d4792ace36c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc7e4104e6555ada88483336917708db943be2a0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210576"
---
# <a name="cconstanttransition-class"></a>Cconstanttransition – třída
Zapouzdřuje konstantní přechod.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CConstantTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CConstantTransition::CConstantTransition](#cconstanttransition)|Vytvoří objekt přechodu a inicializuje vlastnost duration.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CConstantTransition::Create](#create)|Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CConstantTransition::m_duration](#m_duration)|Doba trvání přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Během konstantní přechod hodnota proměnné animace zůstává na počáteční hodnotu na dobu trvání přechodu. Protože všechny přechody jsou automaticky vymazány, doporučuje se je přidělena pomocí operátoru nové. Zapouzdřený objekt IUIAnimationTransition COM je vytvořené CAnimationController::AnimateGroup, dokud je NULL. Změna členské proměnné po vytvoření tohoto objektu COM nemá žádný vliv.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cbasetransition –](../../mfc/reference/cbasetransition-class.md)  
  
 `CConstantTransition`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="cconstanttransition"></a>  CConstantTransition::CConstantTransition  
 Vytvoří objekt přechodu a inicializuje vlastnost duration.  
  
```  
CConstantTransition (UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>Parametry  
 *Doba trvání*  
 Doba trvání přechodu.  
  
##  <a name="create"></a>  CConstantTransition::Create  
 Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá.  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>Parametry  
 *pLibrary*  
 Ukazatel na [IUIAnimationTransitionLibrary rozhraní](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), která definuje knihovnu standardní přechodů.  

### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud úspěšně; vytvoření přechodu v opačném případě FALSE.  
  
##  <a name="m_duration"></a>  CConstantTransition::m_duration  
 Doba trvání přechodu.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
