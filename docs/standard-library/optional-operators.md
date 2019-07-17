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
ms.openlocfilehash: c5d0de435180054b186400384fc0583df5b03246
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268030"
---
# <a name="ltoptionalgt-operators"></a>&lt;volitelné&gt; operátory

## <a name="op_eq_eq"></a> Operator ==

Testuje, zda `optional` objekt na levé straně operátoru rovná `optional` objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

*doprava*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

## <a name="op_neq"></a> Operator! =

Testuje, zda `optional` objekt na levé straně operátoru není roven `optional` objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

*doprava*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `!(left == right)`.

## <a name="op_lt"></a> – Operátor&lt;

Testuje, zda `optional` objekt na levé straně operátoru menší než `optional` objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

*doprava*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než, ale není v seznamu na pravé straně operátoru roven; v opačném případě **false**.

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Testuje, zda `optional` je objekt na levé straně operátoru menší než nebo rovna hodnotě `optional` objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

*doprava*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** -li v seznamu na levé straně operátoru menší než nebo rovna hodnotě v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `!(right < left)`.

## <a name="op_gt"></a> – Operátor&gt;

Testuje, zda `optional` je objekt na levé straně operátoru větší než `optional` objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

*doprava*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud je v seznamu na levé straně operátoru větší než v seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato šablona funkce vrátí `right < left`.

## <a name="op_gt_eq"></a> – Operátor&gt;=

Testuje, zda `optional` je objekt na levé straně operátoru větší než nebo rovna hodnotě `optional` objekt na pravé straně.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*doleva*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

*doprava*\
Objekt typu `optional`, `nullopt_t`, nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true** Pokud `optional` na levé straně operátoru je větší než nebo rovna hodnotě `optional` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Šablona funkce vrátí `!(left < right)`.
