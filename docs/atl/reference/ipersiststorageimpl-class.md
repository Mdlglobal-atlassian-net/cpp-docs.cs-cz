---
title: Ipersiststorageimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 634a7a7373f6686ad36b645a73613a4ae350bbab
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884698"
---
# <a name="ipersiststorageimpl-class"></a>Ipersiststorageimpl – třída
Tato třída implementuje [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `IPersistStorageImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|  
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Nastaví objekt, který chcete uvolnit všechny objekty úložiště a HandsOff režimu. Implementace knihovny ATL vrátí hodnotu S_OK.|  
|[IPersistStorageImpl::InitNew](#initnew)|Inicializuje nové úložiště.|  
|[IPersistStorageImpl::IsDirty](#isdirty)|Kontroluje, zda data objektu se změnila od posledního uložení.|  
|[IPersistStorageImpl::Load](#load)|Načte vlastnosti objektu ze zadané úložiště.|  
|[IPersistStorageImpl::Save](#save)|Uloží do zadané úložiště vlastností objektu.|  
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Upozorní objekt, který může vrátit do normálního režimu pro zápis do jeho objekt úložiště. Implementace knihovny ATL vrátí hodnotu S_OK.|  
  
## <a name="remarks"></a>Poznámky  
 `IPersistStorageImpl` implementuje [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) rozhraní, která umožňuje klientovi požadavek, aby objekt zatížení a uložte trvalá data pomocí úložiště.  
  
 Implementaci této třídy vyžaduje třídu `T` provést implementaci `IPersistStreamInit` rozhraní, které jsou k dispozici prostřednictvím `QueryInterface`. Obvykle to znamená, že třída `T` by měl být odvozen z [ipersiststreaminitimpl –](../../atl/reference/ipersiststreaminitimpl-class.md), zadejte položku pro `IPersistStreamInit` v [mapy modelu COM.](http://msdn.microsoft.com/library/ead2a1e3-334d-44ad-bb1f-b94bb14c2333)a použít [mapování](http://msdn.microsoft.com/library/bfe30be6-62c3-4dc2-bd49-21ef96f15427) k popisu třídy trvalá data.  
  
 **Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID  
 Načte identifikátor CLSID objektu.  
  
```
STDMETHOD(GetClassID)(CLSID* pClassID);
```  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersist::GetClassID](http://msdn.microsoft.com/library/windows/desktop/ms688664) ve Windows SDK.  
  
##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage  
 Nastaví objekt, který chcete uvolnit všechny objekty úložiště a HandsOff režimu.  
  
```
STDMETHOD(HandsOffStorage)(void);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersistStorage::HandsOffStorage](http://msdn.microsoft.com/library/windows/desktop/ms679742) ve Windows SDK.  
  
##  <a name="initnew"></a>  IPersistStorageImpl::InitNew  
 Inicializuje nové úložiště.  
  
```
STDMETHOD(InitNew)(IStorage*);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace knihovny ATL delegoval vůči [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní.  
  
 Zobrazit [IPersistStorage:InitNew](http://msdn.microsoft.com/library/windows/desktop/ms687194) ve Windows SDK.  
  
##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty  
 Kontroluje, zda data objektu se změnila od posledního uložení.  
  
```
STDMETHOD(IsDirty)(void);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace knihovny ATL delegoval vůči [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní.  
  
 Zobrazit [IPersistStorage:IsDirty](http://msdn.microsoft.com/library/windows/desktop/ms683910) ve Windows SDK.  
  
##  <a name="load"></a>  IPersistStorageImpl::Load  
 Načte vlastnosti objektu ze zadané úložiště.  
  
```
STDMETHOD(Load)(IStorage* pStorage);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace knihovny ATL delegoval vůči [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní. `Load` datový proud s názvem "Obsah" se používá k načtení dat tohoto objektu. [Uložit](#save) metoda původně vytvoří tento datový proud.  
  
 Zobrazit [IPersistStorage:Load](http://msdn.microsoft.com/library/windows/desktop/ms680557) ve Windows SDK.  
  
##  <a name="save"></a>  IPersistStorageImpl::Save  
 Uloží do zadané úložiště vlastností objektu.  
  
```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```  
  
### <a name="remarks"></a>Poznámky  
 Implementace knihovny ATL delegoval vůči [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) rozhraní. Když `Save` je první volání vytvoří datový proud s názvem "Obsah" na zadané úložiště. Tento datový proud se pak použije v pozdější volání `Save` a ve voláních [zatížení](#load).  
  
 Zobrazit [IPersistStorage:Save](http://msdn.microsoft.com/library/windows/desktop/ms680680) ve Windows SDK.  
  
##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted  
 Upozorní objekt, který může vrátit do normálního režimu pro zápis do jeho objekt úložiště.  
  
```
STDMETHOD(SaveCompleted)(IStorage*);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK.  
  
### <a name="remarks"></a>Poznámky  
 Zobrazit [IPersistStorage:SaveCompleted](http://msdn.microsoft.com/library/windows/desktop/ms679713) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Úložiště a datové proudy](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Ipersiststreaminitimpl – třída](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [Ipersistpropertybagimpl – třída](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)
