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
ms.openlocfilehash: e3a943ed52ce9653086203713bb98331f809314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372726"
---
# <a name="concurrency-namespace-enums"></a>concurrency – výčty oboru názvů

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[Klíč PolicyElement](#policyelementkey)|
|[Typ plánovače](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[Přepínáníproxystate](#switchingproxystate)|
|[Typ inicializace WinRT](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status-enumeration"></a><a name="agent_status"></a>agent_status výčet

Platné stavy `agent`pro .

```cpp
enum agent_status;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`agent_canceled`|Byla `agent` zrušena.|
|`agent_created`|Byl `agent` vytvořen, ale nebyl spuštěn.|
|`agent_done`|Dokončeno `agent` bez zrušení.|
|`agent_runnable`|Byla `agent` spuštěna, ale nezadala svou `run` metodu.|
|`agent_started`|Začalo `agent` to.|

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Asynchronní agenti](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType výčet

Typy událostí, které lze sledovat pomocí funkce trasování nabízené knihovnou agentů

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Typ události, který představuje vytvoření objektu|
|`AGENTS_EVENT_DESTROY`|Typ události, který představuje odstranění objektu|
|`AGENTS_EVENT_END`|Typ události, který představuje závěr některých zpracování|
|`AGENTS_EVENT_LINK`|Typ události, který představuje propojení bloků zpráv|
|`AGENTS_EVENT_NAME`|Typ události, který představuje název objektu|
|`AGENTS_EVENT_SCHEDULE`|Typ události, který představuje plánování procesu|
|`AGENTS_EVENT_START`|Typ události, který představuje zahájení některých zpracování|
|`AGENTS_EVENT_UNLINK`|Typ události, který představuje odpojení bloků zpráv|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType výčet

Typy událostí, které lze sledovat pomocí funkce trasování, kterou nabízí runtime souběžnosti.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Typ události, který představuje akt připojení k plánovači.|
|`CONCRT_EVENT_BLOCK`|Typ události, který představuje akt blokování kontextu.|
|`CONCRT_EVENT_DETACH`|Typ události, který představuje akt odpojení od plánovače.|
|`CONCRT_EVENT_END`|Typ události, který označuje začátek dvojice událostí začátku a konce.|
|`CONCRT_EVENT_GENERIC`|Typ události používaný pro různé události.|
|`CONCRT_EVENT_IDLE`|Typ události, který představuje akt kontextu stává nečinnosti.|
|`CONCRT_EVENT_START`|Typ události, který označuje začátek dvojice událostí začátku a konce.|
|`CONCRT_EVENT_UNBLOCK`|Typ události, který představuje akt odblokování kontextu.|
|`CONCRT_EVENT_YIELD`|Typ události, který představuje akt kontext udání.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h **Obor názvů:** souběžnost

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags výčet

Příznaky trasování pro typy událostí

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
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

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>Výčet typu CriticalRegion

Typ kritické oblasti kontextu je uvnitř.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`InsideCriticalRegion`|Označuje, že kontext je uvnitř kritické oblasti. Při uvnitř kritické oblasti asynchronní pozastavení jsou skryty z plánovače. Pokud k takovému pozastavení dojde, správce prostředků bude čekat, až se vlákno stane spustitelným, a jednoduše jej obnoví namísto vyvolání plánovače znovu. Všechny zámky odebrané uvnitř takové oblasti musí být brány s velkou opatrností.|
|`InsideHyperCriticalRegion`|Označuje, že kontext je uvnitř hyperkritické oblasti. Při uvnitř hyperkritické oblasti synchronní i asynchronní pozastavení jsou skryty z plánovače. Pokud k takovému pozastavení nebo blokování dojde, správce prostředků bude čekat na vlákno, aby se stal spustitelný a jednoduše jej obnovit namísto vyvolání plánovače znovu. Zámky přijatá uvnitř takové oblasti nesmí být nikdy sdíleny s kódem spuštěným mimo takovou oblast. To způsobí nepředvídatelné zablokování.|
|`OutsideCriticalRegion`|Označuje, že kontext je mimo všechny kritické oblasti.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrtrm.h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>Výčet typu DynamicProgressFeedbackType

Používá `DynamicProgressFeedback` zásady k popisu, zda prostředky pro plánovač bude znovu vyvážit podle statistické informace shromážděné z plánovače nebo pouze na `Activate` základě `Deactivate` virtuálních `IVirtualProcessorRoot` procesorů jít dovnitř a ven z nečinnosti stavu prostřednictvím volání a metody na rozhraní. Další informace o dostupných zásadách plánovače naleznete v [tématu PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Plánovač neshromažďuje informace o průběhu. Vyvažování se provádí výhradně na základě úrovně předplatného základního hardwarového vlákna. Další informace o úrovních předplatného naleznete v [tématu IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Tato hodnota je vyhrazena pro použití za běhu.|
|`ProgressFeedbackEnabled`|Plánovač shromažďuje informace o průběhu a předá je správci prostředků. Správce prostředků použije tyto statistické informace k obnovení rovnováhy prostředků jménem plánovače kromě úrovně předplatného základního hardwarového vlákna. Další informace o úrovních předplatného naleznete v [tématu IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).|

## <a name="join_type-enumeration"></a><a name="join_type"></a>join_type výčet

Typ bloku `join` zasílání zpráv.

```cpp
enum join_type;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`greedy`|Nenasytné `join` bloky zasílání zpráv okamžitě přijmout zprávu při šíření. To je efektivnější, ale má možnost live-lock, v závislosti na konfiguraci sítě.|
|`non_greedy`|Nechamtivý `join` zasílání zpráv blokuje odložit zprávy a pokusit se je spotřebovat poté, co všichni dorazili. Ty jsou zaručeně fungovat, ale pomalejší.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a>message_status výčet

Platné odpovědi pro nabídku `message` objektu bloku.

```cpp
enum message_status;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`accepted`|Cíl zprávu přijal.|
|`declined`|Cíl zprávu nepřijal.|
|`missed`|Cíl se pokusil zprávu přijmout, ale již nebyla k dispozici.|
|`postponed`|Cíl odložil zprávu.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a>Výčet klíče PolicyElementKey

Klíče zásad popisující aspekty chování plánovače. Každý prvek zásady je popsán dvojicí klíč-hodnota. Další informace o zásadách plánovače a jejich dopadu na plánovače naleznete v [tématu Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`ContextPriority`|Priorita vlákna operačního systému každého kontextu v plánovači. Pokud je tento klíč `INHERIT_THREAD_PRIORITY` nastaven na hodnotu, kontexty v plánovači zdědí prioritu vlákna, které plánovač vytvořilo.<br /><br /> Platné hodnoty : Všechny platné hodnoty `SetThreadPriority` pro funkci systému Windows a speciální hodnota`INHERIT_THREAD_PRIORITY`<br /><br /> Výchozí hodnota :`THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Rezervovaná velikost zásobníku každého kontextu v plánovači v kilobajtech.<br /><br /> Platné hodnoty : Kladná celá čísla<br /><br /> Výchozí hodnota `0`: označuje, že výchozí hodnota procesu pro velikost zásobníku bude použita.|
|`DynamicProgressFeedback`|Určuje, zda prostředky pro plánovačbude znovu vyvážena podle statistických informací shromážděných z plánovače nebo pouze na základě úrovně předplatného podkladových hardwarových vláken. Další informace naleznete v tématu [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Platné hodnoty : Člen `DynamicProgressFeedbackType` výčtu, `ProgressFeedbackEnabled` buď nebo`ProgressFeedbackDisabled`<br /><br /> Výchozí hodnota :`ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Pokud `SchedulingProtocol` je klíč zásad nastaven `EnhanceScheduleGroupLocality`na hodnotu , určuje to maximální počet spustitelných kontextů, které mohou být uloženy do mezipaměti v místních frontách virtuálního procesoru. Tyto kontexty se obvykle spustí v pořadí poslední in-first-out (LIFO) na virtuálníprocesor, který způsobil, že se stanou spustitelné. Všimněte si, že tento `SchedulingProtocol` klíč zásad nemá `EnhanceForwardProgress`žádný význam, pokud je klíč nastaven na hodnotu .<br /><br /> Platné hodnoty : Nezáporná celá čísla<br /><br /> Výchozí hodnota :`8`|
|`MaxConcurrency`|Maximální úroveň souběžnosti požadované plánovače. Správce prostředků se pokusí zpočátku přidělit tolik virtuálních procesorů. Speciální hodnota [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) označuje, že požadovaná úroveň souběžnosti je stejná jako počet hardwarových vláken v počítači. Pokud `MinConcurrency` je zadaná hodnota větší než počet hardwarových `MaxConcurrency` vláken `MaxExecutionResources`v počítači `MaxConcurrency` a je určena jako `MinConcurrency`, je hodnota pro zvýšena tak, aby odpovídala tomu, co je nastaveno pro .<br /><br /> Platné hodnoty : Kladná celá čísla a speciální hodnota`MaxExecutionResources`<br /><br /> Výchozí hodnota :`MaxExecutionResources`|
|`MaxPolicyElementKey`|Klíč maximálního prvku zásady. Není platný klíč prvku.|
|`MinConcurrency`|Minimální úroveň souběžnosti, která musí být poskytnuta plánovači správcem prostředků. Počet virtuálních procesorů přiřazených plánovači nikdy neklesne pod minimum. Speciální hodnota [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) označuje, že minimální úroveň souběžnosti je stejná jako počet hardwarových vláken v počítači. Pokud je hodnota `MaxConcurrency` zadaná pro menší než počet `MinConcurrency` hardwarových `MaxExecutionResources`vláken v `MinConcurrency` počítači a je určena `MaxConcurrency`jako , je hodnota pro snížena tak, aby odpovídala tomu, co je nastaveno pro .<br /><br /> Platné hodnoty : Nezáporná celá čísla `MaxExecutionResources`a speciální hodnota . Všimněte si, že pro zásady plánovače používané pro `0` konstrukci plánovačů souběžnosti runtime je hodnota neplatná.<br /><br /> Výchozí hodnota :`1`|
|`SchedulerKind`|Typ podprocesů, které plánovač použije pro základní kontexty spuštění. Další informace naleznete v tématu [SchedulerType](#schedulertype).<br /><br /> Platné hodnoty : Člen `SchedulerType` výčtu, například`ThreadScheduler`<br /><br /> Výchozí hodnota `ThreadScheduler`: . To se promítá do vláken Win32 ve všech operačních systémech.|
|`SchedulingProtocol`|Popisuje, který plánovací algoritmus bude plánovačem používat. Další informace naleznete v tématu [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Platné hodnoty : Člen `SchedulingProtocolType` výčtu, `EnhanceScheduleGroupLocality` buď nebo`EnhanceForwardProgress`<br /><br /> Výchozí hodnota :`EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Předběžný počet virtuálních procesorů na hardwarové vlákno. Cíl oversubscription faktor může zvýšit Správce prostředků, v `MaxConcurrency` případě potřeby uspokojit s podprocesů hardwaru v počítači.<br /><br /> Platné hodnoty : Kladná celá čísla<br /><br /> Výchozí hodnota :`1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a>Výčet typu plánovače

Používá zásady `SchedulerKind` k popisu typu podprocesů, které plánovač by měl použít pro základní kontexty spuštění. Další informace o dostupných zásadách plánovače naleznete v [tématu PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`ThreadScheduler`|Označuje explicitní požadavek běžných vláken Win32.|
|`UmsThreadDefault`|Uživatelsky přívětivé (UMS) vlákna nejsou podporovány v modulu Souběžnost Runtime v sadě Visual Studio 2013. Použití `UmsThreadDefault` jako hodnota `SchedulerType` pro zásadu nebude mít za následek chybu. Plánovač vytvořený pomocí této zásady však bude ve výchozím nastavení používat vlákna Win32.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>Výčet typu SchedulingProtocolType

Používá zásady `SchedulingProtocol` k popisu, který algoritmus plánování bude použit pro plánovače. Další informace o dostupných zásadách plánovače naleznete v [tématu PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`EnhanceForwardProgress`|Plánovač upřednostňuje dotazování prostřednictvím skupin y plánu po provedení jednotlivých úloh. Neblokované kontexty jsou obvykle naplánovány způsobem FIFO (first-in-first-out). Virtuální procesory neukládat do mezipaměti neblokované kontexty.|
|`EnhanceScheduleGroupLocality`|Plánovač upřednostňuje pokračovat v práci na úkolech v rámci aktuální skupiny plánu před přesunutím do jiné skupiny plánu. Neblokované kontexty jsou ukládány do mezipaměti na virtuální procesor a jsou obvykle naplánovány způsobem "last-in-first-out) virtuálním procesorem, který je odblokoval.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>Přepínání výčtu stavu proxy

Používá se k označení stavu proxy vlákna, když provádí kooperativní kontextový přepínač na jiný proxy podproces.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`Blocking`|Označuje, že volající vlákno je kooperativně blokování a by měl být výhradně vlastněny volajícím až následně znovu spuštěna a provádění další akce.|
|`Idle`|Označuje, že volající vlákno již není potřeba plánovačem a je vrácena správci prostředků. Kontext, který byl odesílán již nelze využít Správce prostředků.|
|`Nesting`|Označuje, že volající vlákno vnoří podřízený plánovač a je potřeba volajícím, aby se připojilk jinému plánovači.|

### <a name="remarks"></a>Poznámky

Parametr typu `SwitchingProxyState` je předán metodě `IThreadProxy::SwitchTo` instrukce Správce prostředků, jak zacházet proxy podprocesu, který provádí volání.

Další informace o tom, jak se tento typ používá, naleznete v [tématu IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a>task_group_status výčet

Popisuje stav spuštění `task_group` objektu `structured_task_group` nebo objektu. Hodnota tohoto typu je vrácena mnoha metodami, které čekají na úkoly naplánované na dokončení skupiny úkolů.

```cpp
enum task_group_status;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`canceled`|Objekt `task_group` `structured_task_group` nebo byl zrušen. Je možné, že nebyl proveden jeden nebo více úkolů.|
|`completed`|Úkoly zařazené `task_group` do `structured_task_group` fronty k objektu nebo byly úspěšně dokončeny.|
|`not_complete`|Úkoly zařazené `task_group` do fronty k objektu nebyly dokončeny. Všimněte si, že tato hodnota není v současné době vrácena souběžnosti Runtime.|

### <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>Výčet typu WinRTInitializationType

Používá zásady `WinRTInitialization` k popisu, zda a jak bude prostředí Windows Runtime inicializováno ve vláknech plánovače pro aplikaci, která běží v operačních systémech s verzí Windows 8 nebo vyšší. Další informace o dostupných zásadách plánovače naleznete v [tématu PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Hodnoty

|Name (Název)|Popis|
|----------|-----------------|
|`DoNotInitializeWinRT`|Pokud je aplikace spuštěna v operačních systémech s verzí Windows 8 nebo vyšší, vlákna v plánovači nebude inicializovat prostředí Windows Runtime .|
|`InitializeWinRTAsMTA`|Když je aplikace spuštěna v operačních systémech s verzí Windows 8 nebo vyšší, každé vlákno v rámci plánovače inicializuje prostředí Windows Runtime a deklaruje, že je součástí vícevláknového apartmentu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
