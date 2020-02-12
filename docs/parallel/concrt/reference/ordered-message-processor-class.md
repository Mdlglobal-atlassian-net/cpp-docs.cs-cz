---
title: ordered_message_processor – třída
ms.date: 11/04/2016
f1_keywords:
- ordered_message_processor
- AGENTS/concurrency::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::ordered_message_processor
- AGENTS/concurrency::ordered_message_processor::async_send
- AGENTS/concurrency::ordered_message_processor::initialize
- AGENTS/concurrency::ordered_message_processor::initialize_batched_processing
- AGENTS/concurrency::ordered_message_processor::sync_send
- AGENTS/concurrency::ordered_message_processor::wait
- AGENTS/concurrency::ordered_message_processor::process_incoming_message
helpviewer_keywords:
- ordered_message_processor class
ms.assetid: 787adfb7-7f79-4a70-864a-80e3b64088cd
ms.openlocfilehash: ea9ca799f36cac0d843a578eb7cef9c1e9c5cda6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138785"
---
# <a name="ordered_message_processor-class"></a>ordered_message_processor – třída

`ordered_message_processor` je `message_processor`, která umožňuje blokům zpráv zpracovávat zprávy v pořadí, v jakém byly přijaty.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class ordered_message_processor : public message_processor<T>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ datové části zpráv zpracovávaných procesorem.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[ordered_message_processor](#ctor)|Vytvoří objekt `ordered_message_processor`.|
|[~ ordered_message_processor destruktor](#dtor)|Odstraní objekt `ordered_message_processor`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[async_send](#async_send)|Asynchronně zařadí zprávy do fronty a spustí úlohu zpracování, pokud to ještě nebylo provedeno. (Potlačení [message_processor:: async_send](message-processor-class.md#async_send).)|
|[spuštění](#initialize)|Inicializuje objekt `ordered_message_processor` pomocí příslušné funkce zpětného volání, skupiny Scheduler a plánu.|
|[initialize_batched_processing](#initialize_batched_processing)|Inicializovat zpracování dávkové zprávy|
|[sync_send](#sync_send)|Synchronně zařadí zprávy do fronty a spustí úlohu zpracování, pokud tato operace ještě nebyla dokončena. (Potlačení [message_processor:: sync_send](message-processor-class.md#sync_send).)|
|[Počkej](#wait)|Čekání na procesory specifické pro procesor se používá v destruktorech bloků zpráv, aby bylo zajištěno, že všechny úlohy asynchronního zpracování budou mít čas na dokončení před zničením bloku. (Potlačení [message_processor:: wait](message-processor-class.md#wait))|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Funkce zpracování, která se nazývá asynchronně. Vyřadí zprávy a začne je zpracovávat. (Overrides [message_processor::p rocess_incoming_message](message-processor-class.md#process_incoming_message).)|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[message_processor](message-processor-class.md)

`ordered_message_processor`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="async_send"></a>async_send

Asynchronně zařadí zprávy do fronty a spustí úlohu zpracování, pokud to ještě nebylo provedeno.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Ukazatel na zprávu.

## <a name="initialize"></a>spuštění

Inicializuje objekt `ordered_message_processor` pomocí příslušné funkce zpětného volání, skupiny Scheduler a plánu.

```cpp
void initialize(
    _Inout_opt_ Scheduler* _PScheduler,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup,
    _Handler_method const& _Handler);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Ukazatel na Plánovač, který se má použít pro plánování úloh s nejvyšší váhou.

*_PScheduleGroup*<br/>
Ukazatel na skupinu plánování, která se má použít pro plánování úloh s nejvyšší váhou.

*_Handler*<br/>
Obslužná rutina funktor vyvolala během zpětného volání.

## <a name="initialize_batched_processing"></a>initialize_batched_processing

Inicializovat zpracování dávkové zprávy

```cpp
virtual void initialize_batched_processing(
    _Handler_method const& _Processor,
    _Propagator_method const& _Propagator);
```

### <a name="parameters"></a>Parametry

*_Processor*<br/>
Procesor funktor vyvolal během zpětného volání.

*_Propagator*<br/>
Modul pro šíření funktor vyvolal během zpětného volání.

## <a name="ctor"></a>ordered_message_processor

Vytvoří objekt `ordered_message_processor`.

```cpp
ordered_message_processor();
```

### <a name="remarks"></a>Poznámky

Tato `ordered_message_processor` nebude plánovat asynchronní nebo synchronní obslužné rutiny, dokud není volána funkce `initialize`.

## <a name="dtor"></a>~ ordered_message_processor

Odstraní objekt `ordered_message_processor`.

```cpp
virtual ~ordered_message_processor();
```

### <a name="remarks"></a>Poznámky

Čeká na všechny nedokončené asynchronní operace před zničením procesoru.

## <a name="process_incoming_message"></a>process_incoming_message

Funkce zpracování, která se nazývá asynchronně. Vyřadí zprávy a začne je zpracovávat.

```cpp
virtual void process_incoming_message();
```

## <a name="sync_send"></a>sync_send

Synchronně zařadí zprávy do fronty a spustí úlohu zpracování, pokud tato operace ještě nebyla dokončena.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Ukazatel na zprávu.

## <a name="wait"></a>Počkej

Čekání na procesory specifické pro procesor se používá v destruktorech bloků zpráv, aby bylo zajištěno, že všechny úlohy asynchronního zpracování budou mít čas na dokončení před zničením bloku.

```cpp
virtual void wait();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
