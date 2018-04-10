---
title: funkce obor názvů souběžnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 66cf776e02d286b04c4fe9338d74d6a9db196a68
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="concurrency-namespace-functions"></a>funkce obor názvů souběžnosti
||||  
|-|-|-|  
|[Alloc](#alloc)|[CreateResourceManager](#createresourcemanager)|[DisableTracing](#disabletracing)|  
|[EnableTracing](#enabletracing)|[Volné](#free)|[GetExecutionContextId](#getexecutioncontextid)|  
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
 Přiděluje blok paměti zadaná velikost z Suballocator ukládání do mezipaměti Concurrency Runtime.  
  
```
void* __cdecl Alloc(size_t _NumBytes);
```  
  
### <a name="parameters"></a>Parametry  
 `_NumBytes`  
 Počet bajtů paměti k přidělení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na nově přidělených paměti.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, které scénáře v aplikaci může využívat Suballocator ukládání do mezipaměti najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="asend"></a>  asend –  
 Operace asynchronní odesílání, která plánuje úlohy rozšíření dat na cílový blok.  
  
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
 `T`  
 Typ dat k odeslání.  
  
 `_Trg`  
 Ukazatel nebo odkaz na cíl, do kterého se data se odesílají.  
  
 `_Data`  
 Odkaz na data, která mají být odeslány.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla přijata dřív, než metoda vrátí, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="cancel_current_task"></a>  cancel_current_task  
 Zruší aktuálně spuštěné úlohy. Tuto funkci lze volat z v textu úlohu přerušit provádění úkolu a způsobit, že ho zadat `canceled` stavu.  
  
 Není podporováno pro volání této funkce, pokud nejsou v rámci textu `task`. Díky tomu bude mít za následek nedefinované chování například chybě nebo zablokování v aplikaci.  
  
```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```  
  
##  <a name="clear"></a>  Zrušte zaškrtnutí  
 Vymaže souběžných fronty zničení všechny aktuálně zařazených do fronty elementy. Tato metoda není bezpečná souběžnosti.  
  
```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```   
  
### <a name="parameters"></a>Parametry  
 `T`  
 `_Ax`  
  
##  <a name="create_async"></a>  create_async –  
 Vytvoří prostředí Windows Runtime asynchronní konstrukce podle objekt uživatelem dodaný lambda nebo funkce. Návratový typ `create_async` je jedním z buď `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, nebo `IAsyncOperationWithProgress<TResult, TProgress>^` podle podpis lambda předaný metodě.  
  
```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 `_Func`  
 Objekt lambda nebo funkce, ze které chcete vytvořit asynchronní konstrukt prostředí Windows Runtime.  
  
### <a name="return-value"></a>Návratová hodnota  
 Asynchronní konstrukce reprezentována IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^, nebo IAsyncOperationWithProgress\<TResult, TProgress > ^. Vrátí rozhraní závisí na podpis lambda předána do funkce.  
  
### <a name="remarks"></a>Poznámky  
 Návratový typ argument lambda Určuje, zda je konstrukce operaci nebo akce.  
  
 Lambdas, které vracet typ void způsobit vytvoření akce. Lambdas, které vrací výsledek typu `TResult` způsobit vytvoření operací TResult.  
  
 Argument lambda může také vrátit `task<TResult>` který zapouzdří asynchronní práce v rámci sám sebe nebo je pokračování řetěz úlohu, která představuje asynchronní pracovní. V takovém případě lambda samotné je proveden vložené, protože úlohy jsou ty, které asynchronní a návratový typ argument lambda je úkony, spočívající k vytvoření asynchronní konstrukce vrácený `create_async`. To znamená, že lambda, který vrátí úlohu,\<void > způsobí, že vytvoření akcí a lambda, který vrátí úlohu,\<TResult > způsobí, že vytvoření operací TResult.  
  
 Argument lambda, může trvat nula, jeden nebo dva argumenty. Platnými argumenty jsou `progress_reporter<TProgress>` a `cancellation_token`, v tomto pořadí, pokud se používají. Lambda bez argumentů způsobí, že vytvoření asynchronní konstrukce bez možnosti pro vytváření sestav průběh. Lambda, která přijímá progress_reporter\<TProgress > způsobí, že `create_async` vrátit asynchronní konstrukce, která sestavy průběhu typu TProgress pokaždé, když `report` je volána metoda progress_reporter objektu. Lambda, která přijímá cancellation_token může používat tento token ke kontrole zrušení nebo předejte ji do úlohy, které vytvoří tak, aby zrušení asynchronní konstrukce způsobí, že zrušení těchto úloh.  
  
 Pokud text objektu lambda nebo funkce vrací výsledek (a ne úlohu\<TResult >), lamdba se spustí asynchronně v rámci procesu MTA v kontextu úlohy modulu Runtime implicitně vytvoří pro ni. `IAsyncInfo::Cancel` Způsobí, že metoda zrušení implicitní úlohy.  
  
 Pokud se text vrátí lambda a úloh, lamba provede vložené a deklarováním lambda provést argument typu `cancellation_token` můžete aktivovat zrušení všech úkolů, které vytvoříte v rámci argument lambda předáním ve při jejich vytváření. Můžete také používat `register_callback` metodu na token, který má způsobit modulu Runtime vyvolání zpětné volání při volání `IAsyncInfo::Cancel` na async operace nebo akce vytváří...  
  
 Tato funkce je pouze k dispozici pro aplikace Windows Runtime.  
  
##  <a name="createresourcemanager"></a>  Createresourcemanager –  
 Vrátí rozhraní, které představuje instanci typu singleton z Concurrency Runtime Resource Manager. Resource Manager zodpovídá za přiřazení zdrojů k plánovače, které chcete vzájemně spolupracovat.  
  
```
IResourceManager* __cdecl CreateResourceManager();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `IResourceManager` Rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Více následných volání této metody bude vrátit stejnou instanci Resource Manager. Každé volání metoda přírůstcích odkaz počet v Resource Manageru a musí odpovídat pomocí volání [iresourcemanager::Release –](http://msdn.microsoft.com/en-us/5d1356ec-fbd3-4284-a361-1e9e20bbb522) metoda, pokud se provádí vašeho scheduleru komunikaci s Resource Managerem.  
  
 [unsupported_os](unsupported-os-class.md) je vyvolána, pokud se operační systém nepodporuje Concurrency Runtime.  
  
##  <a name="create_task"></a>  create_task –  
 Vytvoří PPL [úloh](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f) objektu. `create_task` lze použít kdekoli byste použili jste konstruktor úloh. Je poskytována především pro usnadnění práce, protože umožňuje použít `auto` – klíčové slovo při vytváření úlohy.  
  
```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru, ze kterého má být vytvořená úloha.  
  
 `_ReturnType`  
 `_Param`  
 Parametr, ze kterého má být vytvořená úloha. To může být objekt lambda nebo funkce, `task_completion_event` objektu, na jiný `task` objekt nebo Windows::Foundation::IAsyncInfo rozhraní, pokud používáte úlohy v aplikaci UWP.  
  
 `_TaskOptions`  
 `_Task`  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové úlohy typu `T`, která je odvodit z `_Param`.  
  
### <a name="remarks"></a>Poznámky  
 První přetížení se chová jako úloha konstruktor, který přijímá jeden parametr.  
  
 Druhý přetížení přidruží se nově vytvořená úloha zadaný token zrušení. Pokud použijete toto přetížení nejsou povoleny v jiné předat `task` objektu jako první parametr.  
  
 Typ vrácený úlohy, která je odvozeno z první parametr funkce. Pokud `_Param` je `task_completion_event<T>`, `task<T>`, nebo functor, který vrací buď typ `T` nebo `task<T>`, typ vytvořená úloha je `task<T>`.  
  
 V aplikaci pro UPW Pokud `_Param` je typu Windows::Foundation::IAsyncOperation\<T > ^ nebo Windows::Foundation::IAsyncOperationWithProgress\<T, P > ^, nebo functor, která vrátí jednu z těchto typů, bude mít vytvořená úloha typ `task<T>`. Pokud `_Param` je typu Windows::Foundation::IAsyncAction ^ nebo Windows::Foundation::IAsyncActionWithProgress\<P > ^, nebo functor, která vrátí jednu z těchto typů, bude mít typ vytvořená úloha `task<void>`.  
  
##  <a name="disabletracing"></a>  Disabletracing –  
 Zakáže trasování v Concurrency Runtime. Tato funkce je zastaralý, protože je ve výchozím nastavení neregistrovaná trasování událostí pro Windows.  
  
```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud zakázal správně trasování, `S_OK` je vrácen. Pokud trasování nebyla zahájena dříve, `E_NOT_STARTED` je vrácen  
  
##  <a name="enabletracing"></a>  Enabletracing –  
 Umožňuje trasování v Concurrency Runtime. Tato funkce je zastaralý, protože trasování událostí pro Windows je teď na ve výchozím nastavení.  
  
```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud trasování byl správně inicializován, `S_OK` je vrácená, jinak hodnota `E_NOT_STARTED` je vrácen.  
  
##  <a name="free"></a>  Volné  
 Uvolní blok paměti dříve přidělené `Alloc` metodu Suballocator ukládání do mezipaměti Concurrency Runtime.  
  
```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```  
  
### <a name="parameters"></a>Parametry  
 `_PAllocation`  
 Ukazatel na dříve přidělené paměti `Alloc` metodu, která má být uvolněno. Pokud parametr `_PAllocation` je nastaven na hodnotu `NULL`, tato metoda bude ignorovat ho a vrátí okamžitě.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o tom, které scénáře v aplikaci může využívat Suballocator ukládání do mezipaměti najdete v tématu [Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler  
  
```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="getexecutioncontextid"></a>  GetExecutionContextId  
 Vrací jedinečný identifikátor, který lze přiřadit ke kontextu spuštění, který implementuje `IExecutionContext` rozhraní.  
  
```
unsigned int __cdecl GetExecutionContextId();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedinečný identifikátor pro kontextu spuštění.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete získat identifikátor pro váš kontext provádění před předáte `IExecutionContext` rozhraní jako parametr pro některou z metod nabízí Resource Manager.  
  
##  <a name="getosversion"></a>  GetOSVersion  
 Vrátí verzi operačního systému.  
  
```
IResourceManager::OSVersion __cdecl GetOSVersion();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výčtová hodnota představující operační systém.  
  
### <a name="remarks"></a>Poznámky  
 [unsupported_os](unsupported-os-class.md) je vyvolána, pokud se operační systém nepodporuje Concurrency Runtime.  
  
##  <a name="getprocessorcount"></a>  GetProcessorCount  
 Vrátí počet vláken hardwaru v základním systému.  
  
```
unsigned int __cdecl GetProcessorCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet vláken hardwaru.  
  
### <a name="remarks"></a>Poznámky  
 [unsupported_os](unsupported-os-class.md) je vyvolána, pokud se operační systém nepodporuje Concurrency Runtime.  
  
##  <a name="getprocessornodecount"></a>  Getprocessornodecount –  
 Vrátí počet uzlů NUMA nebo balíčky procesoru v základním systému.  
  
```
unsigned int __cdecl GetProcessorNodeCount();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet uzlů NUMA nebo balíčky procesoru.  
  
### <a name="remarks"></a>Poznámky  
 Pokud systému obsahuje více uzlů NUMA, než procesoru balíčky, je vrácen počet uzlů NUMA, jinak, je vrácen počet balíčků, procesoru.  
  
 [unsupported_os](unsupported-os-class.md) je vyvolána, pokud se operační systém nepodporuje Concurrency Runtime.  
  
##  <a name="getschedulerid"></a>  GetSchedulerId  
 Vrací jedinečný identifikátor, který lze přiřadit k Plánovač, který implementuje `IScheduler` rozhraní.  
  
```
unsigned int __cdecl GetSchedulerId();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Jedinečný identifikátor pro plánovače.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této metody můžete získat identifikátor vašeho scheduleru před předáte `IScheduler` rozhraní jako parametr pro některou z metod nabízí Resource Manager.  
  
##  <a name="internal_assign_iterators"></a>  internal_assign_iterators  
  
```
template<typename T, class _Ax>
template<class _I> 
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```   
  
### <a name="parameters"></a>Parametry  
 `T`  
 `_Ax`  
 `_I`  
 `first`  
 `last`  
  
##  <a name="interruption_point"></a>  interruption_point –  
 Vytvoří bod přerušení pro zrušení. Pokud zrušení probíhá v kontextu, kde tato funkce je volána, to vyvolá výjimku interní, která zruší provádění aktuálně prováděné paralelní práce. Pokud zrušení není v průběhu, funkce neprovede žádnou akci.  
  
```
inline void interruption_point();
```  
  
### <a name="remarks"></a>Poznámky  
 Neměli zachycení interní zrušení výjimky vyvolané `interruption_point()` funkce. Výjimka zachycena, který se zpracovávají modulem runtime a zachytávání ho může způsobit vašeho programu chovat neobvyklým způsobem.  
  
##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling –  
 Vrátí údaj o tom, jestli úloha skupiny vložené který je právě prováděných v aktuálním kontextu je in the midst of active zrušení (nebo bude zanedlouho). Všimněte si, že pokud neexistuje žádná skupina úloh aktuálně spuštěných vložené v aktuálním kontextu se `false` bude vrácen.  
  
```
bool __cdecl is_current_task_group_canceling();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je skupina úkolů, které právě probíhá rušení, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [zrušení](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="make_choice"></a>  make_choice  
 Vytvoří `choice` zasílání zpráv bloku z volitelný `Scheduler` nebo `ScheduleGroup` a dvě nebo více vstupních zdrojů.  
  
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
 `T1`  
 Typ bloku zpráv první zdroje.  
  
 `T2`  
 Typ bloku zpráv druhý zdroje.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `choice` je naplánováno zasílání zpráv bloku.  
  
 `_Item1`  
 První zdroj.  
  
 `_Item2`  
 Druhý zdroj.  
  
 `_Items`  
 Další zdroje.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `choice` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `choice` blok zpráv s dvě nebo více vstupních zdrojů.  
  
##  <a name="make_greedy_join"></a>  make_greedy_join –  
 Vytvoří `greedy multitype_join` zasílání zpráv bloku z volitelný `Scheduler` nebo `ScheduleGroup` a dvě nebo více vstupních zdrojů.  
  
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
 `T1`  
 Typ bloku zpráv první zdroje.  
  
 `T2`  
 Typ bloku zpráv druhý zdroje.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `multitype_join` je naplánováno zasílání zpráv bloku.  
  
 `_Item1`  
 První zdroj.  
  
 `_Item2`  
 Druhý zdroj.  
  
 `_Items`  
 Další zdroje.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `multitype_join` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `greedy multitype_join` blok zpráv s dvě nebo více vstupních zdrojů.  
  
##  <a name="make_join"></a>  make_join –  
 Vytvoří `non_greedy multitype_join` zasílání zpráv bloku z volitelný `Scheduler` nebo `ScheduleGroup` a dvě nebo více vstupních zdrojů.  
  
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
 `T1`  
 Typ bloku zpráv první zdroje.  
  
 `T2`  
 Typ bloku zpráv druhý zdroje.  
  
 `_PScheduler`  
 `Scheduler` Objektu, ve kterém šíření úkolů `multitype_join` je naplánováno zasílání zpráv bloku.  
  
 `_Item1`  
 První zdroj.  
  
 `_Item2`  
 Druhý zdroj.  
  
 `_Items`  
 Další zdroje.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Objektu, ve kterém šíření úkolů `multitype_join` je naplánováno zasílání zpráv bloku. `Scheduler` Objekt použitý je zahrnuto v plánu skupiny.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `non_greedy multitype_join` blok zpráv s dvě nebo více vstupních zdrojů.  
  
##  <a name="make_task"></a>  make_task –  
 Metoda factory pro vytváření `task_handle` objektu.  
  
```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána k provedení práce reprezentována `task_handle` objektu.  
  
 `_Func`  
 Funkce, která bude volána k provedení práce reprezentována `task_handle` objektu. To může být functor lambda, ukazatel na funkci, nebo žádný objektu, která podporuje verzi operátor volání funkce s podpisem `void operator()()`.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `task_handle` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je užitečné, když je potřeba vytvořit `task_handle` objekt pomocí výrazu lambda, protože umožňuje vytvořit objekt, aniž by věděly, true typ lambda functor.  
  
##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort –  
 Uspořádá elementů v zadaném rozsahu do nondescending pořadí, nebo podle řazení kritérium určeného predikátu Binární paralelně. Tato funkce je sémanticky podobná `std::sort` , jsou na základě porovnání nestabilním, místní řazení, s tím rozdílem, že je nutné `O(n)` další prostor a vyžaduje výchozí inicializace pro elementy řazen.  
  
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
 `_Random_iterator`  
 Iterator typ vstupu rozsah.  
  
 `_Allocator`  
 Typ přidělení kompatibilní paměti standardní knihovny C++.  
  
 `_Function`  
 Typ Komparátor, který je binární.  
  
 `_Begin`  
 Náhodným přístupem iterator adresování pozice první prvek v rozsahu k řazení.  
  
 `_End`  
 Náhodným přístupem iterator adresování pozici jeden za poslední element v rozsahu který se má seřadit.  
  
 `_Alloc`  
 Instance přidělení kompatibilní paměti standardní knihovny C++.  
  
 `_Func`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Binární predikát má dva argumenty a vrátí `true` při a `false` při není. Tato funkce komparátoru musí použít striktní slabé řazení na páry elementů z pořadí.  
  
 `_Chunk_size`  
 Minimální velikost dávky, která bude možné rozdělit na dvě pro paralelní zpracování.  
  
### <a name="remarks"></a>Poznámky  
 Všechny přetížení vyžadují `n * sizeof(T)` další místo, kde `n` je počet prvků který se má seřadit, a `T` je typ elementu. Ve většině případů parallel_buffered_sort – zobrazí zlepšení výkonu přes [parallel_sort –](concurrency-namespace-functions.md), měli byste použít ho přes parallel_sort – Pokud máte dostupné paměti.  
  
 Pokud nezadáte binární komparátoru `std::less` se používá jako výchozí, což vyžaduje typ elementu zajistit operátor `operator<()`.  
  
 Pokud nezadáte přidělení typ, nebo instance, přidělení paměti standardní knihovna C++ `std::allocator<T>` se používá k přidělení vyrovnávací paměti.  
  
 Algoritmus rozdělí vstupní oblast na dva bloky a postupně rozdělí každého bloku na dvě dílčí bloky dat pro provedení paralelně. Nepovinný argument `_Chunk_size` slouží k označení algoritmus, že by měl zpracovává bloky o velikosti < `_Chunk_size` sériově.  
  
##  <a name="parallel_for"></a>  parallel_for  
 `parallel_for` iteruje nad rozsah indexy a provede funkci uživatelem zadané při každé iteraci paralelně.  
  
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
 `_Index_type`  
 Typ indexu používá pro iterace.  
  
 `_Function`  
 Typ funkce, která budou spuštěny při každé iteraci.  
  
 `_Partitioner`  
 Typ dělicí metody, která se používá k oddílu zadaný rozsah adres.  
  
 `first`  
 Index prvního mají být zahrnuty do iterace.  
  
 `last`  
 Index jeden za poslední index mají být zahrnuty do iterace.  
  
 `_Step`  
 Hodnotu, podle níž krok během iterace z `first` k `last`. V kroku musí být kladná. [invalid_argument](../../../standard-library/invalid-argument-class.md) je vyvolána, pokud v kroku je menší než 1.  
  
 `_Func`  
 Funkce, které mají být provedeny při každé iteraci. To může být výraz lambda ukazatel na funkci nebo žádné objektu, která podporuje verzi operátor volání funkce s podpisem `void operator()(_Index_type)`.  
  
 `_Part`  
 Odkaz na objekt dělicí metody. Argument může být jedna z `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ dělicí metody](simple-partitioner-class.md) `&` nebo [affinity_partitioner](affinity-partitioner-class.md) `&` Pokud [affinity_partitioner](affinity-partitioner-class.md) objekt se používá, odkaz musí být jiný const l – hodnota referenční, tak, aby algoritmus můžete uložit stav pro budoucí smyčky znovu použít.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_for_each"></a>  parallel_for_each  
 `parallel_for_each` Zadaná funkce se vztahuje na každý prvek v rozsahu, paralelně. Je sémanticky ekvivalentní `for_each` v fungovat `std` obor názvů, s tím rozdílem, že iteraci přes elementy provádí paralelně a neurčené pořadí iterace. Argument `_Func` musí podporovat operátor volání funkce formuláře `operator()(T)` kde parametr `T` je typ položky kontejneru se vstupní přes.  
  
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
 `_Iterator`  
 Typ iterator používaný k iteraci nad kontejneru.  
  
 `_Function`  
 Typ funkce, která se použijí pro každý prvek v rozsahu.  
  
 `_Partitioner`  
 `first`  
 Iterace adresování pozice první prvek má být zahrnut v paralelní iterací.  
  
 `last`  
 Iterace adresování jednoho pozice za poslední element má být zahrnut v paralelní iterací.  
  
 `_Func`  
 Uživatelem definované funkce objekt, který se použije pro každý prvek v rozsahu.  
  
 `_Part`  
 Odkaz na objekt dělicí metody. Argument může být jedna z `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ dělicí metody](simple-partitioner-class.md) `&` nebo [affinity_partitioner](affinity-partitioner-class.md) `&` Pokud [affinity_partitioner](affinity-partitioner-class.md) objekt se používá, odkaz musí být jiný const l – hodnota referenční, tak, aby algoritmus můžete uložit stav pro budoucí smyčky znovu použít.  
  
### <a name="remarks"></a>Poznámky  
 [auto_partitioner](auto-partitioner-class.md) se použije pro přetížení bez explicitního dělicí metody.  
  
 Pro iterátory, které nepodporují náhodný přístup pouze k [auto_partitioner](auto-partitioner-class.md) je podporována.  
  
 Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_invoke"></a>  parallel_invoke  
 Provede zadané jako parametry současně a bloky, dokud dokončily spouštění funkce objekty. Každý objekt funkce může být výraz lambda ukazatel na funkci, nebo žádný objektu, který podporuje operátor volání funkce s podpisem `void operator()()`.  
  
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
 `_Function1`  
 Typ první funkce objekt, který má být provedeny souběžně.  
  
 `_Function2`  
 Typ druhý objekt funkce mají být provedeny souběžně.  
  
 `_Function3`  
 Typ třetí funkce objekt, který má být provedeny souběžně.  
  
 `_Function4`  
 Typ čtvrtý funkce objekt, který má být provedeny souběžně.  
  
 `_Function5`  
 Typ páté funkce objekt, který má být provedeny souběžně.  
  
 `_Function6`  
 Typ šestého funkce objekt, který má být provedeny souběžně.  
  
 `_Function7`  
 Typ sedmého funkce objekt, který má být provedeny souběžně.  
  
 `_Function8`  
 Typ osmého funkce objekt, který má být provedeny souběžně.  
  
 `_Function9`  
 Typ deváté funkce objekt, který má být provedeny souběžně.  
  
 `_Function10`  
 Typ desetinu funkce objekt, který má být provedeny souběžně.  
  
 `_Func1`  
 První objekt funkce mají být provedeny souběžně.  
  
 `_Func2`  
 Druhý objekt funkce mají být provedeny souběžně.  
  
 `_Func3`  
 Třetí funkce objekt, který má být provedeny souběžně.  
  
 `_Func4`  
 Čtvrtý funkce objekt, který má být provedeny souběžně.  
  
 `_Func5`  
 Páté funkce objekt, který má být provedeny souběžně.  
  
 `_Func6`  
 Šesté funkce objekt, který má být provedeny souběžně.  
  
 `_Func7`  
 Sedmého funkce objekt, který má být provedeny souběžně.  
  
 `_Func8`  
 Osmého funkce objekt, který má být provedeny souběžně.  
  
 `_Func9`  
 Deváté funkce objekt, který má být provedeny souběžně.  
  
 `_Func10`  
 Desetinu funkce objekt, který má být provedeny souběžně.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že jeden nebo více objektů funkce zadané jako parametry může spustit vložené na kontext volání.  
  
 Pokud jeden nebo více objektů funkce předat jako parametry této funkce vyvolá výjimku, modul runtime bude vyberte jeden takové výjimky jeho výběru a šířit z volání `parallel_invoke`.  
  
 Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_radixsort"></a>  parallel_radixsort –  
 Jiné sestupném pořadí pomocí radix, řazení algoritmus jsou uspořádány elementy v zadaném rozsahu. Toto je funkce stabilní řazení, který vyžaduje projekce funkci, která můžete promítnout elementy, který se má seřadit do nepodepsaných klíčů jako celé číslo. Výchozí inicializace se vyžaduje pro elementy řazen.  
  
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
 `_Random_iterator`  
 Iterator typ vstupu rozsah.  
  
 `_Allocator`  
 Typ přidělení kompatibilní paměti standardní knihovny C++.  
  
 `_Function`  
 Typ funkce projekce.  
  
 `_Begin`  
 Náhodným přístupem iterator adresování pozice první prvek v rozsahu k řazení.  
  
 `_End`  
 Náhodným přístupem iterator adresování pozici jeden za poslední element v rozsahu který se má seřadit.  
  
 `_Alloc`  
 Instance přidělení kompatibilní paměti standardní knihovny C++.  
  
 `_Proj_func`  
 Objekt funkce projekce definovaný uživatelem, který převádí element do celočíselné hodnoty.  
  
 `_Chunk_size`  
 Minimální velikost dávky, která bude možné rozdělit na dvě pro paralelní zpracování.  
  
### <a name="remarks"></a>Poznámky  
 Všechny přetížení vyžadují `n * sizeof(T)` další místo, kde `n` je počet prvků který se má seřadit, a `T` je typ elementu. Functor unární projekce s podpisem `I _Proj_func(T)` je potřeba vrátit klíč při zadané elementu, kde `T` je typ elementu a `I` je typ jako celé číslo bez znaménka.  
  
 Pokud funkce projekce nezadáte, použije se výchozí projekce funkci, která jednoduše vrátí prvek pro integrální typy. Funkce se nepodaří kompilovat element není integrální typu chybí funkce projekce.  
  
 Pokud nezadáte přidělení typ, nebo instance, přidělení paměti standardní knihovna C++ `std::allocator<T>` se používá k přidělení vyrovnávací paměti.  
  
 Algoritmus rozdělí vstupní oblast na dva bloky a postupně rozdělí každého bloku na dvě dílčí bloky dat pro provedení paralelně. Nepovinný argument `_Chunk_size` slouží k označení algoritmus, že by měl zpracovává bloky o velikosti < `_Chunk_size` sériově.  
  
##  <a name="parallel_reduce"></a>  parallel_reduce –  
 Vypočítá součet všech elementů v zadaném rozsahu následných částečné součtů computing připravila nebo vypočítá výsledek následných částečné výsledky podobně získané z pomocí zadané operace binární jinak než součtem, paralelně. `parallel_reduce` je sémanticky podobná `std::accumulate`kromě toho, že vyžaduje binární operace jako asociativní a vyžaduje hodnotu identity namísto počáteční hodnoty.  
  
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
 `_Forward_iterator`  
 Iterator typ vstupu rozsah.  
  
 `_Sym_reduce_fun`  
 Typ funkce symetrický snížení. Toto musí být typu funkce podpisem `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, kde _Reduce_type je stejný jako typ identity a výsledný typ omezení. Pro třetí přetížení, to by měl být konzistentní s typem výstupu `_Range_reduce_fun`.  
  
 `_Reduce_type`  
 Typ, který se sníží vstupu, který se může lišit od typ elementu input. Tento typ se má vrátit hodnotu a hodnotu identity.  
  
 `_Range_reduce_fun`  
 Typ funkce snížení rozsahu. Toto musí být typu funkce podpisem `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type je stejný jako typ identity a výsledný typ omezení.  
  
 `_Begin`  
 Vstupní iterovat adresování prvním elementem v rozsahu snížení.  
  
 `_End`  
 Vstupní iterovat adresování elementu, který je v rozsahu snížení jednu pozici nad rámec konečné elementu.  
  
 `_Identity`  
 Hodnotu identity `_Identity` je stejného typu jako typ výsledku snížení a také `value_type` z iterator pro první a druhý přetížení. Pro třetí přetížení, musí mít stejný typ jako typ výsledku snížení hodnotu identity, ale může lišit od `value_type` z iteraci. Musí mít odpovídající hodnotu tak, aby operátor snížení rozsahu `_Range_fun`, při použití na rozsah jednoho prvku typu `value_type` a hodnotu identity, chová se jako přetypování z typu hodnoty `value_type` typu identity.  
  
 `_Sym_fun`  
 Symetrické funkce, která se použije za sekundu snížení. Další informace naleznete v poznámky.  
  
 `_Range_fun`  
 Funkce, která bude použita v první fázi snížení. Další informace naleznete v poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek snížení.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete provést paralelní snížení, funkce rozděluje rozsahu do bloků dat na základě počtu pracovních procesů, které jsou k dispozici pro základní plánovač. Snížení došlo ve dvou fázích, první fázi provádí snížení v rámci každého bloku a druhé fáze provede snížení mezi částečné výsledky z každého bloku.  
  
 První přetížení vyžaduje, aby iteraci `value_type`, `T`, být stejný jako typ hodnoty identity, jakož i typ výsledku snížení. Typ elementu T musíte zadat operátor `T T::operator + (T)` ke snížení elementů v každého bloku. V druhé fázi se používá stejné operátor.  
  
 Druhý přetížení také vyžaduje, aby iteraci `value_type` být stejný jako typ hodnoty identity, jakož i typ výsledku snížení. Zadaný binární operátor `_Sym_fun` se používá v obou snížení fází, s hodnotou identity jako počáteční hodnotu pro první fázi.  
  
 Pro třetí přetížení typ hodnoty identity musí být stejný jako typ výsledku snížení, ale iteraci `value_type` může lišit od obě. Funkce snížení rozsah `_Range_fun` se používá v první fázi s hodnotu identity jako výchozí hodnoty a binární funkce `_Sym_reduce_fun` se použije na dílčí výsledky v druhé fázi.  
  
##  <a name="parallel_sort"></a>  parallel_sort  
 Uspořádá elementů v zadaném rozsahu do nondescending pořadí, nebo podle řazení kritérium určeného predikátu Binární paralelně. Tato funkce je sémanticky podobná `std::sort` v, že je na základě porovnání nestabilním, místní řazení.  
  
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
 `_Random_iterator`  
 Iterator typ vstupu rozsah.  
  
 `_Function`  
 Typ functor binární porovnání.  
  
 `_Begin`  
 Náhodným přístupem iterator adresování pozice první prvek v rozsahu k řazení.  
  
 `_End`  
 Náhodným přístupem iterator adresování pozici jeden za poslední element v rozsahu který se má seřadit.  
  
 `_Func`  
 Uživatelem definované funkce predikátu objekt, který definuje kritéria porovnání měly splňovat po sobě následujících elementů v řazení. Binární predikát má dva argumenty a vrátí `true` při a `false` při není. Tato funkce komparátoru musí použít striktní slabé řazení na páry elementů z pořadí.  
  
 `_Chunk_size`  
 Minimální velikost dávky, která bude možné rozdělit na dvě pro paralelní zpracování.  
  
### <a name="remarks"></a>Poznámky  
 První přetížení používá binární Komparátor `std::less`.  
  
 Druhý přetížený používá zadaný binární Komparátor, který by měl být podpis `bool _Func(T, T)` kde `T` je typ elementů ve vstupní oblasti.  
  
 Algoritmus rozdělí vstupní oblast na dva bloky a postupně rozdělí každého bloku na dvě dílčí bloky dat pro provedení paralelně. Nepovinný argument `_Chunk_size` slouží k označení algoritmus, že by měl zpracovává bloky o velikosti < `_Chunk_size` sériově.  
  
##  <a name="parallel_transform"></a>  parallel_transform  
 Každý prvek v zdrojový rozsah, nebo pár elementy ze dvou zdrojových oblastí se vztahuje objekt zadaná funkce a zkopíruje návratové hodnoty funkce objektu do cílový rozsah, paralelně. Tuto funkční je sémanticky ekvivalentní `std::transform`.  
  
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
 `_Input_iterator1`  
 Typ prvního nebo pouze vstupní iterator.  
  
 `_Output_iterator`  
 Typ iterator výstup.  
  
 `_Unary_operator`  
 Typ functor unární spuštění na každý prvek ve vstupní oblasti.  
  
 `_Input_iterator2`  
 Typ druhého vstupní iterator.  
  
 `_Binary_operator`  
 Typ binární functor provést ukládání na elementy ze dvou zdrojových oblastí.  
  
 `_Partitioner`  
 `first1`  
 Vstupní iterovat adresování pozice první prvek v první nebo pouze rozsah zdrojových ho zpracovat.  
  
 `last1`  
 Vstupní iterovat adresování pozice jeden za poslední element v první nebo pouze zdrojový rozsah ovládání na.  
  
 `_Result`  
 Iterátor výstup adresování pozice první prvek v cílové oblasti.  
  
 `_Unary_op`  
 Objekt unární uživatelem definované funkce, který se použije pro každý prvek v zdrojový rozsah.  
  
 `_Part`  
 Odkaz na objekt dělicí metody. Argument může být jedna z `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ dělicí metody](simple-partitioner-class.md) `&` nebo [affinity_partitioner](affinity-partitioner-class.md) `&` Pokud [affinity_partitioner](affinity-partitioner-class.md) objekt se používá, odkaz musí být jiný const l – hodnota referenční, tak, aby algoritmus můžete uložit stav pro budoucí smyčky znovu použít.  
  
 `first2`  
 Vstupní iterovat adresování pozice první prvek v druhé zdrojový rozsah ovládání na.  
  
 `_Binary_op`  
 Uživatelem definované funkce binární objekt, který se použije ukládání, popořadě do dvou zdrojových oblastí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Iterátor výstup adresování pozici jeden za poslední element v cílovém rozsahu, který přijímá výstup elementy transformovat objekt funkce.  
  
### <a name="remarks"></a>Poznámky  
 [auto_partitioner](auto-partitioner-class.md) se použije pro přetížení bez argument explicitní dělicí metody.  
  
 Pro iterátory, které nepodporují náhodný přístup pouze k [auto_partitioner](auto-partitioner-class.md) je podporována.  
  
 Přetížení, která trvat argument `_Unary_op` transformace vstupní rozsah do rozsahu výstupu použitím functor unární na každý prvek ve vstupní oblasti. `_Unary_op` musí podporovat operátor volání funkce s podpisem `operator()(T)` kde `T` je typ hodnoty se vstupní přes rozsahu.  
  
 Přetížení, která trvat argument `_Binary_op` transformace dva vstupní rozsahy do rozsahu výstupu použitím binární functor na jeden element z první vstupní rozsah a jeden element z druhého vstupní rozsahu. `_Binary_op` musí podporovat operátor volání funkce s podpisem `operator()(T, U)` kde `T`, `U` se hodnota typy dva vstupní iterátory.  
  
 Další informace najdete v tématu [paralelní algoritmy](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="receive"></a>  Přijímat  
 Obecné přijímat implementace povolení kontext, který má čekat na data z přesně jeden zdroj a filtrování hodnoty, které jsou přijaty.  
  
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
 `T`  
 Typ datové části.  
  
 `_Src`  
 Ukazatel nebo odkaz na zdroj, ze kterého je očekávána data.  
  
 `_Timeout`  
 Maximální doba, pro který by měl metodu dat, v milisekundách.  
  
 `_Filter_proc`  
 Filtr funkci, která určuje, zda mají být přijímány zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota ze zdroje typu datové části.  
  
### <a name="remarks"></a>Poznámky  
 Pokud parametr `_Timeout` má jinou hodnotu než konstanta `COOPERATIVE_TIMEOUT_INFINITE`, výjimka [operation_timed_out](operation-timed-out-class.md) je vyvolána, pokud předtím, než je přijata zpráva vyprší platnost zadaného časového intervalu. Pokud chcete nulové délky vypršení časového limitu, měli byste použít [try_receive –](concurrency-namespace-functions.md) funkce a volání `receive` s vypršení časového limitu z `0` (nula), protože je efektivnější a nevyvolá výjimku výjimek časových limitů.  
  
 Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token –  
 Spustí objekt funkce v kontextu token zrušení pro daný okamžitě a synchronně.  
  
```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ objektu funkce, která bude volána.  
  
 `_Func`  
 Objekt funkce, které budou spuštěny. Tento objekt musí podporovat operátor volání funkce podpisem void(void).  
  
 `_Ct`  
 Token zrušení, který bude řídit implicitní zrušení objektu funkce. Použití `cancellation_token::none()` Pokud chcete spustit funkci bez možnosti implicitní zrušení v nadřazené skupině úloh probíhá její zrušení.  
  
### <a name="remarks"></a>Poznámky  
 Budou všechny body přerušení v objektu, funkce při aktivaci `cancellation_token` je zrušená. Explicitní token `_Ct` to bude izolovat `_Func` z nadřazené zrušení, pokud má nadřazený token jiné nebo žádné token.  
  
##  <a name="send"></a>  Odeslat  
 Operaci synchronní odesílání, která čeká na cíl buď přijme nebo odmítne zprávy.  
  
```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ datové části.  
  
 `_Trg`  
 Ukazatel nebo odkaz na cíl, do kterého se data se odesílají.  
  
 `_Data`  
 Odkaz na data, která mají být odeslány.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud zpráva byla přijata, `false` jinak.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler  
  
```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```  
  
### <a name="parameters"></a>Parametry  
 `_Scheduler`  
  
##  <a name="set_task_execution_resources"></a>  set_task_execution_resources –  
 Omezuje provádění prostředky využívané třídou Concurrency Runtime interní pracovních vláken na sady zadané spřažení.  
  
 Je možné volat tuto metodu jenom dříve, než byl vytvořen správce prostředků, nebo mezi dvě životnosti Resource Manager. Může být vyvolán několikrát, dokud správce prostředků neexistuje v čase volání. Po nastavení omezení vztahů zůstává v platnosti, dokud další platný volání `set_task_execution_resources` metoda.  
  
 Zadaná maska spřažení nemusí být podmnožinou Maska spřažení procesu. Proces přidružení aktualizují v případě potřeby.  
  
```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```  
  
### <a name="parameters"></a>Parametry  
 `_ProcessAffinityMask`  
 Maska spřažení, které mají být omezeno Concurrency Runtime pracovních vláken. Tuto metodu použijte v systému, větší než 64 vláken hardwaru, pouze v případě, že chcete omezit na podmnožinu aktuální skupinu procesorů Concurrency Runtime. Obecně platí měli byste použít verzi metody, která přijímá pole spřažení skupiny jako parametr, omezit spřažení na počítače s víc než 64 vláken hardwaru.  
  
 `count`  
 Počet `GROUP_AFFINITY` položky v poli je určena parametrem `_PGroupAffinity`.  
  
 `_PGroupAffinity`  
 Pole `GROUP_AFFINITY` položky.  
  
### <a name="remarks"></a>Poznámky  
 Vyvolá metodu [invalid_operation](invalid-operation-class.md) výjimka, pokud je k dispozici v době vyvolání, Resource Manager a [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka, pokud spřažení zadané v prázdnou sadu výsledků prostředky.  
  
 Verzi metody, která přebírá jako parametr pole spřažení skupiny mají jenom využité v operačních systémech s verzí systému Windows 7 nebo vyšší. Jinak [invalid_operation](invalid-operation-class.md) je vyvolána výjimka.  
  
 Programově úprava spřažení proces po tato metoda byla volána nezpůsobí správce prostředků, aby znovu vyhodnotit, který je omezen na spřažení. Proto všechny změny zpracovat spřažení by měl být provedeny před voláním této metody.  
  
##  <a name="swap"></a>  Swap  
 Výměny dva elementy `concurrent_vector` objekty.  
  
```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Datový typ elementů uložené v souběžných vektory.  
  
 `_Ax`  
 Typ přidělení souběžných vektory.  
  
 `_A`  
 Souběžné vektoru, jehož elementy jsou k výměně s těmi, která souběžných vektoru `_B`.  
  
 `_B`  
 Souběžné vektoru poskytování elementy pro si místo nebo vektoru, jehož elementy jsou k výměně s těmi, která souběžných vektoru `_A`.  
  
### <a name="remarks"></a>Poznámky  
 Funkce šablony je algoritmus specializuje na třídu kontejneru `concurrent_vector` provést – členská funkce `_A`. [concurrent_vector::swap –](concurrent-vector-class.md#swap)( `_B`). Toto jsou instance částečné řazení šablon funkce kompilátorem. Když funkce šablon jsou přetížené tak, že na shodu šabloně se volání funkce není jedinečný, kompilátor vybere nejvíc specializovanou verzi funkce šablony. Obecné verzi funkce šablony `template <class T> void swap(T&, T&)`, v algoritmu třídy funguje tak, že přiřazení a je pomalé operace. Specializovanou verzi v jednotlivých kontejnerech je mnohem rychlejší, jak můžete pracovat s interního vyjádření třídy kontejneru.  
  
 Tato metoda není bezpečná souběžnosti. Je nutné zajistit, že nejsou žádná jiná vlákna provádění operací na buď souběžných vektory při volání této metody.  
  
##  <a name="task_from_exception"></a>  task_from_exception  
  
```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>Parametry  
 `_TaskType`  
 `_ExType`  
 `_Exception`  
 `_TaskOptions`  
  
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
 `T`  
 `_Param`  
 `_TaskOptions`  
  
### <a name="return-value"></a>Návratová hodnota  
  
##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name –  
 Přidruží daným názvem na blokování zpráv nebo agenta v trasování ETW.  
  
```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ objektu. To je obvykle blok zpráv nebo agenta.  
  
 `_PObject`  
 Ukazatel na blokování zpráv nebo agenta, který se jmenuje trasování.  
  
 `_Name`  
 Název pro daný objekt.  
  
##  <a name="try_receive"></a>  try_receive –  
 Obecné zkuste a přijetí implementace povolení kontextu hledat data z přesně jednoho zdroje a filtrovat hodnoty, které jsou přijaty. Pokud data není připraven, metoda vrátí hodnotu false.  
  
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
 `T`  
 Typ datové části  
  
 `_Src`  
 Ukazatel nebo odkaz na zdroj, ze kterého je očekávána data.  
  
 `_value`  
 Odkaz na umístění, kde budou umístěné výsledek.  
  
 `_Filter_proc`  
 Filtr funkci, která určuje, zda mají být přijímány zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `bool` hodnotu, která udává, zda datové části byla uložena v umístění `_value`.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [funkce předávání zpráv](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="wait"></a>  Počkej  
 Aktuální kontext pozastaví na zadanou dobu.  
  
```
void __cdecl wait(unsigned int _Milliseconds);
```  
  
### <a name="parameters"></a>Parametry  
 `_Milliseconds`  
 Počet milisekund, po které aktuální kontext má pozastaví na. Pokud `_Milliseconds` parametr je nastaven na hodnotu `0`, aktuálním kontextu by měl yield na jiném spustitelného kontextu provedení. než budete pokračovat.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato metoda je volána v kontextu scheduler Concurrency Runtime, zjistí Plánovač jiný kontext spuštění na základní prostředku. Plánovač je ve své podstatě spolupráci, a proto nelze tento kontext obnovit přesně po počet milisekund, po zadaný. Pokud plánovač je zaneprázdněn provedením dalších úloh, které zisk spolupráce při pro Plánovač, může být neomezené doba čekání.  
  
##  <a name="when_all"></a>  when_all –  
 Vytvoří úlohu, která se dokončí úspěšně, když všechny úlohy, zadané jako argumenty úspěšně dokončit.  
  
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
 `_Iterator`  
 Typ vstupu iterator.  
  
 `_Begin`  
 Pozice první prvek v rozsahu elementů do výsledná úloha.  
  
 `_End`  
 Pozice první prvek mimo rozsah elementů do výsledná úloha.  
  
 `_TaskOptions`  
  
### <a name="return-value"></a>Návratová hodnota  
 Úloha, která se dokončí úspěšně po všechny vstupní úlohy byly úspěšně dokončeny. Pokud vstupní úlohy jsou typu `T`, bude výstup této funkce `task<std::vector<T>>`. Pokud vstupní úlohy jsou typu `void` bude také výstup úlohy `task<void>`.  
  
### <a name="remarks"></a>Poznámky  
 `when_all` je neblokující funkce, která vytváří `task` jako svůj výsledek. Na rozdíl od [Task::wait –](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (STA aplikace).  
  
 Pokud některou z úloh je zrušená nebo vyvolá výjimku, vrácený úloha dokončí již v rané fázi, v zrušené stavu, a, pokud je encoutered, dojde k výjimce při volání [Task::Get –](task-class.md#get) nebo `task::wait` na úlohu.  
  
 Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="when_any"></a>  when_any –  
 Vytvoří úlohu, která se úspěšně dokončí, když některé z úloh zadané jako argumenty úspěšně dokončena.  
  
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
 `_Iterator`  
 Typ vstupu iterator.  
  
 `_Begin`  
 Pozice první prvek v rozsahu elementů do výsledná úloha.  
  
 `_End`  
 Pozice první prvek mimo rozsah elementů do výsledná úloha.  
  
 `_TaskOptions`  
 `_CancellationToken`  
 Token zrušení, který řídí zrušení vrácený úlohy. Pokud nezadáte token zrušení, výsledná úloha obdrží token zrušení úlohy, které způsobí, že její dokončení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Úloha, která dokončí úspěšně, pokud vstupní úloh byla úspěšně dokončena. Pokud vstupní úlohy jsou typu `T`, bude výstup této funkce `task<std::pair<T, size_t>>>`, kde je první prvek, které odpovídá páru výsledek dokončuje úlohy a druhý prvkem je index úloha, která bylo dokončeno. Pokud vstupní úlohy jsou typu `void` výstup `task<size_t>`, kde je výsledek index dokončuje úlohy.  
  
### <a name="remarks"></a>Poznámky  
 `when_any` je neblokující funkce, která vytváří `task` jako svůj výsledek. Na rozdíl od [Task::wait –](task-class.md#wait), je bezpečné volat tuto funkci v aplikaci UWP ve vlákně ASTA (STA aplikace).  
  
 Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
