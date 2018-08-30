---
title: Ccomcontainedobject – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba67a990b027ff4cd770a0583f6d857a0ee7c725
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201038"
---
# <a name="ccomcontainedobject-class"></a>Ccomcontainedobject – třída
Tato třída implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) delegováním objekt vlastníka `IUnknown`.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class Base>  
class CComContainedObject : public Base
```  
  
#### <a name="parameters"></a>Parametry  
 *základ*  
 Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor Inicializuje člen ukazatel na objekt vlastníka `IUnknown`.|  
|[Ccomcontainedobject –:: ~ ccomcontainedobject –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComContainedObject::AddRef](#addref)|Zvýší počet odkazů na objekt vlastníka.|  
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Načte objekt vlastníka `IUnknown`.|  
|[CComContainedObject::QueryInterface](#queryinterface)|Načte ukazatel na objekt vlastníka požadované rozhraní.|  
|[CComContainedObject::Release](#release)|Sníží počet odkaz na objekt vlastníka.|  
  
## <a name="remarks"></a>Poznámky  
 ATL – používá `CComContainedObject` ve třídách [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), a [ccomcachedtearoffobject –](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) delegováním objekt vlastníka `IUnknown`. (Vlastník je buď objekt vnější agregaci, nebo objektu, pro kterou se vytváří odtržených rozhraní). `CComContainedObject` volání `CComObjectRootEx`společnosti `OuterQueryInterface`, `OuterAddRef`, a `OuterRelease`, všechny děděné přes `Base`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `Base`  
  
 `CComContainedObject`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="addref"></a>  CComContainedObject::AddRef  
 Zvýší počet odkazů na objekt vlastníka.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku a testování.  
  
##  <a name="ccomcontainedobject"></a>  CComContainedObject::CComContainedObject  
 Konstruktor  
  
```
CComContainedObject(void* pv);
```  
  
### <a name="parameters"></a>Parametry  
 *PV*  
 [in] Objekt vlastníka `IUnknown`.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví `m_pOuterUnknown` ukazatel na člen (zděděné z `Base` třídy) k *pv*.  
  
##  <a name="dtor"></a>  Ccomcontainedobject –:: ~ ccomcontainedobject –  
 Destruktor.  
  
```
~CComContainedObject();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="getcontrollingunknown"></a>  CComContainedObject::GetControllingUnknown  
 Vrátí `m_pOuterUnknown` ukazatel na člen (zděděné z *Base* třídy), který obsahuje objekt vlastníka `IUnknown`.  
  
```
IUnknown* GetControllingUnknown();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Objekt vlastníka `IUnknown`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda může být virtuální Pokud `Base` je deklarovaný [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) – makro.  
  
##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface  
 Načte ukazatel na objekt vlastníka požadované rozhraní.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parametry  
 *identifikátor IID*  
 [in] Identifikátor se požadované rozhraní.  
  
 *ppvObject*  
 [out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*. Pokud objekt nepodporuje toto rozhraní *ppvObject* nastaven na hodnotu NULL.  
  
 *str*  
 [out] Ukazatel na ukazatel rozhraní, které jsou určeny podle typu `Q`. Pokud objekt nepodporuje toto rozhraní *pp* nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnoty HRESULT.  
  
##  <a name="release"></a>  CComContainedObject::Release  
 Sníží počet odkaz na objekt vlastníka.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 V ladicím buildu `Release` vrátí hodnotu, která může být užitečné pro diagnostiku a testování. V sestaveních bez ladění `Release` vždy vrátí hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
