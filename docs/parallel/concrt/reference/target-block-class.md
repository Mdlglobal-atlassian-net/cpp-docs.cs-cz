---
title: target_block – třída
ms.date: 11/04/2016
f1_keywords:
- target_block
- AGENTS/concurrency::target_block
- AGENTS/concurrency::target_block::target_block
- AGENTS/concurrency::target_block::propagate
- AGENTS/concurrency::target_block::send
- AGENTS/concurrency::target_block::async_send
- AGENTS/concurrency::target_block::decline_incoming_messages
- AGENTS/concurrency::target_block::enable_batched_processing
- AGENTS/concurrency::target_block::initialize_target
- AGENTS/concurrency::target_block::link_source
- AGENTS/concurrency::target_block::process_input_messages
- AGENTS/concurrency::target_block::process_message
- AGENTS/concurrency::target_block::propagate_message
- AGENTS/concurrency::target_block::register_filter
- AGENTS/concurrency::target_block::remove_sources
- AGENTS/concurrency::target_block::send_message
- AGENTS/concurrency::target_block::sync_send
- AGENTS/concurrency::target_block::unlink_source
- AGENTS/concurrency::target_block::unlink_sources
- AGENTS/concurrency::target_block::wait_for_async_sends
helpviewer_keywords:
- target_block class
ms.assetid: 3ce181b4-b94a-4894-bf7b-64fc09821f9f
ms.openlocfilehash: 4009133161133a99aeb0ee040f0c82fdbabecaa0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142644"
---
# <a name="target_block-class"></a>target_block – třída

Třída `target_block` je abstraktní základní třída, která poskytuje základní funkce pro správu odkazů a kontrolu chyb pouze pro cílové bloky.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>Parametry

*_SourceLinkRegistry*<br/>
Registr odkazů, který se má použít pro uchovávání zdrojových odkazů.

*_MessageProcessorType*<br/>
Typ procesoru pro zpracování zprávy.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`source_iterator`|Typ iterátoru pro `source_link_manager` pro tento objekt `target_block`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[target_block](#ctor)|Vytvoří objekt `target_block`.|
|[~ target_block destruktor](#dtor)|Odstraní objekt `target_block`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[šířit](#propagate)|Asynchronně předává zprávu ze zdrojového bloku do tohoto cílového bloku.|
|[posílají](#send)|Synchronně předává zprávu ze zdrojového bloku do tohoto cílového bloku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[async_send](#async_send)|Asynchronně pošle zprávu ke zpracování.|
|[decline_incoming_messages](#decline_incoming_messages)|Označuje blok, že by se měly odmítnout nové zprávy.|
|[enable_batched_processing](#enable_batched_processing)|Povolí dávkové zpracování pro tento blok.|
|[initialize_target](#initialize_target)|Inicializuje základní objekt. Konkrétně je nutné inicializovat objekt `message_processor`.|
|[link_source](#link_source)|Propojí zadaný zdrojový blok s tímto objektem `target_block`.|
|[process_input_messages](#process_input_messages)|Zpracovává zprávy, které se přijímají jako vstupy.|
|[process_message](#process_message)|Při přepsání v odvozené třídě zpracovává zprávu, která byla přijata tímto objektem `target_block`.|
|[propagate_message](#propagate_message)|Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku do tohoto objektu `target_block`. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.|
|[register_filter](#register_filter)|Zaregistruje metodu filtru, která bude vyvolána při každé přijaté zprávě.|
|[remove_sources](#remove_sources)|Odpojí všechny zdroje po čekání na dokončení nedokončených asynchronních operací odeslání.|
|[send_message](#send_message)|Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku k tomuto objektu `target_block`. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.|
|[sync_send](#sync_send)|Synchronně pošle zprávu ke zpracování.|
|[unlink_source](#unlink_source)|Odpojí zadaný zdrojový blok od tohoto objektu `target_block`.|
|[unlink_sources](#unlink_sources)|Odpojí všechny zdrojové bloky z tohoto objektu `target_block`. (Overrides [ITarget:: unlink_sources](itarget-class.md#unlink_sources).)|
|[wait_for_async_sends](#wait_for_async_sends)|Čeká na dokončení všech asynchronních rozšíření.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ITarget](itarget-class.md)

`target_block`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="async_send"></a>async_send

Asynchronně pošle zprávu ke zpracování.

```cpp
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na odesílanou zprávu.

## <a name="decline_incoming_messages"></a>decline_incoming_messages

Označuje blok, že by se měly odmítnout nové zprávy.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána destruktorem, aby bylo zajištěno, že budou nové zprávy odmítnuty během procesu zničení.

## <a name="enable_batched_processing"></a>enable_batched_processing

Povolí dávkové zpracování pro tento blok.

```cpp
void enable_batched_processing();
```

## <a name="initialize_target"></a>initialize_target

Inicializuje základní objekt. Konkrétně je nutné inicializovat objekt `message_processor`.

```cpp
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Plánovač, který se má použít pro plánování úloh.

*_PScheduleGroup*<br/>
Skupina plánování, která se má použít pro plánování úloh.

## <a name="link_source"></a>link_source

Propojí zadaný zdrojový blok s tímto objektem `target_block`.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel na blok `ISource`, který má být propojen.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána přímo v objektu `target_block`. Bloky by měly být propojeny společně pomocí metody `link_target` v blocích `ISource`, která vyvolá metodu `link_source` na odpovídajícím cíli.

## <a name="process_input_messages"></a>process_input_messages

Zpracovává zprávy, které se přijímají jako vstupy.

```cpp
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

## <a name="process_message"></a>process_message

Při přepsání v odvozené třídě zpracovává zprávu, která byla přijata tímto objektem `target_block`.

```cpp
virtual void process_message(message<_Source_type> *);
```

## <a name="propagate"></a>šířit

Asynchronně předává zprávu ze zdrojového bloku do tohoto cílového bloku.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud je `NULL`parametr `_PMessage` nebo `_PSource`.

## <a name="propagate_message"></a>propagate_message

Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku do tohoto objektu `target_block`. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.

```cpp
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

## <a name="register_filter"></a>register_filter

Zaregistruje metodu filtru, která bude vyvolána při každé přijaté zprávě.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Metoda Filter

## <a name="remove_sources"></a>remove_sources

Odpojí všechny zdroje po čekání na dokončení nedokončených asynchronních operací odeslání.

```cpp
void remove_sources();
```

### <a name="remarks"></a>Poznámky

Všechny cílové bloky by měly zavolat tuto rutinu pro odebrání zdrojů ve svém destruktoru.

## <a name="send"></a>posílají

Synchronně předává zprávu ze zdrojového bloku do tohoto cílového bloku.

```cpp
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud je `NULL`parametr `_PMessage` nebo `_PSource`.

Použití metody `send` mimo zahájení zprávy a šíření zpráv v síti je nebezpečné a může vést k zablokování.

Když `send` vrátí, zpráva buď již byla přijata, a převedena do cílového bloku, nebo byla odmítnuta cílem.

## <a name="send_message"></a>send_message

Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku k tomuto objektu `target_block`. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tento blok vrátí `declined`, pokud není přepsána odvozenou třídou.

## <a name="sync_send"></a>sync_send

Synchronně pošle zprávu ke zpracování.

```cpp
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na odesílanou zprávu.

## <a name="ctor"></a>target_block

Vytvoří objekt `target_block`.

```cpp
target_block();
```

## <a name="dtor"></a>~ target_block

Odstraní objekt `target_block`.

```cpp
virtual ~target_block();
```

## <a name="unlink_source"></a>unlink_source

Odpojí zadaný zdrojový blok od tohoto objektu `target_block`.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel na blok `ISource`, který se má odpojit.

## <a name="unlink_sources"></a>unlink_sources

Odpojí všechny zdrojové bloky z tohoto objektu `target_block`.

```cpp
virtual void unlink_sources();
```

## <a name="wait_for_async_sends"></a>wait_for_async_sends

Čeká na dokončení všech asynchronních rozšíření.

```cpp
void wait_for_async_sends();
```

### <a name="remarks"></a>Poznámky

Tato metoda je používána destruktory bloku zpráv k zajištění, aby všechny asynchronní operace měly čas na dokončení před zničením bloku.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ITarget – třída](itarget-class.md)
