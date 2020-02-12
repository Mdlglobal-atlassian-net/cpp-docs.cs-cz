---
title: join – třída
ms.date: 11/04/2016
f1_keywords:
- join
- AGENTS/concurrency::join
- AGENTS/concurrency::join::join
- AGENTS/concurrency::join::accept_message
- AGENTS/concurrency::join::consume_message
- AGENTS/concurrency::join::link_target_notification
- AGENTS/concurrency::join::propagate_message
- AGENTS/concurrency::join::propagate_to_any_targets
- AGENTS/concurrency::join::release_message
- AGENTS/concurrency::join::reserve_message
- AGENTS/concurrency::join::resume_propagation
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
ms.openlocfilehash: f75cf8483e7d6d65d118cc8f0ea756302d1b1d7c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139850"
---
# <a name="join-class"></a>join – třída

`join` blok pro zasílání zpráv je jeden cíl, řazený `propagator_block`, který kombinuje zprávy typu `T` od každého ze svých zdrojů.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ datové části zpráv, které byly připojeny a šířeny blokem.

*_Jtype*<br/>
Typ `join` blok je, buď `greedy` nebo `non_greedy`

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[join](#ctor)|Přetíženo. Vytvoří blok pro zasílání zpráv `join`.|
|[~ Join – destruktor](#dtor)|Odstraní blok `join`.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, kterou nabídl tento `join` blok pro zasílání zpráv a přenáší vlastnictví volajícímu.|
|[consume_message](#consume_message)|Spotřebovává zprávu, kterou předtím nabízela služba `join` pro zasílání zpráv a kterou rezervoval cíl, a převádí vlastnictví na volajícího.|
|[link_target_notification](#link_target_notification)|Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `join`m blokem zasílání zpráv.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávu z `ISource` bloku do tohoto `join` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Vytvoří výstupní zprávu obsahující vstupní zprávu z každého zdroje, pokud všechna rozšířila zprávu. Pošle tuto výstupní zprávu do každého cíle.|
|[release_message](#release_message)|Uvolní předchozí rezervaci zprávy. (Potlačení [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu, kterou dřív nabídl tento `join` blok pro zasílání zpráv. (Potlačení [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Po vydání rezervace pokračuje v šíření. (Potlačení [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept_message"></a>accept_message

Přijme zprávu, kterou nabídl tento `join` blok pro zasílání zpráv a přenáší vlastnictví volajícímu.

```cpp
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

## <a name="consume_message"></a>consume_message

Spotřebovává zprávu, kterou předtím nabízela služba `join` pro zasílání zpráv a kterou rezervoval cíl, a převádí vlastnictví na volajícího.

```cpp
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` spotřebovaného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

## <a name="ctor"></a>zúčastnit

Vytvoří blok pro zasílání zpráv `join`.

```cpp
join(
    size_t _NumInputs);

join(
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs);

join(
    Scheduler& _PScheduler,
    size_t _NumInputs,
    filter_method const& _Filter);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs);

join(
    ScheduleGroup& _PScheduleGroup,
    size_t _NumInputs,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_NumInputs*<br/>
Počet vstupů, které tento blok `join`, bude povolen.

*_Filter*<br/>
Funkce filtru, která určuje, zda mají být přijaty nabízené zprávy.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `join`

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `join` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PScheduleGroup`.

Typ `filter_method` je funktor s podpisovým `bool (T const &)`, který je vyvolán pomocí tohoto `join` bloku zpráv k určení, zda by měla přijmout nabízenou zprávu.

## <a name="dtor"></a>~ Join

Odstraní blok `join`.

```cpp
~join();
```

## <a name="link_target_notification"></a>link_target_notification

Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `join`m blokem zasílání zpráv.

```cpp
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

## <a name="propagate_message"></a>propagate_message

Asynchronně předává zprávu z `ISource` bloku do tohoto `join` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.

```cpp
message_status propagate_message(
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

Vytvoří výstupní zprávu obsahující vstupní zprávu z každého zdroje, pokud všechna rozšířila zprávu. Pošle tuto výstupní zprávu do každého cíle.

```cpp
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```

## <a name="release_message"></a>release_message

Uvolní předchozí rezervaci zprávy.

```cpp
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` vydaných `message` objektu.

## <a name="reserve_message"></a>reserve_message

Vyhradí zprávu, kterou dřív nabídl tento `join` blok pro zasílání zpráv.

```cpp
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva úspěšně rezervována, jinak **false** .

### <a name="remarks"></a>Poznámky

Po volání `reserve`, pokud vrátí **hodnotu true**, musí být buď volána `consume` nebo `release`, aby bylo možné převzít nebo uvolnit vlastnictví zprávy.

## <a name="resume_propagation"></a>resume_propagation

Po vydání rezervace pokračuje v šíření.

```cpp
virtual void resume_propagation();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[choice – třída](choice-class.md)<br/>
[multitype_join – třída](multitype-join-class.md)
