---
title: CComObject – třída
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: 045292e4d06b1e86e991a755b267660b72a178da
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299553"
---
# <a name="ccomobject-class"></a>CComObject – třída

Tato třída implementuje `IUnknown` pro neagregovaná objekt.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parametry

*základ*<br/>
Vaše třída odvozena od [ccomobjectroot –](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), jak dobře jako z jiných rozhraní, které chcete podporovat na objekt.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|Konstruktor|
|[CComObject::~CComObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Zvýší počet odkazů na objekt.|
|[CComObject::CreateInstance](#createinstance)|(Statické) Vytvoří novou `CComObject` objektu.|
|[CComObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComObject::Release](#release)|Sníží počet odkaz na objekt.|

## <a name="remarks"></a>Poznámky

`CComObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro neagregovaná objekt. Nicméně volání `QueryInterface`, `AddRef`, a `Release` se deleguje na `CComObjectRootEx`.

Další informace o používání `CComObject`, najdete v článku [základy ATL COM objekty](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="addref"></a>  CComObject::AddRef

Zvýší počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrací nový počet odkazů zvýšena na objekt. Tato hodnota může být užitečné pro diagnostiku a testování.

##  <a name="ccomobject"></a>  CComObject::CComObject

Konstruktor inkrementuje počet zámků modulů.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>Typ void\*</em><br/>
[in] Tento nepojmenovaný parametr se nepoužívá. Existuje symetrie s jinými `CComXXXObjectXXX` konstruktory.

### <a name="remarks"></a>Poznámky

Sníží destruktor ho.

Pokud `CComObject`-odvozeného objektu je úspěšně vytvořený **nové** operátor, počet počáteční odkazů je 0. Pokud chcete nastavit počet odkazů na správnou hodnotu (1), ujistěte se, volání [AddRef](#addref) funkce.

##  <a name="dtor"></a>  CComObject::~CComObject

Destruktor.

```
CComObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volání [FinalRelease](ccomobjectrootex-class.md#finalrelease), a sníží počet modul zámku.

##  <a name="createinstance"></a>  CComObject::CreateInstance

Tato statická funkce vám umožní vytvořit nový **CComObject <** `Base` **>** objekt, bez režie [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parametry

*pp*<br/>
[out] Ukazatel **CComObject <** `Base` **>** ukazatele. Pokud `CreateInstance` neproběhne úspěšně, *pp* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Objekt vrácený má nulový počet odkaz, takže volání `AddRef` okamžitě, pak použijte `Release` uvolnit odkaz na ukazatel objektu, až budete hotovi.

Pokud není nutné přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>  CComObject::QueryInterface

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

##  <a name="release"></a>  CComObject::Release

Sníží počet odkaz na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrací nový počet odkazů sníží na objekt. V sestavení pro ladění může být vrácenou hodnotu užitečné pro diagnostiku a testování. V sestaveních bez ladění `Release` vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
