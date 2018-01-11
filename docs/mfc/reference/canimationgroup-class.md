---
title: "Třída CAnimationGroup | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
dev_langs: C++
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d047940ac1ef3103168aa40b53c726ce0767b52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationgroup-class"></a>CAnimationGroup – třída
Implementuje animace skupiny, která spojuje animace storyboard, animace objektů a přechody k definování animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationGroup;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Vytvoří skupinu animace.|  
|[CAnimationGroup:: ~ CAnimationGroup](#canimationgroup__~canimationgroup)|Destruktor. Voláno, když je zničen skupinu animace.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationGroup::Animate](#animate)|Animuje skupinu.|  
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Přechody se vztahuje na animace objektů.|  
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Vyhledá animace objekt, který obsahuje proměnnou zadaný animace.|  
|[CAnimationGroup::GetGroupID](#getgroupid)|Vrátí ID skupiny.|  
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Odebere a volitelně zničí všechny klíčové snímky, které patří do skupiny animace.|  
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Odebere přechody animace objektů, které patří do skupiny animace.|  
|[CAnimationGroup::Schedule](#schedule)|Naplánuje animace v určeném čase.|  
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Přesměruje, že všechny animace objekty, které patří do skupiny automaticky destroy přechody.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Pomocné rutiny, která přidá klíčové snímky scénáře.|  
|[CAnimationGroup::AddTransitions](#addtransitions)|Pomocné rutiny, která přidává přechody do scénáře.|  
|[CAnimationGroup::CreateTransitions](#createtransitions)|Pomocné rutiny, který vytváří objekty modelu COM přechod.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Určuje, jak vymazat přechodů ze animace objektů, které patří do skupiny. Pokud je tato vlastnost hodnotu TRUE, jsou automaticky odebere přechody, když bylo naplánováno animace. V opačném případě je třeba odebrat přechody ručně.|  
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Určuje, jak se zničit animace objektů. Pokud tento parametr hodnotu PRAVDA, animace objektů budou zničena automaticky, když zničena skupině. Animace objektů v opačném případě musí být zničený ručně. Výchozí hodnota je FALSE. Tuto hodnotu nastavte na hodnotu TRUE pouze v případě, že všechny animace objekty, které patří do skupiny jsou dynamicky přiřazen výraz new – operátor.|  
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Určuje, jak se zničit klíčových snímků. Pokud má hodnotu TRUE, jsou všechny klíčové snímky odstranit a zničit; v opačném případě se odeberou ze seznamu jenom. Výchozí hodnota je TRUE.|  
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Obsahuje seznam objektů animace.|  
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Obsahuje seznam klíčových snímků.|  
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Body do scénáře animace. Tento ukazatel je platný pouze po volání animace.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Jedinečný identifikátor skupiny animace.|  
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Ukazatel na animace řadič, ke které tato skupina patří.|  
  
## <a name="remarks"></a>Poznámky  
 Animace skupiny jsou vytvořeny automaticky adaptérem animace (CAnimationController), když přidáte animace objektů s použitím CAnimationController::AddAnimationObject. Skupinu animace je identifikovaná identifikátorem skupiny, které se obvykle považuje za parametr k manipulaci se skupinami animace. Identifikátor skupiny jsou převzaty z první animace objekt, který chcete přidat do nové skupiny animace. Storyboard zapouzdřené animace bude vytvořen po volání CAnimationController::AnimateGroup a je přístupný prostřednictvím veřejného člena m_pStoryboard.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CAnimationGroup`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationgroup"></a>CAnimationGroup:: ~ CAnimationGroup  
 Destruktor. Voláno, když je zničen skupinu animace.  
  
```  
~CAnimationGroup();
```  
  
##  <a name="addkeyframes"></a>CAnimationGroup::AddKeyframes  
 Pomocné rutiny, která přidá klíčové snímky scénáře.  
  
```  
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na objekt storyboard COM.  
  
 `bAddDeep`  
 Určuje, zda tato metoda by měla přidat do scénáře klíčových snímků, které závisí na jiné klíčových snímků.  
  
##  <a name="addtransitions"></a>CAnimationGroup::AddTransitions  
 Pomocné rutiny, která přidává přechody do scénáře.  
  
```  
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na objekt storyboard COM.  
  
 `bDependOnKeyframes`  
  
##  <a name="animate"></a>CAnimationGroup::Animate  
 Animuje skupinu.  
  
```  
BOOL Animate(
    IUIAnimationManager* pManager,  
    IUIAnimationTimer* pTimer,  
    BOOL bScheduleNow);
```  
  
### <a name="parameters"></a>Parametry  
 `pManager`  
 `pTimer`  
 `bScheduleNow`  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda úspěšně. jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří interní storyboard, vytvoří a použije přechody a plány animace, pokud má hodnotu TRUE, bScheduleNow. Pokud bScheduleNow hodnotu FALSE, budete muset volat plán spuštění animace v určeném čase.  
  
##  <a name="applytransitions"></a>CAnimationGroup::ApplyTransitions  
 Přechody se vztahuje na animace objektů.  
  
```  
void ApplyTransitions();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda VYHODNOTÍ v režimu ladění, pokud nebyl vytvořen scénáře. Nejprve vytvoří všechny přechody potom přidá "statická" klíčových snímků (klíčových snímků, které závisí na posuny), přidá přechody, které jsou nezávislé na klíčových snímků, přidá klíčových snímků v závislosti na přechody a dalších klíčových snímků a v poslední přidá přechody, které jsou závislé na klíčových snímků .  
  
##  <a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup  
 Vytvoří skupinu animace.  
  
```  
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentController`  
 Ukazatel na animace řadiče, které vytvoří skupinu.  
  
 `nGroupID`  
 Určuje ID skupiny.  
  
##  <a name="createtransitions"></a>CAnimationGroup::CreateTransitions  
 Pomocné rutiny, který vytváří objekty modelu COM přechod.  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE je metoda bude úspěšná, jinak hodnota FALSE.  
  
##  <a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject  
 Vyhledá animace objekt, který obsahuje proměnnou zadaný animace.  
  
```  
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>Parametry  
 `pVariable`  
 Ukazatel na proměnnou animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na objekt animace nebo hodnota NULL, pokud objekt animace nebyl nalezen.  
  
##  <a name="getgroupid"></a>CAnimationGroup::GetGroupID  
 Vrátí ID skupiny.  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Identifikátor skupiny.  
  
##  <a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions  
 Určuje, jak vymazat přechodů ze animace objektů, které patří do skupiny. Pokud je tato vlastnost hodnotu TRUE, jsou automaticky odebere přechody, když bylo naplánováno animace. V opačném případě je třeba odebrat přechody ručně.  
  
```  
BOOL m_bAutoclearTransitions;  
```  
  
##  <a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects  
 Určuje, jak se zničit animace objektů. Pokud tento parametr hodnotu PRAVDA, animace objektů budou zničena automaticky, když zničena skupině. Animace objektů v opačném případě musí být zničený ručně. Výchozí hodnota je FALSE. Tuto hodnotu nastavte na hodnotu TRUE pouze v případě, že všechny animace objekty, které patří do skupiny jsou dynamicky přiřazen výraz new – operátor.  
  
```  
BOOL m_bAutodestroyAnimationObjects;  
```  
  
##  <a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes  
 Určuje, jak se zničit klíčových snímků. Pokud má hodnotu TRUE, jsou všechny klíčové snímky odstranit a zničit; v opačném případě se odeberou ze seznamu jenom. Výchozí hodnota je TRUE.  
  
```  
BOOL m_bAutodestroyKeyframes;  
```  
  
##  <a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects  
 Obsahuje seznam objektů animace.  
  
```  
CObList m_lstAnimationObjects;  
```  
  
##  <a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames  
 Obsahuje seznam klíčových snímků.  
  
```  
CObList m_lstKeyFrames;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID  
 Jedinečný identifikátor skupiny animace.  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController  
 Ukazatel na animace řadič, ke které tato skupina patří.  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard  
 Body do scénáře animace. Tento ukazatel je platný pouze po volání animace.  
  
```  
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;  
```  
  
##  <a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes  
 Odebere a volitelně zničí všechny klíčové snímky, které patří do skupiny animace.  
  
```  
void RemoveKeyframes();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud m_bAutodestroyKeyframes člen je TRUE klíčových snímků se odeberou a zničen, jinak se klíčových snímků právě odebrat ze seznamu interní klíčových snímků.  
  
##  <a name="removetransitions"></a>CAnimationGroup::RemoveTransitions  
 Odebere přechody animace objektů, které patří do skupiny animace.  
  
```  
void RemoveTransitions();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud je m_bAutoclearTransitions příznak nastaven na hodnotu TRUE, tato metoda cyklicky prochází přes všechny animace objekty, které patří do skupiny a volá CAnimationObject::ClearTransitions(FALSE).  
  
##  <a name="schedule"></a>CAnimationGroup::Schedule  
 Naplánuje animace v určeném čase.  
  
```  
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```  
  
### <a name="parameters"></a>Parametry  
 `pTimer`  
 Ukazatel na časovače animace.  
  
 `time`  
 Určuje čas při plánování animace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda úspěšně. FALSE Pokud metoda selže, nebo pokud postupné animaci nebyla volána s bScheduleNow nastavena na hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce můžete naplánovat animace v určeném čase. Animace musí volat s bScheduleNow nastavena na hodnotu FALSE.  
  
##  <a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions  
 Přesměruje, že všechny animace objekty, které patří do skupiny automaticky destroy přechody.  
  
```  
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bAutoDestroy`  
 Určuje, jak se zničit přechody.  
  
### <a name="remarks"></a>Poznámky  
 Tuto hodnotu nastavte na hodnotu FALSE, pouze v případě, že přidělíte přechody v zásobníku. Výchozí hodnota je TRUE, proto se důrazně doporučuje přidělit přechod objektů pomocí operátoru nové.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
