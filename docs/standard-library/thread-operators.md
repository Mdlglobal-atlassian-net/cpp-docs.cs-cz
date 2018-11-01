---
title: '&lt;vlákno&gt; operátory'
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
ms.openlocfilehash: 5a2fd845598ac9f9c983bf53cbd7665ef66ffb70
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636901"
---
# <a name="ltthreadgt-operators"></a>&lt;vlákno&gt; operátory

||||
|-|-|-|
|[operator!=](#op_neq)|[– Operátor&gt;](#op_gt)|[– Operátor&gt;=](#op_gt_eq)|
|[– Operátor&lt;](#op_lt)|[– Operátor&lt;&lt;](#op_lt_lt)|[– Operátor&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|

## <a name="op_gt_eq"></a>  – Operátor&gt;=

Určuje, zda jeden `thread::id` objekt je větší než nebo roven jinému.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé straně `thread::id` objektu.

*doprava*<br/>
Vpravo `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

`!(Left < Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_gt"></a>  – Operátor&gt;

Určuje, zda jeden `thread::id` je větší než jiný objekt.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé straně `thread::id` objektu.

*doprava*<br/>
Vpravo `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

`Right < Left`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt_eq"></a>  – Operátor&lt;=

Určuje, zda jeden `thread::id` je objekt menší než nebo rovna do jiného.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé straně `thread::id` objektu.

*doprava*<br/>
Vpravo `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

`!(Right < Left)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt"></a>  – Operátor&lt;

Určuje, zda jeden `thread::id` je menší než jiný objekt.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé straně `thread::id` objektu.

*doprava*<br/>
Vpravo `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *vlevo* předchází *vpravo* v celkový řazení; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Operátor, který definuje celkový řazení ve všech `thread::id` objekty. Tyto objekty je možné jako klíče v asociativních kontejnerech.

Tato funkce nevyvolá žádné výjimky.

## <a name="op_neq"></a>  Operator! =

Porovná dva `thread::id` objekty nerovnost.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé straně `thread::id` objektu.

*doprava*<br/>
Vpravo `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

`!(Left == Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_eq_eq"></a>  Operator ==

Porovná dva `thread::id` objekty pro rovnost.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*doleva*<br/>
Levé straně `thread::id` objektu.

*doprava*<br/>
Vpravo `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** , zda dva objekty představují stejné vlákno provádění, nebo pokud žádný objekt představuje vlákno provádění; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt_lt"></a>  – Operátor&lt;&lt;

Vloží textové vyjádření `thread::id` objektu do datového proudu.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*<br/>
A [basic_ostream –](../standard-library/basic-ostream-class.md) objektu.

*ID*<br/>
A `thread::id` objektu.

### <a name="return-value"></a>Návratová hodnota

*Ostr*.

### <a name="remarks"></a>Poznámky

Tato funkce vloží *Id* do *Ostr*.

Pokud dvě `thread::id` objekty rovnají, byl vložen text interpretací těchto objektů jsou stejné.

## <a name="see-also"></a>Viz také:

[\<vlákna >](../standard-library/thread.md)<br/>
