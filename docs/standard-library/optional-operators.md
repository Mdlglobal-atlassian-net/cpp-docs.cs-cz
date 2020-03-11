---
title: '&lt;volitelné operátory&gt;'
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854051"
---
# <a name="ltoptionalgt-operators"></a>&lt;volitelné operátory&gt;

## <a name="op_eq_eq"></a>operator = = – operátor

Testuje, zda je objekt `optional` na levé straně operátoru roven objektu `optional` na pravé straně.

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*pravé*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

## <a name="op_neq"></a>! = – operátor

Testuje, zda `optional` objekt na levé straně operátoru není roven objektu `optional` na pravé straně.

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*pravé*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="remarks"></a>Poznámky

Tato funkce šablony vrací `!(left == right)`.

## <a name="op_lt"></a>operátor&lt;

Testuje, zda je objekt `optional` na levé straně operátoru menší než objekt `optional` na pravé straně.

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*pravé*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru menší než, ale není rovno seznamu na pravé straně operátoru; v opačném případě **false**.

## <a name="op_lt_eq"></a>operátor&lt;=

Testuje, zda je objekt `optional` na levé straně operátoru menší než nebo roven `optional`mu objektu na pravé straně.

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*pravé*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru menší než nebo rovný seznamu na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce šablony vrací `!(right < left)`.

## <a name="op_gt"></a>operátor&gt;

Testuje, zda je objekt `optional` na levé straně operátoru větší než objekt `optional` na pravé straně.

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*pravé*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je seznam na levé straně operátoru větší než seznam na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce šablony vrací `right < left`.

## <a name="op_gt_eq"></a>operátor&gt;=

Testuje, zda je objekt `optional` na levé straně operátoru větší než nebo roven `optional`mu objektu na pravé straně.

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>Parametry

*levý*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

*pravé*\
Objekt typu `optional`, `nullopt_t`nebo `T`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je `optional` na levé straně operátoru větší než nebo rovno `optional` na pravé straně operátoru; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Funkce šablony vrací `!(left < right)`.
