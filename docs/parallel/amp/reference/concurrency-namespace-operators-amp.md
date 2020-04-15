---
title: Operátory oboru názvů Concurrency (AMP)
ms.date: 11/04/2016
ms.assetid: 77f1ae17-1eb2-480d-8fe5-66d4c24bb91e
ms.openlocfilehash: c4086029b71d71091a12b9b6023cc6098faf2f85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376294"
---
# <a name="concurrency-namespace-operators-amp"></a>Operátory oboru názvů Concurrency (AMP)

||||
|-|-|-|
|[operátor!=](#operator_neq)|[operátor%](#operator_mod)|[operátor*](#operator_star)|
|[operátor+](#operator_add)|[operátor-](#operator-)|[operátor/](#operator_div)|
|[operátor==](#operator_eq_eq)|

## <a name="operator"></a><a name="operator_eq_eq"></a>operátor==

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
Jeden z n-tic porovnat.

*_Rhs*<br/>
Jeden z n-tic porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** v případě, že řazené kolekce členů jsou stejné; jinak **false**.

## <a name="operator"></a><a name="operator_neq"></a>operátor!=

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
Jeden z n-tic porovnat.

*_Rhs*<br/>
Jeden z n-tic porovnat.

### <a name="return-value"></a>Návratová hodnota

**true** v případě, že řazené kolekce členů nejsou stejné; jinak **false**.

## <a name="operator"></a><a name="operator_add"></a>operátor+

Vypočítá součet komponent zadaných argumentů.

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
Jeden z argumentů přidat.

*_Rhs*<br/>
Jeden z argumentů přidat.

### <a name="return-value"></a>Návratová hodnota

Součet komponent y zadané argumenty.

## <a name="operator-"></a><a name="operator-"></a>operátor-

Vypočítá rozdíl komponenty mezi zadanými argumenty.

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
Argument, od který má být odečten.

*_Rhs*<br/>
Argument odečíst.

### <a name="return-value"></a>Návratová hodnota

Komponenta moudrý rozdíl mezi zadané argumenty.

## <a name="operator"></a><a name="operator_star"></a>operátor*

Vypočítá komponenty z hlediska složky zadané argumenty.

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
Jeden z n-tic množí.

*_Rhs*<br/>
Jeden z n-tic množí.

### <a name="return-value"></a>Návratová hodnota

Komponenta moudrý produkt zadané argumenty.

## <a name="operator"></a><a name="operator_div"></a>operátor/

Vypočítá kvocient zadaného argumentu z hlediska komponenty.

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
N-tice, která má být rozdělena.

*_Rhs*<br/>
Řazená kolekce členů, kterou chcete rozdělit.

### <a name="return-value"></a>Návratová hodnota

Kvocient zadaného argumentu z hlediska komponenty.

## <a name="operator"></a><a name="operator_mod"></a>operátor%

Vypočítá modul prvního zadaného argumentu druhým zadaným argumentem.

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
Řazená kolekce členů, ze kterého je vypočítáno modulo.

*_Rhs*<br/>
N-tice na modulo by.

### <a name="return-value"></a>Návratová hodnota

Výsledek prvního zadaného modulu argumentu druhý zadaný argument.

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti](concurrency-namespace-cpp-amp.md)
