---
title: Třída unbounded_buffer
ms.date: 11/04/2016
f1_keywords:
- unbounded_buffer
- AGENTS/concurrency::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::unbounded_buffer
- AGENTS/concurrency::unbounded_buffer::dequeue
- AGENTS/concurrency::unbounded_buffer::enqueue
- AGENTS/concurrency::unbounded_buffer::accept_message
- AGENTS/concurrency::unbounded_buffer::consume_message
- AGENTS/concurrency::unbounded_buffer::link_target_notification
- AGENTS/concurrency::unbounded_buffer::process_input_messages
- AGENTS/concurrency::unbounded_buffer::propagate_message
- AGENTS/concurrency::unbounded_buffer::propagate_output_messages
- AGENTS/concurrency::unbounded_buffer::release_message
- AGENTS/concurrency::unbounded_buffer::reserve_message
- AGENTS/concurrency::unbounded_buffer::resume_propagation
- AGENTS/concurrency::unbounded_buffer::send_message
- AGENTS/concurrency::unbounded_buffer::supports_anonymous_source
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
ms.openlocfilehash: d0f2f81957ee88d4263c6acd879bd286c95631eb
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142337"
---
# <a name="unbounded_buffer-class"></a>Třída unbounded_buffer

`unbounded_buffer` blok zasílání zpráv je více cílů, seřazené `propagator_block` umožňující ukládání neohraničeného počtu zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

### <a name="parameters"></a>Parametry

*_Type*<br/>
Typ datové části zpráv uložených a šířených vyrovnávací pamětí.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Přetíženo. Vytvoří blok pro zasílání zpráv `unbounded_buffer`.|
|[~ unbounded_buffer destruktor](#dtor)|Odstraní blok zasílání zpráv `unbounded_buffer`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[odstranění z fronty](#dequeue)|Odebere položku z `unbounded_buffer`ho bloku pro zasílání zpráv.|
|[zařazování](#enqueue)|Přidá položku do `unbounded_buffer`ho bloku pro zasílání zpráv.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, kterou nabídl tento `unbounded_buffer` blok pro zasílání zpráv a přenáší vlastnictví volajícímu.|
|[consume_message](#consume_message)|Spotřebovává zprávu, kterou předtím nabízela služba `unbounded_buffer` pro zasílání zpráv a kterou rezervoval cíl, a převádí vlastnictví na volajícího.|
|[link_target_notification](#link_target_notification)|Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `unbounded_buffer`m blokem zasílání zpráv.|
|[process_input_messages](#process_input_messages)|Umístí do tohoto `unbounded_buffer` bloku pro zasílání zpráv `message` `_PMessage` a pokusí se ho nabídnout všem propojeným cílům.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávu z `ISource` bloku do tohoto `unbounded_buffer` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.|
|[propagate_output_messages](#propagate_output_messages)|Umístí do tohoto `unbounded_buffer` bloku pro zasílání zpráv `message` `_PMessage` a pokusí se ho nabídnout všem propojeným cílům. (Overrides [source_block::p ropagate_output_messages](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Uvolní předchozí rezervaci zprávy. (Potlačení [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu, kterou dřív nabídl tento `unbounded_buffer` blok pro zasílání zpráv. (Potlačení [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Po vydání rezervace pokračuje v šíření. (Potlačení [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronně předává zprávu z `ISource` bloku do tohoto `unbounded_buffer` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.|
|[supports_anonymous_source](#supports_anonymous_source)|Přepíše metodu `supports_anonymous_source`, aby označovala, že tento blok může přijímat zprávy, které mu byly nabídnuty zdrojem, který není propojen. (Overrides [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

Další informace najdete v tématu [asynchronní bloky zpráv](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept_message"></a>accept_message

Přijme zprávu, kterou nabídl tento `unbounded_buffer` blok pro zasílání zpráv a přenáší vlastnictví volajícímu.

```cpp
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

## <a name="consume_message"></a>consume_message

Spotřebovává zprávu, kterou předtím nabízela služba `unbounded_buffer` pro zasílání zpráv a kterou rezervoval cíl, a převádí vlastnictví na volajícího.

```cpp
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` spotřebovaného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

## <a name="dequeue"></a>odstranění z fronty

Odebere položku z `unbounded_buffer`ho bloku pro zasílání zpráv.

```cpp
_Type dequeue();
```

### <a name="return-value"></a>Návratová hodnota

Datová část zprávy, která byla odebrána z `unbounded_buffer`.

## <a name="enqueue"></a>zařazování

Přidá položku do `unbounded_buffer`ho bloku pro zasílání zpráv.

```cpp
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parametry

*_Item*<br/>
Položka k přidání.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla položka přijata, jinak **false** .

## <a name="link_target_notification"></a>link_target_notification

Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `unbounded_buffer`m blokem zasílání zpráv.

```cpp
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na nově propojený cíl.

## <a name="propagate_message"></a>propagate_message

Asynchronně předává zprávu z `ISource` bloku do tohoto `unbounded_buffer` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.

```cpp
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md#message_status) údaj o tom, co se cíli rozhodl s touto zprávou.

## <a name="propagate_output_messages"></a>propagate_output_messages

Umístí do tohoto `unbounded_buffer` bloku pro zasílání zpráv `message` `_PMessage` a pokusí se ho nabídnout všem propojeným cílům.

```cpp
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Poznámky

Je-li již v `unbounded_buffer`jiná zpráva, dojde k šíření do propojených cílů, dokud nebudou přijaty nebo spotřebovány žádné předchozí zprávy. První propojený cíl, který má úspěšně `accept` nebo `consume` zprávu převezme vlastnictví, a žádný jiný cíl pak nemůže získat zprávu.

## <a name="process_input_messages"></a>process_input_messages

Umístí do tohoto `unbounded_buffer` bloku pro zasílání zpráv `message` `_PMessage` a pokusí se ho nabídnout všem propojeným cílům.

```cpp
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

## <a name="release_message"></a>release_message

Uvolní předchozí rezervaci zprávy.

```cpp
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` vydaných `message` objektu.

## <a name="reserve_message"></a>reserve_message

Vyhradí zprávu, kterou dřív nabídl tento `unbounded_buffer` blok pro zasílání zpráv.

```cpp
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva úspěšně rezervována, jinak **false** .

### <a name="remarks"></a>Poznámky

Po volání `reserve`, pokud vrátí **hodnotu true**, musí být buď volána `consume` nebo `release`, aby bylo možné převzít nebo uvolnit vlastnictví zprávy.

## <a name="resume_propagation"></a>resume_propagation

Po vydání rezervace pokračuje v šíření.

```cpp
virtual void resume_propagation();
```

## <a name="send_message"></a>send_message

Synchronně předává zprávu z `ISource` bloku do tohoto `unbounded_buffer` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.

```cpp
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md#message_status) údaj o tom, co se cíli rozhodl s touto zprávou.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Přepíše metodu `supports_anonymous_source`, aby označovala, že tento blok může přijímat zprávy, které mu byly nabídnuty zdrojem, který není propojen.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Návratová hodnota

**true** , protože blok odloží nabízené zprávy.

## <a name="ctor"></a>unbounded_buffer

Vytvoří blok pro zasílání zpráv `unbounded_buffer`.

```cpp
unbounded_buffer();

unbounded_buffer(
   filter_method const&                 _Filter
);

unbounded_buffer(
   Scheduler&                 _PScheduler
);

unbounded_buffer(
   Scheduler&                 _PScheduler,
   filter_method const&                 _Filter
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup
);

unbounded_buffer(
   ScheduleGroup&                 _PScheduleGroup,
   filter_method const&                 _Filter
);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Funkce filtru, která určuje, zda mají být přijaty nabízené zprávy.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `unbounded_buffer`

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `unbounded_buffer` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PScheduleGroup`.

Typ `filter_method` je funktor s podpisovým `bool (_Type const &)`, který je vyvolán pomocí tohoto `unbounded_buffer` bloku zpráv k určení, zda by měla přijmout nabízenou zprávu.

## <a name="dtor"></a>~ unbounded_buffer

Odstraní blok zasílání zpráv `unbounded_buffer`.

```cpp
~unbounded_buffer();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[overwrite_buffer – třída](overwrite-buffer-class.md)<br/>
[single_assignment – třída](single-assignment-class.md)
