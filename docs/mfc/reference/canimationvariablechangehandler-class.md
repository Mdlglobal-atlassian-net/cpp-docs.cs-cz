---
title: CAnimationVariableChangeHandler – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 2dc8f2c03f9df34012fb9db1ed5e5b0bb448b17f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755041"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler – třída

Implementuje zpětné volání, které je voláno rozhraním API animace při změně hodnoty proměnné animace.

## <a name="syntax"></a>Syntaxe

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|Vytvoří `CAnimationVariableChangeHandler` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|Vytvoří instanci objektu. `CAnimationVariableChangeHandler`|
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|Nazývá se při změně hodnoty proměnné animace. (Přepíše `CUIAnimationVariableChangeHandlerBase::OnValueChanged`.)|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel na řadič animace pro směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná `IUIAnimationVariable::SetVariableChangeHandler` rutina události `CAnimationVariable::EnableValueChangedEvent` je `CAnimationBaseObject::EnableValueChangedEvent` vytvořena a předána metodě, když voláte nebo (což umožňuje tuto událost pro všechny proměnné animace zapouzdřené v objektu animace).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationvariablechangehandleronvaluechanged"></a><a name="onvaluechanged"></a>CAnimationVariableChangeHandler::OnValueChanged

Nazývá se při změně hodnoty proměnné animace.

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>Parametry

*Scénáře*<br/>
Scénář, který animuje proměnnou.

*Proměnné*<br/>
Proměnná animace, která byla aktualizována.

*Newvalue*<br/>
Nová hodnota.

*předchozíhodnota*<br/>
Předchozí hodnota.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="canimationvariablechangehandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationVariableChangeHandler::SetAnimationController

Ukládá ukazatel na řadič animace pro směrování událostí.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
