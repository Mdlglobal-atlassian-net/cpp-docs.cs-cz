---
title: '&lt;chrono&gt; operátory | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 73019bc3d9aca2ef6bc094fd93f1f8b627dad2e4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074680"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; operátory

||||
|-|-|-|
|[Operátor modulo](#op_modulo)|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|
|[– Operátor&gt;=](#op_gt_eq)|[– Operátor&lt;](#op_lt)|[– Operátor&lt;=](#op_lt_eq)|
|[Operator *](#op_star)|[Operator +](#op_add)|[Operator-](#operator-)|
|[Operator /](#op_div)|[operator==](#op_eq_eq)|

## <a name="operator-"></a>  Operator-

Operátor odčítání nebo negace objektů [doba trvání](../standard-library/duration-class.md) a [time_point](../standard-library/time-point-class.md) objekty.

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

*čas*<br/>
A `time_point` objektu.

*Doba trvání*<br/>
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `duration` objekt, jehož délka intervalu je rozdíl mezi časovými intervaly obou argumentů.

Druhá funkce vrátí `time_point` objekt, který představuje bod v čase, který je posunout o negaci časového intervalu, která je reprezentována *doba trvání*, od bodu v čase, který je určen *čas*.

Třetí funkce vrátí `duration` objekt, který představuje časový interval mezi *vlevo* a *vpravo*.

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `!(Left == Right)`.

## <a name="op_star"></a>  Operator *

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

*Doba trvání*<br/>
A `duration` objektu.

*Mult*<br/>
Celočíselná hodnota.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `duration` objekt, jehož délka intervalu je *Mult* vynásobena délkou *doba trvání*.

Není-li `is_convertible<Rep2, common_type<Rep1, Rep2>>` *platí*, první funkce není součástí řešení přetížení. Další informace naleznete v tématu [< type_traits >](../standard-library/type-traits.md).

Není-li `is_convertible<Rep1, common_type<Rep1, Rep2>>` *platí*, druhá funkce není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="op_div"></a>  Operator /

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

*Doba trvání*<br/>
A `duration` objektu.

*div*<br/>
Celočíselná hodnota.

*doleva*<br/>
Levé straně `duration` objektu.

*doprava*<br/>
Vpravo `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

První operátor vrací objekt trvání, jehož intervalu je délka *doba trvání* vydělená hodnotou *Div*.

Druhý operátor vrátí poměr délek interval *vlevo* a *vpravo*.

Není-li `is_convertible<Rep2, common_type<Rep1, Rep2>>` *platí*, a `Rep2` není instancí `duration`, první operátor není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="op_add"></a>  Operator +

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

*čas*<br/>
A `time_point` objektu.

*Doba trvání*<br/>
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `duration` objekt, který obsahuje časový interval, který je roven součtu intervalů *vlevo* a *vpravo*.

Druhý a třetí funkce vrátí `time_point` objekt, který představuje bod v čase, který je posunut o interval *doba trvání*, od bodu v čase *čas*.

## <a name="op_lt"></a>  – Operátor&lt;

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) je menší než jiný objekt `duration` nebo `time_point` objektu.

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

První funkce vrací **true** Pokud délka intervalu *vlevo* je menší než délka intervalu *vpravo*. V opačném případě vrátí funkce **false**.

Druhá funkce vrátí **true** Pokud *vlevo* předchází *vpravo*. V opačném případě vrátí funkce **false**.

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) objekt je menší nebo rovna jiné `duration` nebo `time_point` objektu.

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `!(Right < Left)`.

## <a name="op_eq_eq"></a>  Operator ==

Určuje, zda dva `duration` objekty představují časové intervaly, které mají stejnou délku, nebo zda dva `time_point` objekty představují stejný bod v čase.

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

První funkce vrací **true** Pokud *vlevo* a *vpravo* představují časové intervaly, které mají stejnou délku. V opačném případě vrátí funkce **false**.

Druhá funkce vrátí **true** Pokud *vlevo* a *vpravo* představují stejný bod v čase. V opačném případě vrátí funkce **false**.

## <a name="op_gt"></a>  – Operátor&gt;

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) je větší než jiný objekt `duration` nebo `time_point` objektu.

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `Right < Left`.

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Určuje, zda jeden [doba trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) objekt je větší než nebo roven jinému `duration` nebo `time_point` objektu.

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

*doleva*<br/>
Levé straně `duration` nebo `time_point` objektu.

*doprava*<br/>
Vpravo `duration` nebo `time_point` objektu.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `!(Left < Right)`.

## <a name="op_modulo"></a>  Operátor modulo

Operátor modulo operace [doba trvání](../standard-library/duration-class.md) objekty.

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

*Doba trvání*<br/>
A `duration` objektu.

*div*<br/>
Celočíselná hodnota.

*doleva*<br/>
Levé straně `duration` objektu.

*doprava*<br/>
Vpravo `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce `duration` objekt, jehož délka intervalu je *doba trvání* modulo *Div*.

Druhá funkce vrátí hodnotu, která představuje *vlevo* modulo *vpravo*.

## <a name="see-also"></a>Viz také:

[\<chrono>](../standard-library/chrono.md)<br/>
