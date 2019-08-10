---
title: CAnimationManagerEventHandler – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: bd13ba4d0dd60f65372b2c1f51d70d338566301e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916263"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler – třída

Implementuje zpětné volání, které je voláno rozhraním API animace při změně stavu Správce animací.

## <a name="syntax"></a>Syntaxe

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|`CAnimationManagerEventHandler` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Vytvoří instanci `CAnimationManagerEventHandler` objektu.|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Volá se, když se změní stav správce animace. (Overrides `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.)|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel na animační kontroler pro směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina události je vytvořena a předána metodě IUIAnimationManager:: SetManagerEventHandler při volání CAnimationController:: EnableAnimationManagerEvent.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller. h

##  <a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler

Je požadována sada Visual Studio 2010 SP1.

Vytvoří objekt CAnimationManagerEventHandler.

```
CAnimationManagerEventHandler();
```

##  <a name="createinstance"></a>CAnimationManagerEventHandler:: CreateInstance

Je požadována sada Visual Studio 2010 SP1.

Vytvoří instanci objektu CAnimationManagerEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na řadič animace, který obdrží události.

*ppManagerEventHandler*<br/>
Výkonem. Pokud metoda uspěje, obsahuje ukazatel na objekt COM, který bude zpracovávat aktualizace stavu pro správce animací.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler::OnManagerStatusChanged

Je požadována sada Visual Studio 2010 SP1.

Volá se, když se změní stav správce animace.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*newStatus*<br/>
Nový stav

*previousStatus*<br/>
Předchozí stav

### <a name="return-value"></a>Návratová hodnota

Aktuální implementace vždy vrátí hodnotu S_OK;

##  <a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController

Je požadována sada Visual Studio 2010 SP1.

Ukládá ukazatel na animační kontroler pro směrování událostí.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na řadič animace, který obdrží události.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
