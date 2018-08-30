---
title: Ioleinplaceobjectwindowlessimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aae6e79ec776320e6562df611bc0c801983054c3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207799"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>Ioleinplaceobjectwindowlessimpl – třída
Tato třída implementuje `IUnknown` a poskytuje metody, které umožňují ovládací prvek bez oken pro příjem zprávy okna a účastnit se operace přetažení myší.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IOleInPlaceObjectWindowlessImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umožňuje kontextové nápovědy. Implementace knihovny ATL vrátí E_NOTIMPL.|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Poskytuje `IDropTarget` rozhraní pro místní aktivní, bez oken objekt, který podporuje přetažení. Implementace knihovny ATL vrátí E_NOTIMPL.|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Získá popisovač okna.|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Deaktivuje aktivní ovládací prvek na místě.|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Odešle zprávu z kontejneru na ovládací prvek bez oken, která je na místě aktivní.|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Znovu aktivuje dříve deaktivované ovládacího prvku. Implementace knihovny ATL vrátí E_NOTIMPL.|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Určuje, jaká část ovládacího prvku na místě je viditelné.|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Deaktivuje a odebere uživatelské rozhraní, které podporuje aktivace na místě.|  
  
## <a name="remarks"></a>Poznámky  
 [IOleInPlaceObject](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceobject) rozhraní spravuje opětovné aktivace a deaktivace místní ovládací prvky a určuje, jak velká část ovládací prvek by měl být viditelné. [IOleInPlaceObjectWindowless](/windows/desktop/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless) rozhraní umožňuje ovládací prvek bez oken pro příjem zprávy okna a účastnit se operace přetažení myší. Třída `IOleInPlaceObjectWindowlessImpl` poskytuje výchozí implementaci třídy `IOleInPlaceObject` a `IOleInPlaceObjectWindowless` a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 Vrátí E_NOTIMPL.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleWindow::ContextSensitiveHelp](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-contextsensitivehelp) ve Windows SDK.  
  
##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 Vrátí E_NOTIMPL.  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleInPlaceObjectWindowless::GetDropTarget](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-getdroptarget) ve Windows SDK.  
  
##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow  
 Kontejner volá tuto funkci chcete-li získat popisovač okna ovládacího prvku.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Poznámky  
 S ovládacím prvkem, který je bez oken, i když je aktuálně oddílové nebudou fungovat některé kontejnery. V implementaci ATL Pokud – datový člen třídy ovládacího prvku `m_bWasOnceWindowless` má hodnotu TRUE, funkce vrátí E_FAIL. Jinak, pokud *phwnd* nemá hodnotu NULL, `GetWindow` nastaví \* *phwnd* na datový člen třídy ovládacího prvku `m_hWnd` a vrátí hodnotu S_OK.  
  
 Zobrazit [IOleWindow::GetWindow](/windows/desktop/api/oleidl/nf-oleidl-iolewindow-getwindow) ve Windows SDK.  
  
##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 Volá se kontejnerem deaktivace aktivní ovládací prvek na místě.  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda provádí celé nebo jeho část deaktivaci v závislosti na stavu ovládacího prvku. V případě potřeby deaktivovat ovládacího prvku uživatelského rozhraní a okno ovládacího prvku, pokud existuje, je zničen. Kontejner se zobrazí oznámení, že ovládací prvek již není aktivní v místě. `IOleInPlaceUIWindow` Rozhraní kontejner má být vyjednána nabídky a ohraničení, která místa se uvolní.  
  
 Zobrazit [IOleInPlaceObject::InPlaceDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-inplacedeactivate) ve Windows SDK.  
  
##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 Odešle zprávu z kontejneru na ovládací prvek bez oken, která je na místě aktivní.  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleInPlaceObjectWindowless::OnWindowMessage](/windows/desktop/api/ocidl/nf-ocidl-ioleinplaceobjectwindowless-onwindowmessage) ve Windows SDK.  
  
##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 Vrátí E_NOTIMPL.  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleInPlaceObject::ReactivateAndUndo](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-reactivateandundo) ve Windows SDK.  
  
##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 Volá se kontejnerem ovládacího prvku, který došlo ke změně jeho velikosti nebo pozice informovat.  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>Poznámky  
 Aktualizuje ovládacího prvku `m_rcPos` datový člen a zobrazení ovládacího prvku. Zobrazí se pouze část, která protíná oblast ústřižku ovládacího prvku. Pokud byla dříve oříznut zobrazení ovládacího prvku, ale výstřižek se odebral, tuto funkci lze volat pro překreslení ucelený pohled na ovládací prvek.  
  
 Zobrazit [IOleInPlaceObject::SetObjectRects](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-setobjectrects) ve Windows SDK.  
  
##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 Deaktivuje a odebere ovládacího prvku uživatelského rozhraní, která podporuje aktivace na místě.  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví – datový člen třídy ovládacího prvku `m_bUIActive` na hodnotu FALSE. Implementace knihovny ATL této funkce vždy vrátí hodnotu S_OK.  
  
 Zobrazit [IOleInPlaceObject::UIDeactivate](/windows/desktop/api/oleidl/nf-oleidl-ioleinplaceobject-uideactivate) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ccomcontrol – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
