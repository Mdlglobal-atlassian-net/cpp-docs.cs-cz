---
title: Třída IOleInPlaceActiveObjectImpl
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
ms.openlocfilehash: b39ba2845a5483444dac53d1616654e902969c77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326590"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>Třída IOleInPlaceActiveObjectImpl

Tato třída poskytuje metody pro usnadnění komunikace mezi místním ovládacím prvkem a jeho kontejnerem.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IOleInPlaceActiveObjectImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iOleInPlaceActiveObjectImpl::kontextová nápověda](#contextsensitivehelp)|Umožňuje kontextovou nápovědu. Implementace ATL vrátí E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Povolí nemodální dialogová okna. Implementace ATL vrátí S_OK.|
|[iOleInplaceActiveObjectImpl::GetWindow](#getwindow)|Získá popisovač okna.|
|[iOleInPlaceActiveObjectImpl::OndocWindowActivate](#ondocwindowactivate)|Upozorní ovládací prvek, když je okno dokumentu kontejneru aktivováno nebo deaktivováno. Implementace ATL vrátí S_OK.|
|[iOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Upozorní ovládací prvek, když je aktivováno nebo deaktivováno okno rámce nejvyšší úrovně kontejneru. Implementace ATL vrací|
|[IOleInPlaceActiveObjectImpl::Změna velikostiOhraničení](#resizeborder)|Informuje ovládací prvek, který potřebuje ke změně velikosti svých hranic. Implementace ATL vrátí S_OK.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Zpracuje zprávy s klíčem akcelerátoru nabídky z kontejneru. Implementace ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

[Rozhraní IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) pomáhá komunikaci mezi ovládacím prvkem na místě a jeho kontejnerem; například komunikace aktivnístav ovládacího prvku a kontejneru a informování ovládacího prvku, který potřebuje změnit velikost sám. Třída `IOleInPlaceActiveObjectImpl` poskytuje výchozí `IOleInPlaceActiveObject` implementaci `IUnknown` a podporuje odesíláním informací do zařízení s výpisem stavu paměti v sestaveníladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ioleinplaceactiveobjectimplcontextsensitivehelp"></a><a name="contextsensitivehelp"></a>iOleInPlaceActiveObjectImpl::kontextová nápověda

Umožňuje kontextovou nápovědu.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleWindow::ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) v sadě Windows SDK.

## <a name="ioleinplaceactiveobjectimplenablemodeless"></a><a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless

Povolí nemodální dialogová okna.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject::EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) v sadě Windows SDK.

## <a name="ioleinplaceactiveobjectimplgetwindow"></a><a name="getwindow"></a>iOleInplaceActiveObjectImpl::GetWindow

Kontejner volá tuto funkci získat popisovač okna ovládacího prvku.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Poznámky

Některé kontejnery nebudou fungovat s ovládacím prvkem, který byl bez oken, i v případě, že je aktuálně windowed. V implementaci ATL, pokud `CComControl::m_bWasOnceWindowless` je datový člen TRUE, funkce vrátí E_FAIL. V opačném \* případě pokud *fwnd* není NULL, `GetWindow` přiřadí *fwnd* do datového člena `m_hWnd` třídy ovládacího prvku a vrátí S_OK.

Viz [IOleWindow::GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) v sadě Windows SDK.

## <a name="ioleinplaceactiveobjectimplondocwindowactivate"></a><a name="ondocwindowactivate"></a>iOleInPlaceActiveObjectImpl::OndocWindowActivate

Upozorní ovládací prvek, když je okno dokumentu kontejneru aktivováno nebo deaktivováno.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject::OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) v sadě Windows SDK.

## <a name="ioleinplaceactiveobjectimplonframewindowactivate"></a><a name="onframewindowactivate"></a>iOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Upozorní ovládací prvek, když je aktivováno nebo deaktivováno okno rámce nejvyšší úrovně kontejneru.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject::OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) v sadě Windows SDK.

## <a name="ioleinplaceactiveobjectimplresizeborder"></a><a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::Změna velikostiOhraničení

Informuje ovládací prvek, který potřebuje ke změně velikosti svých hranic.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject::ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) v sadě Windows SDK.

## <a name="ioleinplaceactiveobjectimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator

Zpracuje zprávy s klíčem akcelerátoru nabídky z kontejneru.

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda podporuje následující vrácené hodnoty:

S_OK, pokud byla zpráva úspěšně přeložena.

S_FALSE, pokud zpráva nebyla přeložena.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject::TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
