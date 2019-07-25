---
title: system_clock – struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 7a9fd83840883de5172df8b2e1e451984a95ea47
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450180"
---
# <a name="systemclock-structure"></a>system_clock – struktura

Představuje *typ hodin* , který je založen na hodinách systému v reálném čase.

## <a name="syntax"></a>Syntaxe

```cpp
struct system_clock;
```

## <a name="remarks"></a>Poznámky

*Typ hodin* slouží k získání aktuálního času jako UTC. Typ vytvoří instanci instance [Trvání](../standard-library/duration-class.md) a šablonu třídy [time_point](../standard-library/time-point-class.md)a definuje statickou členskou funkci `now()` , která vrátí čas.

Hodiny jsou *monotónní* , pokud hodnota, která je vrácena prvním voláním `now()` , je vždy menší než nebo rovna hodnotě, která je vrácena následným voláním metody. `now()`

Hodiny jsou *stabilní* , pokud jsou *monotónní* , a pokud je čas mezi takty konstantní.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|`system_clock::duration`|Synonymum pro `duration<rep, period>`.|
|`system_clock::period`|Synonymum pro typ, který se používá k reprezentaci období Tick v uzavřeném vytváření instancí `duration`.|
|`system_clock::rep`|Synonymum pro typ, který představuje počet taktů v uzavřeném vytváření instancí `duration`.|
|`system_clock::time_point`|Synonymum pro `time_point<Clock, duration>`, kde `Clock` je synonymum pro buď typ hodin samotný, nebo jiný typ hodin, který je založen na stejném epocha a má stejný vnořený `duration` typ.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[from_time_t](#from_time_t)|Tras. `time_point` Vrátí, který nejlépe vyblíží zadaný čas.|
|[současné](#now)|Tras. Vrátí aktuální čas.|
|[to_time_t](#to_time_t)|Tras. Vrátí objekt, který nejlépe seblíží zadanou `time_point`hodnotu. `time_t`|

### <a name="public-constants"></a>Veřejné konstanty

|Name|Popis|
|----------|-----------------|
|[system_clock::is_monotonic Constant](#is_monotonic_constant)|Určuje, zda je typ hodin monotónní.|
|[system_clock:: is_steady – konstanta](#is_steady_constant)|Určuje, zda je typ hodin konstantní.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<Chrono >

**Obor názvů:** std:: chrono

## <a name="from_time_t"></a>system_clock::from_time_t

Statická metoda, která vrací [time_point](../standard-library/time-point-class.md) , který nejlépe odpovídá času reprezentovanému *TM*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parametry

*TM*\
Objekt [time_t](../c-runtime-library/standard-types.md) .

## <a name="is_monotonic_constant"></a>system_clock:: is_monotonic – konstanta

Statická hodnota, která určuje, zda je typ hodin monotónní.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Návratová hodnota

V této implementaci `system_clock::is_monotonic` vždy vrátí **hodnotu false**.

### <a name="remarks"></a>Poznámky

Hodiny jsou *monotónní* , pokud hodnota, která je vrácena prvním voláním `now()` , je vždy menší než nebo rovna hodnotě, která je vrácena následným voláním metody. `now()`

## <a name="is_steady_constant"></a>system_clock:: is_steady – konstanta

Statická hodnota, která určuje, zda je typ hodin *konstantní*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Návratová hodnota

V této implementaci `system_clock::is_steady` vždy vrátí **hodnotu false**.

### <a name="remarks"></a>Poznámky

Hodiny jsou *stabilní* , pokud jsou [monotónní](#is_monotonic_constant) , a pokud je čas mezi takty konstantní.

## <a name="now"></a>system_clock:: Now

Statická metoda, která vrací aktuální čas.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [time_point](../standard-library/time-point-class.md) , který představuje aktuální čas.

## <a name="to_time_t"></a>system_clock::to_time_t

Statická metoda, která vrací [time_t](../c-runtime-library/standard-types.md) , který nejlépe odpovídá času reprezentovanému *časem*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parametry

*Interval*\
Objekt [time_point](../standard-library/time-point-class.md) .

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[steady_clock – struktura](../standard-library/steady-clock-struct.md)
