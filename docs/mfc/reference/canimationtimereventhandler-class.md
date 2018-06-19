---
title: Třída CAnimationTimerEventHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc0fe5a59a5efedc00850da03be84bb212d4a51f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352096"
---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler – třída
Implementuje zpětné volání, která je volána rozhraním API animace, když dojde k událostem časování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Vytvoří instanci `CAnimationTimerEventHandler` zpětného volání.|  
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Obslužné rutiny události, které se provádějí až po dokončení aktualizace animace. (Přepisuje `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.)|  
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Obslužné rutiny události, které nastaly před zahájením aktualizace animace. (Přepisuje `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.)|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Zpracovává události, které nastaly při vykreslování snímků za sekundu pro animace klesne pod minimální žádoucí snímků za sekundu. (Přepisuje `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.)|  
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel animace řadiče události trasy.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto obslužnou rutinu události je vytvořen a předaný IUIAnimationTimer::SetTimerEventHandler při volání CAnimationController::EnableAnimationTimerEventHandler.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="createinstance"></a>  CAnimationTimerEventHandler::CreateInstance  
 Vytvoří instanci CAnimationTimerEventHandler zpětného volání.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Ukazatel na animace řadiči, který bude přijímat události.  
  
 `ppTimerEventHandler`  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate  
 Obslužné rutiny události, které se provádějí až po dokončení aktualizace animace.  
  
```  
IFACEMETHOD(OnPostUpdate)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. jinak E_FAIL.  
  
##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate  
 Obslužné rutiny události, které nastaly před zahájením aktualizace animace.  
  
```  
IFACEMETHOD(OnPreUpdate)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. jinak E_FAIL.  
  
##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow  
 Zpracovává události, které nastaly při vykreslování snímků za sekundu pro animace klesne pod minimální žádoucí snímků za sekundu.  
  
```  
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```  
  
### <a name="parameters"></a>Parametry  
 `fps`  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. jinak E_FAIL.  
  
##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController  
 Ukládá ukazatel animace řadiče události trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Ukazatel na animace řadiči, který bude přijímat události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
