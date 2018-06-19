---
title: výčty obor názvů souběžnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
dev_langs:
- C++
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 068aa89c10e92203ce0e826e3aaca101f4786cbb
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695259"
---
# <a name="concurrency-namespace-enums"></a>výčty obor názvů souběžnosti
||||  
|-|-|-|  
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|  
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|  
|[SchedulerType](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|  
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|  
|[message_status](#message_status)|[task_group_status](#task_group_status)|  
  
##  <a name="agent_status"></a>  agent_status – výčet  
 Platné stavy pro `agent`.  
  
```
enum agent_status;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`agent_canceled`|`agent` Byla zrušena.|  
|`agent_created`|`agent` Byla vytvořena, ale není spuštěna.|  
|`agent_done`|`agent` Skončil bez probíhá její zrušení.|  
|`agent_runnable`|`agent` Spuštění, ale nebylo zadáno jeho `run` metoda.|  
|`agent_started`|`agent` Bylo zahájeno.|  

### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [asynchronních agentů](../../../parallel/concrt/asynchronous-agents.md).  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h

##  <a name="agents_eventtype"></a>  Agents_EventType – výčet  
 Typy událostí, které lze sledovat pomocí trasování funkce nabízené knihovna agentů  
  
```
enum Agents_EventType;
```  

### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`AGENTS_EVENT_CREATE`|Typ události, který představuje vytvoření objektu|  
|`AGENTS_EVENT_DESTROY`|Typ události, který představuje odstranění objektu|  
|`AGENTS_EVENT_END`|Typ události, který představuje uzavření některé zpracování|  
|`AGENTS_EVENT_LINK`|Typ události, který představuje propojení bloky zpráv|  
|`AGENTS_EVENT_NAME`|Typ události, který představuje název pro objekt|  
|`AGENTS_EVENT_SCHEDULE`|Typ události, který představuje plánování procesu|  
|`AGENTS_EVENT_START`|Typ události, který představuje spuštění některých zpracování|  
|`AGENTS_EVENT_UNLINK`|Typ události, který představuje odpojuje bloky zpráv|  

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h

##  <a name="concrt_eventtype"></a>  ConcRT_EventType – výčet  
 Typy událostí, které lze sledovat pomocí trasování funkce nabízené Concurrency Runtime.  
  
```
enum ConcRT_EventType;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`CONCRT_EVENT_ATTACH`|Typ události, který představuje v rámci připojení k plánovače.|  
|`CONCRT_EVENT_BLOCK`|Typ události, který představuje v rámci kontextu blokování.|  
|`CONCRT_EVENT_DETACH`|Typ události, který představuje v rámci probíhá odpojování od plánovače.|  
|`CONCRT_EVENT_END`|Typ události, který označuje začátek pár počáteční nebo koncové události.|  
|`CONCRT_EVENT_GENERIC`|Typ události používá pro různé události.|  
|`CONCRT_EVENT_IDLE`|Typ události, který představuje v rámci kontextu nečinných.|  
|`CONCRT_EVENT_START`|Typ události, který označuje začátek pár počáteční nebo koncové události.|  
|`CONCRT_EVENT_UNBLOCK`|Typ události, který představuje v rámci odblokování kontextu.|  
|`CONCRT_EVENT_YIELD`|Typ události, který představuje v rámci kontextu je.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h **Namespace:** souběžnosti

##  <a name="concrt_traceflags"></a>  Concrt_TraceFlags – výčet  
 Příznaky trasování pro typy událostí  
  
```
enum Concrt_TraceFlags;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`AgentEventFlag`||  
|`AllEventsFlag`||  
|`ContextEventFlag`||  
|`PPLEventFlag`||  
|`ResourceManagerEventFlag`||  
|`SchedulerEventFlag`||  
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h

##  <a name="criticalregiontype"></a>  CriticalRegionType – výčet  
 Typ důležité oblasti kontext je uvnitř.  
  
```
enum CriticalRegionType;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`InsideCriticalRegion`|Určuje, zda kontext je uvnitř důležité oblasti. Když uvnitř důležité oblasti, jsou asynchronní pozastavení skryta plánovače. Měly by toto pozastavení proběhnout, správce prostředků bude čekat na vlákno a stát spustitelného jednoduše ho obnoví místo vyvolání Plánovač znovu. Všechny zámky prováděné uvnitř tyto oblasti musí být přijata velmi opatrně.|  
|`InsideHyperCriticalRegion`|Označuje, zda kontext je uvnitř technologie hyper důležité oblasti. Synchronní a asynchronní pozastavení při uvnitř technologie hyper důležité oblasti, jsou skryta plánovače. By toto pozastavení nebo blokování dojít správce prostředků bude čekat na vlákno a stát spustitelného jednoduše ho obnoví místo vyvolání Plánovač znovu. Zámky prováděné uvnitř tyto oblasti musí být sdílená nikdy kódem běží mimo tyto oblasti. To způsobí nepředvídatelným zablokování.|  
|`OutsideCriticalRegion`|Označuje, že kontextu je mimo všechny kritické oblast.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrtrm.h 

##  <a name="dynamicprogressfeedbacktype"></a>  DynamicProgressFeedbackType – výčet  
 Používané `DynamicProgressFeedback` zásady, které popisují, zda bude znovu vyrovnána prostředky pro Plánovač podle statistické informace shromážděné z Plánovač nebo pouze podle virtuálních procesorů, přejděte do aplikace a z stavu nečinnosti prostřednictvím volání `Activate` a `Deactivate` metody na `IVirtualProcessorRoot` rozhraní. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md).  
  
```
enum DynamicProgressFeedbackType;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`ProgressFeedbackDisabled`|Plánovač není shromažďovat informace o průběhu. Vyrovnává se provádí na základě pouze na úrovni předplatného základní hardware vlákna. Další informace o úrovních předplatné najdete v tématu [iexecutionresource::currentsubscriptionlevel –](IExecutionResource-structure.md).<br /><br /> Tato hodnota je vyhrazený pro použití modulem runtime.|  
|`ProgressFeedbackEnabled`|Plánovač shromáždí informace o průběhu a předává je pro správce prostředků. Správce prostředků bude využívat tyto statistické informace znovu vyvážit prostředky jménem Plánovač kromě úroveň předplatného základní hardware vlákno. Další informace o úrovních předplatné najdete v tématu [iexecutionresource::currentsubscriptionlevel –](IExecutionResource-structure.md).|  
##  <a name="join_type"></a>  join_type – výčet  
 Typ `join` zasílání zpráv bloku.  
  
```
enum join_type;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`greedy`|Typu greedy `join` zasílání zpráv bloky okamžitě přijmout zprávu při šíření. To je efektivnější, ale má možnost live-zámek, v závislosti na konfiguraci sítě.|  
|`non_greedy`|Typu non-greedy `join` zasílání zpráv bloky odložit zprávy a zkuste to a využívat po všech se zobrazila. Tyto zaručeně pracovat, ale něco pomalejší.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  

##  <a name="message_status"></a>  message_status – výčet  
 Platný odpovědi pro nabídku `message` objektu do bloku.  
  
```
enum message_status;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`accepted`|Cíl přijaté zprávy.|  
|`declined`|Cíl nepřijal zprávy.|  
|`missed`|Cíl pokusu přijímat zprávy, ale již není k dispozici.|  
|`postponed`|Cíl odložena zprávy.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** agents.h  

##  <a name="policyelementkey"></a>  PolicyElementKey – výčet  
 Zásady klíče popisující aspektů scheduler chování. Každý prvek zásad je popsán pár klíč hodnota. Další informace o zásady plánovače a jejich dopadu na plánovače najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
```
enum PolicyElementKey;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`ContextPriority`|Priorita vlákna operačního systému každý kontext v plánovače. Pokud tento klíč je nastaven na hodnotu `INHERIT_THREAD_PRIORITY` kontexty v Plánovači zdědí prioritu vlákno, které vytvořili plánovače.<br /><br /> Platné hodnoty: žádné platné hodnoty pro Windows `SetThreadPriority` funkce a speciální hodnotu `INHERIT_THREAD_PRIORITY`<br /><br /> Výchozí hodnota: `THREAD_PRIORITY_NORMAL`|  
|`ContextStackSize`|Velikost zásobníku vyhrazené každý kontext v Plánovači v kilobajtech.<br /><br /> Platné hodnoty: kladná celá čísla<br /><br /> Výchozí hodnota: `0`, která udává, že proces výchozí hodnota pro velikost zásobníku používat.|  
|`DynamicProgressFeedback`|Určuje, zda bude znovu vyrovnána prostředky pro Plánovač podle statistické informace shromážděné z Plánovač nebo založena pouze na úrovni předplatného základní hardware vláken. Další informace najdete v tématu [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Platné hodnoty: členem `DynamicProgressFeedbackType` výčtu, buď `ProgressFeedbackEnabled` nebo `ProgressFeedbackDisabled`<br /><br /> Výchozí hodnota: `ProgressFeedbackEnabled`|  
|`LocalContextCacheSize`|Když `SchedulingProtocol` zásad klíč je nastaven na hodnotu `EnhanceScheduleGroupLocality`, určuje maximální počet spustitelného kontexty povolené ukládat do mezipaměti v na místní fronty virtuálních procesorů. Takové kontexty bude obvykle běží v pořadí last-in-first-out (LIFO) na virtuální procesor, která způsobila, že aby se mohly stát spustitelného. Všimněte si, zda má tento klíč zásad žádné znamená, když `SchedulingProtocol` klíč je nastaven na hodnotu `EnhanceForwardProgress`.<br /><br /> Platné hodnoty: nezáporná celá čísla<br /><br /> Výchozí hodnota: `8`|  
|`MaxConcurrency`|Souběžnost maximální úrovně požadovaného plánovačem. Správce prostředků se pokusí původně přidělit uvedený počet virtuálních procesorů. Speciální hodnota [maxexecutionresources –](concurrency-namespace-constants1.md#maxexecutionresources) označuje, že úroveň požadované souběžnosti je stejný jako počet vláken hardwaru v počítači. Pokud je hodnota zadaná u `MinConcurrency` je větší než počet vláken hardwaru v počítači a `MaxConcurrency` je zadán jako `MaxExecutionResources`, hodnota `MaxConcurrency` se vyvolá, tak, aby odpovídaly, co je nastaven pro `MinConcurrency`.<br /><br /> Platné hodnoty: kladná celá čísla a speciální hodnotu `MaxExecutionResources`<br /><br /> Výchozí hodnota: `MaxExecutionResources`|  
|`MaxPolicyElementKey`|Klíč elementu maximální zásad. Není platný element klíč.|  
|`MinConcurrency`|Úroveň minimální souběžnosti pro Plánovač je třeba zadat správce prostředků. Počet virtuálních procesorů, které jsou přiřazené plánovače přejde nikdy menší než minimální. Speciální hodnota [maxexecutionresources –](concurrency-namespace-constants1.md#maxexecutionresources) označuje, že úroveň minimální souběžnosti je stejný jako počet vláken hardwaru v počítači. Pokud je hodnota zadaná u `MaxConcurrency` je menší než počet vláken hardwaru v počítači a `MinConcurrency` je zadán jako `MaxExecutionResources`, hodnota `MinConcurrency` je snížena tak, aby odpovídaly, co je nastaven pro `MaxConcurrency`.<br /><br /> Platné hodnoty: nezáporná celá čísla a speciální hodnotu `MaxExecutionResources`. Všimněte si, že pro zásady plánovače používá pro tvorbu plánovače Concurrency Runtime, hodnota `0` je neplatný.<br /><br /> Výchozí hodnota: `1`|  
|`SchedulerKind`|Typ vláken, která Plánovač budou využívat pro základní kontexty provádění. Další informace najdete v tématu [SchedulerType](#schedulertype).<br /><br /> Platné hodnoty: členem `SchedulerType` výčtu, například `ThreadScheduler`<br /><br /> Výchozí hodnota: `ThreadScheduler`. Výsledkem Win32 vláken ve všech operačních systémech.|  
|`SchedulingProtocol`|Popisuje, jaké plánování algoritmus se použije plánovačem. Další informace najdete v tématu [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Platné hodnoty: členem `SchedulingProtocolType` výčtu, buď `EnhanceScheduleGroupLocality` nebo `EnhanceForwardProgress`<br /><br /> Výchozí hodnota: `EnhanceScheduleGroupLocality`|  
|`TargetOversubscriptionFactor`|Předběžná počet virtuálních procesorů na vlákno hardwaru. Cílový faktor Překryvný odběr může být zvýšena pomocí Správce prostředků v případě potřeby, aby pokryl `MaxConcurrency` s vlákny hardwaru v počítači.<br /><br /> Platné hodnoty: kladná celá čísla<br /><br /> Výchozí hodnota: `1`|  
|`WinRTInitialization`||  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  

##  <a name="schedulertype"></a>  SchedulerType – výčet  
 Používané `SchedulerKind` zásady, které popisují typ vláken, které musí Plánovač využívají pro základní kontexty provádění. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md).  
  
```
enum SchedulerType;
``` 

### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`ThreadScheduler`|Označuje požadavek explicitní regulární Win32 vláken.|  
|`UmsThreadDefault`|Režim uživatele které lze plánovat vláken (UMS) nejsou podporovány v Concurrency Runtime v sadě Visual Studio 2013. Pomocí `UmsThreadDefault` jako hodnotu `SchedulerType` zásada nebude mít za následek chybu. Plánovače vytvořené pomocí této zásadě se však výchozí použití Win32 vláken.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
  
##  <a name="schedulingprotocoltype"></a>  SchedulingProtocolType – výčet  
 Používané `SchedulingProtocol` zásady, které popisují, který plánování algoritmus se budou využívat pro Plánovač. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md).  
  
```
enum SchedulingProtocolType;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`EnhanceForwardProgress`|Plánovač upřednostňuje kruhového dotazování prostřednictvím skupiny plánu po provedení každého úkolu. Odblokování kontexty naplánovány obvykle způsobem first-in-first-out (FIFO). Virtuální procesory Neukládat do mezipaměti odblokuje kontexty.|  
|`EnhanceScheduleGroupLocality`|Chcete-li pokračovat v práci na úlohy v aktuální skupině plán před přesunutím do jiné skupiny pro plán upřednostní plánovače. Odblokování kontexty ukládaných do mezipaměti na virtuální procesor a jsou obvykle naplánovány způsobem last-in-first-out (LIFO) ve virtuálních procesorů, které je odblokováno.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  
 
##  <a name="switchingproxystate"></a>  SwitchingProxyState – výčet  
 Používá se k označení stavu, ve kterém přístup z více vláken proxy server je v, kdy je prováděna spolupráci kontextu přepnout na jiném podprocesu proxy.  
  
```
enum SwitchingProxyState;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`Blocking`|Označuje, že volající vlákno je spolupráce při blokování a vlastníkem by měl být výhradně volající dokud následně znovu a provádění dalších akcí.|  
|`Idle`|Označuje, že volající vlákno je už nepotřebuje plánovačem a se vrací Resource Manager. Kontext, který byl distribuovanou již moci použít Správce prostředků.|  
|`Nesting`|Označuje, že volající vlákno je vnoření plánovače podřízený a je potřeba volající, aby bylo možné připojit k jiné plánovače.|  

### <a name="remarks"></a>Poznámky  
 Parametr typu `SwitchingProxyState` je předaná metodě `IThreadProxy::SwitchTo` dáte pokyn, aby správce prostředků má stát s proxy serverem přístup z více vláken, který je uskutečněním hovoru.  
  
 Další informace o tom, jak tento typ se používá, najdete v části [ithreadproxy::switchto –](ithreadproxy-structure.md#switchto).  
  
##  <a name="task_group_status"></a>  task_group_status – výčet  
 Popisuje provádění stav `task_group` nebo `structured_task_group` objektu. Řada metod, které čekat na úloh naplánovaných pro skupinu úloh k dokončení vrátí hodnotu typu.  
  
```
enum task_group_status;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`canceled`|`task_group` Nebo `structured_task_group` objekt byl zrušen. Jeden nebo více úloh, nemusí mít provést.|  
|`completed`|Zařazených do fronty úloh `task_group` nebo `structured_task_group` objekt byl úspěšně dokončen.|  
|`not_complete`|Zařazených do fronty úloh `task_group` objekt dosud nebyly dokončeny. Všimněte si, že tato hodnota není v současné době vrácený Concurrency Runtime.|  
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** pplinterface.h  

##  <a name="winrtinitializationtype"></a>  WinRTInitializationType – výčet  
 Používané `WinRTInitialization` zásady, které popisují, zda a jak prostředí Windows Runtime budou inicializována na plánovač vláken pro aplikaci, která se spouští v operačních systémech s verzí systému Windows 8 nebo vyšší. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md).  
  
```
enum WinRTInitializationType;
```  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`DoNotInitializeWinRT`|Když je aplikace spuštěné na operačních systémech s verzí systému Windows 8 nebo vyšší, vláken v rámci Plánovač nebude inicializovat prostředí Windows Runtime.|  
|`InitializeWinRTAsMTA`|Když je aplikace spuštěna v operačních systémech s verzí systému Windows 8 nebo vyšší, bude každé vlákno v rámci Plánovač inicializovat prostředí Windows Runtime a deklarovat, který je součástí více vláken typu apartment.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** concrt.h  

## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
