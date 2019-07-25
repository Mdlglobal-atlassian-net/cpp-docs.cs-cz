---
title: condition_variable – třída
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition
- condition_variable/std::condition_variable::condition_variable
- condition_variable/std::condition_variable::native_handle
- condition_variable/std::condition_variable::notify_all
- condition_variable/std::condition_variable::notify_one
- condition_variable/std::condition_variable::wait
- condition_variable/std::condition_variable::wait_for
- condition_variable/std::condition_variable::wait_until
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
helpviewer_keywords:
- std::condition
- std::condition_variable::condition_variable
- std::condition_variable::native_handle
- std::condition_variable::notify_all
- std::condition_variable::notify_one
- std::condition_variable::wait
- std::condition_variable::wait_for
- std::condition_variable::wait_until
ms.openlocfilehash: 999e236433ec4f3f2f52abb06855004a89169fa6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449450"
---
# <a name="conditionvariable-class"></a>condition_variable – třída

Použijte třídu pro čekání na událost, pokud `mutex` máte typ `unique_lock<mutex>`. `condition_variable` Objekty tohoto typu mohou mít lepší výkon než objekty typu [condition_variable_any < unique_lock\<mutex > >](../standard-library/condition-variable-any-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class condition_variable;
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[condition_variable](#condition_variable)|`condition_variable` Vytvoří objekt.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[native_handle](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač condition_variable.|
|[notify_all](#notify_all)|Odblokuje všechna vlákna, která čekají `condition_variable` na objekt.|
|[notify_one](#notify_one)|Odblokuje jedno z vláken, která čekají `condition_variable` na objekt.|
|[Počkej](#wait)|Blokuje vlákno.|
|[wait_for](#wait_for)|Blokuje vlákno a nastavuje časový interval, po kterém se vlákno odblokuje.|
|[wait_until](#wait_until)|Blokuje vlákno a nastavuje maximální bod v čase, kdy se vlákno odblokuje.|

## <a name="condition_variable"></a>condition_variable

`condition_variable` Vytvoří objekt.

```cpp
condition_variable();
```

### <a name="remarks"></a>Poznámky

Není-li k dispozici dostatek paměti, vyvolá konstruktor objekt [system_error](../standard-library/system-error-class.md) , který obsahuje `not_enough_memory` kód chyby. Pokud objekt nelze sestavit, protože nějaký jiný prostředek není k dispozici, konstruktor vyvolá `system_error` objekt, který `resource_unavailable_try_again` má kód chyby.

## <a name="native_handle"></a>native_handle

Vrátí typ specifický pro implementaci, který reprezentuje popisovač condition_variable.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type`je definován jako ukazatel Concurrency Runtime vnitřních datových struktur.

## <a name="notify_all"></a>notify_all

Odblokuje všechna vlákna, která čekají `condition_variable` na objekt.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>notify_one

Odblokuje jedno z vláken, která čekají na `condition_variable` objekt.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>Počkej

Blokuje vlákno.

```cpp
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*Lck*\
Objekt [unique_lock\<mutex >](../standard-library/unique-lock-class.md) .

*Čekání*\
Libovolný výraz, který vrací **hodnotu true** nebo **false**.

### <a name="remarks"></a>Poznámky

První metoda blokuje, `condition_variable` dokud není objekt signalizována voláním metody [notify_one](#notify_one) nebo [notify_all](#notify_all). Může také probudit falešně.

V důsledku druhá metoda spustí následující kód.

```cpp
while(!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>wait_for

Blokuje vlákno a nastavuje časový interval, po kterém se vlákno odblokuje.

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

*Lck*\
Objekt [unique_lock\<mutex >](../standard-library/unique-lock-class.md) .

*Rel_time*\
`chrono::duration` Objekt, který určuje dobu, po jejímž uplynutí se vlákno probudí.

*Čekání*\
Libovolný výraz, který vrací **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `cv_status::timeout` , pokud čekání skončí, když *Rel_time* uplynul. V opačném případě se `cv_status::no_timeout`metoda vrátí.

Druhá metoda vrátí hodnotu *před*.

### <a name="remarks"></a>Poznámky

První metoda blokuje, `condition_variable` dokud není objekt signalizována voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) nebo dokud neuplynul časový interval *Rel_time* . Může také probudit falešně.

V důsledku druhá metoda spustí následující kód.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>wait_until

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

*Lck*\
Objekt [unique_lock\<mutex >](../standard-library/unique-lock-class.md) .

*Abs_time*\
Objekt [chrono:: time_point](../standard-library/time-point-class.md) .

*Čekání*\
Libovolný výraz, který vrací **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Metody, které vracejí `cv_status` typ, `cv_status::timeout` vrátí, pokud čekání skončí, když *Abs_time* uplyne. V opačném případě metody `cv_status::no_timeout`vrátí.

Metody, které vracejí **bool** , vrátí hodnotu *před*.

### <a name="remarks"></a>Poznámky

První `condition_variable` metoda blokuje, dokud není objekt signalizována voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) nebo do. `Abs_time` Může také probudit falešně.

V důsledku druhá metoda spustí následující kód

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Třetí a čtvrtá metoda používá ukazatel na objekt typu `xtime` k `chrono::time_point` nahrazení objektu. `xtime` Objekt určuje maximální dobu, po kterou se má čekat na signál.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[<condition_variable>](../standard-library/condition-variable.md)
