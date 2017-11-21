---
title: "Struktura rozhraní IScheduler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IScheduler
- CONCRTRM/concurrency::IScheduler
- CONCRTRM/concurrency::IScheduler::IScheduler::AddVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::GetId
- CONCRTRM/concurrency::IScheduler::IScheduler::GetPolicy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyBusy
- CONCRTRM/concurrency::IScheduler::IScheduler::NotifyResourcesExternallyIdle
- CONCRTRM/concurrency::IScheduler::IScheduler::RemoveVirtualProcessors
- CONCRTRM/concurrency::IScheduler::IScheduler::Statistics
dev_langs: C++
helpviewer_keywords: IScheduler structure
ms.assetid: 471de85a-2b1a-4b6d-ab81-2eff2737161e
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e38029e13bc342895922f4f3624076ab513f7a45
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ischeduler-structure"></a>Struktura rozhraní IScheduler
Rozhraní pro abstrakci pracovní plánovače. Concurrency Runtime Resource Manager používá ke komunikaci s pracovní plánovače toto rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```
struct IScheduler;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ischeduler::addvirtualprocessors –](#addvirtualprocessors)|Poskytuje plánovače sadu kořeny virtuálních procesorů pro jeho použití. Každý `IVirtualProcessorRoot` rozhraní představuje práva k provedení jednoho vlákno, které můžete provádět práci jménem plánovače.|  
|[Ischeduler::getid –](#getid)|Vrací jedinečný identifikátor pro Plánovač.|  
|[Ischeduler::getpolicy –](#getpolicy)|Vrátí kopii zásad plánovače. Další informace o zásady plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).|  
|[Ischeduler::notifyresourcesexternallybusy –](#notifyresourcesexternallybusy)|Upozorní tento plánovač, která vláken hardwaru reprezentována sadu kořenových virtuálních procesorů v poli `ppVirtualProcessorRoots` jsou nyní používány jiné plánovače.|  
|[Ischeduler::notifyresourcesexternallyidle –](#notifyresourcesexternallyidle)|Upozorní tento plánovač, která vláken hardwaru reprezentována sadu kořenových virtuálních procesorů v poli `ppVirtualProcessorRoots` nejsou používány jiné plánovače.|  
|[Ischeduler::removevirtualprocessors –](#removevirtualprocessors)|Inicializuje odstranění kořeny virtuálních procesorů, které byly dříve přiděleny na tento plánovače.|  
|[Ischeduler::Statistics –](#statistics)|Obsahuje informace související s příchodem a dokončení sazby úlohy a změna v délka fronty pro plánovače.|  
  
## <a name="remarks"></a>Poznámky  
 Při implementaci vlastní plánovače, který komunikuje s Resource Managerem, měli byste jim poskytnout implementaci `IScheduler` rozhraní. Toto rozhraní je jeden atribut end objektu kanál obousměrné komunikace mezi plánovače a Resource Manager. Druhém konci je reprezentována `IResourceManager` a `ISchedulerProxy` rozhraní, která jsou implementovaná pomocí Správce prostředků.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IScheduler`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="addvirtualprocessors"></a>Ischeduler::addvirtualprocessors – metoda  
 Poskytuje plánovače sadu kořeny virtuálních procesorů pro jeho použití. Každý `IVirtualProcessorRoot` rozhraní představuje práva k provedení jednoho vlákno, které můžete provádět práci jménem plánovače.  
  
```
virtual void AddVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Pole `IVirtualProcessorRoot` rozhraní představující virtuálních procesorů kořeny, který se přidává do plánovače.  
  
 `count`  
 Počet `IVirtualProcessorRoot` rozhraní v poli.  
  
### <a name="remarks"></a>Poznámky  
 Volá správce prostředků `AddVirtualProcessor` metoda udělte počáteční sadu virtuálních procesorů kořeny plánovače. Také se může vyvolat metodu se při jej znovu vytvoří rovnováhu mezi plánovače prostředky přidat do plánovače kořeny virtuálních procesorů.  
  
##  <a name="getid"></a>Ischeduler::getid – metoda  
 Vrací jedinečný identifikátor pro Plánovač.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celé číslo jedinečný identifikátor.  
  
### <a name="remarks"></a>Poznámky  
 Měli byste použít [getschedulerid –](concurrency-namespace-functions.md) funkce získat jedinečný identifikátor pro objekt, který implementuje `IScheduler` rozhraní, před použitím rozhraní jako parametr pro metody zadaný správcem prostředků. Předpokládá se, že se vrátíte stejný identifikátor při `GetId` je volána funkce.  
  
 Identifikátor získat z jiného zdroje může vést k nedefinované chování.  
  
##  <a name="getpolicy"></a>Ischeduler::getpolicy – metoda  
 Vrátí kopii zásad plánovače. Další informace o zásady plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).  
  
```
virtual SchedulerPolicy GetPolicy() const = 0;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie zásad plánovače.  
  
##  <a name="notifyresourcesexternallybusy"></a>Ischeduler::notifyresourcesexternallybusy – metoda  
 Upozorní tento plánovač, která vláken hardwaru reprezentována sadu kořenových virtuálních procesorů v poli `ppVirtualProcessorRoots` jsou nyní používány jiné plánovače.  
  
```
virtual void NotifyResourcesExternallyBusy(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Pole `IVirtualProcessorRoot` rozhraní přidružené k hardwaru vláken, na které se staly další plánovače zaneprázdněný.  
  
 `count`  
 Počet `IVirtualProcessorRoot` rozhraní v poli.  
  
### <a name="remarks"></a>Poznámky  
 Je možné pro konkrétní hardware vlákno přiřazen více plánovače ve stejnou dobu. Jedním z důvodů může být, že nejsou k dispozici dostatek hardwaru vláken v systému, aby pokryl minimální souběžnosti pro všechny plánovače bez sdílení prostředků. Další možností je, že prostředky jsou dočasně přiřazené k jiné plánovače při vlastnícím Plánovač, není použití mimo všechny jeho kořeny virtuálních procesorů v daném vláknu hardwaru právě deaktivována.  
  
 Úroveň předplatného vlákno hardwaru je označený jako počet vláken, odebírané a aktivovány virtuálních procesorů kořeny přidružené daném vláknu hardwaru. Z konkrétní scheduler externí předplatné úroveň vlákno hardwaru je část předplatného jiných plánovače podílet se na. Plánovače se posílají oznámení, aby byly prostředky externě zaneprázdněný, pokud úrovni externí předplatného vlákna hardwaru přesune od nuly do kladné území.  
  
 Oznámení prostřednictvím této metody se odesílají pouze do plánovače, které mají zásady kde hodnota `MinConcurrency` zásad klíč je stejná jako hodnota pro `MaxConcurrency` klíč zásad. Další informace o zásady plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).  
  
 Scheduler, která kvalifikují pro oznámení získá sadu počáteční oznámení při vytvoření, oznamující, zda jsou prostředky, které právě byl přiřazen externě zaneprázdněn nebo nečinné.  
  
##  <a name="notifyresourcesexternallyidle"></a>Ischeduler::notifyresourcesexternallyidle – metoda  
 Upozorní tento plánovač, která vláken hardwaru reprezentována sadu kořenových virtuálních procesorů v poli `ppVirtualProcessorRoots` nejsou používány jiné plánovače.  
  
```
virtual void NotifyResourcesExternallyIdle(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Pole `IVirtualProcessorRoot` rozhraní přidružené k hardwaru vláken, na které se staly další plánovače nečinnosti.  
  
 `count`  
 Počet `IVirtualProcessorRoot` rozhraní v poli.  
  
### <a name="remarks"></a>Poznámky  
 Je možné pro konkrétní hardware vlákno přiřazen více plánovače ve stejnou dobu. Jedním z důvodů může být, že nejsou k dispozici dostatek hardwaru vláken v systému, aby pokryl minimální souběžnosti pro všechny plánovače bez sdílení prostředků. Další možností je, že prostředky jsou dočasně přiřazené k jiné plánovače při vlastnícím Plánovač, není použití mimo všechny jeho kořeny virtuálních procesorů v daném vláknu hardwaru právě deaktivována.  
  
 Úroveň předplatného vlákno hardwaru je označený jako počet vláken, odebírané a aktivovány virtuálních procesorů kořeny přidružené daném vláknu hardwaru. Z konkrétní scheduler externí předplatné úroveň vlákno hardwaru je část předplatného jiných plánovače podílet se na. Plánovače se posílají oznámení, aby byly prostředky externě zaneprázdněný, když úroveň externí předplatné vlákna hardwaru klesne na nulu z předchozí kladnou hodnotu.  
  
 Oznámení prostřednictvím této metody se odesílají pouze do plánovače, které mají zásady kde hodnota `MinConcurrency` zásad klíč je stejná jako hodnota pro `MaxConcurrency` klíč zásad. Další informace o zásady plánovače najdete v tématu [SchedulerPolicy](schedulerpolicy-class.md).  
  
 Scheduler, která kvalifikují pro oznámení získá sadu počáteční oznámení při vytvoření, oznamující, zda jsou prostředky, které právě byl přiřazen externě zaneprázdněn nebo nečinné.  
  
##  <a name="removevirtualprocessors"></a>Ischeduler::removevirtualprocessors – metoda  
 Inicializuje odstranění kořeny virtuálních procesorů, které byly dříve přiděleny na tento plánovače.  
  
```
virtual void RemoveVirtualProcessors(
    _In_reads_(count) IVirtualProcessorRoot** ppVirtualProcessorRoots,
    unsigned int count) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `ppVirtualProcessorRoots`  
 Pole `IVirtualProcessorRoot` rozhraní představující procesor virtuálního adresáře, které chcete odebrat.  
  
 `count`  
 Počet `IVirtualProcessorRoot` rozhraní v poli.  
  
### <a name="remarks"></a>Poznámky  
 Volá správce prostředků `RemoveVirtualProcessors` metodu trvat zpět sadu virtuálních procesorů kořeny plánovače. Očekává se Plánovač má být vyvolán [odebrat](iexecutionresource-structure.md#remove) metoda na každém rozhraní, pokud se provádí s kořeny virtuálních procesorů. Nepoužívejte `IVirtualProcessorRoot` rozhraní, když je volána `Remove` metoda na něm.  
  
 Parametr `ppVirtualProcessorRoots` odkazuje na pole rozhraní. Mezi sadu kořenových virtuálních procesorů odeberou kořeny nikdy aktivoval mohou být vráceny okamžitě pomocí `Remove` metoda. Kořeny, které aktivoval a jsou buď provádění práce, nebo bylo deaktivováno a čekají na příchod, má být vrácen asynchronně. Plánovač musíte nastavit každý pokus o odebrání co nejrychleji kořenu virtuálních procesorů. Zpozdit odebrání kořenových virtuálních procesorů může vést k neúmyslnému Překryvný odběr v rámci plánovače.  
  
##  <a name="statistics"></a>Ischeduler::Statistics – metoda  
 Obsahuje informace související s příchodem a dokončení sazby úlohy a změna v délka fronty pro plánovače.  
  
```
virtual void Statistics(
    _Out_ unsigned int* pTaskCompletionRate,
    _Out_ unsigned int* pTaskArrivalRate,
    _Out_ unsigned int* pNumberOfTasksEnqueued) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `pTaskCompletionRate`  
 Počet úloh, které byly dokončeny plánovačem od posledního volání této metody.  
  
 `pTaskArrivalRate`  
 Počet úloh plánovače přijatých od posledního volání této metody.  
  
 `pNumberOfTasksEnqueued`  
 Celkový počet úloh ve všech frontách plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána pomocí Správce prostředků účely shromažďování statistik pro plánovače. Statistiky shromážděné tady se používá k řízení algoritmy dynamické zpětnou vazbu k určení, kdy je třeba přiřadit více zdrojů pro Plánovač a kdy ulici, prostředky. Hodnoty poskytovaných plánovačem může být optimistickou metodu a není nutné přesně odrážet aktuální počet.  
  
 Tato metoda by měla implementovat, pokud chcete, aby Resource Manager, který chcete použít zpětnou vazbu o takové věci jako příchodem úloh a určit, jak k vyrovnávání prostředků mezi vaší Plánovač a dalších plánovače zaregistrován pomocí Resource Manageru. Pokud si zvolíte shromažďování statistik, můžete nastavit zásady klíč `DynamicProgressFeedback` na hodnotu `DynamicProgressFeedbackDisabled` v vašeho scheduleru zásad a prostředek Manager nebude vyvolat tuto metodu pro vaše plánovač.  
  
 Chybí statistické informace Resource Manager používat k provádění prostředku rozhodnutí o přidělení a migrace úrovně předplatné hardwaru přístup z více vláken. Další informace o úrovních předplatné najdete v tématu [iexecutionresource::currentsubscriptionlevel –](iexecutionresource-structure.md#currentsubscriptionlevel).  
  
## <a name="see-also"></a>Viz také  
 [Namespace souběžnosti](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [SchedulerPolicy – třída](schedulerpolicy-class.md)   
 [Iexecutioncontext – struktura](iexecutioncontext-structure.md)   
 [Ithreadproxy – struktura](ithreadproxy-structure.md)   
 [Ivirtualprocessorroot – struktura](ivirtualprocessorroot-structure.md)   
 [Iresourcemanager – struktura](iresourcemanager-structure.md)
