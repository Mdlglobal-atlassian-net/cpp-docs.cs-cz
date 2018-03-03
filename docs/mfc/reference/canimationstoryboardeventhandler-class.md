---
title: "Třída CAnimationStoryboardEventHandler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 599164d1bb2eca17b935fc74f13fe9b134fc4f2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler – třída
Implementuje zpětné volání, která je volána rozhraním API animace, když se změní stav storyboard nebo se aktualizuje scénáře.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Vytvoří `CAnimationStoryboardEventHandler` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Vytvoří instanci `CAnimationStoryboardEventHandler` zpětného volání.|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Zpracovává `OnStoryboardStatusChanged` událostí, ke kterým dochází při změně stavu storyboard (přepíše `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`.)|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|Zpracovává `OnStoryboardUpdated` událostí, ke kterým dochází při aktualizaci scénáře (přepíše `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.)|  
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel animace řadiče události trasy.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto obslužnou rutinu události se vytvoří a předaný `IUIAnimationStoryboard::SetStoryboardEventHandler` při volání metody `CAnimationController::EnableStoryboardEventHandler`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler  
 Vytvoří objekt CAnimationStoryboardEventHandler.  
  
```  
CAnimationStoryboardEventHandler();
```  
  
##  <a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance  
 Vytvoří instanci CAnimationStoryboardEventHandler zpětného volání.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationStoryboardEventHandler** ppHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Ukazatel na animace řadiči, který bude přijímat události.  
  
 `ppHandler`  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatusChanged  
 Zpracovává OnStoryboardStatusChanged událostí, ke kterým dochází při změně stavu scénáře  
  
```  
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>Parametry  
 `storyboard`  
 Ukazatel na scénáře, jejichž stav se změnil.  
  
 `newStatus`  
 Určuje stav nové scénáře.  
  
 `previousStatus`  
 Určuje předchozí stav scénáře.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. jinak E_FAIL.  
  
##  <a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardUpdated  
 Zpracovává OnStoryboardUpdated událostí, ke kterým dochází při aktualizaci scénáře  
  
```  
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```  
  
### <a name="parameters"></a>Parametry  
 `storyboard`  
 Ukazatel na scénáře, který byl aktualizován.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. jinak E_FAIL.  
  
##  <a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController  
 Ukládá ukazatel animace řadiče události trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Ukazatel na animace řadiči, který bude přijímat události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
