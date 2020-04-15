---
title: Třída IOleInPlaceObjectWindowlessImpl
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
ms.openlocfilehash: b0438692161f38445eb7cbed54edcc8a0ba8c0d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326582"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Třída IOleInPlaceObjectWindowlessImpl

Tato třída `IUnknown` implementuje a poskytuje metody, které umožňují ovládací prvek bez oken přijímat zprávy okna a účastnit se operací přetažení myší.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IOleInPlaceObjectWindowlessImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umožňuje kontextovou nápovědu. Implementace ATL vrátí E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Dodává `IDropTarget` rozhraní pro aktivní objekt bez oken, který podporuje přetažení. Implementace ATL vrátí E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Získá popisovač okna.|
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeaktivovat](#inplacedeactivate)|Deaktivuje aktivní ovládací prvek na místě.|
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Odešle zprávu z kontejneru do ovládacího prvku bez oken, který je aktivní na místě.|
|[IOleInPlaceObjectWindowlessImpl::Znovu aktivovatAndUndo](#reactivateandundo)|Znovu aktivuje dříve deaktivovaný ovládací prvek. Implementace ATL vrátí E_NOTIMPL.|
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Označuje, která část ovládacího prvku na místě je viditelná.|
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Deaktivuje a odebere uživatelské rozhraní, které podporuje aktivaci na místě.|

## <a name="remarks"></a>Poznámky

[Rozhraní IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject) spravuje reaktivaci a deaktivaci ovládacích prvků na místě a určuje, kolik ovládacího prvku by měla být viditelná. [Rozhraní IOleInPlaceObjectLess](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) umožňuje ovládací prvek bez oken přijímat zprávy okna a účastnit se operací přetažení myší. Třída `IOleInPlaceObjectWindowlessImpl` poskytuje výchozí `IOleInPlaceObject` implementaci `IOleInPlaceObjectWindowless` a `IUnknown` implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleInPlaceObjectWindowless`

`IOleInPlaceObjectWindowlessImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ioleinplaceobjectwindowlessimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp

Vrátí E_NOTIMPL.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="remarks"></a>Poznámky

Viz [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) v sadě Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetdroptarget"></a><a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget

Vrátí E_NOTIMPL.

```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceObjectWindowless::GetDropTarget](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) v sadě Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplgetwindow"></a><a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow

Kontejner volá tuto funkci získat popisovač okna ovládacího prvku.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Poznámky

Některé kontejnery nebudou fungovat s ovládacím prvkem, který byl bez oken, i v případě, že je aktuálně windowed. V implementaci ATL pokud je datový člen `m_bWasOnceWindowless` třídy ovládacího prvku TRUE, funkce vrátí E_FAIL. V opačném případě pokud *fwnd* není `GetWindow` NULL, nastaví \* *fwnd* na datový člen `m_hWnd` třídy ovládacího prvku a vrátí S_OK.

Viz [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) v sadě Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplinplacedeactivate"></a><a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeaktivovat

Volána kontejnerem deaktivovat aktivní ovládací prvek na místě.

```
HRESULT InPlaceDeactivate(HWND* phwnd);
```

### <a name="remarks"></a>Poznámky

Tato metoda provádí úplnou nebo částečnou deaktivaci v závislosti na stavu ovládacího prvku. V případě potřeby je uživatelské rozhraní ovládacího prvku deaktivováno a okno ovládacího prvku, pokud existuje, je zničeno. Kontejner je upozorněn, že ovládací prvek již není aktivní na místě. Rozhraní `IOleInPlaceUIWindow` používané kontejneru vyjednat nabídky a ohraničení prostoru je uvolněna.

Viz [IOleInPlaceObject::InPlaceDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) v sadě Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplonwindowmessage"></a><a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage

Odešle zprávu z kontejneru do ovládacího prvku bez oken, který je aktivní na místě.

```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/win32/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) v sadě Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplreactivateandundo"></a><a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::Znovu aktivovatAndUndo

Vrátí E_NOTIMPL.

```
HRESULT ReactivateAndUndo();
```

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceObject::ReactivateAndUndo](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) v sadě Windows SDK.

## <a name="ioleinplaceobjectwindowlessimplsetobjectrects"></a><a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects

Volat kontejneru informovat ovládací prvek, že jeho velikost nebo pozice se změnila.

```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```

### <a name="remarks"></a>Poznámky

Aktualizuje datový člen `m_rcPos` ovládacího prvku a zobrazení ovládacího prvku. Zobrazí se pouze část ovládacího prvku, která protíná oblast klipu. Pokud byl displej ovládacího prvku dříve oříznut, ale oříznutí bylo odebráno, lze tuto funkci volat k překreslení úplného zobrazení ovládacího prvku.

Viz [IOleInPlaceObject::SetObjectRects](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) v sadě Windows SDK.

## <a name="ioleinplaceobjectwindowlessimpluideactivate"></a><a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate

Deaktivuje a odebere uživatelské rozhraní ovládacího prvku, které podporuje aktivaci na místě.

```
HRESULT UIDeactivate();
```

### <a name="remarks"></a>Poznámky

Nastaví datový člen `m_bUIActive` třídy ovládacího prvku na hodnotu NEPRAVDA. Implementace ATL této funkce vždy vrátí S_OK.

Viz [IOleInPlaceObject::UIDeactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
