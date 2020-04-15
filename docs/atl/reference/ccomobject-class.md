---
title: Třída CComObject
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
ms.openlocfilehash: de6ffb45fe5c6f73ab656d5c6185b70d9f5edd38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327648"
---
# <a name="ccomobject-class"></a>Třída CComObject

Tato třída `IUnknown` implementuje pro neagregovaný objekt.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), stejně jako z jiných rozhraní, které chcete podporovat na objektu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CcomObject::CcomObject](#ccomobject)|Konstruktor|
|[CComObject::~CComObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComObject::Addref](#addref)|Zintáží počet odkazů na objekt.|
|[CComObject::CreateInstance](#createinstance)|(Statické) Vytvoří nový `CComObject` objekt.|
|[CComObject::QueryInterface](#queryinterface)|Načte ukazatel na požadované rozhraní.|
|[CComObject::Uvolnění](#release)|Sníží počet odkazů na objekt.|

## <a name="remarks"></a>Poznámky

`CComObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro neagregovaný objekt. Volání na `QueryInterface`, `AddRef`a `Release` jsou však delegovány na `CComObjectRootEx`.

Další informace o `CComObject`použití naleznete v článku [Základy objektů ATL COM](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomobjectaddref"></a><a name="addref"></a>CComObject::Addref

Zintáží počet odkazů na objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí nový počet přírůstek odkazů na objekt. Tato hodnota může být užitečná pro diagnostiku nebo testování.

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a>CcomObject::CcomObject

Konstruktor increments počet zámek modulu.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parametry

<em>void\*</em><br/>
[v] Tento nepojmenovaný parametr se nepoužívá. Existuje pro symetrii s jinými `CComXXXObjectXXX` konstruktory.

### <a name="remarks"></a>Poznámky

Destruktor ho sníží.

Pokud `CComObject`je odvozený objekt úspěšně vytvořen pomocí **nového** operátoru, počáteční počet odkazů je 0. Chcete-li nastavit počet odkazů na správnou hodnotu (1), proveďte volání funkce [AddRef.](#addref)

## <a name="ccomobjectccomobject"></a><a name="dtor"></a>CComObject::~CComObject

Destruktor.

```
CComObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky, volá [FinalRelease](ccomobjectrootex-class.md#finalrelease)a sníží počet zámek modulu.

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject::CreateInstance

Tato statická funkce umožňuje vytvořit nový **objekt CComObject<** `Base` **>** bez režie [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parametry

*Stran*<br/>
[out] Ukazatel na **ukazatel CComObject<.** `Base` **>** Pokud `CreateInstance` je neúspěšný, *pp* je nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vrácený objekt má počet odkazů nula, takže okamžitě volat, `AddRef` pak použijte `Release` k uvolnění odkazu na ukazatel objektu, když jste hotovi.

Pokud nepotřebujete přímý přístup k objektu, ale přesto chcete vytvořit `CoCreateInstance`nový objekt bez režie , použijte [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) místo.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject::QueryInterface

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

## <a name="ccomobjectrelease"></a><a name="release"></a>CComObject::Uvolnění

Sníží počet odkazů na objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí nový dekreed počet odkazů na objekt. V sestavení ladění může být vrácená hodnota užitečná pro diagnostiku nebo testování. V sestaveních bez ladění `Release` vždy vrátí 0.

## <a name="see-also"></a>Viz také

[Třída CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Třída CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
