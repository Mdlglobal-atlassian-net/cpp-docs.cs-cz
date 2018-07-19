---
title: condition_variable – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- condition_variable/std::condition
- condition_variable/std::condition_variable::condition_variable
- condition_variable/std::condition_variable::native_handle
- condition_variable/std::condition_variable::notify_all
- condition_variable/std::condition_variable::notify_one
- condition_variable/std::condition_variable::wait
- condition_variable/std::condition_variable::wait_for
- condition_variable/std::condition_variable::wait_until
dev_langs:
- C++
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::condition
- std::condition_variable::condition_variable
- std::condition_variable::native_handle
- std::condition_variable::notify_all
- std::condition_variable::notify_one
- std::condition_variable::wait
- std::condition_variable::wait_for
- std::condition_variable::wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: ca85765d6fed21938a61f52f25c1a377ec43c499
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965175"
---
# <a name="conditionvariable-class"></a>condition_variable – třída

Použití `condition_variable` třídy čekání na událost v případě, že máte `mutex` typu `unique_lock<mutex>`. Objekty tohoto typu může mít lepší výkon než objekty typu [condition_variable_any – < unique_lock –\<mutex >>](../standard-library/condition-variable-any-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class condition_variable;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[condition_variable](#condition_variable)|Vytvoří `condition_variable` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[native_handle –](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač condition_variable.|
|[notify_all](#notify_all)|Odblokuje všechna vlákna, která čekají `condition_variable` objektu.|
|[notify_one](#notify_one)|Odblokuje jedno z vláken, která čekají `condition_variable` objektu.|
|[Počkej](#wait)|Blokuje vlákno.|
|[wait_for](#wait_for)|Blokuje vlákno a nastavuje časový interval, po jejímž uplynutí se vlákno odblokuje.|
|[wait_until](#wait_until)|Blokuje vlákno a nastavuje maximální bod v čase, kdy se vlákno odblokuje.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<condition_variable >

**Namespace:** std

## <a name="condition_variable"></a>  condition_variable::condition_variable – konstruktor

Vytvoří `condition_variable` objektu.

```cpp
condition_variable();
```

### <a name="remarks"></a>Poznámky

Pokud není k dispozici není dostatek paměti, vyvolá konstruktor [system_error](../standard-library/system-error-class.md) objekt, který má `not_enough_memory` kód chyby. Pokud objekt nelze vytvořit, protože jiný prostředek není k dispozici, vyvolá konstruktor `system_error` objekt, který má `resource_unavailable_try_again` kód chyby.

## <a name="native_handle"></a>  condition_variable::native_handle –

Vrátí typ specifický pro implementaci představující popisovač condition_variable.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type` je definován jako ukazatel na Concurrency Runtime interních datových struktur.

## <a name="notify_all"></a>  condition_variable::notify_all –

Odblokuje všechna vlákna, která čekají `condition_variable` objektu.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable::notify_one –

Odblokuje jedno z vláken, která čekají na `condition_variable` objektu.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>  condition_variable::wait –

Blokuje vlákno.

```cpp
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK* A [unique_lock –\<vzájemně vyloučený přístup >](../standard-library/unique-lock-class.md) objektu.

*Před* libovolný výraz, který vrátí **true** nebo **false**.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud `condition_variable` objekt signalizován voláním [notify_one](#notify_one) nebo [notify_all](#notify_all). To může také probudit falešně.

V důsledku druhá metoda spustí následující kód.

```cpp
while(!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable::wait_for –

Blokuje vlákno a nastavuje časový interval, po jejímž uplynutí se vlákno odblokuje.

```cpp
template <class Rep, class Period>
cv_status wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time);

template <class Rep, class Period, class Predicate>
bool wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time,
    Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK* A [unique_lock –\<vzájemně vyloučený přístup >](../standard-library/unique-lock-class.md) objektu.

*Rel_time* A `chrono::duration` probudí objekt, který určuje dobu před vlákna.

*Před* libovolný výraz, který vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `cv_status::timeout` Pokud čekání skončí, když *Rel_time* uplynul. V opačném případě vrátí metoda `cv_status::no_timeout`.

Druhá metoda vrátí hodnotu *před*.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud `condition_variable` objekt signalizován voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) , nebo dokud časový interval *Rel_time* uplynul. To může také probudit falešně.

V důsledku druhá metoda spustí následující kód.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable::wait_until –

Blokuje vlákno a nastavuje maximální bod v čase, kdy se vlákno odblokuje.

```cpp
template <class Clock, class Duration>
cv_status wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time);

template <class Clock, class Duration, class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

cv_status wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time);

template <class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK* A [unique_lock –\<vzájemně vyloučený přístup >](../standard-library/unique-lock-class.md) objektu.

*Abs_time* A [chrono::time_point](../standard-library/time-point-class.md) objektu.

*Před* libovolný výraz, který vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Metody, které vracejí `cv_status` zadejte vrátit `cv_status::timeout` Pokud čekání skončí, když *Abs_time* uplyne. V opačném případě vrátí metody `cv_status::no_timeout`.

Metody, které vracejí **bool** vrácení hodnoty *před*.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud `condition_variable` objekt signalizován voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) , nebo dokud `Abs_time`. To může také probudit falešně.

V důsledku druhá metoda spustí následující kód

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Třetí a čtvrtá metoda použije ukazatel na objekt typu `xtime` nahradit `chrono::time_point` objektu. `xtime` Objekt určuje maximální dobu čekání na signál.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[<condition_variable>](../standard-library/condition-variable.md)<br/>
