---
title: '&lt;typu chrono&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
caps.latest.revision: 8
manager: ghogen
ms.openlocfilehash: ef535697ab7bda5cf193ef386a7e63542f431f45
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="ltchronogt-operators"></a>&lt;typu chrono&gt; operátory

||||
|-|-|-|
|[Operátor modulo](#op_modulo)|[operator!=](#op_neq)|[Operátor&gt;](#op_gt)|
|[Operátor&gt;=](#op_gt_eq)|[Operátor&lt;](#op_lt)|[Operátor&lt;=](#op_lt_eq)|
|[operátor *](#op_star)|[operátor +](#op_add)|[Operator –](#operator-)|
|[operátor nebo](#op_div)|[operator==](#op_eq_eq)|

## <a name="operator-"></a>  Operator –

Operátor odčítání nebo negace [doba trvání](../standard-library/duration-class.md) a [time_point](../standard-library/time-point-class.md) objekty.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);


template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

`Time` A `time_point` objektu.

`Dur` A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `duration` objekt, jehož délka intervalu je rozdíl mezi dvěma argumentů časové intervaly.

Vrátí druhou funkce `time_point` objekt, který reprezentuje bod v čase, který je posunout o negace časový interval, která je reprezentována `Dur`, z bodu v čase, která je zadána `Time`.

Vrátí třetí funkce `duration` objekt, který reprezentuje časový interval mezi `Left` a `Right`.

## <a name="op_neq"></a>  Operator! =

Operátor nerovnosti pro [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) objekty.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);


template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí `!(Left == Right)`.

## <a name="op_star"></a>  operátor *

Operátor násobení pro [doba trvání](../standard-library/chrono-operators.md#op_star) objekty.

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);


template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` objektu.

`Mult` Celočíselné hodnoty.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí `duration` objekt, jehož délka intervalu je `Mult` násobí hodnotou délka `Dur`.

Pokud `is_convertible<Rep2, common_type<Rep1, Rep2>>` *platí*, první funkce neúčastní rozlišení přetížení. Další informace, sssee [< type_traits >](../standard-library/type-traits.md).

Pokud `is_convertible<Rep1, common_type<Rep1, Rep2>>` *platí*, druhý funkce neúčastní rozlišení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="op_div"></a>  operátor nebo

Operátor dělení pro [doba trvání](../standard-library/chrono-operators.md#op_star) objekty.

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);


template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` objektu.

`Div` Celočíselné hodnoty.

`Left` Levé straně `duration` objektu.

`Right` Právo `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí objekt doba trvání intervalu, jehož délka je délka `Dur` dělený hodnota `Div`.

Vrátí druhou operátor poměr délek interval `Left` a `Right`.

Pokud `is_convertible<Rep2, common_type<Rep1, Rep2>>` *platí*, a `Rep2` není vytváření instancí z `duration`, první operátor neúčastní rozlišení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="op_add"></a>  operátor +

Přidá [doba trvání](../standard-library/duration-class.md) a [time_point](../standard-library/time-point-class.md) objekty.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);


template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);


template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

`Time` A `time_point` objektu.

`Dur` A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `duration` objekt, který má časový interval, který je určena součtem intervaly `Left` a `Right`.

Druhý a třetí funkce vrátí `time_point` objekt, který reprezentuje bod v čase, který přemístil, intervalem `Dur`, z bodu v čase `Time`.

## <a name="op_lt"></a>  Operátor&lt;

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) objektu je menší než jiná `duration` nebo `time_point` objektu.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);


template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `true` Pokud délka intervalu `Left` je menší než délka intervalu `Right`. Jinak, funkce vrátí hodnotu `false`.

Vrátí druhou funkce `true` Pokud `Left` předchází `Right`. Jinak, funkce vrátí hodnotu `false`.

## <a name="op_lt_eq"></a>  Operátor&lt;=

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) objektu je menší než nebo rovna do jiného `duration` nebo `time_point` objektu.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí `!(Right < Left)`.

## <a name="op_eq_eq"></a>  Operator ==

Určuje, zda dva `duration` představovat časové intervaly, které mají stejnou délku, nebo zda dvě `time_point` objekty představují stejného bodu v čase.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `true` Pokud `Left` a `Right` představují časové intervaly, které mají stejnou délku. Jinak, funkce vrátí hodnotu `false`.

Vrátí druhou funkce `true` Pokud `Left` a `Right` představují stejného bodu v čase. Jinak, funkce vrátí hodnotu `false`.

## <a name="op_gt"></a>  Operátor&gt;

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) je větší než druhý objekt `duration` nebo `time_point` objektu.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí `Right < Left`.

## <a name="op_gt_eq"></a>  Operátor&gt;=

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) objekt je větší než nebo rovna hodnotě jiného `duration` nebo `time_point` objektu.

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>Parametry

`Left` Levé straně `duration` nebo `time_point` objektu.

`Right` Právo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Jednotlivé funkce vrátí `!(Left < Right)`.

## <a name="op_modulo"></a>  Operátor modulo

Operátor pro modulo operací na [doba trvání](../standard-library/duration-class.md) objekty.

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` objektu.

`Div` Celočíselné hodnoty.

`Left` Levé straně `duration` objektu.

`Right` Právo `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `duration` objekt, jehož délka intervalu je `Dur` modulo `Div`.

Druhý funkce vrátí hodnotu, která představuje `Left` modulo `Right`.

## <a name="see-also"></a>Viz také

[\<chrono>](../standard-library/chrono.md)<br/>
