---
title: CComContainedObject – třída
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: c5e2fa64cc0938e632a37eac7dd1d6e9111c3d98
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497322"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject – třída

Tato třída implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pomocí delegování objektu `IUnknown`vlastníka.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parametry

*Základ*<br/>
Vaše třída odvozená z [třídy CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor Inicializuje ukazatel na člen na objekt `IUnknown`vlastníka.|
|[CComContainedObject::~CComContainedObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComContainedObject:: AddRef](#addref)|Zvýší počet odkazů u objektu Owner.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Načte objekt `IUnknown`vlastníka.|
|[CComContainedObject::QueryInterface](#queryinterface)|Načte ukazatel na rozhraní požadované na objektu Owner.|
|[CComContainedObject::Release](#release)|Sníží počet odkazů u objektu Owner.|

## <a name="remarks"></a>Poznámky

ATL používá `CComContainedObject` ve třídách [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)a [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pomocí delegování objektu `IUnknown`vlastníka. (Vlastník je buď vnější objekt agregace, nebo objekt, pro který je vytvářeno nepoužívané rozhraní.) `CComContainedObject` volání`CComObjectRootEx` ,`OuterRelease` a,`Base`která jsou zděděna prostřednictvím. `OuterAddRef` `OuterQueryInterface`

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComContainedObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="addref"></a>CComContainedObject:: AddRef

Zvýší počet odkazů u objektu Owner.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

##  <a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

Konstruktor

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
pro Objekt `IUnknown`vlastníka.

### <a name="remarks"></a>Poznámky

Nastaví ukazatel na `Base`člen (zděděný přes třídu) na souč_hod. `m_pOuterUnknown`

##  <a name="dtor"></a>CComContainedObject:: ~ CComContainedObject

Destruktor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky.

##  <a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown

Vrátí ukazatel `m_pOuterUnknown` na člen (zděděný prostřednictvím *základní* třídy), který obsahuje objekt `IUnknown`vlastníka.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `IUnknown`vlastníka.

### <a name="remarks"></a>Poznámky

Tato metoda může být virtuální, `Base` Pokud má deklaraci [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) makro.

##  <a name="queryinterface"></a>  CComContainedObject::QueryInterface

Načte ukazatel na rozhraní požadované na objektu Owner.

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

##  <a name="release"></a>CComContainedObject:: Release

Sníží počet odkazů u objektu Owner.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení `Release` ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V sestaveních `Release` bez ladění vždy vrátí hodnotu 0.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
