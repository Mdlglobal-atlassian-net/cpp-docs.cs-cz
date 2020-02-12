---
title: Třída single_assignment
ms.date: 11/04/2016
f1_keywords:
- single_assignment
- AGENTS/concurrency::single_assignment
- AGENTS/concurrency::single_assignment::single_assignment
- AGENTS/concurrency::single_assignment::has_value
- AGENTS/concurrency::single_assignment::value
- AGENTS/concurrency::single_assignment::accept_message
- AGENTS/concurrency::single_assignment::consume_message
- AGENTS/concurrency::single_assignment::link_target_notification
- AGENTS/concurrency::single_assignment::propagate_message
- AGENTS/concurrency::single_assignment::propagate_to_any_targets
- AGENTS/concurrency::single_assignment::release_message
- AGENTS/concurrency::single_assignment::reserve_message
- AGENTS/concurrency::single_assignment::resume_propagation
- AGENTS/concurrency::single_assignment::send_message
helpviewer_keywords:
- single_assignment class
ms.assetid: ccc34728-8de9-4e07-b83d-a36a58d9d2b9
ms.openlocfilehash: 0d302f4f7f85737d9c3b2368e3ae04d88bc1a370
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142739"
---
# <a name="single_assignment-class"></a>Třída single_assignment

`single_assignment` blok pro zasílání zpráv je více cílů, seřazené `propagator_block` umožňující ukládání jednoho, jednorázového `message`ho zápisu.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class single_assignment : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ datové části zprávy uložené a šířené vyrovnávací pamětí.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[single_assignment](#ctor)|Přetíženo. Vytvoří blok pro zasílání zpráv `single_assignment`.|
|[~ single_assignment destruktor](#dtor)|Odstraní blok zasílání zpráv `single_assignment`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[has_value](#has_value)|Kontroluje, zda byl tento blok zasílání zpráv `single_assignment` inicializován s hodnotou.|
|[value](#value)|Získá odkaz na aktuální datovou část zprávy, která je uložena v `single_assignment`ovém bloku pro zasílání zpráv.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, kterou nabídl tento `single_assignment` blok pro zasílání zpráv, a vrátí kopii zprávy volajícímu.|
|[consume_message](#consume_message)|Spotřebovává zprávu, kterou dřív nabídl `single_assignment` a rezervovala cíl, a vrátí kopii zprávy volajícímu.|
|[link_target_notification](#link_target_notification)|Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `single_assignment`m blokem zasílání zpráv.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávu z `ISource` bloku do tohoto `single_assignment` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umístí `message _PMessage` do tohoto bloku `single_assignment` zasílání zpráv a nabídne ho všem propojeným cílům.|
|[release_message](#release_message)|Uvolní předchozí rezervaci zprávy. (Potlačení [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu, kterou dřív nabídl tento `single_assignment` blok pro zasílání zpráv. (Potlačení [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Po vydání rezervace pokračuje v šíření. (Potlačení [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronně předává zprávu z `ISource` bloku do tohoto `single_assignment` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.|

## <a name="remarks"></a>Poznámky

Blok zasílání zpráv `single_assignment` rozšíří kopie své zprávy na každý cíl.

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`single_assignment`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept_message"></a>accept_message

Přijme zprávu, kterou nabídl tento `single_assignment` blok pro zasílání zpráv, a vrátí kopii zprávy volajícímu.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Blok pro zasílání zpráv `single_assignment` vrátí kopie zprávy do cílů, nikoli převod vlastnictví aktuálně uchovávané zprávy.

## <a name="consume_message"></a>consume_message

Spotřebovává zprávu, kterou dřív nabídl `single_assignment` a rezervovala cíl, a vrátí kopii zprávy volajícímu.

```cpp
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` spotřebovaného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

## <a name="has_value"></a>has_value

Kontroluje, zda byl tento blok zasílání zpráv `single_assignment` inicializován s hodnotou.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud blok obdržel hodnotu, jinak **false** .

## <a name="link_target_notification"></a>link_target_notification

Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `single_assignment`m blokem zasílání zpráv.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na nově propojený cíl.

## <a name="propagate_message"></a>propagate_message

Asynchronně předává zprávu z `ISource` bloku do tohoto `single_assignment` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.

```cpp
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Umístí `message` `_PMessage` do tohoto `single_assignment` bloku pro zasílání zpráv a nabídne ho všem propojeným cílům.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na `message`, že tento blok `single_assignment` zasílání zpráv převzal vlastnictví.

## <a name="release_message"></a>release_message

Uvolní předchozí rezervaci zprávy.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` vydaných `message` objektu.

## <a name="reserve_message"></a>reserve_message

Vyhradí zprávu, kterou dřív nabídl tento `single_assignment` blok pro zasílání zpráv.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
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

Synchronně předává zprávu z `ISource` bloku do tohoto `single_assignment` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.

```cpp
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

## <a name="ctor"></a>single_assignment

Vytvoří blok pro zasílání zpráv `single_assignment`.

```cpp
single_assignment();

single_assignment(
    filter_method const& _Filter);

single_assignment(
    Scheduler& _PScheduler);

single_assignment(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

single_assignment(
    ScheduleGroup& _PScheduleGroup);

single_assignment(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Funkce filtru, která určuje, zda mají být přijaty nabízené zprávy.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `single_assignment`

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `single_assignment` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PScheduleGroup`.

Typ `filter_method` je funktor s podpisovým `bool (T const &)`, který je vyvolán pomocí tohoto `single_assignment` bloku zpráv k určení, zda by měla přijmout nabízenou zprávu.

## <a name="dtor"></a>~ single_assignment

Odstraní blok zasílání zpráv `single_assignment`.

```cpp
~single_assignment();
```

## <a name="value"></a>osa

Získá odkaz na aktuální datovou část zprávy, která je uložena v `single_assignment`ovém bloku pro zasílání zpráv.

```cpp
T const& value();
```

### <a name="return-value"></a>Návratová hodnota

Datová část uložené zprávy

### <a name="remarks"></a>Poznámky

Tato metoda počká, dokud zpráva nebude doručena, pokud není v rámci `single_assignment`ho blokování zpráv aktuálně uložena žádná zpráva.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[overwrite_buffer – třída](overwrite-buffer-class.md)<br/>
[unbounded_buffer – třída](unbounded-buffer-class.md)
