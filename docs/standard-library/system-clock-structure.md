---
title: system_clock – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
dev_langs:
- C++
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 432109ae0c05cb864fe92da405bbaa1e0a9c225f
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="systemclock-structure"></a>system_clock – struktura

Představuje *typ hodin* založený na systému v reálném čase hodiny.

## <a name="syntax"></a>Syntaxe

```cpp
struct system_clock;
```

## <a name="remarks"></a>Poznámky

A *typ hodin* slouží k získání aktuální čas ve formátu UTC. Typ ztělesňuje vytváření instancí z [doba trvání](../standard-library/duration-class.md) a šablona třídy [time_point](../standard-library/time-point-class.md)a definuje statické členské funkce `now()` čas, který vrací.

Hodiny, které je *monotónní* Pokud hodnotu, která je vrácen první volání `now()` je vždy menší než nebo rovna hodnotu, která je vrácena voláním následné `now()`.

Hodiny, které je *konstantní* Pokud je *monotónní* a pokud je doba mezi počtu taktů konstantní.

V této implementaci `system_clock` je totožná s `high_resolution_clock`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné – definice TypeDef

|Název|Popis|
|----------|-----------------|
|`system_clock::duration`|Synonymum pro `duration<rep, period>`.|
|`system_clock::period`|Synonymum pro typ, který se používá k reprezentování období značek v obsažené instance `duration`.|
|`system_clock::rep`|Synonymum pro typ, který se používá k reprezentování počet v omezením instance počtu taktů `duration`.|
|`system_clock::time_point`|Synonymum pro `time_point<Clock, duration>`, kde `Clock` je synonymum pro vlastní typ hodin nebo jiného typu hodiny, který je založen na stejné epoch a má stejné vnořené `duration` typu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[from_time_t](#from_time_t)|Statické. Vrátí `time_point` , nejvíce blíží určitou dobu.|
|[Nyní](#now)|Statické. Vrátí aktuální čas.|
|[to_time_t](#to_time_t)|Statické. Vrátí `time_t` objektu, která nejvíce blíží zadané `time_point`.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[system_clock::is_monotonic Constant](#is_monotonic_constant)|Určuje, zda je typ hodiny monotónní.|
|[system_clock::is_steady – konstanta](#is_steady_constant)|Určuje, jestli je typ hodin konstantní.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<typu chrono >

**Namespace:** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t –

Statickou metodu, která vrací [time_point](../standard-library/time-point-class.md) která nejvíc se blíží čas, která je reprezentována `Tm`.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parametry

`Tm` A [time_t](../c-runtime-library/standard-types.md) objektu.

## <a name="is_monotonic_constant"></a>  system_clock::is_monotonic – konstanta

Statická hodnota, která určuje, jestli je typ hodin monotónní.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Návratová hodnota

V této implementaci `system_clock::is_monotonic` vždy vrátí hodnotu `false`.

### <a name="remarks"></a>Poznámky

Hodiny, které je *monotónní* Pokud hodnotu, která je vrácen první volání `now()` je vždy menší než nebo rovna hodnotu, která je vrácena voláním následné `now()`.

## <a name="is_steady_constant"></a>  system_clock::is_steady – konstanta

Statická hodnota, která určuje, zda je typ hodiny *konstantní*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Návratová hodnota

V této implementaci `system_clock::is_steady` vždy vrátí hodnotu `false`.

### <a name="remarks"></a>Poznámky

Hodiny, které je *konstantní* Pokud je [monotónní](#is_monotonic_constant) a pokud je doba mezi počtu taktů konstantní.

## <a name="now"></a>  system_clock::Now –

Statickou metodu, která vrací aktuální čas.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

A [time_point](../standard-library/time-point-class.md) objekt, který představuje aktuální čas.

## <a name="to_time_t"></a>  system_clock::to_time_t –

Statickou metodu, která vrací [time_t](../c-runtime-library/standard-types.md) která nejvíc se blíží čas, která je reprezentována `Time`.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parametry

`Time` A [time_point](../standard-library/time-point-class.md) objektu.

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[steady_clock – struktura](../standard-library/steady-clock-struct.md)<br/>
