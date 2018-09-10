---
title: condition_variable_any – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
dev_langs:
- C++
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: 9acd5abc941c3cc3ab2f1c22486298d7cc7da16c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106961"
---
# <a name="conditionvariableany-class"></a>condition_variable_any – třída

Použití třídy `condition_variable_any` k čekání na událost, která má libovolný `mutex` typu.

## <a name="syntax"></a>Syntaxe

```cpp
class condition_variable_any;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[condition_variable_any –](#condition_variable_any)|Vytvoří `condition_variable_any` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[notify_all](#notify_all)|Odblokuje všechna vlákna, která čekají `condition_variable_any` objektu.|
|[notify_one](#notify_one)|Odblokuje jedno z vláken, která čekají `condition_variable_any` objektu.|
|[Počkej](#wait)|Blokuje vlákno.|
|[wait_for](#wait_for)|Blokuje vlákno a nastavuje časový interval, po jejímž uplynutí se vlákno odblokuje.|
|[wait_until](#wait_until)|Blokuje vlákno a nastavuje maximální bod v čase, kdy se vlákno odblokuje.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<condition_variable >

**Namespace:** std

## <a name="condition_variable_any"></a>  condition_variable_any::condition_variable_any – konstruktor

Vytvoří `condition_variable_any` objektu.

```cpp
condition_variable_any();
```

### <a name="remarks"></a>Poznámky

Pokud není k dispozici není dostatek paměti, vyvolá konstruktor [system_error](../standard-library/system-error-class.md) objekt, který má `not_enough_memory` kód chyby. Pokud objekt nelze vytvořit, protože jiný prostředek není k dispozici, vyvolá konstruktor `system_error` objekt, který má `resource_unavailable_try_again` kód chyby.

## <a name="notify_all"></a>  condition_variable_any::notify_all –

Odblokuje všechna vlákna, která čekají `condition_variable_any` objektu.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable_any::notify_one –

Odblokuje jedno z vláken, která čekají na `condition_variable_any` objektu.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>  condition_variable_any::wait –

Blokuje vlákno.

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*<br/>
A `mutex` objekt jakéhokoli typu.

*Před*<br/>
Libovolný výraz, který vrátí **true** nebo **false**.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud `condition_variable_any` objekt signalizován voláním [notify_one](../standard-library/condition-variable-class.md#notify_one) nebo [notify_all](../standard-library/condition-variable-class.md#notify_all). To může také probudit falešně.

V důsledku druhá metoda spustí následující kód.

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable_any::wait_for –

Blokuje vlákno a nastavuje časový interval, po jejímž uplynutí se vlákno odblokuje.

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*<br/>
A `mutex` objekt jakéhokoli typu.

*Rel_time*<br/>
A `chrono::duration` probudí objekt, který určuje dobu před vlákna.

*Před*<br/>
Libovolný výraz, který vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `cv_status::timeout` Pokud čekání skončí, když *Rel_time* uplynul. V opačném případě vrátí metoda `cv_status::no_timeout`.

Druhá metoda vrátí hodnotu *před*.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud `condition_variable_any` objekt signalizován voláním [notify_one](../standard-library/condition-variable-class.md#notify_one) nebo [notify_all](../standard-library/condition-variable-class.md#notify_all), nebo dokud časový interval *Rel_time* uplynul. To může také probudit falešně.

V důsledku druhá metoda spustí následující kód.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable_any::wait_until –

Blokuje vlákno a nastavuje maximální bod v čase, kdy se vlákno odblokuje.

```cpp
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*<br/>
Objekt mutex.

*Abs_time*<br/>
A [chrono::time_point](../standard-library/time-point-class.md) objektu.

*Před*<br/>
Libovolný výraz, který vrátí **true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Metody, které vracejí `cv_status` zadejte vrátit `cv_status::timeout` Pokud čekání skončí, když *Abs_time* uplyne. V opačném případě vrátí metody `cv_status::no_timeout`.

Metody, které vracejí `bool` vrácení hodnoty *před*.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud `condition_variable` objekt signalizován voláním [notify_one](../standard-library/condition-variable-class.md#notify_one) nebo [notify_all](../standard-library/condition-variable-class.md#notify_all), nebo dokud *Abs_time*. To může také probudit falešně.

V důsledku druhá metoda spustí následující kód.

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
