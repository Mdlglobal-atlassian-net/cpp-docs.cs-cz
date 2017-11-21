---
title: "Třída IPropertyPage2Impl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs: C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40cdaeef31226cf47dcf4beb08f11242932578c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ipropertypage2impl-class"></a>IPropertyPage2Impl – třída
Tato třída implementuje **IUnknown** a dědí výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPropertyPage2Impl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](#editproperty)|Určuje, který vlastnost ovládací prvek bude získat fokus, když je aktivován stránku vlastností. Implementace ATL vrátí **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Poznámky  
 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) rozšiřuje rozhraní [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) přidáním `EditProperty` metoda. Tato metoda umožňuje klientovi, vyberte konkrétní vlastnost v objektu stránku vlastností.  
  
 Třída `IPropertyPage2Impl` jednoduše vrátí **E_NOTIMPL** pro **IPropertyPage2::EditProperty**. Ale zdědil výchozí implementaci [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 Při vytváření stránky vlastností vlastní třídy je obvykle odvozený od `IPropertyPageImpl`. Poskytovat další podporu systému **IPropertyPage2**, upravte definici vaší třídy a přepsat `EditProperty` metoda.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="editproperty"></a>IPropertyPage2Impl::EditProperty  
 Určuje, který vlastnost ovládací prvek bude získat fokus, když je aktivován stránku vlastností.  
  
```
HRESULT EditProperty(DISPID dispID);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **E_NOTIMPL**.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPropertyPage2::EditProperty](http://msdn.microsoft.com/library/windows/desktop/ms690353) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
