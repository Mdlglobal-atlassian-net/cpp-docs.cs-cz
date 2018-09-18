---
title: Ccomcachedtearoffobject – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40dddf2bb1619bd896ecf50008f80fca968ef8c9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075706"
---
# <a name="ccomcachedtearoffobject-class"></a>Ccomcachedtearoffobject – třída

Tato třída implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro rozhraní s odnímatelnými nabídkami.

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

*obsažené*<br/>
Vaše odtržených třída odvozena od `CComTearOffObjectBase` a rozhraní chcete, aby váš objekt odtržených pro podporu.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Konstruktor|
|[Ccomcachedtearoffobject –:: ~ ccomcachedtearoffobject –](#dtor)|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Zvýší počet odkazů `CComCachedTearOffObject` objektu.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Volání `m_contained::FinalConstruct` (metoda odtržených třídu).|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Volání `m_contained::FinalRelease` (metoda odtržených třídu).|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Vrací ukazatel na `IUnknown` z `CComCachedTearOffObject` objektu, nebo na požadované rozhraní na třídě odtržených (třída `contained`).|
|[CComCachedTearOffObject::Release](#release)|Sníží počet odkaz pro `CComCachedTearOffObject` objektu a odstraní ji, pokud počet odkazů je 0.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|A `CComContainedObject` objekt odvozený od vaší třídy odtržených (třída `contained`).|

## <a name="remarks"></a>Poznámky

`CComCachedTearOffObject` implementuje [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) pro rozhraní s odnímatelnými nabídkami. Tato třída se liší od `CComTearOffObject` v tom, že `CComCachedTearOffObject` má vlastní `IUnknown`, nezávisle na objekt vlastníka `IUnknown` (vlastníkem je objekt, pro kterou odtrhnout se vytváří). `CComCachedTearOffObject` udržuje svůj vlastní odkaz na počet jeho `IUnknown` a odstraní sama po jeho počet odkazů je nula. Ale pokud dotaz pro některý z jeho odtržených rozhraní, počet odkazů vlastníka objektu `IUnknown` se zvýší.

Pokud `CComCachedTearOffObject` implementace odtrhnout je již vytvořena instance a odtržených rozhraní se dotazují pro znovu stejný objektů `CComCachedTearOffObject` objekt již byl použit. Naopak, pokud je implementováno rozhraní s odnímatelnými nabídkami `CComTearOffObject` je znovu dotazován na prostřednictvím objektu vlastníka jiného `CComTearOffObject` bude vytvořena instance.

Třída vlastníka, musí implementovat `FinalRelease` a volání `Release` v mezipaměti `IUnknown` pro `CComCachedTearOffObject`, který bude snížení jeho počet odkazů. To způsobí, že `CComCachedTearOffObject`společnosti `FinalRelease` volat a odstraňovat odtrhnout.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CComObjectRootBase`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="addref"></a>  CComCachedTearOffObject::AddRef

Zvýší počet odkazů `CComCachedTearOffObject` objektu 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

##  <a name="ccomcachedtearoffobject"></a>  CComCachedTearOffObject::CComCachedTearOffObject

Konstruktor

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parametry

*PV*<br/>
[in] Ukazatel `IUnknown` z `CComCachedTearOffObject`.

### <a name="remarks"></a>Poznámky

Inicializuje `CComContainedObject` člen [m_contained](#m_contained).

##  <a name="dtor"></a>  Ccomcachedtearoffobject –:: ~ ccomcachedtearoffobject –

Destruktor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Poznámky

Uvolní všechny přidělené prostředky a volání [FinalRelease](#finalrelease).

##  <a name="finalconstruct"></a>  CComCachedTearOffObject::FinalConstruct

Volání `m_contained::FinalConstruct` vytvořit `m_contained`, `CComContainedObject` <  `contained`> objektu se používá pro přístup k rozhraní implementované vaší třídy odtržených.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

##  <a name="finalrelease"></a>  CComCachedTearOffObject::FinalRelease

Volání `m_contained::FinalRelease` uvolnit `m_contained`, `CComContainedObject` <  `contained`> objektu.

```
void FinalRelease();
```

##  <a name="m_contained"></a>  CComCachedTearOffObject::m_contained

A [ccomcontainedobject –](../../atl/reference/ccomcontainedobject-class.md) objekt odvozený od vaší třídy odtržených.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parametry

*obsažené*<br/>
[in] Vaše odtržených třída odvozena od `CComTearOffObjectBase` a rozhraní chcete, aby váš objekt odtržených pro podporu.

### <a name="remarks"></a>Poznámky

Metody `m_contained` dědí používané pro přístup k rozhraní odtržených ve své třídě odtržených prostřednictvím uložené v mezipaměti odtržených objektu `QueryInterface`, `FinalConstruct`, a `FinalRelease`.

##  <a name="queryinterface"></a>  CComCachedTearOffObject::QueryInterface

Načte ukazatel na požadované rozhraní.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parametry

*identifikátor IID*<br/>
[in] Identifikátor GUID se požadované rozhraní.

*ppvObject*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *iid*, nebo hodnota NULL, pokud se nenajde rozhraní.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Pokud je požadovaná rozhraní `IUnknown`, vrací ukazatel na `CComCachedTearOffObject`vaší vlastní `IUnknown` a zvýší počet odkazů. V opačném případě dotazuje na vaše používání třídy odtržených rozhraní [InternalQueryInterface](ccomobjectrootex-class.md#internalqueryinterface) metody zděděné z `CComObjectRootEx`.  

##  <a name="release"></a>  CComCachedTearOffObject::Release

Sníží počet reference o 1 a, pokud počet odkazů na hodnotu 0, odstraní `CComCachedTearOffObject` objektu.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Návratová hodnota

V sestaveních bez ladění vždy vrátí hodnotu 0. V sestavení ladění vrátí hodnotu, která může být užitečné pro diagnostiku a testování.

## <a name="see-also"></a>Viz také

[CComTearOffObject – třída](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx – třída](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
