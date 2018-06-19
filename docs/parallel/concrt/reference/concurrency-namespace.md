---
title: Concurrency Namespace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d5659c48b73eb8dfde4ffc7683de3c2cf721564d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695184"
---
# <a name="concurrency-namespace"></a>concurrency – obor názvů
`Concurrency` Obor názvů obsahuje třídy a funkce, které získáte přístup k Concurrency Runtime, souběžné programování framework pro C++. Další informace najdete v tématu [Concurrency Runtime](../../../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
namespace concurrency;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="namespaces"></a>Jmenné prostory  
  
|Název|Popis|  
|----------|-----------------|  
|[Concurrency::Extensibility Namespace](http://msdn.microsoft.com/en-us/16a86ff2-128e-4edf-89e4-38aac79c81f9)||  
  
### <a name="typedefs"></a>Typedefs  
  
|Název|Popis|  
|----------|-----------------|  
|`runtime_object_identity`|Každá instance zpráva má identitu následujícího je klonovat a předávají mezi součástmi zasílání zpráv. To nemůže být adresu objektu zprávy.|  
|`task_status`|Typ, který představuje terminálu stav úlohy. Platné hodnoty jsou `completed` a `canceled`.|  
|`TaskProc`|Základní abstrakci pro úlohy, definován jako `void (__cdecl * TaskProc)(void *)`. A `TaskProc` je volána k vyvolání text úlohu.|  
|`TaskProc_t`|Základní abstrakci pro úlohy, definován jako `void (__cdecl * TaskProc_t)(void *)`. A `TaskProc` je volána k vyvolání text úlohu.|  
  
### <a name="classes"></a>Třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[affinity_partitioner – třída](affinity-partitioner-class.md)|`affinity_partitioner` Třídy je podobná `static_partitioner` třídy, ale zvyšuje mezipaměti spřažení podle svého výběru mapování podrozsahů na pracovních vláken. Ho může výrazně zvýšit výkon při smyčku je znovu spustit přes stejnou sadu dat a zda je data v mezipaměti. Všimněte si, že stejný `affinity_partitioner` objekt musí být použit s následující iterace paralelní smyčky, která je spuštěna v rámci konkrétní sady dat, abyste mohli využívat výhod polohu data.|  
|[agent – třída](agent-class.md)|Třída určena pro použití jako základní třída pro všechny agenty nezávislé. Umožňuje skrýt stavu z jiné agenty a komunikovat pomocí přenosu zpráv.|  
|[auto_partitioner – třída](auto-partitioner-class.md)|`auto_partitioner` Třída reprezentuje výchozí metoda `parallel_for`, `parallel_for_each` a `parallel_transform` použít při vytváření oddílů se iteruje nad rozsahu. Tato metoda oddíly employes rozsahu krádež pro vyrovnávání zatížení a také za iteraci zrušení.|  
|[bad_target – třída](bad-target-class.md)|Tato třída popisuje výjimka vyvolaná při zasílání zpráv blok je zadána ukazatel cíl, který je neplatný pro prováděnou operaci.|  
|[call – třída](call-class.md)|A `call` zasílání zpráv blok je více zdroje, seřazené `target_block` , který spustí zadaná funkce při přijímání zprávy.|  
|[cancellation_token – třída](cancellation-token-class.md)|`cancellation_token` Třída reprezentuje schopnosti určit, zda byla vyžádána některé operace zrušení. Daný token dají přidružit `task_group`, `structured_task_group`, nebo `task` zajistit implicitní zrušení. Můžete ho také dotazování pro zrušení nebo zpětné volání pro registrováno Pokud a při přidruženého `cancellation_token_source` je zrušená.|  
|[cancellation_token_registration – třída](cancellation-token-registration-class.md)|`cancellation_token_registration` Třída reprezentuje zpětné volání oznámení z `cancellation_token`. Když `register` metodu `cancellation_token` se používá k přijetí oznámení o zrušení v případech, `cancellation_token_registration` jako popisovač pro zpětné volání tak, aby volající požadovat zpětného volání konkrétní už být provedeny prostřednictvím použití sevrátíobjekt`deregister` metoda.|  
|[cancellation_token_source – třída](cancellation-token-source-class.md)|`cancellation_token_source` Třída reprezentuje možnost zrušit některé možné zrušit operaci.|  
|[choice – třída](choice-class.md)|A `choice` zasílání zpráv blok je více zdroje, jeden cílový blok, který představuje tok řízení interakci s sadu zdrojů. Výběr bloku bude čekat na některém z více zdrojů pro vytvoření zprávy a rozšíří index zdroje, který vytváří zprávu.|  
|[combinable – třída](combinable-class.md)|`combinable<T>` Objektu slouží jako vlákno privátní kopií dat, provádět výpočty dílčí uvolnění zámku místní během paralelní algoritmy. Na konci paralelní operace dílčí výpočty vlákno privátní můžete pak sloučit konečný výsledek. Tato třída je možné místo sdílené proměnné a může mít za následek zlepšování výkonu Pokud by jinak byly spoustu kolizí sdílené proměnné.|  
|[concurrent_priority_queue – třída](concurrent-priority-queue-class.md)|`concurrent_priority_queue` Třída je kontejner, který umožňuje více vláken současně nabízení a pop položek. Položky jsou odebrány v pořadí podle priority, kde je priorita určena functor, zadaný jako argument šablony.|  
|[concurrent_queue – třída](concurrent-queue-class.md)|`concurrent_queue` Třída je pořadí kontejneru třídu, která umožňuje first in, první ven přístup k jeho elementy. Umožňuje omezenou sadu souběžnosti bezpečných operace, jako například `push` a `try_pop`.|  
|[concurrent_unordered_map – třída](concurrent-unordered-map-class.md)|`concurrent_unordered_map` Třída je bezpečné souběžnosti kontejner, který určuje posloupnost různých délka elementy typu `std::pair<const K, _Element_type>`. Pořadí je reprezentována způsobem, který umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.|  
|[concurrent_unordered_multimap – třída](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap` Třída je kontejner bezpečných souběžnosti, kterými se řídí různých délka posloupnost elementy typu `std::pair<const K, _Element_type>`. Pořadí je reprezentována způsobem, který umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.|  
|[concurrent_unordered_multiset – třída](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset` Třída je concurrency bezpečných kontejner, který určuje posloupnost různých délka elementy typu K. Pořadí je reprezentována způsobem, který umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.|  
|[concurrent_unordered_set – třída](concurrent-unordered-set-class.md)|`concurrent_unordered_set` Třída je concurrency bezpečných kontejner, který určuje posloupnost různých délka elementy typu K. Pořadí je reprezentována způsobem, který umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.|  
|[concurrent_vector – třída](concurrent-vector-class.md)|`concurrent_vector` Třídy je třída kontejneru pořadí, která umožňuje náhodný přístup k libovolného elementu. Umožňuje bezpečné souběžnosti připojit, iterator traversal operace, iterator přístup a přístup k elementu.|  
|[Context – třída](context-class.md)|Představuje abstrakci pro kontextu spuštění.|  
|[context_self_unblock – třída](context-self-unblock-class.md)|Tato třída popisuje výjimka vyvolaná při `Unblock` metodu `Context` objektu se říká ze stejného kontextu. To by indikovat pokus o daném kontextu odblokovat sám sebe.|  
|[context_unblock_unbalanced – třída](context-unblock-unbalanced-class.md)|Tato třída popisuje výjimka vyvolaná při volání `Block` a `Unblock` metody `Context` objekt nejsou spárovány správně.|  
|[critical_section – třída](critical-section-class.md)|Mutex nejsou vícenásobně přístupné, což je explicitně vědět Concurrency Runtime.|  
|[CurrentScheduler – třída](currentscheduler-class.md)|Představuje abstrakci pro přidružený k volání kontextu aktuálního plánovače.|  
|[default_scheduler_exists – třída](default-scheduler-exists-class.md)|Tato třída popisuje výjimka vyvolaná při `Scheduler::SetDefaultSchedulerPolicy` metoda je volána, když plánovače výchozí již existuje v rámci procesu.|  
|[event – třída](event-class.md)|Ruční vynulování události, které explicitně zná Concurrency Runtime.|  
|[improper_lock – třída](improper-lock-class.md)|Tato třída popisuje výjimku vyvolá, když je nesprávně získat zámek.|  
|[improper_scheduler_attach – třída](improper-scheduler-attach-class.md)|Tato třída popisuje výjimka vyvolaná při `Attach` metoda je volána na `Scheduler` objekt, který je již připojen k aktuálním kontextu.|  
|[improper_scheduler_detach – třída](improper-scheduler-detach-class.md)|Tato třída popisuje výjimka vyvolaná při `CurrentScheduler::Detach` metoda je volána v kontextu, který nebyl přidán do jakékoli služby Plánovač pomocí `Attach` metodu `Scheduler` objektu.|  
|[improper_scheduler_reference – třída](improper-scheduler-reference-class.md)|Tato třída popisuje výjimka vyvolaná při `Reference` metoda je volána na `Scheduler` objekt, který se vypíná, z kontextu, který není součástí tohoto plánovače.|  
|[invalid_link_target – třída](invalid-link-target-class.md)|Tato třída popisuje výjimka vyvolaná při `link_target` je volána metoda blok zasílání zpráv a zasílání zpráv blok nejde připojit k cíli. To může být výsledkem vyšší než počet odkazů, které je povoleno zasílání zpráv bloku nebo při pokusu o odkaz na konkrétní cíl dvakrát pro stejný zdroj.|  
|[invalid_multiple_scheduling – třída](invalid-multiple-scheduling-class.md)|Tato třída popisuje výjimka vyvolaná při `task_handle` objekt je naplánované vícekrát používá `run` metodu `task_group` nebo `structured_task_group` objektu bez použité volání buď `wait` nebo `run_and_wait` metody.|  
|[invalid_operation – třída](invalid-operation-class.md)|Tato třída popisuje výjimka vyvolána v případě, že se provádí na neplatnou operaci, která není popsat přesněji jiný typ výjimky vyvolané Concurrency Runtime.|  
|[invalid_oversubscribe_operation – třída](invalid-oversubscribe-operation-class.md)|Tato třída popisuje výjimka vyvolaná při `Context::Oversubscribe` metoda je volána s `_BeginOversubscription` parametr nastaven na `false` bez předchozího volání `Context::Oversubscribe` metoda s `_BeginOversubscription` parametr nastaven na `true`.|  
|[invalid_scheduler_policy_key – třída](invalid-scheduler-policy-key-class.md)|Tato třída popisuje výjimka vyvolaná při neplatný nebo je předán neznámý klíč `SchedulerPolicy` konstruktoru objektu, nebo `SetPolicyValue` metodu `SchedulerPolicy` klíč, který je třeba změnit pomocí jiným způsobem, jako je předán objekt `SetConcurrencyLimits` metoda.|  
|[invalid_scheduler_policy_thread_specification – třída](invalid-scheduler-policy-thread-specification-class.md)|Tato třída popisuje výjimku při pokusu o nastavení souběžnosti omezení `SchedulerPolicy` objektu tak, že hodnota `MinConcurrency` klíč je menší než hodnota `MaxConcurrency` klíč.|  
|[invalid_scheduler_policy_value – třída](invalid-scheduler-policy-value-class.md)|Tato třída popisuje výjimka vyvolaná při zásad klíč `SchedulerPolicy` je nastavena na neplatnou hodnotu pro tento klíč.|  
|[ISource – třída](isource-class.md)|`ISource` Třída je rozhraní pro všechny zdrojové bloky. Zdroj bloky rozšířit zprávy a pokuste se `ITarget` bloky.|  
|[ITarget – třída](itarget-class.md)|`ITarget` Třída je rozhraní pro všechny cílové bloky. Cíl bloky využívat zprávy jim podle nabízejí `ISource` bloky.|  
|[join – třída](join-class.md)|A `join` zasílání zpráv blok je jeden cíl, více zdroje, seřazených `propagator_block` který kombinuje společně zprávy typu `T` z každé její zdroje.|  
|[location – třída](location-class.md)|Abstrakci fyzické umístění na hardwaru.|  
|[message – třída](message-class.md)|Obálku základní zprávu obsahující datovou předávány mezi bloky zasílání zpráv.|  
|[message_not_found – třída](message-not-found-class.md)|Tato třída popisuje výjimka vyvolaná při blok zasílání zpráv se nepodařilo najít požadovaný zprávu.|  
|[message_processor – třída](message-processor-class.md)|`message_processor` Třída je abstraktní základní třída pro zpracování `message` objekty. Neexistuje žádná záruka řazení zpráv v.|  
|[missing_wait – třída](missing-wait-class.md)|Tato třída popisuje výjimka vyvolaná při stále naplánované úlohy `task_group` nebo `structured_task_group` objektu v době tento objekt destruktor. Tato výjimka bude vyvolána nikdy Pokud destruktoru je dostupný z důvodu unwinding v důsledku výjimky zásobníku.|  
|[multi_link_registry – třída](multi-link-registry-class.md)|`multi_link_registry` Objekt `network_link_registry` , spravuje více bloků zdroje nebo více bloků cíl.|  
|[multitype_join – třída](multitype-join-class.md)|A `multitype_join` zasílání zpráv blok je více zdroje, jeden cílový blok zasílání zpráv, který kombinuje společně zprávy různých typů z každé její zdroje a nabízí řazené kolekce členů kombinované zpráv k jeho cílům.|  
|[nested_scheduler_missing_detach – třída](nested-scheduler-missing-detach-class.md)|Tato třída popisuje výjimka vyvolaná při Concurrency Runtime zjistí, že nevrátil volání `CurrentScheduler::Detach` metoda v kontextu, který je připojen k druhý plánovače pomocí `Attach` metodu `Scheduler` objektu.|  
|[network_link_registry – třída](network-link-registry-class.md)|`network_link_registry` Abstraktní základní třída spravuje propojení mezi zdrojovými a cílovými bloky.|  
|[operation_timed_out – třída](operation-timed-out-class.md)|Tato třída popisuje výjimka vyvolaná při vypršel časový limit operace.|  
|[ordered_message_processor – třída](ordered-message-processor-class.md)|`ordered_message_processor` Je `message_processor` umožňuje bloky zpráv ke zpracování zpráv v pořadí, které byly přijaty.|  
|[overwrite_buffer – třída](overwrite-buffer-class.md)|`overwrite_buffer` Zasílání zpráv blok je více cíl, více zdroje, seřazených `propagator_block` umožňující ukládání do jedné zprávy najednou. Nové zprávy přepsat dříve udržovaných ty.|  
|[progress_reporter – třída](progress-reporter-class.md)|Třída průběh zpravodaje, která umožňuje reporting oznámení průběhu určitého typu. Každý objekt progress_reporter je vázána na operaci nebo konkrétní asynchronní akce.|  
|[propagator_block – třída](propagator-block-class.md)|`propagator_block` Třída je abstraktní základní třídu pro bloky zpráv, které jsou zdrojovém i cílovém. Kombinuje funkci i `source_block` a `target_block` třídy.|  
|[reader_writer_lock – třída](reader-writer-lock-class.md)|Zapisovač předvoleb zámku na základě fronty čtení a zápis s místní pouze otáčí. Zámek uděluje nejprve v – nejprve out (FIFO) přístup k zapisovače a starves čtečky průběžné zatížení zapisovačů.|  
|[ScheduleGroup – třída](schedulegroup-class.md)|Představuje abstrakci pro skupinu plánu. Skupiny plánů uspořádání sady souvisejících pracovních této výhody z naplánován blízko sebe, buď dočasně, a to spuštěním jiná úloha ve stejné skupině před přesunutím do jiné skupiny, nebo jinými objekty, spuštěním více položek v jedné skupině na stejné Nebo soket fyzického uzlu NUMA.|  
|[Scheduler – třída](scheduler-class.md)|Představuje abstrakci pro Concurrency Runtime plánovače.|  
|[scheduler_not_attached – třída](scheduler-not-attached-class.md)|Tato třída popisuje výjimku vyvolá, když se provádí operace, který vyžaduje plánovače připojí se k aktuální kontext a jedna není.|  
|[scheduler_resource_allocation_error – třída](scheduler-resource-allocation-error-class.md)|Tato třída popisuje výjimce z důvodu selhání získat prostředek kritické v Concurrency Runtime.|  
|[scheduler_worker_creation_error – třída](scheduler-worker-creation-error-class.md)|Tato třída popisuje výjimce z důvodu selhání při vytváření kontextu spuštění pracovního procesu v Concurrency Runtime.|  
|[SchedulerPolicy – třída](schedulerpolicy-class.md)|`SchedulerPolicy` Třída obsahuje sadu páry klíč/hodnota, jeden pro každý prvek zásady, které řídí chování instance plánovače.|  
|[simple_partitioner – třída](simple-partitioner-class.md)|`simple_partitioner` Třída reprezentuje statické dělení vstupní přes podle rozsahu `parallel_for`. Dělicí metody rozsahu rozdělí do bloků, tak, aby měl každého bloku alespoň počet iterací určeného velikost bloku.|  
|[single_assignment – třída](single-assignment-class.md)|A `single_assignment` zasílání zpráv blok je více cíl, více zdroje, seřazených `propagator_block` umožňující ukládání jedinou zápisu-po `message`.|  
|[single_link_registry – třída](single-link-registry-class.md)|`single_link_registry` Objekt `network_link_registry` , spravuje pouze jeden blok zdroje nebo cíle.|  
|[source_block – třída](source-block-class.md)|`source_block` Třída je abstraktní základní třídu pro jen zdroj bloky. Třída poskytuje funkce správy základní odkaz jako dobře běžné chyby kontroly.|  
|[source_link_manager – třída](source-link-manager-class.md)|`source_link_manager` Objekt spravuje zasílání zpráv bloku sítě odkazy na `ISource` bloky.|  
|[static_partitioner – třída](static-partitioner-class.md)|`static_partitioner` Třída reprezentuje statické dělení vstupní přes podle rozsahu `parallel_for`. Dělicí metody rozdělí rozsahu na libovolný počet bloků dat jsou k dispozici pro Plánovač underyling pracovních procesů.|  
|[structured_task_group – třída](structured-task-group-class.md)|`structured_task_group` Třída reprezentuje kolekci vysoce strukturovaných paralelní práce. Jednotlivé paralelní úlohy pro můžete fronty `structured_task_group` pomocí `task_handle` objekty a počkat na jejich dokončení nebo zrušte skupiny úloh před dokončením provádění, který bude všech úloh, které nebyly zahájení zpracování přerušeno.|  
|[target_block – třída](target-block-class.md)|`target_block` Třída je abstraktní základní třída, která poskytuje funkce správy základní odkaz a kontrola chyb pro cíl pouze blokuje.|  
|[task – třída (Concurrency Runtime)](task-class.md)|Paralelní vzory knihovny (PPL) `task` třídy. A `task` objekt představuje práci, kterou lze spustit asynchronně a souběžně další úkoly a paralelní pracovní vytvořené paralelní algoritmy v Concurrency Runtime. Vyvolá výsledek typu `_ResultType` při úspěšném dokončení. Úlohy typu `task<void>` vytvořit žádný výsledek. Úlohu můžete čekali při a zrušení nezávisle na jiné úlohy. Můžete také skládat s ostatními úkoly pomocí pokračování (`then`) a spojení (`when_all`) a volba (`when_any`) vzory.|  
|[task_canceled – třída](task-canceled-class.md)|Tato třída popisuje výjimka vyvolaná objektem vrstvě PPL úlohy, aby vynutil aktuální úlohu zrušit. Je také vyvolané `get()` metodu [úloh](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f), zrušené úlohy.|  
|[task_completion_event – třída](task-completion-event-class.md)|`task_completion_event` Třída umožňuje zpozdit provádění úlohy, dokud je podmínka nebo spustit úlohu v reakci na externí událost.|  
|[task_continuation_context – třída](task-continuation-context-class.md)|`task_continuation_context` Třída umožňuje určit, kam chcete pokračování spouštění. Je užitečné k použití této třídy z aplikace UWP. Pro aplikace Windows Runtime kontext provádění úkolů pokračování je určené modulem runtime a nejde konfigurovat.|  
|[task_group – třída](task-group-class.md)|`task_group` Třída reprezentuje kolekci paralelní práce, která může být čekali nebo došlo ke zrušení.|  
|[task_handle – třída](task-handle-class.md)|`task_handle` Třída reprezentuje jednotlivé paralelní pracovní položku. Zapouzdřit pokynů a data potřebná k provedení práce.|  
|[task_options – třída (Concurrency Runtime)](task-options-class-concurrency-runtime.md)|Představuje povolené možnosti pro vytvoření úlohy|  
|[timer – třída](timer-class.md)|A `timer` zasílání zpráv blok je jeden cíl `source_block` může odeslat zprávu k cíli po uplynutí zadané časové období má nebo v určitých intervalech.|  
|[transformer – třída](transformer-class.md)|A `transformer` zasílání zpráv blok je jeden cíl, více zdroje, seřazených `propagator_block` který může přijmout zprávy jednoho typu a je schopný ukládání bez vazby počet zpráv jiného typu.|  
|[Třída unbounded_buffer](unbounded-buffer-class.md)|`unbounded_buffer` Zasílání zpráv blok je více cíl, více zdroje, seřazených `propagator_block` umožňující ukládání bez vazby počet zpráv.|  
|[unsupported_os – třída](unsupported-os-class.md)|Tato třída popisuje výjimku vyvolá, když se používá nepodporovaný operační systém.|  
  
### <a name="structures"></a>Struktury  
  
|Název|Popis|  
|----------|-----------------|  
|[DispatchState – struktura](dispatchstate-structure.md)|`DispatchState` Struktura se používá k přenosu stavu, `IExecutionContext::Dispatch` metoda. Je popsaný v případech, ve kterém `Dispatch` metoda je volána `IExecutionContext` rozhraní.|  
|[IExecutionContext – struktura](iexecutioncontext-structure.md)|Rozhraní na kontext spuštění, který můžete spustit na danou virtuálních procesorů a být spolupráce při přepnout kontext.|  
|[IExecutionResource – struktura](iexecutionresource-structure.md)|Abstrakci pro vlákno hardwaru.|  
|[IResourceManager – struktura](iresourcemanager-structure.md)|Rozhraní pro správce prostředků Concurrency Runtime. Toto je rozhraní, pomocí kterého plánovače komunikovat se správcem prostředků.|  
|[IScheduler – struktura](ischeduler-structure.md)|Rozhraní pro abstrakci pracovní plánovače. Concurrency Runtime Resource Manager používá ke komunikaci s pracovní plánovače toto rozhraní.|  
|[ISchedulerProxy – struktura](ischedulerproxy-structure.md)|Rozhraní, pomocí kterého plánovače komunikovat se správcem prostředků pro vyjednávání přidělení prostředků Concurrency Runtime.|  
|[IThreadProxy – struktura](ithreadproxy-structure.md)|Abstrakci pro vlákno provádění. V závislosti na tom `SchedulerType` klíčem zásad plánovače vytvoříte Resource Manager udělí můžete vlákno proxy server, který je zálohovaný díky regulární vlákno Win32 nebo které lze plánovat vlákna (UMS) uživatelského režimu. Vlákna UMS jsou podporované v operačních systémech 64bitové verze Windows 7 a vyšší.|  
|[ITopologyExecutionResource – struktura](itopologyexecutionresource-structure.md)|Rozhraní k provádění prostředku definovaným pomocí Správce prostředků.|  
|[ITopologyNode – struktura](itopologynode-structure.md)|Rozhraní pro uzel topologie, jak jsou definovány pomocí Správce prostředků. Uzel obsahuje jeden nebo více prostředků provádění.|  
|[IUMSCompletionList – struktura](iumscompletionlist-structure.md)|Představuje seznam dokončení UMS. Při plánování vláken UMS bloky plánovače určené kontextu je odeslat, aby rozhodnutí o při plánování v kořenovém adresáři základní virtuálních procesorů, zatímco původní vlákno je blokované. Při původní vlákno odblokuje, fronty je operační systém do seznamu dokončení, která je přístupná prostřednictvím tohoto rozhraní. Plánovač můžete dotazovat seznamu dokončení v určené plánování kontext nebo jiné místo, které vyhledávání pro práci.|  
|[IUMSScheduler – struktura](iumsscheduler-structure.md)|Rozhraní pro abstrakci plánovače pracovní, který chce Concurrency Runtime Resource Manager k ruční ho, které lze plánovat vláken (UMS) uživatelského režimu. Resource Manager používá toto rozhraní ke komunikaci s plánovače UMS přístup z více vláken. `IUMSScheduler` Rozhraní dědí z `IScheduler` rozhraní.|  
|[IUMSThreadProxy – struktura](iumsthreadproxy-structure.md)|Abstrakci pro vlákno provádění. Pokud chcete vašeho scheduleru udělit oprávnění uživatelského režimu které lze plánovat vláken (UMS), nastavte hodnotu pro element zásad plánovače `SchedulerKind` k `UmsThreadDefault`a implementovat `IUMSScheduler` rozhraní. UMS vláken jsou pouze podporované v operačních systémech 64bitové verze Windows 7 a vyšší.|  
|[IUMSUnblockNotification – struktura](iumsunblocknotification-structure.md)|Představuje oznámení ze Správce prostředků, proxy přístup z více vláken, která blokovaný a aktivaci vraťte se do plánovače určené plánování kontextu má odblokováno a je připravený k naplánování. Toto rozhraní je neplatný, jakmile kontext přidružený spuštění proxy přístup z více vláken, vrátí z `GetContext` je přeplánovat metody.|  
|[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)|Abstrakci pro hardware vláken, ve kterém můžete spustit vlákno proxy.|  
|[scheduler_interface – struktura](scheduler-interface-structure.md)|Rozhraní plánovače|  
|[scheduler_ptr – struktura (Concurrency Runtime)](scheduler-ptr-structure-concurrency-runtime.md)|Představuje ukazatel plánovače. Tato třída existuje umožňující specifikace sdílené životnost pomocí shared_ptr nebo jen prostý odkaz pomocí nezpracovaná ukazatele.|  
  
### <a name="enumerations"></a>Výčty  
  
|Název|Popis|  
|----------|-----------------|  
|[agent_status](concurrency-namespace-enums.md#agent_status)|Platné stavy pro `agent`.|  
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Typy událostí, které lze sledovat pomocí trasování funkce nabízené knihovna agentů|  
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Typy událostí, které lze sledovat pomocí trasování funkce nabízené Concurrency Runtime.|  
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Příznaky trasování pro typy událostí|  
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|Typ důležité oblasti kontext je uvnitř.|  
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Používané `DynamicProgressFeedback` zásady, které popisují, zda bude znovu vyrovnána prostředky pro Plánovač podle statistické informace shromážděné z Plánovač nebo pouze podle virtuálních procesorů, přejděte do aplikace a z stavu nečinnosti prostřednictvím volání `Activate` a `Deactivate` metody na `IVirtualProcessorRoot` rozhraní. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
|[join_type](concurrency-namespace-enums.md#join_type)|Typ `join` zasílání zpráv bloku.|  
|[message_status](concurrency-namespace-enums.md#message_status)|Platný odpovědi pro nabídku `message` objektu do bloku.|  
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Zásady klíče popisující aspektů scheduler chování. Každý prvek zásad je popsán pár klíč hodnota. Další informace o zásady plánovače a jejich dopadu na plánovače najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|  
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|Používané `SchedulerKind` zásady, které popisují typ vláken, které musí Plánovač využívají pro základní kontexty provádění. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|Používané `SchedulingProtocol` zásady, které popisují, který plánování algoritmus se budou využívat pro Plánovač. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Používá se k označení stavu, ve kterém přístup z více vláken proxy server je v, kdy je prováděna spolupráci kontextu přepnout na jiném podprocesu proxy.|  
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Popisuje provádění stav `task_group` nebo `structured_task_group` objektu. Řada metod, které čekat na úloh naplánovaných pro skupinu úloh k dokončení vrátí hodnotu typu.|  
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|Používané `WinRTInitialization` zásady, které popisují, zda a jak prostředí Windows Runtime budou inicializována na plánovač vláken pro aplikaci, která se spouští v operačních systémech s verzí systému Windows 8 nebo vyšší. Další informace o zásadách dostupné Plánovač najdete v tématu [PolicyElementKey](concurrency-namespace-enums.md#policyelementkey).|  
  
### <a name="functions"></a>Funkce  
  
|Název|Popis|  
|----------|-----------------|  
|[ALLOC – funkce](concurrency-namespace-functions.md#alloc)|Přiděluje blok paměti zadaná velikost z Suballocator ukládání do mezipaměti Concurrency Runtime.|  
|[asend – funkce](concurrency-namespace-functions.md#asend)|Přetíženo. Operace asynchronní odesílání, která plánuje úlohy rozšíření dat na cílový blok.|  
|[cancel_current_task Function](concurrency-namespace-functions.md#cancel_current_task)|Zruší aktuálně spuštěné úlohy. Tuto funkci lze volat z v textu úlohu přerušit provádění úkolu a způsobit, že ho zadat `canceled` stavu.<br /><br /> Není podporováno pro volání této funkce, pokud nejsou v rámci textu `task`. Díky tomu bude mít za následek nedefinované chování například chybě nebo zablokování v aplikaci.|  
|[create_async – funkce](concurrency-namespace-functions.md#create_async)|Vytvoří prostředí Windows Runtime asynchronní konstrukce podle objekt uživatelem dodaný lambda nebo funkce. Návratový typ `create_async` je jedním z buď `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, nebo `IAsyncOperationWithProgress<TResult, TProgress>^` podle podpis lambda předaný metodě.|  
|[create_task – funkce](concurrency-namespace-functions.md#create_task)|Přetíženo. Vytvoří PPL [úloh](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f) objektu. `create_task` lze použít kdekoli byste použili jste konstruktor úloh. Je poskytována především pro usnadnění práce, protože umožňuje použít `auto` – klíčové slovo při vytváření úlohy.|  
|[Createresourcemanager – funkce](concurrency-namespace-functions.md#createresourcemanager)|Vrátí rozhraní, které představuje instanci typu singleton z Concurrency Runtime Resource Manager. Resource Manager zodpovídá za přiřazení zdrojů k plánovače, které chcete vzájemně spolupracovat.|  
|[Disabletracing – funkce](concurrency-namespace-functions.md#disabletracing)|Zakáže trasování v Concurrency Runtime. Tato funkce je zastaralý, protože je ve výchozím nastavení neregistrovaná trasování událostí pro Windows.|  
|[Enabletracing – funkce](concurrency-namespace-functions.md#enabletracing)|Umožňuje trasování v Concurrency Runtime. Tato funkce je zastaralý, protože trasování událostí pro Windows je teď na ve výchozím nastavení.|  
|[Free – funkce](concurrency-namespace-functions.md#free)|Uvolní blok paměti dříve přidělené `Alloc` metodu Suballocator ukládání do mezipaměti Concurrency Runtime.|  
|[get_ambient_scheduler – funkce (Concurrency Runtime)](concurrency-namespace-functions.md#get_ambient_scheduler)||  
|[Getexecutioncontextid – funkce](concurrency-namespace-functions.md#getexecutioncontextid)|Vrací jedinečný identifikátor, který lze přiřadit ke kontextu spuštění, který implementuje `IExecutionContext` rozhraní.|  
|[Getosversion – funkce](concurrency-namespace-functions.md#getosversion)|Vrátí verzi operačního systému.|  
|[Getprocessorcount – funkce](concurrency-namespace-functions.md#getprocessorcount)|Vrátí počet vláken hardwaru v základním systému.|  
|[Getprocessornodecount – funkce](concurrency-namespace-functions.md#getprocessornodecount)|Vrátí počet uzlů NUMA nebo balíčky procesoru v základním systému.|  
|[Getschedulerid – funkce](concurrency-namespace-functions.md#getschedulerid)|Vrací jedinečný identifikátor, který lze přiřadit k Plánovač, který implementuje `IScheduler` rozhraní.|  
|[interruption_point Function](concurrency-namespace-functions.md#interruption_point)|Vytvoří bod přerušení pro zrušení. Pokud zrušení probíhá v kontextu, kde tato funkce je volána, to vyvolá výjimku interní, která zruší provádění aktuálně prováděné paralelní práce. Pokud zrušení není v průběhu, funkce neprovede žádnou akci.|  
|[is_current_task_group_canceling – funkce](concurrency-namespace-functions.md#is_current_task_group_canceling)|Vrátí údaj o tom, jestli úloha skupiny vložené který je právě prováděných v aktuálním kontextu je in the midst of active zrušení (nebo bude zanedlouho). Všimněte si, že pokud neexistuje žádná skupina úloh aktuálně spuštěných vložené v aktuálním kontextu se `false` bude vrácen.|  
|[make_choice – funkce](concurrency-namespace-functions.md#make_choice)|Přetíženo. Vytvoří `choice` zasílání zpráv bloku z volitelný `Scheduler` nebo `ScheduleGroup` a dvě nebo více vstupních zdrojů.|  
|[make_greedy_join – funkce](concurrency-namespace-functions.md#make_greedy_join)|Přetíženo. Vytvoří `greedy multitype_join` zasílání zpráv bloku z volitelný `Scheduler` nebo `ScheduleGroup` a dvě nebo více vstupních zdrojů.|  
|[make_join – funkce](concurrency-namespace-functions.md#make_join)|Přetíženo. Vytvoří `non_greedy multitype_join` zasílání zpráv bloku z volitelný `Scheduler` nebo `ScheduleGroup` a dvě nebo více vstupních zdrojů.|  
|[make_task – funkce](concurrency-namespace-functions.md#make_task)|Metoda factory pro vytváření `task_handle` objektu.|  
|[parallel_buffered_sort – funkce](concurrency-namespace-functions.md#parallel_buffered_sort)|Přetíženo. Uspořádá elementů v zadaném rozsahu do nondescending pořadí, nebo podle řazení kritérium určeného predikátu Binární paralelně. Tato funkce je sémanticky podobná `std::sort` , jsou na základě porovnání nestabilním, místní řazení, s tím rozdílem, že je nutné `O(n)` další prostor a vyžaduje výchozí inicializace pro elementy řazen.|  
|[parallel_for – funkce](concurrency-namespace-functions.md#parallel_for)|Přetíženo. `parallel_for` iteruje nad rozsah indexy a provede funkci uživatelem zadané při každé iteraci paralelně.|  
|[parallel_for_each Function](concurrency-namespace-functions.md#parallel_for_each)|Přetíženo. `parallel_for_each` Zadaná funkce se vztahuje na každý prvek v rozsahu, paralelně. Je sémanticky ekvivalentní `for_each` v fungovat `std` obor názvů, s tím rozdílem, že iteraci přes elementy provádí paralelně a neurčené pořadí iterace. Argument `_Func` musí podporovat operátor volání funkce formuláře `operator()(T)` kde parametr `T` je typ položky kontejneru se vstupní přes.|  
|[parallel_invoke – funkce](concurrency-namespace-functions.md#parallel_invoke)|Přetíženo. Provede zadané jako parametry současně a bloky, dokud dokončily spouštění funkce objekty. Každý objekt funkce může být výraz lambda ukazatel na funkci, nebo žádný objektu, který podporuje operátor volání funkce s podpisem `void operator()()`.|  
|[parallel_radixsort Function](concurrency-namespace-functions.md#parallel_radixsort)|Přetíženo. Jiné sestupném pořadí pomocí radix, řazení algoritmus jsou uspořádány elementy v zadaném rozsahu. Toto je funkce stabilní řazení, který vyžaduje projekce funkci, která můžete promítnout elementy, který se má seřadit do nepodepsaných klíčů jako celé číslo. Výchozí inicializace se vyžaduje pro elementy řazen.|  
|[parallel_reduce Function](concurrency-namespace-functions.md#parallel_reduce)|Přetíženo. Vypočítá součet všech elementů v zadaném rozsahu následných částečné součtů computing připravila nebo vypočítá výsledek následných částečné výsledky podobně získané z pomocí zadané operace binární jinak než součtem, paralelně. `parallel_reduce` je sémanticky podobná `std::accumulate`kromě toho, že vyžaduje binární operace jako asociativní a vyžaduje hodnotu identity namísto počáteční hodnoty.|  
|[parallel_sort – funkce](concurrency-namespace-functions.md#parallel_sort)|Přetíženo. Uspořádá elementů v zadaném rozsahu do nondescending pořadí, nebo podle řazení kritérium určeného predikátu Binární paralelně. Tato funkce je sémanticky podobná `std::sort` v, že je na základě porovnání nestabilním, místní řazení.|  
|[parallel_transform Function](concurrency-namespace-functions.md#parallel_transform)|Přetíženo. Každý prvek v zdrojový rozsah, nebo pár elementy ze dvou zdrojových oblastí se vztahuje objekt zadaná funkce a zkopíruje návratové hodnoty funkce objektu do cílový rozsah, paralelně. Tuto funkční je sémanticky ekvivalentní `std::transform`.|  
|[Receive – funkce](concurrency-namespace-functions.md#receive)|Přetíženo. Obecné přijímat implementace povolení kontext, který má čekat na data z přesně jeden zdroj a filtrování hodnoty, které jsou přijaty.|  
|[run_with_cancellation_token – funkce](concurrency-namespace-functions.md#run_with_cancellation_token)|Spustí objekt funkce v kontextu token zrušení pro daný okamžitě a synchronně.|  
|[Send – funkce](concurrency-namespace-functions.md#send)|Přetíženo. Operaci synchronní odesílání, která čeká na cíl buď přijme nebo odmítne zprávy.|  
|[set_ambient_scheduler – funkce (Concurrency Runtime)](concurrency-namespace-functions.md#set_ambient_scheduler)||  
|[set_task_execution_resources Function](concurrency-namespace-functions.md#set_task_execution_resources)|Přetíženo. Omezuje provádění prostředky využívané třídou Concurrency Runtime interní pracovních vláken na sady zadané spřažení.<br /><br /> Je možné volat tuto metodu jenom dříve, než byl vytvořen správce prostředků, nebo mezi dvě životnosti Resource Manager. Může být vyvolán několikrát, dokud správce prostředků neexistuje v čase volání. Po nastavení omezení vztahů zůstává v platnosti, dokud další platný volání `set_task_execution_resources` metoda.<br /><br /> Zadaná maska spřažení nemusí být podmnožinou Maska spřažení procesu. Proces přidružení aktualizují v případě potřeby.|  
|[swap – funkce](concurrency-namespace-functions.md#swap)|Výměny dva elementy `concurrent_vector` objekty.|  
|[task_from_exception – funkce (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_exception)||  
|[task_from_result – funkce (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_result)||  
|[Trace_agents_register_name – funkce](concurrency-namespace-functions.md#trace_agents_register_name)|Přidruží daným názvem na blokování zpráv nebo agenta v trasování ETW.|  
|[try_receive – funkce](concurrency-namespace-functions.md#try_receive)|Přetíženo. Obecné zkuste a přijetí implementace povolení kontextu hledat data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijaty. Pokud data není připraven, metoda vrátí hodnotu false.|  
|[Wait – funkce](concurrency-namespace-functions.md#wait)|Aktuální kontext pozastaví na zadanou dobu.|  
|[when_all – funkce](concurrency-namespace-functions.md#when_all)|Vytvoří úlohu, která se dokončí úspěšně, když všechny úlohy, zadané jako argumenty úspěšně dokončit.|  
|[when_any – funkce](concurrency-namespace-functions.md#when_any)|Přetíženo. Vytvoří úlohu, která se úspěšně dokončí, když některé z úloh zadané jako argumenty úspěšně dokončena.|  
  
### <a name="operators"></a>Operátory  
  
|Název|Popis|  
|----------|-----------------| 
|[operator!=](concurrency-namespace-operators.md#operator_neq)|Pokud testy `concurrent_vector` objekt na levé straně operátor není rovno `concurrent_vector` objekt na pravé straně.|  
|[Operator & &](concurrency-namespace-operators.md#operator_amp_amp)|Přetíženo. Vytvoří úlohu, která se dokončí svou činnost úspěšně, pokud obě úlohy zadané jako argumenty úspěšně dokončit.|  
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Přetíženo. Vytvoří úlohu, která se úspěšně dokončí, když některý z úkolů zadané jako argumenty úspěšně dokončena.|  
|[operátor <](concurrency-namespace-operators.md#operator_lt)|Testuje, pokud `concurrent_vector` objekt na levé straně operátoru je menší než `concurrent_vector` objekt na pravé straně.|  
|[Operator < =](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, pokud `concurrent_vector` objekt na levé straně operátor je menší než nebo rovno `concurrent_vector` objekt na pravé straně.|  
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|Pokud testy `concurrent_vector` objekt na levé straně operátoru rovná `concurrent_vector` objekt na pravé straně.|  
|[operátor >](concurrency-namespace-operators.md#operator_gt)|Pokud testy `concurrent_vector` objekt na levé straně operátoru je větší než `concurrent_vector` objekt na pravé straně.|  
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, pokud `concurrent_vector` objekt na levé straně operátoru je větší než nebo rovno `concurrent_vector` objekt na pravé straně.|  
  
### <a name="constants"></a>Konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[Agenteventguid –](concurrency-namespace-constants1.md#agenteventguid)|Kategorie události trasování událostí popisující spuštěná knihovna agentů v Concurrency Runtime identifikátor GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07}).|  
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, který přímo souvisí s chores nebo úlohy.|  
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Zprostředkovatel trasování událostí pro Windows identifikátor GUID pro Concurrency Runtime.|  
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Uvádí, že podporuje rozhraní správce prostředků, který je definován v sadě Visual Studio 2010.|  
|[Concrteventguid –](concurrency-namespace-constants1.md#concrteventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, které nejsou konkrétně popsány v jiné kategorii.|  
|[Contexteventguid –](concurrency-namespace-constants1.md#contexteventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, který přímo souvisí s kontexty.|  
|[COOPERATIVE_TIMEOUT_INFINITE –](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Hodnota označující, počkejte by nikdy neměly vypršení časového limitu.|  
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Hodnota označující, že vypršel časový limit čekání.|  
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Speciální hodnotu pro klíč zásad `ContextPriority` indikující, že vlákno prioritu všech kontextů v Plánovači musí být stejná jako u vláken, který vytvoří plánovač.|  
|[Lockeventguid –](concurrency-namespace-constants1.md#lockeventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, který přímo souvisí s zámky.|  
|[Maxexecutionresources –](concurrency-namespace-constants1.md#maxexecutionresources)|Speciální hodnoty pro klíče zásad `MinConcurrency` a `MaxConcurrency`. Výchozí hodnota je počet vláken hardwaru v počítači neexistuje jiná omezení.|  
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Kategorie GUID popisující události trasování událostí spuštěná Concurrency Runtime, který přímo souvisí s využití `parallel_for_each` funkce.|  
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|Kategorie GUID popisující události trasování událostí spuštěná Concurrency Runtime, který přímo souvisí s využití `parallel_for` funkce.|  
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Kategorie GUID popisující události trasování událostí spuštěná Concurrency Runtime, který přímo souvisí s využití `parallel_invoke` funkce.|  
|[Resourcemanagereventguid –](concurrency-namespace-constants1.md#resourcemanagereventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, který přímo souvisí s správce prostředků.|  
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, který přímo souvisí s skupiny plánů.|  
|[Schedulereventguid –](concurrency-namespace-constants1.md#schedulereventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, který přímo souvisí s aktivitu plánovač.|  
|[Virtualprocessoreventguid –](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Kategorie GUID popisující události trasování událostí aktivována podle Concurrency Runtime, který přímo souvisí s virtuálními procesory.|  
  
## <a name="requirements"></a>Požadavky  
 **Header:** agents.h, concrt.h, concrtrm.h, concurrent_priority_queue.h, concurrent_queue.h, concurrent_unordered_map.h, concurrent_unordered_set.h, concurrent_vector.h, internal_concurrent_hash.h, internal_split_ordered_list.h, ppl.h, pplcancellation_token.h, pplconcrt.h, pplinterface.h, ppltasks.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace](reference-concurrency-runtime.md)

