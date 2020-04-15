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
ms.openlocfilehash: a4e97c2a1188071b5bde0781630d0dfe52e8a72f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369712"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler – třída

Implementuje zpětné volání, které je voláno rozhraním API animace při změně stavu správce animací.

## <a name="syntax"></a>Syntaxe

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Vytvoří `CAnimationManagerEventHandler` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CanimationManagerEventHandler::CreateInstance](#createinstance)|Vytvoří instanci objektu. `CAnimationManagerEventHandler`|
|[CanimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Nazývá se při změně stavu správce animací. (Přepíše `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.)|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel na řadič animace pro směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina události je vytvořena a předána metodě IUIAnimationManager::SetManagerEventHandler při volání CAnimationController::EnableAnimationManagerEvent.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationmanagereventhandlercanimationmanagereventhandler"></a><a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler

Je požadována sada Visual Studio 2010 SP1.

Vytvoří objekt CAnimationManagerEventHandler.

```
CAnimationManagerEventHandler();
```

## <a name="canimationmanagereventhandlercreateinstance"></a><a name="createinstance"></a>CanimationManagerEventHandler::CreateInstance

Je požadována sada Visual Studio 2010 SP1.

Vytvoří instanci objektu CAnimationManagerEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

*pManagerEventHandler*<br/>
Výstup. Pokud je metoda úspěšná, obsahuje ukazatel na objekt COM, který bude zpracovávat aktualizace stavu správce animací.

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="canimationmanagereventhandleronmanagerstatuschanged"></a><a name="onmanagerstatuschanged"></a>CanimationManagerEventHandler::OnManagerStatusChanged

Je požadována sada Visual Studio 2010 SP1.

Nazývá se při změně stavu správce animací.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*newStatus*<br/>
Nový stav.

*previousStatus*<br/>
Předchozí stav.

### <a name="return-value"></a>Návratová hodnota

Aktuální implementace vždy vrátí S_OK;

## <a name="canimationmanagereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController

Je požadována sada Visual Studio 2010 SP1.

Ukládá ukazatel na řadič animace pro směrování událostí.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
