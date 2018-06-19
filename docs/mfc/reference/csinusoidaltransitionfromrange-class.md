---
title: Třída CSinusoidalTransitionFromRange | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09c302ec414e26c71d8989bb6d624314c8eb6db4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370204"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange – třída
Zapouzdří vlnovitě rozsah přechodu, který má zadaný rozsah kývání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSinusoidalTransitionFromRange : public CBaseTransition;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|Vytvoří objekt přechodu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::Create](#create)|Volá knihovně přechod k vytvoření objektu zapouzdřené přechod COM. (Přepisuje [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|Hodnota proměnné animace na vrcholu vlnovitě wave.|  
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|Hodnota proměnné animace v žlábku vlnovitě tvaru.|  
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|Doba trvání přechodu.|  
|[CSinusoidalTransitionFromRange::m_period](#m_period)|Období kmitání vlnovitě wave v sekundách.|  
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|Sklon na začátku přechodu.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota proměnné animace kolísá mezi zadaná minimální a maximální hodnoty přes celou dobu trvání přechod vlnovitě rozsahu. Parametr sklon se používá k rozlišení mezi dvě možné vlny sinus určeného ostatní parametry. Protože všechny přechody jsou automaticky vymazány, se doporučuje přidělené je pomocí operátoru nové. Obsah zapouzdřeného objektu IUIAnimationTransition COM vytvoří CAnimationController::AnimateGroup, dokud, pak je NULL. Po vytvoření tohoto objektu COM nemá žádný vliv, změna proměnné členů.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="create"></a>  CSinusoidalTransitionFromRange::Create  
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
  
##  <a name="csinusoidaltransitionfromrange"></a>  CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange  
 Vytvoří objekt přechodu.  
  
```  
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE dblMinimumValue,  
    DOUBLE dblMaximumValue,  
    UI_ANIMATION_SECONDS period,  
    UI_ANIMATION_SLOPE slope);
```  
  
### <a name="parameters"></a>Parametry  
 `duration`  
 Doba trvání přechodu.  
  
 `dblMinimumValue`  
 Hodnota proměnné animace v žlábku vlnovitě tvaru.  
  
 `dblMaximumValue`  
 Hodnota proměnné animace na vrcholu vlnovitě wave.  
  
 `period`  
 Období kmitání vlnovitě wave v sekundách.  
  
 `slope`  
 Sklon na začátku přechodu.  
  
##  <a name="m_dblmaximumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMaximumValue  
 Hodnota proměnné animace na vrcholu vlnovitě wave.  
  
```  
DOUBLE m_dblMaximumValue;  
```  
  
##  <a name="m_dblminimumvalue"></a>  CSinusoidalTransitionFromRange::m_dblMinimumValue  
 Hodnota proměnné animace v žlábku vlnovitě tvaru.  
  
```  
DOUBLE m_dblMinimumValue;  
```  
  
##  <a name="m_duration"></a>  CSinusoidalTransitionFromRange::m_duration  
 Doba trvání přechodu.  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_period"></a>  CSinusoidalTransitionFromRange::m_period  
 Období kmitání vlnovitě wave v sekundách.  
  
```  
UI_ANIMATION_SECONDS m_period;  
```  
  
##  <a name="m_slope"></a>  CSinusoidalTransitionFromRange::m_slope  
 Sklon na začátku přechodu.  
  
```  
UI_ANIMATION_SLOPE m_slope;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
