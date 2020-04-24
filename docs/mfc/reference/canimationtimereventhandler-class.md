---
title: Třída CAnimationTimerEventHandler
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
ms.openlocfilehash: d1653e50fef03deb8eb23dd9a989d1ca2a529dd8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755088"
---
# <a name="canimationtimereventhandler-class"></a>Třída CAnimationTimerEventHandler

Implementuje zpětné volání, které je voláno rozhraním API animace při výskytu událostí časování.

## <a name="syntax"></a>Syntaxe

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CanimationeventHandler::CreateInstance](#createinstance)|Vytvoří instanci zpětného `CAnimationTimerEventHandler` volání.|
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|Zpracovává události, ke kterým dochází po dokončení aktualizace animace. (Přepíše `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.)|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|Zpracovává události, ke kterým dochází před zahájením aktualizace animace. (Přepíše `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.)|
|[CanimationtimerEventHandler::OnRenderingTooslow](#onrenderingtooslow)|Zpracovává události, ke kterým dochází, když kmitočet snímků vykreslování pro animaci klesne pod minimální žádoucí kmitočet snímků. (Přepíše `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.)|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel na řadič animace pro směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná rutina události je vytvořena a předána iUIAnimationTimer::SetTimerEventHandler při volání CAnimationController::EnableAnimationTimerEventHandler.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a>CanimationeventHandler::CreateInstance

Vytvoří instanci zpětného volání CAnimationTimerEventHandler.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

*phandler s událostí ppTimer*

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a>CAnimationTimerEventHandler::OnPostUpdate

Zpracovává události, ke kterým dochází po dokončení aktualizace animace.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná; jinak E_FAIL.

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a>CAnimationTimerEventHandler::OnPreUpdate

Zpracovává události, ke kterým dochází před zahájením aktualizace animace.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná; jinak E_FAIL.

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a>CanimationtimerEventHandler::OnRenderingTooslow

Zpracovává události, ke kterým dochází, když kmitočet snímků vykreslování pro animaci klesne pod minimální žádoucí kmitočet snímků.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Parametry

*Fps*

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná; jinak E_FAIL.

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationTimerEventHandler::SetAnimationController

Ukládá ukazatel na řadič animace pro směrování událostí.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
