---
title: funkce&gt; &lt;vlákna
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
ms.openlocfilehash: 8064cec7e94a909d7dc2e1b22142d362bb7b9488
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420734"
---
# <a name="ltthreadgt-functions"></a>funkce&gt; &lt;vlákna

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until](#sleep_until)|
|[adresu](#swap)|[yield](#yield)|

## <a name="get_id"></a>get_id

Jednoznačně identifikuje aktuální vlákno provádění.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Objekt typu [thread:: ID](../standard-library/thread-class.md) , který jednoznačně identifikuje aktuální vlákno provádění.

## <a name="sleep_for"></a>sleep_for

Blokuje volající vlákno.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Objekt [Duration](../standard-library/duration-class.md) , který určuje časový interval.

### <a name="remarks"></a>Poznámky

Funkce blokuje volající vlákno alespoň v čase určeném pomocí *Rel_time*. Tato funkce nevyvolá žádné výjimky.

## <a name="sleep_until"></a>sleep_until

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

## <a name="swap"></a>adresu

Zamění stavy dvou objektů **vlákna** .

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt **vlákna** .

*Pravé*\
Pravý objekt **vlákna** .

### <a name="remarks"></a>Poznámky

Funkce volá `Left.swap(Right)`.

## <a name="yield"></a>Výsledkem

Signalizuje operačnímu systému, aby spouštěl další vlákna, i v případě, že aktuální vlákno obvykle pokračuje v běhu.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Viz také

[> \<vlákna](../standard-library/thread.md)
