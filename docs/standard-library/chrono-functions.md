---
title: '&lt;typu chrono&gt; funkce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
caps.latest.revision: 10
manager: ghogen
ms.openlocfilehash: 91ea7bbec0f86d74cf87ee06b8ec130b13ede83e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltchronogt-functions"></a>&lt;typu chrono&gt; funkce

||||
|-|-|-|
|[duration_cast –](#duration_cast)|[time_point_cast](#time_point_cast)|


## <a name="duration_cast"></a>  duration_cast –

Přetypování `duration` objekt zadaného typu.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```

### <a name="return-value"></a>Návratová hodnota

A `duration` objektu typu `To` časový interval představující `Dur`, která je oříznuta, pokud má a nevejde se do cílového typu.

### <a name="remarks"></a>Poznámky

Pokud `To` je vytváření instancí z `duration`, tato funkce není součástí rozlišení přetížení.

## <a name="time_point_cast"></a>  time_point_cast –

Přetypování [time_point](../standard-library/time-point-class.md) objekt zadaného typu.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```

### <a name="return-value"></a>Návratová hodnota

A `time_point` objektu s dobou trvání typu `To`.

### <a name="remarks"></a>Poznámky

Pokud `To` je vytváření instancí z [doba trvání](../standard-library/duration-class.md), tato funkce není součástí rozlišení přetížení.

## <a name="see-also"></a>Viz také

[\<chrono>](../standard-library/chrono.md)<br/>
