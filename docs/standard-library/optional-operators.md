---
title: '&lt;volitelné&gt; operátory'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: 9bdef0669f90da7865f7652ff4528e51e584e1a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373632"
---
# <a name="ltoptionalgt-operators"></a>&lt;volitelné&gt; operátory

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

Testy, `optional` pokud objekt na levé straně operátoru `optional` se rovná objektu na pravé straně.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*Právo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

## <a name="operator"></a><a name="op_neq"></a>operátor!=

Testy, `optional` pokud objekt na levé straně operátoru `optional` není rovna objektu na pravé straně.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*Právo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="remarks"></a>Poznámky

Tato funkce `!(left == right)`šablony vrátí .

## <a name="operatorlt"></a><a name="op_lt"></a>Operátor&lt;

Testy, `optional` pokud objekt na levé straně operátoru `optional` je menší než objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*Právo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je seznam na levé straně operátora menší než seznam na pravé straně obsluhy, ale nerovná se mu; jinak **false**.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operátor&lt;=

Testy, `optional` pokud objekt na levé straně operátoru je `optional` menší nebo rovno objektu na pravé straně.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*Právo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je seznam na levé straně operátora menší nebo roven seznamu na pravé straně obsluhy; jinak **false**.

### <a name="remarks"></a>Poznámky

Tato funkce `!(right < left)`šablony vrátí .

## <a name="operatorgt"></a><a name="op_gt"></a>Operátor&gt;

Testy, `optional` pokud je objekt na levé straně `optional` operátoru větší než objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*Právo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je seznam na levé straně operátora větší než seznam na pravé straně operátora; jinak **false**.

### <a name="remarks"></a>Poznámky

Tato funkce `right < left`šablony vrátí .

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operátor&gt;=

Testy, `optional` pokud je objekt na levé straně operátoru `optional` větší nebo rovno objektu na pravé straně.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*Právo*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true,** `optional` pokud je na levé straně obsluhy větší `optional` nebo rovna na pravé straně obsluhy; jinak **false**.

### <a name="remarks"></a>Poznámky

Funkce šablony `!(left < right)`vrátí .
