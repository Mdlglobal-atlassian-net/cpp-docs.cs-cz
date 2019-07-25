---
title: unique_lock – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 655d7b08c452bed94277aaed2cc8368aaeb462c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454933"
---
# <a name="uniquelock-class"></a>unique_lock – třída

Představuje šablonu, která může být vytvořena pro vytváření objektů, které spravují uzamykání a odemykání `mutex`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Poznámky

Argument `Mutex` šablony musí pojmenovat *typ mutex*.

Interně `mutex` `mutex`ukládá ukazatel na přidružený objekt a logickou hodnotu, která označuje, zda aktuální vlákno vlastní.  `unique_lock`

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|`mutex_type`|Synonymum pro argument `Mutex`šablony|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[unique_lock](#unique_lock)|`unique_lock` Vytvoří objekt.|
|[~unique_lock Destructor](#dtorunique_lock_destructor)|Uvolní všechny prostředky, které jsou přidruženy `unique_lock` k objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví přidruženého `mutex`.|
|[objekt](#mutex)|Načte uložený ukazatel na přidruženou `mutex`.|
|[owns_lock](#owns_lock)|Určuje, zda volající vlákno vlastní přidruženo `mutex`.|
|[předběžné](#release)|Zruší přidružení `unique_lock` objektu k přidruženému `mutex` objektu.|
|[swap](#swap)|Zamění stav přidruženo `mutex` a vlastnictví zadaným objektem.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.|
|[try_lock_until](#try_lock_until)|Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.|
|[Uzamknout](#unlock)|Uvolní vlastnictví přidruženého `mutex`.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[operátor bool](#op_bool)|Určuje, zda má volající vlákno vlastnictví přidruženého `mutex`.|
|[operátor =](#op_eq)|Zkopíruje uložený `mutex` ukazatel a přidružený stav vlastnictví ze zadaného objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

*unique_lock*

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> mutex

**Obor názvů:** std

## <a name="lock"></a>získáte

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví přidruženého `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud je uložený `mutex` ukazatel null, tato metoda vyvolá [system_error](../standard-library/system-error-class.md) , který má kód `operation_not_permitted`chyby.

Pokud volající vlákno již vlastní `mutex`, tato metoda `system_error` vyvolá chybu s kódem `resource_deadlock_would_occur`.

V opačném případě tato `lock` metoda volá přidruženou `mutex` a nastaví příznak interního vlastnictví vlákna na **hodnotu true**.

## <a name="mutex"></a>objekt

Načte uložený ukazatel na přidruženou `mutex`.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>operátor bool

Určuje, zda má volající vlákno vlastnictví přidruženého objektu mutex.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud vlákno vlastní mutex; v opačném případě **false**.

## <a name="op_eq"></a>operátor =

Zkopíruje uložený `mutex` ukazatel a přidružený stav vlastnictví ze zadaného objektu.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
A `unique_lock` objektu.

### <a name="return-value"></a>Návratová hodnota

`*this`

### <a name="remarks"></a>Poznámky

Pokud volající vlákno vlastní dříve přidružené `mutex`, před tím, než tato metoda zavolá `mutex` `unlock` , přiřadí nové hodnoty.

Po kopírování Tato metoda nastaví *jiné* na výchozí stav sestaven.

## <a name="owns_lock"></a>owns_lock

Určuje, zda volající vlákno vlastní přidruženo `mutex`.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud vlákno vlastní `mutex`; v opačném případě **false**.

## <a name="release"></a>předběžné

Zruší přidružení `unique_lock` objektu k přidruženému `mutex` objektu.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Předchozí hodnota uloženého `mutex` ukazatele.

### <a name="remarks"></a>Poznámky

Tato metoda nastaví hodnotu uloženého `mutex` ukazatele na 0 a nastaví příznak interního `mutex` vlastnictví na **hodnotu false**.

## <a name="swap"></a>adresu

Zamění stav přidruženo `mutex` a vlastnictví zadaným objektem.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Jiná*\
A `unique_lock` objektu.

## <a name="try_lock"></a>try_lock

Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex`, v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud je uložený `mutex` ukazatel null, vyvolá metoda [system_error](../standard-library/system-error-class.md) s kódem `operation_not_permitted`chyby.

Pokud volající vlákno již vlastní `mutex`, metoda `system_error` vyvolá výjimku, která `resource_deadlock_would_occur`má kód chyby.

## <a name="try_lock_for"></a>try_lock_for

Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [chrono::d uration](../standard-library/duration-class.md) , který určuje maximální dobu, po kterou se metoda pokusí získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex`, v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud je uložený `mutex` ukazatel null, vyvolá metoda [system_error](../standard-library/system-error-class.md) s kódem `operation_not_permitted`chyby.

Pokud volající vlákno již vlastní `mutex`, metoda `system_error` vyvolá výjimku, která `resource_deadlock_would_occur`má kód chyby.

## <a name="try_lock_until"></a>try_lock_until

Pokusí se získat vlastnictví přidruženého `mutex` bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Bod v čase, který určuje prahovou hodnotu, po jejímž uplynutí se metoda již nepokouší získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex`, v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud je uložený `mutex` ukazatel null, vyvolá metoda [system_error](../standard-library/system-error-class.md) s kódem `operation_not_permitted`chyby.

Pokud volající vlákno již vlastní `mutex`, metoda `system_error` vyvolá výjimku, která `resource_deadlock_would_occur`má kód chyby.

## <a name="unique_lock"></a>Konstruktor unique_lock

`unique_lock` Vytvoří objekt.

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

*MTX*\
Objekt typu mutex.

*Rel_time*\
Objekt [chrono::d uration](../standard-library/duration-class.md) , který určuje maximální dobu, po kterou se metoda pokusí získat vlastnictví `mutex`.

*Abs_time*\
Bod v čase, který určuje prahovou hodnotu, po jejímž uplynutí se metoda již nepokouší získat vlastnictví `mutex`.

*Jiná*\
A `unique_lock` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, který má přidruženou hodnotu ukazatele mutex 0.

Druhý konstruktor přesune přidružený stav objektu mutex z *jiné*. Po přesunutí už *jiný* není přidružený k objektu mutex.

Zbývající konstruktory se ukládají & *MTX* jako uložený `mutex` ukazatel. `mutex` Vlastnictví je určeno druhým argumentem, pokud existuje.

|||
|-|-|
|`No argument`|Vlastnictví je získáno voláním `lock` metody u přidruženého `mutex` objektu.|
|`Adopt`|Předpokládá se vlastnictví. `Mtx`musí být uzamčen při volání konstruktoru.|
|`Defer`|Volající vlákno se předpokládá, že nevlastní `mutex` objekt. `Mtx`nesmí být uzamčen při volání konstruktoru.|
|`Try`|Vlastnictví je určeno voláním `try_lock` na přidružený `mutex` objekt. Konstruktor nevyvolává nic.|
|`Rel_time`|Vlastnictví je určeno voláním `try_lock_for(Rel_time)`.|
|`Abs_time`|Vlastnictví je určeno voláním `try_lock_until(Abs_time)`.|

## <a name="dtorunique_lock_destructor"></a>~ unique_lock destruktor

Uvolní všechny prostředky, které jsou přidruženy `unique_lock` k objektu.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno vlastní přidruženo `mutex`, destruktor uvolní vlastnictví voláním Unlock `mutex` u objektu.

## <a name="unlock"></a>Uzamknout

Uvolní vlastnictví přidruženého `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno nevlastní přidruženo `mutex`, tato metoda vyvolá [system_error](../standard-library/system-error-class.md) , který má kód `operation_not_permitted`chyby.

V opačném případě tato `unlock` metoda volá přidruženou `mutex` a nastaví příznak interního vlastnictví vlákna na **hodnotu false**.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
