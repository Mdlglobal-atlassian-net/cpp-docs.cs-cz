---
title: propagator_block – třída
ms.date: 11/04/2016
f1_keywords:
- propagator_block
- AGENTS/concurrency::propagator_block
- AGENTS/concurrency::propagator_block::propagator_block
- AGENTS/concurrency::propagator_block::propagate
- AGENTS/concurrency::propagator_block::send
- AGENTS/concurrency::propagator_block::decline_incoming_messages
- AGENTS/concurrency::propagator_block::initialize_source_and_target
- AGENTS/concurrency::propagator_block::link_source
- AGENTS/concurrency::propagator_block::process_input_messages
- AGENTS/concurrency::propagator_block::propagate_message
- AGENTS/concurrency::propagator_block::register_filter
- AGENTS/concurrency::propagator_block::remove_network_links
- AGENTS/concurrency::propagator_block::send_message
- AGENTS/concurrency::propagator_block::unlink_source
- AGENTS/concurrency::propagator_block::unlink_sources
helpviewer_keywords:
- propagator_block class
ms.assetid: 86aa75fd-eda5-42aa-aadf-25c0c1c9742d
ms.openlocfilehash: 340af181669cbbf4c5ba910aa3ee862bd40ba27f
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138742"
---
# <a name="propagator_block-class"></a>propagator_block – třída

Třída `propagator_block` je abstraktní základní třída pro bloky zpráv, které jsou zdrojem i cílem. Kombinuje funkce `source_block` i `target_block` třídy.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

### <a name="parameters"></a>Parametry

*_TargetLinkRegistry*<br/>
Registr odkazů, který se má použít pro uchovávání cílových odkazů.

*_SourceLinkRegistry*<br/>
Registr odkazů, který se má použít pro uchovávání zdrojových odkazů.

*_MessageProcessorType*<br/>
Typ procesoru pro zpracování zprávy.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`source_iterator`|Typ iterátoru pro `source_link_manager` pro tento `propagator_block`|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[propagator_block](#ctor)|Vytvoří objekt `propagator_block`.|
|[~ propagator_block destruktor](#dtor)|Odstraní objekt `propagator_block`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[šířit](#propagate)|Asynchronně předává zprávu ze zdrojového bloku do tohoto cílového bloku.|
|[posílají](#send)|Synchronně zahájí zprávu do tohoto bloku. Volá se blokem `ISource`. Po dokončení této funkce se zpráva již rozšíří do bloku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[decline_incoming_messages](#decline_incoming_messages)|Označuje blok, že by se měly odmítnout nové zprávy.|
|[initialize_source_and_target](#initialize_source_and_target)|Inicializuje základní objekt. Konkrétně je nutné inicializovat objekt `message_processor`.|
|[link_source](#link_source)|Propojí zadaný zdrojový blok s tímto objektem `propagator_block`.|
|[process_input_messages](#process_input_messages)|Zpracuje vstupní zprávy. To je užitečné pouze pro bloky šiřitelů, které jsou odvozeny z source_block (Overrides [source_block::p rocess_input_messages](source-block-class.md#process_input_messages).)|
|[propagate_message](#propagate_message)|Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku do tohoto objektu `propagator_block`. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.|
|[register_filter](#register_filter)|Zaregistruje metodu filtru, která bude vyvolána při každé přijaté zprávě.|
|[remove_network_links](#remove_network_links)|Odebere všechna propojení zdrojové a cílové sítě z tohoto objektu `propagator_block`.|
|[send_message](#send_message)|Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku k tomuto objektu `propagator_block`. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.|
|[unlink_source](#unlink_source)|Odpojí zadaný zdrojový blok od tohoto objektu `propagator_block`.|
|[unlink_sources](#unlink_sources)|Odpojí všechny zdrojové bloky z tohoto objektu `propagator_block`. (Overrides [ITarget:: unlink_sources](itarget-class.md#unlink_sources).)|

## <a name="remarks"></a>Poznámky

Chcete-li zabránit vícenásobné dědění, třída `propagator_block` dědí z třídy `source_block` a `ITarget` abstraktní třídy. Většina funkcí v `target_block` třídě se tady replikuje.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="decline_incoming_messages"></a>decline_incoming_messages

Označuje blok, že by se měly odmítnout nové zprávy.

```cpp
void decline_incoming_messages();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána destruktorem, aby bylo zajištěno, že budou nové zprávy odmítnuty během procesu zničení.

## <a name="initialize_source_and_target"></a>initialize_source_and_target

Inicializuje základní objekt. Konkrétně je nutné inicializovat objekt `message_processor`.

```cpp
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Plánovač, který se má použít pro plánování úloh.

*_PScheduleGroup*<br/>
Skupina plánování, která se má použít pro plánování úloh.

## <a name="link_source"></a>link_source

Propojí zadaný zdrojový blok s tímto objektem `propagator_block`.

```cpp
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel na blok `ISource`, který má být propojen.

## <a name="process_input_messages"></a>process_input_messages

Zpracuje vstupní zprávy. To je užitečné jenom pro bloky šiřitelů, které se odvozují z source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

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

Metoda `propagate` je vyvolána v cílovém bloku pomocí propojeného zdrojového bloku. Zařadí do fronty asynchronní úlohu pro zpracování zprávy, pokud ještě není ve frontě nebo spuštěná.

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud je `NULL`parametr `_PMessage` nebo `_PSource`.

## <a name="propagate_message"></a>propagate_message

Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku do tohoto objektu `propagator_block`. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.

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

## <a name="ctor"></a>propagator_block

Vytvoří objekt `propagator_block`.

```cpp
propagator_block();
```

## <a name="dtor"></a>~ propagator_block

Odstraní objekt `propagator_block`.

```cpp
virtual ~propagator_block();
```

## <a name="register_filter"></a>register_filter

Zaregistruje metodu filtru, která bude vyvolána při každé přijaté zprávě.

```cpp
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Metoda Filter

## <a name="remove_network_links"></a>remove_network_links

Odebere všechna propojení zdrojové a cílové sítě z tohoto objektu `propagator_block`.

```cpp
void remove_network_links();
```

## <a name="send"></a>posílají

Synchronně zahájí zprávu do tohoto bloku. Volá se blokem `ISource`. Po dokončení této funkce se zpráva již rozšíří do bloku.

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

Tato metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud je `NULL`parametr `_PMessage` nebo `_PSource`.

## <a name="send_message"></a>send_message

Při přepsání v odvozené třídě tato metoda asynchronně předává zprávu z `ISource` bloku k tomuto objektu `propagator_block`. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.

```cpp
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tento blok vrátí `declined`, pokud není přepsána odvozenou třídou.

## <a name="unlink_source"></a>unlink_source

Odpojí zadaný zdrojový blok od tohoto objektu `propagator_block`.

```cpp
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel na blok `ISource`, který se má odpojit.

## <a name="unlink_sources"></a>unlink_sources

Odpojí všechny zdrojové bloky z tohoto objektu `propagator_block`.

```cpp
virtual void unlink_sources();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[source_block – třída](source-block-class.md)<br/>
[ITarget – třída](itarget-class.md)
