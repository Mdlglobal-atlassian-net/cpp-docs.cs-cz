---
title: time_point – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::chrono [C++], time_point
ms.workload:
- cplusplus
ms.openlocfilehash: 99209063e8856ffe9ea26ffaaf0917e1f6cd487b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954257"
---
# <a name="timepoint-class"></a>time_point – třída

A `time_point` popisuje typ, který představuje bod v čase. Obsahuje objekt typu [doba trvání](../standard-library/duration-class.md) , který ukládá čas uběhlý od epochy, která je reprezentována argument šablony `Clock`.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

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
|[max](#max)|Určuje horní mez pro `time_point::ref`.|
|[min](#min)|Určuje dolní mez pro `time_point::ref`.|
|[time_since_epoch](#time_since_epoch)|Vrátí uloženou `duration` hodnotu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[time_point::operator+=](#op_add_eq)|Přidá zadanou hodnotu k uložené hodnotě trvání.|
|[time_point::operator-=](#operator-_eq)|Odečte zadanou hodnotu od uložené hodnoty duration.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

**Namespace:** std::chrono

## <a name="max"></a>  time_point::max –

Statická metoda, která vrátí horní mez pro hodnoty typu `time_point::ref`.

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `time_point(duration::max())`.

## <a name="min"></a>  time_point::min –

Statická metoda, která vrátí dolní mez pro hodnoty typu `time_point::ref`.

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Návratová hodnota

V důsledku toho vrátí `time_point(duration::min())`.

## <a name="op_add_eq"></a>  time_point::Operator +=

Přidá zadanou hodnotu k uložené [doba trvání](../standard-library/duration-class.md) hodnotu.

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba trvání*  
 A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`time_point` Objektu po provedení sčítání.

## <a name="time_point__operator-_eq"></a>  time_point::Operator-=

Odečte zadanou hodnotu od uložené [doba trvání](../standard-library/duration-class.md) hodnotu.

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Doba trvání*  
 A `duration` objektu.

### <a name="return-value"></a>Návratová hodnota

`time_point` Objektu po provedení odečtení.

## <a name="time_point"></a>  time_point::time_point – konstruktor

Vytvoří `time_point` objektu.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parametry

*Doba trvání*  
 A [doba trvání](../standard-library/duration-class.md) objektu.

*Zpracování transakcí*  
 A `time_point` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří objekt, jehož uložené `duration` hodnota se rovná [duration::zero](../standard-library/duration-class.md#zero).

Druhý konstruktor vytvoří objekt, jehož uložená hodnota trvání je rovna *doba trvání*. Není-li `is_convertible<Duration2, duration>` *platí*, druhý konstruktor není součástí řešení přetížení. Další informace najdete v tématu [< type_traits >](../standard-library/type-traits.md).

Třetí konstruktor inicializuje jeho `duration` hodnotu s použitím `Tp.time_since_epoch()`.

## <a name="time_since_epoch"></a>  time_point::time_since_epoch –

Načte uloženou [doba trvání](../standard-library/duration-class.md) hodnotu.

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
