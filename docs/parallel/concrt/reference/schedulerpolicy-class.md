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
ms.openlocfilehash: 0d1c28501abc86d09b683b0ed91f831fe8697306
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462048"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy – třída

`SchedulerPolicy` Třída obsahuje sadu párů klíč/hodnota, jeden pro každý prvek zásad, které řídí chování instance plánovače.

## <a name="syntax"></a>Syntaxe

```
class SchedulerPolicy;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Schedulerpolicy –](#ctor)|Přetíženo. Vytvoří novou zásadu plánovače a naplní ji hodnotami pro [klíče zásad](concurrency-namespace-enums.md) podporované plánovači Concurrency Runtime a správce prostředků.|
|[~SchedulerPolicy Destructor](#dtor)|Odstraní zásadu plánovače.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Getpolicyvalue –](#getpolicyvalue)|Načte hodnotu klíče zásad zadaný jako `key` parametru.|
|[Setconcurrencylimits –](#setconcurrencylimits)|Zároveň nastaví `MinConcurrency` a `MaxConcurrency` zásady `SchedulerPolicy` objektu.|
|[Setpolicyvalue –](#setpolicyvalue)|Nastaví hodnotu klíče zásad zadaný jako `key` parametr a vrátí původní hodnotu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Přiřadí zásadu plánovače z jiné zásady plánovače.|

## <a name="remarks"></a>Poznámky

Další informace o zásadách, které se dá řídit pomocí `SchedulerPolicy` najdete v tématu [policyelementkey –](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`SchedulerPolicy`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h, concrtrm.h

**Namespace:** souběžnosti

##  <a name="getpolicyvalue"></a> Getpolicyvalue –

Načte hodnotu klíče zásad zadaný jako `key` parametru.

```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč zásad načíst hodnotu.

### <a name="return-value"></a>Návratová hodnota

Pokud klíč určené `key` je podporován, zásady hodnotu pro klíč přetypovat na `unsigned int`.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_scheduler_policy_key –](invalid-scheduler-policy-key-class.md) neplatná zásada klíče.

##  <a name="operator_eq"></a> operátor =

Přiřadí zásadu plánovače z jiné zásady plánovače.

```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parametry

*_RhsPolicy*<br/>
Zásady, které chcete přiřadit tuto zásadu.

### <a name="return-value"></a>Návratová hodnota

Odkaz na zásadu plánovače.

### <a name="remarks"></a>Poznámky

Často je nejpohodlnější způsob, jak definovat novou zásadu plánovače zkopírovat existující zásadu a upravit ji pomocí `SetPolicyValue` nebo `SetConcurrencyLimits` metody.

##  <a name="ctor"></a> Schedulerpolicy –

Vytvoří novou zásadu plánovače a naplní ji hodnotami pro [klíče zásad](concurrency-namespace-enums.md) podporované plánovači Concurrency Runtime a správce prostředků.

```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Parametry

*_PolicyKeyCount*<br/>
Dvojice klíč/hodnota číslo, které následují `_PolicyKeyCount` parametru.

*_SrcPolicy*<br/>
Zdrojové zásady ke kopírování.

### <a name="remarks"></a>Poznámky

První konstruktor vytvoří novou zásadu plánovače, kde všechny zásady budou inicializovány na výchozí hodnoty.

Druhý konstruktor vytvoří novou zásadu plánovače, která používá styl inicializace s pojmenovaným parametrem. Hodnoty po `_PolicyKeyCount` parametru jsou dodávány jako dvojice klíč/hodnota. Všechny klíče zásad, které není zadané v tomto konstruktoru bude mít výchozí hodnotu. Tento konstruktor může vyvolat výjimky [invalid_scheduler_policy_key –](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value –](invalid-scheduler-policy-value-class.md) nebo [invalid_scheduler_policy_thread_specification –](invalid-scheduler-policy-thread-specification-class.md).

Třetí konstruktor je kopírovací konstruktor. Často je nejpohodlnější způsob, jak definovat novou zásadu plánovače zkopírovat existující zásadu a upravit ji pomocí `SetPolicyValue` nebo `SetConcurrencyLimits` metody.

##  <a name="dtor"></a> ~ Schedulerpolicy –

Odstraní zásadu plánovače.

```
~SchedulerPolicy();
```

##  <a name="setconcurrencylimits"></a> Setconcurrencylimits –

Zároveň nastaví `MinConcurrency` a `MaxConcurrency` zásady `SchedulerPolicy` objektu.

```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parametry

*_MinConcurrency*<br/>
Hodnota `MinConcurrency` klíče zásad.

*_MaxConcurrency*<br/>
Hodnota `MaxConcurrency` klíče zásad.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_scheduler_policy_thread_specification –](invalid-scheduler-policy-thread-specification-class.md) Pokud je hodnota zadaná u `MinConcurrency` je větší než zadaná pro zásady `MaxConcurrency` zásad.

Můžete také vyvolat metodu [invalid_scheduler_policy_value –](invalid-scheduler-policy-value-class.md) další neplatné hodnoty.

##  <a name="setpolicyvalue"></a> Setpolicyvalue –

Nastaví hodnotu klíče zásad zadaný jako `key` parametr a vrátí původní hodnotu.

```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parametry

*Klíč*<br/>
Klíč zásad a nastavit hodnotu pro.

*value*<br/>
Hodnota k nastavení klíče zásad pro.

### <a name="return-value"></a>Návratová hodnota

Pokud klíč určené `key` je podporován, původní hodnota zásady pro klíč přetypovat na `unsigned int`.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_scheduler_policy_key –](invalid-scheduler-policy-key-class.md) klíčem neplatná zásada nebo všechny klíče zásad, jehož hodnota nelze nastavit `SetPolicyValue` metody.

Metoda vyvolá výjimku [invalid_scheduler_policy_value –](invalid-scheduler-policy-value-class.md) na hodnotu, která není podporována pro určený klíč `key` parametru.

Všimněte si, že tato metoda není možné nastavit `MinConcurrency` nebo `MaxConcurrency` zásady. Chcete-li nastavit tyto hodnoty, použijte [setconcurrencylimits –](#setconcurrencylimits) metody.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Policyelementkey –](concurrency-namespace-enums.md)<br/>
[CurrentScheduler – třída](currentscheduler-class.md)<br/>
[Scheduler – třída](scheduler-class.md)<br/>
[Plánovač úloh](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

