---
title: operátory&gt; &lt;vlákna
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
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876165"
---
# <a name="ltthreadgt-operators"></a>operátory&gt; &lt;vlákna

||||
|-|-|-|
|[operator!=](#op_neq)|[operátor&gt;](#op_gt)|[operátor&gt;=](#op_gt_eq)|
|[operátor&lt;](#op_lt)|[operátor&lt;&lt;](#op_lt_lt)|[operátor&lt;=](#op_lt_eq)|
|[operator = = – operátor](#op_eq_eq)|

## <a name="op_gt_eq"></a>operátor&gt;=

Určuje, zda je jeden objekt `thread::id` větší nebo roven jinému.

```cpp
bool operator>= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt `thread::id`.

*Pravé*\
Pravý objekt `thread::id`.

### <a name="return-value"></a>Návratová hodnota

`!(Left < Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_gt"></a>operátor&gt;

Určuje, zda je jeden objekt `thread::id` větší než jiný.

```cpp
bool operator> (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt `thread::id`.

*Pravé*\
Pravý objekt `thread::id`.

### <a name="return-value"></a>Návratová hodnota

`Right < Left`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt_eq"></a>operátor&lt;=

Určuje, zda je jeden objekt `thread::id` menší nebo roven jinému.

```cpp
bool operator<= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt `thread::id`.

*Pravé*\
Pravý objekt `thread::id`.

### <a name="return-value"></a>Návratová hodnota

`!(Right < Left)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt"></a>operátor&lt;

Určuje, zda je jeden objekt `thread::id` menší než jiný objekt.

```cpp
bool operator<(
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt `thread::id`.

*Pravé*\
Pravý objekt `thread::id`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud *vlevo* předchází *právo* v celkovém pořadí; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Operátor definuje celkové řazení u všech objektů `thread::id`. Tyto objekty lze použít jako klíče v asociativních kontejnerech.

Tato funkce nevyvolá žádné výjimky.

## <a name="op_neq"></a>! = – operátor

Porovná dva objekty `thread::id` pro nerovnost.

```cpp
bool operator!= (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt `thread::id`.

*Pravé*\
Pravý objekt `thread::id`.

### <a name="return-value"></a>Návratová hodnota

`!(Left == Right)`

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_eq_eq"></a>operator = = – operátor

Porovná dva objekty `thread::id` k rovnosti.

```cpp
bool operator== (
    thread::id Left,
    thread::id Right) noexcept
```

### <a name="parameters"></a>Parametry

*Levý*\
Levý objekt `thread::id`.

*Pravé*\
Pravý objekt `thread::id`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud dva objekty představují stejné vlákno provedení nebo pokud žádný objekt nepředstavuje vlákno provedení; v opačném případě **false**.

### <a name="remarks"></a>Poznámky

Tato funkce nevyvolá žádné výjimky.

## <a name="op_lt_lt"></a>operátor&lt;&lt;

Vloží do datového proudu textovou reprezentaci objektu `thread::id`.

```cpp
template <class Elem, class Tr>
basic_ostream<Elem, Tr>& operator<<(
    basic_ostream<Elem, Tr>& Ostr, thread::id Id);
```

### <a name="parameters"></a>Parametry

*Ostr*\
Objekt [basic_ostream](../standard-library/basic-ostream-class.md) .

*Id*\
Objekt `thread::id`.

### <a name="return-value"></a>Návratová hodnota

*OSTR*.

### <a name="remarks"></a>Poznámky

Tato funkce vloží *ID* do *OSTR*.

Pokud se dva `thread::id` objekty rovnají, jsou vložené textové reprezentace těchto objektů stejné.

## <a name="see-also"></a>Viz také

[> \<vlákna](../standard-library/thread.md)
