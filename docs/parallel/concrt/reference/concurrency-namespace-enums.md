---
title: výčty oboru názvů Concurrency
ms.date: 11/04/2016
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
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: 342655e290167315b7f10caba979804461e10658
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521073"
---
# <a name="concurrency-namespace-enums"></a>výčty oboru názvů Concurrency

||||
|-|-|-|
|[Agents_eventtype –](#agents_eventtype)|[Concrt_eventtype –](#concrt_eventtype)|[Concrt_traceflags –](#concrt_traceflags)|
|[Criticalregiontype –](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[Policyelementkey –](#policyelementkey)|
|[SchedulerType](#schedulertype)|[Schedulingprotocoltype –](#schedulingprotocoltype)|[Switchingproxystate –](#switchingproxystate)|
|[Winrtinitializationtype –](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status –](#message_status)|[task_group_status](#task_group_status)|

##  <a name="agent_status"></a>  agent_status – výčet

Platné stavy `agent`.

```
enum agent_status;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`agent_canceled`|`agent` Byla zrušena.|
|`agent_created`|`agent` Byla vytvořena, ale nebyla spuštěna.|
|`agent_done`|`agent` Skončil bez rušení.|
|`agent_runnable`|`agent` Spuštěn, ale nebylo zadáno jeho `run` metoda.|
|`agent_started`|`agent` Byla spuštěna.|

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronních agentů](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

##  <a name="agents_eventtype"></a>  Agents_eventtype – výčet

Typy událostí, které lze sledovat pomocí trasování funkce nabízené knihovna agentů

```
enum Agents_EventType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Typ události, která představuje vytvoření objektu|
|`AGENTS_EVENT_DESTROY`|Typ události, která představuje odstranění objektu|
|`AGENTS_EVENT_END`|Typ události, která představuje uzavření některé zpracování|
|`AGENTS_EVENT_LINK`|Typ události, která představuje propojení bloky zpráv|
|`AGENTS_EVENT_NAME`|Typ události, která představuje název pro objekt|
|`AGENTS_EVENT_SCHEDULE`|Typ události, která představuje plánování procesu|
|`AGENTS_EVENT_START`|Typ události, která představuje některé zahájení zpracování|
|`AGENTS_EVENT_UNLINK`|Typ události, která představuje zrušení propojení bloků zprávy|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

##  <a name="concrt_eventtype"></a>  Concrt_eventtype – výčet

Typy událostí, které lze sledovat pomocí trasování funkce nabízené modulem Runtime souběžnost.

```
enum ConcRT_EventType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Typ události, která představuje v rámci připojení do fronty plánovače.|
|`CONCRT_EVENT_BLOCK`|Typ události, která představuje v rámci kontextu blokování.|
|`CONCRT_EVENT_DETACH`|Typ události, která představuje v rámci probíhá odpojování od plánovače.|
|`CONCRT_EVENT_END`|Typ události, který označuje začátek pár začátek/konec události.|
|`CONCRT_EVENT_GENERIC`|Typ události používané pro různé události.|
|`CONCRT_EVENT_IDLE`|Typ události, která představuje v rámci kontextu přešly do stavu nečinnosti.|
|`CONCRT_EVENT_START`|Typ události, který označuje začátek pár začátek/konec události.|
|`CONCRT_EVENT_UNBLOCK`|Typ události, která představuje v rámci odblokování kontextu.|
|`CONCRT_EVENT_YIELD`|Typ události, která představuje v rámci kontextu pozastavuje.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h **Namespace:** souběžnosti

##  <a name="concrt_traceflags"></a>  Concrt_traceflags – výčet

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

##  <a name="criticalregiontype"></a>  Criticalregiontype – výčet

Typ důležité oblasti kontext je uvnitř.

```
enum CriticalRegionType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`InsideCriticalRegion`|Určuje, zda kontext je uvnitř důležité oblasti. Když uvnitř důležité oblasti, jsou asynchronní pozastavení skryté plánovače. Toto pozastavení dojde, Resource Manageru bude čekat na spustitelnost a jednoduše obnovit namísto vyvolání Plánovač znovu podprocesu. Žádné zámky provést uvnitř tyto oblasti musí být přijata extreme opatrně.|
|`InsideHyperCriticalRegion`|Označuje, zda kontext je uvnitř hyper důležité oblasti. Když uvnitř hyper důležité oblasti, synchronní a asynchronní pozastavení jsou skryté plánovače. By měl pozastavení nebo blokování dochází resource Manageru bude čekat na spustitelnost a jednoduše obnovit namísto vyvolání Plánovač znovu podprocesu. Zámky provést uvnitř tyto oblasti musí být nikdy sdílené s kódem spuštěným mimo tyto oblasti. To způsobí neočekávané zablokování.|
|`OutsideCriticalRegion`|Označuje, že je kontextu mimo jakékoliv důležité oblasti.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

##  <a name="dynamicprogressfeedbacktype"></a>  Dynamicprogressfeedbacktype – výčet

Používá `DynamicProgressFeedback` založenou na zásadách popisující, zda bude znovu vyrovnána zdrojů pro Plánovač podle statistické informace shromážděné z plánovače, může obsahovat jenom na přechod do stavu nečinnosti prostřednictvím volání virtuálníchprocesorů`Activate` a `Deactivate` metody `IVirtualProcessorRoot` rozhraní. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md).

```
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Plánovač není shromažďovat informace o průběhu. Opětovné vyvážení se provádí na základě výhradně na úrovni předplatného podkladové vlákno hardwaru. Další informace na úrovni předplatného najdete v tématu [iexecutionresource::currentsubscriptionlevel –](IExecutionResource-structure.md).<br /><br /> Tato hodnota je rezervovaná pro použití modulem runtime.|
|`ProgressFeedbackEnabled`|Plánovač shromažďuje informace o průběhu a předává je do resource Manageru. Tyto statistické informace k obnovení rovnováhy prostředkům jménem Plánovač kromě úroveň předplatného podkladové vlákno hardwaru se využívat resource Manageru. Další informace na úrovni předplatného najdete v tématu [iexecutionresource::currentsubscriptionlevel –](IExecutionResource-structure.md).|

##  <a name="join_type"></a>  join_type – výčet

Typ `join` blok zpráv.

```
enum join_type;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`greedy`|Greedy `join` zasílání zpráv bloky okamžitě příjem zprávy při šíření. To je mnohem efektivnější, ale má možnost live-lock, v závislosti na konfiguraci sítě.|
|`non_greedy`|Bez metody greedy `join` zasílání zpráv bloky odložit zprávy a zkuste to a využívejte je prostřednictvím po všech objevit. Tyto zaručeno, že chcete pracovat, ale pomaleji.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

##  <a name="message_status"></a>  message_status – výčet

Platné odpovědi pro nabídku `message` objektu do bloku.

```
enum message_status;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`accepted`|Cíl přijaté zprávy.|
|`declined`|Cíl nepřijala zprávu.|
|`missed`|Cíl se pokusil přijmout zprávu, ale již není k dispozici.|
|`postponed`|Cíl odložit zprávu.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

##  <a name="policyelementkey"></a>  Policyelementkey – výčet

Klíče zásad popisující aspekty chování plánovače. Každý prvek zásad je popsán pár klíč hodnota. Další informace o zásady plánovače a jejich dopad na plánovači najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```
enum PolicyElementKey;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ContextPriority`|Priorita vlákna operačního systému z jednotlivých kontextech v plánovači. Pokud tento klíč nastavený na hodnotu `INHERIT_THREAD_PRIORITY` kontextech v Plánovači zdědí priorita vlákna, které vytvořili plánovače.<br /><br /> Platné hodnoty: žádné platné hodnoty pro Windows `SetThreadPriority` funkce a zvláštní hodnota `INHERIT_THREAD_PRIORITY`<br /><br /> Výchozí hodnota: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Velikost zásobníku vyhrazené každý kontext v Plánovači v kilobajtech.<br /><br /> Platné hodnoty: kladná celá čísla<br /><br /> Výchozí hodnota: `0`, označující, že použita výchozí hodnota proces pro velikost zásobníku.|
|`DynamicProgressFeedback`|Určuje, zda bude znovu vyrovnána zdrojů pro Plánovač podle statistické informace shromážděné z plánovače nebo pouze podle úrovně předplatného základní hardwarových vláken. Další informace najdete v tématu [dynamicprogressfeedbacktype –](#dynamicprogressfeedbacktype).<br /><br /> Platné hodnoty:, členem `DynamicProgressFeedbackType` výčet, buď `ProgressFeedbackEnabled` nebo `ProgressFeedbackDisabled`<br /><br /> Výchozí hodnota: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Když `SchedulingProtocol` je nastavena na hodnotu klíče zásad `EnhanceScheduleGroupLocality`, určuje maximální počet spustitelných kontextů povolené ukládat do mezipaměti v na místní fronty virtuálního procesoru. Takové kontexty obvykle poběží v pořadí last-in-first-out (LIFO) na virtuální procesor, který je na spustitelnost způsobily. Všimněte si, že má tento klíč zásady nemají smysl, kdy `SchedulingProtocol` klíč nastavený na hodnotu `EnhanceForwardProgress`.<br /><br /> Platné hodnoty: nezáporná celá čísla<br /><br /> Výchozí hodnota: `8`|
|`MaxConcurrency`|Souběžnost maximální úroveň požadovaného plánovačem. Správce prostředků se pokusí nejprve přidělit uvedený počet virtuálních procesorů. Zvláštní hodnota [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) znamená, že je stejný jako počet podprocesů hardwaru na počítači na úrovni požadované souběžnosti. Pokud je hodnota zadaná u `MinConcurrency` je větší než počet podprocesů hardwaru na počítači a `MaxConcurrency` je zadán jako `MaxExecutionResources`, hodnota `MaxConcurrency` je vyvolávána s cílem odpovídat, jaký je nastavený pro `MinConcurrency`.<br /><br /> Platné hodnoty: kladná celá čísla a zvláštní hodnota `MaxExecutionResources`<br /><br /> Výchozí hodnota: `MaxExecutionResources`|
|`MaxPolicyElementKey`|Klíč elementu maximální zásad. Není platný element key.|
|`MinConcurrency`|Úroveň minimální souběžnosti, který se musí poskytnout plánovači resource Manageru. Počet virtuálních procesorů, které jsou přiřazeny do fronty plánovače půjdou nikdy pod požadované minimum. Zvláštní hodnota [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) znamená, že úroveň souběžnosti minimální je stejný jako počet podprocesů hardwaru v počítači. Pokud je hodnota zadaná u `MaxConcurrency` je menší než počet podprocesů hardwaru na počítači a `MinConcurrency` je zadán jako `MaxExecutionResources`, hodnota `MinConcurrency` klesnou tak, aby odpovídaly, jaký je nastavený pro `MaxConcurrency`.<br /><br /> Platné hodnoty: nezáporná celá čísla a zvláštní hodnota `MaxExecutionResources`. Všimněte si, že zásady plánovače použít pro tvorbu plánovači Concurrency Runtime, hodnota `0` je neplatný.<br /><br /> Výchozí hodnota: `1`|
|`SchedulerKind`|Typ vlákna, která Plánovač budou využívat pro základní spuštění kontexty. Další informace najdete v tématu [schedulertype –](#schedulertype).<br /><br /> Platné hodnoty:, členem `SchedulerType` výčtu, například `ThreadScheduler`<br /><br /> Výchozí hodnota: `ThreadScheduler`. To se přeloží na Win32 vlákna ve všech operačních systémech.|
|`SchedulingProtocol`|Popisuje, jaké plánování algoritmus se použije plánovačem. Další informace najdete v tématu [schedulingprotocoltype –](#schedulingprotocoltype).<br /><br /> Platné hodnoty:, členem `SchedulingProtocolType` výčet, buď `EnhanceScheduleGroupLocality` nebo `EnhanceForwardProgress`<br /><br /> Výchozí hodnota: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Předběžná počet virtuálních procesorů na vlákno hardwaru. Cílový překryvného odběru faktor je možné zvýšit Resource Manageru, pokud je to nezbytné pro splnění `MaxConcurrency` s vlákny hardwaru v počítači.<br /><br /> Platné hodnoty: kladná celá čísla<br /><br /> Výchozí hodnota: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

##  <a name="schedulertype"></a>  Schedulertype – výčet

Používá `SchedulerKind` zásady k popisu typu vlákna, která Plánovač by měly využívat pro základní spuštění kontexty. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md).

```
enum SchedulerType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ThreadScheduler`|Označuje požadavek explicitní vláken regulární systému Win32.|
|`UmsThreadDefault`|Uživatel – režim plánovatelná vlákna (UMS) nejsou podporovány v modulu Runtime souběžnosti v sadě Visual Studio 2013. Pomocí `UmsThreadDefault` jako hodnotu `SchedulerType` zásady nesmí dojít k chybě. Ale Plánovač vytvořené pomocí této zásady se ve výchozím nastavení používání vláken Win32.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

##  <a name="schedulingprotocoltype"></a>  Schedulingprotocoltype – výčet

Používá `SchedulingProtocol` zásady k popisu, který plánování algoritmus se používá pro Plánovač. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md).

```
enum SchedulingProtocolType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`EnhanceForwardProgress`|Plánovač upřednostňuje do kruhové dotazování skupiny plánu po spuštění jednotlivých úloh. Odblokuje kontext jsou obvykle naplánované způsobem first-in-first-out (FIFO). Virtuální procesory Neukládat do mezipaměti odblokuje kontext.|
|`EnhanceScheduleGroupLocality`|Plánovač upřednostňuje a pokračujte v práci na úkolech v rámci aktuální plán skupině před přesunutím do jiné skupiny plánu. Odblokuje kontext jsou uložené v mezipaměti na virtuální procesor a jsou obvykle naplánované způsobem last-in-first-out (LIFO) ve virtuální procesor, což je odblokováno.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

##  <a name="switchingproxystate"></a>  Switchingproxystate – výčet

Používá k označení stavu, ve kterém probíhá proxy vlákna, kdy je prováděna kooperativní kontextu přepnout na jiné vlákno proxy.

```
enum SwitchingProxyState;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`Blocking`|Označuje, že kooperativně blokuje volající vlákno a musí být výhradně ve vlastnictví volajícího až do následně znovu a provádění dalších akcí.|
|`Idle`|Označuje, že volající vlákno už je nepotřebujete plánovačem a se vrací do Resource Manageru. Kontext, který se odeslalo již není možné používat Resource Manageru.|
|`Nesting`|Označuje, že volající vlákno je vnořené podřízené Plánovač a je potřeba volajícího, aby bylo možné připojit k jiné plánovače.|

### <a name="remarks"></a>Poznámky

Parametr typu `SwitchingProxyState` předaný metodě `IThreadProxy::SwitchTo` dáte pokyn, aby správce prostředků jak zacházet s proxy vlákna, která provádí volání.

Další informace o tom, jak tento typ se používá, najdete v části [ithreadproxy::switchto –](ithreadproxy-structure.md#switchto).

##  <a name="task_group_status"></a>  task_group_status – výčet

Popisuje stav spuštění objektu `task_group` nebo `structured_task_group` objektu. Hodnota tohoto typu je vrácena řadou metod, které čekat na úloh naplánovaných pro skupinu úloh pro dokončení.

```
enum task_group_status;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`canceled`|`task_group` Nebo `structured_task_group` byl zrušen. Jeden nebo více úkolů pravděpodobně proběhlo.|
|`completed`|Úkoly ve frontě `task_group` nebo `structured_task_group` objekt byla úspěšně dokončena.|
|`not_complete`|Úkoly ve frontě `task_group` objektu nebyly dokončeny. Všimněte si, že tato hodnota není vracena rozhraním Concurrency Runtime.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface.h

##  <a name="winrtinitializationtype"></a>  Winrtinitializationtype – výčet

Používá `WinRTInitialization` zásad popisující, zda a jak Windows Runtime bude inicializován na vláknech plánovače pro aplikaci, která běží v systémech s verzí Windows 8 nebo vyšší. Další informace o dostupných zásadách plánovače naleznete v tématu [policyelementkey –](concurrency-namespace-enums.md).

```
enum WinRTInitializationType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`DoNotInitializeWinRT`|Když je aplikace poběží v operačních systémech s verzí Windows 8 nebo vyšší, vlákna v Plánovači inicializovat nebude modulu Windows Runtime.|
|`InitializeWinRTAsMTA`|Při spuštění aplikace v systémech s verzí Windows 8 nebo vyšší bude každé vlákno v Plánovači inicializovat Windows Runtime a deklarovat, že je součástí apartmentu s více vlákny.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
