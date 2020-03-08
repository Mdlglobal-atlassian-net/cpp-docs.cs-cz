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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78872412"
---
# <a name="condition_variable-class"></a>condition_variable – třída

Použijte třídu `condition_variable` pro čekání na událost, pokud máte `mutex` typu `unique_lock<mutex>`. Objekty tohoto typu mohou mít lepší výkon než objekty typu [condition_variable_any < unique_lock\<mutex > >](../standard-library/condition-variable-any-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
class condition_variable;
```

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[condition_variable](#condition_variable)|Vytvoří objekt `condition_variable`.|

### <a name="functions"></a>Functions

|||
|-|-|
|[native_handle](#native_handle)|Vrátí typ specifický pro implementaci představující popisovač condition_variable.|
|[notify_all](#notify_all)|Odblokuje všechna vlákna, která čekají na objekt `condition_variable`.|
|[notify_one](#notify_one)|Odblokuje jedno z vláken, která čekají na objekt `condition_variable`.|
|[Počkej](#wait)|Blokuje vlákno.|
|[wait_for](#wait_for)|Blokuje vlákno a nastavuje časový interval, po kterém se vlákno odblokuje.|
|[wait_until](#wait_until)|Blokuje vlákno a nastavuje maximální bod v čase, kdy se vlákno odblokuje.|

## <a name="condition_variable"></a>condition_variable

Vytvoří objekt `condition_variable`.

```cpp
condition_variable();
```

### <a name="remarks"></a>Poznámky

Není-li k dispozici dostatek paměti, vyvolá konstruktor objekt [system_error](../standard-library/system-error-class.md) , který obsahuje kód chyby `not_enough_memory`. Pokud objekt nelze sestavit, protože nějaký jiný prostředek není k dispozici, vyvolá konstruktor objekt `system_error`, který obsahuje kód chyby `resource_unavailable_try_again`.

## <a name="native_handle"></a>native_handle

Vrátí typ specifický pro implementaci, který představuje popisovač condition_variable.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Návratová hodnota

`native_handle_type` je definován jako ukazatel pro Concurrency Runtime vnitřních datových struktur.

## <a name="notify_all"></a>notify_all

Odblokuje všechna vlákna, která čekají na objekt `condition_variable`.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>notify_one

Odblokuje jedno z vláken, která čekají na objekt `condition_variable`.

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
Objekt [> mutex unique_lock\<](../standard-library/unique-lock-class.md) .

*Před*\
Libovolný výraz, který vrací **hodnotu true** nebo **false**.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud není objekt `condition_variable` signalizována voláním [notify_one](#notify_one) nebo [notify_all](#notify_all). Může také probudit falešně.

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
Objekt [> mutex unique_lock\<](../standard-library/unique-lock-class.md) .

*Rel_time*\
Objekt `chrono::duration`, který určuje, jak dlouho se má vlákno probudit.

*Před*\
Libovolný výraz, který vrací **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

První metoda vrátí `cv_status::timeout`, pokud čekání skončí, když *Rel_time* uplynul. V opačném případě metoda vrátí `cv_status::no_timeout`.

Druhá metoda vrátí hodnotu *před*.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud není objekt `condition_variable` signalizována voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) nebo dokud neuplynul časový interval *Rel_time* . Může také probudit falešně.

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
Objekt [> mutex unique_lock\<](../standard-library/unique-lock-class.md) .

*Abs_time*\
Objekt [chrono:: time_point](../standard-library/time-point-class.md) .

*Před*\
Libovolný výraz, který vrací **hodnotu true** nebo **false**.

### <a name="return-value"></a>Návratová hodnota

Metody, které vracejí typ `cv_status` vrátí `cv_status::timeout`, pokud čekání skončí, když *Abs_time* uplynuly. V opačném případě metody vrací `cv_status::no_timeout`.

Metody, které vracejí **bool** , vrátí hodnotu *před*.

### <a name="remarks"></a>Poznámky

První metoda blokuje, dokud není objekt `condition_variable` signalizována voláním [notify_one](#notify_one) nebo [notify_all](#notify_all) nebo dokud `Abs_time`. Může také probudit falešně.

V důsledku druhá metoda spustí následující kód

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Třetí a čtvrté metody používají ukazatel na objekt typu `xtime` k nahrazení objektu `chrono::time_point`. Objekt `xtime` určuje maximální dobu, po kterou se má čekat na signál.

## <a name="see-also"></a>Viz také

\ [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[<condition_variable>](../standard-library/condition-variable.md)
