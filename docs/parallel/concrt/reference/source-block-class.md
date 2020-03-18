---
title: source_block – třída
ms.date: 11/04/2016
f1_keywords:
- source_block
- AGENTS/concurrency::source_block
- AGENTS/concurrency::source_block::source_block
- AGENTS/concurrency::source_block::accept
- AGENTS/concurrency::source_block::acquire_ref
- AGENTS/concurrency::source_block::consume
- AGENTS/concurrency::source_block::link_target
- AGENTS/concurrency::source_block::release
- AGENTS/concurrency::source_block::release_ref
- AGENTS/concurrency::source_block::reserve
- AGENTS/concurrency::source_block::unlink_target
- AGENTS/concurrency::source_block::unlink_targets
- AGENTS/concurrency::source_block::accept_message
- AGENTS/concurrency::source_block::async_send
- AGENTS/concurrency::source_block::consume_message
- AGENTS/concurrency::source_block::enable_batched_processing
- AGENTS/concurrency::source_block::initialize_source
- AGENTS/concurrency::source_block::link_target_notification
- AGENTS/concurrency::source_block::process_input_messages
- AGENTS/concurrency::source_block::propagate_output_messages
- AGENTS/concurrency::source_block::propagate_to_any_targets
- AGENTS/concurrency::source_block::release_message
- AGENTS/concurrency::source_block::remove_targets
- AGENTS/concurrency::source_block::reserve_message
- AGENTS/concurrency::source_block::resume_propagation
- AGENTS/concurrency::source_block::sync_send
- AGENTS/concurrency::source_block::unlink_target_notification
- AGENTS/concurrency::source_block::wait_for_outstanding_async_sends
helpviewer_keywords:
- source_block class
ms.assetid: fbdd4146-e8d0-42e8-b714-fe633f69ffbf
ms.openlocfilehash: 3a0d69bc2e2904b1dcf37a7e9891d95bd869a610
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417080"
---
# <a name="source_block-class"></a>source_block – třída

Třída `source_block` je abstraktní základní třída pro bloky pouze ve zdroji. Třída poskytuje základní funkce pro správu odkazů a také běžné kontroly chyb.

## <a name="syntax"></a>Syntaxe

```cpp
template<class _TargetLinkRegistry, class _MessageProcessorType = ordered_message_processor<typename _TargetLinkRegistry::type::type>>
class source_block : public ISource<typename _TargetLinkRegistry::type::type>;
```

### <a name="parameters"></a>Parametry

*_TargetLinkRegistry*<br/>
Propojte registr, který se má použít pro uchovávání cílových odkazů.

*_MessageProcessorType*<br/>
Typ procesoru pro zpracování zprávy

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`target_iterator`|Iterátor, který projde propojeným cílům.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[source_block](#ctor)|Vytvoří objekt `source_block`.|
|[~ source_block destruktor](#dtor)|Odstraní objekt `source_block`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[vyjádřit](#accept)|Přijme zprávu, kterou nabídl tento objekt `source_block`, a přenáší vlastnictví volajícímu.|
|[acquire_ref](#acquire_ref)|Získá počet odkazů na tento objekt `source_block`, aby se zabránilo odstranění.|
|[každém](#consume)|Spotřebovává zprávu, kterou dřív nabídl tento `source_block` objekt a úspěšně rezervoval cíl a přenáší vlastnictví volajícímu.|
|[link_target](#link_target)|Propojí cílový blok s tímto objektem `source_block`.|
|[předběžné](#release)|Uvolní předchozí úspěšnou rezervaci zprávy.|
|[release_ref](#release_ref)|Uvolní počet odkazů na tento objekt `source_block`.|
|[rezervační](#reserve)|Vyhradí zprávu, kterou dřív nabídl tento `source_block` objekt.|
|[unlink_target](#unlink_target)|Odpojí cílový blok od tohoto objektu `source_block`.|
|[unlink_targets](#unlink_targets)|Odpojí všechny cílové bloky z tohoto objektu `source_block`. (Overrides [ISource:: unlink_targets](isource-class.md#unlink_targets).)|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Pokud je přepsána v odvozené třídě, přijímá zdroj nabízenou zprávu. Bloky zpráv by měly přepsat tuto metodu pro ověření `_MsgId` a vrácení zprávy.|
|[async_send](#async_send)|Asynchronně zařadí zprávy do fronty a spustí úlohu šíření, pokud tato operace ještě nebyla dokončena.|
|[consume_message](#consume_message)|Při přepsání v odvozené třídě spotřebovává zprávu, která byla dříve vyhrazena.|
|[enable_batched_processing](#enable_batched_processing)|Povolí dávkové zpracování pro tento blok.|
|[initialize_source](#initialize_source)|Inicializuje `message_propagator` v rámci této `source_block`.|
|[link_target_notification](#link_target_notification)|Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto objektem `source_block`.|
|[process_input_messages](#process_input_messages)|Zpracuje vstupní zprávy. To je užitečné jenom pro bloky šiřitelů, které se odvozují z source_block|
|[propagate_output_messages](#propagate_output_messages)|Rozšiřte zprávy na cíle.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Při přepsání v odvozené třídě rozšíří danou zprávu do všech propojených cílů. Toto je hlavní rutina šíření pro bloky zpráv.|
|[release_message](#release_message)|Při přepsání v odvozené třídě uvolní předchozí rezervaci zprávy.|
|[remove_targets](#remove_targets)|Odebere všechny cílové odkazy pro tento zdrojový blok. To by mělo být voláno z destruktoru.|
|[reserve_message](#reserve_message)|Při přepsání v odvozené třídě si vyhrazuje zprávu, kterou dřív nabídl tento `source_block` objekt.|
|[resume_propagation](#resume_propagation)|Při přepsání v odvozené třídě pokračuje šíření po vydání rezervace.|
|[sync_send](#sync_send)|Synchronně zařadí zprávy do fronty a spustí úlohu šíření, pokud tato operace ještě nebyla dokončena.|
|[unlink_target_notification](#unlink_target_notification)|Zpětné volání upozorňující na zrušení propojení cíle od tohoto objektu `source_block`.|
|[wait_for_outstanding_async_sends](#wait_for_outstanding_async_sends)|Čeká na dokončení všech asynchronních rozšíření. Tento číselník určený k rozšíření pro modul pro šíření se používá v destruktorech bloků zpráv, aby bylo zajištěno, že všechny asynchronní šíření mají čas na dokončení před zničením bloku.|

## <a name="remarks"></a>Poznámky

Bloky zpráv by měly být odvozeny z tohoto bloku, aby mohli využívat možnosti správy odkazů a synchronizace poskytované touto třídou.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

`source_block`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept"></a>vyjádřit

Přijme zprávu, kterou nabídl tento objekt `source_block`, a přenáší vlastnictví volajícímu.

```cpp
virtual message<_Target_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `accept`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud `_PTarget` parametr `NULL`.

Metoda `accept` je volána cílem, zatímco je zpráva nabízena tímto `ISource` bloku. Vrácený ukazatel na zprávu může být jiný než ten, který se předává do metody `propagate` bloku `ITarget`, pokud se tento zdroj rozhodne vytvořit kopii zprávy.

## <a name="accept_message"></a>accept_message

Pokud je přepsána v odvozené třídě, přijímá zdroj nabízenou zprávu. Bloky zpráv by měly přepsat tuto metodu pro ověření `_MsgId` a vrácení zprávy.

```cpp
virtual message<_Target_type>* accept_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
Identita běhového objektu objektu `message`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zprávu, na kterou má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Pro přenos vlastnictví by měl být vrácen původní ukazatel na zprávu. Aby bylo možné zachovat vlastnictví, musí být provedena a vrácena kopie datové části zprávy.

## <a name="acquire_ref"></a>acquire_ref

Získá počet odkazů na tento objekt `source_block`, aby se zabránilo odstranění.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Target_type> *);
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je propojen s tímto zdrojem během metody `link_target`.

## <a name="async_send"></a>async_send

Asynchronně zařadí zprávy do fronty a spustí úlohu šíření, pokud tato operace ještě nebyla dokončena.

```cpp
virtual void async_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Ukazatel na objekt `message` k asynchronnímu odeslání.

## <a name="consume"></a>každém

Spotřebovává zprávu, kterou dřív nabídl tento `source_block` objekt a úspěšně rezervoval cíl a přenáší vlastnictví volajícímu.

```cpp
virtual message<_Target_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `consume`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud `_PTarget` parametr `NULL`.

Metoda vyvolá výjimku [bad_target](bad-target-class.md) , pokud parametr `_PTarget` nepředstavuje cíl, který se volal `reserve`.

Metoda `consume` je podobná `accept`, ale vždy musí předcházet volání `reserve`, které vrátilo **hodnotu true**.

## <a name="consume_message"></a>consume_message

Při přepsání v odvozené třídě spotřebovává zprávu, která byla dříve vyhrazena.

```cpp
virtual message<_Target_type>* consume_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` spotřebovaného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zprávu, na kterou má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

## <a name="enable_batched_processing"></a>enable_batched_processing

Povolí dávkové zpracování pro tento blok.

```cpp
void enable_batched_processing();
```

## <a name="initialize_source"></a>initialize_source

Inicializuje `message_propagator` v rámci této `source_block`.

```cpp
void initialize_source(
    _Inout_opt_ Scheduler* _PScheduler = NULL,
    _Inout_opt_ ScheduleGroup* _PScheduleGroup = NULL);
```

### <a name="parameters"></a>Parametry

*_PScheduler*<br/>
Plánovač, který se má použít pro plánování úloh.

*_PScheduleGroup*<br/>
Skupina plánování, která se má použít pro plánování úloh.

## <a name="link_target"></a>link_target

Propojí cílový blok s tímto objektem `source_block`.

```cpp
virtual void link_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na blok `ITarget`, který se má propojit s tímto objektem `source_block`.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud `_PTarget` parametr `NULL`.

## <a name="link_target_notification"></a>link_target_notification

Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto objektem `source_block`.

```cpp
virtual void link_target_notification(_Inout_ ITarget<_Target_type> *);
```

## <a name="process_input_messages"></a>process_input_messages

Zpracuje vstupní zprávy. To je užitečné jenom pro bloky šiřitelů, které se odvozují z source_block

```cpp
virtual void process_input_messages(_Inout_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

## <a name="propagate_output_messages"></a>propagate_output_messages

Rozšiřte zprávy na cíle.

```cpp
virtual void propagate_output_messages();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Při přepsání v odvozené třídě rozšíří danou zprávu do všech propojených cílů. Toto je hlavní rutina šíření pro bloky zpráv.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<_Target_type>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být šířena.

## <a name="release"></a>předběžné

Uvolní předchozí úspěšnou rezervaci zprávy.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `release`.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud `_PTarget` parametr `NULL`.

Metoda vyvolá výjimku [bad_target](bad-target-class.md) , pokud parametr `_PTarget` nepředstavuje cíl, který se volal `reserve`.

## <a name="release_message"></a>release_message

Při přepsání v odvozené třídě uvolní předchozí rezervaci zprávy.

```cpp
virtual void release_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` vydaných `message` objektu.

## <a name="release_ref"></a>release_ref

Uvolní počet odkazů na tento objekt `source_block`.

```cpp
virtual void release_ref(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který volá tuto metodu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je odpojování od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky rezervované pro cílový blok.

## <a name="remove_targets"></a>remove_targets

Odebere všechny cílové odkazy pro tento zdrojový blok. To by mělo být voláno z destruktoru.

```cpp
void remove_targets();
```

## <a name="reserve"></a>rezervační

Vyhradí zprávu, kterou dřív nabídl tento `source_block` objekt.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `reserve`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva úspěšně rezervována, jinak **false** . Rezervace mohou selhat z mnoha důvodů, včetně: zpráva byla již rezervována nebo přijata jiným cílem, zdroj může zamítnout rezervace atd.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud `_PTarget` parametr `NULL`.

Po volání `reserve`, je-li tato operace úspěšná, je nutné volat buď `consume` nebo `release`, aby bylo možné převzít nebo dát k dispozici zprávu, v uvedeném pořadí.

## <a name="reserve_message"></a>reserve_message

Při přepsání v odvozené třídě si vyhrazuje zprávu, kterou dřív nabídl tento `source_block` objekt.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva úspěšně rezervována, jinak **false** .

### <a name="remarks"></a>Poznámky

Po volání `reserve`, pokud vrátí **hodnotu true**, musí být buď volána `consume` nebo `release`, aby bylo možné převzít nebo uvolnit vlastnictví zprávy.

## <a name="resume_propagation"></a>resume_propagation

Při přepsání v odvozené třídě pokračuje šíření po vydání rezervace.

```cpp
virtual void resume_propagation() = 0;
```

## <a name="ctor"></a>source_block

Vytvoří objekt `source_block`.

```cpp
source_block();
```

## <a name="dtor"></a>~ source_block

Odstraní objekt `source_block`.

```cpp
virtual ~source_block();
```

## <a name="sync_send"></a>sync_send

Synchronně zařadí zprávy do fronty a spustí úlohu šíření, pokud tato operace ještě nebyla dokončena.

```cpp
virtual void sync_send(_Inout_opt_ message<_Target_type>* _Msg);
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Ukazatel na objekt `message` k synchronnímu odeslání.

## <a name="unlink_target"></a>unlink_target

Odpojí cílový blok od tohoto objektu `source_block`.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na blok `ITarget`, který se má odpojit od tohoto objektu `source_block`.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud `_PTarget` parametr `NULL`.

## <a name="unlink_target_notification"></a>unlink_target_notification

Zpětné volání upozorňující na zrušení propojení cíle od tohoto objektu `source_block`.

```cpp
virtual void unlink_target_notification(_Inout_ ITarget<_Target_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Blok `ITarget`, který byl odpojování.

## <a name="unlink_targets"></a>unlink_targets

Odpojí všechny cílové bloky z tohoto objektu `source_block`.

```cpp
virtual void unlink_targets();
```

## <a name="wait_for_outstanding_async_sends"></a>wait_for_outstanding_async_sends

Čeká na dokončení všech asynchronních rozšíření. Tento číselník určený k rozšíření pro modul pro šíření se používá v destruktorech bloků zpráv, aby bylo zajištěno, že všechny asynchronní šíření mají čas na dokončení před zničením bloku.

```cpp
void wait_for_outstanding_async_sends();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ISource – třída](isource-class.md)
