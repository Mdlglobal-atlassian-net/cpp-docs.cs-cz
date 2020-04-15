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
ms.openlocfilehash: ca516551bb1b41d96b99aaf7b842666c9341ee7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376516"
---
# <a name="system_clock-structure"></a>system_clock – struktura

Představuje *typ hodiny,* který je založen na hodiny v reálném čase systému.

## <a name="syntax"></a>Syntaxe

```cpp
struct system_clock;
```

## <a name="remarks"></a>Poznámky

*Typ hodiny* se používá k získání aktuálního času jako UTC. Typ ztělesňuje konkretizaci [doby trvání](../standard-library/duration-class.md) a šablonu třídy [time_point](../standard-library/time-point-class.md)a definuje statickou členskou funkci, `now()` která vrací čas.

Hodiny je *monotónní,* pokud je hodnota, která `now()` je vrácena první volání je vždy menší nebo `now()`rovna hodnotu, která je vrácena následné volání .

Hodiny jsou *stabilní,* pokud jsou *monotónní* a pokud je doba mezi hodinami konstantní.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|`system_clock::duration`|Synonymum `duration<rep, period>`pro .|
|`system_clock::period`|Synonymum pro typ, který se používá k reprezentaci `duration`období značek v obsažené konkretiaci .|
|`system_clock::rep`|Synonymum pro typ, který se používá k reprezentaci počtu značek `duration`hodin v obsažené konkretiaci .|
|`system_clock::time_point`|Synonymum `time_point<Clock, duration>`pro `Clock` , kde je synonymum pro samotný typ hodin nebo jiný typ hodin, `duration` který je založen na stejné epochě a má stejný vnořený typ.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[from_time_t](#from_time_t)|Statická. Vrátí `time_point` hodnotu, která se nejvíce blíží zadanému času.|
|[Nwo](#now)|Statická. Vrátí aktuální čas.|
|[to_time_t](#to_time_t)|Statická. Vrátí `time_t` objekt, který se nejvíce `time_point`blíží zadanému .|

### <a name="public-constants"></a>Veřejné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[system_clock::is_monotonic konstanta](#is_monotonic_constant)|Určuje, zda je typ hodin monotónní.|
|[system_clock::is_steady konstanta](#is_steady_constant)|Určuje, zda je typ hodin stabilní.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<chrono>

**Obor názvů:** std::chrono

## <a name="system_clockfrom_time_t"></a><a name="from_time_t"></a>system_clock::from_time_t

Statická metoda, která vrací [time_point,](../standard-library/time-point-class.md) která nejvíce blíží čas, který je reprezentován *Tm*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parametry

*Tm*\
[Objekt time_t.](../c-runtime-library/standard-types.md)

## <a name="system_clockis_monotonic-constant"></a><a name="is_monotonic_constant"></a>system_clock::is_monotonic konstanta

Statická hodnota, která určuje, zda je typ hodin monotónní.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Návratová hodnota

V této `system_clock::is_monotonic` implementaci vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

Hodiny je *monotónní,* pokud je hodnota, která `now()` je vrácena první volání je vždy menší nebo `now()`rovna hodnotu, která je vrácena následné volání .

## <a name="system_clockis_steady-constant"></a><a name="is_steady_constant"></a>system_clock::is_steady konstanta

Statická hodnota, která určuje, zda je typ hodin *stabilní*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Návratová hodnota

V této `system_clock::is_steady` implementaci vždy vrátí **false**.

### <a name="remarks"></a>Poznámky

Hodiny jsou *stabilní,* pokud jsou [monotónní](#is_monotonic_constant) a pokud je doba mezi hodinami konstantní.

## <a name="system_clocknow"></a><a name="now"></a>system_clock::Nyní

Statická metoda, která vrací aktuální čas.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [time_point,](../standard-library/time-point-class.md) který představuje aktuální čas.

## <a name="system_clockto_time_t"></a><a name="to_time_t"></a>system_clock::to_time_t

Statická metoda, která vrací [time_t,](../c-runtime-library/standard-types.md) která nejvíce blíží čas, který je reprezentován *Time*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parametry

*Čas*\
[Objekt time_point.](../standard-library/time-point-class.md)

## <a name="see-also"></a>Viz také

[Odkaz na soubory záhlaví](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[steady_clock – struktura](../standard-library/steady-clock-struct.md)
