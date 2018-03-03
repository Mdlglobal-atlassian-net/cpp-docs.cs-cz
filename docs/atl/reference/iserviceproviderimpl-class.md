---
title: "Třída IServiceProviderImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4946a88e6bf6767de0e3965670f94b91d1ddaf90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl – třída
Tato třída poskytuje výchozí implementaci třídy `IServiceProvider` rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T>  
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IServiceProviderImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](#queryservice)|Vytvoří nebo přistupovat ke službě zadaný a vrátí ukazatele rozhraní k zadanému rozhraní pro službu.|  
  
## <a name="remarks"></a>Poznámky  
 `IServiceProvider` Rozhraní vyhledá službu určeného její identifikátor GUID a vrátí ukazatel rozhraní pro požadované rozhraní služby. Třída `IServiceProviderImpl` poskytuje výchozí implementaci tohoto rozhraní.  
  
 **IServiceProviderImpl** Určuje jednu metodu: [služby QueryService](#queryservice), který vytvoří nebo přistupovat ke službě zadaný a vrátí ukazatele rozhraní k zadanému rozhraní pro službu.  
  
 `IServiceProviderImpl`používá mapy služeb, počínaje [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) a konče [END_SERVICE_MAP](service-map-macros.md#end_service_map).  
  
 Mapy služeb obsahuje dvě položky: [SERVICE_ENTRY](service-map-macros.md#service_entry), což naznačuje id zadané služby (SID) nepodporuje objekt, a [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), který volá `QueryService` do řetězce do jiného objekt.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="queryservice"></a>IServiceProviderImpl::QueryService  
 Vytvoří nebo přistupovat ke službě zadaný a vrátí ukazatele rozhraní k zadanému rozhraní pro službu.  
  
```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 [V]`guidService`  
 Ukazatel na identifikátor služby (SID).  
  
 [V]`riid`  
 Identifikátor rozhraní, ke kterému má volající získat přístup.  
  
 [OUT]`ppvObj`  
 Nepřímý ukazatel na požadované rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácený `HRESULT` hodnota je jeden z následujících:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|S_OK|Služba byla úspěšně vytvořit nebo načíst.|  
|E_INVALIDARG|Jeden nebo více parametrů je neplatný.|  
|E_OUTOFMEMORY|Velikost paměti je nedostatečná pro vytvoření služby.|  
|E_UNEXPECTED|Došlo k neznámé chybě.|  
|E_NOINTERFACE|Požadované rozhraní není součástí této služby nebo služby neznámý.|  
  
### <a name="remarks"></a>Poznámky  
 `QueryService`Vrátí nepřímý ukazatel požadované rozhraní v zadaná služba. Volající zodpovídá za vydání tento ukazatel, když se už nevyžaduje.  
  
 Při volání `QueryService`, předáte identifikátor služby ( `guidService`) a identifikátor rozhraní ( `riid`). `guidService` Určuje službu, na který má přístup, a `riid` identifikuje rozhraní, které je součástí služby. Naopak se zobrazí nepřímých ukazatel na rozhraní.  
  
 Objekt, který implementuje rozhraní může také implementovat rozhraní, které jsou součástí jiných služeb. Zvažte následující:  
  
-   Některé z těchto rozhraní, mohou být volitelné. Ne všechny rozhraní, které jsou definované v popisu služby nejsou nezbytně na každý implementace služby nebo na každý vráceného objektu.  
  
-   Na rozdíl od volání `QueryInterface`, předávání identifikátor jinou službu nemusí nezbytně znamenat, že se vrátí různé objekt modelu COM (Component Object).  
  
-   Vrácený objekt může mít další rozhraní, které nejsou součástí definice služby.  
  
 Dva různé služby, jako je například SID_SMyService a SID_SYourService, můžete obě určují použití stejné rozhraní, i když implementace rozhraní může mít nic společného mezi těmito dvěma službami. Toto funguje, protože volání `QueryService` (SID_SMyService, IID_IDispatch) může vrátit jiný objekt než `QueryService` (SID_SYourService, IID_IDispatch). Identity – objekt není předpokládá, že když zadáte identifikátor jinou službu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
