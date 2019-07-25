---
title: recursive_timed_mutex – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.openlocfilehash: 6ae61d17084cc744cac8819ac2c0ca48eb59add7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460117"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex – třída

Představuje *typ*nečasovaného mutexu. Objekty tohoto typu slouží k prosazování vzájemného vyloučení pomocí blokování omezeného časem v rámci programu. Na rozdíl od objektů typu [timed_mutex](../standard-library/timed-mutex-class.md)je efekt volání metod zamykání pro `recursive_timed_mutex` objekty dobře definován.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|`recursive_timed_mutex` Vytvoří objekt, který není uzamčen.|
|[~recursive_timed_mutex Destructor](#dtorrecursive_timed_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `recursive_timed_mutex` objektem.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví `mutex` bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat vlastnictví `mutex` pro zadaný časový interval.|
|[try_lock_until](#try_lock_until)|Pokusí se získat vlastnictví `mutex` do určeného času.|
|[Uzamknout](#unlock)|Uvolňuje vlastnictví `mutex`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> mutex

**Obor názvů:** std

## <a name="lock"></a>získáte

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, metoda se vrátí okamžitě a předchozí zámek zůstane v platnosti.

## <a name="recursive_timed_mutex"></a>Konstruktor recursive_timed_mutex

`recursive_timed_mutex` Vytvoří objekt, který není uzamčen.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>~ recursive_timed_mutex destruktor

Uvolní všechny prostředky, které jsou používány `recursive_timed_mutex` objektem.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="try_lock"></a>try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získala vlastnictví `mutex` nebo v případě, že `mutex`volající vlákno již vlastní; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, funkce okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="try_lock_for"></a>try_lock_for

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [chrono::d uration](../standard-library/duration-class.md) , který určuje maximální dobu, po kterou se metoda pokusí získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex` nebo v případě, že volající `mutex`vlákno již vlastní; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, metoda okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="try_lock_until"></a>try_lock_until

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Bod v čase, který určuje prahovou hodnotu, po jejímž uplynutí se metoda již nepokouší získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex` nebo v případě, že volající `mutex`vlákno již vlastní; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, metoda okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="unlock"></a>Uzamknout

Uvolňuje vlastnictví `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda `mutex` uvolní vlastnictví pouze poté, co je volána, kolikrát bylo volání metody [Lock](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for) `recursive_timed_mutex` a [try_lock_until](#try_lock_until) v objektu úspěšné.

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
