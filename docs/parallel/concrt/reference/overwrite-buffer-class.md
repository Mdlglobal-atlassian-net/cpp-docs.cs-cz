---
title: Třída overwrite_buffer
ms.date: 11/04/2016
f1_keywords:
- overwrite_buffer
- AGENTS/concurrency::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::overwrite_buffer
- AGENTS/concurrency::overwrite_buffer::has_value
- AGENTS/concurrency::overwrite_buffer::value
- AGENTS/concurrency::overwrite_buffer::accept_message
- AGENTS/concurrency::overwrite_buffer::consume_message
- AGENTS/concurrency::overwrite_buffer::link_target_notification
- AGENTS/concurrency::overwrite_buffer::propagate_message
- AGENTS/concurrency::overwrite_buffer::propagate_to_any_targets
- AGENTS/concurrency::overwrite_buffer::release_message
- AGENTS/concurrency::overwrite_buffer::reserve_message
- AGENTS/concurrency::overwrite_buffer::resume_propagation
- AGENTS/concurrency::overwrite_buffer::send_message
- AGENTS/concurrency::overwrite_buffer::supports_anonymous_source
helpviewer_keywords:
- overwrite_buffer class
ms.assetid: 5cc428fe-3697-419c-9fb2-78f6181c9293
ms.openlocfilehash: 5b222170112f43ae9700054f42e1368545612d00
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138790"
---
# <a name="overwrite_buffer-class"></a>Třída overwrite_buffer

`overwrite_buffer` blok pro zasílání zpráv je více cílů, seřazené `propagator_block` s možností ukládání jedné zprávy v jednom okamžiku. Nové zprávy se přepisují dříve.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ datové části zpráv uložených a šířených vyrovnávací pamětí.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[overwrite_buffer](#ctor)|Přetíženo. Vytvoří blok pro zasílání zpráv `overwrite_buffer`.|
|[~ overwrite_buffer destruktor](#dtor)|Odstraní blok zasílání zpráv `overwrite_buffer`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[has_value](#has_value)|Kontroluje, zda tento blok zasílání zpráv `overwrite_buffer` má hodnotu ještě.|
|[value](#value)|Získá odkaz na aktuální datovou část zprávy, která je uložena v `overwrite_buffer`ovém bloku pro zasílání zpráv.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, kterou nabídl tento `overwrite_buffer` blok pro zasílání zpráv, a vrátí kopii zprávy volajícímu.|
|[consume_message](#consume_message)|Využije zprávu, kterou předtím nabídl blok pro zasílání zpráv `overwrite_buffer` a vyhrazené cílem, a vrátí kopii zprávy volajícímu.|
|[link_target_notification](#link_target_notification)|Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `overwrite_buffer`m blokem zasílání zpráv.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávu z `ISource` bloku do tohoto `overwrite_buffer` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Umístí `message _PMessage` do tohoto bloku `overwrite_buffer` zasílání zpráv a nabídne ho všem propojeným cílům.|
|[release_message](#release_message)|Uvolní předchozí rezervaci zprávy. (Potlačení [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu, kterou dřív nabídl tento `overwrite_buffer` blok pro zasílání zpráv. (Potlačení [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Po vydání rezervace pokračuje v šíření. (Potlačení [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronně předává zprávu z `ISource` bloku do tohoto `overwrite_buffer` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.|
|[supports_anonymous_source](#supports_anonymous_source)|Přepíše metodu `supports_anonymous_source`, aby označovala, že tento blok může přijímat zprávy, které mu byly nabídnuty zdrojem, který není propojen. (Overrides [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Poznámky

Blok zasílání zpráv `overwrite_buffer` rozšíří kopie své uložené zprávy do každého z jeho cílů.

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept_message"></a>accept_message

Přijme zprávu, kterou nabídl tento `overwrite_buffer` blok pro zasílání zpráv, a vrátí kopii zprávy volajícímu.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Blok pro zasílání zpráv `overwrite_buffer` vrátí kopie zprávy do cílů, nikoli převod vlastnictví aktuálně uchovávané zprávy.

## <a name="consume_message"></a>consume_message

Využije zprávu, kterou předtím nabídl blok pro zasílání zpráv `overwrite_buffer` a vyhrazené cílem, a vrátí kopii zprávy volajícímu.

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

Kontroluje, zda tento blok zasílání zpráv `overwrite_buffer` má hodnotu ještě.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud blok obdržel hodnotu, jinak **false** .

## <a name="link_target_notification"></a>link_target_notification

Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `overwrite_buffer`m blokem zasílání zpráv.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na nově propojený cíl.

## <a name="dtor"></a>~ overwrite_buffer

Odstraní blok zasílání zpráv `overwrite_buffer`.

```cpp
~overwrite_buffer();
```

## <a name="ctor"></a>overwrite_buffer

Vytvoří blok pro zasílání zpráv `overwrite_buffer`.

```cpp
overwrite_buffer();

overwrite_buffer(
    filter_method const& _Filter);

overwrite_buffer(
    Scheduler& _PScheduler);

overwrite_buffer(
    Scheduler& _PScheduler,
    filter_method const& _Filter);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup);

overwrite_buffer(
    ScheduleGroup& _PScheduleGroup,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Filter*<br/>
Funkce filtru, která určuje, zda mají být přijaty nabízené zprávy.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `overwrite_buffer`

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `overwrite_buffer` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PScheduleGroup`.

Typ `filter_method` je funktor s podpisovým `bool (T const &)`, který je vyvolán pomocí tohoto `overwrite_buffer` bloku zpráv k určení, zda by měla přijmout nabízenou zprávu.

## <a name="propagate_message"></a>propagate_message

Asynchronně předává zprávu z `ISource` bloku do tohoto `overwrite_buffer` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.

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

Umístí `message _PMessage` do tohoto bloku `overwrite_buffer` zasílání zpráv a nabídne ho všem propojeným cílům.

```cpp
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`, který tento `overwrite_buffer` převzal vlastnictví.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše aktuální zprávu v `overwrite_buffer` nově přijatou `_PMessage`zprávy.

## <a name="send_message"></a>send_message

Synchronně předává zprávu z `ISource` bloku do tohoto `overwrite_buffer` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.

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

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Přepíše metodu `supports_anonymous_source`, aby označovala, že tento blok může přijímat zprávy, které mu byly nabídnuty zdrojem, který není propojen.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Návratová hodnota

**true** , protože blok odloží nabízené zprávy.

## <a name="release_message"></a>release_message

Uvolní předchozí rezervaci zprávy.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` vydaných `message` objektu.

## <a name="reserve_message"></a>reserve_message

Vyhradí zprávu, kterou dřív nabídl tento `overwrite_buffer` blok pro zasílání zpráv.

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

## <a name="value"></a>osa

Získá odkaz na aktuální datovou část zprávy, která je uložena v `overwrite_buffer`ovém bloku pro zasílání zpráv.

```cpp
T value();
```

### <a name="return-value"></a>Návratová hodnota

Datová část aktuálně uložené zprávy.

### <a name="remarks"></a>Poznámky

Hodnota uložená v `overwrite_buffer` se může změnit hned po návratu této metody. Tato metoda počká, až přijde zpráva, pokud v `overwrite_buffer`není aktuálně uložená žádná zpráva.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[unbounded_buffer – třída](unbounded-buffer-class.md)<br/>
[single_assignment – třída](single-assignment-class.md)
