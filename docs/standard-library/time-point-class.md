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
ms.openlocfilehash: e1de674d4a13ba465100923bffe6cba76e61ab4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368032"
---
# <a name="time_point-class"></a>time_point – třída

A `time_point` popisuje typ, který představuje bod v čase. Obsahuje objekt typu [trvání,](../standard-library/duration-class.md) který ukládá uplynulý čas od epochy, `Clock`která je reprezentována argumentem šablony .

## <a name="syntax"></a>Syntaxe

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`time_point::clock`|Synonymum pro `Clock`parametr šablony .|
|`time_point::duration`|Synonymum pro `Duration`parametr šablony .|
|`time_point::period`|Synonymum pro vnořený název `duration::period`typu .|
|`time_point::rep`|Synonymum pro vnořený název `duration::rep`typu .|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[time_point](#time_point)|Vytvoří `time_point` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Max](#max)|Určuje horní limit `time_point::ref`pro program .|
|[Min](#min)|Určuje dolní limit `time_point::ref`pro program .|
|[time_since_epoch](#time_since_epoch)|Vrátí uloženou `duration` hodnotu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[time_point::operátor+=](#op_add_eq)|Přidá zadanou hodnotu do uložené doby trvání.|
|[time_point::operátor-=](#operator-_eq)|Odečte zadanou hodnotu od uložené doby trvání.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono>

**Obor názvů:** std::chrono

## <a name="time_pointmax"></a><a name="max"></a>time_point::max

Statická metoda, která vrací horní `time_point::ref`mez pro hodnoty typu .

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Návratová hodnota

Ve skutečnosti `time_point(duration::max())`vrátí .

## <a name="time_pointmin"></a><a name="min"></a>time_point::min

Statická metoda, která vrací dolní `time_point::ref`mez pro hodnoty typu .

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Návratová hodnota

Ve skutečnosti `time_point(duration::min())`vrátí .

## <a name="time_pointoperator"></a><a name="op_add_eq"></a>time_point::operátor+=

Přidá zadanou hodnotu k uložené hodnotě [doby trvání.](../standard-library/duration-class.md)

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Objekt. `duration`

### <a name="return-value"></a>Návratová hodnota

Objekt `time_point` po přidání se provádí.

## <a name="time_pointoperator-"></a><a name="operator-_eq"></a>time_point::operátor-=

Odečte zadanou hodnotu od uložené hodnoty [doby trvání.](../standard-library/duration-class.md)

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Objekt. `duration`

### <a name="return-value"></a>Návratová hodnota

Objekt `time_point` po odčítání je provedena.

## <a name="time_pointtime_point-constructor"></a><a name="time_point"></a>time_point::time_point konstruktor

Vytvoří `time_point` objekt.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Objekt [doby trvání.](../standard-library/duration-class.md)

*Tp*\
Objekt. `time_point`

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, `duration` jehož uložená hodnota se rovná [duration::zero](../standard-library/duration-class.md#zero).

Druhý konstruktor vytvoří objekt, jehož uložená hodnota doby trvání se rovná *Dur*. Pokud `is_convertible<Duration2, duration>` platí, druhý konstruktor se neúčastní řešení přetížení. Další informace naleznete [v tématu<type_traits>](../standard-library/type-traits.md).

Třetí konstruktor inicializuje `duration` svou `Tp.time_since_epoch()`hodnotu pomocí .

## <a name="time_pointtime_since_epoch"></a><a name="time_since_epoch"></a>time_point::time_since_epoch

Načte uloženou hodnotu [doby trvání.](../standard-library/duration-class.md)

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
