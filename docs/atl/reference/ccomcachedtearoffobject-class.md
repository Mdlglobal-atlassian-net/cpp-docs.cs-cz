---
title: Třída CComCachedTearOffObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1072faed01033bec9fec127318334f8a61ac29e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362879"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject – třída
Tato třída implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pro rozhraní úplné vypnutí.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template
 <class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
 ::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parametry  
 `contained`  
 Vaše úplné vypnutí třída odvozena od `CComTearOffObjectBase` a rozhraní chcete objektu úplné vypnutí pro podporu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor|  
|[CComCachedTearOffObject:: ~ CComCachedTearOffObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](#addref)|Zvýší počet odkazů pro `CComCachedTearOffObject` objektu.|  
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Volání `m_contained::FinalConstruct` (metoda úplné vypnutí třídy.).|  
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Volání `m_contained::FinalRelease` (metoda úplné vypnutí třídy.).|  
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Vrátí ukazatel na `IUnknown` z `CComCachedTearOffObject` objekt, nebo požadované rozhraní na vaší třídě úplné vypnutí (třída `contained`).|  
|[CComCachedTearOffObject::Release](#release)|Snižuje počet odkaz `CComCachedTearOffObject` objektu a zničí ji, pokud je počet odkazů 0.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CComCachedTearOffObject::m_contained](#m_contained)|A `CComContainedObject` objekt odvozen z úplné vypnutí třídy (třídy `contained`).|  
  
## <a name="remarks"></a>Poznámky  
 `CComCachedTearOffObject` implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) pro rozhraní úplné vypnutí. Tato třída se liší od `CComTearOffObject` v tom, že `CComCachedTearOffObject` má svou vlastní **IUnknown**, oddělený od vlastníka objektu **IUnknown** (Vlastník je objekt, pro který úplné vypnutí se vytváří). `CComCachedTearOffObject` udržuje vlastní počet odkazovat na jeho **IUnknown** a odstraní samotné po jeho počet odkazů nula. Ale pokud dotaz pro některý z jeho úplné – vypnuté rozhraní, počet odkazů objekt vlastníka **IUnknown** se zvýší.  
  
 Pokud `CComCachedTearOffObject` objektu implementace úplné vypnutí je již vytvořena instance a rozhraní úplné vypnutí je dotazován na znovu stejné `CComCachedTearOffObject` se znovu použije objekt. Naopak, pokud rozhraní úplné vypnutí implementované `CComTearOffObject` je znovu dotazován na prostřednictvím objektu vlastníka jiné `CComTearOffObject` bude vytvořena instance.  
  
 Musí implementovat třídu vlastníka `FinalRelease` a volání **verze** na uložená v mezipaměti **IUnknown** pro `CComCachedTearOffObject`, který bude snížení jeho počet odkazů. To způsobí, že `CComCachedTearOffObject`na `FinalRelease` volat a odstraňovat úplné vypnutí.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>  CComCachedTearOffObject::AddRef  
 Zvýší počet odkazů `CComCachedTearOffObject` objektu o 1.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject  
 Konstruktor  
  
```
CComCachedTearOffObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [v] Ukazatel **IUnknown** z `CComCachedTearOffObject`.  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje `CComContainedObject` člen [m_contained](#m_contained).  
  
##  <a name="dtor"></a>  CComCachedTearOffObject:: ~ CComCachedTearOffObject  
 Destruktor.  
  
```
~CComCachedTearOffObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky a volání [FinalRelease](#finalrelease).  
  
##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct  
 Volání **m_contained::FinalConstruct** k vytvoření `m_contained`, `CComContainedObject` <  `contained`> objekt použitý pro přístup k rozhraní implementované třídě úplné vypnutí.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease  
 Volání **m_contained::FinalRelease** k bezplatným `m_contained`, `CComContainedObject` <  `contained`> objektu.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained  
 A [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objekt odvozen od třídě úplné vypnutí.  
  
```
CcomContainedObject <contained> m_contained;
```     
  
### <a name="parameters"></a>Parametry  
 `contained`  
 [v] Vaše úplné vypnutí třída odvozena od `CComTearOffObjectBase` a rozhraní chcete objektu úplné vypnutí pro podporu.  
  
### <a name="remarks"></a>Poznámky  
 Metody `m_contained` dědí se používají pro přístup k rozhraní úplné vypnutí ve třídě úplné vypnutí prostřednictvím uložené v mezipaměti úplné vypnutí objektu `QueryInterface`, `FinalConstruct`, a `FinalRelease`.  
  
##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface  
 Načte ukazatel na požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor GUID se požadované rozhraní.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `iid`, nebo **NULL** Pokud rozhraní nebyl nalezen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud je požadované rozhraní **IUnknown**, vrátí ukazatel `CComCachedTearOffObject`na vlastní **IUnknown** a zvýší počet odkazů. Jinak, dotazuje na rozhraní na vaše úplné vypnutí třídy pomocí [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) metoda zděděno z `CComObjectRootEx`.  

  
##  <a name="release"></a>  CComCachedTearOffObject::Release  
 Snižuje počet reference o 1 a, pokud počet odkazů 0, odstraní `CComCachedTearOffObject` objektu.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro bez ladění vždy vrátí hodnotu 0. V sestavení pro ladění vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování.  
  
## <a name="see-also"></a>Viz také  
 [CComTearOffObject – třída](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
