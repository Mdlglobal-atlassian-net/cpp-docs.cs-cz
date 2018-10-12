---
title: accelerator_view – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 30eb0befda4d439bf4153d7c6726c982d3bf19ae
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163332"
---
# <a name="acceleratorview-class"></a>accelerator_view – třída

Představuje abstrakci virtuálního zařízení v akcelerátoru paralelních dat knihovny C++ AMP.

### <a name="syntax"></a>Syntaxe

```
class accelerator_view;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[accelerator_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator_view` třídy.|
|[~ accelerator_view – destruktor](#dtor)|Odstraní `accelerator_view` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[create_marker](#create_marker)|Vrátí objekt future ke sledování dokončení všech příkazů dosud zaslaných tomuto `accelerator_view` objektu.|
|[Vyprázdnění](#flush)|Odešle všechny příkazy čekající ve frontě `accelerator_view` objekt akcelerátoru ke spuštění.|
|[get_accelerator](#get_accelerator)|Vrátí `accelerator` objekt pro `accelerator_view` objektu.|
|[get_is_auto_selection](#get_is_auto_selection)|Vrátí logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátor při `accelerator_view` objekt je předán [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Vrátí logickou hodnotu, která určuje, zda `accelerator_view` objekt má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.|
|[get_queuing_mode –](#get_queuing_mode)|Vrátí režim zařazování do fronty pro `accelerator_view` objektu.|
|[get_version –](#get_version)|Vrátí verzi `accelerator_view`.|
|[Počkej](#wait)|Čeká na všech příkazů zaslaných `accelerator_view` objektu na dokončení.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porovná tento `accelerator_view` objekt s jiným a vrátí **false** případě, že jsou totožné; v opačném případě vrátí **true**.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `accelerator_view` do tohoto objektu.|
|[operator==](#operator_eq_eq)|Porovná tento `accelerator_view` objekt s jiným a vrátí **true** případě, že jsou totožné; v opačném případě vrátí **false**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[akcelerátor](#accelerator)|Získá `accelerator` objekt pro `accelerator_view` objektu.|
|[is_auto_selection](#is_auto_selection)|Získá logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátor při `accelerator_view` objekt je předán [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Získá logickou hodnotu, která určuje, zda `accelerator_view` objekt má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.|
|[queuing_mode –](#queuing_mode)|Načte režim zařazování do fronty pro `accelerator_view` objektu.|
|[version](#version)|Získá verzi accelerator.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`accelerator_view`

### <a name="remarks"></a>Poznámky

`accelerator_view` Objekt představuje logický, izolovaný pohled na akcelerátor. Jedno fyzické výpočetní zařízení může mít mnoho logických, izolovaných `accelerator_view` objekty. Každý akcelerátor má výchozí `accelerator_view` objektu. Další `accelerator_view` objekty mohou být vytvořeny.

Fyzická zařízení lze sdílet mezi mnoha vlákny klienta. Vlákna klienta můžete kooperativně používat stejné `accelerator_view` objekt akcelerátoru nebo každý klient může komunikovat s výpočetním zařízením prostřednictvím nezávislého `accelerator_view` objektu pro izolaci od ostatních vláken klienta.

`accelerator_view` Může nabývat jednoho ze dvou [queuing_mode – výčet](concurrency-namespace-enums-amp.md#queuing_mode) stavy. Pokud je režim zařazování do fronty `immediate`, příkazy jako `copy` a `parallel_for_each` odesílány příslušnému akceleračnímu zařízení poté, co vrátí volajícímu. Pokud je režim zařazování do fronty `deferred`, jsou takové příkazy zařazeny příkazové fronty odpovídající `accelerator_view` objektu. Příkazy ve skutečnosti neodešlou do zařízení, dokud `flush()` je volána.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** souběžnosti

## <a name="accelerator"></a> akcelerátor

Získá objekt akcelerátoru pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a> accelerator_view

Inicializuje novou instanci třídy accelerator_view zkopírováním existující `accelerator_view` objektu.

### <a name="syntax"></a>Syntaxe

```
accelerator_view( const accelerator_view & _Other );
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objektu, který chcete zkopírovat.

## <a name="accelerator_view__create_marker"></a> create_marker

Vrátí objekt future ke sledování dokončení všech příkazů dosud zaslaných tomuto `accelerator_view` objektu.

### <a name="syntax"></a>Syntaxe

```
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Návratová hodnota

Objekt future ke sledování dokončení všech příkazů dosud zaslaných tomuto `accelerator_view` objektu.

## <a name="flush"></a> Vyprázdnění

Odesílá se, že všechny příkazy čekající ve frontě objektu accelerator_view akcelerátoru ke spuštění.

### <a name="syntax"></a>Syntaxe

```
void flush();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí `void`.

## <a name="accelerator_view__get_accelerator"></a> get_accelerator –

Vrátí objekt akcelerátoru pro objekt accelerator_view.
### <a name="syntax"></a>Syntaxe

```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>Návratová hodnota

Objekt akcelerátoru pro objekt accelerator_view.

## <a name="accelerator_view__get_is_auto_selection"></a> get_is_auto_selection

Vrátí logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátor Pokud je předán accelerator_view [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud modul runtime automaticky vybere odpovídající akcelerátor; v opačném případě **false**.

## <a name="accelerator_view__get_is_debug"></a> get_is_debug –

Vrátí logickou hodnotu, která určuje, zda má objekt accelerator_view povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

### <a name="syntax"></a>Syntaxe

```
bool get_is_debug() const;
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která určuje, zda `accelerator_view` objekt má povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

## <a name="accelerator_view__get_queuing_mode"></a> get_queuing_mode –

Vrátí režim zařazování do fronty pro daný objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Návratová hodnota

Režim zařazování do fronty pro `accelerator_view` objektu.

## <a name="accelerator_view__get_version"></a> get_version –

Vrátí verzi objektu accelerator_view.

### <a name="syntax"></a>Syntaxe

```
unsigned int get_version() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze `accelerator_view`.

## <a name="accelerator_view__is_auto_selection"></a> is_auto_selection

Získá logickou hodnotu, která určuje, zda modul runtime automaticky vybere odpovídající akcelerátor Pokud je předán accelerator_view [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="accelerator_view__is_debug"></a> is_debug –

Získá logickou hodnotu, která určuje, zda má objekt accelerator_view povolenu vrstvu DEBUG pro rozsáhlé hlášení chyb.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="accelerator_view__operator_neq"></a> Operator! =

Porovná tento objekt accelerator_view s jiným a vrátí **false** případě, že jsou totožné; v opačném případě vrátí **true**.

### <a name="syntax"></a>Syntaxe

```
bool operator!= (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objekt k porovnání s touto položkou.

### <a name="return-value"></a>Návratová hodnota

**false** Pokud jsou oba objekty stejné; jinak **true**.

## <a name="accelerator_view__operator_eq"></a> operátor =

Zkopíruje obsah objektu pro zadaný accelerator_view do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```
accelerator_view & operator= (    const accelerator_view & _Other );
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na upravené `accelerator_view` objektu.

## <a name="accelerator_view__operator_eq_eq"></a> Operator ==

Porovná tento objekt accelerator_view s jiným a vrátí **true** případě, že jsou totožné; v opačném případě vrátí **false**.

### <a name="syntax"></a>Syntaxe

```
bool operator= = (    const accelerator_view & _Other ) const;
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`accelerator_view` Objekt k porovnání s touto položkou.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud jsou oba objekty stejné; jinak **false**.

## <a name="accelerator_view__queuing_mode"></a> queuing_mode –

Načte režim zařazování do fronty pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="accelerator_view__version"></a> Verze

Získá verzi accelerator_view.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="accelerator_view__wait"></a> Počkej

Čeká se na všech příkazů zaslaných objektu accelerator_view dokončit.

### <a name="syntax"></a>Syntaxe

```
void wait();
```

#### <a name="return-value"></a>Návratová hodnota

Vrátí `void`.

#### <a name="remarks"></a>Poznámky

Pokud [queuing_mode –](concurrency-namespace-enums-amp.md#queuing_mode) je `immediate`, tato metoda vrátí hodnotu okamžitě bez blokování.

##  <a name="dtor"></a> ~ accelerator_view

Odstraní objekt accelerator_view.

#### <a name="syntax"></a>Syntaxe

```
~accelerator_view();
```

### <a name="return-value"></a>Návratová hodnota

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
