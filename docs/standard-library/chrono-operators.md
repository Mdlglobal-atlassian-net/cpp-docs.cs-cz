---
title: '&lt;operátory&gt; Chrono'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 398e2429c38cffb454c7b510aa5ab44fbe4cfef6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421931"
---
# <a name="ltchronogt-operators"></a>&lt;operátory&gt; Chrono

## <a name="operator-"></a>podnikatel

Operátor pro odčítání nebo negaci [dob trvání](../standard-library/duration-class.md) a [time_point](../standard-library/time-point-class.md) objektů.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

*Čas*\
Objekt `time_point`.

*Doba trvání*\
Objekt `duration`.

### <a name="return-value"></a>Návratová hodnota

První funkce vrátí objekt `duration`, jehož délka intervalu je rozdíl mezi časovými intervaly dvou argumentů.

Druhá funkce vrátí objekt `time_point`, který představuje bod v čase, který je umístěn, po negaci časového intervalu, který je reprezentován hodnotou *dur*, od bodu v čase, který je určen *časem*.

Třetí funkce vrátí objekt `duration`, který představuje časový interval mezi *levým* a *pravým tlačítkem*.

## <a name="op_neq"></a>! = – operátor

Operátor nerovnosti pro [dobu trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) objektů.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `!(Left == Right)`.

## <a name="op_star"></a>podnikatel

Operátor násobení pro objekty [Duration](../standard-library/chrono-operators.md#op_star)

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

*Doba trvání*\
Objekt `duration`.

*Mult*\
Celočíselná hodnota.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí objekt `duration`, jehož délka intervalu je *mult* vynásobená délkou *Trvání*.

Pokud `is_convertible<Rep2, common_type<Rep1, Rep2>>`*nedrží hodnotu true*, první funkce není součástí řešení přetížení. Další informace sssee [< type_traits >](../standard-library/type-traits.md).

Pokud `is_convertible<Rep1, common_type<Rep1, Rep2>>`*nedrží hodnotu true*, druhá funkce není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="op_div"></a>podnikatel

Operátor dělení pro objekty [doby trvání](../standard-library/chrono-operators.md#op_star)

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

*Doba trvání*\
Objekt `duration`.

\ *div*
Celočíselná hodnota.

*Levý*\
Levý objekt `duration`.

*Pravé*\
Pravý objekt `duration`.

### <a name="return-value"></a>Návratová hodnota

První operátor vrátí objekt duration, jehož délka intervalu je délka *Trvání* dělené hodnotou *div*.

Druhý operátor vrátí poměr délky intervalu *vlevo* a *vpravo*.

Pokud `is_convertible<Rep2, common_type<Rep1, Rep2>>`*nedrží hodnotu true*a `Rep2` není instancí `duration`, první operátor se nepodílí na řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

## <a name="op_add"></a>operator + – operátor

Přidá [dobu trvání](../standard-library/duration-class.md) a [time_point](../standard-library/time-point-class.md) objektů.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

*Čas*\
Objekt `time_point`.

*Doba trvání*\
Objekt `duration`.

### <a name="return-value"></a>Návratová hodnota

První funkce vrátí objekt `duration`, který má časový interval, který je roven součtu v intervalech *levého* a *pravého*.

Druhá a třetí funkce vrátí objekt `time_point`, který představuje bod v čase, který je umístěn v intervalu *Trvání*, od bodu v *čase.*

## <a name="op_lt"></a>operátor&lt;

Určuje, zda jeden objekt [Trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) je menší než jiný objekt `duration` nebo `time_point`.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

### <a name="return-value"></a>Návratová hodnota

První funkce vrátí **hodnotu true** , pokud je délka intervalu *vlevo* menší než délka intervalu *vpravo*. V opačném případě vrátí funkce **hodnotu false**.

Druhá funkce vrátí **hodnotu true** , pokud *Left* předchází *Right*. V opačném případě vrátí funkce **hodnotu false**.

## <a name="op_lt_eq"></a>operátor&lt;=

Určuje, zda jeden objekt [Trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) je menší nebo roven jinému `duration` nebo objektu `time_point`.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `!(Right < Left)`.

## <a name="op_eq_eq"></a>operator = = – operátor

Určuje, zda dva objekty `duration` reprezentují časové intervaly, které mají stejnou délku, nebo zda dva objekty `time_point` reprezentují stejný bod v čase.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

### <a name="return-value"></a>Návratová hodnota

První funkce vrátí **hodnotu true** , pokud *Left* a *Right* reprezentují časové intervaly, které mají stejnou délku. V opačném případě vrátí funkce **hodnotu false**.

Druhá funkce vrátí **hodnotu true** , pokud *Left* a *Right* reprezentují stejný bod v čase. V opačném případě vrátí funkce **hodnotu false**.

## <a name="op_gt"></a>operátor&gt;

Určuje, zda jeden objekt [Trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) je větší než jiný objekt `duration` nebo `time_point`.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `Right < Left`.

## <a name="op_gt_eq"></a>operátor&gt;=

Určuje, zda jeden objekt [Trvání](../standard-library/duration-class.md) nebo [time_point](../standard-library/time-point-class.md) je větší nebo roven jinému `duration` nebo objektu `time_point`.

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

*Levý*\
Levý `duration` nebo objekt `time_point`.

*Pravé*\
Pravý `duration` objekt nebo objekt `time_point`.

### <a name="return-value"></a>Návratová hodnota

Každá funkce vrátí `!(Left < Right)`.

## <a name="op_modulo"></a>Operátor modulo

Operátor pro operace modulo u objektů [Duration](../standard-library/duration-class.md)

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

*Doba trvání*\
Objekt `duration`.

\ *div*
Celočíselná hodnota.

*Levý*\
Levý objekt `duration`.

*Pravé*\
Pravý objekt `duration`.

### <a name="return-value"></a>Návratová hodnota

První funkce vrátí objekt `duration`, jehož délka intervalu je *dur* modulo *div*.

Druhá funkce vrátí hodnotu, která představuje *levé* a Nemodulo *zprava*.
