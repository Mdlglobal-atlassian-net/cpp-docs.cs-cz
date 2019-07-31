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
ms.openlocfilehash: e0f876b3c0971e70763f36622fb72a3dea671461
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682522"
---
# <a name="task-class-concurrency-runtime"></a>task – třída (Concurrency Runtime)

Třída knihovny PPL (Parallel Patterns `task` Library). `task` Objekt představuje práci, kterou lze provádět asynchronně a souběžně s jinými úkoly a paralelní práci vytvořenou pomocí paralelních algoritmů v Concurrency Runtime. Vytvoří výsledek typu `_ResultType` po úspěšném dokončení. Úkoly typu `task<void>` nevyvolávají žádný výsledek. Úkol může čekat a zrušit nezávisle na jiných úkolech. Může se také skládat s dalšími úlohami pomocí pokračování ( `then`) a vzorů spojení ( `when_all`) a volby ( `when_any`). Když je objekt úlohy přiřazen nové proměnné, chování je takové `std::shared_ptr`; jinými slovy, oba objekty reprezentují stejnou základní úlohu.

## <a name="syntax"></a>Syntaxe

```
template <>
class task<void>;

template<typename _ResultType>
class task;
```

#### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ výsledku, který úkol vytvoří. 

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|`result_type`|Typ výsledku, který objekt této třídy vytvoří.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[hybn](#ctor)|Přetíženo. `task` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[get](#get)|Přetíženo. Vrátí výsledek, který vytvořil tento úkol. Pokud úloha není v terminálu, `get` bude volání čekat na dokončení úlohy. Tato metoda nevrací hodnotu, pokud je volána na úkolu s `result_type`. `void`|
|[is_apartment_aware](#is_apartment_aware)|Určuje, zda úloha rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo je od takového úkolu popotomkem.|
|[is_done](#is_done)|Určuje, zda je úloha dokončena.|
|[scheduler](#scheduler)|Vrátí Plánovač pro tuto úlohu.|
|[Stisknutím](#then)|Přetíženo. Přidá úlohu pokračování do této úlohy.|
|[Počkej](#wait)|Počká, až tento úkol dorazí na stav terminálu. Je možné `wait` spustit vloženou úlohu, pokud jsou splněné všechny závislosti úkolů a ještě nebyly vyzvednuty pro spuštění pracovníkem na pozadí.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Přetíženo. Určuje, zda `task` dva objekty reprezentují různé interní úlohy.|
|[operátor =](#operator_eq)|Přetíženo. Nahradí obsah jednoho `task` objektu jiným objektem.|
|[operator==](#operator_eq_eq)|Přetíženo. Určuje, zda `task` dva objekty reprezentují stejnou interní úlohu.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks. h

**Obor názvů:** souběžnost

##  <a name="get"></a>Čtěte

Vrátí výsledek, který vytvořil tento úkol. Pokud úloha není v terminálu, `get` bude volání čekat na dokončení úlohy. Tato metoda nevrací hodnotu, pokud je volána na úkolu s `result_type`. `void`

```
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek úlohy

### <a name="remarks"></a>Poznámky

Pokud je úloha zrušena, volání metody `get` vyvolá výjimku [task_canceled](task-canceled-class.md) . V případě, že úloha zjistila jinou výjimku nebo k ní byla výjimka rozšířena z předchozí úlohy, volání `get` vyvolá tuto výjimku.

> [!IMPORTANT]
>  V aplikaci Univerzální platforma Windows (UWP) Nevolejte metodu [Concurrency:: task:: wait](#wait) nebo `get` ( `wait` Calling `get`) v kódu, který běží ve vlákně uživatelského rozhraní. V opačném případě modul runtime vyvolá [Concurrency:: invalid_operation](invalid-operation-class.md) , protože tyto metody blokují aktuální vlákno a může způsobit, že aplikace přestane reagovat. Nicméně můžete zavolat `get` metodu pro přijetí výsledku předchozí úlohy v pokračování založeném na úkolech, protože výsledek je okamžitě k dispozici.

##  <a name="is_apartment_aware"></a>is_apartment_aware

Určuje, zda úloha rozbalí prostředí Windows Runtime `IAsyncInfo` rozhraní nebo je od takového úkolu popotomkem.

```
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud úloha rozbalí `IAsyncInfo` rozhraní nebo je následníkem takové úlohy, jinak **false** .

##  <a name="is_done"></a>Task:: is_done – metoda (Concurrency Runtime)

Určuje, zda je úloha dokončena.

```
bool is_done() const;
```

### <a name="return-value"></a>Návratová hodnota

True, pokud je úkol dokončený, jinak false.

### <a name="remarks"></a>Poznámky

Funkce vrátí hodnotu true, pokud je úkol dokončený nebo zrušený (s výjimkou uživatele nebo bez něj).

##  <a name="operator_neq"></a>! = – operátor

Určuje, zda `task` dva objekty reprezentují různé interní úlohy.

```
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úkol, který se má porovnat

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekty odkazují na různé podkladové úlohy, a jinak **false** .

##  <a name="operator_eq"></a>operátor =

Nahradí obsah jednoho `task` objektu jiným objektem.

```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Zdrojový `task` objekt.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Jak `task` se chová jako inteligentní ukazatel po přiřazení kopírování, představují tyto `task` objekty stejný aktuální úkol jako `_Other` .

##  <a name="operator_eq_eq"></a>operator = = – operátor

Určuje, zda `task` dva objekty reprezentují stejnou interní úlohu.

```
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úkol, který se má porovnat

### <a name="return-value"></a>Návratová hodnota

**true** , pokud objekty odkazují na stejnou základní úlohu a jinak **false** .

##  <a name="scheduler"></a>Task:: Scheduler – metoda (Concurrency Runtime)

Vrátí Plánovač pro tuto úlohu.

```
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na Plánovač

##  <a name="ctor"></a>hybn

`task` Vytvoří objekt.

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

*T*<br/>
Typ parametru, ze kterého má být vytvořen úkol

*_Param*<br/>
Parametr, ze kterého má být vytvořen úkol Může to být lambda, objekt funkce, `task_completion_event<result_type>` objekt nebo Windows:: Foundation:: IAsyncInfo, pokud používáte úkoly v aplikaci prostředí Windows Runtime. Lambda nebo objekt funkce by měl být typu ekvivalentního k `std::function<X(void)>`, kde X může být proměnná typu `result_type`, `task<result_type>`nebo Windows:: Foundation:: IAsyncInfo v aplikacích prostředí Windows Runtime.

*_TaskOptions*<br/>
Mezi možnosti úlohy patří token zrušení, Plánovač atd.

*_Other*<br/>
Zdrojový `task` objekt.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor pro `task` je přítomen pouze v případě, že chcete, aby bylo možné úlohy používat v rámci kontejnerů. Výchozí vytvořenou úlohu nelze použít, dokud do ní nebudete přiřazovat platnou úlohu. Metody, jako například `wait` , `then` nebo vyvolávají výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) při volání na výchozí vytvořenou úlohu. `get`

Úkol, který je vytvořen z, `task_completion_event` bude dokončen (a bude naplánováno jejich pokračování) při nastavení události dokončení úkolu.

Verze konstruktoru, který přijímá token zrušení, vytvoří úlohu, která může být zrušena pomocí `cancellation_token_source` tokenu, který byl získán z. Úkoly vytvořené bez tokenu zrušení nelze zrušit.

Úkoly vytvořené z `Windows::Foundation::IAsyncInfo` rozhraní nebo lambda, které `IAsyncInfo` vrací rozhraní, dosáhnou stavu terminálu, když se dokončí prostředí Windows Runtime asynchronní operace nebo akce. Podobně se úlohy vytvořené z lambda, které vrací `task<result_type>` stav terminálu, když vnitřní úkol dosáhne svého stavu terminálu, a ne když lambda vrátí.

`task`se chová jako inteligentní ukazatel a je bezpečné předávat podle hodnoty. Dá se k němu přistupovat pomocí více vláken bez nutnosti zámků.

Přetížení konstruktoru, která přijímají rozhraní Windows:: Foundation:: IAsyncInfo nebo lambda vracející takové rozhraní, jsou k dispozici pouze pro prostředí Windows Runtime aplikace.

Další informace najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="then"></a>Stisknutím

Přidá úlohu pokračování do této úlohy.

```
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
Funkce pokračování, která se má provést po dokončení této úlohy Tato funkce pokračování musí jako vstup přebírat proměnnou buď `result_type` nebo `task<result_type>`, kde `result_type` je typ výsledku, který tato úloha vytvoří.

*_TaskOptions*<br/>
Mezi možnosti úlohy patří token zrušení, Plánovač a kontext pokračování. Ve výchozím nastavení jsou předchozí 3 možnosti zděděné od předchozí úlohy.

*_CancellationToken*<br/>
Token zrušení, který se má přidružit k úloze pokračování Pokračující úkol, který je vytvořen bez tokenu zrušení, zdědí token jeho předchozí úlohy.

*_ContinuationContext*<br/>
Proměnná, která určuje, kde by mělo být pokračování spuštěno. Tato proměnná je užitečná jenom při použití v aplikaci pro UWP. Další informace najdete v tématu [task_continuation_context](task-continuation-context-class.md) .

### <a name="return-value"></a>Návratová hodnota

Nově vytvořený úkol pokračování. Výsledný typ vrácené úlohy je určen podle toho, co `_Func` vrátí.

### <a name="remarks"></a>Poznámky

Přetížení `then` , která přijímají lambda nebo funktor, které vrací rozhraní Windows:: Foundation:: IAsyncInfo, jsou k dispozici pouze pro prostředí Windows Runtime aplikace.

Další informace o tom, jak používat pokračování úlohy pro vytváření asynchronní práce, najdete v tématu [Task paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="wait"></a>Počkej

Počká, až tento úkol dorazí na stav terminálu. Je možné `wait` spustit vloženou úlohu, pokud jsou splněné všechny závislosti úkolů a ještě nebyly vyzvednuty pro spuštění pracovníkem na pozadí.

```
task_status wait() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být buď `completed` nebo `canceled`. `task_status` Pokud došlo k výjimce během provádění nebo byla výjimka rozšířena z předchozí úlohy, `wait` vyvolá tuto výjimku.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
>  V aplikaci Univerzální platforma Windows (UWP) Nevolejte `wait` v kódu, který běží ve vlákně uživatelského rozhraní. V opačném případě modul runtime vyvolá [Concurrency:: invalid_operation](invalid-operation-class.md) , protože tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane reagovat. Můžete však zavolat metodu [Concurrency:: task:: Get](#get) pro přijetí výsledku předchozí úlohy v pokračování založeném na úlohách.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
