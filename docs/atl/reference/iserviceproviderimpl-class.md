---
title: Třída iServiceProviderimpl
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: ef0ee4f77441cb8d19ea2d6dcada1fed9faf2782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329420"
---
# <a name="iserviceproviderimpl-class"></a>Třída iServiceProviderimpl

Tato třída poskytuje výchozí `IServiceProvider` implementaci rozhraní.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IServiceProviderImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[iServiceProviderImpl::QueryService](#queryservice)|Vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní zadanému rozhraní pro službu.|

## <a name="remarks"></a>Poznámky

Rozhraní `IServiceProvider` vyhledá službu určenou identifikátorem GUID a vrátí ukazatel rozhraní pro požadované rozhraní ve službě. Třída `IServiceProviderImpl` poskytuje výchozí implementaci tohoto rozhraní.

`IServiceProviderImpl`určuje jednu metodu: [QueryService](#queryservice), která vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní určenému rozhraní pro službu.

`IServiceProviderImpl`používá mapu služeb, počínaje [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) a konče [END_SERVICE_MAP](service-map-macros.md#end_service_map).

Mapa služby obsahuje dvě položky: [SERVICE_ENTRY](service-map-macros.md#service_entry), což označuje zadané id služby (SID) podporované objektem, a [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), které volá `QueryService` řetěz na jiný objekt.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

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

[Přehled třídy](../../atl/atl-class-overview.md)
