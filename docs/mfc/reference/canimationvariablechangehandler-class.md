---
title: Třída CAnimationVariableChangeHandler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58646efaaa0087be2bd73e45acd8ade4a16e9767
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957088"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler – třída
Implementuje zpětné volání, která je volána rozhraním API animace při změně hodnoty proměnné animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Vytvoří `CAnimationVariableChangeHandler` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|`CAnimationVariableChangeHandler::CreateInstance`|Vytvoří instanci `CAnimationVariableChangeHandler` objektu.|  
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Voláno, pokud došlo ke změně hodnoty proměnné animace. (Přepisuje `CUIAnimationVariableChangeHandlerBase::OnValueChanged`.)|  
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel animace řadiče události trasy.|  
  
## <a name="remarks"></a>Poznámky  
 Tuto obslužnou rutinu události se vytvoří a předaný `IUIAnimationVariable::SetVariableChangeHandler` při volání metody `CAnimationVariable::EnableValueChangedEvent` nebo `CAnimationBaseObject::EnableValueChangedEvent` (což umožňuje tato událost pro všechny proměnné animace zapouzdřené v objektu animace).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationVariableChangeHandlerBase`  
  
 `CAnimationVariableChangeHandler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged  
 Voláno, pokud došlo ke změně hodnoty proměnné animace.  
  
```  
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```  
  
### <a name="parameters"></a>Parametry  
 *scénáře*  
 Scénáře, který je animace proměnnou.  
  
 *Proměnná*  
 Animace proměnné, která byla aktualizována.  
  
 *newValue*  
 Nová hodnota.  
  
 *previousValue*  
 Předchozí hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud metoda bude úspěšná, vrátí S_OK. Funkce HRESULT chybový kód.  
  
##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController  
 Ukládá ukazatel animace řadiče události trasy.  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>Parametry  
 *pAnimationController*  
 Ukazatel na animace řadiči, který bude přijímat události.  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
