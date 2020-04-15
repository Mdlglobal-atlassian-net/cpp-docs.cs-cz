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
ms.openlocfilehash: 6c9840d9b8c00d4b03e6ea329c7707a0edff9512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368021"
---
# <a name="timed_mutex-class"></a>timed_mutex – třída

Představuje *časovaný typ mutex*. Objekty tohoto typu se používají k vynucení vzájemného vyloučení prostřednictvím časově omezeného blokování v rámci programu.

## <a name="syntax"></a>Syntaxe

```cpp
class timed_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Vytvoří `timed_mutex` objekt, který není uzamčen.|
|[timed_mutex::~timed_mutex Destruktor](#dtortimed_mutex_destructor)|Uvolní všechny prostředky, které `timed_mutex` jsou používány objektem.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Zámek](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`rozhraní .|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví `mutex` bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat vlastnictví `mutex` pro zadaný časový interval.|
|[try_lock_until](#try_lock_until)|Pokusí se získat vlastnictví `mutex` až do zadaného času.|
|[Odemknout](#unlock)|Uvolní vlastnictví . `mutex`|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> mutex

**Obor názvů:** std

## <a name="timed_mutexlock"></a><a name="lock"></a>timed_mutex::zámek

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`rozhraní .

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , chování není definováno.

## <a name="timed_mutextimed_mutex-constructor"></a><a name="timed_mutex"></a>timed_mutex::timed_mutex konstruktor

Vytvoří `timed_mutex` objekt, který není uzamčen.

```cpp
timed_mutex();
```

## <a name="timed_mutextimed_mutex-destructor"></a><a name="dtortimed_mutex_destructor"></a>timed_mutex::~timed_mutex Destruktor

Uvolní všechny prostředky, které `mutex` jsou používány objektem.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="timed_mutextry_lock"></a><a name="try_lock"></a>timed_mutex::try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud metoda úspěšně získá `mutex`vlastnictví ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , chování není definováno.

## <a name="timed_mutextry_lock_for"></a><a name="try_lock_for"></a>timed_mutex::try_lock_for

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
[Chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální dobu, po kterou se metoda `mutex`pokusí získat vlastnictví .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud metoda úspěšně získá `mutex`vlastnictví ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , chování není definováno.

## <a name="timed_mutextry_lock_until"></a><a name="try_lock_until"></a>timed_mutex::try_lock_until

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Bod v čase, který určuje prahovou hodnotu, po které `mutex`se metoda již nepokouší získat vlastnictví .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud metoda úspěšně získá `mutex`vlastnictví ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , chování není definováno.

## <a name="timed_mutexunlock"></a><a name="unlock"></a>timed_mutex::odemknutí

Uvolní vlastnictví . `mutex`

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
