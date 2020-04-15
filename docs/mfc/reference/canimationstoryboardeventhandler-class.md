---
title: CAnimationStoryboardEventHandler – třída
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: 36b8b524591693775403d66fdc1f0754aaf67778
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365005"
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler – třída

Implementuje zpětné volání, které je voláno rozhraní min. animace při změně stavu scénáře nebo je aktualizován scénář.

## <a name="syntax"></a>Syntaxe

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Vytvoří `CAnimationStoryboardEventHandler` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Vytvoří instanci zpětného `CAnimationStoryboardEventHandler` volání.|
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|Zpracovává `OnStoryboardStatusChanged` události, ke kterým dochází při změně stavu `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`scénáře (Přepsání .)|
|[CAnimationStoryboardEventHandler::OnStoryboardAktualizováno](#onstoryboardupdated)|Zpracovává `OnStoryboardUpdated` události, ke kterým dochází při aktualizaci `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`scénáře (lokální změny .)|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Ukládá ukazatel na řadič animace pro směrování událostí.|

## <a name="remarks"></a>Poznámky

Tato obslužná `IUIAnimationStoryboard::SetStoryboardEventHandler` rutina události `CAnimationController::EnableStoryboardEventHandler`je vytvořena a předána metodě při volání .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

Vytvoří objekt CAnimationStoryboardEventHandler.

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance

Vytvoří instanci cAnimationStoryboardEventHandler zpětného volání.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

*ppHandler*

### <a name="return-value"></a>Návratová hodnota

Pokud je metoda úspěšná, vrátí S_OK. V opačném případě vrátí kód chyby HRESULT.

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatusChanged

Zpracovává události OnStoryboardStatusChanged, ke kterým dochází při změně stavu scénáře

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parametry

*Scénáře*<br/>
Ukazatel na scénář, jehož stav se změnil.

*newStatus*<br/>
Určuje nový stav scénáře.

*previousStatus*<br/>
Určuje předchozí stav scénáře.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná; jinak E_FAIL.

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardAktualizováno

Zpracovává OnStoryboardAktualizované události, ke kterým dochází při aktualizaci scénáře

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>Parametry

*Scénáře*<br/>
Ukazatel na scénář, který byl aktualizován.

### <a name="return-value"></a>Návratová hodnota

S_OK pokud je metoda úspěšná; jinak E_FAIL.

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController

Ukládá ukazatel na řadič animace pro směrování událostí.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parametry

*pAnimationController*<br/>
Ukazatel na ovladač animace, který bude přijímat události.

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
