---
title: '&lt;operátory&gt; vlákna'
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
ms.openlocfilehash: c0593b8016cf45abe64114958ccda84eb3704844
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458445"
---
# <a name="ltthreadgt-operators"></a>&lt;operátory&gt; vlákna

||||
|-|-|-|
|[operator!=](#op_neq)|[podnikatel&gt;](#op_gt)|[podnikatel&gt;=](#op_gt_eq)|
|[podnikatel&lt;](#op_lt)|[podnikatel&lt;&lt;](#op_lt_lt)|[podnikatel&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a>podnikatel&gt;=

Určuje, zda `thread::id` je jeden objekt větší nebo roven jinému objektu.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Zbývá*\
Levý `thread::id` objekt

*Kliknutím*\
Pravý `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`!(Left < Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_gt"></a>podnikatel&gt;

Určuje, zda `thread::id` je jeden objekt větší než jiný.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Zbývá*\
Levý `thread::id` objekt

*Kliknutím*\
Pravý `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`Right < Left`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt_eq"></a>podnikatel&lt;=

Určuje, zda `thread::id` je jeden objekt menší nebo roven jinému objektu.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Zbývá*\
Levý `thread::id` objekt

*Kliknutím*\
Pravý `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`!(Right < Left)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt"></a>podnikatel&lt;

Určuje, zda `thread::id` je jeden objekt menší než jiný.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Zbývá*\
Levý `thread::id` objekt

*Kliknutím*\
Pravý `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud *vlevo* předchází *právo* v celkovém pořadí; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Operátor definuje celkové řazení pro všechny `thread::id` objekty. Tyto objekty lze použít jako klíče v asociativních kontejnerech.

Tato funkce nevyvolá žádné výjimky.

## <a name="op_neq"></a>! = – operátor

Porovná `thread::id` dva objekty pro nerovnost.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Zbývá*\
Levý `thread::id` objekt

*Kliknutím*\
Pravý `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

`!(Left == Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_eq_eq"></a>operator = = – operátor

Porovná `thread::id` dva objekty pro rovnost.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Zbývá*\
Levý `thread::id` objekt

*Kliknutím*\
Pravý `thread::id` objekt.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud dva objekty představují stejné vlákno provedení nebo pokud žádný objekt nepředstavuje vlákno provedení; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt_lt"></a>podnikatel&lt;&lt;

Vloží textovou reprezentaci `thread::id` objektu do datového proudu.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*\
Objekt [basic_ostream](../standard-library/basic-ostream-class.md) .

*Účet*\
A `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

*OSTR*.

### <a name="remarks"></a>Poznámky

Tato funkce vloží *ID* do *OSTR*.

Pokud se `thread::id` dva objekty rovnají, jsou vložené textové reprezentace těchto objektů stejné.

## <a name="see-also"></a>Viz také:

[\<> vlákna](../standard-library/thread.md)
