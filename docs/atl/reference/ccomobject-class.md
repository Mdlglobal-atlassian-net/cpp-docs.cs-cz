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
ms.openlocfilehash: a2051932413d8658eb7cedb67ed0eab2077b599d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497138"
---
# <a name="ccomobject-class"></a>CComObject – třída

Tato třída implementuje `IUnknown` neagregovaný objekt.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parametry

*Základ*<br/>
Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)a také z jiných rozhraní, která chcete pro objekt podporovat.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComObject:: CComObject](#ccomobject)|Konstruktor|
|[CComObject::~CComObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComObject:: AddRef](#addref)|Zvýší počet odkazů na objekt.|
|[CComObject:: CreateInstance](#createinstance)|Tras Vytvoří nový `CComObject` objekt.|
|[CComObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComObject:: Release](#release)|Sníží počet odkazů na objekt.|

## <a name="remarks"></a>Poznámky

`CComObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro neagregovaný objekt. Nicméně volání `QueryInterface` `CComObjectRootEx`, `AddRef` a`Release` jsou delegována na.

Další informace o použití `CComObject`naleznete v článku [Základy objektů ATL modelu COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="addref"></a>CComObject:: AddRef

Zvýší počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrací nový přírůstek počtu odkazů na objekt. Tato hodnota může být užitečná pro diagnostiku nebo testování.

##  <a name="ccomobject"></a>CComObject:: CComObject

Konstruktor zvýší počet zámků modulu.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>šekem\*</em><br/>
pro Tento nepojmenovaný parametr se nepoužívá. Existuje pro symetrie s jinými `CComXXXObjectXXX` konstruktory.

### <a name="remarks"></a>Poznámky

Destruktor ho snižuje.

Pokud je `CComObject`objekt odvozený od úspěšného vytvoření pomocí operátoru **New** , počáteční počet odkazů je 0. Chcete-li nastavit počet odkazů na správnou hodnotu (1), proveďte volání funkce [AddRef](#addref) .

##  <a name="dtor"></a>CComObject:: ~ CComObject

Destruktor.

```
CComObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, zavolá [FinalRelease](ccomobjectrootex-class.md#finalrelease)a sníží počet zámků modulu.

##  <a name="createinstance"></a>CComObject:: CreateInstance

Tato statická funkce umožňuje vytvořit nový objekt **<** `Base` **>** CComObject bez režie funkce [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parametry

*pp*<br/>
mimo Ukazatel na **CComObject <** `Base` **>** ukazatel. Pokud `CreateInstance` je neúspěšné, je *PP* nastaven na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrácený objekt má nulový počet odkazů, takže zavolejte `AddRef` hned a pak použijte `Release` k uvolnění odkazu na ukazatel objektu, až budete hotovi.

Pokud nepotřebujete přímý přístup k objektu, ale přesto chcete vytvořit nový objekt bez režie `CoCreateInstance`, použijte raději [CComCoClass:: CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

##  <a name="queryinterface"></a>CComObject:: QueryInterface

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

##  <a name="release"></a>CComObject:: Release

Sníží počet odkazů na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrací nový snížený počet odkazů na objekt. V sestavení ladění může být návratová hodnota užitečná pro diagnostiku nebo testování. V sestaveních `Release` bez ladění vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[CComAggObject – třída](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject – třída](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
