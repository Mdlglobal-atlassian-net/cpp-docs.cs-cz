---
title: '&lt;operátory vláken&gt;'
ms.date: 11/04/2016
f1_keywords:
- thread/std::operator!=
- thread/std::operator&gt;
- thread/std::operator&gt;=
- thread/std::operator&lt;
- thread/std::operator&lt;&lt;
- thread/std::operator&lt;=
- thread/std::operator==
ms.assetid: e6bb6c0f-64f9-4cb2-9ff2-05b88a6ba7ac
helpviewer_keywords:
- std::operator!= (thread)
- std::operator&gt; (thread)
- std::operator&gt;= (thread)
- std::operator&lt; (thread)
- std::operator&lt;&lt; (thread)
- std::operator&lt;= (thread)
- std::operator== (thread)
ms.openlocfilehash: 6312d14dc681736ee396d5c7af6c50ba8d72cd3a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375824"
---
# <a name="ltthreadgt-operators"></a>&lt;operátory vláken&gt;

||||
|-|-|-|
|[operátor!=](#op_neq)|[Operátor&gt;](#op_gt)|[Operátor&gt;=](#op_gt_eq)|
|[Operátor&lt;](#op_lt)|[Operátor&lt;&lt;](#op_lt_lt)|[Operátor&lt;=](#op_lt_eq)|
|[operátor==](#op_eq_eq)|

## <a name="operatorgt"></a><a name="op_gt_eq"></a>Operátor&gt;=

Určuje, zda `thread::id` je jeden objekt větší nebo roven druhému.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý `thread::id` objekt.

*Právo*\
Správný `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`!(Left < Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="operatorgt"></a><a name="op_gt"></a>Operátor&gt;

Určuje, zda `thread::id` je jeden objekt větší než jiný.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý `thread::id` objekt.

*Právo*\
Správný `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`Right < Left`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="operatorlt"></a><a name="op_lt_eq"></a>Operátor&lt;=

Určuje, zda `thread::id` je jeden objekt menší nebo roven jinému objektu.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý `thread::id` objekt.

*Právo*\
Správný `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`!(Right < Left)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="operatorlt"></a><a name="op_lt"></a>Operátor&lt;

Určuje, zda `thread::id` je jeden objekt menší než jiný.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý `thread::id` objekt.

*Právo*\
Správný `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *Vlevo* předchází *Right* v celkové řazení; jinak **false**.

### <a name="remarks"></a>Poznámky

Operátor definuje celkové řazení na `thread::id` všechny objekty. Tyto objekty lze použít jako klíče v asociativních kontejnerech.

Tato funkce nevyvolá žádné výjimky.

## <a name="operator"></a><a name="op_neq"></a>operátor!=

Porovná dva `thread::id` objekty pro nerovnost.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý `thread::id` objekt.

*Právo*\
Správný `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`!(Left == Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="operator"></a><a name="op_eq_eq"></a>operátor==

Porovná dva `thread::id` objekty rovnosti.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Vlevo*\
Levý `thread::id` objekt.

*Právo*\
Správný `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

**true** pokud dva objekty představují stejné vlákno provádění nebo pokud ani jeden objekt představuje vlákno provádění; jinak **false**.

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="operatorltlt"></a><a name="op_lt_lt"></a>Operátor&lt;&lt;

Vloží textovou reprezentaci objektu `thread::id` do datového proudu.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*\
Objekt [basic_ostream.](../standard-library/basic-ostream-class.md)

*Id*\
Objekt. `thread::id`

### <a name="return-value"></a>Návratová hodnota

*Ostr*.

### <a name="remarks"></a>Poznámky

Tato funkce vloží *Id* do *Ostr*.

Pokud `thread::id` se dva objekty rovnají sobě, jsou vložené textové reprezentace těchto objektů stejné.

## <a name="see-also"></a>Viz také

[\<>vláken](../standard-library/thread.md)
