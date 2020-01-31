---
title: concurrency – obor názvů
ms.date: 11/04/2016
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
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
ms.openlocfilehash: 5449362454c5899e544ed370f13d28471a59bd13
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821841"
---
# <a name="concurrency-namespace"></a>concurrency – obor názvů

Obor názvů `Concurrency` poskytuje třídy a funkce, které vám umožní přístup k Concurrency Runtime, souběžně programovací rozhraní pro C++. Další informace najdete v tématu [Concurrency Runtime](../../../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```
namespace concurrency;
```

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|Name|Popis|
|----------|-----------------|
|`runtime_object_identity`|Každá instance zprávy má identitu, která ji následuje, protože je klonována a předána mezi součástmi zasílání zpráv. Nejedná se o adresu objektu zprávy.|
|`task_status`|Typ, který představuje stav terminálu úkolu. Platné hodnoty jsou `completed` a `canceled`.|
|`TaskProc`|Základní abstrakce úlohy definovaná jako `void (__cdecl * TaskProc)(void *)`. Je volána `TaskProc` k vyvolání těla úkolu.|
|`TaskProc_t`|Základní abstrakce úlohy definovaná jako `void (__cdecl * TaskProc_t)(void *)`. Je volána `TaskProc` k vyvolání těla úkolu.|

### <a name="classes"></a>Třídy

|Name|Popis|
|----------|-----------------|
|[affinity_partitioner – třída](affinity-partitioner-class.md)|Třída `affinity_partitioner` je podobná `static_partitioner` třídě, ale vylepšuje spřažení mezipaměti podle výběru mapování dílčích rozsahů na pracovní vlákna. Může výrazně zvýšit výkon, když se smyčka znovu spustí přes stejnou datovou sadu a data se vejdou do mezipaměti. Všimněte si, že stejný objekt `affinity_partitioner` musí být použit s následnými iteracemi paralelní smyčky spouštěné přes konkrétní datovou sadu, aby bylo možné využít data z místního prostředí.|
|[agent – třída](agent-class.md)|Třída určená pro použití jako základní třída pro všechny nezávislé agenty. Slouží ke skrytí stavu od jiných agentů a k interakci s použitím předávání zpráv.|
|[auto_partitioner – třída](auto-partitioner-class.md)|Třída `auto_partitioner` představuje výchozí metodu `parallel_for`, `parallel_for_each` a `parallel_transform` použít k rozdělení rozsahu, na který iterovat. Tato metoda vytváření oddílů využívá krádež rozsahu pro vyrovnávání zatížení a zrušení iterací za sekundu.|
|[bad_target – třída](bad-target-class.md)|Tato třída popisuje výjimku vyvolanou v případě, že je bloku zasílání zpráv uveden ukazatel na cíl, který není pro prováděnou operaci platný.|
|[call – třída](call-class.md)|`call` blok pro zasílání zpráv je více zdrojů seřazená `target_block`, která při přijímání zprávy vyvolá zadanou funkci.|
|[cancellation_token – třída](cancellation-token-class.md)|Třída `cancellation_token` představuje možnost určit, zda některé operace byly vyžádány pro zrušení. Daný token lze přidružit k `task_group`, `structured_task_group`nebo `task` k poskytnutí implicitního zrušení. Může být také dotazování na zrušení nebo zaregistrováno zpětné volání pro IF a při zrušení přidruženého `cancellation_token_source`.|
|[cancellation_token_registration – třída](cancellation-token-registration-class.md)|Třída `cancellation_token_registration` představuje oznámení zpětného volání z `cancellation_token`. Pokud je metoda `register` v `cancellation_token` použita pro příjem oznámení o tom, že dojde k zrušení, je objekt `cancellation_token_registration` vrácen jako popisovač zpětného volání, aby volající mohl požadovat konkrétní zpětné volání, které již není provedeno pomocí metody `deregister`.|
|[cancellation_token_source – třída](cancellation-token-source-class.md)|Třída `cancellation_token_source` představuje schopnost zrušit některé operace, které lze zrušit.|
|[choice – třída](choice-class.md)|`choice` blok pro zasílání zpráv je vícenásobný zdroj s jedním cílovým blokem, který představuje interakci toku řízení se sadou zdrojů. Blok voleb počká, až jeden z několika zdrojů vytvoří zprávu, a bude rozšiřovat index zdroje, který zprávu vytvořil.|
|[combinable – třída](combinable-class.md)|Objekt `combinable<T>` je určen k poskytování kopií dat v soukromém vlákně, aby bylo možné provádět místní výpočty bez omezení na více vláken během paralelních algoritmů. Na konci paralelní operace mohou být dílčí výpočty privátních vláken sloučeny do konečného výsledku. Tato třída se dá použít místo sdílené proměnné a může mít za následek zlepšení výkonu, pokud by se v této sdílené proměnné mohlo nacházet hodně sporů.|
|[concurrent_priority_queue – třída](concurrent-priority-queue-class.md)|Třída `concurrent_priority_queue` je kontejner, který umožňuje více vláknům souběžně vkládat a automaticky otevírané položky. Položky jsou odebrány v pořadí podle priority, kde priorita je určena funktor zadaným jako argument šablony.|
|[concurrent_queue – třída](concurrent-queue-class.md)|Třída `concurrent_queue` je třída kontejneru sekvence, která umožňuje prvnímu přístupu k jeho prvkům. Umožňuje omezené sady bezpečných operací v rámci souběžnosti, například `push` a `try_pop`.|
|[concurrent_unordered_map – třída](concurrent-unordered-map-class.md)|Třída `concurrent_unordered_map` je kontejner bezpečné souběžnosti, který řídí proměnlivou délku sekvence prvků typu `std::pair<const K, _Element_type>`. Sekvence je reprezentována způsobem, který umožňuje připojení bezpečné souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru.|
|[concurrent_unordered_multimap – třída](concurrent-unordered-multimap-class.md)|Třída `concurrent_unordered_multimap` je kontejner bezpečné souběžnosti, který řídí proměnlivou délku sekvence prvků typu `std::pair<const K, _Element_type>`. Sekvence je reprezentována způsobem, který umožňuje připojení bezpečné souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru.|
|[concurrent_unordered_multiset – třída](concurrent-unordered-multiset-class.md)|Třída `concurrent_unordered_multiset` je kontejner bezpečné souběžnosti, který řídí proměnlivou délku sekvence elementů typu K. Sekvence je reprezentována způsobem, který umožňuje připojení bezpečné souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru.|
|[concurrent_unordered_set – třída](concurrent-unordered-set-class.md)|Třída `concurrent_unordered_set` je kontejner bezpečné souběžnosti, který řídí proměnlivou délku sekvence elementů typu K. Sekvence je reprezentována způsobem, který umožňuje připojení bezpečné souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru.|
|[concurrent_vector – třída](concurrent-vector-class.md)|Třída `concurrent_vector` je třída kontejneru sekvence, která umožňuje náhodný přístup k jakémukoli prvku. Umožňuje připojení k bezpečné souběžné souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru.|
|[Context – třída](context-class.md)|Představuje abstrakci pro kontext spuštění.|
|[context_self_unblock – třída](context-self-unblock-class.md)|Tato třída popisuje výjimku vyvolanou při volání metody `Unblock` objektu `Context` ze stejného kontextu. To by znamenalo, že pokus o odblokování samotného daného kontextu.|
|[context_unblock_unbalanced – třída](context-unblock-unbalanced-class.md)|Tato třída popisuje výjimku vyvolanou při volání `Block` a `Unblock` metody objektu `Context` nejsou správně spárovány.|
|[critical_section – třída](critical-section-class.md)|Neurčený mutex, který je výslovně informován o Concurrency Runtime.|
|[CurrentScheduler – třída](currentscheduler-class.md)|Představuje abstrakci aktuálního plánovače přidruženého k volajícímu kontextu.|
|[default_scheduler_exists – třída](default-scheduler-exists-class.md)|Tato třída popisuje výjimku vyvolanou při volání metody `Scheduler::SetDefaultSchedulerPolicy`, když výchozí Plánovač již v rámci procesu existuje.|
|[event – třída](event-class.md)|Událost ručního resetování, která je výslovně informována o Concurrency Runtime.|
|[improper_lock – třída](improper-lock-class.md)|Tato třída popisuje výjimku vyvolanou při nesprávném získání zámku.|
|[improper_scheduler_attach – třída](improper-scheduler-attach-class.md)|Tato třída popisuje výjimku vyvolanou při volání metody `Attach` u objektu `Scheduler`, který je již připojen k aktuálnímu kontextu.|
|[improper_scheduler_detach – třída](improper-scheduler-detach-class.md)|Tato třída popisuje výjimku vyvolanou při volání metody `CurrentScheduler::Detach` v kontextu, který nebyl připojen k žádnému plánovači pomocí metody `Attach` objektu `Scheduler`.|
|[improper_scheduler_reference – třída](improper-scheduler-reference-class.md)|Tato třída popisuje výjimku vyvolanou při volání metody `Reference` u objektu `Scheduler`, který se vypíná od kontextu, který není součástí tohoto plánovače.|
|[invalid_link_target – třída](invalid-link-target-class.md)|Tato třída popisuje výjimku vyvolanou při volání metody `link_target` bloku zasílání zpráv a blok zasílání zpráv se nemůže připojit k cíli. Může to být výsledek překročení počtu odkazů, které je povolený, nebo pokus o připojení konkrétního cíle dvakrát ke stejnému zdroji.|
|[invalid_multiple_scheduling – třída](invalid-multiple-scheduling-class.md)|Tato třída popisuje výjimku vyvolanou při vícenásobném naplánování `task_handle` objektu pomocí metody `run` objektu `task_group` nebo `structured_task_group` bez toho, aby bylo volání metody `wait` nebo `run_and_wait`.|
|[invalid_operation – třída](invalid-operation-class.md)|Tato třída popisuje výjimku vyvolanou při provedení neplatné operace, která není přesněji popsána jiným typem výjimky vyvolaným Concurrency Runtime.|
|[invalid_oversubscribe_operation – třída](invalid-oversubscribe-operation-class.md)|Tato třída popisuje výjimku vyvolanou při volání metody `Context::Oversubscribe` s parametrem `_BeginOversubscription` nastaveným na `false` bez předchozího volání metody `Context::Oversubscribe` s parametrem `_BeginOversubscription` nastaveným na `true`.|
|[invalid_scheduler_policy_key – třída](invalid-scheduler-policy-key-class.md)|Tato třída popisuje výjimku vyvolanou při předání neplatného nebo neznámého klíče do konstruktoru objektu `SchedulerPolicy`, nebo je-li metoda `SetPolicyValue` objektu `SchedulerPolicy`, předána klíč, který musí být změněn pomocí jiných prostředků, jako je například metoda `SetConcurrencyLimits`.|
|[invalid_scheduler_policy_thread_specification – třída](invalid-scheduler-policy-thread-specification-class.md)|Tato třída popisuje výjimku vyvolanou při pokusu o nastavení omezení souběžnosti objektu `SchedulerPolicy` tak, že hodnota `MinConcurrency` klíč je menší než hodnota klíče `MaxConcurrency`.|
|[invalid_scheduler_policy_value – třída](invalid-scheduler-policy-value-class.md)|Tato třída popisuje výjimku vyvolanou při nastavení klíče zásad objektu `SchedulerPolicy` na neplatnou hodnotu pro tento klíč.|
|[ISource – třída](isource-class.md)|Třída `ISource` je rozhraní pro všechny zdrojové bloky. Zdrojové bloky šíří zprávy do bloků `ITarget`.|
|[ITarget – třída](itarget-class.md)|Třída `ITarget` je rozhraní pro všechny cílové bloky. Cílové bloky využívají pro `ISource` bloků zprávy, které jim nabízí.|
|[join – třída](join-class.md)|`join` blok pro zasílání zpráv je jeden cíl, řazený `propagator_block`, který kombinuje zprávy typu `T` od každého ze svých zdrojů.|
|[location – třída](location-class.md)|Abstrakce fyzického umístění na hardwaru.|
|[message – třída](message-class.md)|Základní obálka zprávy obsahující datovou část dat, která se předává mezi bloky pro zasílání zpráv.|
|[message_not_found – třída](message-not-found-class.md)|Tato třída popisuje výjimku vyvolanou v případě, že blok zpráv nemůže najít požadovanou zprávu.|
|[message_processor – třída](message-processor-class.md)|Třída `message_processor` je abstraktní základní třída pro zpracování objektů `message`. Na řazení zpráv není nijak zaručeno.|
|[missing_wait – třída](missing-wait-class.md)|Tato třída popisuje výjimku vyvolanou v případě, že jsou úlohy stále naplánovány na `task_group` nebo `structured_task_group` objekt v době, kdy se spustí destruktor objektu. Tato výjimka nebude nikdy vyvolána, pokud je dosaženo destruktoru z důvodu zrušení zásobníku v důsledku výjimky.|
|[multi_link_registry – třída](multi-link-registry-class.md)|Objekt `multi_link_registry` je `network_link_registry`, který spravuje více zdrojových bloků nebo více cílových bloků.|
|[multitype_join – třída](multitype-join-class.md)|`multitype_join` blok zasílání zpráv je multi-source blok pro zasílání zpráv s jedním cílem, který kombinuje zprávy různých typů od každého ze svých zdrojů a nabízí řazenou kolekci členů kombinovaných zpráv do svých cílů.|
|[nested_scheduler_missing_detach – třída](nested-scheduler-missing-detach-class.md)|Tato třída popisuje výjimku vyvolanou při Concurrency Runtime zjistí, že jste opomíjeni zavolat metodu `CurrentScheduler::Detach` v kontextu, který je připojen k druhému plánovači pomocí metody `Attach` objektu `Scheduler`.|
|[network_link_registry – třída](network-link-registry-class.md)|Abstraktní základní třída `network_link_registry` spravuje propojení mezi zdrojovými a cílovými bloky.|
|[operation_timed_out – třída](operation-timed-out-class.md)|Tato třída popisuje výjimku vyvolanou při vypršení časového limitu operace.|
|[ordered_message_processor – třída](ordered-message-processor-class.md)|`ordered_message_processor` je `message_processor`, která umožňuje blokům zpráv zpracovávat zprávy v pořadí, v jakém byly přijaty.|
|[overwrite_buffer – třída](overwrite-buffer-class.md)|`overwrite_buffer` blok pro zasílání zpráv je více cílů, seřazené `propagator_block` s možností ukládání jedné zprávy v jednom okamžiku. Nové zprávy se přepisují dříve.|
|[progress_reporter – třída](progress-reporter-class.md)|Třída zpravodaj průběhu umožňuje vytváření sestav o průběhu konkrétního typu. Každý objekt progress_reporter je vázán na určitou asynchronní akci nebo operaci.|
|[propagator_block – třída](propagator-block-class.md)|Třída `propagator_block` je abstraktní základní třída pro bloky zpráv, které jsou zdrojem i cílem. Kombinuje funkce `source_block` i `target_block` třídy.|
|[reader_writer_lock – třída](reader-writer-lock-class.md)|Zámek zapisovače založený na frontě pro zapisovače, který se zakládá jenom s místním odstřeďováním Zámek uděluje při průběžném načítání zapisovačů přístup FIFO k modulům pro zápis a starves.|
|[ScheduleGroup – třída](schedulegroup-class.md)|Představuje abstrakci pro skupinu plánů. Skupiny plánů organizují sadu souvisejících práce, které jsou přínosy pro jejich naplánování, a to buď na konci, spuštěním jiného úkolu ve stejné skupině, než přejdete do jiné skupiny, nebo podle toho, že se ve stejné skupině spustí víc položek ve stejné skupině. Uzel NUMA nebo fyzický soket.|
|[Scheduler – třída](scheduler-class.md)|Představuje abstrakci pro Concurrency Runtime Scheduler.|
|[scheduler_not_attached – třída](scheduler-not-attached-class.md)|Tato třída popisuje výjimku vyvolanou při provedení operace, která vyžaduje, aby byl Plánovač připojen k aktuálnímu kontextu a jeden není.|
|[scheduler_resource_allocation_error – třída](scheduler-resource-allocation-error-class.md)|Tato třída popisuje výjimku vyvolanou v důsledku neúspěšného získání důležitého prostředku v Concurrency Runtime.|
|[scheduler_worker_creation_error – třída](scheduler-worker-creation-error-class.md)|Tato třída popisuje výjimku vyvolanou v důsledku selhání vytvoření kontextu spuštění pracovního procesu v Concurrency Runtime.|
|[SchedulerPolicy – třída](schedulerpolicy-class.md)|Třída `SchedulerPolicy` obsahuje sadu párů klíč/hodnota, jednu pro každý prvek zásad, která řídí chování instance Scheduleru.|
|[simple_partitioner – třída](simple-partitioner-class.md)|Třída `simple_partitioner` představuje statický segmentování rozsahu, na které prochází `parallel_for`. Dělicí metoda rozdělí rozsah na bloky dat tak, aby měl každý blok alespoň počet iterací určených velikostí bloku dat.|
|[single_assignment – třída](single-assignment-class.md)|`single_assignment` blok pro zasílání zpráv je více cílů, seřazené `propagator_block` umožňující ukládání jednoho, jednorázového `message`ho zápisu.|
|[single_link_registry – třída](single-link-registry-class.md)|Objekt `single_link_registry` je `network_link_registry`, který spravuje pouze jeden zdrojový nebo cílový blok.|
|[source_block – třída](source-block-class.md)|Třída `source_block` je abstraktní základní třída pro bloky pouze ve zdroji. Třída poskytuje základní funkce pro správu odkazů a také běžné kontroly chyb.|
|[source_link_manager – třída](source-link-manager-class.md)|Objekt `source_link_manager` spravuje zprávy blokující síťové odkazy na bloky `ISource`.|
|[static_partitioner – třída](static-partitioner-class.md)|Třída `static_partitioner` představuje statický segmentování rozsahu, na které prochází `parallel_for`. Dělicí metoda rozdělí rozsah do tolika bloků dat, kolik jsou zaměstnanci k dispozici pro Plánovač základního.|
|[structured_task_group – třída](structured-task-group-class.md)|Třída `structured_task_group` představuje vysoce strukturovaná kolekce paralelní práce. Jednotlivé paralelní úkoly lze zařadit do fronty `structured_task_group` pomocí objektů `task_handle` a počkat na jejich dokončení, nebo zrušit skupinu úloh předtím, než budou dokončeny. tím dojde k přerušení všech úloh, které nezačaly běžet.|
|[target_block – třída](target-block-class.md)|Třída `target_block` je abstraktní základní třída, která poskytuje základní funkce pro správu odkazů a kontrolu chyb pouze pro cílové bloky.|
|[task – třída (Concurrency Runtime)](task-class.md)|Knihovna PPL (Parallel Patterns Library) `task` třídy. Objekt `task` představuje práci, kterou lze provádět asynchronně a souběžně s jinými úkoly a paralelní práci vytvořenou paralelními algoritmy v Concurrency Runtime. Vytvoří výsledek typu `_ResultType` po úspěšném dokončení. Úlohy typu `task<void>` nevydávají žádný výsledek. Úkol může čekat a zrušit nezávisle na jiných úkolech. Může se také skládat s ostatními úkoly pomocí pokračování (`then`) a vzorů spojení (`when_all`) a volby (`when_any`).|
|[task_canceled – třída](task-canceled-class.md)|Tato třída popisuje výjimku vyvolanou vrstvou úloh PPL, aby se vynutilo zrušení aktuální úlohy. Je také vyvolána metodou `get()` v [úloze](task-class.md)pro zrušený úkol.|
|[task_completion_event – třída](task-completion-event-class.md)|Třída `task_completion_event` umožňuje zpozdit provádění úlohy, dokud není splněna podmínka, nebo spustit úlohu jako odpověď na externí událost.|
|[task_continuation_context – třída](task-continuation-context-class.md)|Třída `task_continuation_context` umožňuje určit, kde má být pokračování spuštěno. Tuto třídu je užitečné použít jenom z aplikace pro UWP. Pro aplikace, které nejsou prostředí Windows Runtime, je kontext provádění pokračování úlohy určený modulem runtime a nelze jej konfigurovat.|
|[task_group – třída](task-group-class.md)|Třída `task_group` představuje kolekci paralelní práce, která může být očekávána nebo zrušena.|
|[task_handle – třída](task-handle-class.md)|Třída `task_handle` představuje jednotlivé paralelní pracovní položky. Tyto pokyny zapouzdřuje a data potřebná ke spuštění nějaké práce.|
|[task_options – třída (Concurrency Runtime)](task-options-class-concurrency-runtime.md)|Představuje povolené možnosti pro vytvoření úlohy.|
|[timer – třída](timer-class.md)|`timer` blok zasílání zpráv je `source_block` s jedním cílem, který umožňuje poslat zprávu na cíl po uplynutí zadaného časového období nebo v určitých intervalech.|
|[transformer – třída](transformer-class.md)|`transformer` blok zasílání zpráv je jeden cíl, více zdrojů seřazený `propagator_block`, který může přijímat zprávy jednoho typu a je schopný ukládat neohraničený počet zpráv jiného typu.|
|[unbounded_buffer – třída](unbounded-buffer-class.md)|`unbounded_buffer` blok zasílání zpráv je více cílů, seřazené `propagator_block` umožňující ukládání neohraničeného počtu zpráv.|
|[unsupported_os – třída](unsupported-os-class.md)|Tato třída popisuje výjimku vyvolanou při použití nepodporovaného operačního systému.|

### <a name="structures"></a>Struktury

|Name|Popis|
|----------|-----------------|
|[DispatchState – struktura](dispatchstate-structure.md)|Struktura `DispatchState` slouží k přenosu stavu do metody `IExecutionContext::Dispatch`. Popisuje okolnosti, za kterých je metoda `Dispatch` vyvolána v rozhraní `IExecutionContext`.|
|[IExecutionContext – struktura](iexecutioncontext-structure.md)|Rozhraní do kontextu spuštění, který může běžet na daném virtuálním procesoru a musí být přepnuty do komutovaného kontextu.|
|[IExecutionResource – struktura](iexecutionresource-structure.md)|Abstrakce pro hardwarové vlákno.|
|[IResourceManager – struktura](iresourcemanager-structure.md)|Rozhraní pro Správce prostředků Concurrency Runtime. Toto je rozhraní, podle kterého budou schedulery komunikovat s Správce prostředků.|
|[IScheduler – struktura](ischeduler-structure.md)|Rozhraní pro abstrakci pracovního plánovače. Správce prostředků Concurrency Runtime používá toto rozhraní ke komunikaci s plánovači práce.|
|[ISchedulerProxy – struktura](ischedulerproxy-structure.md)|Rozhraní, podle kterého budou schedulery komunikovat s Správce prostředků Concurrency Runtime k vyjednání přidělení prostředků.|
|[IThreadProxy – struktura](ithreadproxy-structure.md)|Abstrakce pro vlákno provádění. V závislosti na klíči zásad `SchedulerType` plánovače, který vytvoříte, vám Správce prostředků udělí proxy vlákna, které je zajištěné buď regulárním vláknem Win32, nebo podprocesem plánovatelná (UMS) v uživatelském režimu. UMS vlákna jsou podporována v 64 operačních systémech s verzí Windows 7 a vyšší.|
|[ITopologyExecutionResource – struktura](itopologyexecutionresource-structure.md)|Rozhraní k prostředku spuštění, jak je definováno Správce prostředků.|
|[ITopologyNode – struktura](itopologynode-structure.md)|Rozhraní k uzlu topologie, jak je definováno Správce prostředků. Uzel obsahuje jeden nebo více prostředků spuštění.|
|[IUMSCompletionList – struktura](iumscompletionlist-structure.md)|Představuje seznam pro doplňování UMS. Když vlákno UMS blokuje, je určený plánovací kontext plánovače odeslán, aby bylo možné rozhodnout o tom, co naplánovat na podkladovém kořenu virtuálního procesoru v době, kdy je původní vlákno blokované. Když původní vlákno odblokuje, operační systém je zařadí do seznamu dokončení, který je přístupný prostřednictvím tohoto rozhraní. Plánovač může zadat dotaz na seznam pro doplňování v určeném kontextu plánování nebo na jakémkoli jiném místě, kde hledá práci.|
|[IUMSScheduler – struktura](iumsscheduler-structure.md)|Rozhraní pro abstrakci pracovního plánovače, které chce Správce prostředků Concurrency Runtime zaplánovatelná vlákna v uživatelském režimu (UMS). Správce prostředků toto rozhraní používá ke komunikaci s plánovači vláken UMS. Rozhraní `IUMSScheduler` dědí z rozhraní `IScheduler`.|
|[IUMSThreadProxy – struktura](iumsthreadproxy-structure.md)|Abstrakce pro vlákno provádění. Pokud chcete, aby váš Plánovač měl udělená vlákna v uživatelském režimu plánovatelná (UMS), nastavte hodnotu pro element Scheduler Policy `SchedulerKind` na `UmsThreadDefault`a implementujte rozhraní `IUMSScheduler`. UMS vlákna jsou podporována pouze v 64 operačních systémech s verzí Windows 7 a vyšší.|
|[IUMSUnblockNotification – struktura](iumsunblocknotification-structure.md)|Představuje oznámení z Správce prostředků, který proxy vlákno zablokovalo a aktivovalo návrat do určeného časového kontextu plánovače, který je odblokovaný a připravený k naplánování. Toto rozhraní je po přeplánování přidruženého kontextu spuštění, který je vrácen z metody `GetContext`, neplatné.|
|[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)|Abstrakce pro hardwarové vlákno, ve kterém se dá spustit proxy vlákna.|
|[scheduler_interface – struktura](scheduler-interface-structure.md)|Rozhraní Scheduleru|
|[scheduler_ptr – struktura (Concurrency Runtime)](scheduler-ptr-structure-concurrency-runtime.md)|Představuje ukazatel na Plánovač. Tato třída existuje, aby povolovala specifikaci sdílené životnosti pomocí shared_ptr nebo pouze jednoduchého odkazu pomocí nezpracovaného ukazatele.|

### <a name="enumerations"></a>Výčty

|Name|Popis|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|Platné stavy pro `agent`.|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Typy událostí, které lze trasovat pomocí funkce trasování nabízené knihovnou agentů|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Typy událostí, které lze trasovat pomocí funkce trasování, které nabízí Concurrency Runtime.|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Příznaky trasování pro typy událostí|
|[CriticalRegionType –](concurrency-namespace-enums.md#criticalregiontype)|Typ kritické oblasti, ke které je kontext uvnitř.|
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Používá se v zásadách `DynamicProgressFeedback` k popisu, zda budou prostředky pro Plánovač znovu vyrovnávatelné podle statistických informací shromážděných z plánovače nebo pouze na základě virtuálních procesorů, které přecházejí do nečinného stavu prostřednictvím volání metod `Activate` a `Deactivate` na `IVirtualProcessorRoot` rozhraní. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md#policyelementkey).|
|[join_type](concurrency-namespace-enums.md#join_type)|Typ `join`ového bloku pro zasílání zpráv.|
|[message_status](concurrency-namespace-enums.md#message_status)|Platné odpovědi na nabídku objektu `message` do bloku.|
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Klíče zásad popisující aspekty chování plánovače. Jednotlivé prvky zásad jsou popsány dvojicí klíč-hodnota. Další informace o zásadách plánovače a jejich vlivu na plánovače najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|Používá se zásadami `SchedulerKind` k popisu typu vláken, které by měl Plánovač využít pro podkladové kontexty provádění. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md#policyelementkey).|
|[SchedulingProtocolType –](concurrency-namespace-enums.md#schedulingprotocoltype)|Používá se v zásadách `SchedulingProtocol` k popisu, který algoritmus plánování bude pro Plánovač využíván. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md#policyelementkey).|
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Slouží k označení stavu, ve kterém se nachází proxy vlákna, pokud je spuštěný kontext spolupráce, přepnutí na jiný proxy vlákna.|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Popisuje stav spuštění objektu `task_group` nebo `structured_task_group`. Hodnota tohoto typu je vrácena mnoha metodami, které čekají na dokončení úloh naplánovaných na skupinu úloh.|
|[WinRTInitializationType –](concurrency-namespace-enums.md#winrtinitializationtype)|Používá se v zásadách `WinRTInitialization` k popisu, jestli a jak se prostředí Windows Runtime inicializuje na vláknech Scheduleru pro aplikaci, která běží na operačních systémech s verzí Windows 8 nebo vyšší. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md#policyelementkey).|

### <a name="functions"></a>Funkce

|Name|Popis|
|----------|-----------------|
|[Funkce alokace](concurrency-namespace-functions.md#alloc)|Přidělí blok paměti, která je určená od Concurrency Runtimeho subalokátoru pro ukládání do mezipaměti.|
|[asend – funkce](concurrency-namespace-functions.md#asend)|Přetížené Operace asynchronního odeslání, která Naplánuje úkol, aby rozšířil data do cílového bloku.|
|[cancel_current_task Function](concurrency-namespace-functions.md#cancel_current_task)|Zruší právě prováděnou úlohu. Tato funkce může být volána z těla úkolu, aby přerušila provádění úlohy a způsobila, že vstoupí do stavu `canceled`.<br /><br /> Nejedná se o podporovaný scénář pro volání této funkce, pokud nejste v těle `task`. V důsledku toho dojde k nedefinovanému chování, jako je například selhání nebo zablokování aplikace.|
|[create_async Function](concurrency-namespace-functions.md#create_async)|Vytvoří asynchronní konstrukci prostředí Windows Runtime na základě uživatelem zadaného výrazu lambda nebo objektu funkce. Návratový typ `create_async` je jedna z `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`nebo `IAsyncOperationWithProgress<TResult, TProgress>^` na základě signatury lambda předané metodě.|
|[create_task funkce](concurrency-namespace-functions.md#create_task)|Přetížené Vytvoří objekt [úlohy](task-class.md) PPL. `create_task` lze použít všude, kde byste použili konstruktor úlohy. Je poskytován hlavně pro pohodlí, protože umožňuje použití klíčového slova `auto` při vytváření úloh.|
|[CreateResourceManager Function](concurrency-namespace-functions.md#createresourcemanager)|Vrátí rozhraní, které představuje instanci typu Singleton Správce prostředků Concurrency Runtime. Správce prostředků zodpovídá za přiřazení prostředků plánovačům, které chtějí vzájemně spolupracovat.|
|[DisableTracing – – funkce](concurrency-namespace-functions.md#disabletracing)|Zakáže trasování v Concurrency Runtime. Tato funkce je zastaralá, protože trasování ETW je ve výchozím nastavení neregistrované.|
|[EnableTracing – – funkce](concurrency-namespace-functions.md#enabletracing)|Povolí trasování v Concurrency Runtime. Tato funkce je zastaralá, protože trasování ETW je teď ve výchozím nastavení zapnuté.|
|[Free – funkce](concurrency-namespace-functions.md#free)|Uvolní blok paměti dříve přidělený `Alloc` metodou do meziConcurrency Runtime ukládání do mezipaměti.|
|[Funkce get_ambient_scheduler (Concurrency Runtime)](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId – – funkce](concurrency-namespace-functions.md#getexecutioncontextid)|Vrací jedinečný identifikátor, který lze přiřadit kontextu spuštění, který implementuje rozhraní `IExecutionContext`.|
|[GetOSVersion – – funkce](concurrency-namespace-functions.md#getosversion)|Vrátí verzi operačního systému.|
|[GetProcessorCount – – funkce](concurrency-namespace-functions.md#getprocessorcount)|Vrátí počet hardwarových vláken v podkladovém systému.|
|[GetProcessorNodeCount – – funkce](concurrency-namespace-functions.md#getprocessornodecount)|Vrátí počet uzlů NUMA nebo balíčků procesorů v podkladovém systému.|
|[GetSchedulerId – – funkce](concurrency-namespace-functions.md#getschedulerid)|Vrátí jedinečný identifikátor, který lze přiřadit k plánovači, který implementuje rozhraní `IScheduler`.|
|[interruption_point Function](concurrency-namespace-functions.md#interruption_point)|Vytvoří bod přerušení pro zrušení. Pokud probíhá zrušení v kontextu, ve kterém je tato funkce volána, vyvolá se vnitřní výjimka, která přeruší provádění aktuálně prováděné paralelní práce. Pokud zrušení neprobíhá, funkce neprovede žádnou akci.|
|[is_current_task_group_canceling funkce](concurrency-namespace-functions.md#is_current_task_group_canceling)|Vrací údaj o tom, zda je skupina úloh, která aktuálně provádí inlineing v aktuálním kontextu, v průběhu aktivního zrušení (nebo bude brzy). Všimněte si, že pokud v aktuálním kontextu není žádná skupina úloh aktuálně prováděna s vloženým kontextem, bude vrácena `false`.|
|[make_choice funkce](concurrency-namespace-functions.md#make_choice)|Přetížené Vytvoří `choice` blok pro zasílání zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dvou nebo více vstupních zdrojů.|
|[make_greedy_join Function](concurrency-namespace-functions.md#make_greedy_join)|Přetížené Vytvoří `greedy multitype_join` blok pro zasílání zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dvou nebo více vstupních zdrojů.|
|[make_join funkce](concurrency-namespace-functions.md#make_join)|Přetížené Vytvoří `non_greedy multitype_join` blok pro zasílání zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dvou nebo více vstupních zdrojů.|
|[make_task funkce](concurrency-namespace-functions.md#make_task)|Výrobní metoda pro vytvoření objektu `task_handle`.|
|[parallel_buffered_sort Function](concurrency-namespace-functions.md#parallel_buffered_sort)|Přetížené Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle kritéria řazení, které je určeno binárním predikátem paralelně. Tato funkce je sémanticky podobná `std::sort` v tom, že se jedná o porovnání, nestabilní, místní řazení s výjimkou toho, že potřebuje `O(n)` dodatečné místo a vyžaduje výchozí inicializaci pro prvky, které jsou setříděny.|
|[parallel_for funkce](concurrency-namespace-functions.md#parallel_for)|Přetížené `parallel_for` iterovat na určitou škálu indexů a v každé iteraci spustí uživatelsky zadanou funkci, paralelně.|
|[parallel_for_each Function](concurrency-namespace-functions.md#parallel_for_each)|Přetížené `parallel_for_each` aplikuje zadanou funkci na každý prvek v rozsahu paralelně. Je sémanticky ekvivalentní funkci `for_each` v oboru názvů `std`, s tím rozdílem, že iterace nad prvky je prováděna paralelně a pořadí iterace není specifikováno. Argument `_Func` musí podporovat operátor volání funkce ve formě `operator()(T)` kde parametr `T` je typ položky kontejneru, na který se provádí iterace.|
|[parallel_invoke funkce](concurrency-namespace-functions.md#parallel_invoke)|Přetížené Spustí objekty funkce, které jsou zadány jako parametry paralelně, a zablokuje, dokud se nedokončí jejich spuštění. Každý objekt funkce může být výraz lambda, ukazatel na funkci nebo libovolný objekt, který podporuje operátor volání funkce s podpisem `void operator()()`.|
|[parallel_radixsort Function](concurrency-namespace-functions.md#parallel_radixsort)|Přetížené Uspořádá prvky v zadaném rozsahu do nesestupného pořadí pomocí algoritmu řazení číselné řady. Toto je stabilní funkce řazení, která vyžaduje funkci projekce, která může prvky projektu seřadit do unsigned integer klíčů jako. Pro prvky, které jsou řazeny, je vyžadována výchozí inicializace.|
|[parallel_reduce Function](concurrency-namespace-functions.md#parallel_reduce)|Přetížené Vypočítá součet všech prvků v zadaném rozsahu tím, že provede výpočet po sobě jdoucích částečných součtů, nebo vypočítá výsledek po sobě jdoucích částečných výsledků podobně jako u paralelního použití zadané binární operace, která je jiná než součet. `parallel_reduce` je sémanticky podobná `std::accumulate`, s tím rozdílem, že vyžaduje asociativní binární operaci a vyžaduje hodnotu identity namísto počáteční hodnoty.|
|[parallel_sort funkce](concurrency-namespace-functions.md#parallel_sort)|Přetížené Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle kritéria řazení, které je určeno binárním predikátem paralelně. Tato funkce je sémanticky podobná `std::sort` v tom, že se jedná o porovnání nestabilního a místního řazení na místě.|
|[parallel_transform Function](concurrency-namespace-functions.md#parallel_transform)|Přetížené Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a kopíruje návratové hodnoty objektu Functions do cílového rozsahu paralelně. Tato funkce je sémanticky rovnocenná `std::transform`.|
|[Receive – funkce](concurrency-namespace-functions.md#receive)|Přetížené Obecná implementace příjmu, která umožňuje kontextu počkat na data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijaty.|
|[run_with_cancellation_token Function](concurrency-namespace-functions.md#run_with_cancellation_token)|Spustí objekt funkce okamžitě a synchronně v kontextu daného tokenu zrušení.|
|[send – funkce](concurrency-namespace-functions.md#send)|Přetížené Operace synchronního odeslání, která čeká, až cíl zprávu buď přijme, nebo odmítne.|
|[Funkce set_ambient_scheduler (Concurrency Runtime)](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[set_task_execution_resources Function](concurrency-namespace-functions.md#set_task_execution_resources)|Přetížené Omezí prostředky spouštění používané Concurrency Runtime interními pracovními vlákny do zadané sady vztahů.<br /><br /> Volání této metody je platné pouze před vytvořením Správce prostředků nebo mezi dvěma životnostmi Správce prostředků. Dá se vyvolat víckrát, dokud Správce prostředků v době vyvolání neexistují. Po nastavení omezení spřažení zůstane v platnosti, dokud nebude další platné volání metody `set_task_execution_resources`.<br /><br /> Zadaná maska spřažení nemusí být podmnožinou masky spřažení procesu. Spřažení procesů bude v případě potřeby aktualizováno.|
|[swap – funkce](concurrency-namespace-functions.md#swap)|Vyměňuje prvky dvou `concurrent_vector` objektů.|
|[Funkce task_from_exception (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_exception)||
|[Funkce task_from_result (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_result)||
|[Trace_agents_register_name funkce](concurrency-namespace-functions.md#trace_agents_register_name)|Přidruží daný název k bloku zprávy nebo agentovi v trasování ETW.|
|[try_receive funkce](concurrency-namespace-functions.md#try_receive)|Přetížené Obecná implementace try-Receive, která umožňuje kontextu vyhledat data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijaty. Pokud data nejsou připravena, bude metoda vracet hodnotu false.|
|[Wait – funkce](concurrency-namespace-functions.md#wait)|Pozastaví aktuální kontext na určenou dobu.|
|[when_all funkce](concurrency-namespace-functions.md#when_all)|Vytvoří úkol, který se úspěšně dokončí po úspěšném dokončení všech úloh zadaných jako argumenty.|
|[when_any funkce](concurrency-namespace-functions.md#when_any)|Přetížené Vytvoří úkol, který se úspěšně dokončí, když se kterákoli z úkolů dodaných jako argumenty úspěšně dokončí.|

### <a name="operators"></a>Operátory

|Name|Popis|
|----------|-----------------|
|[operator!=](concurrency-namespace-operators.md#operator_neq)|Testuje, zda `concurrent_vector` objekt na levé straně operátoru není roven objektu `concurrent_vector` na pravé straně.|
|[operátor & &](concurrency-namespace-operators.md#operator_amp_amp)|Přetížené Vytvoří úkol, který se úspěšně dokončí, když se obě úlohy dodají jako argumenty úspěšně dokončí.|
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Přetížené Vytvoří úkol, který se úspěšně dokončí, když se kterákoli z úkolů dodaných jako argumenty úspěšně dokončí.|
|[operátor <](concurrency-namespace-operators.md#operator_lt)|Testuje, zda je objekt `concurrent_vector` na levé straně operátoru menší než objekt `concurrent_vector` na pravé straně.|
|[operátor < =](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, zda je objekt `concurrent_vector` na levé straně operátoru menší než nebo roven `concurrent_vector`mu objektu na pravé straně.|
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|Testuje, zda je objekt `concurrent_vector` na levé straně operátoru roven objektu `concurrent_vector` na pravé straně.|
|[operátor >](concurrency-namespace-operators.md#operator_gt)|Testuje, zda je objekt `concurrent_vector` na levé straně operátoru větší než objekt `concurrent_vector` na pravé straně.|
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, zda je objekt `concurrent_vector` na levé straně operátoru větší než nebo roven `concurrent_vector`mu objektu na pravé straně.|

### <a name="constants"></a>Konstanty

|Name|Popis|
|----------|-----------------|
|[Agenteventguid –](concurrency-namespace-constants1.md#agenteventguid)|Identifikátor GUID kategorie ({B9B5B78C-0713-4898-A21A-C67949DCED07}) popisující události ETW, které vyvolala knihovna agentů v Concurrency Runtime.|
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|Identifikátor GUID kategorie popisující události ETW spouštěné Concurrency Runtime, které přímo souvisejí s rutinní nebo úkoly.|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Identifikátor GUID zprostředkovatele ETW pro Concurrency Runtime.|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Určuje podporu rozhraní Správce prostředků definovaného v aplikaci Visual Studio 2010.|
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|Identifikátor GUID kategorie popisující události ETW, které jsou vyvolány Concurrency Runtime, které nejsou speciálně popsané jinou kategorií.|
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|Identifikátor GUID kategorie popisující události ETW spouštěné Concurrency Runtime, které přímo souvisejí s kontexty.|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Hodnota označující, že čas čekání by neměl nikdy trvat.|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Hodnota označující, že čekání vypršel časový limit.|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Speciální hodnota pro klíč zásady `ContextPriority` označující, že priorita vlákna všech kontextů v Plánovači musí být stejná jako u vlákna, které vytvořil Plánovač.|
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|Identifikátor GUID kategorie popisující události ETW spouštěné Concurrency Runtime, které přímo souvisejí s zámky.|
|[MaxExecutionResources –](concurrency-namespace-constants1.md#maxexecutionresources)|Speciální hodnota klíčů zásad `MinConcurrency` a `MaxConcurrency` Ve výchozím nastavení se jedná o počet hardwarových vláken v počítači při absenci jiných omezení.|
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Identifikátor GUID kategorie popisující události ETW, které jsou vyvolány Concurrency Runtime, které přímo souvisejí s používáním funkce `parallel_for_each`.|
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|Identifikátor GUID kategorie popisující události ETW, které jsou vyvolány Concurrency Runtime, které přímo souvisejí s používáním funkce `parallel_for`.|
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Identifikátor GUID kategorie popisující události ETW, které jsou vyvolány Concurrency Runtime, které přímo souvisejí s používáním funkce `parallel_invoke`.|
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|Identifikátor GUID kategorie popisující události ETW, které jsou vyvolány Concurrency Runtime, které přímo souvisejí s Resource Managerem.|
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|Identifikátor GUID kategorie popisující události ETW spouštěné Concurrency Runtime, které přímo souvisejí se skupinami plánů|
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|Identifikátor GUID kategorie popisující události ETW spouštěné Concurrency Runtime, které přímo souvisejí s aktivitou Scheduleru.|
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Identifikátor GUID kategorie popisující události ETW spouštěné Concurrency Runtime, které přímo souvisejí s virtuálními procesory.|

## <a name="requirements"></a>Požadavky

**Header:** agents.h, concrt.h, concrtrm.h, concurrent_priority_queue.h, concurrent_queue.h, concurrent_unordered_map.h, concurrent_unordered_set.h, concurrent_vector.h, internal_concurrent_hash.h, internal_split_ordered_list.h, ppl.h, pplcancellation_token.h, pplconcrt.h, pplinterface.h, ppltasks.h

## <a name="see-also"></a>Viz také:

[Odkazy](reference-concurrency-runtime.md)
