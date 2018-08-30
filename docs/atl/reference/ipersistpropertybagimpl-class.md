---
title: Ipersistpropertybagimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09b0acfc1fc1f9147a6acbe8bbfe66016dc0b54b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201699"
---
# <a name="ipersistpropertybagimpl-class"></a>Ipersistpropertybagimpl – třída
Tato třída implementuje `IUnknown` a umožňuje uložit do kontejneru objektů klientem poskytnutý její vlastnosti.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IPersistPropertyBagImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|  
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt. Implementace knihovny ATL vrátí hodnotu S_OK.|  
|[IPersistPropertyBagImpl::Load](#load)|Načte vlastnosti objektu z kontejneru objektů dodaná klientem.|  
|[IPersistPropertyBagImpl::Save](#save)|Uloží vlastností objektu do kontejneru objektů dodaná klientem.|  
  
## <a name="remarks"></a>Poznámky  
 [IPersistPropertyBag](https://msdn.microsoft.com/library/aa768205.aspx) rozhraní umožňuje uložit do kontejneru objektů klientem poskytnutý její vlastnosti. Třída `IPersistPropertyBagImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 `IPersistPropertyBag` funguje ve spojení s [IPropertyBag](https://msdn.microsoft.com/library/aa768196.aspx) a [IErrorLog](https://msdn.microsoft.com/library/aa768231.aspx). Tato druhá možnost dvě rozhraní musí být implementované klientem. Prostřednictvím `IPropertyBag`, klient ukládá a načítá jednotlivých vlastností objektu. Prostřednictvím `IErrorLog`, objektu a klienta můžete podávat zprávy o chybách byla zjištěna.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID  
 Načte identifikátor CLSID objektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) ve Windows SDK.  
  
##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew  
 Inicializuje nově vytvořený objekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersistPropertyBag::InitNew](https://msdn.microsoft.com/library/aa768204.aspx) ve Windows SDK.  
  
##  <a name="load"></a>  IPersistPropertyBagImpl::Load  
 Načte vlastnosti objektu z kontejneru objektů dodaná klientem.  
  
```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```  
  
### <a name="remarks"></a>Poznámky  
 Mapy vlastností objektu ATL používá pro načtení těchto informací.  
  
 Zobrazit [IPersistPropertyBag::Load](https://msdn.microsoft.com/library/aa768206.aspx) ve Windows SDK.  
  
##  <a name="save"></a>  IPersistPropertyBagImpl::Save  
 Uloží vlastností objektu do kontejneru objektů dodaná klientem.  
  
```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```  
  
### <a name="remarks"></a>Poznámky  
 Mapy vlastností objektu ATL používá k ukládání příslušných informací. Ve výchozím nastavení, tato metoda šetří všechny vlastnosti, bez ohledu na hodnotu *fSaveAllProperties*.  
  
 Zobrazit [IPersistPropertyBag::Save](https://msdn.microsoft.com/library/aa768207.aspx) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)   
 [Přehled tříd](../../atl/atl-class-overview.md)
