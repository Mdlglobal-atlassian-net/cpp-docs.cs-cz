---
title: Makra Map služeb | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
dev_langs:
- C++
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc7b0ca9388de82d49927a7fe76694212b94246b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053710"
---
# <a name="service-map-macros"></a>Makra Map služeb

Tato makra definují map služeb a položky.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Označuje začátek ATL služby mapy.|
|[END_SERVICE_MAP](#end_service_map)|Označuje konec mapování ATL služby.|
|[SERVICE_ENTRY](#service_entry)|Označuje, že objekt podporuje ID konkrétní služby.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Dává pokyn [IServiceProviderImpl::QueryService](#queryservice) ke sledu k zadanému objektu.|  

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP

Označuje začátek toho mapy služeb.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[in] Určuje třídu obsahující mapy služeb.

### <a name="remarks"></a>Poznámky

Implementace funkce poskytovatele služby na váš objekt modelu COM pomocí mapy služeb. Nejprve musíte odvodit třídu z [iserviceproviderimpl –](../../atl/reference/iserviceproviderimpl-class.md). Existují dva typy položek:

- [SERVICE_ENTRY](#service_entry) udává podporu pro zadaný Identifikátor (SID) služby.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain) nařizuje [IServiceProviderImpl::QueryService](#queryservice) řetězce do jiného, zadaný objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>  END_SERVICE_MAP

Označuje konec mapy služeb.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry"></a>  SERVICE_ENTRY

Označuje, že objekt podporuje id služby určené *SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parametry

*IDENTIFIKÁTOR SID*<br/>
ID služby.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN

Dává pokyn [IServiceProviderImpl::QueryService](#queryservice) ke sledu k objektu určeného parametrem *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parametry

*punk*<br/>
Ukazatel **IUnknown** rozhraní, ke kterému do řetězce.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService

Vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní k zadanému rozhraní pro službu.

```
STDMETHOD(QueryService)( 
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*guidService*<br/>
[in] Ukazatel na identifikátor služby (SID).

*riid*<br/>
[in] Identifikátor rozhraní, ke kterému volající získat přístup.

*ppvObj*<br/>
[out] Nepřímé ukazatel na požadované rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota HRESULT je jedním z následujících akcí:

|Návratová hodnota|Význam|
|------------------|-------------|
|S_OK|Služby byl úspěšně vytvořen nebo načten.|
|E_INVALIDARG|Jeden nebo více argumentů je neplatný.|
|E_OUTOFMEMORY|Paměti není dostatečná k vytvoření služby.|
|E_UNEXPECTED, JE-|Došlo k neznámé chybě.|
|E_NOINTERFACE|Požadované rozhraní není součástí této služby nebo služby neznámý.|

### <a name="remarks"></a>Poznámky

`QueryService` Vrátí nepřímým ukazatel na požadované rozhraní v zadaná služba. Volající zodpovídá za uvolňuje tento ukazatel, když se už nevyžaduje.

Při volání `QueryService`, předáte identifikátor služby (*guidService*) a identifikátor rozhraní (*riid*). *GuidService* určuje služby, ke kterému chcete získat přístup, a *riid* identifikuje rozhraní, která je součástí služby. Na oplátku obdržíte nepřímé ukazatel na rozhraní.

Objekt, který implementuje rozhraní může také implementovat rozhraní, které jsou součástí jiné služby. Vezměte v úvahu následující:

- Některé z těchto rozhraní může být volitelný. Ne všechna rozhraní, které jsou definované v popisu služby nejsou nutně na každou implementaci služby nebo na každý vráceného objektu.

- Na rozdíl od volání `QueryInterface`, předávání identifikátor různé služby nemusí nutně znamenat, že se vrátí jiný objekt modelu COM (Component Object).

- Vrácený objekt může mít další rozhraní, které nejsou součástí definice služby.

Dvě různé služby, jako je například SID_SMyService a SID_SYourService, můžete i určit používá stejné rozhraní, i když implementaci rozhraní může mít nic společného mezi těmito dvěma službami. Tento postup funguje, protože volání `QueryService` (SID_SMyService, IID_IDispatch) může vrátit do jiného objektu než `QueryService` (SID_SYourService, IID_IDispatch). Identita objektu není předpokládá, že pokud zadáte identifikátor jinou službu.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
