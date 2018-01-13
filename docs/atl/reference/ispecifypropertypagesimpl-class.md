---
title: "Třída ISpecifyPropertyPagesImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl
- ATLCOM/ATL::ISpecifyPropertyPagesImpl::GetPages
dev_langs: C++
helpviewer_keywords:
- property pages, CLSIDs associated with
- ISpecifyPropertyPages
- ISpecifyPropertyPagesImpl class
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 716e3ba5d48d39cd189da8d92cca694f09508e42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ispecifypropertypagesimpl-class"></a>ISpecifyPropertyPagesImpl – třída
Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci třídy [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl 
   : public ISpecifyPropertyPages
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `ISpecifyPropertyPagesImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](#getpages)|Vyplní hodnoty počítají pole UUID. Každý UUID odpovídá CLSID pro jednu ze stránky vlastností, které lze zobrazit v seznamu vlastností objektu.|  
  
## <a name="remarks"></a>Poznámky  
 [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) rozhraní umožňuje klientům získat seznam CLSID pro stránky vlastností objektem podporována. Třída `ISpecifyPropertyPagesImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
> [!NOTE]
>  Nevystavujte **ISpecifyPropertyPages** rozhraní Pokud objektu nepodporuje stránky vlastností.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getpages"></a>ISpecifyPropertyPagesImpl::GetPages  
 Vyplní pole [CAUUID](http://msdn.microsoft.com/library/windows/desktop/ms680048) struktura s CLSID pro stránky vlastností, které lze zobrazit v seznamu vlastností objektu.  
  
```
STDMETHOD(GetPages)(CAUUID* pPages);
```  
  
### <a name="remarks"></a>Poznámky  
 ATL používá k načtení jednotlivých CLSID mapa vlastností objektu.  
  
 V tématu [ISpecifyPropertyPages::GetPages](http://msdn.microsoft.com/library/windows/desktop/ms687276) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IPropertyPageImpl – třída](../../atl/reference/ipropertypageimpl-class.md)   
 [IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
