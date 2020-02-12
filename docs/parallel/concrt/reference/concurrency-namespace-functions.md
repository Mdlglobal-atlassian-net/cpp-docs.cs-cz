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
ms.openlocfilehash: 4005ae888511ec987fe83ab3d616aa0fc3675a22
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143260"
---
# <a name="concurrency-namespace-functions"></a>concurrency – funkce oboru názvů

||||
|-|-|-|
|[Vyhrazen](#alloc)|[CreateResourceManager –](#createresourcemanager)|[DisableTracing –](#disabletracing)|
|[EnableTracing –](#enabletracing)|[Free](#free)|[GetExecutionContextId –](#getexecutioncontextid)|
|[GetOSVersion –](#getosversion)|[GetProcessorCount –](#getprocessorcount)|[GetProcessorNodeCount –](#getprocessornodecount)|
|[GetSchedulerId –](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[jejich](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[získávají](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[posílají](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[adresu](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Počkej](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a>Vyhrazen

Přidělí blok paměti, která je určená od Concurrency Runtimeho subalokátoru pro ukládání do mezipaměti.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parametry

*_NumBytes*<br/>
Počet bajtů paměti, které mají být přiděleny.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nově přidělenou paměť.

### <a name="remarks"></a>Poznámky

Další informace o tom, které scénáře ve vaší aplikaci můžou využít k používání subalokátoru ukládání do mezipaměti, najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a>asend

Operace asynchronního odeslání, která Naplánuje úkol, aby rozšířil data do cílového bloku.

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

*Š*<br/>
Typ dat, která se mají odeslat

*_Trg*<br/>
Ukazatel nebo odkaz na cíl, na který se odesílají data.

*_Data*<br/>
Odkaz na data, která mají být odeslána.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva přijata před vrácenou metodou, jinak **false** .

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a>cancel_current_task

Zruší právě prováděnou úlohu. Tato funkce může být volána z těla úkolu, aby přerušila provádění úlohy a způsobila, že vstoupí do stavu `canceled`.

Nejedná se o podporovaný scénář pro volání této funkce, pokud nejste v těle `task`. V důsledku toho dojde k nedefinovanému chování, jako je například selhání nebo zablokování aplikace.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a>jejich

Vymaže souběžnou frontu a zničí všechny aktuálně zařazené prvky do fronty. Tato metoda není bezpečná pro souběžnost.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parametry

*Š*<br/>

*_Ax*<br/>

## <a name="create_async"></a>create_async

Vytvoří asynchronní konstrukci prostředí Windows Runtime na základě uživatelem zadaného výrazu lambda nebo objektu funkce. Návratový typ `create_async` je jedna z `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`nebo `IAsyncOperationWithProgress<TResult, TProgress>^` na základě signatury lambda předané metodě.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ:

*_Func*<br/>
Výraz lambda nebo objekt funkce, ze kterého má být vytvořena prostředí Windows Runtime asynchronní konstrukce.

### <a name="return-value"></a>Návratová hodnota

Asynchronní konstrukce reprezentované IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^ nebo IAsyncOperationWithProgress\<TResult, TProgress > ^. Vrácené rozhraní závisí na podpisu výrazu lambda předaného do funkce.

### <a name="remarks"></a>Poznámky

Návratový typ lambda určuje, zda je konstrukce akce nebo operace.

Výrazy lambda, které vracejí anulování, způsobují vytváření akcí. Výrazy lambda, které vracejí výsledek typu `TResult` způsobují vytvoření operací TResult.

Lambda může také vracet `task<TResult>`, který zapouzdřuje asynchronní práci v rámci sebe nebo je pokračováním řetězce úloh reprezentujících asynchronní práci. V tomto případě je lambda sám spuštěno jako inline, protože úkoly jsou ty, které se spouštějí asynchronně, a návratový typ lambda je nezabalený, aby vytvořil asynchronní konstruktor vrácený `create_async`. To znamená, že výraz lambda, který vrací úlohu\<void > způsobí vytvoření akcí a lambda, která vrátí úlohu\<TResult > způsobí vytvoření operací TResult.

Lambda může mít buď nula, jeden nebo dva argumenty. Platné argumenty jsou `progress_reporter<TProgress>` a `cancellation_token`, v takovém pořadí, pokud jsou oba použity. Lambda bez argumentů způsobí vytvoření asynchronní konstrukce bez možnosti vytváření sestav průběhu. Výraz lambda, který přebírá progress_reporter\<TProgress > způsobí, že `create_async` vrátí asynchronní konstruktor, který hlásí průběh typu TProgress pokaždé, když je volána metoda `report` objektu progress_reporter. Výraz lambda, který přebírá cancellation_token může použít tento token pro kontrolu zrušení nebo ho předat úlohám, které vytvoří, aby zrušení asynchronního konstruktoru způsobilo zrušení těchto úloh.

Pokud tělo výrazu lambda nebo objektu funkce vrátí výsledek (a ne úlohu\<TResult >), Lamdba se spustí asynchronně v rámci procesu MTA v kontextu úlohy, kterou pro ni modul runtime implicitně vytvoří. Metoda `IAsyncInfo::Cancel` způsobí zrušení implicitního úkolu.

Pokud tělo lambda vrátí úlohu, provede se vložením na řádku a deklarováním výrazu lambda pro přijetí argumentu typu `cancellation_token` můžete aktivovat zrušení všech úloh, které vytvoříte v rámci výrazu lambda, předáním tohoto tokenu v okamžiku, kdy je vytvoříte. Můžete také použít metodu `register_callback` na tokenu, aby modul runtime vyvolal zpětné volání při volání `IAsyncInfo::Cancel` na asynchronní operaci nebo vytvořenou akci..

Tato funkce je k dispozici pouze pro aplikace prostředí Windows Runtime.

## <a name="createresourcemanager"></a>CreateResourceManager –

Vrátí rozhraní, které představuje instanci typu Singleton Správce prostředků Concurrency Runtime. Správce prostředků zodpovídá za přiřazení prostředků plánovačům, které chtějí vzájemně spolupracovat.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Návratová hodnota

Rozhraní `IResourceManager`.

### <a name="remarks"></a>Poznámky

Několik následných volání této metody vrátí stejnou instanci Správce prostředků. Každé volání metody zvýší počet odkazů na Správce prostředků a musí se shodovat s voláním metody [IResourceManager:: Release](iresourcemanager-structure.md) , když váš Plánovač dokončí komunikaci s správce prostředků.

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud Concurrency Runtime operační systém není podporován.

## <a name="create_task"></a>create_task

Vytvoří objekt [úlohy](task-class.md) PPL. `create_task` lze použít všude, kde byste použili konstruktor úlohy. Je poskytován hlavně pro pohodlí, protože umožňuje použití klíčového slova `auto` při vytváření úloh.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ parametru, ze kterého má být vytvořen úkol

*_ReturnType*<br/>
Typ:

*_Param*<br/>
Parametr, ze kterého má být vytvořen úkol Může to být lambda nebo objekt funkce, objekt `task_completion_event`, jiný objekt `task` nebo rozhraní Windows:: Foundation:: IAsyncInfo, pokud používáte úkoly v aplikaci UWP.

*_TaskOptions*<br/>
Možnosti úlohy.

*_Task*<br/>
Úkol, který se má vytvořit

### <a name="return-value"></a>Návratová hodnota

Nový úkol typu `T`, který je odvozený z `_Param`.

### <a name="remarks"></a>Poznámky

První přetížení se chová jako konstruktor úlohy, který přijímá jeden parametr.

Druhé Přetížení přidruží token zrušení, který je součástí nově vytvořeného úkolu. Použijete-li toto přetížení, nebudete moci předat jiný objekt `task` jako první parametr.

Typ vrácené úlohy je odvozen z prvního parametru funkce. Pokud je `_Param` `task_completion_event<T>`, `task<T>`nebo funktor, které vrátí buď typ `T` nebo `task<T>`, je typ vytvořeného úkolu `task<T>`.

Pokud je v aplikaci UWP `_Param` typu Windows:: Foundation:: IAsyncOperation\<T > ^ nebo Windows:: Foundation:: IAsyncOperationWithProgress\<T, P > ^ nebo funktor, který vrací jeden z těchto typů, bude vytvořený úkol typu `task<T>`. Pokud je `_Param` typu Windows:: Foundation:: IAsyncAction ^ nebo Windows:: Foundation:: IAsyncActionWithProgress\<P > ^ nebo funktor, který vrací jeden z těchto typů, bude vytvořený úkol typu `task<void>`.

## <a name="disabletracing"></a>DisableTracing –

Zakáže trasování v Concurrency Runtime. Tato funkce je zastaralá, protože trasování ETW je ve výchozím nastavení neregistrované.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Návratová hodnota

Pokud bylo trasování správně zakázané, `S_OK` se vrátí. Pokud trasování nebylo zahájeno dříve, `E_NOT_STARTED` je vráceno.

## <a name="enabletracing"></a>EnableTracing –

Povolí trasování v Concurrency Runtime. Tato funkce je zastaralá, protože trasování ETW je teď ve výchozím nastavení zapnuté.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Návratová hodnota

Pokud bylo trasování správně iniciované, `S_OK` se vrátí. v opačném případě se `E_NOT_STARTED` vrátí.

## <a name="free"></a>Dost

Uvolní blok paměti dříve přidělený `Alloc` metodou do meziConcurrency Runtime ukládání do mezipaměti.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parametry

*_PAllocation*<br/>
Ukazatel na paměť, která byla dříve přidělena metodou `Alloc`, která má být uvolněna. Pokud je parametr `_PAllocation` nastaven na hodnotu `NULL`, tato metoda ho ignoruje a okamžitě se vrátí.

### <a name="remarks"></a>Poznámky

Další informace o tom, které scénáře ve vaší aplikaci můžou využít k používání subalokátoru ukládání do mezipaměti, najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Návratová hodnota

## <a name="getexecutioncontextid"></a>GetExecutionContextId –

Vrací jedinečný identifikátor, který lze přiřadit kontextu spuštění, který implementuje rozhraní `IExecutionContext`.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro kontext spuštění.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li získat identifikátor pro svůj kontext spuštění před předáním `IExecutionContext` rozhraní jako parametru kterékoli z metod, které nabízí Správce prostředků.

## <a name="getosversion"></a>GetOSVersion –

Vrátí verzi operačního systému.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Návratová hodnota

Výčtová hodnota představující operační systém.

### <a name="remarks"></a>Poznámky

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud Concurrency Runtime operační systém není podporován.

## <a name="getprocessorcount"></a>GetProcessorCount –

Vrátí počet hardwarových vláken v podkladovém systému.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet hardwarových vláken.

### <a name="remarks"></a>Poznámky

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud Concurrency Runtime operační systém není podporován.

## <a name="getprocessornodecount"></a>GetProcessorNodeCount –

Vrátí počet uzlů NUMA nebo balíčků procesorů v podkladovém systému.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Návratová hodnota

Počet uzlů NUMA nebo balíčků procesorů.

### <a name="remarks"></a>Poznámky

Pokud systém obsahuje víc uzlů NUMA než balíčky procesorů, vrátí se počet uzlů NUMA, jinak se vrátí počet balíčků procesoru.

[unsupported_os](unsupported-os-class.md) je vyvolána, pokud Concurrency Runtime operační systém není podporován.

## <a name="getschedulerid"></a>GetSchedulerId –

Vrátí jedinečný identifikátor, který lze přiřadit k plánovači, který implementuje rozhraní `IScheduler`.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Návratová hodnota

Jedinečný identifikátor pro Scheduler.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li získat identifikátor pro Plánovač před předáním `IScheduler` rozhraní jako parametru libovolné metody nabízené Správce prostředků.

## <a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Parametry

*Š*<br/>

*_Ax*<br/>

*_I*<br/>

*první*<br/>

*posledního*<br/>

## <a name="interruption_point"></a>interruption_point

Vytvoří bod přerušení pro zrušení. Pokud probíhá zrušení v kontextu, ve kterém je tato funkce volána, vyvolá se vnitřní výjimka, která přeruší provádění aktuálně prováděné paralelní práce. Pokud zrušení neprobíhá, funkce neprovede žádnou akci.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Poznámky

Neměli byste zachytit vnitřní výjimku zrušení vyvolanou funkcí `interruption_point()`. Výjimka bude zachycena a zpracována modulem runtime a její zachycení může způsobit neobvyklou funkčnost programu.

## <a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Vrací údaj o tom, zda je skupina úloh, která aktuálně provádí inlineing v aktuálním kontextu, v průběhu aktivního zrušení (nebo bude brzy). Všimněte si, že pokud v aktuálním kontextu není žádná skupina úloh aktuálně prováděna s vloženým kontextem, bude vrácena `false`.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se aktuálně prováděná skupina úloh zruší, jinak **false** .

### <a name="remarks"></a>Poznámky

Další informace naleznete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a>make_choice

Vytvoří `choice` blok pro zasílání zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dvou nebo více vstupních zdrojů.

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

*Lince*<br/>
Typ bloku zprávy prvního zdroje

*T2*<br/>
Typ bloku zprávy druhého zdroje.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `choice`

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Items*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `choice` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="return-value"></a>Návratová hodnota

`choice` blok zpráv se dvěma nebo více vstupními zdroji.

## <a name="make_greedy_join"></a>make_greedy_join

Vytvoří `greedy multitype_join` blok pro zasílání zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dvou nebo více vstupních zdrojů.

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

*Lince*<br/>
Typ bloku zprávy prvního zdroje

*T2*<br/>
Typ bloku zprávy druhého zdroje.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `multitype_join`

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Items*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `multitype_join` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="return-value"></a>Návratová hodnota

`greedy multitype_join` blok zpráv se dvěma nebo více vstupními zdroji.

## <a name="make_join"></a>make_join

Vytvoří `non_greedy multitype_join` blok pro zasílání zpráv z volitelného `Scheduler` nebo `ScheduleGroup` a dvou nebo více vstupních zdrojů.

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

*Lince*<br/>
Typ bloku zprávy prvního zdroje

*T2*<br/>
Typ bloku zprávy druhého zdroje.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `multitype_join`

*_Item1*<br/>
První zdroj.

*_Item2*<br/>
Druhý zdroj.

*_Items*<br/>
Další zdroje.

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `multitype_join` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="return-value"></a>Návratová hodnota

`non_greedy multitype_join` blok zpráv se dvěma nebo více vstupními zdroji.

## <a name="make_task"></a>make_task

Výrobní metoda pro vytvoření objektu `task_handle`.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude vyvolán pro provedení práce reprezentované objektem `task_handle`.

*_Func*<br/>
Funkce, která bude vyvolána pro provedení práce reprezentované objektem `task_handle`. Může to být lambda funktor, ukazatel na funkci nebo libovolný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()()`.

### <a name="return-value"></a>Návratová hodnota

Objekt `task_handle`.

### <a name="remarks"></a>Poznámky

Tato funkce je užitečná v případě, že potřebujete vytvořit objekt `task_handle` s výrazem lambda, protože umožňuje vytvořit objekt bez znalosti skutečného typu funktor lambda.

## <a name="parallel_buffered_sort"></a>parallel_buffered_sort

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle kritéria řazení určeného binárním predikátem paralelně. Tato funkce je sémanticky podobná `std::sort` v tom, že se jedná o porovnání, nestabilní, místní řazení s výjimkou toho, že potřebuje `O(n)` dodatečné místo a vyžaduje výchozí inicializaci pro prvky, které jsou setříděny.

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
Typ C++ standardního přidělování paměti kompatibilní knihovny.

*_Function*<br/>
Typ binárního komparátoru.

*_Begin*<br/>
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který má být seřazen.

*_End*<br/>
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v rozsahu, který má být seřazen.

*_Alloc*<br/>
Instance C++ standardního přidělování paměti kompatibilní knihovny.

*_Func*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna. Tato funkce komparátor musí pro páry prvků z sekvence vytvořit přísné slabé řazení.

*_Chunk_size*<br/>
Velikost minimální bloku, který bude rozdělen do dvou pro paralelní spuštění.

### <a name="remarks"></a>Poznámky

Všechna přetížení vyžadují `n * sizeof(T)` další místo, kde `n` je počet prvků, které mají být seřazeny, a `T` je typ prvku. Ve většině případů parallel_buffered_sort zobrazuje zlepšení výkonu při [parallel_sort](concurrency-namespace-functions.md)a je vhodné ho použít přes parallel_sort, pokud máte k dispozici dostatek paměti.

Pokud nezadáte binární komparátor `std::less` slouží jako výchozí, což vyžaduje, aby typ prvku poskytoval operátor `operator<()`.

Pokud nezadáte typ nebo instanci přidělování, k přidělení vyrovnávací paměti C++ slouží standardní `std::allocator<T>` přidělování paměti knihovny.

Algoritmus rozdělí vstupní rozsah do dvou bloků dat a postupně rozděluje každý blok na dvě dílčí bloky pro spuštění paralelně. Nepovinný argument `_Chunk_size` lze použít k označení algoritmu, který by měl zpracovávat bloky velikosti < `_Chunk_size` sériové.

## <a name="parallel_for"></a>parallel_for

`parallel_for` iterovat na určitou škálu indexů a v každé iteraci spustí uživatelsky zadanou funkci, paralelně.

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
Typ funkce, která bude provedena při každé iteraci.

*_Partitioner*<br/>
Typ rozdělovače, který se používá k rozdělení zadaného rozsahu.

*první*<br/>
První index, který má být zahrnut do iterace.

*posledního*<br/>
Index, který bude přidán do iterace za poslední index.

*_Step*<br/>
Hodnota, kterou se má při iteraci z `first` na `last`krokovat. Krok musí být kladný. [invalid_argument](../../../standard-library/invalid-argument-class.md) je vyvolána, pokud je krok menší než 1.

*_Func*<br/>
Funkce, která má být vykonána při každé iteraci. Může to být výraz lambda, ukazatel na funkci nebo libovolný objekt, který podporuje verzi operátoru volání funkce s podpisem `void operator()(_Index_type)`.

*_Part*<br/>
Odkaz na objekt rozdělovače. Argument může být jeden z `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`, `const`[simple_partitioner](simple-partitioner-class.md)`&` nebo [affinity_partitioner](affinity-partitioner-class.md)`&`, pokud se používá objekt [affinity_partitioner](affinity-partitioner-class.md) , odkaz musí být nekonstantní odkaz l-hodnoty, aby algoritmus mohl uložit stav pro budoucí smyčky pro opakované použití.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a>parallel_for_each

`parallel_for_each` aplikuje zadanou funkci na každý prvek v rozsahu paralelně. Je sémanticky ekvivalentní funkci `for_each` v oboru názvů `std`, s tím rozdílem, že iterace nad prvky je prováděna paralelně a pořadí iterace není specifikováno. Argument `_Func` musí podporovat operátor volání funkce ve formě `operator()(T)` kde parametr `T` je typ položky kontejneru, na který se provádí iterace.

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
Typ iterátoru, který se používá k iterování na kontejneru.

*_Function*<br/>
Typ funkce, která bude použita na každý prvek v rozsahu.

*_Partitioner*<br/>
*první*<br/>
Iterátor adresující pozici prvního prvku, který má být zahrnut do paralelní iterace.

*posledního*<br/>
Iterátor adresující pozici jednu za poslední prvek, který se má zahrnout do paralelní iterace.

*_Func*<br/>
Uživatelem definovaný objekt funkce, který je použit pro každý prvek v rozsahu.

*_Part*<br/>
Odkaz na objekt rozdělovače. Argument může být jeden z `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`, `const`[simple_partitioner](simple-partitioner-class.md)`&` nebo [affinity_partitioner](affinity-partitioner-class.md)`&`, pokud se používá objekt [affinity_partitioner](affinity-partitioner-class.md) , odkaz musí být nekonstantní odkaz l-hodnoty, aby algoritmus mohl uložit stav pro budoucí smyčky pro opakované použití.

### <a name="remarks"></a>Poznámky

[auto_partitioner](auto-partitioner-class.md) se použije pro přetížení bez explicitního dělení.

Pro iterátory, které nepodporují náhodný přístup, je podporována pouze [auto_partitioner](auto-partitioner-class.md) .

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a>parallel_invoke

Spustí objekty funkce, které jsou zadány jako parametry paralelně, a zablokuje, dokud se nedokončí jejich spuštění. Každý objekt funkce může být výraz lambda, ukazatel na funkci nebo libovolný objekt, který podporuje operátor volání funkce s podpisem `void operator()()`.

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
Typ prvního objektu funkce, který má být spuštěn paralelně.

*_Function2*<br/>
Typ druhého objektu funkce, který má být spuštěn paralelně.

*_Function3*<br/>
Typ třetího objektu funkce, který má být spuštěn paralelně.

*_Function4*<br/>
Typ čtvrtého objektu funkce, který má být spuštěn paralelně.

*_Function5*<br/>
Typ pátého objektu funkce, který má být spuštěn paralelně.

*_Function6*<br/>
Typ šestého objektu funkce, který má být spuštěn paralelně.

*_Function7*<br/>
Typ sedmého objektu funkce, který má být spuštěn paralelně.

*_Function8*<br/>
Typ osmého objektu funkce, který má být spuštěn paralelně.

*_Function9*<br/>
Typ devátého objektu funkce, který má být spuštěn paralelně.

*_Function10*<br/>
Typ desátého objektu funkce, který má být spuštěn paralelně.

*_Func1*<br/>
První objekt funkce, který má být spuštěn paralelně.

*_Func2*<br/>
Druhý objekt funkce, který má být spuštěn paralelně.

*_Func3*<br/>
Třetí objekt funkce, který má být spuštěn paralelně.

*_Func4*<br/>
Čtvrtý objekt funkce, který má být spuštěn paralelně.

*_Func5*<br/>
Pátý objekt funkce, který má být spuštěn paralelně.

*_Func6*<br/>
Šestý objekt funkce, který má být spuštěn paralelně.

*_Func7*<br/>
Sedmý objekt funkce, který má být spuštěn paralelně.

*_Func8*<br/>
Osmý objekt funkce, který má být spuštěn paralelně.

*_Func9*<br/>
Devátý objekt funkce, který má být spuštěn paralelně.

*_Func10*<br/>
Desátý objekt funkce, který má být spuštěn paralelně.

### <a name="remarks"></a>Poznámky

Všimněte si, že jeden nebo více objektů funkcí dodaných jako parametry může být spuštěno v kontextu volání.

Pokud jeden nebo více objektů funkcí předaných jako parametry této funkci vyvolá výjimku, modul runtime vybere jednu výjimku, kterou si zvolíte, a rozšíří ji mimo volání `parallel_invoke`.

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a>parallel_radixsort

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí pomocí algoritmu řazení číselné řady. Toto je stabilní funkce řazení, která vyžaduje funkci projekce, která může prvky projektu seřadit do unsigned integer klíčů jako. Pro prvky, které jsou řazeny, je vyžadována výchozí inicializace.

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
Typ C++ standardního přidělování paměti kompatibilní knihovny.

*_Function*<br/>
Typ funkce projekce

*_Begin*<br/>
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který má být seřazen.

*_End*<br/>
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v rozsahu, který má být seřazen.

*_Alloc*<br/>
Instance C++ standardního přidělování paměti kompatibilní knihovny.

*_Proj_func*<br/>
Objekt funkce projekce definovaný uživatelem, který převede element na celočíselnou hodnotu.

*_Chunk_size*<br/>
Velikost minimální bloku, který bude rozdělen do dvou pro paralelní spuštění.

### <a name="remarks"></a>Poznámky

Všechna přetížení vyžadují `n * sizeof(T)` další místo, kde `n` je počet prvků, které mají být seřazeny, a `T` je typ prvku. Unární projekce funktor s podpisem `I _Proj_func(T)` je vyžadována pro vrácení klíče, je-li zadán element, kde `T` je typ prvku a `I` je typ unsigned integer.

Pokud nezadáte funkci projekce, výchozí funkce projekce, která jednoduše vrátí prvek, se používá pro celočíselné typy. Funkce nebude zkompilována, pokud prvek není integrálního typu při absenci funkce projekce.

Pokud nezadáte typ nebo instanci přidělování, k přidělení vyrovnávací paměti C++ slouží standardní `std::allocator<T>` přidělování paměti knihovny.

Algoritmus rozdělí vstupní rozsah do dvou bloků dat a postupně rozděluje každý blok na dvě dílčí bloky pro spuštění paralelně. Nepovinný argument `_Chunk_size` lze použít k označení algoritmu, který by měl zpracovávat bloky velikosti < `_Chunk_size` sériové.

## <a name="parallel_reduce"></a>parallel_reduce

Vypočítá součet všech prvků v zadaném rozsahu tím, že provede výpočet po sobě jdoucích částečných součtů, nebo vypočítá výsledek po sobě jdoucích částečných výsledků podobně jako u paralelního použití zadané binární operace, která je jiná než součet. `parallel_reduce` je sémanticky podobná `std::accumulate`, s tím rozdílem, že vyžaduje asociativní binární operaci a vyžaduje hodnotu identity namísto počáteční hodnoty.

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
Typ funkce symetrického snižování. Musí se jednat o typ funkce s podpisem `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, kde _Reduce_type je stejná jako typ identity a výsledný typ omezení. Pro třetí přetížení by měl být konzistentní s typem výstupu `_Range_reduce_fun`.

*_Reduce_type*<br/>
Typ, na který se bude vstup snižovat, což může být jiné než vstupní typ elementu. Hodnota vrácená hodnota a identita bude mít tento typ.

*_Range_reduce_fun*<br/>
Typ funkce pro snížení rozsahu. Musí se jednat o typ funkce s podpisem `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type je stejný jako typ identity a výsledný typ omezení.

*_Begin*<br/>
Vstupní iterátor adresující první prvek v rozsahu, který má být snížen.

*_End*<br/>
Vstupní iterátor adresující prvek, který je o jednu pozici nad koncovým prvkem v rozsahu, který má být snížen.

*_Identity*<br/>
Hodnota identity `_Identity` je stejného typu jako typ výsledku zmenšení a také `value_type` iterátoru pro první a druhé přetížení. Pro třetí přetížení musí mít hodnota identity stejný typ jako typ výsledku zmenšení, ale může se lišit od `value_type` iterátoru. Musí mít odpovídající hodnotu tak, aby operátor zmenšení rozsahu `_Range_fun`, když se aplikuje na rozsah jednoho elementu typu `value_type` a hodnota identity se chová jako přetypování typu hodnoty z typu `value_type` na typ identity.

*_Sym_fun*<br/>
Symetrická funkce, která bude použita v druhé části zmenšení. Další informace najdete v tématu poznámky.

*_Range_fun*<br/>
Funkce, která bude použita v první fázi zmenšení. Další informace najdete v tématu poznámky.

### <a name="return-value"></a>Návratová hodnota

Výsledek snížení.

### <a name="remarks"></a>Poznámky

Aby bylo možné provést paralelní snížení, funkce rozdělí rozsah na bloky na základě počtu pracovních procesů, které jsou k dispozici pro základní Plánovač. Zmenšení probíhá ve dvou fázích, první fáze provádí snížení v rámci každého bloku a druhá fáze provádí snížení částečných výsledků z každého bloku.

První přetížení vyžaduje, aby `value_type`iterátoru, `T`, byly stejné jako typ hodnoty identity a také typ výsledku snížení. Typ elementu T musí poskytovat operátor `T T::operator + (T)` pro omezení prvků v každém bloku. Stejný operátor se používá také ve druhé fázi.

Druhé přetížení také vyžaduje, aby `value_type` iterátoru byl stejný jako typ hodnoty identity a také typ výsledku snížení. Zadaný binární operátor `_Sym_fun` se používá v obou fázích redukce s hodnotou identity jako počáteční hodnotou pro první fázi.

Pro třetí přetížení musí být typ hodnoty identity stejný jako typ výsledku omezení, ale `value_type` iterátoru se může lišit od obou. Funkce zmenšení rozsahu `_Range_fun` se používá v první fázi s hodnotou identity jako počáteční hodnota a binární funkce `_Sym_reduce_fun` se použije k dílčím výsledkům ve druhé fázi.

## <a name="parallel_sort"></a>parallel_sort

Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle kritéria řazení určeného binárním predikátem paralelně. Tato funkce je sémanticky podobná `std::sort` v tom, že se jedná o porovnání nestabilního a místního řazení na místě.

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
Typ binárního porovnání funktor.

*_Begin*<br/>
Iterátor náhodného přístupu, který adresuje umístění prvního prvku v rozsahu, který má být seřazen.

*_End*<br/>
Iterátor náhodného přístupu, který adresuje pozici jednu za posledním prvkem v rozsahu, který má být seřazen.

*_Func*<br/>
Objekt funkce predikátu definovaný uživatelem, který definuje kritérium porovnání, které se má splnit po sobě jdoucích prvků v řazení. Binární predikát přijímá dva argumenty a vrací **hodnotu true** , pokud je splněno, a **false** , pokud není splněna. Tato funkce komparátor musí pro páry prvků z sekvence vytvořit přísné slabé řazení.

*_Chunk_size*<br/>
Minimální velikost bloku dat, který bude rozdělen do dvou pro paralelní spuštění.

### <a name="remarks"></a>Poznámky

První přetížení používá binární komparátor `std::less`.

Druhé přetížení používá poskytnutý binární komparátor, který by měl mít podpis `bool _Func(T, T)`, kde `T` je typ prvků ve vstupním rozsahu.

Algoritmus rozdělí vstupní rozsah do dvou bloků dat a postupně rozděluje každý blok na dvě dílčí bloky pro spuštění paralelně. Nepovinný argument `_Chunk_size` lze použít k označení algoritmu, který by měl zpracovávat bloky velikosti < `_Chunk_size` sériové.

## <a name="parallel_transform"></a>parallel_transform

Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a kopíruje návratové hodnoty objektu Functions do cílového rozsahu paralelně. Tato funkce je sémanticky rovnocenná `std::transform`.

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
Typ prvního nebo pouze vstupního iterátoru.

*_Output_iterator*<br/>
Typ výstupního iterátoru.

*_Unary_operator*<br/>
Typ unárního funktor, který má být proveden u každého prvku ve vstupním rozsahu.

*_Input_iterator2*<br/>
Typ druhého vstupního iterátoru.

*_Binary_operator*<br/>
Typ binárního funktor spustil párový na elementy ze dvou zdrojových rozsahů.

*_Partitioner*<br/>
*first1*<br/>
Vstupní iterátor adresující pozici prvního prvku v prvním nebo pouze zdrojovém rozsahu, na kterém má být provozován.

*last1*<br/>
Vstupní iterátor adresující pozici jednu za poslední prvek v prvním nebo pouze zdrojovém rozsahu, na kterém má být provozován.

*_Result*<br/>
Výstupní iterátor adresující pozici prvního prvku v cílovém rozsahu.

*_Unary_op*<br/>
Uživatelem definovaný unární objekt funkce, který je použit pro každý prvek ve zdrojovém rozsahu.

*_Part*<br/>
Odkaz na objekt rozdělovače. Argument může být jeden z `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`, `const`[simple_partitioner](simple-partitioner-class.md)`&` nebo [affinity_partitioner](affinity-partitioner-class.md)`&`, pokud se používá objekt [affinity_partitioner](affinity-partitioner-class.md) , odkaz musí být nekonstantní odkaz l-hodnoty, aby algoritmus mohl uložit stav pro budoucí smyčky pro opakované použití.

*first2*<br/>
Vstupní iterátor adresující pozici prvního prvku v druhém zdrojovém rozsahu, na kterém má být provozován.

*_Binary_op*<br/>
Uživatelsky definovaný objekt binární funkce, který je v dopředných objednávkách použit jako párový, do dvou zdrojových rozsahů.

### <a name="return-value"></a>Návratová hodnota

Výstupní iterátor adresující pozici jednu za poslední prvek v cílovém rozsahu, který přijímá výstupní prvky transformované objektem funkce.

### <a name="remarks"></a>Poznámky

[auto_partitioner](auto-partitioner-class.md) se použije pro přetížení bez argumentu explicitního dělení.

Pro iterátory, které nepodporují náhodný přístup, je podporována pouze [auto_partitioner](auto-partitioner-class.md) .

Přetížení, která přijímají argument `_Unary_op` transformují vstupní rozsah do výstupního rozsahu použitím unárního funktor na každý prvek ve vstupním rozsahu. `_Unary_op` musí podporovat operátor volání funkce s signaturou `operator()(T)`, kde `T` je typ hodnoty rozsahu, na který se provádí iterace.

Přetížení, která přijímají argument `_Binary_op` transformují dva vstupní rozsahy do výstupního rozsahu použitím binárního funktoru na jeden prvek z prvního vstupního rozsahu a jednoho prvku z druhého vstupního rozsahu. `_Binary_op` musí podporovat operátor volání funkce s signaturou `operator()(T, U)` kde `T``U` jsou typy hodnot dvou vstupních iterátorů.

Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a>získávají

Obecná implementace příjmu, která umožňuje kontextu počkat na data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijaty.

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

*Š*<br/>
Typ datové části.

*_Src*<br/>
Ukazatel nebo odkaz na zdroj, ze kterého jsou očekávána data.

*_Timeout*<br/>
Maximální doba, po kterou by měla metoda pro data v milisekundách.

*_Filter_proc*<br/>
Funkce filtru, která určuje, zda mají být zprávy přijaty.

### <a name="return-value"></a>Návratová hodnota

Hodnota ze zdroje typu datové části.

### <a name="remarks"></a>Poznámky

Pokud má parametr `_Timeout` jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, je vyvolána výjimka [operation_timed_out](operation-timed-out-class.md) v případě, že zadaná doba vyprší před přijetím zprávy. Pokud chcete vypršení časového limitu nulové délky, měli byste použít funkci [try_receive](concurrency-namespace-functions.md) , na rozdíl od volání `receive` s časovým limitem `0` (nula), protože je efektivnější a nevyvolává výjimky v časových limitech.

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a>run_with_cancellation_token

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
Objekt funkce, který se spustí. Tento objekt musí podporovat operátor volání funkce s signaturou void (void).

*_Ct*<br/>
Token zrušení, který bude řídit implicitní zrušení objektu Function. Použijte `cancellation_token::none()`, pokud chcete funkci provést bez možnosti implicitního zrušení z nadřazené skupiny úloh.

### <a name="remarks"></a>Poznámky

Všechny body přerušení v objektu Function budou aktivovány při zrušení `cancellation_token`. Explicitní `_Ct` tokenu izoluje tento `_Func` z nadřazeného zrušení, pokud má nadřazený objekt jiný token nebo žádný token.

## <a name="send"></a>posílají

Operace synchronního odeslání, která čeká, až cíl zprávu buď přijme, nebo odmítne.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ datové části.

*_Trg*<br/>
Ukazatel nebo odkaz na cíl, na který se odesílají data.

*_Data*<br/>
Odkaz na data, která mají být odeslána.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva přijata, jinak **false** .

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parametry

*_Scheduler*<br/>
Ambientní Plánovač, který se má nastavit.

## <a name="set_task_execution_resources"></a>set_task_execution_resources

Omezí prostředky spouštění používané Concurrency Runtime interními pracovními vlákny do zadané sady vztahů.

Volání této metody je platné pouze před vytvořením Správce prostředků nebo mezi dvěma životnostmi Správce prostředků. Dá se vyvolat víckrát, dokud Správce prostředků v době vyvolání neexistují. Po nastavení omezení spřažení zůstane v platnosti, dokud nebude další platné volání metody `set_task_execution_resources`.

Zadaná maska spřažení nemusí být podmnožinou masky spřažení procesu. Spřažení procesů bude v případě potřeby aktualizováno.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parametry

*_ProcessAffinityMask*<br/>
Maska spřažení, na kterou mají být Concurrency Runtime pracovním vláknům omezeny. Tuto metodu použijte v systému s více než 64y hardwarových vláken pouze v případě, že chcete omezit Concurrency Runtime na podmnožinu aktuální skupiny procesorů. Obecně platí, že byste měli použít verzi metody, která přijímá pole spřažení skupin jako parametr, aby bylo možné omezit spřažení na počítačích s více než 64 hardwarovými vlákny.

*count*<br/>
Počet položek `GROUP_AFFINITY` v poli určeném parametrem `_PGroupAffinity`.

*_PGroupAffinity*<br/>
Pole `GROUP_AFFINITY`ch položek.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_operation](invalid-operation-class.md) , pokud je v době vyvolání správce prostředků přítomna, a výjimka [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud zadaná spřažení vede k prázdné sadě prostředků.

Verze metody, která přijímá pole spřažení skupin, jako parametr by měla být použita pouze v operačních systémech se systémem Windows 7 nebo vyšší verzí. V opačném případě je vyvolána výjimka [invalid_operation](invalid-operation-class.md) .

Programově se změnou spřažení procesu po vyvolání této metody nedojde k tomu, že Správce prostředků znovu vyhodnotit spřažení, které je omezené na. Všechny změny spřažení procesů by proto měly být provedeny před voláním této metody.

## <a name="swap"></a>adresu

Vyměňuje prvky dvou `concurrent_vector` objektů.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ prvků uložených v souběžných vektorech.

*_Ax*<br/>
Typ přidělování souběžných vektorů.

*_A*<br/>
Souběžný vektor, jehož prvky mají být vyměňovány pomocí souběžných vektorových `_B`.

*_B*<br/>
Souběžný vektor, který poskytuje prvky, které mají být měněny, nebo vektor, jehož prvky mají být vyměňovány pomocí souběžných vektorových `_A`.

### <a name="remarks"></a>Poznámky

Funkce šablony je algoritmus specializovaný na třídu kontejneru `concurrent_vector` ke spuštění členské funkce `_A`. [concurrent_vector:: swap](concurrent-vector-class.md#swap)(`_B`). Jedná se o instance částečného řazení šablon funkcí kompilátorem. Pokud jsou funkce šablony přetíženy takovým způsobem, že shoda šablony s voláním funkce není jedinečná, kompilátor vybere nejvíce specializované verze funkce šablony. Obecná verze funkce šablony, `template <class T> void swap(T&, T&)`, ve třídě algoritmu funguje podle přiřazení a je pomalé operace. Specializovaná verze v každém kontejneru je mnohem rychlejší, protože může pracovat s interní reprezentace třídy kontejneru.

Tato metoda není bezpečná pro souběžnost. Je nutné zajistit, aby při volání této metody žádné další podprocesy neprováděly operace na jednom ze současných vektorů.

## <a name="task_from_exception"></a>task_from_exception

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

## <a name="task_from_result"></a>task_from_result

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

*Š*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Návratová hodnota

## <a name="trace_agents_register_name"></a>Trace_agents_register_name

Přidruží daný název k bloku zprávy nebo agentovi v trasování ETW.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ objektu. Obvykle se jedná o blok zprávy nebo agenta.

*_PObject*<br/>
Ukazatel na blok zprávy nebo agenta, který je pojmenován v trasování.

*_Name*<br/>
Název pro daný objekt.

## <a name="try_receive"></a>try_receive

Obecná implementace try-Receive, která umožňuje kontextu vyhledat data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijaty. Pokud data nejsou připravena, bude metoda vracet **hodnotu false**.

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

*Š*<br/>
Typ datové části

*_Src*<br/>
Ukazatel nebo odkaz na zdroj, ze kterého jsou očekávána data.

*_value*<br/>
Odkaz na místo, kde bude umístěn výsledek.

*_Filter_proc*<br/>
Funkce filtru, která určuje, zda mají být zprávy přijaty.

### <a name="return-value"></a>Návratová hodnota

Hodnota `bool`, která označuje, zda byla v `_value`umístěna datová část.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a>Počkej

Pozastaví aktuální kontext na určenou dobu.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parametry

*_Milliseconds*<br/>
Počet milisekund, po který má být aktuální kontext pozastaven. Pokud je parametr `_Milliseconds` nastaven na hodnotu `0`, aktuální kontext by měl před pokračováním vrátit zpracování do jiných kontextů spustitelný.

### <a name="remarks"></a>Poznámky

Pokud je tato metoda volána v kontextu Concurrency Runtime Scheduleru, Plánovač zjistí jiný kontext, který bude spuštěn na podkladovém prostředku. Vzhledem k tomu, že Scheduler má společný charakter, nemůže tento kontext pokračovat přesně po zadaném počtu milisekund. Pokud je Plánovač zaneprázdněn prováděním jiných úloh, které se do plánovače nedružstvy, čekací doba může být nekonečná.

## <a name="when_all"></a>when_all

Vytvoří úkol, který se úspěšně dokončí po úspěšném dokončení všech úloh zadaných jako argumenty.

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
Pozice prvního prvku v rozsahu prvků, které budou zkombinovány do výsledného úkolu.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které budou zkombinovány do výsledného úkolu.

*_TaskOptions*<br/>
Objekt `task_options`

### <a name="return-value"></a>Návratová hodnota

Úkol, který se úspěšně dokončí po úspěšném dokončení všech vstupních úloh. Pokud jsou vstupní úlohy typu `T`, výstup této funkce bude `task<std::vector<T>>`. Pokud jsou vstupní úlohy typu `void` bude výstupní úloha také `task<void>`.

### <a name="remarks"></a>Poznámky

`when_all` je neblokovaná funkce, která jako svůj výsledek vytvoří `task`. Na rozdíl od [úlohy:: wait](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (Application sta).

Pokud se jedna z úloh zruší nebo vyvolá výjimku, vrácený úkol bude dokončen v počátečním stavu a výjimka, pokud k ní dojde, bude vyvolána při volání [Task:: Get](task-class.md#get) nebo `task::wait` na tomto úkolu.

Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a>when_any

Vytvoří úkol, který se úspěšně dokončí, když se kterákoli z úkolů dodaných jako argumenty úspěšně dokončí.

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
Pozice prvního prvku v rozsahu prvků, které budou zkombinovány do výsledného úkolu.

*_End*<br/>
Pozice prvního prvku mimo rozsah prvků, které budou zkombinovány do výsledného úkolu.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token zrušení, který řídí zrušení vráceného úkolu. Pokud neposkytnete token zrušení, výsledná úloha obdrží token zrušení úlohy, která způsobí, že se bude dokončit.

### <a name="return-value"></a>Návratová hodnota

Úkol, který se úspěšně dokončí, když se jedna ze vstupních úloh úspěšně dokončí. Pokud jsou vstupní úlohy typu `T`, výstup této funkce bude `task<std::pair<T, size_t>>>`, kde první prvek dvojice je výsledkem dokončení úkolu a druhý prvek je index úkolu, který byl dokončen. Pokud jsou vstupní úlohy typu `void` výstupem je `task<size_t>`, kde výsledek je index dokončené úlohy.

### <a name="remarks"></a>Poznámky

`when_any` je neblokovaná funkce, která jako svůj výsledek vytvoří `task`. Na rozdíl od [úlohy:: wait](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (Application sta).

Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
