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
ms.openlocfilehash: d42c7fbd3e065fc295027b7c56e207b2a49221bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358739"
---
# <a name="task-class-concurrency-runtime"></a>task – třída (Concurrency Runtime)

Třída Paralelní vzorky knihovny `task` (PPL). Objekt `task` představuje práci, která může být provedena asynchronně a souběžně s jinými úkoly a paralelní práce vytvořené paralelní algoritmy v modulu Runtime souběžnosti. Vytváří výsledek typu `_ResultType` při úspěšném dokončení. Úkoly `task<void>` typu nevytvářejí žádný výsledek. Na úkol lze čekat a zrušit jej nezávisle na jiných úkolech. To může být také složen s `then`dalšími úkoly pomocí pokračování( ), a spojit( `when_all`) a volba( `when_any`) vzory. Pokud je objekt úkolu přiřazen k nové proměnné, `std::shared_ptr`je chováním ; jinými slovy, oba objekty představují stejný základní úkol.

## <a name="syntax"></a>Syntaxe

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ výsledku, který vytvoří úkol.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`result_type`|Typ výsledku, který vytvoří objekt této třídy.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Úkol](#ctor)|Přetíženo. Vytvoří `task` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get](#get)|Přetíženo. Vrátí výsledek, který tento úkol vytvořil. Pokud úloha není v terminálovém `get` stavu, bude volání čekat na dokončení úkolu. Tato metoda nevrátí hodnotu při volání na `result_type` `void`úkol s .|
|[is_apartment_aware](#is_apartment_aware)|Určuje, zda úloha rozbalí rozhraní `IAsyncInfo` prostředí Windows Runtime nebo je potomkem takové úlohy.|
|[is_done](#is_done)|Určuje, zda je úkol dokončen.|
|[Plánovač](#scheduler)|Vrátí plánovač pro tento úkol.|
|[Pak](#then)|Přetíženo. Přidá k tomuto úkolu úkol pokračování.|
|[Počkej](#wait)|Čeká na tuto úlohu k dosažení stavu terminálu. Je možné `wait` provést úlohu v řádku, pokud jsou splněny všechny závislosti úkolů a již nebyla přijata k provedení pracovníkem na pozadí.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[operátor!=](#operator_neq)|Přetíženo. Určuje, zda `task` dva objekty představují různé vnitřní úkoly.|
|[operátor =](#operator_eq)|Přetíženo. Nahradí obsah jednoho `task` objektu jiným.|
|[operátor==](#operator_eq_eq)|Přetíženo. Určuje, zda `task` dva objekty představují stejnou vnitřní úlohu.|

## <a name="remarks"></a>Poznámky

Další informace naleznete v [tématu Paralelismus úlohy](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks.h

**Obor názvů:** souběžnost

## <a name="get"></a><a name="get"></a>Dostat

Vrátí výsledek, který tento úkol vytvořil. Pokud úloha není v terminálovém `get` stavu, bude volání čekat na dokončení úkolu. Tato metoda nevrátí hodnotu při volání na `result_type` `void`úkol s .

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek úkolu.

### <a name="remarks"></a>Poznámky

Pokud je úloha zrušena, `get` volání vyvolá [výjimku task_canceled.](task-canceled-class.md) Pokud úloha zjistila jinou výjimku nebo výjimku, která byla rozšířena z `get` předchozí úlohy, volání vyvolá tuto výjimku.

> [!IMPORTANT]
> V aplikaci univerzální platformy Windows (UPW) nevolejte [souběžnost::task::wait](#wait) nebo `get` ( volání `wait` `get`) v kódu, který běží ve vlákně uživatelského rozhraní. V opačném případě runtime vyvolá [souběžnost::invalid_operation](invalid-operation-class.md) protože tyto metody blokují aktuální vlákno a může způsobit, že aplikace přestane odpovídat. Můžete však volat `get` metodu pro příjem výsledku předchozí úlohy v pokračování založeném na úkolu, protože výsledek je okamžitě k dispozici.

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

Určuje, zda úloha rozbalí rozhraní `IAsyncInfo` prostředí Windows Runtime nebo je potomkem takové úlohy.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** pokud úkol rozbalí `IAsyncInfo` rozhraní nebo je potomkem takového úkolu, **false** jinak.

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>task::is_done Metoda (Souběžnost Runtime)

Určuje, zda je úkol dokončen.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>Návratová hodnota

True Pokud byl úkol dokončen, false jinak.

### <a name="remarks"></a>Poznámky

Funkce vrátí hodnotu true, pokud je úloha dokončena nebo zrušena (s výjimkou uživatele nebo bez něj).

## <a name="operator"></a><a name="operator_neq"></a>operátor!=

Určuje, zda `task` dva objekty představují různé vnitřní úkoly.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úkol porovnat.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud objekty odkazují na různé základní úkoly a **false** jinak.

## <a name="operator"></a><a name="operator_eq"></a>operátor =

Nahradí obsah jednoho `task` objektu jiným.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Zdrojový `task` objekt.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Jak `task` se chová jako inteligentní ukazatel, po `task` přiřazení kopie tyto objekty představují stejný skutečný úkol jako. `_Other`

## <a name="operator"></a><a name="operator_eq_eq"></a>operátor==

Určuje, zda `task` dva objekty představují stejnou vnitřní úlohu.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Úkol porovnat.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud objekty odkazují na stejný základní úkol a **false** jinak.

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>task::Metoda plánovače (Souběžnost Runtime)

Vrátí plánovač pro tento úkol.

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na plánovač

## <a name="task"></a><a name="ctor"></a>Úkol

Vytvoří `task` objekt.

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

*T*<br/>
Typ parametru, ze kterého má být úloha vytvořena.

*_Param*<br/>
Parametr, ze kterého má být úkol vytvořen. To může být lambda, objekt `task_completion_event<result_type>` funkce, objekt nebo Windows::Foundation::IAsyncInfo, pokud používáte úlohy v aplikaci prostředí Windows Runtime. Lambda nebo objekt funkce by měl `std::function<X(void)>`být typ ekvivalentní , `result_type`kde `task<result_type>`X může být proměnná typu , , nebo Windows::Foundation::IAsyncInfo v aplikacích prostředí Windows Runtime.

*_TaskOptions*<br/>
Možnosti úlohy zahrnují token zrušení, plánovač atd.

*_Other*<br/>
Zdrojový `task` objekt.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor pro `task` a je k dispozici pouze za účelem povolení úkoly, které mají být použity v rámci kontejnerů. Výchozí zkonstruovaný úkol nelze použít, dokud mu nepřiřadíte platný úkol. Metody, `get`jako `wait` `then` je například , nebo vyvolá [výjimku invalid_argument](../../../standard-library/invalid-argument-class.md) při volání na výchozí konstruované úlohy.

Úkol, který je `task_completion_event` vytvořen z bude dokončena (a má jeho pokračování naplánováno) při dokončení úkolu událost je nastavena.

Verze konstruktoru, který přebírá token zrušení vytvoří úlohu, `cancellation_token_source` která může být zrušena pomocí tokenu byla získána z. Úkoly vytvořené bez tokenu zrušení nelze zrušit.

Úlohy vytvořené `Windows::Foundation::IAsyncInfo` z rozhraní nebo lambda, který vrací `IAsyncInfo` rozhraní dosáhnout jejich terminálu stavu po uzavření uzavřené ho systému Windows Runtime asynchronní operace nebo akce dokončena. Podobně úkoly vytvořené z lambda, `task<result_type>` který vrátí dosažení jejich terminálu stavu, když vnitřní úkol dosáhne jeho terminálu stavu a ne při lambda vrátí.

`task`chová se jako inteligentní ukazatel a je bezpečné předávat podle hodnoty. To může být přístupné více vláken bez nutnosti uzamčení.

Přetížení konstruktoru, které berou rozhraní Windows::Foundation::IAsyncInfo nebo lambda vracející takové rozhraní, jsou k dispozici pouze pro aplikace prostředí Windows Runtime.

Další informace naleznete v [tématu Paralelismus úlohy](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="then"></a><a name="then"></a>Pak

Přidá k tomuto úkolu úkol pokračování.

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
Typ objektu funkce, který bude vyvolán tímto úkolem.

*_Func*<br/>
Funkce pokračování, která má být spuštěna po dokončení této úlohy. Tato funkce pokračování musí mít jako `result_type` `task<result_type>`vstup `result_type` proměnnou buď nebo , kde je typ výsledku, který tato úloha vytváří.

*_TaskOptions*<br/>
Možnosti úlohy zahrnují token zrušení, plánovač a kontext pokračování. Ve výchozím nastavení jsou předchozí 3 možnosti zděděny z předchozí úlohy

*_CancellationToken*<br/>
Token zrušení přidružit k úloze pokračování. Úloha pokračování, která je vytvořena bez tokenu zrušení, zdědí token předchozí úlohy.

*_ContinuationContext*<br/>
Proměnná, která určuje, kde by mělo být provedeno pokračování. Tato proměnná je užitečná pouze při použití v aplikaci UPW. Další informace naleznete [v tématu task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Návratová hodnota

Nově vytvořená úloha pokračování. Výsledek typu vrácené úlohy je `_Func` určena, jaké výnosy.

### <a name="remarks"></a>Poznámky

`then` Přetížení, které trvat lambda nebo functor, který vrací rozhraní Windows::Foundation::IAsyncInfo, jsou k dispozici pouze pro aplikace prostředí Windows Runtime.

Další informace o použití pokračování úlohy k vytvoření asynchronní práce naleznete v [tématu Paralelismus úlohy](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="wait"></a><a name="wait"></a>Počkej

Čeká na tuto úlohu k dosažení stavu terminálu. Je možné `wait` provést úlohu v řádku, pokud jsou splněny všechny závislosti úkolů a již nebyla přijata k provedení pracovníkem na pozadí.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, `task_status` která může `completed` `canceled`být buď nebo . Pokud úloha zjistila výjimku během provádění nebo výjimka byla rozšířena na `wait` něj z předchozí úlohy, vyvolá tuto výjimku.

### <a name="remarks"></a>Poznámky

> [!IMPORTANT]
> V aplikaci univerzální platformy Windows (UPW) nevolejte `wait` kód, který běží ve vlákně uživatelského rozhraní. V opačném případě runtime vyvolá [souběžnost::invalid_operation](invalid-operation-class.md) protože tato metoda blokuje aktuální vlákno a může způsobit, že aplikace přestane odpovídat. Můžete však volat [souběžnost::task::get](#get) metoda pro příjem výsledku předchozí úlohy v pokračování založeném na úkolu.

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
