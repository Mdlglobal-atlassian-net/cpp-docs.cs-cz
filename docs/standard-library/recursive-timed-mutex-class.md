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
ms.openlocfilehash: 93ce7b99728d1ce89c8124efd6c74aea7ff66d22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320137"
---
# <a name="recursive_timed_mutex-class"></a>recursive_timed_mutex – třída

Představuje *časovaný typ mutex*. Objekty tohoto typu se používají k vynucení vzájemnévyloučení pomocí časově omezené blokování v rámci programu. Na rozdíl od objektů typu [timed_mutex](../standard-library/timed-mutex-class.md)je `recursive_timed_mutex` efekt volání metod uzamčení objektů dobře definován.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Vytvoří `recursive_timed_mutex` objekt, který není uzamčen.|
|[~recursive_timed_mutex Destruktor](#dtorrecursive_timed_mutex_destructor)|Uvolní všechny prostředky, které `recursive_timed_mutex` jsou používány objektem.|

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

## <a name="lock"></a><a name="lock"></a>Zámek

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`rozhraní .

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , metoda se vrátí okamžitě a předchozí zámek zůstane v platnosti.

## <a name="recursive_timed_mutex-constructor"></a><a name="recursive_timed_mutex"></a>konstruktor recursive_timed_mutex

Vytvoří `recursive_timed_mutex` objekt, který není uzamčen.

```cpp
recursive_timed_mutex();
```

## <a name="recursive_timed_mutex-destructor"></a><a name="dtorrecursive_timed_mutex_destructor"></a>~recursive_timed_mutex Destruktor

Uvolní všechny prostředky, které `recursive_timed_mutex` jsou používány objektem.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, chování není definováno.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**true** pokud metoda úspěšně získala `mutex` vlastnictví nebo pokud volající vlákno `mutex`již vlastní ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , funkce okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="try_lock_for"></a><a name="try_lock_for"></a>try_lock_for

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
[Chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální dobu, po kterou se metoda `mutex`pokusí získat vlastnictví .

### <a name="return-value"></a>Návratová hodnota

**true** pokud metoda úspěšně získá vlastnictví `mutex` nebo pokud volající vlákno `mutex`již vlastní ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , metoda okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="try_lock_until"></a><a name="try_lock_until"></a>try_lock_until

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

**true** pokud metoda úspěšně získá vlastnictví `mutex` nebo pokud volající vlákno `mutex`již vlastní ; jinak **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již `mutex`vlastní , metoda okamžitě vrátí **hodnotu true**a předchozí zámek zůstane v platnosti.

## <a name="unlock"></a><a name="unlock"></a>Odemknout

Uvolní vlastnictví . `mutex`

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda uvolní vlastnictví `mutex` pouze poté, co je volána tolikrát jako [zámek](#lock), [try_lock](#try_lock) `recursive_timed_mutex` , [try_lock_for](#try_lock_for)a [try_lock_until](#try_lock_until) byly úspěšně volány na objektu.

Pokud volající vlákno nevlastní `mutex`, chování není definováno.

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<>mutex](../standard-library/mutex.md)
