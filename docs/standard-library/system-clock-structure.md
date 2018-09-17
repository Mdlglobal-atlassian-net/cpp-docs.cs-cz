---
title: system_clock – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 146a764cd2b1fcc567a564a6995c191c4f838262
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722225"
---
# <a name="systemclock-structure"></a>system_clock – struktura

Představuje *typ hodin* , který je založen na reálného času systému.

## <a name="syntax"></a>Syntaxe

```cpp
struct system_clock;
```

## <a name="remarks"></a>Poznámky

A *typ hodin* slouží k získání aktuálního času UTC. Typ ztělesňuje instanci [doba trvání](../standard-library/duration-class.md) a šablonu třídy [time_point](../standard-library/time-point-class.md)a definuje statickou členskou funkci `now()` , který vrací čas.

Hodiny jsou *monotónní* Pokud hodnotu, která je vrácena prvním voláním do `now()` je vždy menší než hodnota, která je vrácena následujícím voláním do `now()`.

Hodiny jsou *stabilní* jde *monotónní* a je-li doba mezi cykly hodin konstantní.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`system_clock::duration`|Synonymum pro `duration<rep, period>`.|
|`system_clock::period`|Synonymum pro typ, který se používá k počet dob taktů v uzavřeném vytváření instancí `duration`.|
|`system_clock::rep`|Synonymum pro typ, který reprezentuje počet taktů v uzavřeném vytváření instancí `duration`.|
|`system_clock::time_point`|Synonymum pro `time_point<Clock, duration>`, kde `Clock` je synonymum pro typ hodin sám nebo jiný typ hodin, který je založen na stejném období a má stejný vnořený `duration` typu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[from_time_t](#from_time_t)|Statické. Vrátí `time_point` , který nejvíce přibližuje zadanému času.|
|[Nyní](#now)|Statické. Vrátí aktuální čas.|
|[to_time_t](#to_time_t)|Statické. Vrátí `time_t` objekt, který se nejvíce přibližuje zadanému `time_point`.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[system_clock::is_monotonic Constant](#is_monotonic_constant)|Určuje, zda je typ hodin monotónní.|
|[system_clock::is_steady – konstanta](#is_steady_constant)|Určuje, zda je typ hodin konstantní.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono >

**Namespace:** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t –

Statická metoda, která se vrátí [time_point](../standard-library/time-point-class.md) , který nejlépe přibližuje čas reprezentovaný *Tm*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parametry

*TM*<br/>
A [time_t](../c-runtime-library/standard-types.md) objektu.

## <a name="is_monotonic_constant"></a>  system_clock::is_monotonic – konstanta

Statická hodnota, která určuje, zda je typ hodin monotónní.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Návratová hodnota

V této implementaci `system_clock::is_monotonic` vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

Hodiny jsou *monotónní* Pokud hodnotu, která je vrácena prvním voláním do `now()` je vždy menší než hodnota, která je vrácena následujícím voláním do `now()`.

## <a name="is_steady_constant"></a>  system_clock::is_steady – konstanta

Statická hodnota, která určuje, zda je typ hodin *stabilní*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Návratová hodnota

V této implementaci `system_clock::is_steady` vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

Hodiny jsou *stabilní* jde [monotónní](#is_monotonic_constant) a je-li doba mezi cykly hodin konstantní.

## <a name="now"></a>  system_clock::Now –

Statická metoda, která vrací aktuální čas.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

A [time_point](../standard-library/time-point-class.md) objekt, který představuje aktuální čas.

## <a name="to_time_t"></a>  system_clock::to_time_t –

Statická metoda, která se vrátí [time_t](../c-runtime-library/standard-types.md) , který nejlépe přibližuje čas reprezentovaný *čas*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parametry

*čas*<br/>
A [time_point](../standard-library/time-point-class.md) objektu.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[steady_clock – struktura](../standard-library/steady-clock-struct.md)<br/>
