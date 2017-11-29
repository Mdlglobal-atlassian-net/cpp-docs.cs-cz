---
title: "Třída IPropertyPageImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 345379de254338fa8d344ee21b022439380d9851
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl – třída
Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IPropertyPageImpl
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPropertyPageImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPageImpl::Activate](#activate)|Vytvoří dialogové okno pole pro stránku vlastností.|  
|[IPropertyPageImpl::Apply](#apply)|Aktuální hodnoty vlastností stránky se vztahuje na základní objekty uvedené prostřednictvím `SetObjects`. Implementace ATL vrátí `S_OK`.|  
|[IPropertyPageImpl::Deactivate](#deactivate)|Zničí okna vytvořeného s **aktivovat**.|  
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Načte informace o jeho stránku vlastností.|  
|[IPropertyPageImpl::Help](#help)|Vyvolá nápovědy pro Windows pro stránku vlastností.|  
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Určuje, zda byl změněn na stránku vlastností, vzhledem k tomu, že byl aktivován.|  
|[IPropertyPageImpl::Move](#move)|Umisťuje a změní velikost dialogového okna Vlastnosti stránku.|  
|[IPropertyPageImpl::SetDirty](#setdirty)|Flags – stránka vlastností stavu jako změněné nebo unchanged.|  
|[IPropertyPageImpl::SetObjects](#setobjects)|Poskytuje pole **IUnknown** ukazatele pro objekty přidružené k jeho stránku vlastností. Tyto objekty se zobrazit aktuální hodnoty vlastností stránky pomocí volání **použít**.|  
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Poskytuje stránku vlastností s `IPropertyPageSite` ukazatele, pomocí kterého se stránka vlastností komunikuje s vlastnost rámečku.|  
|[IPropertyPageImpl::Show](#show)|Dialogové okno stránky vlastností je viditelný nebo neviditelná.|  
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Zpracuje zadané klávesu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Určuje, zda došlo ke změně stavu na stránce vlastností.|  
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Ukládá identifikátor prostředku, který je přidružený textový řetězec popisující stránku vlastností.|  
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Ukládá identifikátor kontext pro téma nápovědy, které jsou přidružené k jeho stránku vlastností.|  
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Ukládá identifikátor prostředku přidružené k názvu souboru nápovědy popisující stránku vlastností.|  
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Ukládá identifikátor prostředku, který je přidružený textový řetězec, který se zobrazí na kartě stránky vlastností.|  
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Ukládá číslo objekty přidružené k jeho stránku vlastností.|  
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Odkazuje na `IPropertyPageSite` rozhraní, pomocí kterého se stránka vlastností komunikuje s vlastnost rámečku.|  
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Odkazuje na pole **IUnknown** ukazatelé na objekty přidružené k jeho stránku vlastností.|  
|[IPropertyPageImpl::m_size](#m_size)|Výška a šířka dialogové okno vlastností stránky, ukládá v pixelech.|  
  
## <a name="remarks"></a>Poznámky  
 [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) rozhraní, které umožňuje spravovat konkrétní stránka vlastností v rámci vlastností objektu. Třída `IPropertyPageImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="activate"></a>IPropertyPageImpl::Activate  
 Vytvoří dialogové okno pole pro stránku vlastností.  
  
```
HRESULT Activate(  
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, dialogové okno je vždy nemodální, bez ohledu na hodnotu *bModal* parametr.  
  
 V tématu [IPropertyPage::Activate](http://msdn.microsoft.com/library/windows/desktop/ms682250) ve Windows SDK.  
  
##  <a name="apply"></a>IPropertyPageImpl::Apply  
 Aktuální hodnoty vlastností stránky se vztahuje na základní objekty uvedené prostřednictvím `SetObjects`.  
  
```
HRESULT Apply();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::Apply](http://msdn.microsoft.com/library/windows/desktop/ms691284) ve Windows SDK.  
  
##  <a name="deactivate"></a>IPropertyPageImpl::Deactivate  
 Zničí dialogového okna pole vytvořené pomocí [aktivovat](#activate).  
  
```
HRESULT Deactivate();
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms682504) ve Windows SDK.  
  
##  <a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo  
 Vyplní celé *pPageInfo* struktura s informace obsažené v datových členů.  
  
```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Poznámky  
 `GetPageInfo`načte řetězcové prostředky přidružené k [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile), a [m_dwTitle](#m_dwtitle).  
  
 V tématu [IPropertyPage::GetPageInfo](http://msdn.microsoft.com/library/windows/desktop/ms680714) ve Windows SDK.  
  
##  <a name="help"></a>IPropertyPageImpl::Help  
 Vyvolá nápovědy pro Windows pro stránku vlastností.  
  
```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::Help](http://msdn.microsoft.com/library/windows/desktop/ms691504) ve Windows SDK.  
  
##  <a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl  
 Konstruktor  
  
```
IPropertyPageImpl();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje všechny datové členy.  
  
##  <a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty  
 Určuje, zda byl změněn na stránku vlastností, vzhledem k tomu, že byl aktivován.  
  
```
HRESULT IsPageDirty(void);
```  
  
### <a name="remarks"></a>Poznámky  
 `IsPageDirty`Vrátí `S_OK` Pokud došlo ke změně stránky vzhledem k tomu, že byl aktivován.  
  
##  <a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty  
 Určuje, zda došlo ke změně stavu na stránce vlastností.  
  
```
BOOL m_bDirty;
```  
  
##  <a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects  
 Ukládá číslo objekty přidružené k jeho stránku vlastností.  
  
```
ULONG m_nObjects;
```  
  
##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext  
 Ukládá identifikátor kontext pro téma nápovědy, které jsou přidružené k jeho stránku vlastností.  
  
```
DWORD m_dwHelpContext;
```  
  
##  <a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString  
 Ukládá identifikátor prostředku, který je přidružený textový řetězec popisující stránku vlastností.  
  
```
UINT m_dwDocString;
```  
  
##  <a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile  
 Ukládá identifikátor prostředku přidružené k názvu souboru nápovědy popisující stránku vlastností.  
  
```
UINT m_dwHelpFile;
```  
  
##  <a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle  
 Ukládá identifikátor prostředku, který je přidružený textový řetězec, který se zobrazí na kartě stránky vlastností.  
  
```
UINT m_dwTitle;
```  
  
##  <a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite  
 Odkazuje na [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) rozhraní, pomocí kterého se stránka vlastností komunikuje s vlastnost rámečku.  
  
```
IPropertyPageSite* m_pPageSite;
```  
  
##  <a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk  
 Odkazuje na pole **IUnknown** ukazatelé na objekty přidružené k jeho stránku vlastností.  
  
```
IUnknown** m_ppUnk;
```  
  
##  <a name="m_size"></a>IPropertyPageImpl::m_size  
 Výška a šířka dialogové okno vlastností stránky, ukládá v pixelech.  
  
```
SIZE m_size;
```  
  
##  <a name="move"></a>IPropertyPageImpl::Move  
 Umisťuje a změní velikost dialogového okna Vlastnosti stránku.  
  
```
HRESULT Move(LPCRECT pRect);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::Move](http://msdn.microsoft.com/library/windows/desktop/ms680118) ve Windows SDK.  
  
##  <a name="setdirty"></a>IPropertyPageImpl::SetDirty  
 Flags – stránka vlastností stavu jako změněné nebo beze změny, v závislosti na hodnotě `bDirty`.  
  
```
void SetDirty(BOOL bDirty);
```  
  
### <a name="parameters"></a>Parametry  
 `bDirty`  
 [v] Pokud **TRUE**, stránka vlastností stavu je označena jako změnit. Jinak je označen jako beze změny.  
  
### <a name="remarks"></a>Poznámky  
 V případě potřeby `SetDirty` informuje rámce, který se změnil její stránku vlastností.  
  
##  <a name="setobjects"></a>IPropertyPageImpl::SetObjects  
 Poskytuje pole **IUnknown** ukazatele pro objekty přidružené k jeho stránku vlastností.  
  
```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::SetObjects](http://msdn.microsoft.com/library/windows/desktop/ms678529) ve Windows SDK.  
  
##  <a name="setpagesite"></a>IPropertyPageImpl::SetPageSite  
 Poskytuje stránku vlastností s [IPropertyPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690583) ukazatele, pomocí kterého se stránka vlastností komunikuje s vlastnost rámečku.  
  
```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::SetPageSite](http://msdn.microsoft.com/library/windows/desktop/ms690413) ve Windows SDK.  
  
##  <a name="show"></a>IPropertyPageImpl::Show  
 Dialogové okno stránky vlastností je viditelný nebo neviditelná.  
  
```
HRESULT Show(UINT nCmdShow);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::Show](http://msdn.microsoft.com/library/windows/desktop/ms694467) ve Windows SDK.  
  
##  <a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator  
 Zpracuje klávesu zadaný v `pMsg`.  
  
```
HRESULT TranslateAccelerator(MSG* pMsg);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms686603) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IPropertyPage2Impl – třída](../../atl/reference/ipropertypage2impl-class.md)   
 [IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)