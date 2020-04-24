---
title: CAnimationVariableIntegerChangeHandler – třída
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
ms.openlocfilehash: dec940d2f5e68f0531fc917df447b5a1a5cb8189
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755054"
---
# <a name="canimationvariableintegerchangehandler-class"></a>CAnimationVariableIntegerChangeHandler – třída

Implementuje zpětné volání, které je voláno rozhraním API animace při změně hodnoty proměnné animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariableIntegerChangeHandler : public CUIAnimationVariableIntegerChangeHandlerBase<CAnimationVariableIntegerChangeHandler>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler](#canimationvariableintegerchangehandler)|Vytvoří `CAnimationVariableIntegerChangeHandler` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationVariableIntegerChangeHandler::CreateInstance](#createinstance)|Vytvoří instanci zpětného `CAnimationVariableIntegerChangeHandler` volání.|
|[CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged](#onintegervaluechanged)|Nazývá se při změně hodnoty proměnné animace. (Přepíše `CUIAnimationVariableIntegerChangeHandlerBase::OnIntegerValueChanged`.)|
|[CAnimationVariableIntegerChangeHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel na řadič animace pro směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina události je vytvořena a předána metodě IUIAnimationVariable::SetVariableIntegerChangeHandler, když voláte CAnimationVariable::EnableIntegerValueChangedEvent nebo CAnimationBaseObject::EnableIntegerValueChangedEvent (která umožňuje tuto událost pro všechny proměnné animace zapouzdřené v objektu animace).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy knihovny MFC](../../mfc/reference/mfc-classes.md)

`CUIAnimationCallbackBase`

`CUIAnimationVariableIntegerChangeHandlerBase`

`CAnimationVariableIntegerChangeHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationvariableintegerchangehandlercanimationvariableintegerchangehandler"></a><a name="canimationvariableintegerchangehandler"></a>CAnimationVariableIntegerChangeHandler::CAnimationVariableIntegerChangeHandler

Vytvoří objekt CAnimationVariableIntegerChangeHandler.

```
CAnimationVariableIntegerChangeHandler ();
```

## <a name="canimationvariableintegerchangehandlercreateinstance"></a><a name="createinstance"></a>CAnimationVariableIntegerChangeHandler::CreateInstance

Vytvoří instanci zpětného volání CAnimationVariableIntegerChangeHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationVariableIntegerChangeHandler** ppHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

*ppHandler*

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="canimationvariableintegerchangehandleronintegervaluechanged"></a><a name="onintegervaluechanged"></a>CAnimationVariableIntegerChangeHandler::OnIntegerValueChanged

Nazývá se při změně hodnoty proměnné animace.

```
IFACEMETHOD(OnIntegerValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in INT32 newValue,
    __in INT32 previousValue);
```

### <a name="parameters"></a>Parametry

*Scénáře*<br/>
Scénář, který animuje proměnnou.

*Proměnné*<br/>
Proměnná animace, která byla aktualizována.

*Newvalue*<br/>
Nová zaokrouhlená hodnota.

*předchozíhodnota*<br/>
Předchozí zaokrouhlená hodnota.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná; jinak E_FAIL.

## <a name="canimationvariableintegerchangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableIntegerChangeHandler::SetAnimationController

Ukládá ukazatel na řadič animace pro směrování událostí.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
