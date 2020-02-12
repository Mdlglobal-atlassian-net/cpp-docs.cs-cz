---
title: task – třída (Concurrency Runtime)
ms.date: 07/30/2019
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
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: 3657dc54584b120304ccda13ed93b5a0e37bb4af
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142619"
---
# <a name="task-class-concurrency-runtime"></a>task – třída (Concurrency Runtime)

Knihovna PPL (Parallel Patterns Library) `task` třídy. Objekt `task` představuje práci, kterou lze provádět asynchronně a souběžně s jinými úkoly a paralelní práci vytvořenou paralelními algoritmy v Concurrency Runtime. Vytvoří výsledek typu `_ResultType` po úspěšném dokončení. Úlohy typu `task<void>` nevydávají žádný výsledek. Úkol může čekat a zrušit nezávisle na jiných úkolech. Může se také skládat s ostatními úkoly pomocí pokračování (`then`) a vzorů spojení (`when_all`) a volby (`when_any`). Když je objekt Task přiřazen nové proměnné, chování je `std::shared_ptr`; Jinými slovy, oba objekty reprezentují stejnou základní úlohu.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ výsledku, který úkol vytvoří.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`result_type`|Typ výsledku, který objekt této třídy vytvoří.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[hybn](#ctor)|Přetíženo. Vytvoří objekt `task`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get](#get)|Přetíženo. Vrátí výsledek, který vytvořil tento úkol. Pokud úloha není ve stavu terminálu, volání `get` bude čekat na dokončení úlohy. Tato metoda nevrací hodnotu při volání úlohy s `result_type` `void`.|
|[is_apartment_aware](#is_apartment_aware)|Určuje, zda úloha rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo je od takové úlohy popotomkem.|
|[is_done](#is_done)|Určuje, zda je úloha dokončena.|
|[Plánovač](#scheduler)|Vrátí Plánovač pro tuto úlohu.|
|[Stisknutím](#then)|Přetíženo. Přidá úlohu pokračování do této úlohy.|
|[Počkej](#wait)|Počká, až tento úkol dorazí na stav terminálu. Je možné, aby `wait` spustila vloženou úlohu, pokud jsou splněné všechny závislosti úkolů a ještě není vyzvednuta pro spuštění pracovním procesem na pozadí.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Přetíženo. Určuje, zda dva objekty `task` reprezentují různé interní úlohy.|
|[operátor =](#operator_eq)|Přetíženo. Nahradí obsah jednoho `task` objektu jiným objektem.|
|[operator = = – operátor](#operator_eq_eq)|Přetíženo. Určuje, zda dva objekty `task` reprezentují stejnou interní úlohu.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks. h

**Obor názvů:** souběžnost

## <a name="get"></a>Čtěte

Vrátí výsledek, který vytvořil tento úkol. Pokud úloha není ve stavu terminálu, volání `get` bude čekat na dokončení úlohy. Tato metoda nevrací hodnotu při volání úlohy s `result_type` `void`.

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek úlohy

### <a name="remarks"></a>Poznámky

Pokud je úloha zrušena, volání `get` vyvolá výjimku [task_canceled](task-canceled-class.md) . V případě, že úloha zjistila jinou výjimku nebo k ní byla výjimka rozšířena z předchozí úlohy, volání `get` vyvolá tuto výjimku.

> [!IMPORTANT]
> V aplikaci Univerzální platforma Windows (UWP) Nevolejte metodu [Concurrency:: task:: wait](#wait) nebo `get` (`wait` volá `get`) v kódu, který běží ve vlákně uživatelského rozhraní. V opačném případě modul runtime vyvolá [Concurrency:: invalid_operation](invalid-operation-class.md) , protože tyto metody blokují aktuální vlákno a může způsobit, že aplikace přestane reagovat. Můžete však zavolat metodu `get` pro přijetí výsledku předchozí úlohy v pokračování založeném na úkolech, protože výsledek je okamžitě k dispozici.

## <a name="is_apartment_aware"></a>is_apartment_aware

Určuje, zda úloha rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo je od takové úlohy popotomkem.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Návratová hodnota

**hodnota true** v případě, že úloha rozbalí `IAsyncInfo` rozhraní nebo je následníkem této úlohy, jinak **false** .

## <a name="is_done"></a>Task:: is_done – metoda (Concurrency Runtime)

Určuje, zda je úloha dokončena.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>Návratová hodnota

True, pokud je úkol dokončený, jinak false.

### <a name="remarks"></a>Poznámky

Funkce vrátí hodnotu true, pokud je úkol dokončený nebo zrušený (s výjimkou uživatele nebo bez něj).

## <a name="operator_neq"></a>! = – operátor

Určuje, zda dva objekty `task` reprezentují různé interní úlohy.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úkol, který se má porovnat

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekty odkazují na různé podkladové úlohy, a jinak **false** .

## <a name="operator_eq"></a>operátor =

Nahradí obsah jednoho `task` objektu jiným objektem.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Zdrojový objekt `task`.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Když se `task` chová jako inteligentní ukazatel po přiřazení kopírování, představuje tento objekt `task` stejný skutečný úkol jako `_Other`.

## <a name="operator_eq_eq"></a>operator = = – operátor

Určuje, zda dva objekty `task` reprezentují stejnou interní úlohu.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úkol, který se má porovnat

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekty odkazují na stejnou základní úlohu a jinak **false** .

## <a name="scheduler"></a>Task:: Scheduler – metoda (Concurrency Runtime)

Vrátí Plánovač pro tuto úlohu.

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na Plánovač

## <a name="ctor"></a>hybn

Vytvoří objekt `task`.

```cpp
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

*Š*<br/>
Typ parametru, ze kterého má být vytvořen úkol

*_Param*<br/>
Parametr, ze kterého má být vytvořen úkol Může to být lambda, objekt funkce, objekt `task_completion_event<result_type>` nebo Windows:: Foundation:: IAsyncInfo, pokud používáte úkoly v aplikaci prostředí Windows Runtime. Výraz lambda nebo objekt funkce by měl být typu ekvivalentního `std::function<X(void)>`, kde X může být proměnná typu `result_type`, `task<result_type>`nebo Windows:: Foundation:: IAsyncInfo v aplikacích prostředí Windows Runtime.

*_TaskOptions*<br/>
Mezi možnosti úlohy patří token zrušení, Plánovač atd.

*_Other*<br/>
Zdrojový objekt `task`.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor pro `task` je k dispozici pouze v zájmu umožnění použití úloh v rámci kontejnerů. Výchozí vytvořenou úlohu nelze použít, dokud do ní nebudete přiřazovat platnou úlohu. Metody, jako `get`, `wait` nebo `then`, vyvolávají výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) při volání na výchozí vytvořenou úlohu.

Úkol vytvořený z `task_completion_event` bude dokončen (a bude naplánováno jejich pokračování) při nastavení události dokončení úkolu.

Verze konstruktoru, který přijímá token zrušení, vytvoří úlohu, kterou lze zrušit pomocí `cancellation_token_source`, ze kterého byl token získán. Úkoly vytvořené bez tokenu zrušení nelze zrušit.

Úkoly vytvořené z rozhraní `Windows::Foundation::IAsyncInfo` nebo lambda, které vrací rozhraní `IAsyncInfo`, dosáhnou stavu terminálu, když je uzavřená prostředí Windows Runtime asynchronní operace nebo akce dokončena. Podobně úlohy vytvořené z lambda, které vrací `task<result_type>` dosáhnou stavu terminálu, když vnitřní úkol dosáhne svého stavu terminálu, a ne, když vrátí výraz lambda.

`task` se chová jako inteligentní ukazatel a je bezpečné předávat podle hodnoty. Dá se k němu přistupovat pomocí více vláken bez nutnosti zámků.

Přetížení konstruktoru, která přijímají rozhraní Windows:: Foundation:: IAsyncInfo nebo lambda vracející takové rozhraní, jsou k dispozici pouze pro prostředí Windows Runtime aplikace.

Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="then"></a>Stisknutím

Přidá úlohu pokračování do této úlohy.

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

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

*_Function*<br/>
Typ objektu funkce, který bude vyvolán touto úlohou.

*_Func*<br/>
Funkce pokračování, která se má provést po dokončení této úlohy Tato funkce pokračování musí jako vstup přebírat proměnnou buď `result_type`, nebo `task<result_type>`, kde `result_type` je typ výsledku, který tato úloha vytvoří.

*_TaskOptions*<br/>
Mezi možnosti úlohy patří token zrušení, Plánovač a kontext pokračování. Ve výchozím nastavení jsou předchozí 3 možnosti zděděné od předchozí úlohy.

*_CancellationToken*<br/>
Token zrušení, který se má přidružit k úloze pokračování Pokračující úkol, který je vytvořen bez tokenu zrušení, zdědí token jeho předchozí úlohy.

*_ContinuationContext*<br/>
Proměnná, která určuje, kde by mělo být pokračování spuštěno. Tato proměnná je užitečná jenom při použití v aplikaci pro UWP. Další informace najdete v tématu [task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Návratová hodnota

Nově vytvořený úkol pokračování. Výsledný typ vrácené úlohy je určen podle toho, co `_Func` vrátí.

### <a name="remarks"></a>Poznámky

Přetížení `then`, která přebírají lambda nebo funktor, které vrací rozhraní Windows:: Foundation:: IAsyncInfo, jsou k dispozici pouze pro prostředí Windows Runtime aplikace.

Další informace o tom, jak používat pokračování úlohy pro vytváření asynchronní práce, najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="wait"></a>Počkej

Počká, až tento úkol dorazí na stav terminálu. Je možné, aby `wait` spustila vloženou úlohu, pokud jsou splněné všechny závislosti úkolů a ještě není vyzvednuta pro spuštění pracovním procesem na pozadí.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>Návratová hodnota

`task_status` hodnota, která může být buď `completed` nebo `canceled`. Pokud došlo k výjimce během provádění nebo došlo k výjimce z předchozí úlohy, `wait` vyvolá tuto výjimku.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
> V aplikaci Univerzální platforma Windows (UWP) Nevolejte `wait` v kódu, který běží ve vlákně uživatelského rozhraní. V opačném případě modul runtime vyvolá [Concurrency:: invalid_operation](invalid-operation-class.md) , protože tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane reagovat. Můžete však zavolat metodu [Concurrency:: task:: Get](#get) pro přijetí výsledku předchozí úlohy v pokračování založeném na úlohách.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
