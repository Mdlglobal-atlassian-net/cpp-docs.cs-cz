---
title: "Třída IPerPropertyBrowsingImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetDisplayString
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedStrings
- ATLCTL/ATL::IPerPropertyBrowsingImpl::GetPredefinedValue
- ATLCTL/ATL::IPerPropertyBrowsingImpl::MapPropertyToPage
dev_langs: C++
helpviewer_keywords:
- IPerPropertyBrowsingImpl class
- property pages, accessing information
- IPerPropertyBrowsing, ATL implementation
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4e8755d4f9728476967196837b112a66613d6912
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iperpropertybrowsingimpl-class"></a>IPerPropertyBrowsingImpl – třída
Tato třída implementuje **IUnknown** a umožňuje klientům přístup k informacím na stránkách vlastností objektu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```

template <class T>
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :
    public IPerPropertyBrowsing
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPerPropertyBrowsingImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](#getdisplaystring)|Načte řetězec popisující dané vlastnosti.|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](#getpredefinedstrings)|Načte pole řetězců odpovídající hodnoty, které může přijmout dané vlastnosti.|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](#getpredefinedvalue)|Načte **VARIANT** obsahující hodnotu vlastnosti identifikovaný dané DISPID. DISPID je spojena s název řetězce načítají `GetPredefinedStrings`. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](#mappropertytopage)|Načte CLSID ze stránky vlastností, které jsou přidružené k dané vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432) rozhraní umožňuje klientům přístup k informacím na stránkách vlastností objektu. Třída `IPerPropertyBrowsingImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
> [!NOTE]
>  Pokud používáte Microsoft Access jako kontejner aplikace, musí být odvozeny třídě z `IPerPropertyBrowsingImpl`. Přístup, jinak hodnota nenačte vlastního ovládacího prvku.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="getdisplaystring"></a>IPerPropertyBrowsingImpl::GetDisplayString  
 Načte řetězec popisující dané vlastnosti.  
  
```
STDMETHOD(GetDisplayString)(
    DISPID dispID,
    BSTR* pBstr);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPerPropertyBrowsing::GetDisplayString](http://msdn.microsoft.com/library/windows/desktop/ms688734) ve Windows SDK.  
  
##  <a name="getpredefinedstrings"></a>IPerPropertyBrowsingImpl::GetPredefinedStrings  
 Doplní každé pole s nulové položky.  
  
```
STDMETHOD(GetPredefinedStrings)(
    DISPID dispID,
    CALPOLESTR* pCaStringsOut,
    CADWORD* pCaCookiesOut);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Implementace je ATL [GetPredefinedValue](#getpredefinedvalue) vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPerPropertyBrowsing::GetPredefinedStrings](http://msdn.microsoft.com/library/windows/desktop/ms679724) ve Windows SDK.  
  
##  <a name="getpredefinedvalue"></a>IPerPropertyBrowsingImpl::GetPredefinedValue  
 Načte **VARIANT** obsahující hodnotu vlastnosti identifikovaný dané DISPID. DISPID je spojena s název řetězce načítají `GetPredefinedStrings`.  
  
```
STDMETHOD(GetPredefinedValue)(
    DISPID dispID,
    DWORD dwCookie,
    VARIANT* pVarOut);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 Implementace je ATL [GetPredefinedStrings](#getpredefinedstrings) načte žádné odpovídající řetězce.  
  
 V tématu [IPerPropertyBrowsing::GetPredefinedValue](http://msdn.microsoft.com/library/windows/desktop/ms690401) ve Windows SDK.  
  
##  <a name="mappropertytopage"></a>IPerPropertyBrowsingImpl::MapPropertyToPage  
 Načte identifikátor CLSID její stránku vlastností, které jsou přidružené k zadané vlastnosti.  
  
```
STDMETHOD(MapPropertyToPage)(
    DISPID dispID,
    CLSID* pClsid);
```  
  
### <a name="remarks"></a>Poznámky  
 ATL používá mapa vlastností objektu k získání těchto informací.  
  
 V tématu [IPerPropertyBrowsing::MapPropertyToPage](http://msdn.microsoft.com/library/windows/desktop/ms694476) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IPropertyPageImpl – třída](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
