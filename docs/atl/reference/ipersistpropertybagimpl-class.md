---
title: "Třída IPersistPropertyBagImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3783d505c989b11205104cd70a9c440aa6f645f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl – třída
Tato třída implementuje **IUnknown** a umožňuje objekt uložení jeho vlastnosti do kontejneru objektů zadané klienta.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPersistPropertyBagImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Načte CLSID objektu.|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt. Implementace ATL vrátí `S_OK`.|  
|[IPersistPropertyBagImpl::Load](#load)|Načte vlastností objektu z kontejneru objektů zadané klienta.|  
|[IPersistPropertyBagImpl::Save](#save)|Uloží vlastností objektu do kontejneru objektů zadané klienta.|  
  
## <a name="remarks"></a>Poznámky  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx) rozhraní, které umožňuje objekt uložení jeho vlastnosti do kontejneru objektů zadané klienta. Třída `IPersistPropertyBagImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
 **IPersistPropertyBag** funguje ve spojení s [IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx) a [IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx). Tyto pozdější dvě rozhraní musí být implementované klientem. Prostřednictvím `IPropertyBag`, klient uloží a načte jednotlivé vlastnosti objektu. Prostřednictvím **IErrorLog**, objekt a klient mohou zasílat zprávy o chybách došlo.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getclassid"></a>IPersistPropertyBagImpl::GetClassID  
 Načte CLSID objektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) ve Windows SDK.  
  
##  <a name="initnew"></a>IPersistPropertyBagImpl::InitNew  
 Inicializuje nově vytvořený objekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) ve Windows SDK.  
  
##  <a name="load"></a>IPersistPropertyBagImpl::Load  
 Načte vlastností objektu z kontejneru objektů zadané klienta.  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>Poznámky  
 ATL používá mapa vlastností objektu k načtení těchto informací.  
  
 V tématu [IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx) ve Windows SDK.  
  
##  <a name="save"></a>IPersistPropertyBagImpl::Save  
 Uloží vlastností objektu do kontejneru objektů zadané klienta.  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>Poznámky  
 ATL používá k ukládání těchto informací mapa vlastností objektu. Ve výchozím nastavení, tato metoda šetří všechny vlastnosti, bez ohledu na hodnotu *fSaveAllProperties*.  
  
 V tématu [IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [Přehled třídy](../../atl/atl-class-overview.md)
