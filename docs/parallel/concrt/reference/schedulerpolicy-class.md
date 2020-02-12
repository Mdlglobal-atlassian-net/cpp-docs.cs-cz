---
title: SchedulerPolicy – třída
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: fed33c198502b75e824bcaf698227d283f4b85f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142753"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy – třída

Třída `SchedulerPolicy` obsahuje sadu párů klíč/hodnota, jednu pro každý prvek zásad, která řídí chování instance Scheduleru.

## <a name="syntax"></a>Syntaxe

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Přetíženo. Vytvoří novou zásadu plánovače a naplní je hodnotami pro [klíče zásad](concurrency-namespace-enums.md) podporované Concurrency Runtime plánovači a správce prostředků.|
|[~ SchedulerPolicy destruktor](#dtor)|Odstraní zásady plánovače.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Getpolicyvalue –](#getpolicyvalue)|Načte hodnotu klíče zásad zadanou jako parametr `key`.|
|[SetConcurrencyLimits –](#setconcurrencylimits)|Současně nastavuje `MinConcurrency` a zásady `MaxConcurrency` na objektu `SchedulerPolicy`.|
|[SetPolicyValue –](#setpolicyvalue)|Nastaví hodnotu klíče zásad dodané jako parametr `key` a vrátí starou hodnotu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přiřadí zásadu plánovače z jiné zásady plánovače.|

## <a name="remarks"></a>Poznámky

Další informace o zásadách, které lze řídit pomocí `SchedulerPolicy` třídy, naleznete v tématu [PolicyElementKey –](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SchedulerPolicy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h, concrtrm. h

**Obor názvů:** souběžnost

## <a name="getpolicyvalue"></a>Getpolicyvalue –

Načte hodnotu klíče zásad zadanou jako parametr `key`.

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč zásady, pro který se má načíst hodnota

### <a name="return-value"></a>Návratová hodnota

Pokud je klíč určený parametrem `key` podporován, hodnota zásady pro přetypování klíče na `unsigned int`.

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pro Neplatný klíč zásad.

## <a name="operator_eq"></a>operátor =

Přiřadí zásadu plánovače z jiné zásady plánovače.

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parametry

*_RhsPolicy*<br/>
Zásady, které se mají přiřadit k této zásadě.

### <a name="return-value"></a>Návratová hodnota

Odkaz na zásady plánovače.

### <a name="remarks"></a>Poznámky

Nejpohodlnější způsob, jak definovat nové zásady Scheduleru, je často možnost zkopírovat existující zásadu a upravit ji pomocí `SetPolicyValue` nebo `SetConcurrencyLimits`ch metod.

## <a name="ctor"></a>SchedulerPolicy

Vytvoří novou zásadu plánovače a naplní je hodnotami pro [klíče zásad](concurrency-namespace-enums.md) podporované Concurrency Runtime plánovači a správce prostředků.

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Parametry

*_PolicyKeyCount*<br/>
Počet párů klíč/hodnota, které následují po parametru `_PolicyKeyCount`.

*_SrcPolicy*<br/>
Zdrojové zásady, které se mají zkopírovat

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří novou zásadu plánovače, ve které budou všechny zásady inicializovány na výchozí hodnoty.

Druhý konstruktor vytvoří novou zásadu plánovače, která používá pro inicializaci styl pojmenovaného parametru. Hodnoty za parametrem `_PolicyKeyCount` jsou zadány jako páry klíč/hodnota. Všechny klíče zásad, které nejsou zadány v tomto konstruktoru, budou mít výchozí hodnotu. Tento konstruktor může vyvolat výjimky [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) nebo [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

Třetí konstruktor je kopírovací konstruktor. Nejpohodlnější způsob, jak definovat nové zásady Scheduleru, je často možnost zkopírovat existující zásadu a upravit ji pomocí `SetPolicyValue` nebo `SetConcurrencyLimits`ch metod.

## <a name="dtor"></a>~ SchedulerPolicy

Odstraní zásady plánovače.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a>SetConcurrencyLimits –

Současně nastavuje `MinConcurrency` a zásady `MaxConcurrency` na objektu `SchedulerPolicy`.

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parametry

*_MinConcurrency*<br/>
Hodnota klíče zásad `MinConcurrency`

*_MaxConcurrency*<br/>
Hodnota klíče zásad `MaxConcurrency`

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) , pokud je hodnota zadaná pro `MinConcurrency` zásada větší než zadaná pro `MaxConcurrency` zásady.

Metoda může také vyvolat [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pro jiné neplatné hodnoty.

## <a name="setpolicyvalue"></a>SetPolicyValue –

Nastaví hodnotu klíče zásad dodané jako parametr `key` a vrátí starou hodnotu.

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parametry

*key*<br/>
Klíč zásad pro nastavení hodnoty.

*value*<br/>
Hodnota, na kterou má být klíč zásad nastaven.

### <a name="return-value"></a>Návratová hodnota

Pokud je klíč zadaný parametrem `key` podporovaný, stará hodnota zásad pro přetypování klíče na `unsigned int`.

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) pro Neplatný klíč zásad nebo libovolný klíč zásad, jehož hodnotu nelze nastavit metodou `SetPolicyValue`.

Metoda vyvolá [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) pro hodnotu, která není podporována pro klíč určený parametrem `key`.

Všimněte si, že tato metoda není povolena pro nastavení zásad `MinConcurrency` nebo `MaxConcurrency`. Chcete-li nastavit tyto hodnoty, použijte metodu [SetConcurrencyLimits –](#setconcurrencylimits) .

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[PolicyElementKey –](concurrency-namespace-enums.md)<br/>
[CurrentScheduler – třída](currentscheduler-class.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
