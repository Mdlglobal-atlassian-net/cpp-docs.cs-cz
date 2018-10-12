---
title: JOIN – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- join class
ms.assetid: d2217119-70a1-40b6-809f-c1c13a571c3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 045cdeab321e9e3f88ee9bd50d337101e8512718
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49163813"
---
# <a name="join-class"></a>join – třída

A `join` blok zpráv je jeden cíl, více zdroje, seřazený `propagator_block` který spojuje dohromady zprávy typu `T` ze všech zdrojů.

## <a name="syntax"></a>Syntaxe

```
template<class T,
    join_type _Jtype = non_greedy>
class join : public propagator_block<single_link_registry<ITarget<std::vector<T>>>,
    multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ datové části zprávy připojený a následně bloku.

*_Jtype*<br/>
Druh nástroje `join` bloku jedná buď `greedy` nebo `non_greedy`

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Připojte se k](#ctor)|Přetíženo. Vytvoří `join` blok zpráv.|
|[~join Destructor](#dtor)|Odstraní `join` bloku.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, která byly nabízeny situace `join` blok zpráv, přenos vlastnictví volajícímu.|
|[consume_message](#consume_message)|Využívá dříve nabízená zpráva `join` bloku zpráv a vyhrazená v cíli, přenos vlastnictví volajícímu.|
|[link_target_notification](#link_target_notification)|Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `join` blok zpráv.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávy ze `ISource` bloku k tomuto `join` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Vytvoří zprávu výstup obsahující vstupní zprávy z každého zdroje, když máte šíří zprávy. Odešle tento výstupní zprávu pro každý svůj cíl.|
|[release_message](#release_message)|Uvolní předchozí rezervace zprávy. (Přepíše [source_block::release_message –](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu nabízely dříve v tomto `join` blok zpráv. (Přepíše [source_block::reserve_message –](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Obnoví šíření po rezervaci byla uvolněna. (Přepíše [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Isource –](isource-class.md)

[Itarget –](itarget-class.md)

[source_block –](source-block-class.md)

[propagator_block](propagator-block-class.md)

`join`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="accept_message"></a> accept_message

Přijme zprávu, která byly nabízeny situace `join` blok zpráv, přenos vlastnictví volajícímu.

```
virtual message<_OutputType>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

##  <a name="consume_message"></a> consume_message

Využívá dříve nabízená zpráva `join` bloku zpráv a vyhrazená v cíli, přenos vlastnictví volajícímu.

```
virtual message<_OutputType>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objektu spotřebovává.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

##  <a name="ctor"></a> Připojte se k

Vytvoří `join` blok zpráv.

```
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
Počet vstupů to `join` bude možné blokovat.

*_Filtrovat*<br/>
Funkce filtru, která určuje, zda by měl být přijat nabízené zprávy.

*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `join` naplánovaný zasílání zpráv bloku.

*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `join` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.

Typ `filter_method` je funktor s podpisem `bool (T const &)` která je vyvolána situace `join` blok zpráv k určení, zda by měla přijímat nabízená zpráva.

##  <a name="dtor"></a> ~ join

Odstraní `join` bloku.

```
~join();
```

##  <a name="link_target_notification"></a> link_target_notification –

Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `join` blok zpráv.

```
virtual void link_target_notification(_Inout_ ITarget<std::vector<T>> *);
```

##  <a name="propagate_message"></a> propagate_message

Asynchronně předává zprávy ze `ISource` bloku k tomuto `join` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.

```
message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Vytvoří zprávu výstup obsahující vstupní zprávy z každého zdroje, když máte šíří zprávy. Odešle tento výstupní zprávu pro každý svůj cíl.

```
void propagate_to_any_targets(_Inout_opt_ message<_OutputType> *);
```

##  <a name="release_message"></a> release_message

Uvolní předchozí rezervace zprávy.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objektu se vydávají.

##  <a name="reserve_message"></a> reserve_message

Vyhradí zprávu nabízely dříve v tomto `join` blok zpráv.

```
virtual bool reserve_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zpráva byla úspěšně vyhrazené, **false** jinak.

### <a name="remarks"></a>Poznámky

Po `reserve` je volána, pokud se vrátí **true**– buď `consume` nebo `release` využít nebo uvolnit vlastnictví zprávy musí být volána.

##  <a name="resume_propagation"></a> resume_propagation

Obnoví šíření po rezervaci byla uvolněna.

```
virtual void resume_propagation();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[choice – třída](choice-class.md)<br/>
[multitype_join – třída](multitype-join-class.md)
