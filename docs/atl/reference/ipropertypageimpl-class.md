---
title: Ipropertypageimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7692f60731c47f295630885c77e0e61e8bb5aac
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884747"
---
# <a name="ipropertypageimpl-class"></a>Ipropertypageimpl – třída
Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IPropertyPageImpl
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IPropertyPageImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPageImpl::Activate](#activate)|Vytvoří okno dialogové okno stránky vlastností.|  
|[IPropertyPageImpl::Apply](#apply)|Platí pro základní objekty zadané pomocí aktuální hodnoty vlastností stránky `SetObjects`. Implementace knihovny ATL vrátí hodnotu S_OK.|  
|[IPropertyPageImpl::Deactivate](#deactivate)|Odstraní okno vytvořené s `Activate`.|  
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Načte informace o stránce vlastností.|  
|[IPropertyPageImpl::Help](#help)|Vyvolá nápovědu Windows pro stránku vlastností.|  
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Označuje, zda stránka vlastností změnila se aktivoval.|  
|[IPropertyPageImpl::Move](#move)|Umístění a změní velikost dialogové okno stránky vlastností.|  
|[IPropertyPageImpl::SetDirty](#setdirty)|Označí stav na stránce vlastností jako změněné nebo beze změny.|  
|[IPropertyPageImpl::SetObjects](#setobjects)|Poskytuje celou řadu `IUnknown` ukazatelů pro objekty přidružené k stránky vlastností. Tyto objekty dostávat aktuální hodnoty vlastností stránky pomocí volání `Apply`.|  
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Na stránce vlastností s poskytuje `IPropertyPageSite` ukazatel, pomocí kterého se na stránce vlastností komunikuje s rámec vlastnosti.|  
|[IPropertyPageImpl::Show](#show)|Dialogové okno stránky vlastností je viditelná nebo neviditelné.|  
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Zpracuje zadané stisk klávesy.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Určuje, zda se změnil stav na stránce vlastností.|  
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Ukládá identifikátor přidružený k textový řetězec s popisem stránky vlastností.|  
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Ukládá identifikátor kontextu pro téma nápovědy přidružené k stránky vlastností.|  
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Ukládá identifikátor prostředku přidružené k názvu souboru nápovědy popisující, na stránce vlastností.|  
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Ukládá identifikátor přidružený k textový řetězec, který se zobrazí na kartě stránky vlastností.|  
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Ukládá číslo objekty přidružené k stránky vlastností.|  
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Odkazuje `IPropertyPageSite` rozhraní, pomocí kterého se na stránce vlastností komunikuje s rámec vlastnosti.|  
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Odkazuje na pole `IUnknown` ukazatelů na objekty přidružené k stránky vlastností.|  
|[IPropertyPageImpl::m_size](#m_size)|Ukládá výšku a šířku dialogového okna stránky vlastností, v pixelech.|  
  
## <a name="remarks"></a>Poznámky  
 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) rozhraní umožňuje spravovat konkrétní stránka vlastností v rámci seznamu vlastností. Třída `IPropertyPageImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="activate"></a>  IPropertyPageImpl::Activate  
 Vytvoří okno dialogové okno stránky vlastností.  
  
```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, dialogové okno je vždy nemodální, bez ohledu na hodnotu *bModal* parametru.  
  
 Zobrazit [IPropertyPage::Activate](http://msdn.microsoft.com/library/windows/desktop/ms682250) ve Windows SDK.  
  
##  <a name="apply"></a>  IPropertyPageImpl::Apply  
 Platí pro základní objekty zadané pomocí aktuální hodnoty vlastností stránky `SetObjects`.  
  
```
HRESULT Apply();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::Apply](http://msdn.microsoft.com/library/windows/desktop/ms691284) ve Windows SDK.  
  
##  <a name="deactivate"></a>  IPropertyPageImpl::Deactivate  
 Zničí dialogového okna pole vytvořené pomocí [aktivovat](#activate).  
  
```
HRESULT Deactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms682504) ve Windows SDK.  
  
##  <a name="getpageinfo"></a>  IPropertyPageImpl::GetPageInfo  
 Vyplní *pPageInfo* strukturu pomocí informací obsažených v datové členy.  
  
```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Poznámky  
 `GetPageInfo` načte řetězec prostředky spojené s [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile), a [m_dwTitle](#m_dwtitle).  
  
 Zobrazit [IPropertyPage::GetPageInfo](http://msdn.microsoft.com/library/windows/desktop/ms680714) ve Windows SDK.  
  
##  <a name="help"></a>  IPropertyPageImpl::Help  
 Vyvolá nápovědu Windows pro stránku vlastností.  
  
```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::Help](http://msdn.microsoft.com/library/windows/desktop/ms691504) ve Windows SDK.  
  
##  <a name="ipropertypageimpl"></a>  IPropertyPageImpl::IPropertyPageImpl  
 Konstruktor  
  
```
IPropertyPageImpl();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje všechny datové členy.  
  
##  <a name="ispagedirty"></a>  IPropertyPageImpl::IsPageDirty  
 Označuje, zda stránka vlastností změnila se aktivoval.  
  
```
HRESULT IsPageDirty(void);
```  
  
### <a name="remarks"></a>Poznámky  
 `IsPageDirty` Vrátí hodnotu S_OK, pokud stránce změnila se aktivoval.  
  
##  <a name="m_bdirty"></a>  IPropertyPageImpl::m_bDirty  
 Určuje, zda se změnil stav na stránce vlastností.  
  
```
BOOL m_bDirty;
```  
  
##  <a name="m_nobjects"></a>  IPropertyPageImpl::m_nObjects  
 Ukládá číslo objekty přidružené k stránky vlastností.  
  
```
ULONG m_nObjects;
```  
  
##  <a name="m_dwhelpcontext"></a>  IPropertyPageImpl::m_dwHelpContext  
 Ukládá identifikátor kontextu pro téma nápovědy přidružené k stránky vlastností.  
  
```
DWORD m_dwHelpContext;
```  
  
##  <a name="m_dwdocstring"></a>  IPropertyPageImpl::m_dwDocString  
 Ukládá identifikátor přidružený k textový řetězec s popisem stránky vlastností.  
  
```
UINT m_dwDocString;
```  
  
##  <a name="m_dwhelpfile"></a>  IPropertyPageImpl::m_dwHelpFile  
 Ukládá identifikátor prostředku přidružené k názvu souboru nápovědy popisující, na stránce vlastností.  
  
```
UINT m_dwHelpFile;
```  
  
##  <a name="m_dwtitle"></a>  IPropertyPageImpl::m_dwTitle  
 Ukládá identifikátor přidružený k textový řetězec, který se zobrazí na kartě stránky vlastností.  
  
```
UINT m_dwTitle;
```  
  
##  <a name="m_ppagesite"></a>  IPropertyPageImpl::m_pPageSite  
 Odkazuje [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) rozhraní, pomocí kterého se na stránce vlastností komunikuje s rámec vlastnosti.  
  
```
IPropertyPageSite* m_pPageSite;
```  
  
##  <a name="m_ppunk"></a>  IPropertyPageImpl::m_ppUnk  
 Odkazuje na pole `IUnknown` ukazatelů na objekty přidružené k stránky vlastností.  
  
```
IUnknown** m_ppUnk;
```  
  
##  <a name="m_size"></a>  IPropertyPageImpl::m_size  
 Ukládá výšku a šířku dialogového okna stránky vlastností, v pixelech.  
  
```
SIZE m_size;
```  
  
##  <a name="move"></a>  IPropertyPageImpl::Move  
 Umístění a změní velikost dialogové okno stránky vlastností.  
  
```
HRESULT Move(LPCRECT pRect);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::Move](http://msdn.microsoft.com/library/windows/desktop/ms680118) ve Windows SDK.  
  
##  <a name="setdirty"></a>  IPropertyPageImpl::SetDirty  
 Označí stav na stránce vlastností jako změněné nebo beze změny, závisí na hodnotě *bDirty*.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Parametry  
 *bDirty*  
 [in] Při hodnotě TRUE se stav na stránce vlastností je označen jako změnit. V opačném případě je označen jako beze změny.  
  
### <a name="remarks"></a>Poznámky  
 V případě potřeby `SetDirty` informuje rámce, který se změnil na stránce vlastností.  
  
##  <a name="setobjects"></a>  IPropertyPageImpl::SetObjects  
 Poskytuje celou řadu `IUnknown` ukazatelů pro objekty přidružené k stránky vlastností.  
  
```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::SetObjects](http://msdn.microsoft.com/library/windows/desktop/ms678529) ve Windows SDK.  
  
##  <a name="setpagesite"></a>  IPropertyPageImpl::SetPageSite  
 Na stránce vlastností s poskytuje [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) ukazatel, pomocí kterého se na stránce vlastností komunikuje s rámec vlastnosti.  
  
```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::SetPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690413) ve Windows SDK.  
  
##  <a name="show"></a>  IPropertyPageImpl::Show  
 Dialogové okno stránky vlastností je viditelná nebo neviditelné.  
  
```
HRESULT Show(UINT nCmdShow);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::Show](http://msdn.microsoft.com/library/windows/desktop/ms694467) ve Windows SDK.  
  
##  <a name="translateaccelerator"></a>  IPropertyPageImpl::TranslateAccelerator  
 Zpracuje stisk klávesy podle `pMsg`.  
  
```
HRESULT TranslateAccelerator(MSG* pMsg);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms686603) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Ipropertypage2impl – třída](../../atl/reference/ipropertypage2impl-class.md)   
 [Iperpropertybrowsingimpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
