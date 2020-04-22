---
title: Třída CComAggObject
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: b9200c9c396fc16b6df3f4c2f4c66fb7976316d4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748161"
---
# <a name="ccomaggobject-class"></a>Třída CComAggObject

Tato třída implementuje rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro agregovaný objekt. Podle definice je agregovaný objekt obsažen uvnitř vnějšího objektu. Třída `CComAggObject` je podobná [CComObject Class](../../atl/reference/ccomobject-class.md)s tím rozdílem, že zpřístupňuje rozhraní, které je přímo přístupné externím klientům.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*Obsažené*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jiných rozhraní, které chcete podporovat na objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|Konstruktor|
|[CComAggObject::~CComAggObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Zvýšení počet odkazů na agregovaný objekt.|
|[CComAggObject::CreateInstance](#createinstance)|Tato statická funkce umožňuje vytvořit nový **objekt CComAggObject<** `contained` **>** bez režie [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci . `m_contained`|
|[CComAggObject::FinalRelease CComAggObject::FinalRelease CComAggObject::FinalRelease CCom](#finalrelease)|Provede konečné `m_contained`zničení .|
|[CComAggObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComAggObject::Vydání](#release)|Sníží počet odkazů na agregovaný objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Delegáti `IUnknown` volání vnější neznámé.|

## <a name="remarks"></a>Poznámky

`CComAggObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro agregovaný objekt. `CComAggObject`má své `IUnknown` vlastní rozhraní, oddělené od `IUnknown` vnějšího objektu rozhraní a udržuje svůj vlastní počet odkazů.

Další informace o agregaci naleznete v článku [Základy objektů ATL COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a>CComAggObject::AddRef

Zvýšení počet odkazů na agregovaný objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a>CComAggObject::CComAggObject

Konstruktor

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[v] Vnější neznámý.

### <a name="remarks"></a>Poznámky

Inicializuje `CComContainedObject` člen, [m_contained](#m_contained)a zintáží počet zámek modulu.

Destruktor sníží počet zámek modulu.

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a>CComAggObject::~CComAggObject

Destruktor.

```
~CComAggObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volá [FinalRelease](#finalrelease)a sníží počet zámek modulu.

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a>CComAggObject::CreateInstance

Tato statická funkce umožňuje vytvořit nový **objekt CComAggObject<** `contained` **>** bez režie [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*Stran*<br/>
[out] Ukazatel na **CComAggObject\<**<em>obsahoval</em> **>** ukazatel. Pokud `CreateInstance` je neúspěšný, *pp* je nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrácený objekt má počet odkazů nula, takže okamžitě volat, `AddRef` pak použijte `Release` k uvolnění odkazu na ukazatel objektu, když jste hotovi.

Pokud nepotřebujete přímý přístup k objektu, ale přesto chcete vytvořit `CoCreateInstance`nový objekt bez režie , použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a>CComAggObject::FinalConstruct

Volána během závěrečné fáze konstrukce objektu, tato metoda provede všechny konečné inicializace na [m_contained](#m_contained) člen.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a>CComAggObject::FinalRelease CComAggObject::FinalRelease CComAggObject::FinalRelease CCom

Volána během zničení objektu, tato metoda uvolní [m_contained](#m_contained) člen.

```cpp
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a>CComAggObject::m_contained

[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objekt odvozený z vaší třídy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*Obsažené*<br/>
[v] Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jiných rozhraní, které chcete podporovat na objektu.

### <a name="remarks"></a>Poznámky

Všechna `IUnknown` volání `m_contained` prostřednictvím jsou delegovány na vnější neznámé.

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a>CComAggObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel rozhraní identifikovaný *iid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObject* nastavena na hodnotu NULL.

*Stran*<br/>
[out] Ukazatel na ukazatel rozhraní identifikovaný `Q`typem . Pokud objekt nepodporuje toto rozhraní, *pp* je nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je `IUnknown`požadované `QueryInterface` rozhraní , vrátí ukazatel na vlastní `IUnknown` agregované objektu a přírůstky počet odkazů. Jinak tato metoda dotazy pro rozhraní `CComContainedObject` prostřednictvím člena, [m_contained](#m_contained).

## <a name="ccomaggobjectrelease"></a><a name="release"></a>CComAggObject::Vydání

Sníží počet odkazů na agregovaný objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění `Release` vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V sestaveních bez ladění `Release` vždy vrátí 0.

## <a name="see-also"></a>Viz také

[Třída CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Třída CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
