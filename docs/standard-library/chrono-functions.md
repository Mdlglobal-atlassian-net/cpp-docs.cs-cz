---
title: '&lt;chrono&gt; funkce'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: 5aadf776cc25e22a40ed75f854481dff63cce4bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371651"
---
# <a name="ltchronogt-functions"></a>&lt;chrono&gt; funkce

||||
|-|-|-|
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|

## <a name="duration_cast"></a>  duration_cast –

Přetypování `duration` objekt zadaného typu.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```

### <a name="return-value"></a>Návratová hodnota

A `duration` objekt typu `To` , který představuje časový interval `Dur`, který je zkrácen, pokud je nutné umístit do cílového typu.

### <a name="remarks"></a>Poznámky

Pokud `To` je instance `duration`, tato funkce není součástí řešení přetížení.

## <a name="time_point_cast"></a>  time_point_cast –

Přetypování [time_point](../standard-library/time-point-class.md) objekt zadaného typu.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```

### <a name="return-value"></a>Návratová hodnota

A `time_point` objekt, který má dobu trvání typu `To`.

### <a name="remarks"></a>Poznámky

Není-li `To` je instance [doba trvání](../standard-library/duration-class.md), tato funkce není součástí řešení přetížení.

## <a name="see-also"></a>Viz také:

[\<chrono>](../standard-library/chrono.md)<br/>
