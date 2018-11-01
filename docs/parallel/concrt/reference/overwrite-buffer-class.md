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
ms.openlocfilehash: 680c07015538a2eacc9480d3cd22da9a36071e32
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455996"
---
# <a name="overwritebuffer-class"></a>Třída overwrite_buffer

`overwrite_buffer` Je více cílový blok zpráv více zdroje, seřazený `propagator_block` umožňující ukládání do jedné zprávy najednou. Nové zprávy přepsat dříve vlastněnou značky.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class overwrite_buffer : public propagator_block<multi_link_registry<ITarget<T>>, multi_link_registry<ISource<T>>>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ datové části zprávy, uloženy a následně vyrovnávací paměti.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[overwrite_buffer](#ctor)|Přetíženo. Vytvoří `overwrite_buffer` blok zpráv.|
|[~ overwrite_buffer – destruktor](#dtor)|Odstraní `overwrite_buffer` blok zpráv.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[has_value](#has_value)|Zkontroluje, jestli to `overwrite_buffer` blok zpráv ještě nemá hodnotu.|
|[value](#value)|Získá odkaz na aktuální datové části zprávy v `overwrite_buffer` blok zpráv.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, která byly nabízeny situace `overwrite_buffer` blok zpráv, vrácení kopie zprávy volajícímu.|
|[consume_message](#consume_message)|Využívá dříve nabízená zpráva `overwrite_buffer` bloku zpráv a vyhrazená v cíli, vrácení kopie zprávy volajícímu.|
|[link_target_notification](#link_target_notification)|Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `overwrite_buffer` blok zpráv.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávy ze `ISource` bloku k tomuto `overwrite_buffer` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Místa `message _PMessage` v tomto `overwrite_buffer` bloku pro zasílání zpráv a nabídne ji na všechny propojené cílů.|
|[release_message](#release_message)|Uvolní předchozí rezervace zprávy. (Přepíše [source_block::release_message –](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu nabízely dříve v tomto `overwrite_buffer` blok zpráv. (Přepíše [source_block::reserve_message –](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Obnoví šíření po rezervaci byla uvolněna. (Přepíše [source_block::resume_propagation –](source-block-class.md#resume_propagation).)|
|[send_message](#send_message)|Synchronně předává zprávy ze `ISource` bloku k tomuto `overwrite_buffer` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.|
|[supports_anonymous_source –](#supports_anonymous_source)|Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený. (Přepíše [itarget::supports_anonymous_source –](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Poznámky

`overwrite_buffer` Blok zpráv šíří kopie uložené zprávy pro každý svůj cíl.

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Isource –](isource-class.md)

[Itarget –](itarget-class.md)

[source_block –](source-block-class.md)

[propagator_block](propagator-block-class.md)

`overwrite_buffer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="accept_message"></a> accept_message

Přijme zprávu, která byly nabízeny situace `overwrite_buffer` blok zpráv, vrácení kopie zprávy volajícímu.

```
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

### <a name="remarks"></a>Poznámky

`overwrite_buffer` Zasílání zpráv bloku vrátí kopii zprávy do cíle, spíše než přenos vlastnictví aktuálně vlastněnou zprávy.

##  <a name="consume_message"></a> consume_message

Využívá dříve nabízená zpráva `overwrite_buffer` bloku zpráv a vyhrazená v cíli, vrácení kopie zprávy volajícímu.

```
virtual message<T>* consume_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objektu spotřebovává.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

### <a name="remarks"></a>Poznámky

Podobně jako `accept`, ale vždy předchází volání `reserve`.

##  <a name="has_value"></a> has_value –

Zkontroluje, jestli to `overwrite_buffer` blok zpráv ještě nemá hodnotu.

```
bool has_value() const;
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** pokud blok obsahuje přijala se hodnota, **false** jinak.

##  <a name="link_target_notification"></a> link_target_notification –

Zpětné volání, která upozorňuje, že nový cíl je propojená s tím `overwrite_buffer` blok zpráv.

```
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na nově odkazovaný cíl.

##  <a name="dtor"></a> ~ overwrite_buffer

Odstraní `overwrite_buffer` blok zpráv.

```
~overwrite_buffer();
```

##  <a name="ctor"></a> overwrite_buffer

Vytvoří `overwrite_buffer` blok zpráv.

```
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

*_Filtrovat*<br/>
Funkce filtru, která určuje, zda by měl být přijat nabízené zprávy.

*_PScheduler*<br/>
`Scheduler` Objekt v rámci kterého Úloha šíření pro `overwrite_buffer` naplánovaný zasílání zpráv bloku.

*_PScheduleGroup*<br/>
`ScheduleGroup` Objekt v rámci kterého Úloha šíření pro `overwrite_buffer` naplánovaný zasílání zpráv bloku. `Scheduler` Skupina plánování předpokládá používaný objekt.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí plánovač, pokud není zadán `_PScheduler` nebo `_PScheduleGroup` parametry.

Typ `filter_method` je funktor s podpisem `bool (T const &)` která je vyvolána situace `overwrite_buffer` blok zpráv k určení, zda by měla přijímat nabízená zpráva.

##  <a name="propagate_message"></a> propagate_message

Asynchronně předává zprávy ze `ISource` bloku k tomuto `overwrite_buffer` blok zpráv. Je vyvolán `propagate` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status propagate_message(
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

Místa `message _PMessage` v tomto `overwrite_buffer` bloku pro zasílání zpráv a nabídne ji na všechny propojené cílů.

```
virtual void propagate_to_any_targets(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu, že tento `overwrite_buffer` má převzetí vlastnictví.

### <a name="remarks"></a>Poznámky

Tato metoda přepíše aktuální zprávu ve `overwrite_buffer` s nově přijaté zprávy `_PMessage`.

##  <a name="send_message"></a> send_message

Synchronně předává zprávy ze `ISource` bloku k tomuto `overwrite_buffer` blok zpráv. Je vyvolán `send` metodu, když se zavolá pomocí zdrojového bloku.

```
virtual message_status send_message(
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

##  <a name="supports_anonymous_source"></a> supports_anonymous_source –

Přepsání `supports_anonymous_source` indikace, že tento blok můžete přijímat zprávy, které jsou nabízeny zdrojem, který není spojený.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** protože bloku není odložit nabízené zprávy.

##  <a name="release_message"></a> release_message

Uvolní předchozí rezervace zprávy.

```
virtual void release_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z `message` objektu se vydávají.

##  <a name="reserve_message"></a> reserve_message

Vyhradí zprávu nabízely dříve v tomto `overwrite_buffer` blok zpráv.

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

##  <a name="value"></a> Hodnota

Získá odkaz na aktuální datové části zprávy v `overwrite_buffer` blok zpráv.

```
T value();
```

### <a name="return-value"></a>Návratová hodnota

Datová část aktuálně uložené zprávy.

### <a name="remarks"></a>Poznámky

Hodnota uložená v `overwrite_buffer` změnit hned po návratu tato metoda. Tato metoda budou čekat na přijetí e-mailu Pokud žádná zpráva je aktuálně uloženo v `overwrite_buffer`.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Třída unbounded_buffer](unbounded-buffer-class.md)<br/>
[single_assignment – třída](single-assignment-class.md)
