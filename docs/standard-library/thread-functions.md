---
title: '&lt;funkce&gt; vlákna'
ms.date: 11/04/2016
f1_keywords:
- thread/std::get_id
- thread/std::sleep_for
- thread/std::sleep_until
- thread/std::swap
- thread/std::yield
ms.assetid: bb1aa1ef-fe3f-4e2c-8b6e-e22dbf2f5a19
helpviewer_keywords:
- std::get_id [C++]
- std::sleep_for [C++]
- std::sleep_until [C++]
- std::swap [C++]
- std::yield [C++]
ms.openlocfilehash: bb0a0a12ec2882701447804f9c88d1776a196cb7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375842"
---
# <a name="ltthreadgt-functions"></a>&lt;funkce&gt; vlákna

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[Swap](#swap)|[yield](#yield)|

## <a name="get_id"></a><a name="get_id"></a>get_id

Jednoznačně identifikuje aktuální vlákno provádění.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Objekt typu [thread::id,](../standard-library/thread-class.md) který jednoznačně identifikuje aktuální vlákno spuštění.

## <a name="sleep_for"></a><a name="sleep_for"></a>sleep_for

Blokuje volající vlákno.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [duration,](../standard-library/duration-class.md) který určuje časový interval.

### <a name="remarks"></a>Poznámky

Funkce blokuje volající vlákno alespoň po dobu určenou *Rel_time*. Tato funkce nevyvolá žádné výjimky.

## <a name="sleep_until"></a><a name="sleep_until"></a>sleep_until

Blokuje volající vlákno alespoň do zadaného času.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Představuje bod v čase.

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="swap"></a><a name="swap"></a>Swap

Zamění stavy dvou objektů **podprocesu.**

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt **levého vlákna.**

*Právo*\
Objekt **pravého vlákna.**

### <a name="remarks"></a>Poznámky

Funkce volá `Left.swap(Right)`.

## <a name="yield"></a><a name="yield"></a>Výnos

Signalizuje operačnímu systému spustit jiná vlákna, i v případě, že aktuální vlákno by obvykle nadále spustit.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Viz také

[\<>vláken](../standard-library/thread.md)
