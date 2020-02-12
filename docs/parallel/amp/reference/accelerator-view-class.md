---
title: accelerator_view – třída
ms.date: 03/27/2019
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view::accelerator_view
- AMPRT/Concurrency::accelerator_view::create_marker
- AMPRT/Concurrency::accelerator_view::flush
- AMPRT/Concurrency::accelerator_view::get_accelerator
- AMPRT/Concurrency::accelerator_view::get_is_auto_selection
- AMPRT/Concurrency::accelerator_view::get_is_debug
- AMPRT/Concurrency::accelerator_view::get_queuing_mode
- AMPRT/Concurrency::accelerator_view::get_version
- AMPRT/Concurrency::accelerator_view::wait
- AMPRT/Concurrency::accelerator_view::accelerator
- AMPRT/Concurrency::accelerator_view::is_auto_selection
- AMPRT/Concurrency::accelerator_view::is_debug
- AMPRT/Concurrency::accelerator_view::queuing_mode
- AMPRT/Concurrency::accelerator_view::version
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
ms.openlocfilehash: 8990566fb3a700d61de324f725dea3ec00006d04
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127173"
---
# <a name="accelerator_view-class"></a>accelerator_view – třída

Představuje abstrakci virtuálního zařízení v akcelerátoru C++ paralelního zpracování dat amp.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator_view;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[accelerator_view – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator_view`.|
|[~ accelerator_view destruktor](#dtor)|Odstraní objekt `accelerator_view`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[create_marker](#create_marker)|Vrátí budoucnost pro sledování dokončení všech příkazů odeslaných zatím do tohoto objektu `accelerator_view`.|
|[zaznamenány](#flush)|Odešle všechny čekající příkazy zařazené do objektu `accelerator_view` do akcelerátoru pro spuštění.|
|[get_accelerator](#get_accelerator)|Vrátí objekt `accelerator` pro objekt `accelerator_view`.|
|[get_is_auto_selection](#get_is_auto_selection)|Vrací logickou hodnotu, která označuje, zda modul runtime automaticky vybere vhodný akcelerátor, pokud je objekt `accelerator_view` předán do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Vrací logickou hodnotu, která označuje, zda objekt `accelerator_view` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.|
|[get_queuing_mode](#get_queuing_mode)|Vrátí režim zařazování do fronty pro objekt `accelerator_view`.|
|[get_version](#get_version)|Vrátí verzi `accelerator_view`.|
|[Počkej](#wait)|Čeká na dokončení všech příkazů odeslaných do objektu `accelerator_view`.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)|Porovná tento objekt `accelerator_view` s jiným objektem a vrátí **hodnotu false** , pokud jsou stejné. v opačném případě vrátí **hodnotu true**.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `accelerator_view` do tohoto objektu.|
|[operator = = – operátor](#operator_eq_eq)|Porovná tento objekt `accelerator_view` s jiným objektem a vrátí **hodnotu true** , pokud jsou stejné. v opačném případě vrátí **hodnotu false**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[Accelerator](#accelerator)|Získá objekt `accelerator` pro objekt `accelerator_view`.|
|[is_auto_selection](#is_auto_selection)|Získá logickou hodnotu, která označuje, zda modul runtime automaticky vybere odpovídající akcelerátor, pokud je objekt `accelerator_view` předán do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Získá logickou hodnotu, která označuje, zda objekt `accelerator_view` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.|
|[queuing_mode](#queuing_mode)|Načte režim zařazování do fronty pro objekt `accelerator_view`.|
|[version](#version)|Získá verzi akcelerátoru.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`accelerator_view`

### <a name="remarks"></a>Poznámky

Objekt `accelerator_view` představuje logické a izolované zobrazení akcelerátoru. Jedno fyzické výpočetní zařízení může mít mnoho logických, izolovaných `accelerator_view` objektů. Každý akcelerátor má výchozí objekt `accelerator_view`. Lze vytvořit další objekty `accelerator_view`.

Fyzická zařízení lze sdílet mezi mnoha klientskými vlákny. Klientská vlákna můžou v družstvu používat stejný objekt `accelerator_view` akcelerátoru, nebo každý klient může komunikovat s výpočetním zařízením prostřednictvím nezávislého objektu `accelerator_view` pro izolaci od ostatních klientských vláken.

Objekt `accelerator_view` může mít jeden ze dvou stavů [výčtu queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) . Pokud je režim služby Řízení front `immediate`, příkazy jako `copy` a `parallel_for_each` se odesílají do odpovídajícího zařízení akcelerátoru, jakmile se vrátí volajícímu. Pokud je režim služby Řízení front `deferred`, jsou tyto příkazy zařazené do fronty příkazů, které odpovídají objektu `accelerator_view`. Příkazy se ve skutečnosti neodesílají do zařízení, dokud se nevolá `flush()`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency

## <a name="accelerator"></a>Accelerator

Získá objekt akcelerátoru pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="ctor"></a>accelerator_view

Inicializuje novou instanci třídy accelerator_view zkopírováním existujícího objektu `accelerator_view`.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Objekt `accelerator_view` ke zkopírování.

## <a name="create_marker"></a>create_marker

Vrátí budoucnost pro sledování dokončení všech příkazů odeslaných zatím do tohoto objektu `accelerator_view`.

### <a name="syntax"></a>Syntaxe

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Návratová hodnota

Budoucí sledování dokončení všech příkazů odeslaných zatím tomuto objektu `accelerator_view`.

## <a name="flush"></a>flush

Odešle všechny čekající příkazy zařazené do objektu accelerator_view do akcelerátoru pro spuštění.

### <a name="syntax"></a>Syntaxe

```cpp
void flush();
```

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `void`.

## <a name="get_accelerator"></a>get_accelerator

Vrátí objekt akcelerátoru pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt akcelerátoru pro objekt accelerator_view.

## <a name="get_is_auto_selection"></a>get_is_auto_selection

Vrací logickou hodnotu, která označuje, zda modul runtime automaticky vybere vhodný akcelerátor, pokud je accelerator_view předán do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud bude modul runtime automaticky vybírat příslušný akcelerátor; v opačném případě **false**.

## <a name="get_is_debug"></a>get_is_debug

Vrací logickou hodnotu, která označuje, zda objekt accelerator_view má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která označuje, zda objekt `accelerator_view` má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.

## <a name="get_queuing_mode"></a>get_queuing_mode

Vrátí režim zařazování do fronty pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Návratová hodnota

Režim zařazování do fronty pro objekt `accelerator_view`.

## <a name="get_version"></a>get_version

Vrátí verzi accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze `accelerator_view`.

## <a name="is_auto_selection"></a>is_auto_selection

Získá logickou hodnotu, která označuje, zda modul runtime automaticky vybere odpovídající akcelerátor, pokud je accelerator_view předán do [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a>is_debug

Získá logickou hodnotu, která označuje, zda objekt accelerator_view má povolenou vrstvu ladění pro rozsáhlé hlášení chyb.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator_neq"></a>! = – operátor

Porovná tento objekt accelerator_view s jiným objektem a vrátí **hodnotu false** , pokud jsou stejné. v opačném případě vrátí **hodnotu true**.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Objekt `accelerator_view`, který se má porovnat s tímto.

### <a name="return-value"></a>Návratová hodnota

**false** , pokud jsou tyto dva objekty stejné; v opačném případě **true**.

## <a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného objektu accelerator_view do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Objekt `accelerator_view`, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na upravený objekt `accelerator_view`.

## <a name="operator_eq_eq"></a>operator = = – operátor

Porovná tento objekt accelerator_view s jiným objektem a vrátí **hodnotu true** , pokud jsou stejné. v opačném případě vrátí **hodnotu false**.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Objekt `accelerator_view`, který se má porovnat s tímto.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou tyto dva objekty stejné; v opačném případě **false**.

## <a name="queuing_mode"></a>queuing_mode

Načte režim zařazování do fronty pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>Verze nástroje

Získá verzi accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>Počkej

Čeká na dokončení všech příkazů odeslaných do objektu accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
void wait();
```

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `void`.

### <a name="remarks"></a>Poznámky

Pokud je [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) `immediate`, vrátí tato metoda okamžitě bez blokování.

## <a name="dtor"></a>~ accelerator_view

Odstraní objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
