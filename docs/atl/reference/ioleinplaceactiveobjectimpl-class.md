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
ms.openlocfilehash: f52638c8a28652cc958ebb3d774319ab37a3c46d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495763"
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl Class

Tato třída poskytuje metody pro pomoc s komunikací mezi místně umístěným ovládacím prvkem a jeho kontejnerem.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IOleInPlaceActiveObjectImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IOleInPlaceActiveObjectImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Povolí kontextovou Nápověda. Implementace ATL Vrátí E_NOTIMPL.|
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Umožňuje používat nemodální dialogová okna. Implementace ATL vrací S_OK.|
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Získá popisovač okna.|
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno dokumentu kontejneru. Implementace ATL vrací S_OK.|
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno rámce nejvyšší úrovně kontejneru. Implementace ATL vrátí|
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Informuje ovládací prvek, který potřebuje pro změnu velikosti ohraničení. Implementace ATL vrací S_OK.|
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Procesy – klíčové zprávy z kontejneru v nabídce procesy Implementace ATL Vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Rozhraní [IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject) pomáhá komunikovat mezi místně umístěným ovládacím prvkem a jeho kontejnerem. například komunikace s aktivním stavem ovládacího prvku a kontejneru a informování ovládacího prvku, který potřebuje změnit velikost samotného. Třída `IOleInPlaceActiveObjectImpl` poskytuje výchozí `IOleInPlaceActiveObject` implementaci a podporuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IOleInPlaceActiveObject`

`IOleInPlaceActiveObjectImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="contextsensitivehelp"></a>  IOleInPlaceActiveObjectImpl::ContextSensitiveHelp

Povolí kontextovou Nápověda.

```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IOleWindow:: ContextSensitiveHelp](/windows/win32/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) v Windows SDK.

##  <a name="enablemodeless"></a>  IOleInPlaceActiveObjectImpl::EnableModeless

Umožňuje používat nemodální dialogová okna.

```
HRESULT EnableModeless(BOOL fEnable);
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless) v Windows SDK.

##  <a name="getwindow"></a>  IOleInPlaceActiveObjectImpl::GetWindow

Kontejner volá tuto funkci, aby získala popisovač okna ovládacího prvku.

```
HRESULT GetWindow(HWND* phwnd);
```

### <a name="remarks"></a>Poznámky

Některé kontejnery nebudou fungovat s ovládacím prvkem, který byl bez okna, i v případě, že je aktuálně okna. V případě implementace knihovny ATL, pokud `CComControl::m_bWasOnceWindowless` je datový člen pravdivý, vrátí funkce E_FAIL. V opačném \* případě, pokud *phwnd* není `GetWindow` null, přiřadí *phwnd* datovému členu `m_hWnd` třídy ovládacího prvku a vrátí hodnotu S_OK.

Viz [IOleWindow:: GetWindow](/windows/win32/api/oleidl/nf-oleidl-iolewindow-getwindow) v Windows SDK.

##  <a name="ondocwindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnDocWindowActivate

Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno dokumentu kontejneru.

```
HRESULT OnDocWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate) v Windows SDK.

##  <a name="onframewindowactivate"></a>  IOleInPlaceActiveObjectImpl::OnFrameWindowActivate

Upozorní ovládací prvek, když se aktivuje nebo deaktivuje okno rámce nejvyšší úrovně kontejneru.

```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject:: OnFrameWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate) v Windows SDK.

##  <a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder

Informuje ovládací prvek, který potřebuje pro změnu velikosti ohraničení.

```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder) v Windows SDK.

##  <a name="translateaccelerator"></a>  IOleInPlaceActiveObjectImpl::TranslateAccelerator

Procesy – klíčové zprávy z kontejneru v nabídce procesy

```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```

### <a name="return-value"></a>Návratová hodnota

Tato metoda podporuje následující návratové hodnoty:

S_OK, pokud byla zpráva přeložena úspěšně

S_FALSE, pokud nebyla zpráva přeložena.

### <a name="remarks"></a>Poznámky

Viz [IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator) v Windows SDK.

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
