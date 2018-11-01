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
ms.openlocfilehash: 323b9a6e2c46bea8d82f0f589d1174041c1f0780
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480103"
---
# <a name="event-class"></a>event – třída

Ruční obnovení události, která je explicitně vědoma souběžnosti modulu runtime.

## <a name="syntax"></a>Syntaxe

```
class event;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ event – destruktor](#dtor)|Zničí událost.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Resetovat](#reset)|Obnoví událost do nesignálového stavu.|
|[set](#set)|Signalizuje událost.|
|[Počkej](#wait)|Čeká na signálování události.|
|[wait_for_multiple](#wait_for_multiple)|Čeká na signálování více událostí.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[timeout_infinite](#timeout_infinite)|Hodnota označující, že čekání by nemělo nikdy vypršet.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [synchronizačních datových struktur](../../../parallel/concrt/synchronization-data-structures.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`event`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> Události

Vytvoří novou událost.

```
_CRTIMP event();
```

### <a name="remarks"></a>Poznámky

##  <a name="dtor"></a> ~ události

Zničí událost.

```
~event();
```

### <a name="remarks"></a>Poznámky

Očekává se, že neexistují žádná vlákna čekající na událost při spuštění destruktoru. Povolení událostí k destrukci pomocí vláken, která stále čekají způsobí nedefinované chování.

##  <a name="reset"></a> Resetovat

Obnoví událost do nesignálového stavu.

```
void reset();
```

##  <a name="set"></a> Nastavit

Signalizuje událost.

```
void set();
```

### <a name="remarks"></a>Poznámky

Signalizace události může způsobit, že libovolný počet kontextů čekat na spustitelnost události.

##  <a name="timeout_infinite"></a> timeout_infinite

Hodnota označující, že čekání by nemělo nikdy vypršet.

```
static const unsigned int timeout_infinite = COOPERATIVE_TIMEOUT_INFINITE;
```

##  <a name="wait"></a> Počkej

Čeká na signálování události.

```
size_t wait(unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_Vypršení časového limitu*<br/>
Určuje počet milisekund před vypršením čekání. Hodnota `COOPERATIVE_TIMEOUT_INFINITE` znamená, že neexistuje žádný časový limit.

### <a name="return-value"></a>Návratová hodnota

Pokud bylo čekání splněno, hodnota `0` je vrácena; jinak hodnota `COOPERATIVE_WAIT_TIMEOUT` k označení, že vypršení čekání bez signalizace události.

> [!IMPORTANT]
>  V aplikaci pro univerzální platformu Windows (UPW), nevolejte `wait` na ASTA vlákno, protože toto volání může blokovat aktuální vlákno a může způsobit, že aplikace přestane reagovat.

##  <a name="wait_for_multiple"></a> wait_for_multiple –

Čeká na signálování více událostí.

```
static size_t __cdecl wait_for_multiple(
    _In_reads_(count) event** _PPEvents,
    size_t count,
    bool _FWaitAll,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*_PPEvents*<br/>
Pole událostí pro čekání. Počet událostí v poli je indikován `count` parametru.

*Počet*<br/>
Počet událostí v poli v `_PPEvents` parametru.

*_FWaitAll*<br/>
Pokud nastaveno na hodnotu **true**, parametr určuje, že všechny události v poli dodané v `_PPEvents` parametr musí být signalizovány, aby vyhověly čekání. Pokud nastaveno na hodnotu **false**, určuje, že všechny události v poli dodané v `_PPEvents` parametr stávají signalizovanými vyhoví čekání.

*_Vypršení časového limitu*<br/>
Určuje počet milisekund před vypršením čekání. Hodnota `COOPERATIVE_TIMEOUT_INFINITE` znamená, že neexistuje žádný časový limit.

### <a name="return-value"></a>Návratová hodnota

Pokud bylo čekání uspokojeno, index v poli dodané v `_PPEvents` parametr, který splnil čekací podmínku; v opačném případě hodnota `COOPERATIVE_WAIT_TIMEOUT` k označení, že vypršení čekání bez splnění podmínky.

### <a name="remarks"></a>Poznámky

Pokud parametr `_FWaitAll` je nastaveno na hodnotu `true` k označení, že všechny události musí být signalizovány, aby splnily čekání, index vrácený funkcí nemá žádný speciální význam mimo skutečnost, že není hodnota `COOPERATIVE_WAIT_TIMEOUT`.

> [!IMPORTANT]
> V aplikaci pro univerzální platformu Windows (UPW), nevolejte `wait_for_multiple` na ASTA vlákno, protože toto volání může blokovat aktuální vlákno a může způsobit, že aplikace přestane reagovat.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
