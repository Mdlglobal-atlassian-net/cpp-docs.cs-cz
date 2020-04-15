---
title: task_options – třída (Concurrency Runtime)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: e79dd7979b587ae807c8984a04b79be362b03758
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368594"
---
# <a name="task_options-class-concurrency-runtime"></a>task_options – třída (Concurrency Runtime)

Představuje povolené možnosti pro vytvoření úkolu.

## <a name="syntax"></a>Syntaxe

```cpp
class task_options;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[task_options::task_options konstruktor (souběžnost runtime)](#ctor)|Přetíženo. Výchozí seznam možností vytvoření úkolu|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[task_options::get_cancellation_token metoda (souběžnost runtime)](#get_cancellation_token)|Vrátí token zrušení.|
|[task_options::get_continuation_context metoda (souběžnost runtime)](#get_continuation_context)|Vrátí kontext pokračování.|
|[task_options::get_scheduler metoda (souběžnost runtime)](#get_scheduler)|Vrátí plánovač.|
|[task_options::has_cancellation_token metoda (souběžnost runtime)](#has_cancellation_token)|Označuje, zda byl token zrušení určen uživatelem.|
|[task_options::has_scheduler metoda (souběžnost runtime)](#has_scheduler)|Označuje, zda byl plánovač n určen uživatelem.|
|[task_options::set_cancellation_token metoda (souběžnost runtime)](#set_cancellation_token)|Nastaví daný token v možnostech|
|[task_options::set_continuation_context metoda (souběžnost runtime)](#set_continuation_context)|Nastaví daný kontext pokračování v možnostech.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task_options`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks.h

**Obor názvů:** souběžnost

## <a name="task_optionsget_cancellation_token-method-concurrency-runtime"></a><a name="get_cancellation_token"></a>task_options::get_cancellation_token metoda (souběžnost runtime)

Vrátí token zrušení.

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="task_optionsget_continuation_context-method-concurrency-runtime"></a><a name="get_continuation_context"></a>task_options::get_continuation_context metoda (souběžnost runtime)

Vrátí kontext pokračování.

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="task_optionsget_scheduler-method-concurrency-runtime"></a><a name="get_scheduler"></a>task_options::get_scheduler metoda (souběžnost runtime)

Vrátí plánovač.

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="task_optionshas_cancellation_token-method-concurrency-runtime"></a><a name="has_cancellation_token"></a>task_options::has_cancellation_token metoda (souběžnost runtime)

Označuje, zda byl token zrušení určen uživatelem.

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="task_optionshas_scheduler-method-concurrency-runtime"></a><a name="has_scheduler"></a>task_options::has_scheduler metoda (souběžnost runtime)

Označuje, zda byl plánovač n určen uživatelem.

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="task_optionsset_cancellation_token-method-concurrency-runtime"></a><a name="set_cancellation_token"></a>task_options::set_cancellation_token metoda (souběžnost runtime)

Nastaví daný token v možnostech

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Parametry

`_Token`

## <a name="task_optionsset_continuation_context-method-concurrency-runtime"></a><a name="set_continuation_context"></a>task_options::set_continuation_context metoda (souběžnost runtime)

Nastaví daný kontext pokračování v možnostech.

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Parametry

`_ContinuationContext`

## <a name="task_optionstask_options-constructor-concurrency-runtime"></a><a name="ctor"></a>task_options::task_options konstruktor (souběžnost runtime)

Výchozí seznam možností vytvoření úkolu

```cpp
task_options();

task_options(
    cancellation_token _Token);

task_options(
    task_continuation_context _ContinuationContext);

task_options(
    cancellation_token _Token,
    task_continuation_context _ContinuationContext);

template<typename _SchedType>
task_options(
    std::shared_ptr<_SchedType> _Scheduler);

task_options(
    scheduler_interface& _Scheduler);

task_options(
    scheduler_ptr _Scheduler);

task_options(
    const task_options& _TaskOptions);
```

### <a name="parameters"></a>Parametry

`_SchedType`

`_Token`

`_ContinuationContext`

`_Scheduler`

`_TaskOptions`

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
