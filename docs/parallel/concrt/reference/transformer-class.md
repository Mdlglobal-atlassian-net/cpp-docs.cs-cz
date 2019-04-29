---
title: Třída transformer
ms.date: 11/04/2016
f1_keywords:
- transformer
- AGENTS/concurrency::transformer
- AGENTS/concurrency::transformer::transformer
- AGENTS/concurrency::transformer::accept_message
- AGENTS/concurrency::transformer::consume_message
- AGENTS/concurrency::transformer::link_target_notification
- AGENTS/concurrency::transformer::propagate_message
- AGENTS/concurrency::transformer::propagate_to_any_targets
- AGENTS/concurrency::transformer::release_message
- AGENTS/concurrency::transformer::reserve_message
- AGENTS/concurrency::transformer::resume_propagation
- AGENTS/concurrency::transformer::send_message
- AGENTS/concurrency::transformer::supports_anonymous_source
helpviewer_keywords:
- transformer class
ms.assetid: eea71925-7043-4a92-bfd4-dbc0ece5d081
ms.openlocfilehash: c07017539bc0125e9e8c27e208480a50ccc7a719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408066"
---
# <a name="transformer-class"></a>Třída transformer

A `transformer` blok zpráv je jeden cíl, více zdroje, seřazený `propagator_block` který může přijmout zprávy z jednoho typu a umožňuje ukládání množství zpráv jiného typu.

## <a name="syntax"></a>Syntaxe

```
template<class _Input, class _Output>
class transformer : public propagator_block<single_link_registry<ITarget<_Output>>,
    multi_link_registry<ISource<_Input>>>;
```

#### <a name="parameters"></a>Parametry

*_Input*<br/>
Typ datové části zprávy přijal vyrovnávací paměti.

*_Output*<br/>
Typ datové části zprávy, uloženy a šířen mimo ve vyrovnávací paměti.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[transformer](#ctor)|Přetíženo. Vytvoří `transformer` blok zpráv.|
|[~transformer Destructor](#dtor)|Odstraní `transformer` blok zpráv.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, která byly nabízeny situace `transformer` blok zpráv, přenos vlastnictví volajícímu.|
|[consume_message](#consume_message)|Využívá dříve nabízená zpráva `transformer` a vyhrazená v cíli, přenos vlastnictví volajícímu.|
|[link_target_notification](#link_target_notification)|Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `transformer` blok zpráv.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávy ze `ISource` bloku k tomuto `transformer` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Provede funkci transformer na vstupní zprávy.|
|[release_message](#release_message)|Uvolní předchozí rezervace zprávy. (Přepíše [source_block::release_message –](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu nabízely dříve v tomto `transformer` blok zpráv. (Přepíše [source_block::reserve_message –](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Obnoví šíření po rezervaci byla uvolněna. (Přepíše [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronně předává zprávy ze `ISource` bloku k tomuto `transformer` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.|
|[supports_anonymous_source](#supports_anonymous_source)|Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený. (Přepíše [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

[ITarget](itarget-class.md)

[source_block](source-block-class.md)

[propagator_block](propagator-block-class.md)

`transformer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="accept_message"></a> accept_message

Přijme zprávu, která byly nabízeny situace `transformer` blok zpráv, přenos vlastnictví volajícímu.

```
virtual message<_Output>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

##  <a name="consume_message"></a> consume_message

Využívá dříve nabízená zpráva `transformer` a vyhrazená v cíli, přenos vlastnictví volajícímu.

```
virtual message<_Output>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objektu spotřebovává.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

##  <a name="link_target_notification"></a> link_target_notification –

Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `transformer` blok zpráv.

```
virtual void link_target_notification(_Inout_ ITarget<_Output> *);
```

##  <a name="propagate_message"></a> propagate_message

Asynchronně předává zprávy ze `ISource` bloku k tomuto `transformer` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status propagate_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

##  <a name="propagate_to_any_targets"></a> propagate_to_any_targets

Provede funkci transformer na vstupní zprávy.

```
virtual void propagate_to_any_targets(_Inout_opt_ message<_Output> *);
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

Vyhradí zprávu nabízely dříve v tomto `transformer` blok zpráv.

```
virtual bool reserve_message(runtime_object_identity _MsgId);
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

Synchronně předává zprávy ze `ISource` bloku k tomuto `transformer` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status send_message(
    _Inout_ message<_Input>* _PMessage,
    _Inout_ ISource<_Input>* _PSource);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source –

Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** protože bloku není odložit nabízené zprávy.

##  <a name="ctor"></a> Transformer

Vytvoří `transformer` blok zpráv.

```
transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    Scheduler& _PScheduler,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget = NULL);

transformer(
    ScheduleGroup& _PScheduleGroup,
    _Transform_method const& _Func,
    _Inout_opt_ ITarget<_Output>* _PTarget,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Func*<br/>
Funkce, která bude volána pro každé přijaté zprávy.

*_PTarget*<br/>
Ukazatel na cílový blok pro propojení transformátoru.

*_Filter*<br/>
Funkce filtru, která určuje, zda by měl být přijat nabízené zprávy.

*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `transformer` naplánovaný zasílání zpráv bloku.

*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `transformer` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.

Typ `_Transform_method` je funktor s podpisem `_Output (_Input const &)` která je vyvolána situace `transformer` blok zpráv ke zpracování zprávy.

Typ `filter_method` je funktor s podpisem `bool (_Input const &)` která je vyvolána situace `transformer` blok zpráv k určení, zda by měla přijímat nabízená zpráva.

##  <a name="dtor"></a> ~ transformer

Odstraní `transformer` blok zpráv.

```
~transformer();
```

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[call – třída](call-class.md)
