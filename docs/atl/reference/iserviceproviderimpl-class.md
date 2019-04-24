---
title: IServiceProviderImpl Class
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: e52c28d528e187713d2d0925fed23bd8cd4493d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276000"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl Class

Tato třída poskytuje výchozí implementaci třídy `IServiceProvider` rozhraní.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IServiceProviderImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|Vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní k zadanému rozhraní pro službu.|

## <a name="remarks"></a>Poznámky

`IServiceProvider` Rozhraní vyhledá službu určené její identifikátor GUID a vrátí ukazatel rozhraní pro požadované rozhraní ve službě. Třída `IServiceProviderImpl` poskytuje výchozí implementaci tohoto rozhraní.

`IServiceProviderImpl` Určuje jednu metodu: [Služby QueryService](#queryservice), který vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní k zadanému rozhraní pro službu.

`IServiceProviderImpl` využívá mapu služeb, počínaje [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) a konče [END_SERVICE_MAP](service-map-macros.md#end_service_map).

Mapy služeb obsahuje dvě položky: [SERVICE_ENTRY](service-map-macros.md#service_entry), což znamená id zadané služby (SID) podporována objektem, a [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), který volá `QueryService` řetězce do jiného objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

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

Objekt, který implementuje rozhraní může také implementovat rozhraní, které jsou součástí jiné služby. Zvažte použití těchto zdrojů:

- Některé z těchto rozhraní může být volitelný. Ne všechna rozhraní, které jsou definované v popisu služby nejsou nutně na každou implementaci služby nebo na každý vráceného objektu.

- Na rozdíl od volání `QueryInterface`, předávání identifikátor různé služby nemusí nutně znamenat, že se vrátí jiný objekt modelu COM (Component Object).

- Vrácený objekt může mít další rozhraní, které nejsou součástí definice služby.

Dvě různé služby, jako je například SID_SMyService a SID_SYourService, můžete i určit používá stejné rozhraní, i když implementaci rozhraní může mít nic společného mezi těmito dvěma službami. Tento postup funguje, protože volání `QueryService` (SID_SMyService, IID_IDispatch) může vrátit do jiného objektu než `QueryService` (SID_SYourService, IID_IDispatch). Identita objektu není předpokládá, že pokud zadáte identifikátor jinou službu.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
