---
title: "Iresourcemanager – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d309e057a8f829b11cc97ad60f3f5d56ff7ecaff
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="iresourcemanager-structure"></a>IResourceManager – struktura
Rozhraní pro správce prostředků Concurrency Runtime. Toto je rozhraní, pomocí kterého plánovače komunikovat se správcem prostředků.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-enumerations"></a>Veřejné výčty  
  
|Název|Popis|  
|----------|-----------------|  
|[IResourceManager::OSVersion](#osversion)|Výčtový typ, který představuje verzi operačního systému.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Iresourcemanager::createnodetopology –](#createnodetopology)|Nachází pouze v ladění sestavení modulu runtime, tato metoda je test háku, navrženy k usnadnění testování služby Správce prostředků v různých topologiích hardwaru, bez nutnosti skutečné hardwarové odpovídající konfiguraci. Prodejní sestavení modulu runtime tato metoda vrátí bez provedení všech akcí.|  
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|Vrátí počet uzlů, které jsou k dispozici pro správce prostředků.|  
|[Iresourcemanager::getfirstnode –](#getfirstnode)|Vrátí první uzel v pořadí výčtu definovaným pomocí Správce prostředků.|  
|[Iresourcemanager::Reference –](#reference)|Zvýší počet odkazů na instanci Resource Manager.|  
|[IResourceManager::RegisterScheduler](#registerscheduler)|Zaregistruje plánovače s Resource Managerem. Po registraci Plánovač měli komunikovat s pomocí Správce prostředků `ISchedulerProxy` rozhraní, která je vrácena.|  
|[Iresourcemanager::Release –](#release)|Snižuje počet odkaz na instanci Resource Manager. Resource Manager zničen při jeho počet odkazů přejde na `0`.|  
  
## <a name="remarks"></a>Poznámky  
 Použití [createresourcemanager –](concurrency-namespace-functions.md) funkce získat rozhraní pro správce prostředků instanci typu singleton. Metoda zvýší počet odkazů v Resource Manageru a by měla vyvolat [iresourcemanager::Release –](#release) metodu pro uvolnění odkaz, když jste hotovi s Resource Managerem. Každý plánovače, kterou vytvoříte obvykle bude volat tuto metodu během vytváření a uvolněte odkaz na správci prostředků vypnut.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IResourceManager`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="createnodetopology"></a>  Iresourcemanager::createnodetopology – metoda  
 Nachází pouze v ladění sestavení modulu runtime, tato metoda je test háku, navrženy k usnadnění testování služby Správce prostředků v různých topologiích hardwaru, bez nutnosti skutečné hardwarové odpovídající konfiguraci. Prodejní sestavení modulu runtime tato metoda vrátí bez provedení všech akcí.  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `nodeCount`  
 Počet právě simulated uzlů procesoru.  
  
 `pCoreCount`  
 Pole, která určuje počet jader na každém uzlu.  
  
 `pNodeDistance`  
 Matice zadání uzlu vzdálenost mezi dvěma uzly. Tento parametr může mít hodnotu `NULL`.  
  
 `pProcessorGroups`  
 Pole, které určuje skupinu procesorů každý uzel patří do.  
  
### <a name="remarks"></a>Poznámky  
 [invalid_argument](../../../standard-library/invalid-argument-class.md) je vyvolána, pokud parametr `nodeCount` má hodnotu `0` byl předán v, nebo pokud parametr `pCoreCount` má hodnotu `NULL`.  
  
 [invalid_operation](invalid-operation-class.md) je vyvolána, pokud tato metoda je volána, když existují další plánovače v procesu.  
  
##  <a name="getavailablenodecount"></a>  Iresourcemanager::getavailablenodecount – metoda  
 Vrátí počet uzlů, které jsou k dispozici pro správce prostředků.  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet uzlů, které jsou k dispozici pro správce prostředků.  
  
##  <a name="getfirstnode"></a>  Iresourcemanager::getfirstnode – metoda  
 Vrátí první uzel v pořadí výčtu definovaným pomocí Správce prostředků.  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 První uzel v pořadí výčtu definovaným pomocí Správce prostředků.  
  
##  <a name="iresourcemanager__osversion"></a>  IResourceManager::OSVersion – výčet  
 Výčtový typ, který představuje verzi operačního systému.  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>  Iresourcemanager::Reference – metoda  
 Zvýší počet odkazů na instanci Resource Manager.  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledný počet odkazů.  
  
##  <a name="registerscheduler"></a>  Iresourcemanager::registerscheduler – metoda  
 Zaregistruje plánovače s Resource Managerem. Po registraci Plánovač měli komunikovat s pomocí Správce prostředků `ISchedulerProxy` rozhraní, která je vrácena.  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pScheduler`  
 `IScheduler` Rozhraní plánovačem k registraci.  
  
 `version`  
 Verze rozhraní komunikace Plánovač používá ke komunikaci s Resource Managerem. Používáte verzi umožňuje Resource Manager vyvíjí rozhraní komunikace současně získat přístup do starší funkce plánovače. Plánovače, které chcete používat funkce služby Správce prostředků v sadě Visual Studio 2010 měli použít verzi `CONCRT_RM_VERSION_1`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `ISchedulerProxy` Rozhraní Resource Manager je spojen s vašeho scheduleru. Vašeho scheduleru použít ke komunikaci s Resource Managerem z tohoto bodu na toto rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k zahájení komunikace s Resource Managerem. Metoda přidruží `IScheduler` rozhraní pro vašeho scheduleru se `ISchedulerProxy` rozhraní a rukou zpátky na vás. Požadavky na spuštění prostředky pro použití vašeho scheduleru nebo přihlášení k odběru vláken s Resource Managerem, můžete použít rozhraní vrácená. Resource Manager použije elementů zásad ze zásad plánovače vrácený [ischeduler::getpolicy –](ischeduler-structure.md#getpolicy) metoda určit, jaké typy vláken Plánovač bude nutné spustit pracovní. Pokud vaše `SchedulerKind` zásad klíč má hodnotu `UmsThreadDefault` a hodnota je pro čtení zpět z zásady jako hodnota `UmsThreadDefault`, `IScheduler` rozhraní předaný metodě musí být `IUMSScheduler` rozhraní.  
  
 Vyvolá metoda `invalid_argument` výjimka Pokud parametr `pScheduler` má hodnotu `NULL` nebo pokud parametr `version` není platnou verzi pro rozhraní komunikace.  
  
##  <a name="release"></a>  Iresourcemanager::Release – metoda  
 Snižuje počet odkaz na instanci Resource Manager. Resource Manager zničen při jeho počet odkazů přejde na `0`.  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledný počet odkazů.  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [ISchedulerProxy Structure](ischedulerproxy-structure.md)   
 [IScheduler – struktura](ischeduler-structure.md)
