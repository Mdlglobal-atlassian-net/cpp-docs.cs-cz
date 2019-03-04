---
title: Canimationtimereventhandler – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: e5e6b0a22d438f9c26318129e2d04df96d386cda
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264427"
---
# <a name="canimationtimereventhandler-class"></a>Canimationtimereventhandler – třída

Implementuje zpětné volání, které je voláno rozhraním API animace při výskytu události časování.

## <a name="syntax"></a>Syntaxe

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Vytvoří instanci `CAnimationTimerEventHandler` zpětného volání.|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Zpracovává události, ke kterým dochází po dokončení aktualizace animace. (Přepíše `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.)|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Zpracovává události, ke kterým dochází před zahájením aktualizace animace. (Přepíše `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.)|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|Zpracovává události, ke kterým dochází při vykreslování snímkovou frekvenci animace klesne pod minimální kmitočet žádoucí. (Přepíše `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.)|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Uchovává ukazatel na řadič animace směrování událostí.|

## <a name="remarks"></a>Poznámky

Tuto obslužnou rutinu události je vytvořen a předán IUIAnimationTimer::SetTimerEventHandler při volání CAnimationController::EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

##  <a name="createinstance"></a>  CAnimationTimerEventHandler::CreateInstance

Vytvoří instanci canimationtimereventhandler – zpětného volání.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na řadič animace, který se zobrazí události.

*ppTimerEventHandler*

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje, vrátí hodnotu S_OK. V opačném případě vrátí kód chyby HRESULT.

##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate

Zpracovává události, ke kterým dochází po dokončení aktualizace animace.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje; S_OK jinak E_FAIL.

##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate

Zpracovává události, ke kterým dochází před zahájením aktualizace animace.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje; S_OK jinak E_FAIL.

##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow

Zpracovává události, ke kterým dochází při vykreslování snímkovou frekvenci animace klesne pod minimální kmitočet žádoucí.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*snímků za sekundu*

### <a name="return-value"></a>Návratová hodnota

Pokud metoda uspěje; S_OK jinak E_FAIL.

##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController

Uchovává ukazatel na řadič animace směrování událostí.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na řadič animace, který se zobrazí události.

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
