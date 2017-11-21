---
title: "Třída IEnumOnSTLImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl
- ATLCOM/ATL::IEnumOnSTLImpl::Clone
- ATLCOM/ATL::IEnumOnSTLImpl::Init
- ATLCOM/ATL::IEnumOnSTLImpl::Next
- ATLCOM/ATL::IEnumOnSTLImpl::Reset
- ATLCOM/ATL::IEnumOnSTLImpl::Skip
- ATLCOM/ATL::IEnumOnSTLImpl::m_iter
- ATLCOM/ATL::IEnumOnSTLImpl::m_pcollection
- ATLCOM/ATL::IEnumOnSTLImpl::m_spUnk
dev_langs: C++
helpviewer_keywords: IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 50cb78893eeca685f0b538fad397aca445502776
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ienumonstlimpl-class"></a>IEnumOnSTLImpl – třída
Tato třída definuje enumerátor rozhraní na základě kolekce standardní knihovna C++.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Enumerátor COM ( [IEnumXXXX](https://msdn.microsoft.com/library/ms680089.aspx)) rozhraní.  
  
 `piid`  
 Ukazatel na hodnotu Identifikátoru rozhraní enumerátor.  
  
 `T`  
 Typ položky, které jsou vystavené rozhraní enumerátor.  
  
 `Copy`  
 A [zkopírujte zásady třída](../../atl/atl-copy-policy-classes.md).  
  
 `CollType`  
 Kontejner – třída standardní knihovna C++.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|Implementace [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx).|  
|[IEnumOnSTLImpl::Init](#init)|Inicializuje enumerátor.|  
|[IEnumOnSTLImpl::Next](#next)|Implementace [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx).|  
|[IEnumOnSTLImpl::Reset](#reset)|Implementace [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx).|  
|[IEnumOnSTLImpl::Skip](#skip)|Implementace [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx).|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterator, který představuje enumerátor na aktuální pozici v rámci kolekce.|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Ukazatel ke kontejneru standardní knihovna C++, která uchovává položky, které chcete vytvořit její výčet.|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|**IUnknown** ukazatele objektu poskytuje kolekci.|  
  
## <a name="remarks"></a>Poznámky  
 `IEnumOnSTLImpl`poskytuje implementaci pro rozhraní modelu COM enumerátor ve výčtu jsou umístění v kontejneru C++ Standard kompatibilní knihovny. Tato třída je obdobou [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) třídy, která poskytuje implementaci pro rozhraní enumerátor na základě pole.  
  
> [!NOTE]
>  V tématu [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) podrobnosti o další rozdíly mezi `CComEnumImpl` a `IEnumOnSTLImpl`.  
  
 Obvykle bude *není* muset vytvořit vlastní Enumerátor třídy odvozené z této implementaci rozhraní. Pokud chcete použít enumerátor zadané ATL podle kontejner standardní knihovna C++, je dnes běžné k vytvoření instance [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), nebo vytvořit třídu kolekce, která vrací enumerátor odvozené z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).  
  
 Ale pokud potřebujete zajistit vlastní enumerátor, (například jeden, který zveřejňuje rozhraní kromě rozhraní enumerátor), můžete odvozovat z této třídy. V takovém případě je pravděpodobné, že budete potřebovat k přepsání [klon](#clone) metody můžete zajistit vlastní implementaci.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="init"></a>IEnumOnSTLImpl::Init  
 Inicializuje enumerátor.  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>Parametry  
 `pUnkForRelease`  
 [v] **IUnknown** ukazatele objektu, který musí být zachováno po dobu životnosti enumerátor. Předat **NULL** Pokud takový objekt existuje.  
  
 `collection`  
 Odkaz na kontejner standardní knihovna C++, který obsahuje položky, které chcete vytvořit její výčet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte `Init` odkaz na kolekci uchovávat v jiném objektu, můžete použít `pUnkForRelease` parametr zajistit, že objektu a kolekce drží, je k dispozici pro tak dlouho, dokud jej potřebuje enumerátor.  
  
 Tato metoda musí volat před předáním ukazatele rozhraní enumerátor zpět na všechny klienty.  
  
##  <a name="clone"></a>IEnumOnSTLImpl::Clone  
 Tato metoda poskytuje implementace [IEnumXXXX::Clone](https://msdn.microsoft.com/library/ms690336.aspx) metoda tak, že vytvoříte objekt typu `CComEnumOnSTL`, inicializace stejným kolekce a iterator používá aktuální objekt nebo vrátit rozhraní na nově vytvořený objekt.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Enumerátor rozhraní na nově vytvořený objekt klonovat z aktuální enumerátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="m_spunk"></a>IEnumOnSTLImpl::m_spUnk  
 **IUnknown** ukazatele objektu poskytuje kolekci.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>Poznámky  
 Ukazatel this inteligentní udržuje odkaz na objekt předaný [IEnumOnSTLImpl::Init](#init), zajistíte, aby zůstala aktivní po dobu životnosti enumerátor.  
  
##  <a name="m_pcollection"></a>IEnumOnSTLImpl::m_pcollection  
 Tento člen odkazuje na kolekci, která poskytuje data řídící implementace rozhraní enumerátor.  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen se inicializuje pomocí volání [IEnumOnSTLImpl::Init](#init).  
  
##  <a name="m_iter"></a>IEnumOnSTLImpl::m_iter  
 Tento člen obsahuje iterator používá k označení aktuální pozici v rámci kolekce a přejděte na další prvky.  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="next"></a>IEnumOnSTLImpl::Next  
 Tato metoda poskytuje implementace [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) metoda.  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet elementů požadovaný.  
  
 `rgelt`  
 [out] Pole pro vyplnění elementy.  
  
 `pceltFetched`  
 [out] Počet elementů ve skutečnosti, vrátí se v `rgelt`. To může být menší než `celt` Pokud méně než `celt` elementy zůstanou v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="reset"></a>IEnumOnSTLImpl::Reset  
 Tato metoda poskytuje implementace [IEnumXXXX::Reset](https://msdn.microsoft.com/library/ms693414.aspx) metoda.  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="skip"></a>IEnumOnSTLImpl::Skip  
 Tato metoda poskytuje implementace [IEnumXXXX::Skip](https://msdn.microsoft.com/library/ms690392.aspx) metoda.  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet elementů tak, aby přeskočil.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
