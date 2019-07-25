---
title: time_point – třída
ms.date: 03/27/2019
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
helpviewer_keywords:
- std::chrono [C++], time_point
ms.openlocfilehash: 4511c7b2d8629f1a052137c7997daf5913c976ab
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459990"
---
# <a name="timepoint-class"></a>time_point – třída

`time_point` Popisuje typ, který představuje bod v čase. Obsahuje objekt typu [Duration](../standard-library/duration-class.md) , který ukládá uplynulý čas od epocha, který je reprezentován argumentem `Clock`šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|`time_point::clock`|Synonymum pro parametr `Clock`šablony|
|`time_point::duration`|Synonymum pro parametr `Duration`šablony|
|`time_point::period`|Synonymum pro název `duration::period`vnořeného typu|
|`time_point::rep`|Synonymum pro název `duration::rep`vnořeného typu|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[time_point](#time_point)|`time_point` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[max](#max)|Určuje horní mez pro `time_point::ref`.|
|[dlouhé](#min)|Určuje dolní mez pro `time_point::ref`.|
|[time_since_epoch](#time_since_epoch)|Vrátí uloženou `duration` hodnotu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[time_point::operator+=](#op_add_eq)|Přidá zadanou hodnotu k uložené hodnotě Duration.|
|[time_point::operator-=](#operator-_eq)|Odečte zadanou hodnotu od uložené doby trvání.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<Chrono >

**Obor názvů:** std:: chrono

## <a name="max"></a>time_point:: max

Statická metoda, která vrátí horní mez pro hodnoty typu `time_point::ref`.

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `time_point(duration::max())`.

## <a name="min"></a>time_point:: min

Statická metoda, která vrátí dolní mez pro hodnoty typu `time_point::ref`.

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `time_point(duration::min())`.

## <a name="op_add_eq"></a>time_point:: operator + =

Přidá zadanou hodnotu k uložené hodnotě [Duration](../standard-library/duration-class.md) .

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba*\
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`time_point` Objekt po provedení přidání.

## <a name="operator-_eq"></a>time_point:: operator-=

Odečte zadanou hodnotu od uložené hodnoty [Duration](../standard-library/duration-class.md) .

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba*\
A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`time_point` Objekt po odčítání.

## <a name="time_point"></a>time_point:: time_point – konstruktor

`time_point` Vytvoří objekt.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parametry

*Doba*\
Objekt [Duration](../standard-library/duration-class.md) .

*Transakční program*\
A `time_point` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, jehož uložená `duration` hodnota se rovná [Duration:: Zero](../standard-library/duration-class.md#zero).

Druhý konstruktor vytvoří objekt, jehož uložená hodnota trvání je rovna *dur*. `is_convertible<Duration2, duration>` Není-li true, druhý konstruktor není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

Třetí konstruktor inicializuje svoji `duration` hodnotu pomocí. `Tp.time_since_epoch()`

## <a name="time_since_epoch"></a>time_point::time_since_epoch

Načte uloženou hodnotu [Duration](../standard-library/duration-class.md) .

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
