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
ms.openlocfilehash: c48670ca6e7dd38e94a2c57f0a0c0415f654f445
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881487"
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
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) rozhraní spravuje opětovné aktivace a deaktivace místní ovládací prvky a určuje, jak velká část ovládací prvek by měl být viditelné. [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) rozhraní umožňuje ovládací prvek bez oken pro příjem zprávy okna a účastnit se operace přetažení myší. Třída `IOleInPlaceObjectWindowlessImpl` poskytuje výchozí implementaci třídy `IOleInPlaceObject` a `IOleInPlaceObjectWindowless` a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
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
 Zobrazit [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) ve Windows SDK.  
  
##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 Vrátí E_NOTIMPL.  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535) ve Windows SDK.  
  
##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow  
 Kontejner volá tuto funkci chcete-li získat popisovač okna ovládacího prvku.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Poznámky  
 S ovládacím prvkem, který je bez oken, i když je aktuálně oddílové nebudou fungovat některé kontejnery. V implementaci ATL Pokud – datový člen třídy ovládacího prvku `m_bWasOnceWindowless` má hodnotu TRUE, funkce vrátí E_FAIL. Jinak, pokud *phwnd* nemá hodnotu NULL, `GetWindow` nastaví \* *phwnd* na datový člen třídy ovládacího prvku `m_hWnd` a vrátí hodnotu S_OK.  
  
 Zobrazit [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) ve Windows SDK.  
  
##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 Volá se kontejnerem deaktivace aktivní ovládací prvek na místě.  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda provádí celé nebo jeho část deaktivaci v závislosti na stavu ovládacího prvku. V případě potřeby deaktivovat ovládacího prvku uživatelského rozhraní a okno ovládacího prvku, pokud existuje, je zničen. Kontejner se zobrazí oznámení, že ovládací prvek již není aktivní v místě. `IOleInPlaceUIWindow` Rozhraní kontejner má být vyjednána nabídky a ohraničení, která místa se uvolní.  
  
 Zobrazit [IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) ve Windows SDK.  
  
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
 Zobrazit [IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783) ve Windows SDK.  
  
##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 Vrátí E_NOTIMPL.  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) ve Windows SDK.  
  
##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 Volá se kontejnerem ovládacího prvku, který došlo ke změně jeho velikosti nebo pozice informovat.  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>Poznámky  
 Aktualizuje ovládacího prvku `m_rcPos` datový člen a zobrazení ovládacího prvku. Zobrazí se pouze část, která protíná oblast ústřižku ovládacího prvku. Pokud byla dříve oříznut zobrazení ovládacího prvku, ale výstřižek se odebral, tuto funkci lze volat pro překreslení ucelený pohled na ovládací prvek.  
  
 Zobrazit [IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) ve Windows SDK.  
  
##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 Deaktivuje a odebere ovládacího prvku uživatelského rozhraní, která podporuje aktivace na místě.  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví – datový člen třídy ovládacího prvku `m_bUIActive` na hodnotu FALSE. Implementace knihovny ATL této funkce vždy vrátí hodnotu S_OK.  
  
 Zobrazit [IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ccomcontrol – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
