---
title: '&lt;vlákno&gt; funkce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 948c00f7c0b773bf366f4ea9e102c832e9878d9b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38960447"
---
# <a name="ltthreadgt-functions"></a>&lt;vlákno&gt; funkce

||||
|-|-|-|
|[get_id](#get_id)|[sleep_for](#sleep_for)|[sleep_until –](#sleep_until)|
|[Prohození](#swap)|[yield](#yield)|

## <a name="get_id"></a>  get_id –

Jednoznačně identifikuje aktuální vlákno provádění.

```cpp
thread::id this_thread::get_id() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Objekt typu [Thread::ID –](../standard-library/thread-class.md) , který jednoznačně identifikuje aktuální vlákno provádění.

## <a name="sleep_for"></a>  sleep_for –

Blokuje volající vlákno.

```cpp
template <class Rep,
class Period>
inline void sleep_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parametry

*Rel_time*  
 A [doba trvání](../standard-library/duration-class.md) objekt, který určuje časový interval.

### <a name="remarks"></a>Poznámky

Funkce blokuje volající vlákno pro alespoň čas, který je určen *Rel_time*. Tato funkce nevyvolá žádné výjimky.

## <a name="sleep_until"></a>  sleep_until –

Blokuje volající vlákno, alespoň do zadané doby.

```cpp
template <class Clock, class Duration>
void sleep_until(const chrono::time_point<Clock, Duration>& Abs_time);

void sleep_until(const xtime *Abs_time);
```

### <a name="parameters"></a>Parametry

*Abs_time*  
 Představuje bod v čase.

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="swap"></a>  Prohození

Prohodí dva stavy **vlákno** objekty.

```cpp
void swap(thread& Left, thread& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Doleva*  
 Levé straně **vlákno** objektu.

*Doprava*  
 Vpravo **vlákno** objektu.

### <a name="remarks"></a>Poznámky

Volání funkcí `Left.swap(Right)`.

## <a name="yield"></a>  YIELD

Signály ke spuštění jiných vláken operačního systému, i v případě, že aktuální vlákno by obvykle i nadále spouštět.

```cpp
inline void yield() noexcept;
```

## <a name="see-also"></a>Viz také:

[\<vlákna >](../standard-library/thread.md)<br/>
