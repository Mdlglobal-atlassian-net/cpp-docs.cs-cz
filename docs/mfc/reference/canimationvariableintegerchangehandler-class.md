---
title: Canimationvariableintegerchangehandler – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableIntegerChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableIntegerChangeHandler [MFC], CAnimationVariableIntegerChangeHandler
- CAnimationVariableIntegerChangeHandler [MFC], CreateInstance
- CAnimationVariableIntegerChangeHandler [MFC], OnIntegerValueChanged
- CAnimationVariableIntegerChangeHandler [MFC], SetAnimationController
ms.assetid: 6ac8e91b-e514-4ff6-babd-33f77c4b2b61
ms.openlocfilehash: 66d740d7042ed2e19b6fe3a87345d7abb096f12c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449631"
---
# <a name="canimationvariableintegerchangehandler-class"></a>Canimationvariableintegerchangehandler – třída

Implementuje zpětné volání, které je voláno rozhraním API animace při změně hodnoty proměnné animace.

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
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|Volá se při změně hodnoty proměnné animace. (Přepíše `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`.)|
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Uchovává ukazatel na řadič animace směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina události je vytvořen a předán metodě IUIAnimationVariable::SetVariableIntegerChangeHandler při volání CAnimationVariable::EnableIntegerValueChangedEvent nebo CAnimationBaseObject::EnableIntegerValueChangedEvent (umožňující Tato událost pro všechny proměnné animace zapouzdřené v objektu animace).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[MFC – třídy](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="canimationvariableintegerchangehandler"></a>  CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler

Vytvoří objekt canimationvariableintegerchangehandler –.

```
CAnimationVariableIntegerChangeHandler ();
```

##  <a name="createinstance"></a>  CAnimationVariableIntegerChangeHandler::CreateInstance

Vytvoří instanci canimationvariableintegerchangehandler – zpětného volání.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na řadič animace, který se zobrazí události.

*ppHandler*

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="onintegervaluechanged"></a>  CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged

Volá se při změně hodnoty proměnné animace.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>Parametry

*scénáře*<br/>
Scénář, který je proměnné animace.

*Proměnná*<br/>
Proměnné animace, který byl aktualizován.

*newValue*<br/>
Nové Zaokrouhlená hodnota.

*previousValue*<br/>
Předchozí Zaokrouhlená hodnota.

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje; S_OK jinak E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationVariableIntegerChangeHandler::SetAnimationController

Uchovává ukazatel na řadič animace směrování událostí.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na řadič animace, který se zobrazí události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
