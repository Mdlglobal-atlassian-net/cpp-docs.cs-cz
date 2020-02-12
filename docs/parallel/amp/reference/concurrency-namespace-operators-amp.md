---
title: Operátory oboru názvů Concurrency (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: 3b536f75e4ef6405b60d45e89290a7d97a01707d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126914"
---
# <a name="concurrency-namespace-operators-amp"></a>Operátory oboru názvů Concurrency (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[podnikatel](#operator_mod)|[podnikatel](#operator_star)|
|[operator + – operátor](#operator_add)|[podnikatel](#operator-)|[podnikatel](#operator_div)|
|[operator = = – operátor](#operator_eq_eq)|

## <a name="operator_eq_eq"></a>operator = = – operátor

Určuje, zda jsou zadané argumenty stejné.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator== (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí argumentů řazené kolekce členů.

*_Lhs*<br/>
Jedna z řazených kolekcí členů k porovnání

*_Rhs*<br/>
Jedna z řazených kolekcí členů k porovnání

### <a name="return-value"></a>Návratová hodnota

**true** , pokud se řazené kolekce členů rovnají; v opačném případě **false**.

## <a name="operator_neq"></a>! = – operátor

Určuje, zda zadané argumenty nejsou stejné.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
bool operator!= (
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí argumentů řazené kolekce členů.

*_Lhs*<br/>
Jedna z řazených kolekcí členů k porovnání

*_Rhs*<br/>
Jedna z řazených kolekcí členů k porovnání

### <a name="return-value"></a>Návratová hodnota

**true** , pokud řazené kolekce členů nejsou stejné; v opačném případě **false**.

## <a name="operator_add"></a>operator + – operátor

Vypočítá součet zadaných argumentů ze součásti.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
class _Tuple_type> _Tuple_type<_Rank>   operator+(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí argumentů řazené kolekce členů.

*_Lhs*<br/>
Jeden z argumentů, které mají být přidány.

*_Rhs*<br/>
Jeden z argumentů, které mají být přidány.

### <a name="return-value"></a>Návratová hodnota

Součet zadaných argumentů ze součásti.

## <a name="operator-"></a>podnikatel

Vypočítá rozdíl mezi zadanými argumenty v rámci součásti.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator-(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí argumentů řazené kolekce členů.

*_Lhs*<br/>
Argument, od kterého má být odečtena.

*_Rhs*<br/>
Argument, který má být odečten.

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi zadanými argumenty v součásti.

## <a name="operator_star"></a>podnikatel

Vypočítá produkt určený argumenty v rámci součásti.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator*(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí argumentů řazené kolekce členů.

*_Lhs*<br/>
Jedna z řazených kolekcí členů k násobení.

*_Rhs*<br/>
Jedna z řazených kolekcí členů k násobení.

### <a name="return-value"></a>Návratová hodnota

Produkt, který je součástí zadaných argumentů.

## <a name="operator_div"></a>podnikatel

Vypočítá podíl zadaných argumentů v rámci součásti.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator/(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí argumentů řazené kolekce členů.

*_Lhs*<br/>
Řazená kolekce členů k rozdělení.

*_Rhs*<br/>
Řazená kolekce členů k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Podíl zadaných argumentů v rámci součásti.

## <a name="operator_mod"></a>podnikatel

Vypočítá zbytky prvního zadaného argumentu druhým zadaným argumentem.

```cpp
template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    const _Tuple_type<_Rank>& _Lhs,
    typename _Tuple_type<_Rank>::value_type _Rhs) restrict(amp,cpu);

template <
    int _Rank,
    template <int> class _Tuple_type
>
_Tuple_type<_Rank>   operator%(
    typename _Tuple_type<_Rank>::value_type _Lhs,
    const _Tuple_type<_Rank>& _Rhs) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Rank*<br/>
Pořadí argumentů řazené kolekce členů.

*_Lhs*<br/>
Řazená kolekce členů, ze které se počítá modulo.

*_Rhs*<br/>
Řazená kolekce členů do modulo podle.

### <a name="return-value"></a>Návratová hodnota

Výsledkem prvního zadaného argumentu je druhý zadaný argument.

## <a name="see-also"></a>Viz také

[Concurrency – obor názvů](concurrency-namespace-cpp-amp.md)
