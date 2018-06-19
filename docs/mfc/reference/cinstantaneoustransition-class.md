---
title: Třída CInstantaneousTransition | Microsoft Docs
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
ms.openlocfilehash: 894d782f0f896837474c24255703a60e228737ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366733"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition – třída
Zapouzdří okamžitou přechodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CInstantaneousTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInstantaneousTransition::CInstantaneousTransition](#cinstantaneoustransition)|Vytvoří objekt přechod a inicializuje jeho konečná hodnota.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CInstantaneousTransition::Create](#create)|Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM. (Přepisuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|Hodnota proměnné animace na konci přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Během okamžitou přechodu hodnota proměnné animace změny okamžitě od aktuální hodnoty zadané konečná hodnota. Trvání tento přechod je vždy nula. Protože všechny přechody jsou automaticky vymazány, se doporučuje přidělené je pomocí operátoru nové. Obsah zapouzdřeného objektu IUIAnimationTransition COM vytvoří CAnimationController::AnimateGroup, dokud, pak je NULL. Po vytvoření tohoto objektu COM nemá žádný vliv, změna proměnné členů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="cinstantaneoustransition"></a>  CInstantaneousTransition::CInstantaneousTransition  
 Vytvoří objekt přechod a inicializuje jeho konečná hodnota.  
  
```  
CInstantaneousTransition(DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>Parametry  
 `dblFinalValue`  
 Hodnota proměnné animace na konci přechodu.  
  
##  <a name="create"></a>  CInstantaneousTransition::Create  
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
  
##  <a name="m_dblfinalvalue"></a>  CInstantaneousTransition::m_dblFinalValue  
 Hodnota proměnné animace na konci přechodu.  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
