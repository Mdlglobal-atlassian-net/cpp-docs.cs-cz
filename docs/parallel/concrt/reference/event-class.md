---
title: event – třída
ms.date: 11/04/2016
f1_keywords:
- event
- CONCRT/concurrency::event
- CONCRT/concurrency::event::reset
- CONCRT/concurrency::event::set
- CONCRT/concurrency::event::wait
- CONCRT/concurrency::event::wait_for_multiple
- CONCRT/concurrency::event::timeout_infinite
helpviewer_keywords:
- event class
ms.assetid: fba35a53-6568-4bfa-9aaf-07c0928cf73d
ms.openlocfilehash: 2c72b4b086e932f4fe404259c25f8d2c8be2be31
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138848"
---
# <a name="event-class"></a>event – třída

Událost ručního resetování, která je výslovně informována o Concurrency Runtime.

## <a name="syntax"></a>Syntaxe

```cpp
class event;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ Event – destruktor](#dtor)|Zničí událost.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[nové](#reset)|Obnoví událost na stav bez signalizace.|
|[set](#set)|Signalizuje událost.|
|[Počkej](#wait)|Čeká, až se událost přestane signalizovat.|
|[wait_for_multiple](#wait_for_multiple)|Čeká, až se zasignalizují více událostí.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Hodnota označující, že čas čekání by neměl nikdy trvat.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Synchronizace datových struktur](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`event`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>událostí

Vytvoří novou událost.

```cpp
_CRTIMP event();
```

### <a name="remarks"></a>Poznámky

## <a name="dtor"></a>~ – událost

Zničí událost.

```cpp
~event();
```

### <a name="remarks"></a>Poznámky

Očekává se, že při spuštění destruktoru nečekají na událost žádná vlákna. Umožnění destrukci události s vlákny, na kterých stále čeká, má za následek nedefinované chování.

## <a name="reset"></a>nové

Obnoví událost na stav bez signalizace.

```cpp
void reset();
```

## <a name="set"></a>stanovenými

Signalizuje událost.

```cpp
void set();
```

### <a name="remarks"></a>Poznámky

Signalizace události může způsobit, že libovolný počet kontextů čeká na událost, která má být spustitelný.

## <a name="timeout_infinite"></a>timeout_infinite

Hodnota označující, že čas čekání by neměl nikdy trvat.

```cpp
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

## <a name="wait"></a>Počkej

Čeká, až se událost přestane signalizovat.

```cpp
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_Timeout*<br/>
Označuje počet milisekund, po jejichž uplynutí vypršel časový limit. Hodnota `COOPERATIVE_TIMEOUT_INFINITE` znamená, že neexistuje žádný časový limit.

### <a name="return-value"></a>Návratová hodnota

Pokud bylo čekání splněno, je vrácena hodnota `0`. v opačném případě hodnota `COOPERATIVE_WAIT_TIMEOUT` označuje, že čekání vypršel časový limit, aniž by došlo k signalizaci události.

> [!IMPORTANT]
> V aplikaci Univerzální platforma Windows (UWP) Nevolejte `wait` ve vlákně ASTA, protože toto volání může zablokovat aktuální vlákno a může způsobit, že aplikace přestane reagovat.

## <a name="wait_for_multiple"></a>wait_for_multiple

Čeká, až se zasignalizují více událostí.

```cpp
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_PPEvents*<br/>
Pole událostí, na které se má čekat. Počet událostí v poli je označen parametrem `count`.

*count*<br/>
Počet událostí v poli, které jsou zadány v parametru `_PPEvents`.

*_FWaitAll*<br/>
Pokud je nastavena na hodnotu **true**, parametr určuje, že všechny události v poli, které jsou zadány v parametru `_PPEvents`, musí být oznámeny, aby bylo možné vyhovět čekání. Pokud je nastavena na hodnotu **false**, určuje, že jakákoli událost v poli, která je uvedena v parametru `_PPEvents` přestala signalizovat, bude vyhovovat čekání.

*_Timeout*<br/>
Označuje počet milisekund, po jejichž uplynutí vypršel časový limit. Hodnota `COOPERATIVE_TIMEOUT_INFINITE` znamená, že neexistuje žádný časový limit.

### <a name="return-value"></a>Návratová hodnota

Pokud bylo čekání splněno, index v poli dodaném v parametru `_PPEvents`, který splnil čekací podmínku; v opačném případě hodnota `COOPERATIVE_WAIT_TIMEOUT` označuje, že čekání vypršela bez splněné podmínky.

### <a name="remarks"></a>Poznámky

Pokud je parametr `_FWaitAll` nastaven na hodnotu `true`, aby označoval, že všechny události musí být signalizaci, aby splňovaly čekání, index vrácený funkcí nepřenese žádný zvláštní význam, než fakt, že se nejedná o hodnotu `COOPERATIVE_WAIT_TIMEOUT`.

> [!IMPORTANT]
> V aplikaci Univerzální platforma Windows (UWP) Nevolejte `wait_for_multiple` ve vlákně ASTA, protože toto volání může zablokovat aktuální vlákno a může způsobit, že aplikace přestane reagovat.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
