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
ms.openlocfilehash: 8b05284104f9d2e5e7704bceaee6f8adf9a33aac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497661"
---
# <a name="ccomaggobject-class"></a>CComAggObject – třída

Tato třída implementuje rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro agregovaný objekt. Podle definice je agregovaný objekt obsažen v rámci vnějšího objektu. Třída je podobná třídě CComObject, s tím rozdílem, že zpřístupňuje rozhraní, které je přímo přístupné pro externí klienty. [](../../atl/reference/ccomobject-class.md) `CComAggObject`

## <a name="syntax"></a>Syntaxe

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*uložen*<br/>
Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)a také z jiných rozhraní, která chcete pro objekt podporovat.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|Konstruktor|
|[CComAggObject::~CComAggObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComAggObject:: AddRef](#addref)|Zvýší počet odkazů u agregovaného objektu.|
|[CComAggObject:: CreateInstance](#createinstance)|Tato statická funkce umožňuje vytvořit nový objekt **<** `contained` **>** CComAggObject bez režie funkce [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComAggObject::FinalConstruct](#finalconstruct)|Provede konečnou inicializaci `m_contained`.|
|[CComAggObject::FinalRelease](#finalrelease)|Provede konečné zničení `m_contained`.|
|[CComAggObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComAggObject:: Release](#release)|Sníží počet odkazů u agregovaného objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Deleguje `IUnknown` volání do vnějšího neznámého.|

## <a name="remarks"></a>Poznámky

`CComAggObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro agregovaný objekt. `CComAggObject`má své vlastní `IUnknown` rozhraní oddělené od `IUnknown` rozhraní vnějšího objektu a udržuje vlastní počet odkazů.

Další informace o agregaci naleznete v článku [Základy objektů ATL modelu COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="addref"></a>CComAggObject:: AddRef

Zvýší počet odkazů u agregovaného objektu.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

##  <a name="ccomaggobject"></a>CComAggObject::CComAggObject

Konstruktor

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
pro Vnější neznámý.

### <a name="remarks"></a>Poznámky

Inicializuje člen, m_contained a zvýší počet zámků modulu. [](#m_contained) `CComContainedObject`

Destruktor snižuje počet zámků modulu.

##  <a name="dtor"></a>CComAggObject:: ~ CComAggObject

Destruktor.

```
~CComAggObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, zavolá [FinalRelease](#finalrelease)a sníží počet zámků modulu.

##  <a name="createinstance"></a>CComAggObject:: CreateInstance

Tato statická funkce umožňuje vytvořit nový objekt **<** `contained` **>** CComAggObject bez režie funkce [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parametry

*pp*<br/>
mimo Ukazatel na **CComAggObject\<** <em>obsažený</em> **>** ukazatel. Pokud `CreateInstance` je neúspěšné, je *PP* nastaven na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrácený objekt má nulový počet odkazů, takže zavolejte `AddRef` hned a pak použijte `Release` k uvolnění odkazu na ukazatel objektu, až budete hotovi.

Pokud nepotřebujete přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte raději [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) .

##  <a name="finalconstruct"></a>CComAggObject::FinalConstruct

Tato metoda je volána během finálních fází konstrukce objektu, provádí jakoukoli konečnou inicializaci člena [m_contained](#m_contained) .

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="finalrelease"></a>CComAggObject::FinalRelease

Volá se během zničení objektu. Tato metoda uvolní člen [m_contained](#m_contained) .

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComAggObject::m_contained

Objekt [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) odvozený z vaší třídy.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parametry

*uložen*<br/>
pro Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)a také z jiných rozhraní, která chcete pro objekt podporovat.

### <a name="remarks"></a>Poznámky

Všechna `IUnknown` volání prostřednictvím `m_contained` jsou delegována na vnější neznámý.

##  <a name="queryinterface"></a>CComAggObject:: QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor požadovaného rozhraní.

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *identifikátorem IID*. Pokud objekt nepodporuje toto rozhraní, je *ppvObject* nastaveno na hodnotu null.

*pp*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný typem `Q`. Pokud objekt nepodporuje toto rozhraní, je *PP* nastaven na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je `IUnknown`požadované rozhraní, `QueryInterface` vrátí ukazatel na vlastní `IUnknown` agregovaný objekt a zvýší počet odkazů. V opačném případě se tato metoda dotazuje pro `CComContainedObject` rozhraní prostřednictvím členu, [m_contained](#m_contained).

##  <a name="release"></a>CComAggObject:: Release

Sníží počet odkazů u agregovaného objektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení `Release` ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V sestaveních `Release` bez ladění vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[CComObject – třída](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
