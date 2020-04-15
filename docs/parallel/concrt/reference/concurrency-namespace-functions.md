---
title: concurrency – funkce oboru názvů
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
ms.openlocfilehash: 15b265744640628425502706d69fd98a1c64bda2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374376"
---
# <a name="concurrency-namespace-functions"></a>concurrency – funkce oboru názvů

||||
|-|-|-|
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|
|[EnableTracing](#enabletracing)|[Free](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[Getosversion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[Jasné](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[Přijímat](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[Odeslat](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[Swap](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Počkej](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a><a name="alloc"></a>Alloc

Přidělí blok paměti velikosti zadané z souběžnosti Runtime Ukládání do mezipaměti Suballocator.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parametry

*_NumBytes*<br/>
Počet bajtů paměti přidělit.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Další informace o scénářích ve vaší aplikaci by mohly mít prospěch z použití suballocator ukládání do mezipaměti, naleznete v [tématu Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a><a name="asend"></a>asend

Asynchronní operace odesílání, která naplánuje úlohu k šíření dat do cílového bloku.

```cpp
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
Typ dat, která mají být odeslána.

*_Trg*<br/>
Ukazatel nebo odkaz na cíl, ke kterému jsou data odesílána.

*_Data*<br/>
Odkaz na data, která mají být odeslána.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud byla zpráva přijata před vrácenou metodou, **false** jinak.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a><a name="cancel_current_task"></a>cancel_current_task

Zruší aktuálně spuštěnou úlohu. Tato funkce může být volána z těla úlohy přerušit provádění úlohy `canceled` a způsobit jeho zadání stavu.

Není podporovaný scénář volání této funkce, pokud nejste v `task`těle . Pokud tak učiníte, bude mít za následek nedefinované chování, jako je například selhání nebo zablokování v aplikaci.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a><a name="clear"></a>Jasné

Vymaže souběžnou frontu a zničí všechny aktuálně zařazené prvky. Tato metoda není bezpečné souběžnosti.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parametry

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a><a name="create_async"></a>create_async

Vytvoří asynchronní konstrukci prostředí Windows Runtime založenou na uživateli zadaném lambda nebo objektu funkce. `create_async` Návratový typ je jeden `IAsyncAction^` `IAsyncActionWithProgress<TProgress>^`z `IAsyncOperation<TResult>^`, `IAsyncOperationWithProgress<TResult, TProgress>^` , nebo na základě podpisu lambda předán metodě.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ.

*_Func*<br/>
Lambda nebo objekt funkce, ze kterého chcete vytvořit asynchronní konstrukci prostředí Windows Runtime.

### <a name="return-value"></a>Návratová hodnota

Asynchronní konstrukce reprezentovaná iAsyncAction^, IAsyncActionWithProgress\<TProgress>\<^, IAsyncOperation TResult>\<^, nebo IAsyncOperationWithProgress TResult, TProgress>^. Vrácené rozhraní závisí na podpisu lambda předándo funkce.

### <a name="remarks"></a>Poznámky

Návratový typ lambda určuje, zda je konstrukce akce nebo operace.

Lambdas, které vracejí prázdnotu způsobit vytvoření akcí. Lambdas, které vracejí `TResult` výsledek typu způsobit vytvoření operací TResult.

Lambda může také `task<TResult>` vrátit, který zapouzdřuje aysnchronní práci v rámci sebe nebo je pokračování mnoství úkoly, které představují asynchronní práce. V tomto případě lambda sám je proveden vřádí, protože úkoly jsou ty, které se provádějí asynchronně a návratový typ lambda je `create_async`rozbalen k výrobě asynchronní konstrukce vrácena . To znamená, že lambda,\<který vrací> neplatné úlohy způsobí vytvoření akcí\<a lambda, který vrátí úkol TResult> způsobí vytvoření operací TResult.

Lambda může trvat buď nula, jeden nebo dva argumenty. Platné argumenty `progress_reporter<TProgress>` jsou `cancellation_token`a , v tomto pořadí, pokud jsou použity obě. Lambda bez argumentů způsobí vytvoření asynchronní konstrukce bez schopnosti pro vykazování průběhu. Lambda, která trvá\<progress_reporter TProgress `create_async`> způsobí vrátit asynchronní konstrukce, která hlásí `report` průběh typu TProgress pokaždé, když je volána metoda progress_reporter objektu. Lambda, která trvá cancellation_token může použít tento token ke kontrole zrušení nebo předat úkoly, které vytvoří tak, aby zrušení asynchronní konstrukce způsobí zrušení těchto úkolů.

Pokud tělo lambda nebo objekt funkce vrátí výsledek (a nikoli úlohu\<TResult>), lamdba bude spuštěna asynchronně v rámci procesu MTA v kontextu úlohy, kterou pro něj modul Runtime implicitně vytvoří. Metoda `IAsyncInfo::Cancel` způsobí zrušení implicitní úlohy.

Pokud tělo lambda vrátí úkol, lamba provede vřádí a deklarováním lambda přijmout `cancellation_token` argument typu můžete aktivovat zrušení všech úkolů, které vytvoříte v rámci lambda předáním tohoto tokenu při jejich vytvoření. Můžete také použít `register_callback` metodu na tokenu způsobit Runtime vyvolat zpětné `IAsyncInfo::Cancel` volání při volání na asynchronní operace nebo akce vyrobené..

Tato funkce je k dispozici pouze pro aplikace prostředí Windows Runtime.

## <a name="createresourcemanager"></a><a name="createresourcemanager"></a>CreateResourceManager

Vrátí rozhraní, které představuje instanci singleton správce prostředků modulu Runtime souběžnosti. Správce prostředků je zodpovědný za přiřazení zdrojů plánovačům, kteří chtějí vzájemně spolupracovat.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní. `IResourceManager`

### <a name="remarks"></a>Poznámky

Více následných volání této metody vrátí stejnou instanci Správce prostředků. Každé volání metody se zpřísňuje počet odkazů na Správce prostředků a musí být spárováno s voláním [metody IResourceManager::Release,](iresourcemanager-structure.md) když plánovač provádí komunikaci se Správcem prostředků.

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulrunu souběžnosti.

## <a name="create_task"></a><a name="create_task"></a>create_task

Vytvoří objekt [úlohy](task-class.md) PPL. `create_task`lze použít kdekoli, kde byste použili konstruktor úlohy. Je poskytována především pro pohodlí, protože umožňuje `auto` použití klíčového slova při vytváření úkolů.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru, ze kterého má být úloha vytvořena.

*_ReturnType*<br/>
Typ.

*_Param*<br/>
Parametr, ze kterého má být úkol vytvořen. To může být lambda nebo `task_completion_event` objekt funkce, `task` objekt, jiný objekt nebo rozhraní Windows::Foundation::IAsyncInfo, pokud používáte úkoly v aplikaci UPW.

*_TaskOptions*<br/>
Možnosti úkolu.

*_Task*<br/>
Úkol vytvořit.

### <a name="return-value"></a>Návratová hodnota

Nový úkol typu `T`, který je `_Param`odvozen z .

### <a name="remarks"></a>Poznámky

První přetížení se chová jako konstruktor úlohy, který přebírá jeden parametr.

Druhé přetížení přidruží token zrušení poskytované s nově vytvořenou úlohou. Pokud použijete toto přetížení, není povoleno `task` předat v jiném objektu jako první parametr.

Typ vrácené úlohy je odvozen z prvního parametru do funkce. Pokud `_Param` je `task_completion_event<T>`, `task<T>`a , nebo functor, `task<T>`který vrací buď typ `task<T>` `T` nebo , typ vytvořeného úkolu je .

V aplikaci `_Param` UPW, pokud je typu Windows::Foundation::IAsyncOperation\<T>^ nebo Windows::Foundation::IAsyncOperationWithProgress\<T,P>^, nebo functor, který vrátí jeden z těchto typů, bude vytvořená úloha typu `task<T>`. Pokud `_Param` je typu Windows::Foundation::IAsyncAction^ nebo Windows::Foundation::IAsyncActionWithProgress\<P>^, nebo functor, který vrátí `task<void>`jeden z těchto typů, bude mít vytvořená úloha typ .

## <a name="disabletracing"></a><a name="disabletracing"></a>DisableTracing

Zakáže trasování v době runtime souběžnosti. Tato funkce je zastaralá, protože trasování ETW je ve výchozím nastavení neregistrované.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Návratová hodnota

Pokud bylo trasování `S_OK` správně zakázáno, je vráceno. Pokud trasování nebylo dříve `E_NOT_STARTED` zahájeno, je vrácena

## <a name="enabletracing"></a><a name="enabletracing"></a>EnableTracing

Umožňuje trasování v době runtime souběžnosti. Tato funkce je zastaralá, protože trasování ETW je nyní ve výchozím nastavení zapnuto.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Návratová hodnota

Pokud bylo trasování správně `S_OK` zahájeno, je vráceno; v `E_NOT_STARTED` opačném případě je vrácena.

## <a name="free"></a><a name="free"></a>Zdarma

Uvolní blok paměti dříve přidělené `Alloc` metodou souběžnosti Runtime Ukládání do mezipaměti Suballocator.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parametry

*_PAllocation*<br/>
Ukazatel na paměť dříve přidělené metodou, `Alloc` která má být uvolněna. Pokud je `_PAllocation` parametr nastaven `NULL`na hodnotu , tato metoda ji bude ignorovat a okamžitě se vrátí.

### <a name="remarks"></a>Poznámky

Další informace o scénářích ve vaší aplikaci by mohly mít prospěch z použití suballocator ukládání do mezipaměti, naleznete v [tématu Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a><a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Návratová hodnota

## <a name="getexecutioncontextid"></a><a name="getexecutioncontextid"></a>GetExecutionContextId

Vrátí jedinečný identifikátor, který lze přiřadit k kontextu `IExecutionContext` spuštění, který implementuje rozhraní.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro kontext spuštění.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete získat identifikátor pro kontext `IExecutionContext` spuštění před předáním rozhraní jako parametru některé z metod nabízených Správcem prostředků.

## <a name="getosversion"></a><a name="getosversion"></a>Getosversion

Vrátí verzi operačního systému.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Návratová hodnota

Výčet hodnoty představující operační systém.

### <a name="remarks"></a>Poznámky

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulrunu souběžnosti.

## <a name="getprocessorcount"></a><a name="getprocessorcount"></a>GetProcessorCount

Vrátí počet hardwarových vláken v základním systému.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet hardwarových vláken.

### <a name="remarks"></a>Poznámky

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulrunu souběžnosti.

## <a name="getprocessornodecount"></a><a name="getprocessornodecount"></a>GetProcessorNodeCount

Vrátí počet uzlů NUMA nebo balíčků procesorů v základním systému.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet uzlů NUMA nebo balíčků procesoru.

### <a name="remarks"></a>Poznámky

Pokud systém obsahuje více uzlů NUMA než balíčky procesoru, je vrácen počet uzlů NUMA, jinak je vrácen počet balíčků procesoru.

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud operační systém není podporován modulrunu souběžnosti.

## <a name="getschedulerid"></a><a name="getschedulerid"></a>GetSchedulerId

Vrátí jedinečný identifikátor, který lze přiřadit plánovači, `IScheduler` který implementuje rozhraní.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor plánovače.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete získat identifikátor plánovače `IScheduler` před předáním rozhraní jako parametru některé z metod nabízených Správcem prostředků.

## <a name="internal_assign_iterators"></a><a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
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

*První*<br/>

*Poslední*<br/>

## <a name="interruption_point"></a><a name="interruption_point"></a>interruption_point

Vytvoří bod přerušení pro zrušení. Pokud zrušení probíhá v kontextu, kde je volána tato funkce, to vyvolá vnitřní výjimku, která přeruší provádění aktuálně provádějící paralelní práce. Pokud zrušení neprobíhá, funkce neprovede žádné.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Poznámky

Neměli byste zachytit vnitřní zrušení výjimky `interruption_point()` vyvolána funkce. Výjimka bude zachycena a zpracována za běhu a zachycení může způsobit, že se program bude chovat abnormálně.

## <a name="is_current_task_group_canceling"></a><a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Vrátí údaj o tom, zda je skupina úloh, která je aktuálně provádění vazby na aktuální kontext je uprostřed aktivní zrušení (nebo bude brzy). Všimněte si, že pokud neexistuje žádná skupina úloh aktuálně `false` provádění vazby na aktuální kontext, budou vráceny.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud skupina úloh, která právě provádí, je zrušení, **false** jinak.

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [Zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a><a name="make_choice"></a>make_choice

Vytvoří blok `choice` zasílání zpráv z `Scheduler` `ScheduleGroup` volitelné nebo a dva nebo více vstupních zdrojů.

```cpp
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
Objekt, `Scheduler` ve kterém je naplánováno `choice` úlohy šíření pro blok zasílání zpráv.

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Items*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
Objekt, `ScheduleGroup` ve kterém je naplánováno `choice` úlohy šíření pro blok zasílání zpráv. Použitý `Scheduler` objekt je implikován skupinou plánu.

### <a name="return-value"></a>Návratová hodnota

Blok `choice` zpráv se dvěma nebo více vstupními zdroji.

## <a name="make_greedy_join"></a><a name="make_greedy_join"></a>make_greedy_join

Vytvoří blok `greedy multitype_join` zasílání zpráv z `Scheduler` `ScheduleGroup` volitelné nebo a dva nebo více vstupních zdrojů.

```cpp
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
Objekt, `Scheduler` ve kterém je naplánováno `multitype_join` úlohy šíření pro blok zasílání zpráv.

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Items*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
Objekt, `ScheduleGroup` ve kterém je naplánováno `multitype_join` úlohy šíření pro blok zasílání zpráv. Použitý `Scheduler` objekt je implikován skupinou plánu.

### <a name="return-value"></a>Návratová hodnota

Blok `greedy multitype_join` zpráv se dvěma nebo více vstupními zdroji.

## <a name="make_join"></a><a name="make_join"></a>make_join

Vytvoří blok `non_greedy multitype_join` zasílání zpráv z `Scheduler` `ScheduleGroup` volitelné nebo a dva nebo více vstupních zdrojů.

```cpp
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
Objekt, `Scheduler` ve kterém je naplánováno `multitype_join` úlohy šíření pro blok zasílání zpráv.

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Items*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
Objekt, `ScheduleGroup` ve kterém je naplánováno `multitype_join` úlohy šíření pro blok zasílání zpráv. Použitý `Scheduler` objekt je implikován skupinou plánu.

### <a name="return-value"></a>Návratová hodnota

Blok `non_greedy multitype_join` zpráv se dvěma nebo více vstupními zdroji.

## <a name="make_task"></a><a name="make_task"></a>make_task

Metoda výroby pro `task_handle` vytvoření objektu.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán k provedení `task_handle` práce reprezentované objektem.

*_Func*<br/>
Funkce, která bude vyvolána k provedení `task_handle` práce reprezentované objektem. Může se jedná o lambda functor, ukazatel na funkci nebo jakýkoli objekt, který `void operator()()`podporuje verzi operátoru volání funkce s podpisem .

### <a name="return-value"></a>Návratová hodnota

Objekt. `task_handle`

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná, `task_handle` když potřebujete vytvořit objekt s výrazem lambda, protože umožňuje vytvořit objekt bez znalosti skutečného typu lambda functor.

## <a name="parallel_buffered_sort"></a><a name="parallel_buffered_sort"></a>parallel_buffered_sort

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle kritéria řazení určeného binárním predikátem paralelně. Tato funkce je sémanticky podobná `std::sort` v tom, že je na základě porovnání, `O(n)` nestabilní, na místě řazení s tím rozdílem, že potřebuje další místo a vyžaduje výchozí inicializaci pro prvky, které jsou seřazeny.

```cpp
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
Typ iterátoru vstupního rozsahu.

*_Allocator*<br/>
Typ alokátoru paměti kompatibilního se standardní knihovnou jazyka C++.

*_Function*<br/>
Typ binárního komparátoru.

*_Begin*<br/>
Random-access iterátor adresování pozici prvníprvek v oblasti, které mají být seřazeny.

*_End*<br/>
Random-access iterátor adresování pozice jeden kolem poslední prvek v rozsahu, který má být seřazen.

*_Alloc*<br/>
Instance alokátoru paměti kompatibilního se standardní knihovnou jazyka C++.

*_Func*<br/>
Uživatelem definovaný objekt predikátové funkce, který definuje kritérium porovnání, které mají být splněny po sobě jdoucími prvky v řazení. Binární predikát trvá dva argumenty a vrátí **true,** pokud je splněna a **false,** pokud není splněna. Tato funkce komparátoru musí uložit přísné slabé řazení na dvojice prvků z sekvence.

*_Chunk_size*<br/>
Velikost mimimum bloku, který bude rozdělen na dvě pro paralelní provádění.

### <a name="remarks"></a>Poznámky

Všechna přetížení `n * sizeof(T)` vyžadují další `n` místo, kde je počet prvků, `T` které mají být seřazeny a je typ prvku. Ve většině případů parallel_buffered_sort ukáže zlepšení výkonu oproti [parallel_sort](concurrency-namespace-functions.md)a měli byste jej použít v průběhu parallel_sort, pokud máte k dispozici paměť.

Pokud nezadáte binární komparátor `std::less` se používá jako výchozí, který vyžaduje typ `operator<()`prvku poskytnout operátor .

Pokud nezadáte typ alokátoru nebo instanci, alokátor paměti `std::allocator<T>` standardní knihovny jazyka C++ se používá k přidělení vyrovnávací paměti.

Algoritmus rozdělí vstupní rozsah na dva bloky a postupně rozdělí každý blok do dvou dílčích bloků pro paralelní spuštění. Volitelný argument `_Chunk_size` lze použít k označení algoritmu, který by měl `_Chunk_size` zpracovávat bloky velikosti < sériově.

## <a name="parallel_for"></a><a name="parallel_for"></a>parallel_for

`parallel_for`iterace přes rozsah indexů a provede uživatelem dodané funkce v každé iteraci, paralelně.

```cpp
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
Typ indexu, který se používá pro iteraci.

*_Function*<br/>
Typ funkce, která bude spuštěna při každé iteraci.

*_Partitioner*<br/>
Typ rozdělovače, který se používá k rozdělení dodané oblasti.

*První*<br/>
První index, který má být zahrnut do iterace.

*Poslední*<br/>
Index jeden za poslední index, který má být zahrnut do iterace.

*_Step*<br/>
Hodnota, kterou krok při iterace z `first` do `last`. Krok musí být pozitivní. [invalid_argument](../../../standard-library/invalid-argument-class.md) je vyvolána, pokud je krok menší než 1.

*_Func*<br/>
Funkce, která má být spuštěna při každé iteraci. Může se jedná o výraz lambda, ukazatel funkce nebo libovolný objekt, který `void operator()(_Index_type)`podporuje verzi operátoru volání funkce s podpisem .

*_Part*<br/>
Odkaz na objekt partitioner. Argument může být `const`jeden `const`z [auto_partitioner](auto-partitioner-class.md)`&`, [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` nebo [affinity_partitioner](affinity-partitioner-class.md) `&` Pokud je použit [affinity_partitioner](affinity-partitioner-class.md) objekt, odkaz musí být odkaz na hodnotu l, aby algoritmus mohl uložit stav pro budoucí smyčky k opětovnému použití.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a><a name="parallel_for_each"></a>parallel_for_each

`parallel_for_each`aplikuje zadanou funkci na každý prvek v rozsahu paralelně. Je sémanticky ekvivalentní `for_each` funkci `std` v oboru názvů, s tím rozdílem, že iterace přes prvky se provádí paralelně a pořadí iterace není určeno. Argument `_Func` musí podporovat operátor volání funkce `operator()(T)` formuláře, `T` kde je parametr typ položky kontejneru je iterated nad.

```cpp
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
Typ iterátoru se používá k iterazovat přes kontejner.

*_Function*<br/>
Typ funkce, která bude použita pro každý prvek v rozsahu.

*_Partitioner*<br/>
*První*<br/>
Iterátor adresování pozici první prvek, který mají být zahrnuty v paralelní iteraci.

*Poslední*<br/>
Iterátor adresování pozice jeden kolem poslední prvek, který má být zahrnut v paralelní iteraci.

*_Func*<br/>
Objekt funkce definované uživatelem, který je použit pro každý prvek v rozsahu.

*_Part*<br/>
Odkaz na objekt partitioner. Argument může být `const`jeden `const`z [auto_partitioner](auto-partitioner-class.md)`&`, [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` nebo [affinity_partitioner](affinity-partitioner-class.md) `&` Pokud je použit [affinity_partitioner](affinity-partitioner-class.md) objekt, odkaz musí být odkaz na hodnotu l, aby algoritmus mohl uložit stav pro budoucí smyčky k opětovnému použití.

### <a name="remarks"></a>Poznámky

[auto_partitioner](auto-partitioner-class.md) bude použit pro přetížení bez explicitní partitioner.

Pro iterátory, které nepodporují náhodný přístup, je podporovánpouze [auto_partitioner.](auto-partitioner-class.md)

Další informace naleznete [v tématu Paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a><a name="parallel_invoke"></a>parallel_invoke

Provede objekty funkce zadané jako parametry paralelně a blokuje, dokud nedokončí provádění. Každý objekt funkce může být lambda výraz, ukazatel funkce nebo jakýkoli objekt, `void operator()()`který podporuje operátor volání funkce s podpisem .

```cpp
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
Typ prvního objektu funkce, který má být proveden paralelně.

*_Function2*<br/>
Typ druhého objektu funkce, který má být proveden paralelně.

*_Function3*<br/>
Typ třetí objekt funkce, který má být proveden paralelně.

*_Function4*<br/>
Typ čtvrtého objektu funkce, který má být proveden paralelně.

*_Function5*<br/>
Typ pátého objektu funkce, který má být proveden paralelně.

*_Function6*<br/>
Typ šestého objektu funkce, který má být proveden paralelně.

*_Function7*<br/>
Typ sedmého objektu funkce, který má být proveden paralelně.

*_Function8*<br/>
Typ osmého objektu funkce, který má být proveden paralelně.

*_Function9*<br/>
Typ devátého objektu funkce, který má být proveden paralelně.

*_Function10*<br/>
Typ desátého objektu funkce, který má být proveden paralelně.

*_Func1*<br/>
První objekt funkce, který má být proveden paralelně.

*_Func2*<br/>
Druhý objekt funkce, který má být proveden paralelně.

*_Func3*<br/>
Třetí objekt funkce, který má být proveden paralelně.

*_Func4*<br/>
Čtvrtý objekt funkce, který má být proveden paralelně.

*_Func5*<br/>
Pátý objekt funkce, který má být proveden paralelně.

*_Func6*<br/>
Šestý objekt funkce, který má být proveden paralelně.

*_Func7*<br/>
Sedmý objekt funkce, který má být proveden paralelně.

*_Func8*<br/>
Osmý objekt funkce, který má být proveden paralelně.

*_Func9*<br/>
Devátý objekt funkce, který má být proveden paralelně.

*_Func10*<br/>
Desátý objekt funkce, který má být proveden paralelně.

### <a name="remarks"></a>Poznámky

Všimněte si, že jeden nebo více objektů funkce zadané jako parametry může spustit vložit na volající kontext.

Pokud jeden nebo více objektů funkce předaných jako parametry této funkce vyvolá výjimku, runtime vybere jednu takovou `parallel_invoke`výjimku podle svého výběru a rozšíří ji z volání .

Další informace naleznete [v tématu Paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a><a name="parallel_radixsort"></a>parallel_radixsort

Uspořádá prvky v zadaném rozsahu do nesestupového pořadí pomocí algoritmu řazení radix. Jedná se o stabilní funkci řazení, která vyžaduje funkci projekce, která může promítat prvky, které mají být seřazeny do nepodepsaných celočíselných klíčů. Pro seřazené prvky je vyžadována výchozí inicializace.

```cpp
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
Typ iterátoru vstupního rozsahu.

*_Allocator*<br/>
Typ alokátoru paměti kompatibilního se standardní knihovnou jazyka C++.

*_Function*<br/>
Typ funkce projekce.

*_Begin*<br/>
Random-access iterátor adresování pozici prvníprvek v oblasti, které mají být seřazeny.

*_End*<br/>
Random-access iterátor adresování pozice jeden kolem poslední prvek v rozsahu, který má být seřazen.

*_Alloc*<br/>
Instance alokátoru paměti kompatibilního se standardní knihovnou jazyka C++.

*_Proj_func*<br/>
Objekt funkce projekce definované uživatelem, který převádí prvek na integrální hodnotu.

*_Chunk_size*<br/>
Velikost mimimum bloku, který bude rozdělen na dvě pro paralelní provádění.

### <a name="remarks"></a>Poznámky

Všechna přetížení `n * sizeof(T)` vyžadují další `n` místo, kde je počet prvků, `T` které mají být seřazeny a je typ prvku. Unární projekce functor s `I _Proj_func(T)` podpisem je nutné vrátit klíč `T` při daný prvek, kde je typ prvku a `I` je nepodepsaný celočíselný typ.

Pokud nezadáte funkci projekce, výchozí funkce projekce, která jednoduše vrátí prvek, se používá pro integrální typy. Funkce se nezdaří zkompilovat, pokud prvek není integrální typ v nepřítomnosti funkce projekce.

Pokud nezadáte typ alokátoru nebo instanci, alokátor paměti `std::allocator<T>` standardní knihovny jazyka C++ se používá k přidělení vyrovnávací paměti.

Algoritmus rozdělí vstupní rozsah na dva bloky a postupně rozdělí každý blok do dvou dílčích bloků pro paralelní spuštění. Volitelný argument `_Chunk_size` lze použít k označení algoritmu, který by měl `_Chunk_size` zpracovávat bloky velikosti < sériově.

## <a name="parallel_reduce"></a><a name="parallel_reduce"></a>parallel_reduce

Vypočítá součet všech prvků v zadaném rozsahu výpočtem po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích dílčích výsledků podobně získaných z použití zadané binární operace jiné než součet paralelně. `parallel_reduce`je sémanticky `std::accumulate`podobný , s tím rozdílem, že vyžaduje, aby binární operace byla asociativní a vyžaduje hodnotu identity namísto počáteční hodnoty.

```cpp
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
Typ iterátoru vstupního rozsahu.

*_Sym_reduce_fun*<br/>
Typ funkce symetrické redukce. Musí se jednat o `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`typ funkce s podpisem , kde _Reduce_type je stejný jako typ identity a typ výsledku snížení. Pro třetí přetížení by to mělo být `_Range_reduce_fun`v souladu s výstupním typem .

*_Reduce_type*<br/>
Typ, který bude snížit na vstup, který se může lišit od typu vstupní prvek. Vrácená hodnota a hodnota identity bude mít tento typ.

*_Range_reduce_fun*<br/>
Typ funkce redukce rozsahu. Musí se jednat o `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`typ funkce s podpisem , _Reduce_type je stejný jako typ identity a typ výsledku redukce.

*_Begin*<br/>
Vstupní iterátor adresování první prvek v rozsahu, který má být snížena.

*_End*<br/>
Vstupní iterátor adresování prvek, který je jedna pozice za poslední prvek v rozsahu, který má být snížena.

*_Identity*<br/>
Hodnota `_Identity` identity je stejného typu jako výsledek typu snížení `value_type` a také iterátoru pro první a druhé přetížení. Pro třetí přetížení hodnota identity musí mít stejný typ jako výsledek typu snížení, `value_type` ale může se lišit od iterátoru. Musí mít odpovídající hodnotu tak, `_Range_fun`aby operátor snížení rozsahu , při `value_type` použití na rozsah jednoho prvku typu a hodnoty identity, se chová jako typ přetypované hodnoty z typu `value_type` na typ identity.

*_Sym_fun*<br/>
Symetrická funkce, která bude použita v druhém snížení. Další informace naleznete v poznámkách.

*_Range_fun*<br/>
Funkce, která bude použita v první fázi redukce. Další informace naleznete v poznámkách.

### <a name="return-value"></a>Návratová hodnota

Výsledek snížení.

### <a name="remarks"></a>Poznámky

Chcete-li provést paralelní redukci, funkce rozdělí rozsah na bloky na základě počtu pracovníků, které jsou k dispozici pro základní plánovač. Snížení probíhá ve dvou fázích, první fáze provádí snížení v rámci každého bloku a druhá fáze provádí snížení mezi částečné výsledky z každého bloku.

První přetížení `value_type`vyžaduje, aby iterátor `T`, být stejný jako typ hodnoty identity, jakož i typ výsledku snížení. Typ prvku T musí `T T::operator + (T)` poskytnout operátor snížit prvky v každém bloku. Stejný operátor se používá i ve druhé fázi.

Druhé přetížení také vyžaduje, aby iterátor je `value_type` být stejný jako typ hodnoty identity, jakož i typ výsledku snížení. Zadaný binární `_Sym_fun` operátor se používá v obou fázích redukce, přičemž hodnota identity je počáteční hodnotou pro první fázi.

Pro třetí přetížení typ hodnoty identity musí být stejný jako typ výsledku snížení, `value_type` ale iterátor se může lišit od obou. Funkce `_Range_fun` redukce rozsahu se používá v první fázi s hodnotou identity jako počáteční hodnotou a binární funkce `_Sym_reduce_fun` je použita pro dílčí výsledky ve druhé fázi.

## <a name="parallel_sort"></a><a name="parallel_sort"></a>parallel_sort

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle kritéria řazení určeného binárním predikátem paralelně. Tato funkce je sémanticky podobná `std::sort` v tom, že je na základě porovnání, nestabilní, na místě řazení.

```cpp
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
Typ iterátoru vstupního rozsahu.

*_Function*<br/>
Typ binární porovnání functor.

*_Begin*<br/>
Random-access iterátor adresování pozici prvníprvek v oblasti, které mají být seřazeny.

*_End*<br/>
Random-access iterátor adresování pozice jeden kolem poslední prvek v rozsahu, který má být seřazen.

*_Func*<br/>
Uživatelem definovaný objekt predikátové funkce, který definuje kritérium porovnání, které mají být splněny po sobě jdoucími prvky v řazení. Binární predikát trvá dva argumenty a vrátí **true,** pokud je splněna a **false,** pokud není splněna. Tato funkce komparátoru musí uložit přísné slabé řazení na dvojice prvků z sekvence.

*_Chunk_size*<br/>
Minimální velikost bloku, který bude rozdělen na dvě pro paralelní spuštění.

### <a name="remarks"></a>Poznámky

První přetížení používá binární komparátor `std::less`.

Druhý přetížený používá zadaný binární komparátor, `bool _Func(T, T)` `T` který by měl mít podpis, kde je typ prvků ve vstupní oblasti.

Algoritmus rozdělí vstupní rozsah na dva bloky a postupně rozdělí každý blok do dvou dílčích bloků pro paralelní spuštění. Volitelný argument `_Chunk_size` lze použít k označení algoritmu, který by měl `_Chunk_size` zpracovávat bloky velikosti < sériově.

## <a name="parallel_transform"></a><a name="parallel_transform"></a>parallel_transform

Aplikuje zadaný objekt funkce na každý prvek ve zdrojové oblasti nebo na dvojici prvků ze dvou zdrojových oblastí a zkopíruje vrácené hodnoty objektu funkce do cílové oblasti paralelně. Tento funkční je sémanticky ekvivalentní `std::transform`.

```cpp
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
Typ prvního nebo jediného vstupního iterátoru.

*_Output_iterator*<br/>
Typ výstupního iterátoru.

*_Unary_operator*<br/>
Typ unární functor, které mají být provedeny na každý prvek ve vstupní oblasti.

*_Input_iterator2*<br/>
Typ druhého vstupního iterátoru.

*_Binary_operator*<br/>
Typ binárního functoru proveden na prvky ze dvou zdrojových oblastí.

*_Partitioner*<br/>
*první1*<br/>
Vstupní iterátor adresující pozici prvního prvku v prvním nebo jediném zdrojovém rozsahu, na kterém má být provozován.

*last1*<br/>
Vstupní iterátor adresování pozice jeden kolem poslední prvek v první nebo jediný zdroj rozsah, který má být provozován.

*_Result*<br/>
Výstupní iterátor adresující pozici prvního prvku v cílovéoblasti.

*_Unary_op*<br/>
Uživatelem definovaný objekt unární funkce, který je použit pro každý prvek ve zdrojové oblasti.

*_Part*<br/>
Odkaz na objekt partitioner. Argument může být `const`jeden `const`z [auto_partitioner](auto-partitioner-class.md)`&`, [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_partitioner](simple-partitioner-class.md) `&` nebo [affinity_partitioner](affinity-partitioner-class.md) `&` Pokud je použit [affinity_partitioner](affinity-partitioner-class.md) objekt, odkaz musí být odkaz na hodnotu l, aby algoritmus mohl uložit stav pro budoucí smyčky k opětovnému použití.

*první2*<br/>
Vstupní iterátor adresující pozici prvního prvku v oblasti druhého zdroje, který má být provozován.

*_Binary_op*<br/>
Uživatelem definovaný binární objekt funkce, který je použit spárově, v pořadí dopředu, na dvě zdrojové oblasti.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresování pozice jeden kolem poslední prvek v cílové oblasti, která přijímá výstupní prvky transformované objektu funkce.

### <a name="remarks"></a>Poznámky

[auto_partitioner](auto-partitioner-class.md) budou použity pro přetížení bez explicitní partitioner argument.

Pro iterátory, které nepodporují náhodný přístup, je podporovánpouze [auto_partitioner.](auto-partitioner-class.md)

Přetížení, které přebírají `_Unary_op` argument, transformují vstupní rozsah do výstupního rozsahu použitím unárního functoru na každý prvek ve vstupním rozsahu. `_Unary_op`musí podporovat operátor volání `operator()(T)` funkce `T` s podpisem, kde je typ hodnoty rozsahu iterována nad.

Přetížení, které přebírají `_Binary_op` argument, transformují dva vstupní rozsahy do výstupního rozsahu použitím binárního functoru na jeden prvek z prvnívstupní oblasti a jeden prvek z druhého vstupního rozsahu. `_Binary_op`musí podporovat operátor volání `operator()(T, U)` funkce `T` `U` s podpisem, kde jsou typy hodnot dvou vstupních iterátorů.

Další informace naleznete [v tématu Paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a><a name="receive"></a>Přijímat

Obecné přijímat implementace, umožňující kontext čekat na data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijaty.

```cpp
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
Ukazatel nebo odkaz na zdroj, ze kterého se očekávají data.

*_Timeout*<br/>
Maximální doba, po kterou by měla metoda pro data v milisekundách.

*_Filter_proc*<br/>
Funkce filtru, která určuje, zda mají být zprávy přijímány.

### <a name="return-value"></a>Návratová hodnota

Hodnota ze zdroje typu datové části.

### <a name="remarks"></a>Poznámky

Pokud má `_Timeout` parametr jinou hodnotu než konstantu `COOPERATIVE_TIMEOUT_INFINITE`, je vyvolána výjimka [operation_timed_out,](operation-timed-out-class.md) pokud zadaný čas vyprší před přijetím zprávy. Pokud chcete časový rozsah nulové délky, měli byste použít [funkci try_receive,](concurrency-namespace-functions.md) na rozdíl od volání `receive` s časovým časem (nula), `0` protože je efektivnější a nevyvolá výjimky na časové opony.

Další informace naleznete v [tématu Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a><a name="run_with_cancellation_token"></a>run_with_cancellation_token

Spustí objekt funkce okamžitě a synchronně v kontextu daného tokenu zrušení.

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán.

*_Func*<br/>
Objekt funkce, který bude proveden. Tento objekt musí podporovat operátor volání funkce s podpisem void(void).

*_Ct*<br/>
Token zrušení, který bude řídit implicitní zrušení objektu funkce. Použijte, `cancellation_token::none()` pokud chcete, aby funkce byla spuštěna bez možnosti zrušení implicitního zrušení z nadřazené skupiny úkolů.

### <a name="remarks"></a>Poznámky

Všechny body přerušení v objektu funkce `cancellation_token` budou spuštěny při zrušení. Explicitní token `_Ct` bude izolovat `_Func` od nadřazené zrušení, pokud nadřazený má jiný token nebo žádný token.

## <a name="send"></a><a name="send"></a>Odeslat

Synchronní operace odeslání, která čeká, dokud cíl nepřijme nebo odmítne zprávu.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ datové části.

*_Trg*<br/>
Ukazatel nebo odkaz na cíl, ke kterému jsou data odesílána.

*_Data*<br/>
Odkaz na data, která mají být odeslána.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud byla zpráva přijata, **false** jinak.

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a><a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parametry

*_Scheduler*<br/>
Okolní plánovač nastavit.

## <a name="set_task_execution_resources"></a><a name="set_task_execution_resources"></a>set_task_execution_resources

Omezuje prostředky spuštění používané vnitřnípracovní vlákna souběžnosti runtime na zadanou sadu spřažení.

Je platné volat tuto metodu pouze před správce prostředků byl vytvořen, nebo mezi dvěma životnostmi Správce prostředků. Může být vyvolána vícekrát, pokud Správce prostředků neexistuje v době vyvolání. Po nastavení limitu spřažení zůstane v platnosti až do `set_task_execution_resources` dalšího platného volání metody.

Zapředpokladu maska spřažení nemusí být podmnožinou masky spřažení procesů. Spřažení procesů bude v případě potřeby aktualizováno.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parametry

*_ProcessAffinityMask*<br/>
Maska spřažení, na kterou mají být omezena pracovní vlákna souběžnosti runtime. Tuto metodu použijte v systému s více než 64 hardwarových vláken pouze v případě, že chcete omezit modul Runtime souběžnosti na podmnožinu aktuální skupiny procesorů. Obecně byste měli použít verzi metody, která přijímá pole spřažení skupin jako parametr, chcete-li omezit spřažení na počítačích s více než 64 hardwarových podprocesů.

*Počet*<br/>
Počet `GROUP_AFFINITY` položek v poli určeném `_PGroupAffinity`parametrem .

*_PGroupAffinity*<br/>
Pole `GROUP_AFFINITY` položek.

### <a name="remarks"></a>Poznámky

Metoda vyvolá [výjimku invalid_operation,](invalid-operation-class.md) pokud správce prostředků je k dispozici v době, kdy je vyvolána, a [výjimku invalid_argument,](../../../standard-library/invalid-argument-class.md) pokud zadaný spřažení má za následek prázdnou sadu prostředků.

Verze metody, která přebírá pole spřažení skupin jako parametr by měl být používán pouze v operačních systémech s verzí Windows 7 nebo vyšší. V opačném případě je vyvolána [výjimka invalid_operation.](invalid-operation-class.md)

Programově úprava spřažení procesů po vyvolání této metody nezpůsobí, že Správce prostředků znovu vyhodnotí spřažení, na kterou je omezen. Proto všechny změny spřažení procesů by měly být provedeny před voláním této metody.

## <a name="swap"></a><a name="swap"></a>Swap

Vyměňuje prvky `concurrent_vector` dvou objektů.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ prvků uložených v souběžných vektorech.

*_Ax*<br/>
Typ alokátoru souběžných vektorů.

*_A*<br/>
Souběžný vektor, jehož prvky mají být vyměněny `_B`s prvky souběžného vektoru .

*_B*<br/>
Souběžný vektor poskytující prvky, které mají být zaměněny, nebo vektor, jehož `_A`prvky mají být vyměněny s prvky souběžného vektoru .

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na `concurrent_vector` třídu kontejneru pro spuštění členské funkce `_A`. [concurrent_vector::swap](concurrent-vector-class.md#swap) `_B`( ). Jedná se o instance částečnéřazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejspecializovanější verzi funkce šablony. Obecná verze funkce šablony `template <class T> void swap(T&, T&)`, ve třídě algoritmu funguje podle přiřazení a je pomalá operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s vnitřní reprezentací třídy kontejneru.

Tato metoda není bezpečné souběžnosti. Při volání této metody je nutné zajistit, aby žádná jiná vlákna neprováděla operace s žádným ze souběžných vektorů.

## <a name="task_from_exception"></a><a name="task_from_exception"></a>task_from_exception

```cpp
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

## <a name="task_from_result"></a><a name="task_from_result"></a>task_from_result

```cpp
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

## <a name="trace_agents_register_name"></a><a name="trace_agents_register_name"></a>Trace_agents_register_name

Přidružené křestní jméno bloku zprávy nebo agent a agent v trasování ETW.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ objektu. Obvykle se jedná o blok zpráv nebo agenta.

*_PObject*<br/>
Ukazatel na blok zprávy nebo agenta, který je pojmenován v trasování.

*_Name*<br/>
Název pro daný objekt.

## <a name="try_receive"></a><a name="try_receive"></a>try_receive

Obecné try-receive implementace, povolení kontextu hledat data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijímány. Pokud data nejsou připravena, metoda vrátí **false**.

```cpp
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
Ukazatel nebo odkaz na zdroj, ze kterého se očekávají data.

*_value*<br/>
Odkaz na umístění, kam bude umístěn výsledek.

*_Filter_proc*<br/>
Funkce filtru, která určuje, zda mají být zprávy přijímány.

### <a name="return-value"></a>Návratová hodnota

Hodnota `bool` označující, zda byla datová `_value`část umístěna do .

### <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu Message Passing Functions](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a><a name="wait"></a>Počkej

Pozastaví aktuální kontext po určitou dobu.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parametry

*_Milliseconds*<br/>
Počet milisekund, pro které by měl být aktuální kontext pozastaven. Pokud `_Milliseconds` je parametr nastaven `0`na hodnotu , aktuální kontext by měl před pokračováním přinést spuštění jiným spustitelným kontextům.

### <a name="remarks"></a>Poznámky

Pokud je tato metoda volána v kontextu plánovače souběžnosti runtime, plánovač najde jiný kontext, který se má spustit na podkladovém prostředku. Vzhledem k tomu, že plánovač je kooperativní povahy, tento kontext nelze pokračovat přesně po zadaný počet milisekund. Pokud plánovač je zaneprázdněn provádění jiných úloh, které nejsou kooperativně výnos plánovače, čekací doba může být neomezená.

## <a name="when_all"></a><a name="when_all"></a>when_all

Vytvoří úkol, který bude úspěšně dokončen po úspěšném dokončení všech úkolů zadaných jako argumenty.

```cpp
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

*_Begin*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být sloučeny do výsledného úkolu.

*_End*<br/>
Pozice prvníprvek mimo rozsah prvků, které mají být sloučeny do výsledného úkolu.

*_TaskOptions*<br/>
Objekt `task_options`

### <a name="return-value"></a>Návratová hodnota

Úkol, který je úspěšně dokončen po úspěšném dokončení všech vstupních úkolů. Pokud jsou vstupní úkoly typu `T`, výstup em `task<std::vector<T>>`této funkce bude . Pokud jsou vstupní úkoly typu, `void` výstupní `task<void>`úloha bude také .

### <a name="remarks"></a>Poznámky

`when_all`je neblokující funkce, která `task` vytváří jako jeho výsledek. Na rozdíl od [task::wait](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UPW ve vlákně ASTA (Application STA).

Pokud je jeden z úkolů zrušen nebo vyvolá výjimku, vrácená úloha bude dokončena dříve, v zrušeném stavu a výjimka, `task::wait` pokud k ní dojde, bude vyvolána, pokud zavoláte [task::get](task-class.md#get) nebo na tento úkol.

Další informace naleznete v [tématu Paralelismus úlohy](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a><a name="when_any"></a>when_any

Vytvoří úkol, který bude úspěšně dokončen po úspěšném dokončení některého z úkolů zadaných jako argumenty.

```cpp
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

*_Begin*<br/>
Pozice prvního prvku v rozsahu prvků, které mají být sloučeny do výsledného úkolu.

*_End*<br/>
Pozice prvníprvek mimo rozsah prvků, které mají být sloučeny do výsledného úkolu.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token zrušení, který řídí zrušení vrácené úlohy. Pokud nezadáte token zrušení, výsledná úloha obdrží token zrušení úlohy, která způsobí jeho dokončení.

### <a name="return-value"></a>Návratová hodnota

Úkol, který se úspěšně dokončí po úspěšném dokončení některého ze vstupních úkolů. Pokud vstupní úkoly `T`jsou typu , výstup této `task<std::pair<T, size_t>>>`funkce bude , kde první prvek dvojice je výsledkem dokončení úkolu a druhý prvek je index úkolu, který byl dokončen. Pokud vstupní úkoly `void` jsou typu `task<size_t>`výstup je , kde výsledkem je index dokončení úkolu.

### <a name="remarks"></a>Poznámky

`when_any`je neblokující funkce, která `task` vytváří jako jeho výsledek. Na rozdíl od [task::wait](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UPW ve vlákně ASTA (Application STA).

Další informace naleznete v [tématu Paralelismus úlohy](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
