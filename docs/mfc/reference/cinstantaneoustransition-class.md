---
title: Cinstantaneoustransition – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
dev_langs:
- C++
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f83775e04c7b5c4c104f9790870ea067392b0bce
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209211"
---
# <a name="cinstantaneoustransition-class"></a>Cinstantaneoustransition – třída
Zapouzdřuje okamžitý přechod.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CInstantaneousTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Vytvoří objekt přechodu a inicializuje jeho konečnou hodnotu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CInstantaneousTransition::Create](#create)|Knihovna přechod k vytvoření objektu přechod zapouzdřený objekt modelu COM zavolá. (Přepíše [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Během okamžitý přechod hodnotu proměnné animace změní okamžitě aktuální hodnotu na zadaný konečnou hodnotu. Doba trvání tohoto přechodu je vždycky nula. Protože všechny přechody jsou automaticky vymazány, doporučuje se je přidělena pomocí operátoru nové. Zapouzdřený objekt IUIAnimationTransition COM je vytvořené CAnimationController::AnimateGroup, dokud je NULL. Změna členské proměnné po vytvoření tohoto objektu COM nemá žádný vliv.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cbasetransition –](../../mfc/reference/cbasetransition-class.md)  
  
 [Cinstantaneoustransition –](../../mfc/reference/cinstantaneoustransition-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="cinstantaneoustransition"></a>  CInstantaneousTransition::CInstantaneousTransition  
 Vytvoří objekt přechodu a inicializuje jeho konečnou hodnotu.  
  
```  
CInstantaneousTransition(DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parametry  
 *dblFinalValue*  
 Hodnota proměnné animace na konci přechodu.  
  
##  <a name="create"></a>  CInstantaneousTransition::Create  
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
  
##  <a name="m_dblfinalvalue"></a>  CInstantaneousTransition::m_dblFinalValue  
 Hodnota proměnné animace na konci přechodu.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
