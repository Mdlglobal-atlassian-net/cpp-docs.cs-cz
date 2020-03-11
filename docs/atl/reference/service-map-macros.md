---
title: Service Map makra
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: ab130b2401dc9885f82fd5668a2d722a96dd289b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862511"
---
# <a name="service-map-macros"></a>Service Map makra

Tato makra definují mapy a položky služeb.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Označuje začátek mapy služby ATL.|
|[END_SERVICE_MAP](#end_service_map)|Označuje konec mapy služby ATL.|
|[SERVICE_ENTRY](#service_entry)|Indikuje, že objekt podporuje konkrétní ID služby.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Instruuje [IServiceProviderImpl:: QueryService](#queryservice) k zřetězení zadaného objektu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Označuje začátek mapy služby.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
pro Určuje třídu obsahující mapu služby.

### <a name="remarks"></a>Poznámky

K implementaci funkce poskytovatele služeb v objektu COM použijte mapu služby. Nejprve musíte třídu odvodit z [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Existují dva typy položek:

- [SERVICE_ENTRY](#service_entry)   Určuje podporu pro zadané ID služby (SID).

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Instruuje [IServiceProviderImpl:: QueryService](#queryservice) k zřetězení do jiného zadaného objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>END_SERVICE_MAP

Označuje konec mapy služby.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry"></a>SERVICE_ENTRY

Indikuje, že objekt podporuje ID služby určené *identifikátorem SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parametry

*ID*<br/>
ID služby

### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Instruuje [IServiceProviderImpl:: QueryService](#queryservice) a řetězení k objektu určenému parametrem *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parametry

*punk*<br/>
Ukazatel na rozhraní **IUnknown** , na které se má zřetězit.

### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="queryservice"></a>IServiceProviderImpl::QueryService

Vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní na určené rozhraní pro službu.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*guidService*<br/>
pro Ukazatel na identifikátor služby (SID).

*riid*<br/>
pro Identifikátor rozhraní, ke kterému má volající získat přístup.

*ppvObj*<br/>
mimo Nepřímý ukazatel na požadované rozhraní

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota HRESULT je jedna z následujících:

|Návratová hodnota|Význam|
|------------------|-------------|
|S_OK|Služba byla úspěšně vytvořena nebo načtena.|
|E_INVALIDARG|Jeden nebo více argumentů je neplatných.|
|E_OUTOFMEMORY|Paměť nemá dostatek místa k vytvoření služby.|
|E_UNEXPECTED|Došlo k neznámé chybě.|
|E_NOINTERFACE|Požadované rozhraní není součástí této služby, nebo je služba neznámá.|

### <a name="remarks"></a>Poznámky

`QueryService` vrátí nepřímý ukazatel na požadované rozhraní v zadané službě. Volající je zodpovědný za uvolnění tohoto ukazatele, pokud již není požadován.

Při volání `QueryService`předáte jak identifikátor služby (*guidService*), tak identifikátor rozhraní (*riid*). *GuidService* Určuje službu, ke které chcete získat přístup, a *riid* identifikuje rozhraní, které je součástí služby. V rámci návratu obdržíte nepřímý ukazatel na rozhraní.

Objekt, který implementuje rozhraní, může také implementovat rozhraní, která jsou součástí jiných služeb. Zvažte použití těchto zdrojů:

- Některá z těchto rozhraní můžou být volitelná. Ne všechna rozhraní definovaná v popisu služby jsou nutně přítomna při každé implementaci služby nebo u všech vrácených objektů.

- Na rozdíl od volání `QueryInterface`, předání jiného identifikátoru služby nemusí nutně znamenat, že je vrácen jiný objekt modelu COM (Component Object Model).

- Vrácený objekt může mít další rozhraní, která nejsou součástí definice služby.

Dvě různé služby, například SID_SMyService a SID_SYourService, mohou určovat použití stejného rozhraní, i když implementace rozhraní nemusí mít mezi těmito dvěma službami společný nic. To funguje, protože volání `QueryService` (SID_SMyService, IID_IDispatch) může vracet jiný objekt než `QueryService` (SID_SYourService, IID_IDispatch). Identita objektu se nepředpokládá, když zadáte jiný identifikátor služby.

## <a name="see-also"></a>Viz také

[Makr](../../atl/reference/atl-macros.md)
