---
title: time_point – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
dev_langs:
- C++
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::chrono [C++], time_point
ms.workload:
- cplusplus
ms.openlocfilehash: 9e01a168312f83d375f40102705f3ac52138f0eb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="timepoint-class"></a>time_point – třída

A `time_point` popisuje typ, který reprezentuje bod v čase. Drží objekt typu [doba trvání](../standard-library/duration-class.md) , ukládá uplynulý čas od epoch, která je reprezentována argument šablony `Clock`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné – definice TypeDef

|Název|Popis|
|----------|-----------------|
|`time_point::clock`|Synonymum pro parametr šablony `Clock`.|
|`time_point::duration`|Synonymum pro parametr šablony `Duration`.|
|`time_point::period`|Synonymum pro název vnořeného typu `duration::period`.|
|`time_point::rep`|Synonymum pro název vnořeného typu `duration::rep`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[time_point](#time_point)|Vytvoří `time_point` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[max](#max)|Určuje horní omezení pro `time_point::ref`.|
|[Min.](#min)|Určuje dolní limit pro `time_point::ref`.|
|[time_since_epoch](#time_since_epoch)|Vrátí uložené `duration` hodnotu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[time_point::operator+=](#op_add_eq)|Přidá zadanou hodnotu do uložené doba trvání.|
|[time_point::operator-=](#operator-_eq)|Odečte zadanou hodnotu z uložené doba trvání.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typu chrono >

**Namespace:** std::chrono

## <a name="max"></a>  time_point::max –

Statickou metodu, která vrací horní mez pro hodnoty typu `time_point::ref`.

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `time_point(duration::max())`.

## <a name="min"></a>  time_point::min –

Statickou metodu, která vrací dolní mez pro hodnoty typu `time_point::ref`.

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `time_point(duration::min())`.

## <a name="op_add_eq"></a>  time_point::Operator +=

Přidá zadanou hodnotu uložené [doba trvání](../standard-library/duration-class.md) hodnotu.

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`time_point` Objektu po přidání provádí.

## <a name="time_point__operator-_eq"></a>  time_point::Operator-=

Odečte zadanou hodnotu z uložené [doba trvání](../standard-library/duration-class.md) hodnotu.

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`time_point` Objektu po provedení odčítání.

## <a name="time_point"></a>  time_point::time_point – konstruktor

Vytvoří `time_point` objektu.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parametry

`Dur` A [doba trvání](../standard-library/duration-class.md) objektu.

`Tp` A `time_point` objektu.

### <a name="remarks"></a>Poznámky

První konstruktoru vytvoří objekt jehož uložené `duration` hodnota se rovná [DURATION::Zero –](../standard-library/duration-class.md#zero).

Druhý konstruktor vytvoří objekt, jehož uložené trvání hodnota se rovná `Dur`. Pokud `is_convertible<Duration2, duration>` *platí*, druhý konstruktor neúčastní rozlišení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

Třetí konstruktor inicializuje jeho `duration` hodnotu pomocí `Tp.time_since_epoch()`.

## <a name="time_since_epoch"></a>  time_point::time_since_epoch –

Načte uložené [doba trvání](../standard-library/duration-class.md) hodnotu.

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
