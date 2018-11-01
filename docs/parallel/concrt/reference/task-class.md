---
title: task – třída (Concurrency Runtime)
ms.date: 11/04/2016
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
ms.openlocfilehash: c2ac1df322a2778356ce8acca90392fc9f6a17f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482075"
---
# <a name="task-class-concurrency-runtime"></a>task – třída (Concurrency Runtime)

Knihovna paralelních vzorů (PPL) `task` třídy. A `task` objekt představuje práci, kterou lze provádět asynchronně a současně další úkoly a paralelní práci vytvořeno paralelní algoritmy v modulu Runtime souběžnosti. Vygeneruje výsledek typu `_ResultType` při úspěšném dokončení. Úkoly typu `task<void>` nevyrábějí žádný výsledek. Úkol lze počkat a zrušit jej nezávisle na jiných úkolech. Je možné také skládání s ostatními úlohami pokračování ( `then`) a spojení ( `when_all`) a možnost výběru ( `when_any`) vzory.

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

*T*<br/>
Typ objektu úlohy.

*_ReturnType*<br/>
Typ výsledku tohoto úkolu.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`result_type`|Typ výsledku objekt této třídy vytváří.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Úloha](#ctor)|Přetíženo. Vytvoří `task` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get](#get)|Přetíženo. Vrátí výsledek tohoto úkolu. Pokud není úloha v terminálu stavu, volání `get` bude čekat na dokončení úlohy. Tato metoda nevrací hodnotu při volání na úkol `result_type` z `void`.|
|[is_apartment_aware](#is_apartment_aware)|Určuje, zda úkol rozbalí Windows Runtime `IAsyncInfo` rozhraní nebo je potomkem takového úkolu.|
|[is_done](#is_done)|Určuje, pokud je úloha dokončena.|
|[scheduler](#scheduler)|Vrátí Plánovač pro tento úkol|
|[Potom](#then)|Přetíženo. Přidá úlohu pokračování k tomuto úkolu.|
|[Počkej](#wait)|Čeká se na tento úkol dosáhne konečného stavu. Je možné, `wait` k provedla úlohu jako vloženou, pokud jsou splněny všechny závislosti úlohy, a to není již vyzvednuty pro provedení pracovníkem na pozadí.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Přetíženo. Určuje, zda dva `task` objekty představují různé interní úlohy.|
|[operátor =](#operator_eq)|Přetíženo. Nahradí obsah jednoho `task` objekt s jiným.|
|[operator==](#operator_eq_eq)|Přetíženo. Určuje, zda dva `task` objekty představují stejnou interní úlohu.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks.h

**Namespace:** souběžnosti

##  <a name="get"></a> získat

Vrátí výsledek tohoto úkolu. Pokud není úloha v terminálu stavu, volání `get` bude čekat na dokončení úlohy. Tato metoda nevrací hodnotu při volání na úkol `result_type` z `void`.

```
_ReturnType get() const;

void get() const;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek úkolu.

### <a name="remarks"></a>Poznámky

Pokud dojde ke zrušení úlohy, volání `get` vyvolá výjimku [task_canceled](task-canceled-class.md) výjimky. Pokud úloha zjistila jinou výjimku nebo byla výjimka rozšířena z předchozí úlohy, volání `get` vyvolá tuto výjimku.

> [!IMPORTANT]
>  V aplikaci pro univerzální platformu Windows (UPW), nevolejte [Concurrency::Task:: wait](#wait) nebo `get` ( `wait` volání `get`) v kódu, který běží v STA. V opačném případě modul runtime vyvolá [concurrency::invalid_operation](invalid-operation-class.md) vzhledem k tomu, že tyto metody blokují aktuální vlákno a může způsobit, že aplikace přestane reagovat. Můžete však volat `get` metody pro získání výsledku předchozího úkolu v pokračování založeném na úkolech, protože výsledek je ihned k dispozici.

##  <a name="is_apartment_aware"></a> is_apartment_aware –

Určuje, zda úkol rozbalí Windows Runtime `IAsyncInfo` rozhraní nebo je potomkem takového úkolu.

```
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud úkol rozbaluje `IAsyncInfo` rozhraní nebo je potomkem takového úkolu **false** jinak.

##  <a name="is_done"></a>  Task::is_done – metoda (Concurrency Runtime)

Určuje, pokud je úloha dokončena.

```
bool is_done() const;
```

### <a name="return-value"></a>Návratová hodnota

True, pokud úkol je dokončen, jinak false.

### <a name="remarks"></a>Poznámky

Tato funkce vrací true, pokud je úloha dokončena nebo zrušena (s nebo bez výjimky uživatele).

##  <a name="operator_neq"></a> Operator! =

Určuje, zda dva `task` objekty představují různé interní úlohy.

```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úloha k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekty odkazují na různé základní úkoly a **false** jinak.

##  <a name="operator_eq"></a> operátor =

Nahradí obsah jednoho `task` objekt s jiným.

```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
Zdroj `task` objektu.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Jako `task` se chová jako inteligentní ukazatel, po přiřazení kopie, to `task` objekty představuje stejné skutečné úlohy jako `_Other` nepodporuje.

##  <a name="operator_eq_eq"></a> Operator ==

Určuje, zda dva `task` objekty představují stejnou interní úlohu.

```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úloha k porovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekty odkazují na stejný základní úkol a **false** jinak.

##  <a name="scheduler"></a>  Task::Scheduler – metoda (Concurrency Runtime)

Vrátí Plánovač pro tento úkol

```
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na Plánovač

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

*T*<br/>
Typ parametru, ze kterého se má úloha sestavit.

*_Param*<br/>
Parametr, ze kterého se má úloha sestavit. To může být lambda, objekt funkce `task_completion_event<result_type>` objektu nebo Windows::Foundation:: iasyncinfo, pokud používáte úkoly v aplikaci pro Windows Runtime. Objekt lambda nebo funkce by měl být odpovídající typ `std::function<X(void)>`, kde X může být proměnná typu `result_type`, `task<result_type>`, nebo Windows::Foundation:: iasyncinfo v aplikacích pro Windows Runtime.

*_TaskOptions*<br/>
Mezi možnosti úkolů patří token zrušení, Plánovač atd

*Ji_né*<br/>
Zdroj `task` objektu.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor `task` nachází pouze aby byly povoleny úlohy pro použití v rámci kontejnerů. Výchozí vyrobený úkol nelze použít, dokud nepřiřadíte platný úkol k němu. Metody jako `get`, `wait` nebo `then` vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka při volání na výchozí vytvořené úloze.

Úloha, která je vytvořena z `task_completion_event` bude dokončen (a bude naplánováno jeho pokračování) je-li nastavena událost dokončení úkolu.

Verze konstruktoru, který přijímá token zrušení, vytvoří se úkol, který může být zrušen pomocí `cancellation_token_source` token, který byl získán z. Úkoly vytvořené bez zrušení tokenu nejsou zrušitelné.

Úkoly vytvořené z `Windows::Foundation::IAsyncInfo` rozhraní nebo lambda vracející `IAsyncInfo` rozhraní dosáhnou svého stavu terminálu, když uzavřené asynchronní operaci Windows Runtime nebo skončení akce. Podobně úkoly vytvořené z lambda, který vrací `task<result_type>` dosáhnou svého stavu terminálu, když vnitřní úkol dosáhne stavu terminálu, a ne v případě, že se vrátí hodnota lambda.

`task` se chová jako inteligentní ukazatel a je bezpečné předávat podle hodnoty. Je přístupný prostřednictvím více vláken bez potřeby zámků.

Přetížení konstruktoru, které trvat rozhraní Windows::Foundation:: iasyncinfo nebo lambda vracející takovéto rozhraní, jsou dostupné pouze pro aplikace Windows Runtime.

Další informace najdete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="then"></a> Potom

Přidá úlohu pokračování k tomuto úkolu.

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

*_Function*<br/>
Typ objektu funkce, který bude vyvolán tímto úkolem.

*_Func*<br/>
Pokračování funkce pro spuštění při dokončení této úlohy. Tato funkce pokračování musí brát jako vstupní proměnnou buď `result_type` nebo `task<result_type>`, kde `result_type` je typ výsledku tento úkol vytvoří.

*_TaskOptions*<br/>
Mezi možnosti úkolů patří zrušení tokenu, Plánovač a kontext pokračování. Ve výchozím nastavení jsou bývalé 3 možnosti zděděné z předchozí úlohy

*_CancellationToken*<br/>
Token rušení, který chcete přidružit k úloze pokračování. Pokračování úlohy vytvořené bez rušícího tokenu zdědí token svého předchozího úkolu.

*_ContinuationContext*<br/>
Proměnná, která určuje, kde by se měl spustit pokračování. Tato proměnná je užitečná pouze při používaných pro aplikace pro UPW. Další informace najdete v tématu [task_continuation_context –](task-continuation-context-class.md)

### <a name="return-value"></a>Návratová hodnota

Nově vytvořené pokračování úkolu. Typ výsledku vrácené úlohy je určen tím, co `_Func` vrátí.

### <a name="remarks"></a>Poznámky

Přetížení `then` , které přijímají lambdu nebo funktor, který vrací rozhraní Windows::Foundation:: iasyncinfo, jsou dostupné jenom pro aplikace Windows Runtime.

Další informace o tom, jak pomocí úloh pokračování k vytvoření asynchronní práce, naleznete v tématu [paralelismus](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="wait"></a> Počkej

Čeká se na tento úkol dosáhne konečného stavu. Je možné, `wait` k provedla úlohu jako vloženou, pokud jsou splněny všechny závislosti úlohy, a to není již vyzvednuty pro provedení pracovníkem na pozadí.

```
task_status wait() const;
```

### <a name="return-value"></a>Návratová hodnota

A `task_status` hodnotu, která by mohla být `completed` nebo `canceled`. Pokud úloha zjistila výjimku během provádění, nebo byla výjimka rozšířena z předchozí úlohy, `wait` vyvolá tuto výjimku.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
>  V aplikaci pro univerzální platformu Windows (UPW), nevolejte `wait` v kódu, který běží v STA. V opačném případě modul runtime vyvolá [concurrency::invalid_operation](invalid-operation-class.md) vzhledem k tomu, že tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane reagovat. Můžete však volat [Concurrency::Task:: Get](#get) metody pro získání výsledku předchozího úkolu v pokračování založeném na úkolech.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
