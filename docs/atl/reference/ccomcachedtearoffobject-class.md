---
title: CComCachedTearOffObject – třída
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
ms.openlocfilehash: d993a349d38342bda30a83dfdbe25577953799b3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497539"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject – třída

Tato třída implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro odkládací rozhraní.

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

*uložen*<br/>
Odtrhnout třídu odvozenou z `CComTearOffObjectBase` a rozhraní, které chcete pro odložení objektu podporovat.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor|
|[CComCachedTearOffObject::~CComCachedTearOffObject](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComCachedTearOffObject:: AddRef](#addref)|Zvýší počet odkazů pro `CComCachedTearOffObject` objekt.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Volá metodu `m_contained::FinalConstruct` (metoda trhlin-off).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Volá metodu `m_contained::FinalRelease` (metoda trhlin-off).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Vrátí ukazatel na `IUnknown` `CComCachedTearOffObject` objekt, nebo na požadované rozhraní třídy trhliny (třída `contained`).|
|[CComCachedTearOffObject:: Release](#release)|Sníží počet odkazů u `CComCachedTearOffObject` objektu a odstraní jej, pokud je počet odkazů 0.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Objekt odvozený z vaší třídy s podtrhnout (třída `contained`). `CComContainedObject`|

## <a name="remarks"></a>Poznámky

`CComCachedTearOffObject`implementuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) pro odkládací rozhraní. Tato třída se liší od `CComTearOffObject` v, `CComCachedTearOffObject` která má svou `IUnknown`vlastní, oddělenou od objektu `IUnknown` vlastníka (vlastníkem je objekt, pro který se vytváří trhlina). `CComCachedTearOffObject`udržuje svůj vlastní počet odkazů na své `IUnknown` a odstraní sám sebe, jakmile je počet odkazů nula. Nicméně pokud se dotazuje na kterékoli z jeho nevypnutých rozhraní, zvýší se počet odkazů objektu `IUnknown` vlastníka.

Pokud objekt implementující trhlinu je již vytvořen a je znovu dotazováno na rozhraní, je stejný `CComCachedTearOffObject` objekt znovu použit. `CComCachedTearOffObject` Na rozdíl od toho, pokud je přerušené rozhraní implementované a `CComTearOffObject` znovu dotazováno pro objekt vlastníka, vytvoří se další `CComTearOffObject` instance.

Třída `FinalRelease` Owner musí implementovat a volat `Release` `IUnknown` v mezipaměti pro, čímž se sníží počet odkazů. `CComCachedTearOffObject` To způsobí `CComCachedTearOffObject` `FinalRelease` , že se bude volat a odstraní trhlinu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="addref"></a>CComCachedTearOffObject:: AddRef

Zvýší počet `CComCachedTearOffObject` odkazů objektu o 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku a testování.

##  <a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

Konstruktor

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*pv*<br/>
pro Ukazatel na `IUnknown`. `CComCachedTearOffObject`

### <a name="remarks"></a>Poznámky

Inicializuje člen m_contained. [](#m_contained) `CComContainedObject`

##  <a name="dtor"></a>CComCachedTearOffObject:: ~ CComCachedTearOffObject

Destruktor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volá [FinalRelease](#finalrelease).

##  <a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

Volání `m_contained::FinalConstruct` pro vytvoření `m_contained`, objekt `CComContainedObject` >`contained`, < který slouží k přístupu k rozhraní implementovanému podtřídy.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

##  <a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

Volání `m_contained::FinalRelease` Free `m_contained`, `CComContainedObject` objekt>.`contained` < 

```
void FinalRelease();
```

##  <a name="m_contained"></a>CComCachedTearOffObject::m_contained

Objekt [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) odvozený z vaší odkládací třídy.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parametry

*uložen*<br/>
pro Odtrhnout třídu odvozenou z `CComTearOffObjectBase` a rozhraní, které chcete pro odložení objektu podporovat.

### <a name="remarks"></a>Poznámky

Metody `m_contained` dědění se používají pro přístup k nevypnutému rozhraní ve vaší podtřídě pomocí nepřipojeného `QueryInterface`objektu v mezipaměti, `FinalConstruct`a `FinalRelease`.

##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*iid*<br/>
pro Identifikátor GUID požadovaného rozhraní

*ppvObject*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *identifikátorem IID*nebo hodnotu null, pokud rozhraní nebylo nalezeno.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je `IUnknown`požadované rozhraní, vrátí ukazatel `CComCachedTearOffObject`na vlastní `IUnknown` a zvýší počet odkazů. V opačném případě se dotazy na rozhraní třídy odtrhnout pomocí metody [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) zděděné z `CComObjectRootEx`.

##  <a name="release"></a>CComCachedTearOffObject:: Release

Sníží počet odkazů o 1 a, pokud je počet odkazů 0, `CComCachedTearOffObject` objekt odstraní.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí hodnotu 0. V sestavení ladění vrátí hodnotu, která může být užitečná pro diagnostiku nebo testování.

## <a name="see-also"></a>Viz také:

[CComTearOffObject – třída](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
