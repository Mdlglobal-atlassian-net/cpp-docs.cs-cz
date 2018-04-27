---
title: condition_variable – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
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
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
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
ms.openlocfilehash: 316c3d68506a206ebcf91d63fcad0c359019300c
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="conditionvariable-class"></a>condition_variable – třída

Použití `condition_variable` třída pro čekání na událost, když máte `mutex` typu `unique_lock<mutex>`. Objekty tohoto typu mohou mít lepší výkon než objekty typu [condition_variable_any < unique_lock\<mutex >>](../standard-library/condition-variable-any-class.md).

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
|[native_handle –](#native_handle)|Vrátí typ závisí na implementaci představující condition_variable popisovač.|
|[notify_all](#notify_all)|Odblokuje všechna vlákna, která čekají `condition_variable` objektu.|
|[notify_one](#notify_one)|Odblokuje jeden vláken, která čekají `condition_variable` objektu.|
|[Počkej](#wait)|Blokuje vlákno.|
|[wait_for](#wait_for)|Blokuje vlákno a nastaví časový interval, po jejímž uplynutí odblokuje vlákno.|
|[wait_until](#wait_until)|Blokuje vlákno a nastaví maximální bodu v čase, kdy odblokuje vlákno.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<condition_variable >

**Namespace:** – std

## <a name="condition_variable"></a>  condition_variable::condition_variable – konstruktor

Vytvoří `condition_variable` objektu.

```cpp
condition_variable();
```

### <a name="remarks"></a>Poznámky

Pokud je k dispozici není dostatek paměti, vyvolá konstruktoru [system_error –](../standard-library/system-error-class.md) objekt, který má `not_enough_memory` kód chyby. Pokud objekt nelze vytvořit, protože jiný prostředek není k dispozici, vyvolá konstruktoru `system_error` objekt, který má `resource_unavailable_try_again` kód chyby.

## <a name="native_handle"></a>  condition_variable::native_handle –

Vrátí typ konkrétní implementace, který představuje popisovač condition_variable.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type` je definován jako ukazatel na interních datových strukturách Concurrency Runtime.

## <a name="notify_all"></a>  condition_variable::notify_all –

Odblokuje všechna vlákna, která čekají `condition_variable` objektu.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable::notify_one –

Jeden z vláken, která čekají na odblokuje `condition_variable` objektu.

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

`Lck` A [unique_lock\<mutex >](../standard-library/unique-lock-class.md) objektu.

`Pred` Jakýkoli výraz, který vrací `true` nebo `false`.

### <a name="remarks"></a>Poznámky

První metoda blokuje až `condition_variable` objekt signalizace voláním [notify_one](#notify_one) nebo [notify_all](#notify_all). Ho můžete také probuzení spuriously.

Druhá metoda platit, provede následující kód.

```cpp
while(!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable::wait_for –

Blokuje vlákno a nastaví časový interval, po jejímž uplynutí odblokuje vlákno.

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

`Lck` A [unique_lock\<mutex >](../standard-library/unique-lock-class.md) objektu.

`Rel_time` A `chrono::duration` probudí objekt, který určuje množství času, než vlákno.

`Pred` Jakýkoli výraz, který vrací `true` nebo `false`.

### <a name="return-value"></a>Návratová hodnota

Vrátí první metoda `cv_status::timeout` Pokud ukončí dobu, kdy `Rel_time` uplynul. Jinak, vrátí metoda `cv_status::no_timeout`.

Druhá metoda vrátí hodnotu `Pred`.

### <a name="remarks"></a>Poznámky

První metoda blokuje až `condition_variable` objekt signalizace voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) , nebo dokud se časový interval `Rel_time` uplynul. Ho můžete také probuzení spuriously.

Druhá metoda platit, provede následující kód.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable::wait_until –

Blokuje vlákno a nastaví maximální bodu v čase, kdy odblokuje vlákno.

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

`Lck` A [unique_lock\<mutex >](../standard-library/unique-lock-class.md) objektu.

`Abs_time` A [chrono::time_point](../standard-library/time-point-class.md) objektu.

`Pred` Jakýkoli výraz, který vrací `true` nebo `false`.

### <a name="return-value"></a>Návratová hodnota

Metody, které vracejí `cv_status` návratový typ `cv_status::timeout` Pokud ukončí dobu, kdy `Abs_time` uplynutí. Jinak vrátí metody `cv_status::no_timeout`.

Metody, které vracejí `bool` vrátí hodnotu `Pred`.

### <a name="remarks"></a>Poznámky

První metoda blokuje až `condition_variable` objekt signalizace voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) nebo dokud `Abs_time`. Ho můžete také probuzení spuriously.

Ve skutečnosti druhý metoda spustí následující kód

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Metody třetí a čtvrtý použití ukazatel na objekt typu `xtime` nahradit `chrono::time_point` objektu. `xtime` Objektu určuje maximální množství času čekání na signál.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[<condition_variable>](../standard-library/condition-variable.md)<br/>
