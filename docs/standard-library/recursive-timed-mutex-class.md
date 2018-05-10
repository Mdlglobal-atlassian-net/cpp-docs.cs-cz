---
title: recursive_timed_mutex – třída | Microsoft Docs
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
ms.openlocfilehash: 9b4a87cadedb11368d7803231b96d0f7a5acfb99
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex – třída

Představuje *vypršel časový limit typu mutex*. Objekty tohoto typu se používají k vynucení vzájemné vyloučení pomocí časově omezené blokování v rámci programu. Na rozdíl od objekty typu [timed_mutex](../standard-library/timed-mutex-class.md), účinek volání uzamčení metod pro `recursive_timed_mutex` objektů je dobře definovaný.

## <a name="syntax"></a>Syntaxe

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Vytvoří `recursive_timed_mutex` objekt, který není uzamčený.|
|[~recursive_timed_mutex Destructor](#dtorrecursive_timed_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `recursive_timed_mutex` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[lock](#lock)|Blokuje volající vlákno, dokud vlákno získá vlastnictví `mutex`.|
|[try_lock](#try_lock)|Pokusí se získat vlastnictví `mutex` bez blokování.|
|[try_lock_for](#try_lock_for)|Pokusí se získat vlastnictví `mutex` zadaný časový interval.|
|[try_lock_until](#try_lock_until)|Pokusí se získat vlastnictví `mutex` až po zadanou dobu.|
|[odemknutí](#unlock)|Uvolní vlastnictví `mutex`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<mutex >

**Namespace:** – std

## <a name="lock"></a>  Zámek

Blokuje volající vlákno, dokud vlákno získá vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, vrátí tato metoda hodnotu okamžitě a předchozí zámek zůstává v platnosti.

## <a name="recursive_timed_mutex"></a>  recursive_timed_mutex – konstruktor

Vytvoří `recursive_timed_mutex` objekt, který není uzamčený.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a>  ~ recursive_timed_mutex – destruktor

Uvolní všechny prostředky, které jsou používány `recursive_timed_mutex` objektu.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud při spuštění destruktoru, není objekt uzamčen, chování nedefinovaný.

## <a name="try_lock"></a>  try_lock –

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud metoda byly úspěšně načteny vlastnictví `mutex` nebo pokud již vlastní volající vlákno `mutex`, jinak hodnota `false`.

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, funkce hned vrátí `true`, a předchozí zámek zůstává v platnosti.

## <a name="try_lock_for"></a>  try_lock_for –

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální množství času, která metoda se pokusí získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud metoda úspěšně získá vlastnictví `mutex` nebo pokud již vlastní volající vlákno `mutex`, jinak hodnota `false`.

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, okamžitě vrátí metoda `true`, a předchozí zámek zůstává v platnosti.

## <a name="try_lock_until"></a>  try_lock_until

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

`Abs_time` Bod v čase, který určuje mezní hodnotu, po jejímž uplynutí metodu již nebude pokoušet o získání vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud metoda úspěšně získá vlastnictví `mutex` nebo pokud již vlastní volající vlákno `mutex`, jinak hodnota `false`.

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, okamžitě vrátí metoda `true`, a předchozí zámek zůstává v platnosti.

## <a name="unlock"></a>  odemknutí

Uvolní vlastnictví `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Tato metoda uvolní vlastnictví `mutex` až po jako tolikrát, kolikrát se označuje jako [zámku](#lock), [try_lock –](#try_lock), [try_lock_for –](#try_lock_for), a [try_lock_ dokud](#try_lock_until) byla úspěšně volána na `recursive_timed_mutex` objektu.

Pokud není vlastníkem volající vlákno `mutex`, chování není definován.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex >](../standard-library/mutex.md)<br/>
