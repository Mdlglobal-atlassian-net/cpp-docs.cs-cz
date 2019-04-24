---
title: Funkce oboru názvů Concurrency
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 9cb726ccc475d6d08e036229d0d06089e3fac31c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163738"
---
# <a name="concurrency-namespace-functions"></a>Funkce oboru názvů Concurrency

||||
|-|-|-|
|[ALLOC](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|
|[Enabletracing –](#enabletracing)|[Free](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend –](#asend)|
|[cancel_current_task](#cancel_current_task)|[clear](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[receive](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[Odeslat](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Počkej](#wait)|
|[when_all](#when_all)|[when_any –](#when_any)|

##  <a name="alloc"></a>  Alloc

Přiděluje blok paměti zadaná velikost ze služby Concurrency Runtime Caching Suballocator.

```
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parametry

*_NumBytes*<br/>
Počet bajtů paměti k přidělení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Další informace o tom, které scénáře v aplikaci mohou benefitovat z použití služby Caching Suballocator, viz [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

##  <a name="asend"></a>  asend –

Operace asynchronního odeslání, která plánuje úlohy rozšíření dat na cílový blok.

```
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ dat k odeslání.

*_Trg*<br/>
Ukazatel nebo odkaz na cíl, do kterého se data odesílají.

*_Data*<br/>
Odkaz na data, která mají být odeslány.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zpráva byla přijata před vrácením metodu **false** jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

##  <a name="cancel_current_task"></a>  cancel_current_task

Zruší právě prováděnou úlohu. Tuto funkci lze volat z těla úkolu k přerušení provádění daného úkolu a způsobí, že vstoupí `canceled` stavu.

Není podporovaný scénář pro volání této funkce, pokud nejste v těle `task`. To způsobí nedefinované chování, jako je například zhroucení nebo zablokování aplikace.

```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

##  <a name="clear"></a>  Vymazat

Vymaže souběžná fronta zničení všechny aktuálně zařazených do fronty elementy. Tato metoda není bezpečná pro souběžnost.

```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parametry

*T*<br/>

*_Ax*<br/>

##  <a name="create_async"></a>  create_async

Vytvoří asynchronní konstrukt Windows Runtime založený na uživatelem zadaný výraz lambda nebo funkce objektu. Návratový typ `create_async` je buď `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, nebo `IAsyncOperationWithProgress<TResult, TProgress>^` založené na signatuře lambdy předané metodě.

```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Zadejte.

*_Func*<br/>
Výraz lambda nebo funkce objektu, ze které se vytvoří asynchronní konstrukt Windows Runtime.

### <a name="return-value"></a>Návratová hodnota

Asynchronní konstrukce reprezentované IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^, nebo IAsyncOperationWithProgress\<TResult, TProgress > ^. Vrácené rozhraní závisí na podpis lambda předaného do funkce.

### <a name="remarks"></a>Poznámky

Návratový typ lambdy Určuje, zda je konstrukce akce nebo operace.

Výrazy lambda, které vracejí void, způsobují vytváření akcí. Výrazy lambda, které vrací výsledek typu `TResult` způsobují vytváření operací TResult.

Může také vracet lambda `task<TResult>` které zapouzdřuje asynchronní práci sám nebo je pokračováním posloupnosti úkolů, které představují asynchronní práci. V takovém případě je samotný výraz lambda vykonán jako vložený, protože úlohy jsou ty, které jsou spouštěny asynchronně, a návratový typ výrazu lambda je neobalený, aby vytvořil asynchronní konstrukt vrácený funkcí `create_async`. Z toho vyplývá, že výraz lambda, který vrátí úlohu\<void >, způsobí vytvoření akcí a lambda, která vrátí úkol\<TResult >, způsobí vytvoření operací TResult.

Lambda může mít nula, jeden nebo dva argumenty. Platné argumenty jsou `progress_reporter<TProgress>` a `cancellation_token`v tomto pořadí, pokud se oba používají. Výraz lambda bez argumentů způsobí vytvoření asynchronní konstrukce bez možnosti pro vykazování průběhu. Lambda, která používá progress_reporter\<TProgress > způsobí, že `create_async` k vrátí asynchronní konstrukci, která hlásí průběh typu TProgress pokaždé, když `report` volání metody objektu progress_reporter. Lambda, která trvá cancellation_token může pomocí tohoto tokenu zkontrolovat zrušení nebo předat úkolům, které vytvoří tak, aby zrušení asynchronní konstrukce způsobilo zrušení těchto úkolů.

Pokud tělo výrazu lambda nebo funkce objektu funkce vrátí výsledek (a ne úlohu\<TResult >), výraz lambda bude spuštěn asynchronně v rámci procesu MTA v kontextu úlohy modul Runtime implicitně vytvoří pro ni. `IAsyncInfo::Cancel` Metody způsobí zrušení implicitního úkolu.

Pokud tělo výrazu lambda vrátí úkol, lambda, který provede vložené a deklarováním výrazu lambda pro příjem argumentu typu `cancellation_token` můžete vyvolat zrušení všech úloh, které vytvoříte v rámci výrazu lambda předáním tohoto tokenu při jejich vytváření. Můžete také použít `register_callback` metodu na token, který má k vyvolání zpětného volání při volání pomocí běhového modulu `IAsyncInfo::Cancel` v asynchronní operaci nebo provedené akci...

Tato funkce je pouze k dispozici pro aplikace Windows Runtime.

##  <a name="createresourcemanager"></a>  CreateResourceManager

Vrátí rozhraní, které představuje instanci singletonu ze Správce prostředků modulu Runtime souběžnosti. Správce prostředků zodpovídá za přiřazení zdrojů plánovačům, které chtějí vzájemně spolupracovat.

```
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Návratová hodnota

`IResourceManager` Rozhraní.

### <a name="remarks"></a>Poznámky

Několik následných volání této metody vrátí stejnou instanci správce prostředků. Každé volání metody zvýší odkaz počet v Resource Manageru a musí mít odpovídající volání [IResourceManager::Release](iresourcemanager-structure.md) metodu, když váš Plánovač dokončí komunikaci se správcem prostředků.

[unsupported_os –](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulem Runtime souběžnost.

##  <a name="create_task"></a>  create_task –

Vytvoří PPL [úloh](task-class.md) objektu. `create_task` lze použít kdekoli by jste použili úkol konstruktoru. Je určen hlavně pro pohodlí, protože umožňuje používat `auto` – klíčové slovo při vytváření úloh.

```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru, ze kterého se má úloha sestavit.

*_ReturnType*<br/>
Zadejte.

*_Param*<br/>
Parametr, ze kterého se má úloha sestavit. To může být objekt lambda nebo funkce `task_completion_event` objektu, jiný `task` objektu nebo rozhraní Windows::Foundation:: iasyncinfo, pokud používáte úkoly v aplikaci pro UPW.

*_TaskOptions*<br/>
Možnosti úlohy.

*_Task*<br/>
Úloha k vytvoření.

### <a name="return-value"></a>Návratová hodnota

Nový úkol typu `T`, který je odvozen z `_Param`.

### <a name="remarks"></a>Poznámky

První přetížení se chová jako konstruktor úkolu, který přijímá jeden parametr.

Druhé přetížení přidružuje token zrušení, opatřeného nově vytvořené úlohy. Pokud použijete toto přetížení nemůžete předat do jiného `task` objekt jako první parametr.

Typ vrácené úlohy je odvozen z prvního parametru funkce. Pokud `_Param` je `task_completion_event<T>`, `task<T>`, nebo funktor, který vrátí buď typ `T` nebo `task<T>`, typ vytvořeného úkolu je `task<T>`.

V aplikaci UWP Pokud `_Param` je typu:: iasyncoperation\<T > ^ nebo Windows::Foundation:: iasyncoperationwithprogress\<T, P > ^, nebo funktor, který vrací jeden z těchto typů, bude mít bude vytvořený úkol typ `task<T>`. Pokud `_Param` je typu Windows::Foundation:: iasyncaction ^ nebo Windows::Foundation:: iasyncactionwithprogress\<P > ^, nebo funktor, který vrací jeden z těchto typů, bude vytvořený úkol typ `task<void>`.

##  <a name="disabletracing"></a>  Disabletracing –

Zakáže trasování v modulu Runtime souběžnosti. Tato funkce je zastaralá, protože je ve výchozím nastavení neregistrovaná trasování událostí pro Windows.

```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je trasování bylo správně zakázané, `S_OK` je vrácena. Pokud dříve nebyla zahájeno trasování, `E_NOT_STARTED` je vrácena

##  <a name="enabletracing"></a>  Enabletracing –

Umožňuje trasování v modulu Runtime souběžnosti. Tato funkce je zastaralá, protože trasování událostí pro Windows je teď ve výchozím.

```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Návratová hodnota

Pokud bylo správně zahájeno trasování, `S_OK` je vrácena; jinak `E_NOT_STARTED` je vrácena.

##  <a name="free"></a>  Zdarma

Uvolní blok paměti dříve přidělený metodou `Alloc` metodu služby Concurrency Runtime Caching Suballocator.

```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parametry

*_PAllocation*<br/>
Ukazatel na paměť přidělenou dříve metodou `Alloc` metodu, která má být uvolněna. Pokud parametr `_PAllocation` je nastaveno na hodnotu `NULL`, tato metoda bude ignorovat a okamžitě jej vrátí.

### <a name="remarks"></a>Poznámky

Další informace o tom, které scénáře v aplikaci mohou benefitovat z použití služby Caching Suballocator, viz [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler

```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Návratová hodnota

##  <a name="getexecutioncontextid"></a>  GetExecutionContextId

Vrací jedinečný identifikátor, který je možné přiřadit ke kontextu spuštění, který implementuje `IExecutionContext` rozhraní.

```
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro kontext spuštění.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete získat identifikátor pro kontext spuštění předtím, než je předáte `IExecutionContext` rozhraní jako parametr pro některou z metod nabízí Resource Manageru.

##  <a name="getosversion"></a>  Getosversion –

Vrátí verzi operačního systému.

```
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Návratová hodnota

Výčtová hodnota představující operační systém.

### <a name="remarks"></a>Poznámky

[unsupported_os –](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulem Runtime souběžnost.

##  <a name="getprocessorcount"></a>  Getprocessorcount –

Vrátí počet podprocesů hardwaru základního systému.

```
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet hardwarových vláken.

### <a name="remarks"></a>Poznámky

[unsupported_os –](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulem Runtime souběžnost.

##  <a name="getprocessornodecount"></a>  Getprocessornodecount –

Vrátí počet uzlů NUMA nebo balíček procesoru použitého systému.

```
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet uzlů NUMA nebo balíčků procesoru.

### <a name="remarks"></a>Poznámky

Pokud systém obsahuje více uzlů NUMA, než balíčky procesoru, vrátí se počet uzlů NUMA, jinak se vrátí počet balíčků procesoru.

[unsupported_os –](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulem Runtime souběžnost.

##  <a name="getschedulerid"></a>  Getschedulerid –

Vrací jedinečný identifikátor, který je možné přiřadit do fronty plánovače, která implementuje `IScheduler` rozhraní.

```
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro Plánovač.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete získat identifikátor pro váš Plánovač, předtím, než je předáte `IScheduler` rozhraní jako parametr pro některou z metod nabízí Resource Manageru.

##  <a name="internal_assign_iterators"></a>  internal_assign_iterators

```
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Parametry

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*první*<br/>

*last*<br/>

##  <a name="interruption_point"></a>  interruption_point –

Vytvoří jako bod přerušení pro zrušení. Pokud se zrušením probíhá v kontextu, ve kterém je tato funkce volána, to vyvolá vnitřní výjimka, která zruší spuštění aktuálně prováděné paralelní práci. Pokud neprobíhá zrušení, funkce nemá žádný účinek.

```
inline void interruption_point();
```

### <a name="remarks"></a>Poznámky

Neměli byste zachytit vnitřní zrušení výjimky vyvolané `interruption_point()` funkce. Výjimka bude zachycena a zpracovat modulem runtime a jejímu může způsobit, že váš program neobvyklým způsobem chovat.

##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling –

Vrací údaj o Určuje, zda úloha skupině, která je právě probíhá vloženě v aktuálním kontextu je uprostřed aktivního rušení (nebo bude za chvíli). Všimněte si, že pokud neexistuje žádná skupina úloha právě probíhá vloženě v aktuálním kontextu `false` bude vrácen.

```
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud skupina úloh, který právě probíhá ruší, **false** jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

##  <a name="make_choice"></a>  make_choice –

Vytvoří `choice` blok zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dva nebo více vstupními zdroji.

```
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Typ bloku zprávy prvního zdroje.

*T2*<br/>
Typ bloku zprávy druhého zdroje.

*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `choice` naplánovaný zasílání zpráv bloku.

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Položky*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `choice` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.

### <a name="return-value"></a>Návratová hodnota

A `choice` bloku zpráv s dvěma nebo více vstupními zdroji.

##  <a name="make_greedy_join"></a>  make_greedy_join

Vytvoří `greedy multitype_join` blok zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dva nebo více vstupními zdroji.

```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Typ bloku zprávy prvního zdroje.

*T2*<br/>
Typ bloku zprávy druhého zdroje.

*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `multitype_join` naplánovaný zasílání zpráv bloku.

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Položky*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `multitype_join` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.

### <a name="return-value"></a>Návratová hodnota

A `greedy multitype_join` bloku zpráv s dvěma nebo více vstupními zdroji.

##  <a name="make_join"></a>  make_join –

Vytvoří `non_greedy multitype_join` blok zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dva nebo více vstupními zdroji.

```
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parametry

*T1*<br/>
Typ bloku zprávy prvního zdroje.

*T2*<br/>
Typ bloku zprávy druhého zdroje.

*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `multitype_join` naplánovaný zasílání zpráv bloku.

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Položky*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `multitype_join` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.

### <a name="return-value"></a>Návratová hodnota

A `non_greedy multitype_join` bloku zpráv s dvěma nebo více vstupními zdroji.

##  <a name="make_task"></a>  make_task –

Metoda factory pro vytváření `task_handle` objektu.

```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, která bude volána k provedení práce reprezentována `task_handle` objektu.

*_Func*<br/>
Funkce, která bude volána k provedení práce reprezentována `task_handle` objektu. To může být funktor lambda, ukazatele na funkci, nebo žádný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()()`.

### <a name="return-value"></a>Návratová hodnota

A `task_handle` objektu.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná, když je potřeba vytvořit `task_handle` objektu s výrazem lambda, protože umožňuje vytvoření objektu bez znalosti skutečný typ výrazu lambda funktor.

##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort –

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem paralelně. Tato funkce je sémanticky podobné `std::sort` v tom, že je na základě porovnání, nestabilní, místní řazení s tím rozdílem, že je nutné `O(n)` další místo a vyžaduje výchozí inicializace pro se setříděnými prvky.

```
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parametry

*_Random_iterator*<br/>
Typ iterátoru vstupním rozsahu.

*_Allocator*<br/>
Typ alokátoru paměti kompatibilní standardní knihovny C++.

*_Function*<br/>
Typ binární porovnání.

*_Zahájit*<br/>
Iterátor s náhodným přístupem adresuje umístění prvního prvku v rozsahu který se má seřadit.

*_End*<br/>
Iterátor s náhodným přístupem adresuje umístění jedno místo za poslední prvek v rozsahu který se má seřadit.

*_Alloc*<br/>
Instance Přidělovač paměti kompatibilní standardní knihovny C++.

*_Func*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují. Tato funkce porovnání musí uložit přísné slabé seřazení na dvojice prvků z posloupnosti.

*_Chunk_size*<br/>
Minimální velikost bloku dat, který bude možné rozdělit na dvě pro paralelní zpracování.

### <a name="remarks"></a>Poznámky

Všechna přetížení vyžadují `n * sizeof(T)` další místo, kde `n` je počet prvků který se má seřadit, a `T` je typ prvku. Parallel_buffered_sort – ve většině případů se zobrazí zlepšení výkonu přes [parallel_sort –](concurrency-namespace-functions.md), a abyste ho používali přes parallel_sort – Pokud máte k dispozici paměť.

Pokud nezadáte binární porovnání `std::less` slouží jako výchozí, což vyžaduje, aby typ prvku poskytnout operátor `operator<()`.

Pokud nezadáte k alokátoru typu nebo instance, přidělení paměti standardní knihovny C++ `std::allocator<T>` se používá k přidělení vyrovnávací paměti.

Algoritmus rozděluje vstupním rozsahu do dvou bloků dat a postupně jednotlivé bloky rozdělí dvě dílčí bloky dat pro spuštění paralelně. Volitelný argument `_Chunk_size` slouží k označení algoritmus, že by měl zpracovává bloky o velikosti < `_Chunk_size` sériově.

##  <a name="parallel_for"></a>  parallel_for

`parallel_for` Iteruje přes celou řadu indexy a spustí funkci uživatelem zadané v jednotlivých iteracích paralelní.

```
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>Parametry

*_Index_type*<br/>
Typ indexu se používají pro iteraci.

*_Function*<br/>
Typ funkce, která se spustí při každé iteraci.

*_Partitioner*<br/>
Typ dělicí metodou, která se používá při vytváření oddílů zadaný rozsah.

*první*<br/>
První index mají být zahrnuty v iteraci.

*last*<br/>
Index jeden za poslední index mají být zahrnuty v iteraci.

*_Step*<br/>
Hodnota, podle kterého chcete-li během iterace z `first` k `last`. V kroku musí být kladná. [invalid_argument –](../../../standard-library/invalid-argument-class.md) je vyvolána, pokud v kroku je menší než 1.

*_Func*<br/>
Funkce, který se spustí při každé iteraci. To může být výraz lambda, ukazatele na funkci nebo některý objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()(_Index_type)`.

*_Part –*<br/>
Odkaz na objekt rozdělovač. Argument může být jedna z `const` [auto_partitioner –](auto-partitioner-class.md)`&`, `const` [static_partitioner –](static-partitioner-class.md)`&`, `const` [simple_ dělicí metoda](simple-partitioner-class.md) `&` nebo [affinity_partitioner –](affinity-partitioner-class.md) `&` Pokud [affinity_partitioner –](affinity-partitioner-class.md) objekt se používá, odkaz musí být nekonstantní l-value odkazovat, tak, aby algoritmus může ukládání stavu pro budoucí cykly znovu použít.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="parallel_for_each"></a>  parallel_for_each

`parallel_for_each` použije zadanou funkci na každý prvek v rozsahu, paralelní. Je sémanticky rovnocenné `for_each` fungovat v `std` obor názvů, s výjimkou danou iteraci přes prvky se provádí paralelní a pořadí iterace není zadána. Argument `_Func` musí podporovat operátor volání funkce formuláře `operator()(T)` kde parametr `T` je typ položky kontejneru se provést iteraci.

```
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ iterátoru, který se používá k iteraci přes kontejneru.

*_Function*<br/>
Typ funkce, která se použije na každý prvek v rozsahu.

*_Partitioner*<br/>
*první*<br/>
Iterátor adresuje umístění prvního prvku mají být zahrnuty v paralelní iterace.

*last*<br/>
Iterátor adresuje umístění jedno místo za posledním prvkem mají být zahrnuty v paralelní iterace.

*_Func*<br/>
Uživatelem definované funkce objektu, který se použije na každý prvek v rozsahu.

*_Part –*<br/>
Odkaz na objekt rozdělovač. Argument může být jedna z `const` [auto_partitioner –](auto-partitioner-class.md)`&`, `const` [static_partitioner –](static-partitioner-class.md)`&`, `const` [simple_ dělicí metoda](simple-partitioner-class.md) `&` nebo [affinity_partitioner –](affinity-partitioner-class.md) `&` Pokud [affinity_partitioner –](affinity-partitioner-class.md) objekt se používá, odkaz musí být nekonstantní l-value odkazovat, tak, aby algoritmus může ukládání stavu pro budoucí cykly znovu použít.

### <a name="remarks"></a>Poznámky

[auto_partitioner –](auto-partitioner-class.md) se použije pro přetížení bez explicitního dělicí metody.

U iterátorů, které nepodporují náhodný přístup pouze k [auto_partitioner –](auto-partitioner-class.md) je podporována.

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="parallel_invoke"></a>  parallel_invoke

Spustí funkci objekty zadané jako parametry v paralelních a blokuje, dokud se nedokončí provádění. Každý objekt funkce může být výraz lambda, ukazatele na funkce, nebo žádný objekt, který podporuje operátor volání funkce s podpisem `void operator()()`.

```
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>Parametry

*_Function1*<br/>
Typ první objekt funkce provádět paralelně.

*_Function2*<br/>
Typ druhého objektu funkce provádět paralelně.

*_Function3*<br/>
Typ třetí objekt funkce, který se spustí paralelně.

*_Function4*<br/>
Typ čtvrtý objekt funkce, který se spustí paralelně.

*_Function5*<br/>
Typ páté objekt funkce, který se spustí paralelně.

*_Function6*<br/>
Typ šestého objekt funkce, který se spustí paralelně.

*_Function7*<br/>
Typ sedmého objekt funkce, který se spustí paralelně.

*_Function8*<br/>
Typ osmého objekt funkce, který se spustí paralelně.

*_Function9*<br/>
Typ devátého objekt funkce, který se spustí paralelně.

*_Function10*<br/>
Typ desátý objekt funkce, který se spustí paralelně.

*_Func1*<br/>
První objekt funkce provádět paralelně.

*_Func2*<br/>
Druhý objekt funkce provádět paralelně.

*_Func3*<br/>
Třetí objekt funkce provádět paralelně.

*_Func4*<br/>
Čtvrtý objekt funkce provádět paralelně.

*_Func5*<br/>
Pátý objekt funkce provádět paralelně.

*_Func6*<br/>
Šestý objekt funkce provádět paralelně.

*_Func7*<br/>
Sedmý objekt funkce provádět paralelně.

*_Func8*<br/>
Objekt osmého funkce provádět paralelně.

*_Func9*<br/>
Devátý objekt funkce provádět paralelně.

*_Func10*<br/>
Objekt desátý funkce provádět paralelně.

### <a name="remarks"></a>Poznámky

Všimněte si, že jeden nebo více objektů funkce zadaná jako parametry může spustit vložené na kontext volání.

Pokud jeden nebo více objektů funkce předány jako parametry této funkce dojde k výjimce, modul runtime vyberte jeden takový výjimka jeho výběru, který se šířit z volání `parallel_invoke`.

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="parallel_radixsort"></a>  parallel_radixsort

Uspořádá prvky v zadaném rozsahu do bez sestupném pořadí pomocí základ algoritmu řazení. Toto je funkce stabilní řazení, která vyžaduje projekce funkci, která můžete promítnout prvků, které se dají seřadit podle nepodepsaných klíčů jako celé číslo. Výchozí inicializace je požadovaná pro se setříděnými prvky.

```
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>Parametry

*_Random_iterator*<br/>
Typ iterátoru vstupním rozsahu.

*_Allocator*<br/>
Typ alokátoru paměti kompatibilní standardní knihovny C++.

*_Function*<br/>
Typ funkce projekce.

*_Zahájit*<br/>
Iterátor s náhodným přístupem adresuje umístění prvního prvku v rozsahu který se má seřadit.

*_End*<br/>
Iterátor s náhodným přístupem adresuje umístění jedno místo za poslední prvek v rozsahu který se má seřadit.

*_Alloc*<br/>
Instance Přidělovač paměti kompatibilní standardní knihovny C++.

*_Proj_func*<br/>
Projekce uživatelem definovaný objekt funkce, který převede prvek na celočíselnou hodnotu.

*_Chunk_size*<br/>
Minimální velikost bloku dat, který bude možné rozdělit na dvě pro paralelní zpracování.

### <a name="remarks"></a>Poznámky

Všechna přetížení vyžadují `n * sizeof(T)` další místo, kde `n` je počet prvků který se má seřadit, a `T` je typ prvku. Funktor unární projekce s podpisem `I _Proj_func(T)` je potřeba vrátit klíč, pokud zadaný prvek, kde `T` je typ prvku a `I` je typ jako celé číslo bez znaménka.

Pokud nezadáte projekce funkce, výchozí projekce funkce, které jednoduše vrátí hodnotu prvku se používá pro integrální typy. Funkce se nezdaří pro kompilaci, pokud element není celočíselného typu chybí funkce projekce.

Pokud nezadáte k alokátoru typu nebo instance, přidělení paměti standardní knihovny C++ `std::allocator<T>` se používá k přidělení vyrovnávací paměti.

Algoritmus rozděluje vstupním rozsahu do dvou bloků dat a postupně jednotlivé bloky rozdělí dvě dílčí bloky dat pro spuštění paralelně. Volitelný argument `_Chunk_size` slouží k označení algoritmus, že by měl zpracovává bloky o velikosti < `_Chunk_size` sériově.

##  <a name="parallel_reduce"></a>  parallel_reduce

Vypočítá součet všech prvků v zadaném rozsahu, podle výpočtu po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků podobně získaných pomocí zadané binární operace, než součtem, paralelně. `parallel_reduce` je sémanticky podobné `std::accumulate`, s tím rozdílem, že vyžaduje asociativní binární operace a vyžaduje hodnotu identity místo počáteční hodnoty.

```
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>Parametry

*_Forward_iterator*<br/>
Typ iterátoru vstupním rozsahu.

*_Sym_reduce_fun*<br/>
Typ funkce symetrický snížení. Toto musí být typu funkce s podpisem `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, kde _Reduce_type je stejný jako typ identity a výsledný typ omezení. Pro třetí přetížení, to by měl být konzistentní s typem výstupu `_Range_reduce_fun`.

*_Reduce_type*<br/>
Typ, který omezí vstup, který může být odlišný od typu elementu input. Tento typ se má návratovou hodnotu a hodnotu identity.

*_Range_reduce_fun*<br/>
Typ funkce omezení rozsahu. Toto musí být typu funkce s podpisem `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type je stejný jako typ identity a výsledný typ omezení.

*_Zahájit*<br/>
Vstupní iterátor adresující první prvek v rozsahu sníží.

*_End*<br/>
Vstupní iterátor adresující prvek, který je o jednu pozici za posledním prvkem v rozsahu, který chcete zmenšit.

*_Identity*<br/>
Hodnota identity `_Identity` je stejného typu jako výsledek typu snížení a také `value_type` iterátoru pro první a druhé přetížení. Pro třetí přetížení, musí být stejného typu jako výsledek typu snížení hodnoty identity, ale může lišit od `value_type` iterátoru. Musí mít odpovídající hodnotu tak, že operátor snížení rozsahu `_Range_fun`, při použití na celou řadu jeden element typu `value_type` a hodnotu identity, se chová jako přetypování z typu hodnoty `value_type` pro typ identity.

*_Sym_fun*<br/>
Symetrický funkce, která se použije ve druhém snížení. Další informace naleznete na poznámky.

*_Range_fun*<br/>
Funkce, která se použije v první fázi snížení. Další informace naleznete na poznámky.

### <a name="return-value"></a>Návratová hodnota

Výsledek snížení.

### <a name="remarks"></a>Poznámky

Funkci provádět paralelní redukci rozdělí rozsah do bloků dat na základě počtu pracovních procesů, které jsou k dispozici do příslušného plánovače. Snížení dojde ve dvou fázích, první fáze provede snížení v rámci každého bloku a druhé fáze provede snížení mezi částečné výsledky z každého bloku.

První přetížení vyžaduje, aby iterátoru `value_type`, `T`, být stejný jako typ hodnoty identity, jakož i omezení typu výsledku. Element typu T musí poskytovat operátor `T T::operator + (T)` ke snížení prvky v každého bloku. Ve druhé fázi se používá stejný operátor.

Druhé přetížení také vyžaduje, aby iterátoru `value_type` být stejný jako typ hodnoty identity, jakož i omezení typu výsledku. Zadaný binární operátor `_Sym_fun` se používá v obě tyto fáze snížení, s hodnotu identity jako počáteční hodnota pro první fázi.

Třetí přetížení, typ hodnoty identity musí být stejné jako omezení typu výsledku, ale iterátoru `value_type` může lišit od obou. Funkce omezení rozsahu `_Range_fun` se používá v první fázi s hodnotu identity jako výchozí hodnoty a binární funkce `_Sym_reduce_fun` se použije na dílčí výsledky ve druhé fázi.

##  <a name="parallel_sort"></a>  parallel_sort –

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem paralelně. Tato funkce je sémanticky podobné `std::sort` v tom, že je na základě porovnání, nestabilní, místní řazení.

```
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parametry

*_Random_iterator*<br/>
Typ iterátoru vstupním rozsahu.

*_Function*<br/>
Typ funktor binární porovnání.

*_Zahájit*<br/>
Iterátor s náhodným přístupem adresuje umístění prvního prvku v rozsahu který se má seřadit.

*_End*<br/>
Iterátor s náhodným přístupem adresuje umístění jedno místo za poslední prvek v rozsahu který se má seřadit.

*_Func*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání vyhovět pomocí po sobě jdoucí prvky v pořadí. Binární predikát přijímá dva argumenty a vrací **true** při splnění a **false** pokud nevyhovují. Tato funkce porovnání musí uložit přísné slabé seřazení na dvojice prvků z posloupnosti.

*_Chunk_size*<br/>
Minimální velikost bloku dat, který bude možné rozdělit na dvě pro paralelní zpracování.

### <a name="remarks"></a>Poznámky

První přetížení používá binární porovnání `std::less`.

Druhé přetížení používá zadané binární Komparátor, který by měl mít podpis `bool _Func(T, T)` kde `T` je typ prvků ve vstupním rozsahu.

Algoritmus rozděluje vstupním rozsahu do dvou bloků dat a postupně jednotlivé bloky rozdělí dvě dílčí bloky dat pro spuštění paralelně. Volitelný argument `_Chunk_size` slouží k označení algoritmus, že by měl zpracovává bloky o velikosti < `_Chunk_size` sériově.

##  <a name="parallel_transform"></a>  parallel_transform

Zadaný objekt funkce se vztahuje na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu, paralelně. Tuto funkční je sémanticky ekvivalentní `std::transform`.

```
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>Parametry

*_Input_iterator1*<br/>
Typ první nebo pouze vstupní iterátor.

*_Output_iterator*<br/>
Typ výstupního iterátoru.

*_Unary_operator*<br/>
Typ unární funktor, který se spustí na každý prvek ve vstupním rozsahu.

*_Input_iterator2*<br/>
Typ druhé vstupní iterátor.

*_Binary_operator*<br/>
Typ binární funktor ukládání spuštěné na prvky ze dvou zdrojových rozsahů.

*_Partitioner*<br/>
*first1*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v první nebo pouze zdrojového rozsahu do ho zpracovat.

*last1*<br/>
Vstupní iterátor, který adresuje umístění jedno místo za posledním prvkem v prvním nebo pouze zdrojového rozsahu do ho zpracovat.

*_Result*<br/>
Výstupní iterace adresující pozici prvního prvku v cílové oblasti.

*_Unary_op*<br/>
Uživatelem definovaný objekt jednočlenné funkce, která se aplikuje na každý prvek ve zdrojovém rozsahu.

*_Part –*<br/>
Odkaz na objekt rozdělovač. Argument může být jedna z `const` [auto_partitioner –](auto-partitioner-class.md)`&`, `const` [static_partitioner –](static-partitioner-class.md)`&`, `const` [simple_ dělicí metoda](simple-partitioner-class.md) `&` nebo [affinity_partitioner –](affinity-partitioner-class.md) `&` Pokud [affinity_partitioner –](affinity-partitioner-class.md) objekt se používá, odkaz musí být nekonstantní l-value odkazovat, tak, aby algoritmus může ukládání stavu pro budoucí cykly znovu použít.

*first2*<br/>
Vstupní iterátor, který adresuje umístění prvního prvku v druhé zdrojové oblasti ho zpracovat.

*_Binary_op*<br/>
Objekt binární funkce definované uživatelem, který se použije ukládání, v pořadí dopředu, do dvou zdrojových rozsahů.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterace adresující jedna pozice za posledním prvkem v cílovém rozsahu, který přijímá výstup elementy transformovány sadou objektu funkce.

### <a name="remarks"></a>Poznámky

[auto_partitioner –](auto-partitioner-class.md) se použije pro přetížení bez argumentu explicitní rozdělovač.

U iterátorů, které nepodporují náhodný přístup pouze k [auto_partitioner –](auto-partitioner-class.md) je podporována.

Přetížení, která trvat argumentu `_Unary_op` transformace vstupním rozsahu do výstupní oblasti s použitím funktor unární na každý prvek ve vstupním rozsahu. `_Unary_op` operátor volání funkce s podpisem, musí podporovat `operator()(T)` kde `T` je typ hodnoty rozsahu se provést iteraci.

Přetížení, která trvat argumentu `_Binary_op` transformace dva vstupní rozsahy do výstupní oblasti použitím binární funktor na jeden element z první vstupním rozsahu a jeden element z druhého vstupu rozsahu. `_Binary_op` operátor volání funkce s podpisem, musí podporovat `operator()(T, U)` kde `T`, `U` jsou typy hodnot iterátorů dva vstupní.

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

##  <a name="receive"></a>  Zobrazit

Obecné přijímat implementace, což kontextu pro čekání na data z přesně jeden zdroj a filtrování hodnot, které byly přijaty.

```
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ datové části.

*_Src*<br/>
Ukazatel nebo odkaz na zdroj, ze kterého je očekávána data.

*_Vypršení časového limitu*<br/>
Maximální doba, pro který by měl metodu data v milisekundách.

*_Filter_proc*<br/>
Funkce filtru, která určuje, zda by měl přijmout zprávy.

### <a name="return-value"></a>Návratová hodnota

Hodnota ze zdroje typu datové části.

### <a name="remarks"></a>Poznámky

Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out –](operation-timed-out-class.md) je vyvolána, pokud před doručení zprávy do vypršení platnosti určenou dobu. Pokud chcete, aby žádný časový limit délky, měli byste použít [try_receive –](concurrency-namespace-functions.md) funkce, na rozdíl od volání `receive` s časovým `0` (nula), protože je mnohem efektivnější a nevyvolá výjimky na vypršení časového limitu.

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token –

Objekt funkce spustí v kontextu daného rušícího tokenu okamžitě a synchronně.

```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, která bude vyvolána.

*_Func*<br/>
Objekt funkce, která se spustí. Operátor volání funkce s podpisem void(void) musí podporovat tento objekt.

*_Ct*<br/>
Token rušení, který bude řídit implicitní zrušení objektu funkce. Použití `cancellation_token::none()` Pokud chcete funkci provést udeří nějaká implicitní zrušení z nadřazené skupiny úloh se zrušilo.

### <a name="remarks"></a>Poznámky

Všechny body přerušení v objektu funkce budou při aktivaci `cancellation_token` se zruší. Explicitní token `_Ct` izoluje to `_Func` z nadřazené zrušení, pokud má nadřazená token jiný nebo žádný token.

##  <a name="send"></a>  Odeslat

Odesílání synchronní operace, která čeká na cíl přijme nebo odmítne zprávy.

```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ datové části.

*_Trg*<br/>
Ukazatel nebo odkaz na cíl, do kterého se data odesílají.

*_Data*<br/>
Odkaz na data, která mají být odeslány.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud byla přijata zpráva, **false** jinak.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler

```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parametry

*_Scheduler*<br/>
Vedlejší Plánovač, aby nastavení.

##  <a name="set_task_execution_resources"></a>  set_task_execution_resources –

Omezuje provádění prostředky využívané třídou interní pracovní vlákna Concurrency Runtime přidružení zadána sada.

Je možné tuto metodu volat pouze před správce prostředků se vytvořila, nebo mezi dvěma životnosti Resource Manageru. Může být vyvolán více než jednou za předpokladu, správce prostředků v době vyvolání neexistuje. Po nastavení limit spřažení zůstává v platnosti až do další platné volání `set_task_execution_resources` metody.

Zadaná maska spřažení nemusí být podmnožinou Maska spřažení procesu. Proces spřažení aktualizují i v případě potřeby.

```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parametry

*_ProcessAffinityMask*<br/>
Maska spřažení, která mají být omezena na pracovních vláken Concurrency Runtime. Tuto metodu lze použijte v systému s více než 64 hardwarových vláken pouze v případě, že byste měli omezit na podmnožinu aktuální skupinu procesorů Concurrency Runtime. Obecně byste měli používat verzi metody, která přijímá pole spřažení skupiny jako parametr, chcete-li omezit spřažení na počítačích s více než 64 hardwarových vláken.

*Počet*<br/>
Počet `GROUP_AFFINITY` položky v poli určeném parametrem `_PGroupAffinity`.

*_PGroupAffinity*<br/>
Pole `GROUP_AFFINITY` položky.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_operation –](invalid-operation-class.md) výjimku, pokud je k dispozici v době, je vyvolána, správce prostředků a [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimku, pokud zadané spřažení v prázdnou sadu výsledků prostředky.

Verze metody, která přijímá jako parametr pole spřažení skupiny musí být pouze používaných v systémech s verzí Windows 7 nebo vyšší. V opačném případě [invalid_operation –](invalid-operation-class.md) je vyvolána výjimka.

Programově úprava vztahů proces po zavolání této metody nezpůsobí Resource Manageru k opětovnému vyhodnocení, které je omezen na spřažení. Všechny změny ke zpracování vztahů by se proto před voláním této metody.

##  <a name="swap"></a>  Prohození

Vymění prvky dvou `concurrent_vector` objekty.

```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžné vektorů.

*_Ax*<br/>
Typ alokátoru souběžných vektorů.

*_A*<br/>
Souběžného vektoru, jehož prvky mají být zaměněny souběžného vektoru `_B`.

*_B*<br/>
Souběžného vektoru poskytující prvky pro záměnu nebo vektor, jehož prvky mají být zaměněny souběžného vektoru `_A`.

### <a name="remarks"></a>Poznámky

Funkce šablon je algoritmus specializované třídy kontejneru `concurrent_vector` ke spuštění funkce člena `_A`. [concurrent_vector::swap](concurrent-vector-class.md#swap)( `_B`). Toto jsou instance částečné řazení šablon funkcí v kompilátoru. Pokud funkce šablony jsou přetížené tak, že shoda šablony pomocí volání funkce není jedinečný, pak kompilátor zvolit nejvíce specializovanou verzi šablony funkce. Obecné verzi funkce šablony `template <class T> void swap(T&, T&)`, v algoritmu třída pracuje podle přiřazení a je pomalá operace. Specializované verze v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s vnitřní reprezentaci třídy kontejneru.

Tato metoda není bezpečná pro souběžnost. Ujistěte se, že nejsou žádná jiná vlákna provádění operací v jedné ze souběžných vektory při volání této metody.

##  <a name="task_from_exception"></a>  task_from_exception

```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parametry

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Návratová hodnota

##  <a name="task_from_result"></a>  task_from_result –

```
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parametry

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Návratová hodnota

##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name –

Přidruží daný název bloku zpráv nebo agenta v trasování ETW.

```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu. Obvykle je blok zpráv nebo agenta.

*_PObject*<br/>
Ukazatel na blok zpráv nebo agenta, který se jmenuje trasování.

*_Název*<br/>
Název pro daný objekt.

##  <a name="try_receive"></a>  try_receive –

Obecné try a přijetí implementace, povolení kontextu vyhledat data z přesně jednoho zdroje a filtrování hodnot, které byly přijaty. Pokud data nejsou připravené, metoda vrátí **false**.

```
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ datové části

*_Src*<br/>
Ukazatel nebo odkaz na zdroj, ze kterého je očekávána data.

*_value*<br/>
Odkaz na umístění, kde budou umístěné výsledek.

*_Filter_proc*<br/>
Funkce filtru, která určuje, zda by měl přijmout zprávy.

### <a name="return-value"></a>Návratová hodnota

A `bool` hodnotu označující, zda byl datové části je umístěn v `_value`.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

##  <a name="wait"></a>  Počkej

Pozastaví aktuální kontext pro určenou dobu.

```
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parametry

*_Milliseconds*<br/>
Počet milisekund, po které aktuálního kontextu by měla pro pozastaveno. Pokud `_Milliseconds` parametr je nastaven na hodnotu `0`, aktuálním kontextu by měla yield v provádění dalších spustitelných kontexty než budete pokračovat.

### <a name="remarks"></a>Poznámky

Pokud tato metoda je volána u objektu context Plánovač Concurrency Runtime, Plánovač najdete jiný kontext pro spuštění na tento základní prostředek spravovat. Vzhledem k tomu, že plánovač má kooperativní charakter, nelze obnovit tento kontext přesně po počet milisekund. Pokud plánovač je zaneprázdněný, provádění další úloh, které neposkytují kooperativně plánovači, může být doba čekání neomezené.

##  <a name="when_all"></a>  when_all –

Vytvoří úlohu, která bude dokončena úspěšně, pokud všechny úlohy uvedené jako argumenty úspěšně dokončena.

```
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ vstupního iterátoru.

*_Zahájit*<br/>
Pozice prvního prvku v rozsahu prvků se zkombinuje do výsledného úkolu.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků se zkombinuje do výsledného úkolu.

*_TaskOptions*<br/>
`task_options` Objektu.

### <a name="return-value"></a>Návratová hodnota

Úloha, která se úspěšně dokončí, když všechny vstupní úlohy byly úspěšně dokončeny. Pokud jsou vstupní úlohy typu `T`, bude výstup této funkce `task<std::vector<T>>`. Pokud jsou vstupní úlohy typu `void` výstupní úloha bude také `task<void>`.

### <a name="remarks"></a>Poznámky

`when_all` je neblokující funkce, která vytváří `task` jako svůj výsledek. Na rozdíl od [task::wait](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (Application STA).

Pokud jeden z úkolů zrušen nebo vyvolá výjimku, vrácené úlohy budou dokončeny včas ve zrušeném stavu a, pokud je encoutered, bude vyvolána výjimka při volání [task::get](task-class.md#get) nebo `task::wait` pro tento úkol.

Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="when_any"></a>  when_any –

Vytvoří úlohu, která bude dokončena úspěšně, pokud některá z úloh zadané jako argumenty úspěšně dokončena.

```
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ vstupního iterátoru.

*_Zahájit*<br/>
Pozice prvního prvku v rozsahu prvků se zkombinuje do výsledného úkolu.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků se zkombinuje do výsledného úkolu.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token zrušení, který řídí zrušení vrácených úloh. Pokud nezadáte token zrušení, výsledná úloha obdrží token zrušení úkolu, který způsobí její dokončení.

### <a name="return-value"></a>Návratová hodnota

Úloha, která se úspěšně dokončí, když některý vstupní úlohy byla úspěšně dokončena. Pokud jsou vstupní úlohy typu `T`, bude výstup této funkce `task<std::pair<T, size_t>>>`, kde první prvek dvojice je výsledkem dokončující úlohy a druhý prvek je indexem dokončené úlohy. Pokud jsou vstupní úlohy typu `void` je výstup `task<size_t>`, kde výsledkem je index dokončující úlohy.

### <a name="remarks"></a>Poznámky

`when_any` je neblokující funkce, která vytváří `task` jako svůj výsledek. Na rozdíl od [task::wait](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (Application STA).

Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
