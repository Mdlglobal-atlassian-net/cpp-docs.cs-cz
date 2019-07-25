---
title: timed_mutex – třída
ms.date: 11/04/2016
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.openlocfilehash: 6b9785dc41791be63d585d18802953eade370b2a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459926"
---
# <a name="timedmutex-class"></a>timed_mutex – třída

Představuje *typ*nečasovaného mutexu. Objekty tohoto typu slouží k prosazování vzájemného vyloučení prostřednictvím blokování omezeného časem v rámci programu.

## <a name="syntax"></a>Syntaxe

```cpp
class timed_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|`timed_mutex` Vytvoří objekt, který není uzamčen.|
|[timed_mutex::~timed_mutex Destructor](#dtortimed_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `timed_mutex` objektem.|

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

## <a name="lock"></a>timed_mutex:: Lock

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, chování není definováno.

## <a name="timed_mutex"></a>timed_mutex:: timed_mutex – konstruktor

`timed_mutex` Vytvoří objekt, který není uzamčen.

```cpp
timed_mutex();
```

## <a name="dtortimed_mutex_destructor"></a>timed_mutex:: ~ timed_mutex – destruktor

Uvolní všechny prostředky, které jsou používány `mutex` objektem.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="try_lock"></a>timed_mutex::try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex`, v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, chování není definováno.

## <a name="try_lock_for"></a>timed_mutex::try_lock_for

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [chrono::d uration](../standard-library/duration-class.md) , který určuje maximální dobu, po kterou se metoda pokusí získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud metoda úspěšně získá vlastnictví `mutex`, v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, chování není definováno.

## <a name="try_lock_until"></a>timed_mutex::try_lock_until

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

**true** , pokud metoda úspěšně získá vlastnictví `mutex`, v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, chování není definováno.

## <a name="unlock"></a>timed_mutex:: Unlock

Uvolňuje vlastnictví `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
