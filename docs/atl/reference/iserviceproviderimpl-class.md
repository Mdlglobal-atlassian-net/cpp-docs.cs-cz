---
title: Iserviceproviderimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
dev_langs:
- C++
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d14d00e57cbbb04c77f0b84c584ebb1c4f4260e5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703199"
---
# <a name="iserviceproviderimpl-class"></a>Iserviceproviderimpl – třída

Tato třída poskytuje výchozí implementaci třídy `IServiceProvider` rozhraní.

## <a name="syntax"></a>Syntaxe

```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Parametry

*T*  
Vaše třída odvozena od `IServiceProviderImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|Vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní k zadanému rozhraní pro službu.|

## <a name="remarks"></a>Poznámky

`IServiceProvider` Rozhraní vyhledá službu určené její identifikátor GUID a vrátí ukazatel rozhraní pro požadované rozhraní ve službě. Třída `IServiceProviderImpl` poskytuje výchozí implementaci tohoto rozhraní.

`IServiceProviderImpl` Určuje jednu metodu: [služby QueryService](#queryservice), který vytvoří nebo přistupuje k zadané službě a vrátí ukazatel rozhraní k zadanému rozhraní pro službu.

`IServiceProviderImpl` využívá mapu služeb, počínaje [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) a konče [END_SERVICE_MAP](service-map-macros.md#end_service_map).

Mapy služeb obsahuje dvě položky: [SERVICE_ENTRY](service-map-macros.md#service_entry), což znamená id zadané služby (SID) podporována objektem, a [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), který volá `QueryService` řetězce do jiného objekt.

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

Objekt, který implementuje rozhraní může také implementovat rozhraní, které jsou součástí jiné služby. Vezměte v úvahu následující:

- Některé z těchto rozhraní může být volitelný. Ne všechna rozhraní, které jsou definované v popisu služby nejsou nutně na každou implementaci služby nebo na každý vráceného objektu.

- Na rozdíl od volání `QueryInterface`, předávání identifikátor různé služby nemusí nutně znamenat, že se vrátí jiný objekt modelu COM (Component Object).

- Vrácený objekt může mít další rozhraní, které nejsou součástí definice služby.

Dvě různé služby, jako je například SID_SMyService a SID_SYourService, můžete i určit používá stejné rozhraní, i když implementaci rozhraní může mít nic společného mezi těmito dvěma službami. Tento postup funguje, protože volání `QueryService` (SID_SMyService, IID_IDispatch) může vrátit do jiného objektu než `QueryService` (SID_SYourService, IID_IDispatch). Identita objektu není předpokládá, že pokud zadáte identifikátor jinou službu.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
