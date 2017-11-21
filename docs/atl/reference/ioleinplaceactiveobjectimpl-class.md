---
title: "Třída IOleInPlaceActiveObjectImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b72f211d605958c345d84ae7297f5d513b7adc18
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl – třída
Tato třída poskytuje metody, které komunikaci mezi ovládacího prvku na místě a jejímu kontejneru.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IOleInPlaceActiveObjectImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|Umožňuje Kontextová nápověda. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|Umožňuje nemodální dialogová okna. Implementace ATL vrátí `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|Získá popisovač okna.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|Ovládací prvek upozorní, když je aktivace nebo deaktivace kontejneru okna dokumentu. Implementace ATL vrátí `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|Ovládací prvek upozorní, když je aktivace nebo deaktivace kontejneru nejvyšší úrovně rámce okna. Vrátí implementace knihovny ATL|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|Ovládací prvek informuje, že je potřeba změnit velikost jeho ohraničení. Implementace ATL vrátí `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|Zpracuje zprávy o klávesa akcelerátoru nabídky z kontejneru. Implementace ATL vrátí **E_NOTIMPL**.|  
  
  
## <a name="remarks"></a>Poznámky  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) rozhraní pomáhá zajistit komunikaci mezi ovládacího prvku na místě a jejímu kontejneru; například komunikaci aktivním stavu řízení a kontejneru a informuje o prvku potřebuje ke změně velikosti sám sebe. Třída `IOleInPlaceActiveObjectImpl` poskytuje výchozí implementaci třídy `IOleInPlaceActiveObject` a podporuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 Umožňuje Kontextová nápověda.  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) ve Windows SDK.  
  
##  <a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless  
 Umožňuje nemodální dialogová okna.  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115) ve Windows SDK.  
  
##  <a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow  
 Kontejner volání této funkce můžete získat popisovač okna ovládacího prvku.  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>Poznámky  
 Některé kontejnery nebude fungovat s ovládacím prvkem, který byl bez oken, i když je aktuálně oddílové. V implementaci společnosti ATL Pokud **CComControl::m_bWasOnceWindowless** – datový člen je **TRUE**, funkce vrátí hodnotu **E_FAIL**. Jinak Pokud \* *phwnd* není **NULL**, `GetWindow` přiřadí *phwnd* k – datový člen třídy ovládacího prvku `m_hWnd` a vrátí `S_OK`.  
  
 V tématu [IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) ve Windows SDK.  
  
##  <a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 Ovládací prvek upozorní, když je aktivace nebo deaktivace kontejneru okna dokumentu.  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281) ve Windows SDK.  
  
##  <a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 Ovládací prvek upozorní, když je aktivace nebo deaktivace kontejneru nejvyšší úrovně rámce okna.  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969) ve Windows SDK.  
  
##  <a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder  
 Ovládací prvek informuje, že je potřeba změnit velikost jeho ohraničení.  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053) ve Windows SDK.  
  
##  <a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 Zpracuje zprávy o klávesa akcelerátoru nabídky z kontejneru.  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda podporuje následující návratové hodnoty:  
  
 `S_OK`Pokud zpráva byla úspěšně přeložit.  
  
 **S_FALSE** Pokud zpráva nebyla přeložit.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)  
 [Rozhraní ovládací prvky ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [Přehled třídy](../../atl/atl-class-overview.md)
