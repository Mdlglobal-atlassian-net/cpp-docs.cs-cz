---
title: Třída IOleInPlaceObjectWindowlessImpl | Microsoft Docs
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
ms.openlocfilehash: f5616258405eb8346132d32b8f7fd71d0b4794d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32364999"
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl – třída
Tato třída implementuje **IUnknown** a poskytuje metody, které umožní ovládacího prvku bez oken pro příjem zpráv oken a zapojit se do operací přetažení myší.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IOleInPlaceObjectWindowlessImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umožňuje Kontextová nápověda. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|Zdroje `IDropTarget` rozhraní pro místní active, bez oken objekt, který podporuje přetažení. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|Získá popisovač okna.|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|Deaktivuje ovládacího prvku active na místě.|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|Odešle zprávu do ovládacího prvku bez oken, který je na místě aktivní zprávu z kontejneru.|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|Znovu aktivuje dříve deaktivované ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|Určuje, jaká část ovládacího prvku na místě je viditelná.|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|Deaktivuje a odebere uživatelské rozhraní, která podporuje aktivace na místě.|  
  
## <a name="remarks"></a>Poznámky  
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) rozhraní spravuje opětovné aktivace a deaktivace místní ovládací prvky a určuje, kolik ovládacího prvku by měly jít vidět. [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) rozhraní umožňuje ovládacího prvku bez oken pro příjem zpráv oken a zapojit se do operací přetažení myší. Třída `IOleInPlaceObjectWindowlessImpl` poskytuje výchozí implementaci třídy `IOleInPlaceObject` a `IOleInPlaceObjectWindowless` a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>  IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 Vrátí **E_NOTIMPL**.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) ve Windows SDK.  
  
##  <a name="getdroptarget"></a>  IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 Vrátí **E_NOTIMPL**.  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535) ve Windows SDK.  
  
##  <a name="getwindow"></a>  IOleInPlaceObjectWindowlessImpl::GetWindow  
 Kontejner volání této funkce můžete získat popisovač okna ovládacího prvku.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Poznámky  
 Některé kontejnery nebude fungovat s ovládacím prvkem, který byl bez oken, i když je aktuálně oddílové. V implementaci společnosti ATL Pokud – datový člen třídy ovládacího prvku `m_bWasOnceWindowless` je **TRUE**, funkce vrátí hodnotu **E_FAIL**. Jinak Pokud *phwnd* není **NULL**, `GetWindow` nastaví \* *phwnd* k – datový člen třídy ovládacího prvku `m_hWnd` a vrátí `S_OK`.  
  
 V tématu [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) ve Windows SDK.  
  
##  <a name="inplacedeactivate"></a>  IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 Voláno rozhraním kontejneru deaktivace active ovládacího prvku na místě.  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda provede úplné nebo částečné deaktivace v závislosti na stavu ovládacího prvku. V případě potřeby je deaktivována uživatelské rozhraní ovládacího prvku a ovládacího prvku okno, pokud existuje, zničena. Kontejner je upozornění, že ovládací prvek již active na místě. **IOleInPlaceUIWindow** vydání rozhraní používá kontejneru k vyjednávání nabídek a ohraničení místa.  
  
 V tématu [IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) ve Windows SDK.  
  
##  <a name="onwindowmessage"></a>  IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 Odešle zprávu do ovládacího prvku bez oken, který je na místě aktivní zprávu z kontejneru.  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783) ve Windows SDK.  
  
##  <a name="reactivateandundo"></a>  IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 Vrátí **E_NOTIMPL**.  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) ve Windows SDK.  
  
##  <a name="setobjectrects"></a>  IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 Voláno rozhraním kontejneru k informování ovládací prvek, který došlo ke změně jeho velikost nebo pozice.  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>Poznámky  
 Aktualizace ovládacího prvku `m_rcPos` – datový člen a zobrazení ovládacího prvku. Zobrazí se pouze část ovládací prvek, který protíná klip oblast. Pokud byl dříve oříznut zobrazení ovládacího prvku, ale byla odebrána výstřižek, tuto funkci lze volat pro ho překreslit úplný přehled ovládacího prvku.  
  
 V tématu [IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) ve Windows SDK.  
  
##  <a name="uideactivate"></a>  IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 Deaktivuje a odebere uživatelské rozhraní ovládacího prvku, který podporuje aktivace na místě.  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Nastaví – datový člen třídy ovládacího prvku `m_bUIActive` k **FALSE**. ATL provedení této funkce vždy vrátí `S_OK`.  
  
 V tématu [IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
