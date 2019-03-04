---
title: IOleInPlaceActiveObjectImpl Class
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
ms.openlocfilehash: fd0bcb7bb20967128ef3b3cc62722c3b68e728d8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285045"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl Class

Tato třída poskytuje metody pro pomoc komunikace mezi ovládací prvek na místě a jeho kontejneru.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IOleInPlaceActiveObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umožňuje kontextové nápovědy. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Umožňuje nemodálních dialogových oken. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Získá popisovač okna.|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno dokumentu kontejneru. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno rámce nejvyšší úrovně kontejneru. Implementace vrátí ATL|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informuje o ovládacím prvku, které že potřebuje ke změně velikosti jeho okrajů. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Zpracovává zprávy nabídky přístupové klíče z kontejneru. Implementace knihovny ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

[IOleInPlaceActiveObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceactiveobject) rozhraní pomáhá zajistit komunikaci mezi ovládací prvek na místě a jeho kontejneru; například komunikaci aktivní stav ovládacího prvku a kontejner a informuje ovládací prvek potřebuje pro změnu velikosti samotný. Třída `IOleInPlaceActiveObjectImpl` poskytuje výchozí implementaci třídy `IOleInPlaceActiveObject` a podporuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Umožňuje kontextové nápovědy.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) ve Windows SDK.

##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless

Umožňuje nemodálních dialogových oken.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleInPlaceActiveObject::EnableModeless](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) ve Windows SDK.

##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow

Kontejner volá tuto funkci chcete-li získat popisovač okna ovládacího prvku.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Poznámky

S ovládacím prvkem, který je bez oken, i když je aktuálně oddílové nebudou fungovat některé kontejnery. V implementaci ATL Pokud `CComControl::m_bWasOnceWindowless` datový člen je hodnota TRUE, vrátí příslušná funkce E_FAIL. Jinak, pokud \* *phwnd* nemá hodnotu NULL, `GetWindow` přiřadí *phwnd* na datový člen třídy ovládacího prvku `m_hWnd` a vrátí hodnotu S_OK.

Zobrazit [IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) ve Windows SDK.

##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate

Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno dokumentu kontejneru.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) ve Windows SDK.

##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno rámce nejvyšší úrovně kontejneru.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) ve Windows SDK.

##  <a name="resizeborder"></a>  IOleInPlaceActiveObjectImpl::ResizeBorder

Informuje o ovládacím prvku, které že potřebuje ke změně velikosti jeho okrajů.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleInPlaceActiveObject::ResizeBorder](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) ve Windows SDK.

##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator

Zpracovává zprávy nabídky přístupové klíče z kontejneru.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda podporuje následující návratové hodnoty:

S_OK Pokud zprávy byl úspěšně přeložen.

S_FALSE, je-li zprávy nebyl přeložen.

### <a name="remarks"></a>Poznámky

Zobrazit [IOleInPlaceActiveObject::TranslateAccelerator](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní – ovládací prvky ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
