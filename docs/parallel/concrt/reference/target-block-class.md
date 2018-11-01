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
ms.openlocfilehash: cb8880b66ebeef12018ef7449c9c383b99ec396c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50656885"
---
# <a name="targetblock-class"></a>target_block – třída

`target_block` Třída je abstraktní základní třídu, která poskytuje funkce pro správu základní odkaz a kontroly chyb pro cíl pouze blokuje.

## <a name="syntax"></a>Syntaxe

```
template<class _SourceLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _SourceLinkRegistry::type::source_type>>
class target_block : public ITarget<typename _SourceLinkRegistry::type::source_type>;
```

#### <a name="parameters"></a>Parametry

*_SourceLinkRegistry*<br/>
Odkaz registru se použije pro uchování odkazy zdroje.

*_MessageProcessorType*<br/>
Typ procesoru pro zpracování zpráv.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`source_iterator`|Typ iterátoru pro `source_link_manager` to `target_block` objektu.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[target_block –](#ctor)|Vytvoří `target_block` objektu.|
|[~ target_block – destruktor](#dtor)|Odstraní `target_block` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[propagate](#propagate)|Asynchronně předává zprávy z zdrojový blok pro tento cílový blok.|
|[Odeslat](#send)|Synchronně předává zprávy z zdrojový blok pro tento cílový blok.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[async_send](#async_send)|Asynchronně odešle zprávu pro zpracování.|
|[decline_incoming_messages –](#decline_incoming_messages)|Na blok označuje, že by měl odmítnuty nové zprávy.|
|[enable_batched_processing –](#enable_batched_processing)|Umožňuje dávce zpracování pro tento blok.|
|[initialize_target](#initialize_target)|Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializována.|
|[link_source –](#link_source)|Odkazuje na tento blok zadaný zdroj `target_block` objektu.|
|[process_input_messages](#process_input_messages)|Zpracovává zprávy přijaté za vstupy.|
|[process_message –](#process_message)|Při přepisu v odvozené třídě, zpracuje zprávu, která byla přijata situace `target_block` objektu.|
|[propagate_message](#propagate_message)|Při přepisu v odvozené třídě, tato metoda asynchronně předává zprávy ze `ISource` bloku k tomuto `target_block` objektu. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.|
|[register_filter –](#register_filter)|Zaregistruje filtr metodu, která se vyvolá u každé zprávy přijaté.|
|[remove_sources –](#remove_sources)|Zruší po čekání na dokončení zbývajících asynchronní odeslání operací propojení všech zdrojů.|
|[send_message](#send_message)|Při přepisu v odvozené třídě, tato metoda synchronně předává zprávy ze `ISource` bloku k tomuto `target_block` objektu. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.|
|[sync_send](#sync_send)|Synchronně odešlete zprávu pro zpracování.|
|[unlink_source](#unlink_source)|Zruší se propojení z tohoto bloku zadaný zdrojový `target_block` objektu.|
|[unlink_sources –](#unlink_sources)|Zruší všechny zdrojové bloky z tohoto propojení `target_block` objektu. (Přepíše [itarget::unlink_sources –](itarget-class.md#unlink_sources).)|
|[wait_for_async_sends](#wait_for_async_sends)|Čeká na všechny asynchronní šíření dokončete.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Itarget –](itarget-class.md)

`target_block`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="async_send"></a> async_send –

Asynchronně odešle zprávu pro zpracování.

```
void async_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na odeslání zprávy.

##  <a name="decline_incoming_messages"></a> decline_incoming_messages –

Na blok označuje, že by měl odmítnuty nové zprávy.

```
void decline_incoming_messages();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volán destruktor zajistit, že nové zprávy jsou odmítnuta, Probíhá odstraňování.

##  <a name="enable_batched_processing"></a> enable_batched_processing –

Umožňuje dávce zpracování pro tento blok.

```
void enable_batched_processing();
```

##  <a name="initialize_target"></a> initialize_target –

Inicializuje základní objekt. Konkrétně `message_processor` objekt musí být inicializována.

```
void initialize_target(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Plánovač má být použit pro plánování úloh.

*_PScheduleGroup*<br/>
Plánu skupiny, která má být použit pro plánování úloh.

##  <a name="link_source"></a> link_source –

Odkazuje na tento blok zadaný zdroj `target_block` objektu.

```
virtual void link_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel `ISource` blok, který je spojen.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána přímo na `target_block` objektu. Bloky by měly být propojeny pomocí `link_target` metoda `ISource` bloků, které se vyvolá `link_source` metodu na odpovídající cíle.

##  <a name="process_input_messages"></a> process_input_messages –

Zpracovává zprávy přijaté za vstupy.

```
virtual void process_input_messages(_Inout_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

##  <a name="process_message"></a> process_message –

Při přepisu v odvozené třídě, zpracuje zprávu, která byla přijata situace `target_block` objektu.

```
virtual void process_message(message<_Source_type> *);
```

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

Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimku, pokud buď `_PMessage` nebo `_PSource` parametr je `NULL`.

##  <a name="propagate_message"></a> propagate_message

Při přepisu v odvozené třídě, tato metoda asynchronně předává zprávy ze `ISource` bloku k tomuto `target_block` objektu. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.

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

##  <a name="register_filter"></a> register_filter –

Zaregistruje filtr metodu, která se vyvolá u každé zprávy přijaté.

```
void register_filter(filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filtrovat*<br/>
Metoda filtru.

##  <a name="remove_sources"></a> remove_sources –

Zruší po čekání na dokončení zbývajících asynchronní odeslání operací propojení všech zdrojů.

```
void remove_sources();
```

### <a name="remarks"></a>Poznámky

Všechny cílové bloky by měly volat tato rutina pro odebrání zdroje v jejich destruktor.

##  <a name="send"></a> Odeslat

Synchronně předává zprávy z zdrojový blok pro tento cílový blok.

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

Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimku, pokud buď `_PMessage` nebo `_PSource` parametr je `NULL`.

Použití `send` metoda mimo zahájení zprávu a šíření zpráv v rámci sítě je nebezpečné a může vést k zablokování.

Když `send` vrátí zprávy buď již byla přijata a přenést na cílový blok, nebo byla zamítnuta v cíli.

##  <a name="send_message"></a> send_message

Při přepisu v odvozené třídě, tato metoda synchronně předává zprávy ze `ISource` bloku k tomuto `target_block` objektu. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status send_message(
    _Inout_ message<_Source_type> *,
    _Inout_ ISource<_Source_type> *);
```

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, vrátí tento blok `declined` přepsána odvozenou třídou.

##  <a name="sync_send"></a> sync_send –

Synchronně odešlete zprávu pro zpracování.

```
void sync_send(_Inout_opt_ message<_Source_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na odeslání zprávy.

##  <a name="ctor"></a> target_block –

Vytvoří `target_block` objektu.

```
target_block();
```

##  <a name="dtor"></a> ~ target_block –

Odstraní `target_block` objektu.

```
virtual ~target_block();
```

##  <a name="unlink_source"></a> unlink_source –

Zruší se propojení z tohoto bloku zadaný zdrojový `target_block` objektu.

```
virtual void unlink_source(_Inout_ ISource<_Source_type>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Ukazatel `ISource` blok, který se má odpojit.

##  <a name="unlink_sources"></a> unlink_sources –

Zruší všechny zdrojové bloky z tohoto propojení `target_block` objektu.

```
virtual void unlink_sources();
```

##  <a name="wait_for_async_sends"></a> wait_for_async_sends –

Čeká na všechny asynchronní šíření dokončete.

```
void wait_for_async_sends();
```

### <a name="remarks"></a>Poznámky

Tato metoda používá destruktory bloku zpráv k zajištění, že všechny asynchronní operace měli čas dokončení a zničení bloku.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ITarget – třída](itarget-class.md)
