---
title: "Třída CComContainedObject | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3579d4080b4dba130b58592fa47efd636805ed1d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject – třída
Tato třída implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) delegováním k objektu vlastníka **IUnknown**.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComContainedObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 `Base`  
 Vlastní třídy odvozené od [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor Inicializuje člen ukazatel na objekt vlastníka `IUnknown`.|  
|[CComContainedObject:: ~ CComContainedObject](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComContainedObject::AddRef](#addref)|Zvětší počet odkaz objektu vlastníka.|  
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Načte objekt vlastníka `IUnknown`.|  
|[CComContainedObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované objektu vlastníka rozhraní.|  
|[CComContainedObject::Release](#release)|Snižuje počet odkaz objektu vlastníka.|  
  
## <a name="remarks"></a>Poznámky  
 ATL používá `CComContainedObject` ve třídách [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), a [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementuje [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) delegováním k objektu vlastníka **IUnknown**. (Vlastník je buď objekt vnější agregace, nebo objekt, pro kterou je vytvořen rozhraní úplné vypnutí.) `CComContainedObject` volání `CComObjectRootEx`na `OuterQueryInterface`, `OuterAddRef`, a `OuterRelease`, všechny zděděné prostřednictvím `Base`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComContainedObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>CComContainedObject::AddRef  
 Zvětší počet odkaz objektu vlastníka.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject  
 Konstruktor  
  
```
CComContainedObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 `pv`  
 [v] Objekt vlastníka **IUnknown**.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví `m_pOuterUnknown` člen ukazatele (zděděná prostřednictvím `Base` – třída) k `pv`.  
  
##  <a name="dtor"></a>CComContainedObject:: ~ CComContainedObject  
 Destruktor.  
  
```
~CComContainedObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown  
 Vrátí `m_pOuterUnknown` člen ukazatele (zděděná prostřednictvím *základní* třída) která obsahuje vlastníka objektu **IUnknown**.  
  
```
IUnknown* GetControllingUnknown();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt vlastníka **IUnknown**.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být virtuální Pokud `Base` deklaruje [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) makro.  
  
##  <a name="queryinterface"></a>CComContainedObject::QueryInterface  
 Načte ukazatel na požadované objektu vlastníka rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Identifikátor rozhraní požadováno.  
  
 `ppvObject`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `iid`. Pokud objekt nepodporuje toto rozhraní `ppvObject` je nastaven na **NULL**.  
  
 `pp`  
 [out] Ukazatel na ukazatel rozhraní typ identifikovat `Q`. Pokud objekt nepodporuje toto rozhraní `pp` je nastaven na **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="release"></a>CComContainedObject::Release  
 Snižuje počet odkaz objektu vlastníka.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V sestavení pro ladění **verze** vrátí hodnotu, která může být užitečné pro diagnostiku nebo testování. V sestavení pro bez ladění **verze** vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
