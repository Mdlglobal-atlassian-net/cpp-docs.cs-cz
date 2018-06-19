---
title: timed_mutex – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
dev_langs:
- C++
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.workload:
- cplusplus
ms.openlocfilehash: a4dc22ed8676c720dd8bde5c8f424915dfa8fe40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33863255"
---
# <a name="timedmutex-class"></a>timed_mutex – třída

Představuje *vypršel časový limit typu mutex*. Objekty tohoto typu se používají k vynucení vzájemné vyloučení prostřednictvím časově omezené blokování v rámci programu.

## <a name="syntax"></a>Syntaxe

```cpp
class timed_mutex;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Vytvoří `timed_mutex` objekt, který není uzamčený.|
|[timed_mutex::~timed_mutex Destructor](#dtortimed_mutex_destructor)|Uvolní všechny prostředky, které jsou používány `timed_mutex` objektu.|

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

## <a name="lock"></a>  timed_mutex::LOCK –

Blokuje volající vlákno, dokud vlákno získá vlastnictví `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, chování není definován.

## <a name="timed_mutex"></a>  timed_mutex::timed_mutex – konstruktor

Vytvoří `timed_mutex` objekt, který není uzamčený.

```cpp
timed_mutex();
```

## <a name="dtortimed_mutex_destructor"></a>  timed_mutex:: ~ timed_mutex – destruktor

Uvolní všechny prostředky, které jsou používány `mutex` objektu.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Poznámky

Pokud při spuštění destruktoru, není objekt uzamčen, chování nedefinovaný.

## <a name="try_lock"></a>  timed_mutex::try_lock –

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Návratová hodnota

`true` Pokud metoda úspěšně získá vlastnictví `mutex`, jinak hodnota `false`.

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, chování není definován.

## <a name="try_lock_for"></a>  timed_mutex::try_lock_for –

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) objekt, který určuje maximální množství času, která metoda se pokusí získat vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud metoda úspěšně získá vlastnictví `mutex`, jinak hodnota `false`.

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, chování není definován.

## <a name="try_lock_until"></a>  timed_mutex::try_lock_until –

Pokusí se získat vlastnictví `mutex` bez blokování.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parametry

`Abs_time` Bod v čase, který určuje mezní hodnotu, po jejímž uplynutí metodu již nebude pokoušet o získání vlastnictví `mutex`.

### <a name="return-value"></a>Návratová hodnota

`true` Pokud metoda úspěšně získá vlastnictví `mutex`, jinak hodnota `false`.

### <a name="remarks"></a>Poznámky

Pokud již vlastní volající vlákno `mutex`, chování není definován.

## <a name="unlock"></a>  timed_mutex::Unlock –

Uvolní vlastnictví `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Poznámky

Pokud není vlastníkem volající vlákno `mutex`, chování není definován.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex >](../standard-library/mutex.md)<br/>
