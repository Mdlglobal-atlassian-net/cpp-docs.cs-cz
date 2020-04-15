---
title: Makra mapy služeb
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: eb2fe41c79135a7ac2ced9bc3242b070170716b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325944"
---
# <a name="service-map-macros"></a>Makra mapy služeb

Tato makra definují mapy služeb a položky.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Označuje začátek mapy služby ATL.|
|[END_SERVICE_MAP](#end_service_map)|Označuje konec mapy služby ATL.|
|[SERVICE_ENTRY](#service_entry)|Označuje, že objekt podporuje konkrétní ID služby.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Instruuje [iServiceProviderImpl::QueryService,](#queryservice) aby zřetězení na zadaný objekt.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="begin_service_map"></a><a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Označuje začátek mapy služeb.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
[v] Určuje třídu obsahující mapu služeb.

### <a name="remarks"></a>Poznámky

Pomocí mapy služeb implementujte funkce poskytovatele služeb na objektu COM. Nejprve je nutné odvodit třídu z [iServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Existují dva typy položek:

- [SERVICE_ENTRY](#service_entry)   Označuje podporu pro zadané ID služby (SID).

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Instruuje [iServiceProviderImpl::QueryService](#queryservice) zřetězit na jiný, zadaný objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a>END_SERVICE_MAP

Označuje konec mapy služeb.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry"></a><a name="service_entry"></a>SERVICE_ENTRY

Označuje, že objekt podporuje id služby určené *identifikátorem SID*.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parametry

*SID*<br/>
ID služby.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Instruuje [iServiceProviderImpl::QueryService,](#queryservice) aby zřetězení k objektu určenému *punk*.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parametry

*Punk*<br/>
Ukazatel na **rozhraní IUnknown,** na které se má zřetězit.

### <a name="example"></a>Příklad

Viz příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a>iServiceProviderImpl::QueryService

Vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní zadanému rozhraní pro službu.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parametry

*guidService*<br/>
[v] Ukazatel na identifikátor služby (SID).

*riid řekl:*<br/>
[v] Identifikátor rozhraní, ke kterému má volající získat přístup.

*ppvObj*<br/>
[out] Nepřímý ukazatel na požadované rozhraní.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota HRESULT je jedna z následujících:

|Návratová hodnota|Význam|
|------------------|-------------|
|S_OK|Služba byla úspěšně vytvořena nebo načtena.|
|E_invalidarg|Jeden nebo více argumentů je neplatných.|
|E_OUTOFMEMORY|Paměť je nedostatečná k vytvoření služby.|
|E_UNEXPECTED|Došlo k neznámé chybě.|
|E_NOINTERFACE|Požadované rozhraní není součástí této služby nebo je služba neznámá.|

### <a name="remarks"></a>Poznámky

`QueryService`vrátí nepřímý ukazatel na požadované rozhraní v zadané službě. Volající je zodpovědný za uvolnění tohoto ukazatele, pokud již není vyžadováno.

Při volání `QueryService`předáte identifikátor služby *(guidService)* a identifikátor rozhraní (*riid*). *GuidService* určuje službu, ke které chcete získat přístup a *riid* identifikuje rozhraní, které je součástí služby. Na oplátku obdržíte nepřímý ukazatel na rozhraní.

Objekt, který implementuje rozhraní může také implementovat rozhraní, které jsou součástí jiných služeb. Zvažte použití těchto zdrojů:

- Některá z těchto rozhraní mohou být volitelné. Ne všechna rozhraní definovaná v popisu služby jsou nutně k dispozici při každé implementaci služby nebo na každém vráceném objektu.

- Na rozdíl `QueryInterface`od volání , předávání jiný identifikátor služby nemusí nutně znamenat, že je vrácena jiný objekt modelu COM (COM).

- Vrácený objekt může mít další rozhraní, které nejsou součástí definice služby.

Dvě různé služby, jako je například SID_SMyService a SID_SYourService, mohou určit použití stejného rozhraní, i když implementace rozhraní může mít mezi těmito dvěma službami nic společného. To funguje, protože `QueryService` volání (SID_SMyService, IID_IDispatch) může `QueryService` vrátit jiný objekt než (SID_SYourService, IID_IDispatch). Identita objektu se nepředpokládá, když zadáte jiný identifikátor služby.

## <a name="see-also"></a>Viz také

[Makra](../../atl/reference/atl-macros.md)
