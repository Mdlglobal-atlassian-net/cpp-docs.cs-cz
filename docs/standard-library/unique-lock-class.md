---
title: unique_lock – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 59201fbaba6f2e8ae0ed5f53925b287b4d33aab3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367262"
---
# <a name="unique_lock-class"></a>unique_lock – třída

Představuje šablonu, která může být vytvořena instance k vytvoření objektů, `mutex`které spravují zamykání a odemykání .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Poznámky

Argument `Mutex` šablony musí pojmenovat *typ mutex*.

Interně `unique_lock` uloží ukazatel na přidružený `mutex` objekt a **bool,** který označuje, `mutex`zda aktuální vlákno vlastní .

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`mutex_type`|Synonymum pro `Mutex`argument šablony .|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[unique_lock](#unique_lock)|Vytvoří `unique_lock` objekt.|
|[~unique_lock Destruktor](#dtorunique_lock_destructor)|Uvolní všechny prostředky, které `unique_lock` jsou přidruženy k objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Zámek](#lock)|Blokuje volající vlákno, dokud vlákno nezíská `mutex`vlastnictví přidruženého .|
|[Mutex](#mutex)|Načte uložený ukazatel `mutex`na přidružený .|
|[owns_lock](#owns_lock)|Určuje, zda volající vlákno vlastní `mutex`přidružené vlákno .|
|[Vydání](#release)|Odpojí `unique_lock` objekt od přidruženého `mutex` objektu.|
|[Swap](#swap)|Zamění přidružený `mutex` stav a stav vlastnictví za stav zadaného objektu.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví `mutex` přidružené bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat vlastnictví `mutex` přidružené bez blokování.|
|[try_lock_until](#try_lock_until)|Pokusí se získat vlastnictví `mutex` přidružené bez blokování.|
|[Odemknout](#unlock)|Uvolní vlastnictví přidruženého `mutex`.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[operátor bool](#op_bool)|Určuje, zda má volající vlákno `mutex`vlastnictví přidruženého .|
|[operátor =](#op_eq)|Zkopíruje `mutex` uložený ukazatel a přidružený stav vlastnictví z určeného objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

*unique_lock*

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> mutex

**Obor názvů:** std

## <a name="lock"></a><a name="lock"></a>Zámek

Blokuje volající vlákno, dokud vlákno nezíská `mutex`vlastnictví přidruženého .

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud je `mutex` uložený ukazatel NULL, tato metoda vyvolá [system_error,](../standard-library/system-error-class.md) který má kód chyby `operation_not_permitted`.

Pokud volající vlákno již vlastní `mutex`přidružené , tato `system_error` metoda vyvolá, `resource_deadlock_would_occur`který má kód chyby .

Jinak tato metoda `lock` volá `mutex` přidružené a nastaví příznak vlastnictví vnitřní vlákno na **true**.

## <a name="mutex"></a><a name="mutex"></a>Mutex

Načte uložený ukazatel `mutex`na přidružený .

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="operator-bool"></a><a name="op_bool"></a>operátor bool

Určuje, zda volající vlákno má vlastnictví přidruženého objektu mutex.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud vlákno vlastní mutex; jinak **false**.

## <a name="operator"></a><a name="op_eq"></a>operátor =

Zkopíruje `mutex` uložený ukazatel a přidružený stav vlastnictví z určeného objektu.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další*\
Objekt. `unique_lock`

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Pokud volající vlákno vlastní dříve `mutex`přidružené , `unlock` před `mutex`touto metodou volá na , přiřadí nové hodnoty.

Po kopii tato metoda nastaví *Other* do výchozího konstruovaného stavu.

## <a name="owns_lock"></a><a name="owns_lock"></a>owns_lock

Určuje, zda volající vlákno vlastní `mutex`přidružené vlákno .

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud vlákno `mutex`vlastní ; jinak **false**.

## <a name="release"></a><a name="release"></a>Vydání

Odpojí `unique_lock` objekt od přidruženého `mutex` objektu.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota uloženého `mutex` ukazatele.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví hodnotu uloženého `mutex` ukazatele `mutex` na hodnotu 0 a nastaví příznak vnitřního vlastnictví na **hodnotu false**.

## <a name="swap"></a><a name="swap"></a>Swap

Zamění přidružený `mutex` stav a stav vlastnictví za stav zadaného objektu.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Další*\
Objekt. `unique_lock`

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Pokusí se získat vlastnictví `mutex` přidružené bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud metoda úspěšně získá `mutex`vlastnictví ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud je `mutex` uložený ukazatel NULL, metoda vyvolá [system_error,](../standard-library/system-error-class.md) `operation_not_permitted`který má kód chyby .

Pokud volající vlákno již `mutex`vlastní , metoda `system_error` vyvolá, který má `resource_deadlock_would_occur`kód chyby .

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Pokusí se získat vlastnictví `mutex` přidružené bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
[Chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální dobu, po kterou se metoda `mutex`pokusí získat vlastnictví .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud metoda úspěšně získá `mutex`vlastnictví ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud je `mutex` uložený ukazatel NULL, metoda vyvolá [system_error,](../standard-library/system-error-class.md) `operation_not_permitted`který má kód chyby .

Pokud volající vlákno již `mutex`vlastní , metoda `system_error` vyvolá, který má `resource_deadlock_would_occur`kód chyby .

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

Pokusí se získat vlastnictví `mutex` přidružené bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Bod v čase, který určuje prahovou hodnotu, po které `mutex`se metoda již nepokouší získat vlastnictví .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud metoda úspěšně získá `mutex`vlastnictví ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud je `mutex` uložený ukazatel NULL, metoda vyvolá [system_error,](../standard-library/system-error-class.md) `operation_not_permitted`který má kód chyby .

Pokud volající vlákno již `mutex`vlastní , metoda `system_error` vyvolá, který má `resource_deadlock_would_occur`kód chyby .

## <a name="unique_lock-constructor"></a><a name="unique_lock"></a>konstruktor unique_lock

Vytvoří `unique_lock` objekt.

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>Parametry

*Mtx*\
Objekt typu mutex.

*Rel_time*\
[Chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální dobu, po kterou se metoda `mutex`pokusí získat vlastnictví .

*Abs_time*\
Bod v čase, který určuje prahovou hodnotu, po které `mutex`se metoda již nepokouší získat vlastnictví .

*Další*\
Objekt. `unique_lock`

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, který má přidruženou hodnotu ukazatele mutex 0.

Druhý konstruktor přesune přidružený stav mutex z *jiného*. Po přesunutí *Other* již není spojena s mutex.

Zbývající konstruktory ukládají & *Mtx* jako uložený `mutex` ukazatel. Vlastnictví `mutex` je určena druhý argument, pokud existuje.

|||
|-|-|
|`No argument`|Vlastnictví je získán `lock` voláním metody `mutex` na přidružený objekt.|
|`Adopt`|Předpokládá se vlastnictví. `Mtx`musí být uzamčen, když je volán konstruktor.|
|`Defer`|Volající vlákno se předpokládá, `mutex` že není vlastní objekt. `Mtx`nesmí být uzamčen, když je volán konstruktor.|
|`Try`|Vlastnictví je určeno `try_lock` voláním `mutex` přidruženého objektu. Konstruktor nehází nic.|
|`Rel_time`|Vlastnictví je určeno `try_lock_for(Rel_time)`voláním .|
|`Abs_time`|Vlastnictví je určeno `try_lock_until(Abs_time)`voláním .|

## <a name="unique_lock-destructor"></a><a name="dtorunique_lock_destructor"></a>~unique_lock Destruktor

Uvolní všechny prostředky, které `unique_lock` jsou přidruženy k objektu.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno vlastní `mutex`přidružené , destruktor uvolní vlastnictví `mutex` voláním odemknout na objektu.

## <a name="unlock"></a><a name="unlock"></a>Odemknout

Uvolní vlastnictví přidruženého `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno nevlastní přidružené `mutex`, tato metoda vyvolá [system_error,](../standard-library/system-error-class.md) který `operation_not_permitted`má kód chyby .

Jinak tato metoda `unlock` volá `mutex` přidružené a nastaví příznak vlastnictví vnitřní vlákno na **false**.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
