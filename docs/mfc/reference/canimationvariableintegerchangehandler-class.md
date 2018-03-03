---
title: "Třída CAnimationVariableIntegerChangeHandler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d94576c2a831f9e7fa744d0a3c5a50a33809aaa0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler – třída
Implementuje zpětné volání, která je volána rozhraním API animace při změně hodnoty proměnné animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|Vytvoří `CAnimationVariableIntegerChangeHandler` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|Vytvoří instanci `CAnimationVariableIntegerChangeHandler` zpětného volání.|  
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|Voláno, pokud došlo ke změně hodnoty proměnné animace. (Přepisuje `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`.)|  
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel animace řadiče události trasy.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto obslužnou rutinu události se vytvoří a předaný metodě IUIAnimationVariable::SetVariableIntegerChangeHandler, při volání CAnimationVariable::EnableIntegerValueChangedEvent nebo CAnimationBaseObject::EnableIntegerValueChangedEvent (která umožňuje Tato událost pro všechny proměnné animace zapouzdřené v objektu animace).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [MFC – třídy](../../mfc/reference/mfc-classes.md)  
  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableIntegerChangeHandlerBase`  
  
 `CAnimationVariableIntegerChangeHandler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="canimationvariableintegerchangehandler"></a>CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler  
 Vytvoří objekt CAnimationVariableIntegerChangeHandler.  
  
```  
CAnimationVariableIntegerChangeHandler ();
```  
  
##  <a name="createinstance"></a>CAnimationVariableIntegerChangeHandler::CreateInstance  
 Vytvoří instanci CAnimationVariableIntegerChangeHandler zpětného volání.  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Ukazatel na animace řadiči, který bude přijímat události.  
  
 `ppHandler`  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="onintegervaluechanged"></a>CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged  
 Voláno, pokud došlo ke změně hodnoty proměnné animace.  
  
```  
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```  
  
### <a name="parameters"></a>Parametry  
 `storyboard`  
 Scénáře, který je animace proměnnou.  
  
 `variable`  
 Animace proměnné, která byla aktualizována.  
  
 `newValue`  
 Nová hodnota zaokrouhlené.  
  
 `previousValue`  
 Předchozí zaokrouhlené hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. jinak E_FAIL.  
  
##  <a name="setanimationcontroller"></a>CAnimationVariableIntegerChangeHandler::SetAnimationController  
 Ukládá ukazatel animace řadiče události trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 `pAnimationController`  
 Ukazatel na animace řadiči, který bude přijímat události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
