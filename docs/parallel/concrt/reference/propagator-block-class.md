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
ms.openlocfilehash: 38b7c920f8ffcab6d709d9484f308a56cd6b8425
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613275"
---
# <a name="propagatorblock-class"></a>propagator_block – třída

`propagator_block` Třída je abstraktní základní třída pro bloky zpráv, které jsou zdrojovém i cílovém. Kombinuje funkce i `source_block` a `target_block` třídy.

## <a name="syntax"></a>Syntaxe

```
template<class _TargetLinkRegistry, class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class propagator_block : public source_block<_TargetLinkRegistry,
    _MessageProcessorType>,
public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

#### <a name="parameters"></a>Parametry

*_TargetLinkRegistry*<br/>
Odkaz registru, který má být použit pro obsahující cílové odkazy.

*_SourceLinkRegistry*<br/>
Odkaz registru se použije pro uchování odkazy zdroje.

*_MessageProcessorType*<br/>
Typ procesoru pro zpracování zpráv.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`source_iterator`|Typ iterátoru pro `source_link_manager` to `propagator_block`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[propagator_block](#ctor)|Vytvoří `propagator_block` objektu.|
|[~propagator_block Destructor](#dtor)|Odstraní `propagator_block` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[propagate](#propagate)|Asynchronně předává zprávy z zdrojový blok pro tento cílový blok.|
|[Odeslat](#send)|Inicializuje synchronně zprávy do tohoto bloku. Volané `ISource` bloku. Po dokončení této funkce bude zpráva již rozšíření do bloku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[decline_incoming_messages –](#decline_incoming_messages)|Na blok označuje, že by měl odmítnuty nové zprávy.|
|[initialize_source_and_target –](#initialize_source_and_target)|Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializována.|
|[link_source –](#link_source)|Odkazuje na tento blok zadaný zdroj `propagator_block` objektu.|
|[process_input_messages](#process_input_messages)|Zprávy o zadávání procesu. Tím se zajistí Šiřitel bloků, které jsou odvozeny z source_block – (přepíše [source_block::process_input_messages –](source-block-class.md#process_input_messages).)|
|[propagate_message](#propagate_message)|Při přepisu v odvozené třídě, tato metoda asynchronně předává zprávy ze `ISource` bloku k tomuto `propagator_block` objektu. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.|
|[register_filter –](#register_filter)|Zaregistruje filtr metodu, která se vyvolá u každé přijaté zprávy.|
|[remove_network_links](#remove_network_links)|Odebere všechny zdrojové a cílové sítě odkazy z tohoto `propagator_block` objektu.|
|[send_message](#send_message)|Při přepisu v odvozené třídě, tato metoda synchronně předává zprávy ze `ISource` bloku k tomuto `propagator_block` objektu. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.|
|[unlink_source](#unlink_source)|Zruší se propojení z tohoto bloku zadaný zdrojový `propagator_block` objektu.|
|[unlink_sources –](#unlink_sources)|Zruší všechny zdrojové bloky z tohoto propojení `propagator_block` objektu. (Přepíše [itarget::unlink_sources –](itarget-class.md#unlink_sources).)|

## <a name="remarks"></a>Poznámky

Aby se zabránilo vícenásobné dědičnosti `propagator_block` třída dědí z `source_block` třídy a `ITarget` abstraktní třídy. Většina funkcí portálu `target_block` tříd replikovány tady.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Isource –](isource-class.md)

[Itarget –](itarget-class.md)

[source_block –](source-block-class.md)

`propagator_block`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="decline_incoming_messages"></a> decline_incoming_messages –

Na blok označuje, že by měl odmítnuty nové zprávy.

```
void decline_incoming_messages();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volán destruktor zajistit, že nové zprávy jsou odmítnuta, Probíhá odstraňování.

##  <a name="initialize_source_and_target"></a> initialize_source_and_target –

Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializována.

```
void initialize_source_and_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Plánovač má být použit pro plánování úloh.

*_PScheduleGroup*<br/>
Plánu skupiny, která má být použit pro plánování úloh.

##  <a name="link_source"></a> link_source –

Odkazuje na tento blok zadaný zdroj `propagator_block` objektu.

```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel `ISource` blok, který je spojen.

##  <a name="process_input_messages"></a> process_input_messages –

Zprávy o zadávání procesu. Tím se zajistí Šiřitel bloků, které jsou odvozeny z source_block –

```
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

##  <a name="propagate"></a> rozšíření

Asynchronně předává zprávy z zdrojový blok pro tento cílový blok.

```
virtual message_status propagate(
    _Inout_opt_ message<_Source_type>* _PMessage,
    _Inout_opt_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

### <a name="remarks"></a>Poznámky

`propagate` Vyvolání metody na cílový blok blokem propojený zdroj. Zařadí do fronty je asynchronní úloha pro zpracování zpráv, pokud jeden není již ve frontě nebo provádění.

Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimku, pokud buď `_PMessage` nebo `_PSource` parametr je `NULL`.

##  <a name="propagate_message"></a> propagate_message

Při přepisu v odvozené třídě, tato metoda asynchronně předává zprávy ze `ISource` bloku k tomuto `propagator_block` objektu. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status propagate_message(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

##  <a name="ctor"></a> propagator_block –

Vytvoří `propagator_block` objektu.

```
propagator_block();
```

##  <a name="dtor"></a> ~ propagator_block –

Odstraní `propagator_block` objektu.

```
virtual ~propagator_block();
```

##  <a name="register_filter"></a> register_filter –

Zaregistruje filtr metodu, která se vyvolá u každé přijaté zprávy.

```
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filtrovat*<br/>
Metoda filtru.

##  <a name="remove_network_links"></a> remove_network_links –

Odebere všechny zdrojové a cílové sítě odkazy z tohoto `propagator_block` objektu.

```
void remove_network_links();
```

##  <a name="send"></a> Odeslat

Inicializuje synchronně zprávy do tohoto bloku. Volané `ISource` bloku. Po dokončení této funkce bude zpráva již rozšíření do bloku.

```
virtual message_status send(
    _Inout_ message<_Source_type>* _PMessage,
    _Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

### <a name="remarks"></a>Poznámky

Tato metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimku, pokud `_PMessage` nebo `_PSource` parametr je `NULL`.

##  <a name="send_message"></a> send_message

Při přepisu v odvozené třídě, tato metoda synchronně předává zprávy ze `ISource` bloku k tomuto `propagator_block` objektu. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, vrátí tento blok `declined` přepsána odvozenou třídou.

##  <a name="unlink_source"></a> unlink_source –

Zruší se propojení z tohoto bloku zadaný zdrojový `propagator_block` objektu.

```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel `ISource` blok, který se má odpojit.

##  <a name="unlink_sources"></a> unlink_sources –

Zruší všechny zdrojové bloky z tohoto propojení `propagator_block` objektu.

```
virtual void unlink_sources();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[source_block – třída](source-block-class.md)<br/>
[ITarget – třída](itarget-class.md)
