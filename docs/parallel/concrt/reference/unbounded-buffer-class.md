---
title: Třída unbounded_buffer | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 6b1a939a-1819-4385-b1d8-708f83d4ec47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ffc1ea1f512e049f3a6af15170429a3618323dc5
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162994"
---
`unbounded_buffer` Je více cílový blok zpráv více zdroje, seřazený `propagator_block` umožňující ukládání množství zpráv.

## <a name="syntax"></a>Syntaxe

```
template<
   class             _Type
>
class unbounded_buffer : public propagator_block<multi_link_registry<ITarget<            _Type>>, multi_link_registry<ISource<            _Type>>>;
```

#### <a name="parameters"></a>Parametry

*_Typ*<br/>
Typ datové části zprávy, uloženy a následně vyrovnávací paměti.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[unbounded_buffer](#ctor)|Přetíženo. Vytvoří `unbounded_buffer` blok zpráv.|
|[~ unbounded_buffer – destruktor](#dtor)|Odstraní `unbounded_buffer` blok zpráv.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Odstranění z fronty](#dequeue)|Odebere položku z `unbounded_buffer` blok zpráv.|
|[Zařazení do fronty](#enqueue)|Přidá položku do `unbounded_buffer` blok zpráv.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, která byly nabízeny situace `unbounded_buffer` blok zpráv, přenos vlastnictví volajícímu.|
|[consume_message](#consume_message)|Využívá dříve nabízená zpráva `unbounded_buffer` bloku zpráv a vyhrazená v cíli, přenos vlastnictví volajícímu.|
|[link_target_notification](#link_target_notification)|Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `unbounded_buffer` blok zpráv.|
|[process_input_messages](#process_input_messages)|Místa `message` `_PMessage` v tomto `unbounded_buffer` blok zpráv a pokouší se nabízejí na všechny propojené cíle.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávy ze `ISource` bloku k tomuto `unbounded_buffer` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.|
|[propagate_output_messages](#propagate_output_messages)|Místa `message` `_PMessage` v tomto `unbounded_buffer` blok zpráv a pokouší se nabízejí na všechny propojené cíle. (Přepíše [source_block::propagate_output_messages –](source-block-class.md#propagate_output_messages).)|
|[release_message](#release_message)|Uvolní předchozí rezervace zprávy. (Přepíše [source_block::release_message –](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu nabízely dříve v tomto `unbounded_buffer` blok zpráv. (Přepíše [source_block::reserve_message –](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Obnoví šíření po rezervaci byla uvolněna. (Přepíše [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronně předává zprávy ze `ISource` bloku k tomuto `unbounded_buffer` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.|
|[supports_anonymous_source –](#supports_anonymous_source)|Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený. (Přepíše [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|

Další informace najdete v tématu [asynchronní bloky zpráv](../asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Isource –](isource-class.md)

[Itarget –](itarget-class.md)

[source_block –](source-block-class.md)

[propagator_block](propagator-block-class.md)

`unbounded_buffer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="accept_message"></a> accept_message

Přijme zprávu, která byly nabízeny situace `unbounded_buffer` blok zpráv, přenos vlastnictví volajícímu.

```
virtual message<_Type> * accept_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

##  <a name="consume_message"></a> consume_message

Využívá dříve nabízená zpráva `unbounded_buffer` bloku zpráv a vyhrazená v cíli, přenos vlastnictví volajícímu.

```
virtual message<_Type> * consume_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objektu spotřebovává.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

##  <a name="dequeue"></a> Odstranění z fronty

Odebere položku z `unbounded_buffer` blok zpráv.

```
_Type dequeue();
```

### <a name="return-value"></a>Návratová hodnota

Datová část zprávy odebrán z `unbounded_buffer`.

##  <a name="enqueue"></a> Zařazení do fronty

Přidá položku do `unbounded_buffer` blok zpráv.

```
bool enqueue(
   _Type const&                 _Item
);
```

### <a name="parameters"></a>Parametry

*_Položku*<br/>
Položka k přidání.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud položka byla přijata, **false** jinak.

##  <a name="link_target_notification"></a> link_target_notification –

Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `unbounded_buffer` blok zpráv.

```
virtual void link_target_notification(
   _Inout_ ITarget<_Type> *                 _PTarget
);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na nově odkazovaný cíl.

##  <a name="propagate_message"></a> propagate_message

Asynchronně předává zprávy ze `ISource` bloku k tomuto `unbounded_buffer` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status propagate_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md#message_status) označení cíl rozhodla se zprávy.

##  <a name="propagate_output_messages"></a> propagate_output_messages –

Místa `message` `_PMessage` v tomto `unbounded_buffer` blok zpráv a pokouší se nabízejí na všechny propojené cíle.

```
virtual void propagate_output_messages();
```

### <a name="remarks"></a>Poznámky

Pokud už před touto možností v další zprávu `unbounded_buffer`, šíření na propojené cíle nedojde, dokud všechny předchozí zprávy byla přijata nebo spotřebovanými. První propojení cíl, aby se úspěšně vytvořilo `accept` nebo `consume` zprávy převezme vlastnictví a žádný cíl pak můžete získat zprávu.

##  <a name="process_input_messages"></a> process_input_messages –

Místa `message` `_PMessage` v tomto `unbounded_buffer` blok zpráv a pokouší se nabízejí na všechny propojené cíle.

```
virtual void process_input_messages(
   _Inout_ message<_Type> *                 _PMessage
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

##  <a name="release_message"></a> release_message

Uvolní předchozí rezervace zprávy.

```
virtual void release_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objektu se vydávají.

##  <a name="reserve_message"></a> reserve_message

Vyhradí zprávu nabízely dříve v tomto `unbounded_buffer` blok zpráv.

```
virtual bool reserve_message(
   runtime_object_identity                 _MsgId
);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objekt dochází k rezervaci.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zpráva byla úspěšně vyhrazené, **false** jinak.

### <a name="remarks"></a>Poznámky

Po `reserve` je volána, pokud se vrátí **true**– buď `consume` nebo `release` využít nebo uvolnit vlastnictví zprávy musí být volána.

##  <a name="resume_propagation"></a> resume_propagation

Obnoví šíření po rezervaci byla uvolněna.

```
virtual void resume_propagation();
```

##  <a name="send_message"></a> send_message

Synchronně předává zprávy ze `ISource` bloku k tomuto `unbounded_buffer` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status send_message(
   _Inout_ message<_Type> *                 _PMessage,
   _Inout_ ISource<_Type> *                 _PSource
);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md#message_status) označení cíl rozhodla se zprávy.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source –

Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** protože bloku není odložit nabízené zprávy.

##  <a name="ctor"></a> unbounded_buffer

Vytvoří `unbounded_buffer` blok zpráv.

```
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

*_Filtrovat*<br/>
Funkce filtru, která určuje, zda by měl být přijat nabízené zprávy.

*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `unbounded_buffer` naplánovaný zasílání zpráv bloku.

*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `unbounded_buffer` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.

Typ `filter_method` je funktor s podpisem `bool (_Type const &)` která je vyvolána situace `unbounded_buffer` blok zpráv k určení, zda by měla přijímat nabízená zpráva.

##  <a name="dtor"></a> ~ unbounded_buffer

Odstraní `unbounded_buffer` blok zpráv.

```
~unbounded_buffer();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[overwrite_buffer – třída](overwrite-buffer-class.md)<br/>
[single_assignment – třída](single-assignment-class.md)

