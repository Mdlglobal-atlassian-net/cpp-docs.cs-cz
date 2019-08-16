---
title: IOleInPlaceObjectWindowlessImpl Class
ms.date: 11/04/2016
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
ms.openlocfilehash: fdd660daae109ac2a656519131dd9869ceaeaf4e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495749"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl Class

Tato třída implementuje `IUnknown` a poskytuje metody, které umožňují řízení bez oken přijímat zprávy oken a zúčastnit se operací přetažení.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IOleInPlaceObjectWindowlessImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Povolí kontextovou Nápověda. Implementace ATL Vrátí E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|`IDropTarget` Poskytuje rozhraní pro místní aktivní objekt bez oken, který podporuje přetahování myší. Implementace ATL Vrátí E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Získá popisovač okna.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Deaktivuje aktivní místní ovládací prvek.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Odesílá zprávu z kontejneru do ovládacího prvku bez oken, který je místně aktivní.|
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Znovu aktivuje dříve deaktivovaný ovládací prvek. Implementace ATL Vrátí E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Označuje, jaká část místního ovládacího prvku je viditelná.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Deaktivuje a odebere uživatelské rozhraní, které podporuje místní aktivaci.|

## <a name="remarks"></a>Poznámky

Rozhraní [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) spravuje opětovnou aktivaci a deaktivaci místních ovládacích prvků a určuje, jak velká část ovládacího prvku by měla být viditelná. Rozhraní [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) umožňuje ovládat bez oken příjem zpráv oken a účast na operacích přetažení. Třída `IOleInPlaceObjectWindowlessImpl` poskytuje výchozí `IOleInPlaceObject` implementaci a `IOleInPlaceObjectWindowless` a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Vrátí E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Poznámky

Viz [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) v Windows SDK.

##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget

Vrátí E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceObjectWindowless:: GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) v Windows SDK.

##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow

Kontejner volá tuto funkci, aby získala popisovač okna ovládacího prvku.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Poznámky

Některé kontejnery nebudou fungovat s ovládacím prvkem, který byl bez okna, i v případě, že je aktuálně okna. V implementaci ATL, pokud je datový člen `m_bWasOnceWindowless` třídy ovládacího prvku true, vrátí funkce E_FAIL. V opačném případě, pokud *phwnd* není `GetWindow` null \* , nastaví *phwnd* na datový člen `m_hWnd` třídy ovládacího prvku a vrátí hodnotu S_OK.

Viz [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) v Windows SDK.

##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate

Volá se kontejnerem, aby se deaktivoval místní aktivní ovládací prvek.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Poznámky

Tato metoda provádí úplnou nebo částečnou deaktivaci v závislosti na stavu ovládacího prvku. V případě potřeby je uživatelské rozhraní ovládacího prvku dezaktivováno a okno ovládacího prvku, pokud je nějaké, je zničeno. Kontejner je upozorněn, že ovládací prvek již není aktivní. `IOleInPlaceUIWindow` Rozhraní používané kontejnerem k vyjednání nabídek a prostoru ohraničení je uvolněno.

Viz [IOleInPlaceObject:: InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) v Windows SDK.

##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Odesílá zprávu z kontejneru do ovládacího prvku bez oken, který je místně aktivní.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceObjectWindowless:: OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) v Windows SDK.

##  <a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo

Vrátí E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceObject:: ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) v Windows SDK.

##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects

Volá se kontejnerem, který informuje ovládací prvek, že se změnila jeho velikost nebo pozice.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Poznámky

Aktualizuje `m_rcPos` datový člen ovládacího prvku a zobrazení ovládacího prvku. Zobrazí se pouze ta část ovládacího prvku, která se protínají oblasti klipu. Pokud byla dříve oříznuta obrazovka ovládacího prvku, ale byl odebrán výstřižek, lze tuto funkci volat pro překreslení celého zobrazení ovládacího prvku.

Viz [IOleInPlaceObject:: SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) v Windows SDK.

##  <a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate

Deaktivuje a odebere uživatelské rozhraní ovládacího prvku, které podporuje místní aktivaci.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Poznámky

Nastaví datový člen `m_bUIActive` třídy ovládacího prvku na hodnotu false. Implementace knihovny ATL této funkce vždy vrátí hodnotu S_OK.

Viz [IOleInPlaceObject:: UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) v Windows SDK.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
