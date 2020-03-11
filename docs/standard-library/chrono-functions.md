---
title: funkce &lt;Chrono&gt;
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 85fdd413354b3f310d3315a80cf7da983cf6621d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865193"
---
# <a name="ltchronogt-functions"></a>funkce &lt;Chrono&gt;

## <a name="duration_cast"></a>duration_cast

Přetypování `duration` objektu na zadaný typ.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);

template <class ToDuration, class Rep, class Period>
constexpr ToDuration floor(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration ceil(const duration<Rep, Period>& d);
template <class ToDuration, class Rep, class Period>
constexpr ToDuration round(const duration<Rep, Period>& d);
```

### <a name="return-value"></a>Návratová hodnota

Objekt `duration` typu `To`, který představuje `Dur`časového intervalu, který je zkrácen, pokud se musí vejít do cílového typu.

### <a name="remarks"></a>Poznámky

Pokud je `To` instance `duration`, tato funkce není součástí řešení přetížení.

## <a name="time_point_cast"></a>time_point_cast

Přetypování [time_point](../standard-library/time-point-class.md) objektu na zadaný typ.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);

template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
floor(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
ceil(const time_point<Clock, Duration>& tp);
template <class ToDuration, class Clock, class Duration>
constexpr time_point<Clock, ToDuration>
round(const time_point<Clock, Duration>& tp);
```

### <a name="return-value"></a>Návratová hodnota

Objekt `time_point`, který má dobu trvání typu `To`.

### <a name="remarks"></a>Poznámky

Pokud `To` není instancí [Trvání](../standard-library/duration-class.md), tato funkce není součástí řešení přetížení.
