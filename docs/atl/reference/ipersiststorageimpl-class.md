---
title: "Třída IPersistStorageImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
dev_langs: C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3a8fb59d03bed295d28a88d9659205bd173a5355
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl – třída
Tato třída implementuje [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IPersistStorageImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|Načte CLSID objektu.|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Nastaví objekt, který chcete uvolnit všechny objekty úložiště a zadejte HandsOff režimu. Implementace ATL vrátí `S_OK`.|  
|[IPersistStorageImpl::InitNew](#initnew)|Inicializuje nové úložiště.|  
|[IPersistStorageImpl::IsDirty](#isdirty)|Kontroluje, zda dat objektu se změnil od posledního uložení.|  
|[IPersistStorageImpl::Load](#load)|Načte ze zadané úložiště vlastností objektu.|  
|[IPersistStorageImpl::Save](#save)|Uloží do zadané úložiště vlastností objektu.|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Upozorní objekt, který se může vrátit do normálního režimu k zápisu do objektu jeho úložiště. Implementace ATL vrátí `S_OK`.|  
  
## <a name="remarks"></a>Poznámky  
 `IPersistStorageImpl`implementuje [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) rozhraní, která umožňuje klientům požadavek, aby objekt zatížení a uložte trvalá data pomocí úložiště.  
  
 Implementace této třídy vyžaduje třídu `T` aby implementace `IPersistStreamInit` rozhraní, které jsou k dispozici prostřednictvím `QueryInterface`. Obvykle to znamená, že třída `T` by měl být odvozen z [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), zadejte položku pro `IPersistStreamInit` v [COM mapy](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)a použít [mapa vlastností](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427) k popisu trvalých dat třídu.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytváření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getclassid"></a>IPersistStorageImpl::GetClassID  
 Načte CLSID objektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) ve Windows SDK.  
  
##  <a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage  
 Nastaví objekt, který chcete uvolnit všechny objekty úložiště a zadejte HandsOff režimu.  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/windows/desktop/ms679742) ve Windows SDK.  
  
##  <a name="initnew"></a>IPersistStorageImpl::InitNew  
 Inicializuje nové úložiště.  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace ATL deleguje [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní.  
  
 V tématu [IPersistStorage:InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194) ve Windows SDK.  
  
##  <a name="isdirty"></a>IPersistStorageImpl::IsDirty  
 Kontroluje, zda dat objektu se změnil od posledního uložení.  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace ATL deleguje [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní.  
  
 V tématu [IPersistStorage:IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) ve Windows SDK.  
  
##  <a name="load"></a>IPersistStorageImpl::Load  
 Načte ze zadané úložiště vlastností objektu.  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace ATL deleguje [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní. **Zatížení** používá datového proudu s názvem "Obsah" k načtení dat objektu. [Uložit](#save) metoda původně vytvoří tento datový proud.  
  
 V tématu [IPersistStorage:Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) ve Windows SDK.  
  
##  <a name="save"></a>IPersistStorageImpl::Save  
 Uloží do zadané úložiště vlastností objektu.  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace ATL deleguje [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní. Když **Uložit** je první volá, vytvoří datový proud na zadané úložiště s názvem "Obsah". Tento datový proud se pak použije v pozdější volání **Uložit** a v jeho voláních [zatížení](#load).  
  
 V tématu [IPersistStorage:Save](http://msdn.microsoft.com/library/windows/desktop/ms680680) ve Windows SDK.  
  
##  <a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted  
 Upozorní objekt, který se může vrátit do normálního režimu k zápisu do objektu jeho úložiště.  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK`.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IPersistStorage:SaveCompleted](http://msdn.microsoft.com/library/windows/desktop/ms679713) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Úložiště a datové proudy](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [IPersistStreamInitImpl – třída](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [IPersistPropertyBagImpl – třída](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
