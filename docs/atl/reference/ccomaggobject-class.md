---
title: CComAggObject – třída
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
ms.openlocfilehash: 52cdddb1d922ca21e24122422ca14d9c12d13a83
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259921"
---
# <a name="ccomaggobject-class"></a>CComAggObject – třída

Tato třída implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) rozhraní pro agregovaného objektu. Podle definice agregovaného objektu je součástí vnějšího objektu. `CComAggObject` Třída je podobně jako [CComObject – třída](../../atl/reference/ccomobject-class.md), s tím rozdílem, že poskytuje rozhraní, které jsou přímo přístupné specialistům do externích klientů.

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*obsažené*<br/>
Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|Konstruktor|
|[CComAggObject::~CComAggObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Zvýší počet odkazů na agregovaný objekt.|
|[CComAggObject::CreateInstance](#createinstance)|Tato statická funkce vám umožní vytvořit nový **CComAggObject <** `contained` **>** objektu bez režie [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci `m_contained`.|
|[CComAggObject::FinalRelease](#finalrelease)|Provádí konečné zničení `m_contained`.|
|[CComAggObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComAggObject::Release](#release)|Sníží počet odkaz na agregovaný objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Delegáti `IUnknown` volání vnější neznámá.|

## <a name="remarks"></a>Poznámky

`CComAggObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro agregovaného objektu. `CComAggObject` má vlastní `IUnknown` rozhraní, odděleně od vnějšího objektu `IUnknown` rozhraní a udržuje svůj vlastní počet odkazů.

Další informace o agregaci naleznete v článku [základy ATL COM objekty](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="addref"></a>  CComAggObject::AddRef

Zvýší počet odkazů na agregovaný objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

##  <a name="ccomaggobject"></a>  CComAggObject::CComAggObject

Konstruktor

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
[in] Vnější neznámá.

### <a name="remarks"></a>Poznámky

Inicializuje `CComContainedObject` člen [m_contained](#m_contained)a zvýší počet zámků modulů.

Destruktor sníží počet zámků modulů.

##  <a name="dtor"></a>  CComAggObject::~CComAggObject

Destruktor.

```
~CComAggObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volání [FinalRelease](#finalrelease), a sníží počet modul zámku.

##  <a name="createinstance"></a>  CComAggObject::CreateInstance

Tato statická funkce vám umožní vytvořit nový **CComAggObject <** `contained` **>** objektu bez režie [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*pp*<br/>
[out] Ukazatel **CComAggObject\<**<em>obsažené</em> **>** ukazatele. Pokud `CreateInstance` neproběhne úspěšně, *pp* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Objekt vrácený má nulový počet odkaz, takže volání `AddRef` okamžitě, pak použijte `Release` uvolnit odkaz na ukazatel objektu, až budete hotovi.

Pokud není nutné přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.

##  <a name="finalconstruct"></a>  CComAggObject::FinalConstruct

Volá se v závěrečných fázích vytváření objektu, tato metoda provádí na všechny konečné inicializace [m_contained](#m_contained) člena.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="finalrelease"></a>  CComAggObject::FinalRelease

Volá se během odstraňování objektů, tato metoda uvolní [m_contained](#m_contained) člena.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComAggObject::m_contained

A [ccomcontainedobject –](../../atl/reference/ccomcontainedobject-class.md) objekt odvozený od vaší třídy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*obsažené*<br/>
[in] Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.

### <a name="remarks"></a>Poznámky

Všechny `IUnknown` provádí volání prostřednictvím `m_contained` se deleguje na vnější neznámá.

##  <a name="queryinterface"></a>  CComAggObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
[in] Identifikátor se požadované rozhraní.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*. Pokud objekt nepodporuje toto rozhraní *ppvObject* nastaven na hodnotu NULL.

*pp*<br/>
[out] Ukazatel na ukazatel rozhraní, které jsou určeny podle typu `Q`. Pokud objekt nepodporuje toto rozhraní *pp* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je požadovaná rozhraní `IUnknown`, `QueryInterface` vrací ukazatel na agregovaný objektu vlastní `IUnknown` a zvýší počet odkazů. Jinak tato metoda dotazuje na rozhraní prostřednictvím `CComContainedObject` člen [m_contained](#m_contained).

##  <a name="release"></a>  CComAggObject::Release

Sníží počet odkaz na agregovaný objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V ladicím buildu `Release` vrátí hodnotu, která může být užitečné pro diagnostiku a testování. V sestaveních bez ladění `Release` vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[CComObject – třída](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
