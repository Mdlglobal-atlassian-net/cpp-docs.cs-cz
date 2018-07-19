---
title: Ipersiststreaminitimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
dev_langs:
- C++
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b862d6b0fc99184232621432ec1c2a1027f8a9d5
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881500"
---
# <a name="ipersiststreaminitimpl-class"></a>Ipersiststreaminitimpl – třída
Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci třídy [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IPersistStreamInitImpl 
   : public IPersistStreamInit
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IPersistStreamInitImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|  
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Získá velikost streamu potřebné k uložení dat tohoto objektu. Implementace knihovny ATL vrátí E_NOTIMPL.|  
|[IPersistStreamInitImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt.|  
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Kontroluje, zda data objektu se změnila od posledního uložení.|  
|[IPersistStreamInitImpl::Load](#load)|Načte vlastnosti objektu ze zadaného datového proudu.|  
|[IPersistStreamInitImpl::Save](#save)|Uloží vlastností objektu do zadaného datového proudu.|  
  
## <a name="remarks"></a>Poznámky  
 [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní umožňuje klientovi vyžadovat, aby váš objekt načte a uloží jeho trvalá data do jednoho datového proudu. Třída `IPersistStreamInitImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getclassid"></a>  IPersistStreamInitImpl::GetClassID  
 Načte identifikátor CLSID objektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) ve Windows SDK.  
  
##  <a name="getsizemax"></a>  IPersistStreamInitImpl::GetSizeMax  
 Získá velikost streamu potřebné k uložení dat tohoto objektu.  
  
```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí E_NOTIMPL.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersistStreamInit::GetSizeMax](http://msdn.microsoft.com/library/windows/desktop/ms687287) ve Windows SDK.  
  
##  <a name="initnew"></a>  IPersistStreamInitImpl::InitNew  
 Inicializuje nově vytvořený objekt.  
  
```
STDMETHOD(InitNew)();
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersistStreamInit::InitNew](http://msdn.microsoft.com/library/windows/desktop/ms690234) ve Windows SDK.  
  
##  <a name="isdirty"></a>  IPersistStreamInitImpl::IsDirty  
 Kontroluje, zda data objektu se změnila od posledního uložení.  
  
```
STDMETHOD(IsDirty)();
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersistStreamInit::IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms680092) ve Windows SDK.  
  
##  <a name="load"></a>  IPersistStreamInitImpl::Load  
 Načte vlastnosti objektu ze zadaného datového proudu.  
  
```
STDMETHOD(Load)(LPSTREAM pStm);
```  
  
### <a name="remarks"></a>Poznámky  
 Mapy vlastností objektu ATL používá pro načtení těchto informací.  
  
 Zobrazit [IPersistStreamInit::Load](http://msdn.microsoft.com/library/windows/desktop/ms680730) ve Windows SDK.  
  
##  <a name="save"></a>  IPersistStreamInitImpl::Save  
 Uloží vlastností objektu do zadaného datového proudu.  
  
```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```  
  
### <a name="remarks"></a>Poznámky  
 Mapy vlastností objektu ATL používá k ukládání příslušných informací.  
  
 Zobrazit [IPersistStreamInit::Save](http://msdn.microsoft.com/library/windows/desktop/ms694439) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Úložiště a datové proudy](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Přehled tříd](../../atl/atl-class-overview.md)
