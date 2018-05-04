---
title: Makra Map služeb | Microsoft Docs
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
ms.openlocfilehash: d2d2fa313c574951a8f8ba7c85d5b405707ec220
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="service-map-macros"></a>Makra Map služby
Tyto makra definovat map služeb a položky.  
  
|||  
|-|-|  
|[BEGIN_SERVICE_MAP](#begin_service_map)|Označuje začátek ATL mapy služeb.|  
|[END_SERVICE_MAP](#end_service_map)|Označuje konec ATL mapy služeb.|  
|[SERVICE_ENTRY](#service_entry)|Označuje, že objekt podporuje konkrétní službu ID.|  
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Dá pokyn [IServiceProviderImpl::QueryService](#queryservice) na řetězec pro zadaný objekt.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
   
##  <a name="begin_service_map"></a>  BEGIN_SERVICE_MAP  
 Označuje začátek mapy služeb.  
  
```
BEGIN_SERVICE_MAP(theClass)
```  
  
### <a name="parameters"></a>Parametry  
 `theClass`  
 [v] Určuje třídu obsahující mapy služeb.  
  
### <a name="remarks"></a>Poznámky  
 Implementace funkce služby poskytovatele na objektu modelu COM pomocí mapy služeb. Nejdřív musí být odvozeny třídě z [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md). Existují dva typy položek:  
  
- [SERVICE_ENTRY](#service_entry) udává podporu pro zadaný služby ID (SID).  
  
- [SERVICE_ENTRY_CHAIN](#service_entry_chain) nařizuje [IServiceProviderImpl::QueryService](#queryservice) na řetězec na jiný, zadaný objekt.  
  
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
 Označuje, že objekt podporuje id služby určeného *SID*.  
  
```
SERVICE_ENTRY( SID )
```  
  
### <a name="parameters"></a>Parametry  
 *IDENTIFIKÁTOR SID*  
 ID služby.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="service_entry_chain"></a>  SERVICE_ENTRY_CHAIN  
 Dá pokyn [IServiceProviderImpl::QueryService](#queryservice) ke tvoří řetěz k objektu určeného `punk`.  
  
```
SERVICE_ENTRY_CHAIN( punk )
```  
  
### <a name="parameters"></a>Parametry  
 `punk`  
 Ukazatel **IUnknown** rozhraní, ke kterému do řetězce.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [BEGIN_SERVICE_MAP](#begin_service_map).  
  
##  <a name="queryservice"></a>  IServiceProviderImpl::QueryService  
 Vytvoří nebo přistupovat ke službě zadaný a vrátí ukazatele rozhraní k zadanému rozhraní pro službu.  
  
```
STDMETHOD(QueryService)( 
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```  
  
### <a name="parameters"></a>Parametry  
 [V] `guidService`  
 Ukazatel na identifikátor služby (SID).  
  
 [V] `riid`  
 Identifikátor rozhraní, ke kterému má volající získat přístup.  
  
 [OUT] `ppvObj`  
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
 `QueryService` Vrátí nepřímý ukazatel požadované rozhraní v zadaná služba. Volající zodpovídá za vydání tento ukazatel, když se už nevyžaduje.  
  
 Při volání `QueryService`, předáte identifikátor služby ( `guidService`) a identifikátor rozhraní ( `riid`). `guidService` Určuje službu, na který má přístup, a `riid` identifikuje rozhraní, které je součástí služby. Naopak se zobrazí nepřímých ukazatel na rozhraní.  
  
 Objekt, který implementuje rozhraní může také implementovat rozhraní, které jsou součástí jiných služeb. Zvažte následující:  
  
-   Některé z těchto rozhraní, mohou být volitelné. Ne všechny rozhraní, které jsou definované v popisu služby nejsou nezbytně na každý implementace služby nebo na každý vráceného objektu.  
  
-   Na rozdíl od volání `QueryInterface`, předávání identifikátor jinou službu nemusí nezbytně znamenat, že se vrátí různé objekt modelu COM (Component Object).  
  
-   Vrácený objekt může mít další rozhraní, které nejsou součástí definice služby.  
  
 Dva různé služby, jako je například SID_SMyService a SID_SYourService, můžete obě určují použití stejné rozhraní, i když implementace rozhraní může mít nic společného mezi těmito dvěma službami. Toto funguje, protože volání `QueryService` (SID_SMyService, IID_IDispatch) může vrátit jiný objekt než `QueryService` (SID_SYourService, IID_IDispatch). Identity – objekt není předpokládá, že když zadáte identifikátor jinou službu.  
  
## <a name="see-also"></a>Viz také  
 [Makra](../../atl/reference/atl-macros.md)
