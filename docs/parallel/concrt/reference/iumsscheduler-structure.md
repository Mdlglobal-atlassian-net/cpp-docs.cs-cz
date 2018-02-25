---
title: "Struktura rozhraní IUMSScheduler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
dev_langs:
- C++
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da35fe5ae8d00ee537674fd689fd7f27074b0355
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="iumsscheduler-structure"></a>Struktura rozhraní IUMSScheduler
Rozhraní pro abstrakci plánovače pracovní, který chce Concurrency Runtime Resource Manager k ruční ho, které lze plánovat vláken (UMS) uživatelského režimu. Resource Manager používá toto rozhraní ke komunikaci s plánovače UMS přístup z více vláken. `IUMSScheduler` Rozhraní dědí z `IScheduler` rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IUMSScheduler : public IScheduler;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Přiřadí `IUMSCompletionList` rozhraní pro přístup z více vláken plánovače UMS.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud implementujete vlastní plánovače, který komunikuje s Resource Managerem a chcete UMS vláken možné předat do vašeho scheduleru místo obyčejnou Win32 vláken, by měl poskytovat implementace `IUMSScheduler` rozhraní. Kromě toho by měl nastavit zásady hodnotu pro klíč zásad plánovače `SchedulerKind` být `UmsThreadDefault`. Pokud tato zásada určuje UMS přístup z více vláken, `IScheduler` rozhraní, které se předá jako parametr, který se [iresourcemanager::registerscheduler –](iresourcemanager-structure.md#registerscheduler) musí být nastavena metoda `IUMSScheduler` rozhraní.  
  
 Správce prostředků je možné k ruční můžete UMS vláken pouze v operačních systémech, které mají funkci UMS. 64bitová verze operačních systémů s verzí systému Windows 7 a vyšší podporuje UMS vláken. Pokud vytvoříte zásad plánovače s `SchedulerKind` klíč nastaven na hodnotu `UmsThreadDefault` a základní platforma nepodporuje UMS, hodnota `SchedulerKind` klíč v této zásadě se změní na hodnotu `ThreadScheduler`. Vždy přečtěte zpět tuto hodnotu zásad před očekává příjem UMS vláken.  
  
 `IUMSScheduler` Rozhraní je jeden element end kanálu obousměrné komunikace mezi plánovače a Resource Manager. Druhém konci je reprezentována `IResourceManager` a `ISchedulerProxy` rozhraní, která jsou implementovaná pomocí Správce prostředků.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Rozhraní IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="setcompletionlist"></a>  Iumsscheduler::setcompletionlist – metoda  
 Přiřadí `IUMSCompletionList` rozhraní pro přístup z více vláken plánovače UMS.  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pCompletionList`  
 Rozhraní seznamu dokončení pro Plánovač. Neexistuje jeden seznam za plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Správce prostředků bude volat tuto metodu pro Plánovač, která určuje, že chce UMS vláken, po Plánovač požádal počáteční přidělení prostředků. Můžete použít Plánovač `IUMSCompletionList` rozhraní k určení, kdy mají odblokováno UMS vlákno proxy. Je platný pouze pro přístup k toto rozhraní z vlákna proxy systémem virtuálních procesorů kořenové přiřazené plánovače UMS.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [Struktura rozhraní IScheduler](ischeduler-structure.md)   
 [Iumscompletionlist – struktura](iumscompletionlist-structure.md)   
 [IResourceManager – struktura](iresourcemanager-structure.md)
