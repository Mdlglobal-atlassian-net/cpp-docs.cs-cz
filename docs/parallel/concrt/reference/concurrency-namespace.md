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
ms.openlocfilehash: aa2fe7dedd1c7e1a8b5a72e01508b4201bd72a7d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160068"
---
# <a name="concurrency-namespace"></a>concurrency – obor názvů

`Concurrency` Obor názvů obsahuje třídy a funkce, které umožňují přístup k modulu Concurrency Runtime, souběžnému programovacímu rámci pro jazyk C++. Další informace najdete v tématu [Concurrency Runtime](../../../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntaxe

```
namespace concurrency;
```

## <a name="members"></a>Členové

### <a name="typedefs"></a>Typedefs

|Název|Popis|
|----------|-----------------|
|`runtime_object_identity`|Každá instance zpráva má identitu, která ji následuje klonovat a předány mezi součásti zasílání zpráv. To nemůže být adresa objekt zprávy.|
|`task_status`|Typ, který představuje konečný stav úkolu. Platné hodnoty jsou `completed` a `canceled`.|
|`TaskProc`|Základní abstrakci pro úlohu, definovaná jako `void (__cdecl * TaskProc)(void *)`. A `TaskProc` je volána k vyvolání tělo úkolu.|
|`TaskProc_t`|Základní abstrakci pro úlohu, definovaná jako `void (__cdecl * TaskProc_t)(void *)`. A `TaskProc` je volána k vyvolání tělo úkolu.|

### <a name="classes"></a>Třídy

|Název|Popis|
|----------|-----------------|
|[affinity_partitioner – třída](affinity-partitioner-class.md)|`affinity_partitioner` Třída je podobně jako `static_partitioner` třídy, ale zvyšuje přidružení mezipaměti podle svého výběru mapování podrozsahů na pracovních vláken. To výrazně zvýšit výkon při smyčku znovu provést prostřednictvím stejné datové sady, a data vejde se do mezipaměti. Všimněte si, že stejné `affinity_partitioner` objekt musí být použit s dalších iteracích paralelní smyčky, který se spouští nad konkrétní datové sady, abyste využili výhod data lokality.|
|[agent – třída](agent-class.md)|Třída určena pro použití jako základní třída pro všechny agenty nezávislé. Používá se k skrýt stav z další agenty a komunikovat pomocí předávání zpráv.|
|[auto_partitioner – třída](auto-partitioner-class.md)|`auto_partitioner` Třída představuje výchozí metodu `parallel_for`, `parallel_for_each` a `parallel_transform` použít při vytváření oddílů rozsah se Iteruje přes. Tato metoda dělení employes rozsahu zcizování pro vyrovnávání zatížení také na iterovat zrušení.|
|[bad_target – třída](bad-target-class.md)|Tato třída popisuje výjimku vyvolanou při blok zpráv je dán ukazatel cíl, který není platný pro právě prováděnou operaci.|
|[call – třída](call-class.md)|A `call` blok zpráv je zdroj více seřazené `target_block` zadanou funkci, která vyvolá při přijímání zprávy.|
|[cancellation_token – třída](cancellation-token-class.md)|`cancellation_token` Třída představuje možnost zjistit, zda některé operace požadují zrušení. Daný token lze přidružit `task_group`, `structured_task_group`, nebo `task` a poskytnout implicitní zrušení. Také ho můžete testovat na zrušení nebo mít registrace zpětného volání pro případ přidružený `cancellation_token_source` se zruší.|
|[cancellation_token_registration – třída](cancellation-token-registration-class.md)|`cancellation_token_registration` Třída představuje zpětné volání upozornění z `cancellation_token`. Když `register` metodu na `cancellation_token` slouží k přijímání oznámení tom, kdy kde zrušení dojde, `cancellation_token_registration` objekt je vrácen jako popisovač pro zpětné volání tak, aby volající mohl požadovat konkrétní zpětné volání již nebude provedeno pomocí `deregister` metody.|
|[cancellation_token_source – třída](cancellation-token-source-class.md)|`cancellation_token_source` Třída představuje schopnost zrušit zrušitelnou operaci.|
|[choice – třída](choice-class.md)|A `choice` blok zpráv je více zdroje, jeden cílový blok, který představuje tok řízení interakce sadu zdrojů. Výběr bloku počká na některou z několika zdrojů do výsledné zprávu a rozšíří index zdroj, který vytvořil zprávu.|
|[combinable – třída](combinable-class.md)|`combinable<T>` Objektu je určená k zajištění vlákno soukromé kopie dat, provádět výpočty bez zámku thread local dílčí během paralelních algoritmů. Na konci paralelní operace můžete vlákno privátní dílčí výpočty pak sloučen do konečný výsledek. Tato třída je možné použít místo sdílené proměnné a může vést k zlepšení výkonu, pokud by jinak byly velké množství kolizí v dané sdílené proměnné.|
|[concurrent_priority_queue – třída](concurrent-priority-queue-class.md)|`concurrent_priority_queue` Třída je kontejner, který umožňuje více vláken současně nabízená oznámení a pop položek. Položky jsou otevřené v pořadí podle priority, kde je určen priority funktor zadaný jako argument šablony.|
|[concurrent_queue – třída](concurrent-queue-class.md)|`concurrent_queue` Třída je sekvence kontejner – třída, která umožňuje first-in, FIFO přístup k jeho prvkům. Umožňuje omezenou sadu operace bezpečné na souběžnosti, jako například `push` a `try_pop`.|
|[concurrent_unordered_map – třída](concurrent-unordered-map-class.md)|`concurrent_unordered_map` Třídy je kontejner bezpečné souběžnosti, který řídí různé délky sekvence elementů typu `std::pair<const K, _Element_type>`. Sekvence je reprezentována způsobem, který umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.|
|[concurrent_unordered_multimap – třída](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap` Třídy je kontejner bezpečné souběžnosti, který řídí různé délky sekvence elementů typu `std::pair<const K, _Element_type>`. Sekvence je reprezentována způsobem, který umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.|
|[concurrent_unordered_multiset – třída](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset` Třídy je kontejner bezpečné souběžnosti, který řídí různé délky sekvence elementů typu K. Sekvence je reprezentována způsobem, který umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.|
|[concurrent_unordered_set – třída](concurrent-unordered-set-class.md)|`concurrent_unordered_set` Třídy je kontejner bezpečné souběžnosti, který řídí různé délky sekvence elementů typu K. Sekvence je reprezentována způsobem, který umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.|
|[concurrent_vector – třída](concurrent-vector-class.md)|`concurrent_vector` Třídy je třída kontejneru sekvence, která umožňuje náhodný přístup k libovolnému prvku. Umožňuje bezpečné na souběžnosti, přístup k prvkům, přístup k iterátoru a operace procházení iterátoru připojit.|
|[Context – třída](context-class.md)|Představuje abstrakci pro kontext spuštění.|
|[context_self_unblock – třída](context-self-unblock-class.md)|Tato třída popisuje výjimku vyvolána, když `Unblock` metodu `Context` objektu je volána z stejný kontext. Pokus o by jít odblokujete samotné podle daného kontextu.|
|[context_unblock_unbalanced – třída](context-unblock-unbalanced-class.md)|Tato třída popisuje výjimku vyvolanou při volání `Block` a `Unblock` metody `Context` nejsou správně spárované objektu.|
|[critical_section – třída](critical-section-class.md)|Bez reentrant objektu mutex, na které je explicitně vědoma souběžnosti modulu runtime.|
|[CurrentScheduler – třída](currentscheduler-class.md)|Představuje abstrakci pro aktuální Plánovač přidružený kontext volání.|
|[default_scheduler_exists – třída](default-scheduler-exists-class.md)|Tato třída popisuje výjimku vyvolána, když `Scheduler::SetDefaultSchedulerPolicy` metoda se volá, když je výchozím plánovačem již existuje v rámci procesu.|
|[event – třída](event-class.md)|Ruční obnovení události, která je explicitně vědoma souběžnosti modulu runtime.|
|[improper_lock – třída](improper-lock-class.md)|Tato třída popisuje výjimku vyvolanou při nesprávně získán zámek.|
|[improper_scheduler_attach – třída](improper-scheduler-attach-class.md)|Tato třída popisuje výjimku vyvolána, když `Attach` metoda je volána na `Scheduler` objekt, který je již připojen k aktuálním kontextu.|
|[improper_scheduler_detach – třída](improper-scheduler-detach-class.md)|Tato třída popisuje výjimku vyvolána, když `CurrentScheduler::Detach` metoda je volána u objektu context, která nebyla připojena k žádné scheduleru pomocí `Attach` metodu `Scheduler` objektu.|
|[improper_scheduler_reference – třída](improper-scheduler-reference-class.md)|Tato třída popisuje výjimku vyvolána, když `Reference` metoda je volána na `Scheduler` objekt, který se vypíná, z kontextu, který není součástí tohoto plánovače.|
|[invalid_link_target – třída](invalid-link-target-class.md)|Tato třída popisuje výjimku vyvolána, když `link_target` je volána metoda blok zpráv a blok zpráv se nejde připojit k cíli. To může být vyšší než počet odkazů, které je povoleno blok zpráv nebo pokus o odkaz konkrétní cílovou dvakrát ke stejnému zdroji.|
|[invalid_multiple_scheduling – třída](invalid-multiple-scheduling-class.md)|Tato třída popisuje výjimku vyvolána, když `task_handle` objekt je naplánované vícekrát pomocí `run` metodu `task_group` nebo `structured_task_group` objekt bez opětovné volání na buď `wait` nebo `run_and_wait` metody.|
|[invalid_operation – třída](invalid-operation-class.md)|Tato třída popisuje výjimku vyvolanou při provádění neplatné operace, která není přesněji popsána jako jiný typ výjimky vyvolané modulem Runtime souběžnost.|
|[invalid_oversubscribe_operation – třída](invalid-oversubscribe-operation-class.md)|Tato třída popisuje výjimku vyvolána, když `Context::Oversubscribe` metoda je volána `_BeginOversubscription` parametr nastaven na `false` bez předchozího volání `Context::Oversubscribe` metodu s `_BeginOversubscription` parametr nastaven na `true`.|
|[invalid_scheduler_policy_key – třída](invalid-scheduler-policy-key-class.md)|Tato třída popisuje výjimku vyvolanou při neplatný nebo je předán neznámý klíč `SchedulerPolicy` konstruktor objektu nebo `SetPolicyValue` metodu `SchedulerPolicy` objekt je předán klíč, který musí být změněno pomocí jiným způsobem, jako `SetConcurrencyLimits` – metoda.|
|[invalid_scheduler_policy_thread_specification – třída](invalid-scheduler-policy-thread-specification-class.md)|Tato třída popisuje výjimku vyvolanou při pokusu o nastavení omezení souběžnosti `SchedulerPolicy` objektu tak, aby hodnota `MinConcurrency` klíč je menší než hodnota `MaxConcurrency` klíč.|
|[invalid_scheduler_policy_value – třída](invalid-scheduler-policy-value-class.md)|Tato třída popisuje výjimku vyvolanou při klíč zásady `SchedulerPolicy` objektu je nastavena na neplatnou hodnotu pro daný klíč.|
|[ISource – třída](isource-class.md)|`ISource` Třídy je rozhraní pro všechny zdrojové bloky. Zdrojové bloky šíření zpráv `ITarget` bloky.|
|[ITarget – třída](itarget-class.md)|`ITarget` Třídy je rozhraní pro všechny cílové bloky. Cílovým blokům využívat zprávy, nabízí jim `ISource` bloky.|
|[join – třída](join-class.md)|A `join` blok zpráv je jeden cíl, více zdroje, seřazený `propagator_block` který spojuje dohromady zprávy typu `T` ze všech zdrojů.|
|[location – třída](location-class.md)|Abstrakce fyzického umístění na hardwaru.|
|[message – třída](message-class.md)|Obálky základní zprávy obsahující datovou část předávaný mezi bloky zasílání zpráv.|
|[message_not_found – třída](message-not-found-class.md)|Tato třída popisuje výjimku vyvolanou při blok zpráv se nepodařilo najít požadovaný zprávu.|
|[message_processor – třída](message-processor-class.md)|`message_processor` Třída je abstraktní základní třída pro zpracování `message` objekty. Neexistuje žádná záruka na pořadí zpráv.|
|[missing_wait – třída](missing-wait-class.md)|Tato třída popisuje výjimku vyvolanou při stále naplánované úlohy `task_group` nebo `structured_task_group` objektu v době tento objekt destruktor. Tato výjimka bude vyvolána nikdy destruktor při dosažení z důvodu výjimky v důsledku uvolnění zásobníku.|
|[multi_link_registry – třída](multi-link-registry-class.md)|`multi_link_registry` Je objekt `network_link_registry` , který spravuje více zdrojových bloků nebo více cílových bloků.|
|[multitype_join – třída](multitype-join-class.md)|A `multitype_join` blok zpráv je více zdroje, jeden cílový blok zpráv, který spojuje dohromady zpráv různých typů ze všech zdrojů a nabízí se řazená kolekce členů kombinované zprávy do cíle.|
|[nested_scheduler_missing_detach – třída](nested-scheduler-missing-detach-class.md)|Tato třída popisuje výjimku vyvolanou při modulu Runtime souběžnosti zjistí, že opominul volání `CurrentScheduler::Detach` metody u objektu context, který připojuje k druhé pomocí plánovače `Attach` metodu `Scheduler` objektu.|
|[network_link_registry – třída](network-link-registry-class.md)|`network_link_registry` Abstraktní základní třída spravuje propojení mezi zdrojovými a cílovými bloky.|
|[operation_timed_out – třída](operation-timed-out-class.md)|Tato třída popisuje výjimku vyvolanou při vypršel časový limit operace.|
|[ordered_message_processor – třída](ordered-message-processor-class.md)|`ordered_message_processor` Je `message_processor` , která umožňuje blokům zpráv zpracovávat zprávy v pořadí, v jakém byly přijaty.|
|[overwrite_buffer – třída](overwrite-buffer-class.md)|`overwrite_buffer` Je více cílový blok zpráv více zdroje, seřazený `propagator_block` umožňující ukládání do jedné zprávy najednou. Nové zprávy přepsat dříve vlastněnou značky.|
|[progress_reporter – třída](progress-reporter-class.md)|Třída zpravodaj pokroku umožňuje vykazování průběhu oznámení určitého typu. Každý objekt progress_reporter je vázán na konkrétní asynchronní akci nebo operaci.|
|[propagator_block – třída](propagator-block-class.md)|`propagator_block` Třída je abstraktní základní třída pro bloky zpráv, které jsou zdrojovém i cílovém. Kombinuje funkce i `source_block` a `target_block` třídy.|
|[reader_writer_lock – třída](reader-writer-lock-class.md)|Zapisovač předvoleb zámek na základě fronty čtení a zápis s místní pouze na otáčejících se. Zámek pro autory uděluje nejprve – první out (FIFO) přístup a nepřetržitě, ubírá čtenáři průběžné zatížení zapisovačů.|
|[ScheduleGroup – třída](schedulegroup-class.md)|Představuje abstrakci pro skupinu plánování. Skupiny plánování organizují sadu souvisejících prací, které mají výhody z plánovány blízko sebe, buď časově, prováděním jiné úlohy ve stejné skupině před přesunutím do jiné skupiny, nebo prostorově, prováděním více položek ve stejné skupině na stejném Uzel NUMA nebo fyzickém soketu.|
|[Scheduler – třída](scheduler-class.md)|Představuje abstrakci pro Plánovač Concurrency Runtime.|
|[scheduler_not_attached – třída](scheduler-not-attached-class.md)|Tato třída popisuje výjimku vyvolána, když probíhá operace vyžadující plánovače bude připojený k aktuálnímu kontextu a není spuštěná.|
|[scheduler_resource_allocation_error – třída](scheduler-resource-allocation-error-class.md)|Tato třída popisuje výjimku vyvolána, protože se nepodařilo získat důležitých prostředků v modulu Runtime souběžnosti.|
|[scheduler_worker_creation_error – třída](scheduler-worker-creation-error-class.md)|Tato třída popisuje výjimku vyvolanou z důvodu selhání při vytváření kontextu spuštění pracovního procesu v modulu Runtime souběžnosti.|
|[SchedulerPolicy – třída](schedulerpolicy-class.md)|`SchedulerPolicy` Třída obsahuje sadu párů klíč/hodnota, jeden pro každý prvek zásad, které řídí chování instance plánovače.|
|[simple_partitioner – třída](simple-partitioner-class.md)|`simple_partitioner` Třída reprezentuje statické dělení provést iteraci přes podle rozsahu `parallel_for`. Dělicí rozsahu rozdělí do bloků dat tak, aby měl každý blok minimální počet iterací určená velikost deduplikačního bloku dat.|
|[single_assignment – třída](single-assignment-class.md)|A `single_assignment` je více cílový blok zpráv více zdroje, seřazený `propagator_block` umožňující ukládání jediné, zápis – po `message`.|
|[single_link_registry – třída](single-link-registry-class.md)|`single_link_registry` Je objekt `network_link_registry` , který spravuje pouze jeden blok zdroje nebo cíle.|
|[source_block – třída](source-block-class.md)|`source_block` Třída je abstraktní základní třída pro pouze zdrojové bloky. Třída poskytuje funkce správy základní odkaz jako dobře běžné kontroly chyb.|
|[source_link_manager – třída](source-link-manager-class.md)|`source_link_manager` Objekt spravuje zasílání zpráv bloku síťová propojení k `ISource` bloky.|
|[static_partitioner – třída](static-partitioner-class.md)|`static_partitioner` Třída reprezentuje statické dělení provést iteraci přes podle rozsahu `parallel_for`. Dělicí rozdělí rozsah tolik bloky dat jsou k dispozici Plánovač inteligentním pracovních procesů.|
|[structured_task_group – třída](structured-task-group-class.md)|`structured_task_group` Třída reprezentuje kolekci vysoce strukturovaná paralelní práce. Můžete fronty jednotlivých paralelních úloh `structured_task_group` pomocí `task_handle` objekty a počkat na jejich dokončení nebo zrušení skupiny úloh před dokončením provádění, která ukončí všechny úkoly, které nebyly začal spuštění.|
|[target_block – třída](target-block-class.md)|`target_block` Třída je abstraktní základní třídu, která poskytuje funkce pro správu základní odkaz a kontroly chyb pro cíl pouze blokuje.|
|[task – třída (Concurrency Runtime)](task-class.md)|Knihovna paralelních vzorů (PPL) `task` třídy. A `task` objekt představuje práci, kterou lze provádět asynchronně a současně další úkoly a paralelní práci vytvořeno paralelní algoritmy v modulu Runtime souběžnosti. Vygeneruje výsledek typu `_ResultType` při úspěšném dokončení. Úkoly typu `task<void>` nevyrábějí žádný výsledek. Úkol lze počkat a zrušit jej nezávisle na jiných úkolech. Je možné také skládání s ostatními úlohami pokračování (`then`) a spojení (`when_all`) a možnost výběru (`when_any`) vzory.|
|[task_canceled – třída](task-canceled-class.md)|Tato třída popisuje výjimku vyvolanou vrstvou úkolů PPL, aby bylo možné zrušit aktuální úlohu. Je také vyvolané `get()` metodu na [úloh](task-class.md), případě zrušené úlohy.|
|[task_completion_event – třída](task-completion-event-class.md)|`task_completion_event` Třída umožňuje zpoždění spuštění úlohy, dokud není splněna podmínka, nebo spuštění úlohy jako odpověď na vnější události.|
|[task_continuation_context – třída](task-continuation-context-class.md)|`task_continuation_context` Třída umožňuje určit, kde byste chtěli pokračování má být proveden. Je vhodné použít tuto třídu z aplikace pro UPW. Pro aplikace Windows Runtime je kontext pokračování úlohy určován v modulu runtime a nelze jej konfigurovat.|
|[task_group – třída](task-group-class.md)|`task_group` Třída reprezentuje kolekci paralelní práce, které mohou čekat nebo bylo zrušeno.|
|[task_handle – třída](task-handle-class.md)|`task_handle` Třída představuje jednotlivé paralelní pracovní položku. Zapouzdřuje pokynů a data potřebná k provedení práce.|
|[task_options – třída (Concurrency Runtime)](task-options-class-concurrency-runtime.md)|Představuje povolené možnosti pro vytvoření úkolu|
|[timer – třída](timer-class.md)|A `timer` blok zpráv je jeden cíl `source_block` schopné odesílat zprávy k cíli po uplynutí zadaného časového období se nebo v určitých intervalech.|
|[transformer – třída](transformer-class.md)|A `transformer` blok zpráv je jeden cíl, více zdroje, seřazený `propagator_block` který může přijmout zprávy z jednoho typu a umožňuje ukládání množství zpráv jiného typu.|
|[unbounded_buffer – třída](unbounded-buffer-class.md)|`unbounded_buffer` Je více cílový blok zpráv více zdroje, seřazený `propagator_block` umožňující ukládání množství zpráv.|
|[unsupported_os – třída](unsupported-os-class.md)|Tato třída popisuje výjimku vyvolána, když se používá nepodporovaný operační systém.|

### <a name="structures"></a>Struktury

|Název|Popis|
|----------|-----------------|
|[DispatchState – struktura](dispatchstate-structure.md)|`DispatchState` Struktura se používá k přenosu stavu `IExecutionContext::Dispatch` metody. Popisuje okolností, pod kterým `Dispatch` metoda se vyvolá u `IExecutionContext` rozhraní.|
|[IExecutionContext – struktura](iexecutioncontext-structure.md)|Rozhraní pro provádění kontext, který můžete spustit na danou virtuální procesor a být spolupráce při přepnutí kontextu.|
|[IExecutionResource – struktura](iexecutionresource-structure.md)|Abstrakce pro vlákno hardwaru.|
|[IResourceManager – struktura](iresourcemanager-structure.md)|Rozhraní pro správce prostředků modulu Runtime souběžnosti. Toto je rozhraní, díky které plánovači komunikovat s Resource Managerem.|
|[IScheduler – struktura](ischeduler-structure.md)|Rozhraní pro abstrakci pracovní plánovače. Správce prostředků modulu Runtime souběžnosti používá ke komunikaci s plánovači pracovní toto rozhraní.|
|[ISchedulerProxy – struktura](ischedulerproxy-structure.md)|Rozhraní, pomocí kterého plánovači komunikovat se správcem prostředků pro vyjednávání přidělení prostředků modulu Runtime souběžnosti.|
|[IThreadProxy – struktura](ithreadproxy-structure.md)|Abstrakce vlákna exekuce. V závislosti na tom `SchedulerType` klíče zásad plánovače vytvoříte, Resource Manageru, udělí se vám proxy vlákna, která je založená na regulárních vlákno Win32 nebo uživatelským režimem plánovatelná vlákna (UMS). UMS vlákna jsou podporované v 64bitových systémech s verzí Windows 7 a vyšší.|
|[ITopologyExecutionResource – struktura](itopologyexecutionresource-structure.md)|Rozhraní pro prostředek provádění definované správcem prostředků.|
|[ITopologyNode – struktura](itopologynode-structure.md)|Rozhraní pro uzel topologie definované správcem prostředků. Uzel obsahuje jeden nebo více spuštění prostředků.|
|[IUMSCompletionList – struktura](iumscompletionlist-structure.md)|Představuje seznam pro doplňování UMS. Při plánování určené plánovače vlákno blokováno UMS kontext je odeslána k provedení rozhodnutí toho, jak naplánovat na základního kořenového virtuálního procesoru, zatímco původní vlákno blokované. Když se původní vlákno odblokuje, operační systém zařadí do fronty se do seznamu dokončení, která je dostupná prostřednictvím tohoto rozhraní. Plánovač můžete dotazovat v seznamu dokončení na určené plánování kontextu nebo druhém místě, které prohledává pro práci.|
|[IUMSScheduler – struktura](iumsscheduler-structure.md)|Rozhraní pro abstrakci plánovače, která chce, aby správce prostředků modulu Runtime souběžnosti k předání zařízení uživatelského režimu plánovatelná vlákna (UMS). Resource Manager používá ke komunikaci s podprocesu plánovače UMS toto rozhraní. `IUMSScheduler` Rozhraní zdědí `IScheduler` rozhraní.|
|[IUMSThreadProxy – struktura](iumsthreadproxy-structure.md)|Abstrakce vlákna exekuce. Pokud má váš Plánovač udělit uživatelským režimem plánovatelná vlákna (UMS) nastavte hodnotu pro element zásad plánovače `SchedulerKind` k `UmsThreadDefault`a implementovat `IUMSScheduler` rozhraní. UMS vlákna jsou pouze podporované v 64bitových systémech s verzí Windows 7 a vyšší.|
|[IUMSUnblockNotification – struktura](iumsunblocknotification-structure.md)|Představuje oznámení ze Správce prostředků, že proxy vlákna, která zablokuje a aktivuje návrat do plánovače určené plánování kontextu má odblokováno a je připravený k naplánování. Toto rozhraní je neplatný, jakmile vrácený kontext spuštění přidružené vlákno proxy, `GetContext` přeplánovat metody.|
|[IVirtualProcessorRoot – struktura](ivirtualprocessorroot-structure.md)|Abstrakce pro vlákno hardwaru, na kterém můžete spustit proxy vlákna.|
|[scheduler_interface – struktura](scheduler-interface-structure.md)|Rozhraní plánovače|
|[scheduler_ptr – struktura (Concurrency Runtime)](scheduler-ptr-structure-concurrency-runtime.md)|Představuje ukazatel na Plánovač. Tato třída existuje pro povolení specifikace sdílené životnosti pomocí shared_ptr nebo jen prostým odkazem pomocí nezpracovaného ukazatele.|

### <a name="enumerations"></a>Výčty

|Název|Popis|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|Platné stavy `agent`.|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Typy událostí, které lze sledovat pomocí trasování funkce nabízené knihovna agentů|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Typy událostí, které lze sledovat pomocí trasování funkce nabízené modulem Runtime souběžnost.|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Příznaky trasování pro typy událostí|
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|Typ důležité oblasti kontext je uvnitř.|
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Používá `DynamicProgressFeedback` založenou na zásadách popisující, zda bude znovu vyrovnána zdrojů pro Plánovač podle statistické informace shromážděné z plánovače, může obsahovat jenom na přechod do stavu nečinnosti prostřednictvím volání virtuálníchprocesorů`Activate` a `Deactivate` metody `IVirtualProcessorRoot` rozhraní. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md#policyelementkey).|
|[join_type](concurrency-namespace-enums.md#join_type)|Typ `join` blok zpráv.|
|[message_status](concurrency-namespace-enums.md#message_status)|Platné odpovědi pro nabídku `message` objektu do bloku.|
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Klíče zásad popisující aspekty chování plánovače. Každý prvek zásad je popsán pár klíč hodnota. Další informace o zásady plánovače a jejich dopad na plánovači najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|Používá `SchedulerKind` zásady k popisu typu vlákna, která Plánovač by měly využívat pro základní spuštění kontexty. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md#policyelementkey).|
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|Používá `SchedulingProtocol` zásady k popisu, který plánování algoritmus se používá pro Plánovač. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md#policyelementkey).|
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Používá k označení stavu, ve kterém probíhá proxy vlákna, kdy je prováděna kooperativní kontextu přepnout na jiné vlákno proxy.|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Popisuje stav spuštění objektu `task_group` nebo `structured_task_group` objektu. Hodnota tohoto typu je vrácena řadou metod, které čekat na úloh naplánovaných pro skupinu úloh pro dokončení.|
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|Používá `WinRTInitialization` zásad popisující, zda a jak Windows Runtime bude inicializován na vláknech plánovače pro aplikaci, která běží v systémech s verzí Windows 8 nebo vyšší. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md#policyelementkey).|

### <a name="functions"></a>Funkce

|Název|Popis|
|----------|-----------------|
|[ALLOC – funkce](concurrency-namespace-functions.md#alloc)|Přiděluje blok paměti zadaná velikost ze služby Concurrency Runtime Caching Suballocator.|
|[asend – funkce](concurrency-namespace-functions.md#asend)|Přetíženo. Operace asynchronního odeslání, která plánuje úlohy rozšíření dat na cílový blok.|
|[cancel_current_task Function](concurrency-namespace-functions.md#cancel_current_task)|Zruší právě prováděnou úlohu. Tuto funkci lze volat z těla úkolu k přerušení provádění daného úkolu a způsobí, že vstoupí `canceled` stavu.<br /><br /> Není podporovaný scénář pro volání této funkce, pokud nejste v těle `task`. To způsobí nedefinované chování, jako je například zhroucení nebo zablokování aplikace.|
|[create_async Function](concurrency-namespace-functions.md#create_async)|Vytvoří asynchronní konstrukt Windows Runtime založený na uživatelem zadaný výraz lambda nebo funkce objektu. Návratový typ `create_async` je buď `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, nebo `IAsyncOperationWithProgress<TResult, TProgress>^` založené na signatuře lambdy předané metodě.|
|[create_task – funkce](concurrency-namespace-functions.md#create_task)|Přetíženo. Vytvoří PPL [úloh](task-class.md) objektu. `create_task` lze použít kdekoli by jste použili úkol konstruktoru. Je určen hlavně pro pohodlí, protože umožňuje používat `auto` – klíčové slovo při vytváření úloh.|
|[CreateResourceManager Function](concurrency-namespace-functions.md#createresourcemanager)|Vrátí rozhraní, které představuje instanci singletonu ze Správce prostředků modulu Runtime souběžnosti. Správce prostředků zodpovídá za přiřazení zdrojů plánovačům, které chtějí vzájemně spolupracovat.|
|[Disabletracing – funkce](concurrency-namespace-functions.md#disabletracing)|Zakáže trasování v modulu Runtime souběžnosti. Tato funkce je zastaralá, protože je ve výchozím nastavení neregistrovaná trasování událostí pro Windows.|
|[Enabletracing – funkce](concurrency-namespace-functions.md#enabletracing)|Umožňuje trasování v modulu Runtime souběžnosti. Tato funkce je zastaralá, protože trasování událostí pro Windows je teď ve výchozím.|
|[Free – funkce](concurrency-namespace-functions.md#free)|Uvolní blok paměti dříve přidělený metodou `Alloc` metodu služby Concurrency Runtime Caching Suballocator.|
|[get_ambient_scheduler Function (Concurrency Runtime)](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId Function](concurrency-namespace-functions.md#getexecutioncontextid)|Vrací jedinečný identifikátor, který je možné přiřadit ke kontextu spuštění, který implementuje `IExecutionContext` rozhraní.|
|[Getosversion – funkce](concurrency-namespace-functions.md#getosversion)|Vrátí verzi operačního systému.|
|[Getprocessorcount – funkce](concurrency-namespace-functions.md#getprocessorcount)|Vrátí počet podprocesů hardwaru základního systému.|
|[Getprocessornodecount – funkce](concurrency-namespace-functions.md#getprocessornodecount)|Vrátí počet uzlů NUMA nebo balíček procesoru použitého systému.|
|[Getschedulerid – funkce](concurrency-namespace-functions.md#getschedulerid)|Vrací jedinečný identifikátor, který je možné přiřadit do fronty plánovače, která implementuje `IScheduler` rozhraní.|
|[interruption_point Function](concurrency-namespace-functions.md#interruption_point)|Vytvoří jako bod přerušení pro zrušení. Pokud se zrušením probíhá v kontextu, ve kterém je tato funkce volána, to vyvolá vnitřní výjimka, která zruší spuštění aktuálně prováděné paralelní práci. Pokud neprobíhá zrušení, funkce nemá žádný účinek.|
|[is_current_task_group_canceling Function](concurrency-namespace-functions.md#is_current_task_group_canceling)|Vrací údaj o Určuje, zda úloha skupině, která je právě probíhá vloženě v aktuálním kontextu je uprostřed aktivního rušení (nebo bude za chvíli). Všimněte si, že pokud neexistuje žádná skupina úloha právě probíhá vloženě v aktuálním kontextu `false` bude vrácen.|
|[make_choice Function](concurrency-namespace-functions.md#make_choice)|Přetíženo. Vytvoří `choice` blok zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dva nebo více vstupními zdroji.|
|[make_greedy_join Function](concurrency-namespace-functions.md#make_greedy_join)|Přetíženo. Vytvoří `greedy multitype_join` blok zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dva nebo více vstupními zdroji.|
|[make_join Function](concurrency-namespace-functions.md#make_join)|Přetíženo. Vytvoří `non_greedy multitype_join` blok zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dva nebo více vstupními zdroji.|
|[make_task – funkce](concurrency-namespace-functions.md#make_task)|Metoda factory pro vytváření `task_handle` objektu.|
|[parallel_buffered_sort Function](concurrency-namespace-functions.md#parallel_buffered_sort)|Přetíženo. Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem paralelně. Tato funkce je sémanticky podobné `std::sort` v tom, že je na základě porovnání, nestabilní, místní řazení s tím rozdílem, že je nutné `O(n)` další místo a vyžaduje výchozí inicializace pro se setříděnými prvky.|
|[parallel_for – funkce](concurrency-namespace-functions.md#parallel_for)|Přetíženo. `parallel_for` Iteruje přes celou řadu indexy a spustí funkci uživatelem zadané v jednotlivých iteracích paralelní.|
|[parallel_for_each Function](concurrency-namespace-functions.md#parallel_for_each)|Přetíženo. `parallel_for_each` použije zadanou funkci na každý prvek v rozsahu, paralelní. Je sémanticky rovnocenné `for_each` fungovat v `std` obor názvů, s výjimkou danou iteraci přes prvky se provádí paralelní a pořadí iterace není zadána. Argument `_Func` musí podporovat operátor volání funkce formuláře `operator()(T)` kde parametr `T` je typ položky kontejneru se provést iteraci.|
|[parallel_invoke – funkce](concurrency-namespace-functions.md#parallel_invoke)|Přetíženo. Spustí funkci objekty zadané jako parametry v paralelních a blokuje, dokud se nedokončí provádění. Každý objekt funkce může být výraz lambda, ukazatele na funkce, nebo žádný objekt, který podporuje operátor volání funkce s podpisem `void operator()()`.|
|[parallel_radixsort Function](concurrency-namespace-functions.md#parallel_radixsort)|Přetíženo. Uspořádá prvky v zadaném rozsahu do bez sestupném pořadí pomocí základ algoritmu řazení. Toto je funkce stabilní řazení, která vyžaduje projekce funkci, která můžete promítnout prvků, které se dají seřadit podle nepodepsaných klíčů jako celé číslo. Výchozí inicializace je požadovaná pro se setříděnými prvky.|
|[parallel_reduce Function](concurrency-namespace-functions.md#parallel_reduce)|Přetíženo. Vypočítá součet všech prvků v zadaném rozsahu, podle výpočtu po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků podobně získaných pomocí zadané binární operace, než součtem, paralelně. `parallel_reduce` je sémanticky podobné `std::accumulate`, s tím rozdílem, že vyžaduje asociativní binární operace a vyžaduje hodnotu identity místo počáteční hodnoty.|
|[parallel_sort Function](concurrency-namespace-functions.md#parallel_sort)|Přetíženo. Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem paralelně. Tato funkce je sémanticky podobné `std::sort` v tom, že je na základě porovnání, nestabilní, místní řazení.|
|[parallel_transform Function](concurrency-namespace-functions.md#parallel_transform)|Přetíženo. Zadaný objekt funkce se vztahuje na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu, paralelně. Tuto funkční je sémanticky ekvivalentní `std::transform`.|
|[Receive – funkce](concurrency-namespace-functions.md#receive)|Přetíženo. Obecné přijímat implementace, což kontextu pro čekání na data z přesně jeden zdroj a filtrování hodnot, které byly přijaty.|
|[run_with_cancellation_token Function](concurrency-namespace-functions.md#run_with_cancellation_token)|Objekt funkce spustí v kontextu daného rušícího tokenu okamžitě a synchronně.|
|[Send – funkce](concurrency-namespace-functions.md#send)|Přetíženo. Odesílání synchronní operace, která čeká na cíl přijme nebo odmítne zprávy.|
|[set_ambient_scheduler – funkce (Concurrency Runtime)](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[set_task_execution_resources Function](concurrency-namespace-functions.md#set_task_execution_resources)|Přetíženo. Omezuje provádění prostředky využívané třídou interní pracovní vlákna Concurrency Runtime přidružení zadána sada.<br /><br /> Je možné tuto metodu volat pouze před správce prostředků se vytvořila, nebo mezi dvěma životnosti Resource Manageru. Může být vyvolán více než jednou za předpokladu, správce prostředků v době vyvolání neexistuje. Po nastavení limit spřažení zůstává v platnosti až do další platné volání `set_task_execution_resources` metody.<br /><br /> Zadaná maska spřažení nemusí být podmnožinou Maska spřažení procesu. Proces spřažení aktualizují i v případě potřeby.|
|[swap – funkce](concurrency-namespace-functions.md#swap)|Vymění prvky dvou `concurrent_vector` objekty.|
|[task_from_exception – funkce (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_exception)||
|[task_from_result – funkce (Concurrency Runtime)](concurrency-namespace-functions.md#task_from_result)||
|[Trace_agents_register_name – funkce](concurrency-namespace-functions.md#trace_agents_register_name)|Přidruží daný název bloku zpráv nebo agenta v trasování ETW.|
|[try_receive – funkce](concurrency-namespace-functions.md#try_receive)|Přetíženo. Obecné try a přijetí implementace, povolení kontextu vyhledat data z přesně jednoho zdroje a filtrování hodnot, které byly přijaty. Pokud data není připraven, metoda vrátí hodnotu false.|
|[Wait – funkce](concurrency-namespace-functions.md#wait)|Pozastaví aktuální kontext pro určenou dobu.|
|[when_all – funkce](concurrency-namespace-functions.md#when_all)|Vytvoří úlohu, která bude dokončena úspěšně, pokud všechny úlohy uvedené jako argumenty úspěšně dokončena.|
|[when_any – funkce](concurrency-namespace-functions.md#when_any)|Přetíženo. Vytvoří úlohu, která bude dokončena úspěšně, pokud některá z úloh zadané jako argumenty úspěšně dokončena.|

### <a name="operators"></a>Operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](concurrency-namespace-operators.md#operator_neq)|Testuje, zda `concurrent_vector` objekt na levé straně operátoru není roven `concurrent_vector` objekt na pravé straně.|
|[Operator & &](concurrency-namespace-operators.md#operator_amp_amp)|Přetíženo. Vytvoří úlohu, která bude dokončena úspěšně, pokud obě úlohy uvedené jako argumenty úspěšně dokončena.|
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Přetíženo. Vytvoří úlohu, která bude dokončena úspěšně, pokud jeden z úkolů zadané jako argumenty úspěšně dokončena.|
|[Operator <](concurrency-namespace-operators.md#operator_lt)|Testuje, zda `concurrent_vector` objekt na levé straně operátoru menší než `concurrent_vector` objekt na pravé straně.|
|[operator<=](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, zda `concurrent_vector` je objekt na levé straně operátoru menší než nebo rovna hodnotě `concurrent_vector` objekt na pravé straně.|
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|Testuje, zda `concurrent_vector` objekt na levé straně operátoru rovná `concurrent_vector` objekt na pravé straně.|
|[operator>](concurrency-namespace-operators.md#operator_gt)|Testuje, zda `concurrent_vector` je objekt na levé straně operátoru větší než `concurrent_vector` objekt na pravé straně.|
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, zda `concurrent_vector` je objekt na levé straně operátoru větší než nebo rovna hodnotě `concurrent_vector` objekt na pravé straně.|

### <a name="constants"></a>Konstanty

|Název|Popis|
|----------|-----------------|
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|Kategorie GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07}), knihovna agentů v modulu Runtime souběžnosti odesílané popisující události trasování událostí pro Windows.|
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, který přímo souvisí s vás ujmeme rutinních úkolů nebo úkolů.|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Zprostředkovatel trasování událostí pro Windows, identifikátor GUID modulu Runtime souběžnosti.|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Označuje podporu rozhraní Resource Manageru definované v sadě Visual Studio 2010.|
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, která nejsou popsána konkrétně podle jiné kategorie.|
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, který přímo souvisí s kontexty.|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Hodnota označující, že čekání by nemělo nikdy vypršet.|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Hodnota označující, že vypršel časový limit čekání.|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Zvláštní hodnota klíče zásad `ContextPriority` označující, že priorita vlákna v Plánovači všechny kontexty by měl být stejný jako vlákno, které vytvořili plánovače.|
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, který přímo souvisí na zámků.|
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|Speciální hodnotu klíče zásad `MinConcurrency` a `MaxConcurrency`. Výchozí hodnota je počet podprocesů hardwaru v počítači chybí jiná omezení.|
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Kategorie odesílané GUID popisující události trasování událostí pro Windows, které jsou přímo souvisí s k využití modulu Concurrency Runtime `parallel_for_each` funkce.|
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|Kategorie odesílané GUID popisující události trasování událostí pro Windows, které jsou přímo souvisí s k využití modulu Concurrency Runtime `parallel_for` funkce.|
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Kategorie odesílané GUID popisující události trasování událostí pro Windows, které jsou přímo souvisí s k využití modulu Concurrency Runtime `parallel_invoke` funkce.|
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, který přímo souvisí s resource Manageru.|
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, který přímo souvisí s plánování skupin.|
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, který přímo souvisí s aktivitu plánovače.|
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Kategorie GUID popisující události trasování událostí pro Windows vyvolané modulu Runtime souběžnosti, který přímo souvisí s virtuálními procesory.|

## <a name="requirements"></a>Požadavky

**Header:** agents.h, concrt.h, concrtrm.h, concurrent_priority_queue.h, concurrent_queue.h, concurrent_unordered_map.h, concurrent_unordered_set.h, concurrent_vector.h, internal_concurrent_hash.h, internal_split_ordered_list.h, ppl.h, pplcancellation_token.h, pplconcrt.h, pplinterface.h, ppltasks.h

## <a name="see-also"></a>Viz také:

[Referenční informace](reference-concurrency-runtime.md)
