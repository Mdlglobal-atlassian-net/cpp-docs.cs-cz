---
title: recursive_timed_mutex – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
dev_langs:
- C++
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: bfabbd938f2258f7e1a75fd77eaac7b2cd23b2b8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957620"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex – třída

Představuje *vypršel časový limit typ mutex*. Objekty tohoto typu se používají k zajištění vzájemného vyloučení pomocí časově omezené blokování v rámci programu. Na rozdíl od objektů typu [timed_mutex –](../standard-library/timed-mutex-class.md), efekt volání pro uzamčení metod `recursive_timed_mutex` objekty je dobře definovaný.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Vytvoří `recursive_timed_mutex` objektu, která není uzamčena.|
|[~recursive_timed_mutex Destructor](#dtorrecursive_timed_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `recursive_timed_mutex` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.|
|[try_lock](#try_lock)|Pokusy o získání vlastnictví `mutex` bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusy o získání vlastnictví `mutex` pro zadaný časový interval.|
|[try_lock_until](#try_lock_until)|Pokusy o získání vlastnictví `mutex` až do zadaného času.|
|[Odemknutí](#unlock)|Uvolní vlastnictví objektu `mutex`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<vzájemně vyloučeného přístupu >

**Namespace:** std

## <a name="lock"></a>  Zámek

Blokuje volající vlákno, dokud vlákno nezíská vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, metoda vrátí hodnotu okamžitě a uzamčení předchozího zůstává v platnosti.

## <a name="recursive_timed_mutex"></a>  recursive_timed_mutex – konstruktor

Vytvoří `recursive_timed_mutex` objektu, která není uzamčena.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>  ~ recursive_timed_mutex – destruktor

Uvolní všechny prostředky, které jsou používány `recursive_timed_mutex` objektu.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud je objekt uzamčen při spuštění destruktoru, není chování definováno.

## <a name="try_lock"></a>  try_lock –

Pokusy o získání vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně získat vlastnictví `mutex` nebo pokud volající vlákno již vlastní `mutex`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, funkce vrátí okamžitě **true**, a uzamčení předchozího zůstává v platnosti.

## <a name="try_lock_for"></a>  try_lock_for –

Pokusy o získání vlastnictví `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time* A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální množství času, která metoda se pokusí získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně nezíská vlastnictví `mutex` nebo pokud volající vlákno již vlastní `mutex`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, okamžitě vrátí metoda **true**, a uzamčení předchozího zůstává v platnosti.

## <a name="try_lock_until"></a>  try_lock_until

Pokusy o získání vlastnictví `mutex` bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time* bodu v čase, který určuje mezní hodnotu, po jejímž uplynutí metody se již nebude pokoušet o získání vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud metoda úspěšně nezíská vlastnictví `mutex` nebo pokud volající vlákno již vlastní `mutex`; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Pokud volající vlákno již vlastní `mutex`, okamžitě vrátí metoda **true**, a uzamčení předchozího zůstává v platnosti.

## <a name="unlock"></a>  Odemknutí

Uvolní vlastnictví objektu `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda uvolní vlastnictví `mutex` až po je volána jako tolikrát, kolikrát [Zámek](#lock), [try_lock –](#try_lock), [try_lock_for –](#try_lock_for), a [try_lock_ dokud](#try_lock_until) byla úspěšně volána na `recursive_timed_mutex` objektu.

Pokud volající vlákno není vlastníkem `mutex`, není chování definováno.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex – >](../standard-library/mutex.md)<br/>
