---
title: Operátory oboru názvů Concurrency (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: cd40f771cbab5651b2f33f0ed2e84ea1412855bd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598039"
---
# <a name="concurrency-namespace-operators-amp"></a>Operátory oboru názvů Concurrency (AMP)

||||
|-|-|-|
|[operator!=](#operator_neq)|[% – operátor](#operator_mod)|[Operator *](#operator_star)|
|[Operator +](#operator_add)|[Operator-](#operator-)|[Operator /](#operator_div)|
|[operator==](#operator_eq_eq)|

##  <a name="operator_eq_eq"></a>  Operator ==

Určuje, jestli jsou zadané argumenty jsou stejné.

```
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
Pořadí argumentů n-tice.

*_Lhs*<br/>
Jedna z n-tic pro srovnání.

*_Rhs*<br/>
Jedna z n-tic pro srovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou záznamy stejné; jinak **false**.

##  <a name="operator_neq"></a>  Operator! =

Určuje, zda jsou zadané argumenty nejsou stejné.

```
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
Pořadí argumentů n-tice.

*_Lhs*<br/>
Jedna z n-tic pro srovnání.

*_Rhs*<br/>
Jedna z n-tic pro srovnání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud záznamy nejsou stejné; jinak **false**.

##  <a name="operator_add"></a>  Operator +

Vypočítá součet zadaných argumentů podle komponent.

```
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
Pořadí argumentů n-tice.

*_Lhs*<br/>
Jeden z argumentů, které chcete přidat.

*_Rhs*<br/>
Jeden z argumentů, které chcete přidat.

### <a name="return-value"></a>Návratová hodnota

Podle komponent součet zadaných argumentů.

##  <a name="operator-"></a>  Operator-

Vypočítá rozdíl mezi zadanými argumenty podle komponent.

```
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
Pořadí argumentů n-tice.

*_Lhs*<br/>
Argument, který chcete odečíst od.

*_Rhs*<br/>
Argument, který se má odečíst.

### <a name="return-value"></a>Návratová hodnota

Rozdíl mezi zadanými argumenty podle komponent.

##  <a name="operator_star"></a>  Operator *

Vypočítá součin zadaných argumentů.

```
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
Pořadí argumentů n-tice.

*_Lhs*<br/>
Jeden ze záznamů pro násobení.

*_Rhs*<br/>
Jeden ze záznamů pro násobení.

### <a name="return-value"></a>Návratová hodnota

Součin zadaných argumentů.

##  <a name="operator_div"></a>  Operator /

Vypočítá podíl zadaných argumentů podle komponent.

```
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
Pořadí argumentů n-tice.

*_Lhs*<br/>
Řazená kolekce členů k rozdělení.

*_Rhs*<br/>
Řazená kolekce členů k rozdělení.

### <a name="return-value"></a>Návratová hodnota

Podle komponent podíl zadaných argumentů.

##  <a name="operator_mod"></a>  % – operátor

Vypočítá zbytek z prvního zadaného argumentu pomocí druhého zadaného argumentu.

```
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
Pořadí argumentů n-tice.

*_Lhs*<br/>
Řazené kolekce členů, ze kterého modul počítá.

*_Rhs*<br/>
Řazené kolekce členů k modulo podle.

### <a name="return-value"></a>Návratová hodnota

Výsledek prvního zadaného argumentu mění druhý zadaný argument.

## <a name="see-also"></a>Viz také

[souběžnost Namespace ](concurrency-namespace-cpp-amp.md)
