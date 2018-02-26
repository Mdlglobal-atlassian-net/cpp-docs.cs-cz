---
title: "Task – třída (Concurrency Runtime) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
dev_langs:
- C++
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 80f56f02c8a26e87da3f402ecebf738304408eac
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="task-class-concurrency-runtime"></a>task – třída (Concurrency Runtime)
Paralelní vzory knihovny (PPL) `task` třídy. A `task` objekt představuje práci, kterou lze spustit asynchronně a souběžně další úkoly a paralelní pracovní vytvořené paralelní algoritmy v Concurrency Runtime. Vyvolá výsledek typu `_ResultType` při úspěšném dokončení. Úlohy typu `task<void>` vytvořit žádný výsledek. Úlohu můžete čekali při a zrušení nezávisle na jiné úlohy. Můžete také skládat s ostatními úkoly pomocí pokračování ( `then`) a spojení ( `when_all`) a volba ( `when_any`) vzory.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename T>
class task;

template <>
class task<void>;

template<typename _ReturnType>
class task;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 `T`  
 `_ReturnType`  
 Typ výsledku této úlohy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`result_type`|Typ výsledku vytvoří objekt této třídy.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[task](#ctor)|Přetíženo. Vytvoří `task` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get](#get)|Přetíženo. Vrátí výsledek tato úloha vytváří. Pokud úloha není v terminálu stavu, volání `get` způsobí čekání na dokončení úlohy. Tato metoda nevrátí hodnotu při volání pro úlohy `result_type` z `void`.|  
|[is_apartment_aware](#is_apartment_aware)|Určuje, zda úloha rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo je následníky takových úloh.|  
|[is_done](#is_done)|Určuje, pokud je úloha dokončena.|  
|[scheduler](#scheduler)|Vrátí Plánovač pro tuto úlohu|  
|[then](#then)|Přetíženo. Tato úloha přidá úkolů pokračování.|  
|[wait](#wait)|Čeká se na tento úkol dosáhne stavu terminálu. Je možné, `wait` k provedení úloh vložený, pokud jsou splněny všechny závislosti úkolů a jeho nebyla již byla zachyceny pro provedení pracovníkem pozadí.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Přetíženo. Určuje, zda dva `task` objekty představují různé interních úlohách.|  
|[operator=](#operator_eq)|Přetíženo. Nahradí obsah jedné `task` objekt s jinou.|  
|[operator==](#operator_eq_eq)|Přetíženo. Určuje, zda dva `task` objekty představují stejnou interní úlohu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `task`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppltasks.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="get"></a> GET 

 Vrátí výsledek tato úloha vytváří. Pokud úloha není v terminálu stavu, volání `get` způsobí čekání na dokončení úlohy. Tato metoda nevrátí hodnotu při volání pro úlohy `result_type` z `void`.  
  
```
_ReturnType get() const;

void get() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek úlohy.  
  
### <a name="remarks"></a>Poznámky  
 Pokud zrušení úlohy volání `get` vyvolá výjimku [task_canceled](task-canceled-class.md) výjimka. Pokud úlohy došlo k výjimce různých nebo došlo k výjimce rozšíří z předchůdce úkolů, volání `get` vyvolá výjimku této výjimky.  
  
> [!IMPORTANT]
>  V aplikaci pro univerzální platformu Windows (UWP), nevolejte [concurrency::task::wait](#wait) nebo `get` ( `wait` volání `get`) v kódu, který běží na STA Jinak, modul runtime vyvolá [concurrency::invalid_operation](invalid-operation-class.md) vzhledem k tomu, že tyto metody blokovat aktuální vlákno a může způsobit, že aplikace přestane odpovídat. Můžete však volat `get` metoda přijímat výsledek předchozí úlohou v pokračování založený na úlohách, protože výsledek je ihned k dispozici.  
  
##  <a name="is_apartment_aware"></a> is_apartment_aware – 

 Určuje, zda úloha rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo je následníky takových úloh.  
  
```
bool is_apartment_aware() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud úloha rozbalí `IAsyncInfo` rozhraní nebo je následníky úlohy, `false` jinak.  
  
##  <a name="is_done"></a>  Task::is_done – metoda (Concurrency Runtime)  
 Určuje, pokud je úloha dokončena.  
  
```
bool is_done() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud úloha byla dokončena, false jinak.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vrátí hodnotu true, pokud je úloha dokončit nebo zrušit (s nebo bez uživatelskou výjimkou).  
  
##  <a name="operator_neq"></a> Operator! = 

 Určuje, zda dva `task` objekty představují různé interních úlohách.  
  
```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud objekty odkazují na různé základní úlohy, a `false` jinak.  
  
##  <a name="operator_eq"></a> operátor = 

 Nahradí obsah jedné `task` objekt s jinou.  
  
```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 Zdroj `task` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
 Jako `task` chová jako inteligentní ukazatel, po přiřazení kopírování, to `task` objekty představuje pro stejnou úlohu skutečné jako `_Other` nepodporuje.  
  
##  <a name="operator_eq_eq"></a> Operator == 

 Určuje, zda dva `task` objekty představují stejnou interní úlohu.  
  
```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud objekty odkazují na stejnou základní úlohy, a `false` jinak.  
  
##  <a name="scheduler"></a>  Task::Scheduler – metoda (Concurrency Runtime)  
 Vrátí Plánovač pro tuto úlohu  
  
```
scheduler_ptr scheduler() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na plánovače  
  
##  <a name="ctor"></a> Úloha 

 Vytvoří `task` objektu.  
  
```
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru, ze kterého má být vytvořená úloha.  
  
 `_Param`  
 Parametr, ze kterého má být vytvořená úloha. To může být lambda, objekt funkce, `task_completion_event<result_type>` objekt nebo Windows::Foundation::IAsyncInfo, pokud používáte úlohy v aplikaci Windows Runtime. Objekt lambda nebo funkce musí být typu ekvivalentní `std::function<X(void)>`, kde X lze proměnné typu `result_type`, `task<result_type>`, nebo Windows::Foundation::IAsyncInfo v prostředí Windows Runtime aplikace.  
  
 `_TaskOptions`  
 Úloha možnosti zahrnují scheduler tokenu zrušení atd  
  
 `_Other`  
 Zdroj `task` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí konstruktor `task` nachází pouze chcete-li povolit úlohy, který se má použít v rámci kontejnerů. Výchozí vytvořená úloha nemohou používat, dokud přiřazení platný úkolu. Metody, jako `get`, `wait` nebo `then` vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimky při volání pro výchozí vytvořená úloha.  
  
 Úloha, která je vytvořená z `task_completion_event` dokončí (a její pokračování naplánovali) je-li nastavena události dokončení úlohy.  
  
 Verze konstruktor, který přebírá token zrušení vytvoří úlohu, která se dají zrušit pomocí `cancellation_token_source` token byl získán z. Úkoly vytvořené bez token zrušení nejsou možné zrušit.  
  
 Úlohy vytvořené z `Windows::Foundation::IAsyncInfo` rozhraní nebo lambda, který vrací `IAsyncInfo` rozhraní reach jejich stavu terminálu, po dokončení závorkách asynchronní operaci prostředí Windows Runtime nebo akce. Podobně úlohy vytvořené z lambda, který vrací `task<result_type>` dosáhnout jejich stavu terminálu, když úlohu vnitřní dosáhne stavu terminálu, a ne v případě, že lambda vrátí.  
  
 `task` chová se jako inteligentní ukazatel a je bezpečné předat kolem hodnotou. Byla přístupná pomocí více vláken bez nutnosti zámky.  
  
 Konstruktor přetížení, které trvat Windows::Foundation::IAsyncInfo rozhraní nebo lambda vrácení takového rozhraní, jsou dostupné jenom pro aplikace Windows Runtime.  
  
 Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="then"></a> potom 

 Tato úloha přidá úkolů pokračování.  
  
```
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```   
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ funkce objekt, který bude vyvolán této úlohy.  
  
 `_Func`  
 Funkce pokračování, který se má provést při dokončení této úlohy. Tato funkce pokračování vyžaduje jako vstupní proměnné buď `result_type` nebo `task<result_type>`, kde `result_type` je typ výsledku tato úloha vytvoří.  
  
 `_TaskOptions`  
 Úloha možnosti zahrnují kontext zrušení token, Plánovač a pokračování. Ve výchozím nastavení bývalé 3 možnosti jsou převzaty z předchozí úlohou  
  
 `_CancellationToken`  
 Token zrušení přidružení k úkolů pokračování. Pokračování úlohu, která je vytvořen bez token zrušení zdědí tokenu svou předchozí úlohou.  
  
 `_ContinuationContext`  
 Proměnné, která určuje, kde má být spuštěn pokračování. Tato proměnná je pouze užitečné při použití v aplikaci UWP. Další informace najdete v tématu [task_continuation_context](task-continuation-context-class.md)  
  
### <a name="return-value"></a>Návratová hodnota  
 Nově vytvořený pokračování úloha. Typ výsledku vrácený úlohy je dáno co `_Func` vrátí.  
  
### <a name="remarks"></a>Poznámky  
 Přetížení `then` který trvat lambda nebo functor, který vrací Windows::Foundation::IAsyncInfo rozhraní, které jsou dostupné jenom pro aplikace Windows Runtime.  
  
 Další informace o tom, jak využít pokračování úlohy k vytváření asynchronní pracovní najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="wait"></a> Počkej 

 Čeká se na tento úkol dosáhne stavu terminálu. Je možné, `wait` k provedení úloh vložený, pokud jsou splněny všechny závislosti úkolů a jeho nebyla již byla zachyceny pro provedení pracovníkem pozadí.  
  
```
task_status wait() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `task_status` hodnotu, která může být buď `completed` nebo `canceled`. Pokud úlohy došlo k výjimce během zpracování, nebo došlo k výjimce rozšíří z předchozí úlohou, `wait` vyvolá výjimku této výjimky.  
  
### <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  V aplikaci pro univerzální platformu Windows (UWP), nevolejte `wait` v kódu, který běží na STA Jinak, modul runtime vyvolá [concurrency::invalid_operation](invalid-operation-class.md) vzhledem k tomu, že tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane odpovídat. Můžete však volat [concurrency::task::get](#get) metodu výsledek předchozí úlohou v pokračování založený na úlohách.  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
