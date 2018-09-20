---
title: Canimationvariablechangehandler – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 23521a9ee9706787df0568547fe3419fe7e4fae5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424596"
---
# <a name="canimationvariablechangehandler-class"></a>Canimationvariablechangehandler – třída

Implementuje zpětné volání, které je voláno rozhraním API animace při změně hodnoty proměnné animace.

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
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Volá se při změně hodnoty proměnné animace. (Přepíše `CUIAnimationVariableChangeHandlerBase::OnValueChanged`.)|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Uchovává ukazatel na řadič animace směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina události je vytvořen a předán `IUIAnimationVariable::SetVariableChangeHandler` při volání metody `CAnimationVariable::EnableValueChangedEvent` nebo `CAnimationBaseObject::EnableValueChangedEvent` (což umožňuje tato událost pro všechny proměnné animace zapouzdřené v objektu animace).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged

Volá se při změně hodnoty proměnné animace.

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>Parametry

*scénáře*<br/>
Scénář, který je proměnné animace.

*Proměnná*<br/>
Proměnné animace, který byl aktualizován.

*newValue*<br/>
Nová hodnota.

*previousValue*<br/>
Předchozí hodnota.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController

Uchovává ukazatel na řadič animace směrování událostí.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na řadič animace, který se zobrazí události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
