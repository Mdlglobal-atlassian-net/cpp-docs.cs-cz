---
title: Třída CComContainedObject
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
ms.openlocfilehash: 72ba27c3be6576621995ffb8c98995c6abc9324c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320787"
---
# <a name="ccomcontainedobject-class"></a>Třída CComContainedObject

Tato třída implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegováním na `IUnknown`objekt vlastníka .

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parametry

*Základní*<br/>
Vaše třída, odvozená z [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) nebo [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CComContainedObject::CComContainedObject](#ccomcontainedobject)|Konstruktor Inicializuje ukazatel člena na objekt `IUnknown`vlastníka .|
|[CComContainedObject::~CComContainedObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Zintáží počet odkazů na objekt vlastníka.|
|[CComContainedObject::GetControllingUnknown](#getcontrollingunknown)|Načte objekt vlastníka `IUnknown`.|
|[CComContainedObject::QueryInterface](#queryinterface)|Načte ukazatel na rozhraní požadované na objekt vlastníka.|
|[CComContainedObject::Vydání](#release)|Sníží počet odkazů na objekt vlastníka.|

## <a name="remarks"></a>Poznámky

ATL `CComContainedObject` používá ve třídách [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)a [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) delegováním na objekt `IUnknown`vlastníka . (Vlastník je buď vnější objekt agregace nebo objekt, pro který je vytvořeno rozhraní odtržení.) `CComContainedObject` všechny `CComObjectRootEx`hovory `OuterQueryInterface` `OuterAddRef`, `OuterRelease`a , všechny `Base`zděděné .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Base`

`CComContainedObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a>CComContainedObject::AddRef

Zintáží počet odkazů na objekt vlastníka.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CComContainedObject::CComContainedObject

Konstruktor

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[v] Objekt vlastníka `IUnknown`.

### <a name="remarks"></a>Poznámky

Nastaví `m_pOuterUnknown` ukazatel člena (zděděný prostřednictvím `Base` třídy) na *pv*.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CComContainedObject::~CComContainedObject

Destruktor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené zdroje.

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CComContainedObject::GetControllingUnknown

Vrátí `m_pOuterUnknown` ukazatel člena (zděděný prostřednictvím třídy *Base),* který obsahuje objekt vlastníka `IUnknown`.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Návratová hodnota

Objekt vlastníka `IUnknown`.

### <a name="remarks"></a>Poznámky

Tato metoda může `Base` být virtuální, pokud deklaroval [DECLARE_GET_CONTROLLING_UNKNOWN](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) makro.

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CComContainedObject::QueryInterface

Načte ukazatel na rozhraní požadované na objekt vlastníka.

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

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a>CComContainedObject::Vydání

Sníží počet odkazů na objekt vlastníka.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestavení ladění `Release` vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování. V sestaveních bez ladění `Release` vždy vrátí 0.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
