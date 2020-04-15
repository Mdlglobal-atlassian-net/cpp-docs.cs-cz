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
ms.openlocfilehash: f3be8cc3ab9a0f36027cc38c88f026570d1fdb55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370891"
---
# <a name="accelerator_view-class"></a>accelerator_view – třída

Představuje abstrakce virtuálního zařízení na paralelním akcelerátoru dat C++ AMP.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator_view;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[konstruktor accelerator_view](#ctor)|Inicializuje novou instanci třídy. `accelerator_view`|
|[~accelerator_view Destruktor](#dtor)|Zničí `accelerator_view` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[create_marker](#create_marker)|Vrátí budoucnost ke sledování dokončení všech příkazů, které `accelerator_view` byly dosud odeslány k tomuto objektu.|
|[flush](#flush)|Odešle všechny čekající příkazy `accelerator_view` zařazené do fronty do objektu akcelerátoru ke spuštění.|
|[get_accelerator](#get_accelerator)|Vrátí `accelerator` objekt pro `accelerator_view` objekt.|
|[get_is_auto_selection](#get_is_auto_selection)|Vrátí logickou hodnotu, která označuje, zda modul runtime `accelerator_view` automaticky vybere příslušný akcelerátor, když je objekt předán [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[get_is_debug](#get_is_debug)|Vrátí logickou hodnotu, `accelerator_view` která označuje, zda má objekt povolenou vrstvu LADĚNÍ pro rozsáhlé zasílání zpráv o chybách.|
|[get_queuing_mode](#get_queuing_mode)|Vrátí režim `accelerator_view` řazení objektu do fronty.|
|[get_version](#get_version)|Vrátí verzi souboru `accelerator_view`.|
|[Počkej](#wait)|Čeká na dokončení všech příkazů `accelerator_view` odeslaných do objektu.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[operátor!=](#operator_neq)|Porovná tento `accelerator_view` objekt s jiným a vrátí **false,** pokud jsou stejné; v opačném případě vrátí **hodnotu true**.|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `accelerator_view` objektu do tohoto objektu.|
|[operátor==](#operator_eq_eq)|Porovná tento `accelerator_view` objekt s jiným a vrátí **hodnotu true,** pokud jsou stejné; v opačném případě vrátí **hodnotu false**.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[Accelerator](#accelerator)|Získá `accelerator` objekt pro `accelerator_view` objekt.|
|[is_auto_selection](#is_auto_selection)|Získá logickou hodnotu, která označuje, zda modul runtime `accelerator_view` automaticky vybere příslušný akcelerátor, když je objekt předán [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|
|[is_debug](#is_debug)|Získá logickou hodnotu, `accelerator_view` která označuje, zda má objekt povolenou vrstvu LADĚNÍ pro rozsáhlé zasílání zpráv o chybách.|
|[queuing_mode](#queuing_mode)|Získá režim řazení do `accelerator_view` fronty pro objekt.|
|[Verze](#version)|Získá verzi akcelerátoru.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`accelerator_view`

### <a name="remarks"></a>Poznámky

Objekt `accelerator_view` představuje logické, izolované zobrazení akcelerátoru. Jedno fyzické výpočetní zařízení může mít `accelerator_view` mnoho logických, izolovaných objektů. Každý akcelerátor `accelerator_view` má výchozí objekt. Další `accelerator_view` objekty mohou být vytvořeny.

Fyzická zařízení mohou být sdílena mezi mnoha vlákny klienta. Klientské podprocesy mohou `accelerator_view` kooperativně používat stejný objekt akcelerátoru nebo každý `accelerator_view` klient může komunikovat s výpočetním zařízením prostřednictvím nezávislého objektu pro izolaci od jiných vláken klienta.

Objekt `accelerator_view` může mít jeden ze dvou [stavů výčtu queuing_mode.](concurrency-namespace-enums-amp.md#queuing_mode) Pokud je `immediate`režim řazení do fronty `copy` `parallel_for_each` , příkazy jako a jsou odesílány do odpovídajícíakcelerátoru, jakmile se vrátí volajícímu. Pokud je `deferred`režim řazení do fronty , jsou tyto příkazy zařazeny `accelerator_view` do fronty příkazů, která odpovídá objektu. Příkazy nejsou ve skutečnosti odesílány do zařízení, dokud `flush()` není volána.

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Obor názvů:** Souběžnost

## <a name="accelerator"></a><a name="accelerator"></a>Accelerator

Získá objekt akcelerátoru pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;
```

## <a name="accelerator_view"></a><a name="ctor"></a>accelerator_view

Inicializuje novou instanci třídy accelerator_view `accelerator_view` zkopírováním existujícího objektu.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Objekt, `accelerator_view` který chcete zkopírovat.

## <a name="create_marker"></a><a name="create_marker"></a>create_marker

Vrátí budoucnost ke sledování dokončení všech příkazů, které `accelerator_view` byly dosud odeslány k tomuto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
concurrency::completion_future create_marker();
```

### <a name="return-value"></a>Návratová hodnota

Budoucnost sledovat dokončení všech příkazů, které byly `accelerator_view` dosud odeslány k tomuto objektu.

## <a name="flush"></a>flush

Odešle všechny čekající příkazy zařazené do accelerator_view objektu akcelerátoru ke spuštění.

### <a name="syntax"></a>Syntaxe

```cpp
void flush();
```

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `void`.

## <a name="get_accelerator"></a><a name="get_accelerator"></a>get_accelerator

Vrátí objekt akcelerátoru pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator get_accelerator() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt akcelerátoru pro objekt accelerator_view.

## <a name="get_is_auto_selection"></a><a name="get_is_auto_selection"></a>get_is_auto_selection

Vrátí logickou hodnotu, která označuje, zda modul runtime automaticky vybere příslušný akcelerátor, když je accelerator_view předán [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_auto_selection() const;
```

### <a name="return-value"></a>Návratová hodnota

**true,** pokud modul runtime automaticky vybere vhodný akcelerátor; jinak **false**.

## <a name="get_is_debug"></a><a name="get_is_debug"></a>get_is_debug

Vrátí logickou hodnotu, která označuje, zda má objekt accelerator_view povolenou vrstvu LADĚNÍ pro rozsáhlé zasílání zpráv o chybách.

### <a name="syntax"></a>Syntaxe

```cpp
bool get_is_debug() const;
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která `accelerator_view` označuje, zda má objekt povolenou vrstvu LADĚNÍ pro rozsáhlé zasílání zpráv o chybách.

## <a name="get_queuing_mode"></a><a name="get_queuing_mode"></a>get_queuing_mode

Vrátí režim řazení accelerator_view objektu.

### <a name="syntax"></a>Syntaxe

```cpp
queuing_mode get_queuing_mode() const;
```

### <a name="return-value"></a>Návratová hodnota

Režim `accelerator_view` řazení objektu do fronty.

## <a name="get_version"></a><a name="get_version"></a>get_version

Vrátí verzi accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned int get_version() const;
```

### <a name="return-value"></a>Návratová hodnota

Verze . `accelerator_view`

## <a name="is_auto_selection"></a><a name="is_auto_selection"></a>is_auto_selection

Získá logickou hodnotu, která označuje, zda modul runtime automaticky vybere příslušný akcelerátor, když je accelerator_view předán [a parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;
```

## <a name="is_debug"></a><a name="is_debug"></a>is_debug

Získá logickou hodnotu, která označuje, zda má objekt accelerator_view povolenou vrstvu DEBUG pro rozsáhlé zasílání zpráv o chybách.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_is_debug)) bool is_debug;
```

## <a name="operator"></a><a name="operator_neq"></a>operátor!=

Porovná tento accelerator_view objekt s jiným a vrátí **false,** pokud jsou stejné; v opačném případě vrátí **hodnotu true**.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator!= ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Objekt `accelerator_view` porovnat s tímto jeden.

### <a name="return-value"></a>Návratová hodnota

**false,** pokud dva objekty jsou stejné; jinak **true**.

## <a name="operator"></a><a name="operator_eq"></a>operátor =

Zkopíruje obsah zadaného accelerator_view objektu do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
accelerator_view & operator= ( const accelerator_view & other );
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Objekt, `accelerator_view` ze který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na změněný `accelerator_view` objekt.

## <a name="operator"></a><a name="operator_eq_eq"></a>operátor==

Porovná tento accelerator_view objekt s jiným a vrátí **hodnotu true,** pokud jsou stejné; v opačném případě vrátí **hodnotu false**.

### <a name="syntax"></a>Syntaxe

```cpp
bool operator== ( const accelerator_view & other ) const;
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Objekt `accelerator_view` porovnat s tímto jeden.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud jsou oba objekty stejné; jinak **false**.

## <a name="queuing_mode"></a><a name="queuing_mode"></a>queuing_mode

Získá režim řazení do fronty pro objekt accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;
```

## <a name="version"></a>version

Získá verzi accelerator_view.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_version)) unsigned int version;
```

## <a name="wait"></a>Počkej

Čeká na dokončení všech příkazů odeslaných do accelerator_view objektu.

### <a name="syntax"></a>Syntaxe

```cpp
void wait();
```

### <a name="return-value"></a>Návratová hodnota

Vrací objekt `void`.

### <a name="remarks"></a>Poznámky

Pokud [je](concurrency-namespace-enums-amp.md#queuing_mode) `immediate`queuing_mode , tato metoda vrátí okamžitě bez blokování.

## <a name="accelerator_view"></a><a name="dtor"></a>~accelerator_view

Zničí accelerator_view objekt.

### <a name="syntax"></a>Syntaxe

```cpp
~accelerator_view();
```

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
