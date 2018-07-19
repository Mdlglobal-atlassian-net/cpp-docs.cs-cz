---
title: Ipropertypage2impl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl
- ATLCTL/ATL::IPropertyPage2Impl::EditProperty
dev_langs:
- C++
helpviewer_keywords:
- property pages
- IPropertyPage2 ATL implementation
- IPropertyPage2Impl class
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf5cf9438d2fcecb434802dc99aaa5c692ba108f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882894"
---
# <a name="ipropertypage2impl-class"></a>Ipropertypage2impl – třída
Tato třída implementuje `IUnknown` a zdědí výchozí implementace [ipropertypageimpl –](../../atl/reference/ipropertypageimpl-class.md).  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class IPropertyPage2Impl : public IPropertyPageImpl<T>
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IPropertyPage2Impl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](#editproperty)|Určuje, který vlastnost ovládací prvek získá fokus, když je aktivován na stránce vlastností. Implementace knihovny ATL vrátí E_NOTIMPL.|  
  
## <a name="remarks"></a>Poznámky  
 [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) rozhraní rozšiřuje [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) tak, že přidáte `EditProperty` metody. Tato metoda umožňuje vybrat konkrétní vlastnost v objektu vlastností stránky klientovi.  
  
 Třída `IPropertyPage2Impl` jednoduše vrací E_NOTIMPL pro `IPropertyPage2::EditProperty`. Ale dědí výchozí implementace [ipropertypageimpl –](../../atl/reference/ipropertypageimpl-class.md) a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 Při vytváření stránky vlastností vaší třídy je obvykle odvozen z `IPropertyPageImpl`. Kvůli další podpoře `IPropertyPage2`, úpravě vaší definice třídy a přepsat `EditProperty` metody.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPropertyPage`  
  
 [Ipropertypageimpl –](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
##  <a name="editproperty"></a>  IPropertyPage2Impl::EditProperty  
 Určuje, který vlastnost ovládací prvek získá fokus, když je aktivován na stránce vlastností.  
  
```
HRESULT EditProperty(DISPID dispID);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_NOTIMPL.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPropertyPage2::EditProperty](http://msdn.microsoft.com/library/windows/desktop/ms690353) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Iperpropertybrowsingimpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
