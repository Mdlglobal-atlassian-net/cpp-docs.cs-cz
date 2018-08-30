---
title: Ienumonstlimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- IEnumOnSTLImpl class
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 15f0b26c5c86d023d98d6a13e6b92518756a3179
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43206203"
---
# <a name="ienumonstlimpl-class"></a>Ienumonstlimpl – třída
Tato třída definuje výčet rozhraní na základě kolekce standardní knihovny C++.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Base,
    const IID* piid, class T, class Copy, class CollType>  
class ATL_NO_VTABLE IEnumOnSTLImpl : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 *základ*  
 COM enumerátor. Zobrazit [IEnumString](/windows/desktop/api/objidl/nn-objidl-ienumstring) příklad.
  
 *piid*  
 Ukazatel na Identifikátor rozhraní rozhraní enumerátor.  
  
 *T*  
 Typ položky, které jsou vystavené rozhraní enumerátor.  
  
 *kopírování*  
 A [třídy zásady kopírování](../../atl/atl-copy-policy-classes.md).  
  
 *CollType*  
 Třída kontejneru standardní knihovny C++.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](#clone)|Provádění **klonování**.|  
|[IEnumOnSTLImpl::Init](#init)|Inicializuje čítače výčtu.|  
|[IEnumOnSTLImpl::Next](#next)|Provádění **Další**.|  
|[IEnumOnSTLImpl::Reset](#reset)|Provádění **resetování**.|  
|[IEnumOnSTLImpl::Skip](#skip)|Provádění **přeskočit**.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m_iter](#m_iter)|Iterátor, který představuje aktuální pozice čítače výčtu v rámci kolekce.|  
|[IEnumOnSTLImpl::m_pcollection](#m_pcollection)|Ukazatel na kontejneru standardní knihovny C++ obsahující položky, které chcete vytvořit výčet.|  
|[IEnumOnSTLImpl::m_spUnk](#m_spunk)|`IUnknown` Ukazatel objektu, který poskytuje kolekci.|  
  
## <a name="remarks"></a>Poznámky  
 `IEnumOnSTLImpl` poskytuje implementaci pro uložení položky výčtu v kontejneru kompatibilní knihovny C++ Standard rozhraní modelu COM enumerátor. Tato třída je obdobou [ccomenumimpl –](../../atl/reference/ccomenumimpl-class.md) třídu, která poskytuje implementaci pro enumerátor rozhraní založené na pole.  
  
> [!NOTE]
>  Zobrazit [CComEnumImpl::Init](../../atl/reference/ccomenumimpl-class.md#init) podrobnosti o další rozdíly mezi `CComEnumImpl` a `IEnumOnSTLImpl`.  
  
 Obvykle bude *není* muset vytvořit vlastní čítač třídy odvozené z implementace tohoto rozhraní. Pokud chcete použít enumerátor poskytované ATL podle kontejneru standardní knihovny C++, je běžné vytvořit instanci [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), nebo chcete-li vytvořit třídu kolekce, která vrací enumerátor odvozením z [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).  
  
 Ale pokud potřebujete poskytovat vlastní čítače výčtu (například jeden, který zpřístupňuje rozhraní kromě rozhraní enumerátor), můžete odvozovat z této třídy. V takovém případě je pravděpodobné, že bude nutné přepsat [klonování](#clone) metodu a zadejte vlastní implementaci.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="init"></a>  IEnumOnSTLImpl::Init  
 Inicializuje čítače výčtu.  
  
```
HRESULT Init(
    IUnknown* pUnkForRelease,
    CollType& collection);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnkForRelease*  
 [in] `IUnknown` Ukazatel objektu, který musí být zachováno po celou dobu životnosti enumerátor. Předejte hodnotu NULL, pokud žádný takový objekt neexistuje.  
  
 *Kolekce*  
 Odkaz na kontejner standardní knihovny C++, který obsahuje položky, které chcete vytvořit výčet.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Pokud předáte `Init` odkaz na kolekci uchovávat v jiném objektu, můžete použít *pUnkForRelease* parametr k zajištění, že objektu a kolekce obsahuje, je k dispozici pro tak dlouho, dokud jej potřebuje enumerátor.  
  
 Tato metoda musí volat před předáním ukazatel rozhraní enumerátor zpět na všechny klienty.  
  
##  <a name="clone"></a>  IEnumOnSTLImpl::Clone  
 Tato metoda poskytuje implementaci **klonování** metodu tak, že vytvoříte objekt typu `CComEnumOnSTL`, inicializuje se stejnými kolekce a používá aktuální objekt iterátoru a vrací rozhraní na nově vytvořený objekt.  
  
```
STDMETHOD(Clone)(Base** ppEnum);
```  
  
### <a name="parameters"></a>Parametry  
 *ppEnum*  
 [out] Enumerátor rozhraní na nově vytvořený objekt naklonovali z aktuální enumerátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="m_spunk"></a>  IEnumOnSTLImpl::m_spUnk  
 `IUnknown` Ukazatel objektu, který poskytuje kolekci.  
  
```
CComPtr<IUnknown> m_spUnk;
```  
  
### <a name="remarks"></a>Poznámky  
 Inteligentní ukazatele this udržuje odkaz na objekt předaný [IEnumOnSTLImpl::Init](#init), zajištění, že zůstane aktivní po dobu životnosti enumerátor.  
  
##  <a name="m_pcollection"></a>  IEnumOnSTLImpl::m_pcollection  
 Tento člen odkazuje na kolekci, která poskytuje data řízení implementací rozhraní enumerátor.  
  
```
CollType* m_pcollection;
```  
  
### <a name="remarks"></a>Poznámky  
 Tento člen je inicializován pomocí volání [IEnumOnSTLImpl::Init](#init).  
  
##  <a name="m_iter"></a>  IEnumOnSTLImpl::m_iter  
 Tento člen uchovává iterátor používá k označení aktuální pozici v rámci kolekce a přejděte na další prvky.  
  
```
CollType::iterator m_iter;
```  
  
##  <a name="next"></a>  IEnumOnSTLImpl::Next  
 Tato metoda poskytuje implementaci **Další** metody.  
  
```
STDMETHOD(Next)(
    ULONG celt,
    T* rgelt,
    ULONG* pceltFetched);
```  
  
### <a name="parameters"></a>Parametry  
 *celt*  
 [in] Počet prvků požadavku.  
  
 *rgelt*  
 [out] Pole pro vyplnění pomocí elementů.  
  
 *pceltFetched*  
 [out] Počet prvků ve skutečnosti vrátí v *rgelt*. To může být kratší než *celt* Pokud méně než *celt* prvky zůstanou v seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="reset"></a>  IEnumOnSTLImpl::Reset  
 Tato metoda poskytuje implementaci **resetování** metody.  
  
```
STDMETHOD(Reset)(void);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="skip"></a>  IEnumOnSTLImpl::Skip  
 Tato metoda poskytuje implementaci **přeskočit** metody.  
  
```
STDMETHOD(Skip)(ULONG celt);
```  
  
### <a name="parameters"></a>Parametry  
 *celt*  
 [in] Počet prvků, které mají přeskočit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
