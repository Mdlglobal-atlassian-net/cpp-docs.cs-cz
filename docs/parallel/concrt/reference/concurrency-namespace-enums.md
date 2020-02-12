---
title: concurrency – výčty oboru názvů
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
ms.openlocfilehash: 716c2d03e6d1ff67566bd28e5931996ea2d400af
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141319"
---
# <a name="concurrency-namespace-enums"></a>concurrency – výčty oboru názvů

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType –](#criticalregiontype)|[DynamicProgressFeedbackType –](#dynamicprogressfeedbacktype)|[PolicyElementKey –](#policyelementkey)|
|[SchedulerType –](#schedulertype)|[SchedulingProtocolType –](#schedulingprotocoltype)|[SwitchingProxyState –](#switchingproxystate)|
|[WinRTInitializationType –](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status"></a>Výčet agent_status

Platné stavy pro `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`agent_canceled`|`agent` byla zrušena.|
|`agent_created`|`agent` byl vytvořen, ale nebyl spuštěn.|
|`agent_done`|`agent` dokončen bez zrušení.|
|`agent_runnable`|`agent` se spustil, ale nezadal jeho `run` metodu.|
|`agent_started`|`agent` bylo zahájeno.|

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Asynchronní agenti](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

## <a name="agents_eventtype"></a>Výčet Agents_EventType

Typy událostí, které lze trasovat pomocí funkce trasování nabízené knihovnou agentů

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Typ události, která představuje vytvoření objektu|
|`AGENTS_EVENT_DESTROY`|Typ události, která představuje odstranění objektu|
|`AGENTS_EVENT_END`|Typ události, která představuje uzavření nějakého zpracování|
|`AGENTS_EVENT_LINK`|Typ události, která představuje propojení bloků zpráv|
|`AGENTS_EVENT_NAME`|Typ události, která představuje název objektu|
|`AGENTS_EVENT_SCHEDULE`|Typ události, která představuje plánování procesu|
|`AGENTS_EVENT_START`|Typ události, která představuje zahájení nějakého zpracování|
|`AGENTS_EVENT_UNLINK`|Typ události, která představuje odpojení bloků zpráv|

### <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

## <a name="concrt_eventtype"></a>Výčet ConcRT_EventType

Typy událostí, které lze trasovat pomocí funkce trasování, které nabízí Concurrency Runtime.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Typ události, která představuje akt připojení ke Scheduleru.|
|`CONCRT_EVENT_BLOCK`|Typ události, která představuje akt kontextu blokování.|
|`CONCRT_EVENT_DETACH`|Typ události, která představuje akt odpojení od plánovače.|
|`CONCRT_EVENT_END`|Typ události, která označuje začátek dvojice událostí Start/end.|
|`CONCRT_EVENT_GENERIC`|Typ události, který se používá pro různé události.|
|`CONCRT_EVENT_IDLE`|Typ události, která představuje Act kontextu, se stane nečinným.|
|`CONCRT_EVENT_START`|Typ události, která označuje začátek dvojice událostí Start/end.|
|`CONCRT_EVENT_UNBLOCK`|Typ události, která představuje Act z odblokování kontextu.|
|`CONCRT_EVENT_YIELD`|Typ události, která představuje Act z kontextu, který je výsledkem.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h **obor názvů:** concurrency

## <a name="concrt_traceflags"></a>Výčet Concrt_TraceFlags

Příznaky trasování pro typy událostí

```cpp
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

**Záhlaví:** ConcRT. h

## <a name="criticalregiontype"></a>Výčet CriticalRegionType –

Typ kritické oblasti, ke které je kontext uvnitř.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`InsideCriticalRegion`|Označuje, že kontext je uvnitř kritické oblasti. V případě kritické oblasti jsou asynchronní pozastavení od plánovače skryta. Pokud dojde k pozastavení, Správce prostředků počká, až se vlákno stane spustitelný a jednoduše ho obnoví, místo vyvolání plánovače. Jakékoli zámky pořízené v takové oblasti se musí považovat za extrémní péči.|
|`InsideHyperCriticalRegion`|Označuje, že kontext je uvnitř oblasti kritické pro technologii Hyper-v. V případě kritických oblastí, které jsou v oblasti Hyper-v kritické, jsou synchronní i asynchronní odpružení od plánovače skryté. Pokud by mohlo dojít k pozastavení nebo blokování, správce prostředků počká na spustitelný vlákna a jednoduše ho obnoví, místo aby znovu vyvolal Plánovač. Zámky pořízené v takové oblasti nesmí být nikdy sdíleny s kódem běžícím mimo takovou oblast. Tím dojde k nepředvídatelnému zablokování.|
|`OutsideCriticalRegion`|Označuje, že kontext je mimo jakoukoli kritickou oblast.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm. h

## <a name="dynamicprogressfeedbacktype"></a>Výčet DynamicProgressFeedbackType –

Používá se v zásadách `DynamicProgressFeedback` k popisu, zda budou prostředky pro Plánovač znovu vyrovnávatelné podle statistických informací shromážděných z plánovače nebo pouze na základě virtuálních procesorů, které přecházejí do nečinného stavu prostřednictvím volání metod `Activate` a `Deactivate` na `IVirtualProcessorRoot` rozhraní. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Plánovač neshromažďuje informace o průběhu. Nové vyrovnávání se provádí výhradně na úrovni předplatného podkladového vlákna hardwaru. Další informace o úrovních předplatného najdete v tématu [IExecutionResource:: CurrentSubscriptionLevel –](IExecutionResource-structure.md).<br /><br /> Tato hodnota je vyhrazena pro použití modulem runtime.|
|`ProgressFeedbackEnabled`|Plánovač shromažďuje informace o průběhu a předává je do Správce prostředků. Správce prostředků bude tyto statistické informace využívat k vyvážení prostředků jménem plánovače kromě úrovně předplatného základního hardwarového vlákna. Další informace o úrovních předplatného najdete v tématu [IExecutionResource:: CurrentSubscriptionLevel –](IExecutionResource-structure.md).|

## <a name="join_type"></a>Výčet join_type

Typ `join`ového bloku pro zasílání zpráv.

```cpp
enum join_type;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`greedy`|Hladce `join` bloky zasílání zpráv hned po rozmnožení přijmout zprávu. To je efektivnější, ale má možnost živý zámek v závislosti na konfiguraci sítě.|
|`non_greedy`|Nehladové `join` blok zasílání zpráv odloží zprávy a pokusí se je využít po doručení všech. Jsou zaručené pracovat, ale pomalejší.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

## <a name="message_status"></a>Výčet message_status

Platné odpovědi na nabídku objektu `message` do bloku.

```cpp
enum message_status;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`accepted`|Cíl zprávu přijal.|
|`declined`|Cíl zprávu nepřijal.|
|`missed`|Cíl se pokusil přijmout zprávu, ale již není k dispozici.|
|`postponed`|Cíl odložil zprávu.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

## <a name="policyelementkey"></a>Výčet PolicyElementKey –

Klíče zásad popisující aspekty chování plánovače. Jednotlivé prvky zásad jsou popsány dvojicí klíč-hodnota. Další informace o zásadách plánovače a jejich vlivu na plánovače najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ContextPriority`|Priorita vlákna operačního systému každého kontextu v plánovači. Pokud je tento klíč nastavený na hodnotu, `INHERIT_THREAD_PRIORITY` kontexty v Plánovači zdědí prioritu vlákna, které vytvořil Plánovač.<br /><br /> Platné hodnoty: všechny platné hodnoty pro funkci Windows `SetThreadPriority` a speciální hodnotu `INHERIT_THREAD_PRIORITY`<br /><br /> Výchozí hodnota: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Velikost rezervovaného zásobníku každého kontextu v Plánovači v kilobajtech.<br /><br /> Platné hodnoty: kladná celá čísla<br /><br /> Výchozí hodnota: `0`, což znamená, že se použije výchozí hodnota procesu pro velikost zásobníku.|
|`DynamicProgressFeedback`|Určuje, zda budou prostředky pro Plánovač znovu vyrovnávatelné podle statistických informací shromážděných z plánovače nebo pouze podle úrovně předplatného základních hardwarových vláken. Další informace najdete v tématu [DynamicProgressFeedbackType –](#dynamicprogressfeedbacktype).<br /><br /> Platné hodnoty: člen výčtu `DynamicProgressFeedbackType`, buď `ProgressFeedbackEnabled`, nebo `ProgressFeedbackDisabled`<br /><br /> Výchozí hodnota: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Když je klíč zásad `SchedulingProtocol` nastavený na hodnotu `EnhanceScheduleGroupLocality`, určuje se maximální počet spustitelný kontextů, které se můžou ukládat do mezipaměti v místních frontách virtuálních procesorů. Takové kontexty obvykle budou spouštěny v pořadí posledního navýšení (LIFO) na virtuálním procesoru, což způsobilo, že se stanou spustitelný. Všimněte si, že tento klíč zásad nemá žádný význam, pokud je `SchedulingProtocol` klíč nastaven na hodnotu `EnhanceForwardProgress`.<br /><br /> Platné hodnoty: nezáporná celá čísla<br /><br /> Výchozí hodnota: `8`|
|`MaxConcurrency`|Maximální úroveň souběžnosti, kterou Plánovač požaduje. Správce prostředků se pokusí tento počet virtuálních procesorů zpočátku přidělit. Speciální hodnota [MaxExecutionResources –](concurrency-namespace-constants1.md#maxexecutionresources) označuje, že požadovaná souběžná úroveň je shodná s počtem hardwarových vláken v počítači. Je-li hodnota zadaná pro `MinConcurrency` větší než počet hardwarových vláken v počítači a `MaxConcurrency` je určena jako `MaxExecutionResources`, bude hodnota `MaxConcurrency` vyvolána, aby odpovídala nastavení pro `MinConcurrency`.<br /><br /> Platné hodnoty: kladná celá čísla a speciální hodnota `MaxExecutionResources`<br /><br /> Výchozí hodnota: `MaxExecutionResources`|
|`MaxPolicyElementKey`|Maximální klíč elementu zásad Nejedná se o platný klíč elementu.|
|`MinConcurrency`|Minimální úroveň souběžnosti, kterou je nutné poskytnout plánovači správcem prostředků. Počet virtuálních procesorů přiřazených k plánovači nikdy nebude nižší než minimum. Speciální hodnota [MaxExecutionResources –](concurrency-namespace-constants1.md#maxexecutionresources) označuje, že minimální souběžnost je stejná jako počet hardwarových vláken v počítači. Pokud je hodnota zadaná pro `MaxConcurrency` menší než počet hardwarových vláken v počítači a `MinConcurrency` je zadána jako `MaxExecutionResources`, hodnota `MinConcurrency` je nižší, aby odpovídala nastavení pro `MaxConcurrency`.<br /><br /> Platné hodnoty: nezáporná celá čísla a speciální hodnota `MaxExecutionResources`. Všimněte si, že pro zásady plánovače používané pro konstrukci Concurrency Runtime schedulerů je hodnota `0` neplatná.<br /><br /> Výchozí hodnota: `1`|
|`SchedulerKind`|Typ vláken, která bude Plánovač využívat pro podkladové kontexty provádění. Další informace najdete v tématu [SchedulerType –](#schedulertype).<br /><br /> Platné hodnoty: člen výčtu `SchedulerType`, například `ThreadScheduler`<br /><br /> Výchozí hodnota: `ThreadScheduler`. Tím se přeloží na vlákna Win32 ve všech operačních systémech.|
|`SchedulingProtocol`|Popisuje, který algoritmus plánování bude Plánovač používat. Další informace najdete v tématu [SchedulingProtocolType –](#schedulingprotocoltype).<br /><br /> Platné hodnoty: člen výčtu `SchedulingProtocolType`, buď `EnhanceScheduleGroupLocality`, nebo `EnhanceForwardProgress`<br /><br /> Výchozí hodnota: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Nezávazně počet virtuálních procesorů na hardwarové vlákno. Pokud je to nutné, můžete v případě potřeby Správce prostředků zvýšit cílový faktor předplatného tak, aby `MaxConcurrency` s hardwarovými vlákny v počítači.<br /><br /> Platné hodnoty: kladná celá čísla<br /><br /> Výchozí hodnota: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

## <a name="schedulertype"></a>Výčet SchedulerType –

Používá se zásadami `SchedulerKind` k popisu typu vláken, které by měl Plánovač využít pro podkladové kontexty provádění. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`ThreadScheduler`|Označuje explicitní požadavek normálních vláken Win32.|
|`UmsThreadDefault`|V Concurrency Runtime v Visual Studio 2013 se nepodporují vlákna v uživatelském režimu plánovatelná (UMS). Použití `UmsThreadDefault` jako hodnoty pro zásady `SchedulerType` nebude mít za následek chybu. Plánovač vytvořený s touto zásadou ale bude ve výchozím nastavení používat vlákna Win32.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

## <a name="schedulingprotocoltype"></a>Výčet SchedulingProtocolType –

Používá se v zásadách `SchedulingProtocol` k popisu, který algoritmus plánování bude pro Plánovač využíván. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`EnhanceForwardProgress`|Plánovač dává přednost kruhovému dotazování prostřednictvím skupin plánů po provedení jednotlivých úkolů. Odblokované kontexty jsou obvykle naplánovány v rámci metody FIFO (First-in-first-out). Virtuální procesory neukládá do mezipaměti neblokované kontexty.|
|`EnhanceScheduleGroupLocality`|Před přechodem do jiné skupiny plánů upřednostňuje Plánovač, aby pokračoval v práci na úkolech v rámci aktuální skupiny plánovače. Odblokované kontexty jsou ukládány do mezipaměti pro virtuální procesor a jsou obvykle naplánovány pomocí metody LIFO (za sekundu) virtuálním procesorem, který je odblokované.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

## <a name="switchingproxystate"></a>Výčet SwitchingProxyState –

Slouží k označení stavu, ve kterém se nachází proxy vlákna, pokud je spuštěný kontext spolupráce, přepnutí na jiný proxy vlákna.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`Blocking`|Označuje, že volající vlákno spolupracuje a že by měl být výhradně vlastníkem volajícího, dokud ho znovu nespustí a provede jinou akci.|
|`Idle`|Označuje, že volající vlákno již není plánovačem vyžadováno a je vrácen do Správce prostředků. Kontext, který byl odeslán, již nebude moci využívat Správce prostředků.|
|`Nesting`|Označuje, že volající vlákno je vnořeno do podřízeného plánovače a je vyžadováno volajícím, aby se mohl připojit k jinému plánovači.|

### <a name="remarks"></a>Poznámky

Do metody `IThreadProxy::SwitchTo` je předán parametr typu `SwitchingProxyState`, který instruuje Správce prostředků, jak považovat proxy vlákna, které provádí volání.

Další informace o použití tohoto typu naleznete v tématu [IThreadProxy:: SwitchTo –](ithreadproxy-structure.md#switchto).

## <a name="task_group_status"></a>Výčet task_group_status

Popisuje stav spuštění objektu `task_group` nebo `structured_task_group`. Hodnota tohoto typu je vrácena mnoha metodami, které čekají na dokončení úloh naplánovaných na skupinu úloh.

```cpp
enum task_group_status;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`canceled`|Objekt `task_group` nebo `structured_task_group` byl zrušen. Jeden nebo více úkolů možná není spuštěno.|
|`completed`|Úkoly zařazené do fronty `task_group` nebo `structured_task_group` objektu byly úspěšně dokončeny.|
|`not_complete`|Úkoly zařazené do fronty pro objekt `task_group` nebyly dokončeny. Všimněte si, že tato hodnota není aktuálně vrácena Concurrency Runtime.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface. h

## <a name="winrtinitializationtype"></a>Výčet WinRTInitializationType –

Používá se v zásadách `WinRTInitialization` k popisu, jestli a jak se prostředí Windows Runtime inicializuje na vláknech Scheduleru pro aplikaci, která běží na operačních systémech s verzí Windows 8 nebo vyšší. Další informace o dostupných zásadách plánovače najdete v tématu [PolicyElementKey –](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Hodnoty

|Název|Popis|
|----------|-----------------|
|`DoNotInitializeWinRT`|Pokud je aplikace spuštěna v operačních systémech s verzí Windows 8 nebo vyšší, vlákna v Plánovači nebudou inicializovat prostředí Windows Runtime.|
|`InitializeWinRTAsMTA`|Když je aplikace spuštěna v operačních systémech s verzí Windows 8 nebo vyšší, každé vlákno v Plánovači Inicializuje prostředí Windows Runtime a deklaruje, že je součástí vícevláknového objektu apartment.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
