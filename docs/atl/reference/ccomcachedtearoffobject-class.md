---
title: Třída CComCachedTearOffObject
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: 019b90c932de144d05fbf05f3ca339f4e5d6edd1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748100"
---
# <a name="ccomcachedtearoffobject-class"></a>Třída CComCachedTearOffObject

Tato třída implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro rozhraní odtržení.

## <a name="syntax"></a>Syntaxe

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parametry

*Obsažené*<br/>
Vaše třída odtržení, odvozená od `CComTearOffObjectBase` a rozhraní, která chcete podporovat objekt odtržení.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor|
|[CComCachedTearOffObject::~CComCachedTearOffObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Zintáží počet odkazů `CComCachedTearOffObject` pro objekt.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Volá `m_contained::FinalConstruct` metodu (tear-off class).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Volá `m_contained::FinalRelease` metodu (tear-off class).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Vrátí ukazatel na `IUnknown` `CComCachedTearOffObject` objekt nebo na požadované rozhraní ve třídě odtržení `contained`(třída).|
|[CComCachedTearOffObject::Vydání](#release)|Sníží počet odkazů pro `CComCachedTearOffObject` objekt a zničí jej, pokud je počet odkazů 0.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Objekt `CComContainedObject` odvozený z třídy odtržení `contained`(třída).|

## <a name="remarks"></a>Poznámky

`CComCachedTearOffObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro rozhraní odtržení. Tato třída se `CComTearOffObject` liší `CComCachedTearOffObject` od `IUnknown`v tom, který má `IUnknown` vlastní , odděleně od objektu vlastníka (vlastník je objekt, pro který je vytvořen odtržení). `CComCachedTearOffObject`udržuje svůj vlastní počet `IUnknown` odkazů na jeho a odstraní sám, jakmile jeho počet odkazů je nula. Pokud se však dotazujete na některé z jeho rozhraní odtržení, `IUnknown` bude se zvýší počet odkazů objektu vlastníka.

Pokud `CComCachedTearOffObject` objekt implementující odtržení je již vytvořena instance a odtržení rozhraní je dotazován znovu, stejný `CComCachedTearOffObject` objekt je znovu použit. Naproti tomu pokud tear-off rozhraní `CComTearOffObject` implementované a je znovu dotazován `CComTearOffObject` prostřednictvím objektu vlastníka, jiné bude vytvořena instance.

Třída vlastníka `FinalRelease` musí `Release` implementovat a `IUnknown` volat `CComCachedTearOffObject`do mezipaměti pro , který sníží počet odkazů. To způsobí, `CComCachedTearOffObject` `FinalRelease` že bude volána a odstranit odtrhávací.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a>CComCachedTearOffObject::AddRef

Zintáží počet odkazů `CComCachedTearOffObject` objektu o 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

Konstruktor

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*Pv*<br/>
[v] Ukazatel na `IUnknown` . `CComCachedTearOffObject`

### <a name="remarks"></a>Poznámky

Inicializuje `CComContainedObject` člen, [m_contained](#m_contained).

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a>CComCachedTearOffObject::~CComCachedTearOffObject

Destruktor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volání [FinalRelease](#finalrelease).

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

Volání `m_contained::FinalConstruct` k `m_contained`vytvoření `CComContainedObject` <  `contained` ,> objekt používaný pro přístup k rozhraní implementované odtrhávací třídy.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

Volání `m_contained::FinalRelease` zdarma `m_contained` `CComContainedObject` <  `contained` ,> objekt.

```cpp
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a>CComCachedTearOffObject::m_contained

[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objekt odvozený z třídy odtržení.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parametry

*Obsažené*<br/>
[v] Vaše třída odtržení, odvozená od `CComTearOffObjectBase` a rozhraní, která chcete podporovat objekt odtržení.

### <a name="remarks"></a>Poznámky

`m_contained` Metody dědí se používají pro přístup k odtržení rozhraní ve třídě odtržení prostřednictvím `QueryInterface` `FinalConstruct`uložených `FinalRelease`odtrhávací objekt objekt , a .

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Identifikátor GUID požadovaného rozhraní.

*ppvObjekt*<br/>
[out] Ukazatel rozhraní identifikovaný *iid*nebo NULL, pokud rozhraní není nalezeno.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je `IUnknown`požadované rozhraní , vrátí `CComCachedTearOffObject`ukazatel `IUnknown` na vlastní a přírůstky počet odkazů. V opačném případě dotazy na rozhraní na odtrhávací třídy pomocí [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) metoda zděděné z `CComObjectRootEx`.

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a>CComCachedTearOffObject::Vydání

Sníží počet odkazů o 1 a pokud je počet odkazů 0, odstraní `CComCachedTearOffObject` objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí 0. V sestavení ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

## <a name="see-also"></a>Viz také

[Třída CComTearoffObject](../../atl/reference/ccomtearoffobject-class.md)<br/>
[Třída CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
