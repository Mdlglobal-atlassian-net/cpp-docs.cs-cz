---
title: task_options – třída (Concurrency Runtime)
ms.date: 11/04/2016
f1_keywords:
- ppltasks/concurrency::task_options
ms.assetid: f93d146b-70f7-46ec-8c2f-c33b8bb0af69
ms.openlocfilehash: 5f60a07d709a79f3ce4845c8fbd1c40cb2ee7328
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142535"
---
# <a name="task_options-class-concurrency-runtime"></a>task_options – třída (Concurrency Runtime)

Představuje povolené možnosti pro vytvoření úlohy.

## <a name="syntax"></a>Syntaxe

```cpp
class task_options;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[task_options:: task_options – konstruktor (Concurrency Runtime)](#ctor)|Přetíženo. Výchozí seznam možností vytvoření úlohy|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[task_options:: get_cancellation_token – metoda (Concurrency Runtime)](#get_cancellation_token)|Vrátí token zrušení.|
|[task_options:: get_continuation_context – metoda (Concurrency Runtime)](#get_continuation_context)|Vrátí kontext pokračování.|
|[task_options:: get_scheduler – metoda (Concurrency Runtime)](#get_scheduler)|Vrátí Scheduler.|
|[task_options:: has_cancellation_token – metoda (Concurrency Runtime)](#has_cancellation_token)|Indikuje, jestli byl token zrušení zadaný uživatelem.|
|[task_options:: has_scheduler – metoda (Concurrency Runtime)](#has_scheduler)|Indikuje, jestli uživatel zadal Scheduler n.|
|[task_options:: set_cancellation_token – metoda (Concurrency Runtime)](#set_cancellation_token)|Nastaví daný token v možnostech.|
|[task_options:: set_continuation_context – metoda (Concurrency Runtime)](#set_continuation_context)|Nastaví daný kontext pokračování v možnostech.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`task_options`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppltasks. h

**Obor názvů:** souběžnost

## <a name="get_cancellation_token"></a>task_options:: get_cancellation_token – metoda (Concurrency Runtime)

Vrátí token zrušení.

```cpp
cancellation_token get_cancellation_token() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="get_continuation_context"></a>task_options:: get_continuation_context – metoda (Concurrency Runtime)

Vrátí kontext pokračování.

```cpp
task_continuation_context get_continuation_context() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="get_scheduler"></a>task_options:: get_scheduler – metoda (Concurrency Runtime)

Vrátí Scheduler.

```cpp
scheduler_ptr get_scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="has_cancellation_token"></a>task_options:: has_cancellation_token – metoda (Concurrency Runtime)

Indikuje, jestli byl token zrušení zadaný uživatelem.

```cpp
bool has_cancellation_token() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="has_scheduler"></a>task_options:: has_scheduler – metoda (Concurrency Runtime)

Indikuje, jestli uživatel zadal Scheduler n.

```cpp
bool has_scheduler() const;
```

### <a name="return-value"></a>Návratová hodnota

## <a name="set_cancellation_token"></a>task_options:: set_cancellation_token – metoda (Concurrency Runtime)

Nastaví daný token v možnostech.

```cpp
void set_cancellation_token(cancellation_token _Token);
```

### <a name="parameters"></a>Parametry

`_Token`

## <a name="set_continuation_context"></a>task_options:: set_continuation_context – metoda (Concurrency Runtime)

Nastaví daný kontext pokračování v možnostech.

```cpp
void set_continuation_context(task_continuation_context _ContinuationContext);
```

### <a name="parameters"></a>Parametry

`_ContinuationContext`

## <a name="ctor"></a>task_options:: task_options – konstruktor (Concurrency Runtime)

Výchozí seznam možností vytvoření úlohy

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

[concurrency – obor názvů](concurrency-namespace.md)
