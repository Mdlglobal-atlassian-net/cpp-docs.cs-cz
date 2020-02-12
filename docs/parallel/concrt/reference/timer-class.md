---
title: Třída timer
ms.date: 11/04/2016
f1_keywords:
- timer
- AGENTS/concurrency::timer
- AGENTS/concurrency::timer::timer
- AGENTS/concurrency::timer::pause
- AGENTS/concurrency::timer::start
- AGENTS/concurrency::timer::stop
- AGENTS/concurrency::timer::accept_message
- AGENTS/concurrency::timer::consume_message
- AGENTS/concurrency::timer::link_target_notification
- AGENTS/concurrency::timer::propagate_to_any_targets
- AGENTS/concurrency::timer::release_message
- AGENTS/concurrency::timer::reserve_message
- AGENTS/concurrency::timer::resume_propagation
helpviewer_keywords:
- timer class
ms.assetid: 4f4dea51-de9f-40f9-93f5-dd724c567b49
ms.openlocfilehash: c39afc565a7ec775600b9c9fb6f15a89acdef57b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142533"
---
# <a name="timer-class"></a>Třída timer

`timer` blok zasílání zpráv je `source_block` s jedním cílem, který umožňuje poslat zprávu na cíl po uplynutí zadaného časového období nebo v určitých intervalech.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class timer : public Concurrency::details::_Timer, public source_block<single_link_registry<ITarget<T>>>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ datové části výstupních zpráv tohoto bloku.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[ukládání](#ctor)|Přetíženo. Vytvoří `timer` blok pro zasílání zpráv, který po zadaném intervalu spustí danou zprávu.|
|[~ Timer – destruktor](#dtor)|Odstraní blok zasílání zpráv `timer`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[chvíli](#pause)|Zastaví blok zasílání zpráv `timer`. Pokud se jedná o opakující se `timer` blok pro zasílání zpráv, může se restartovat s následným `start()`m voláním. U neopakujících se časovačů má stejný účinek jako volání `stop`.|
|[start](#start)|Spustí `timer` blok pro zasílání zpráv. Zadaný počet milisekund po volání bude zadaná hodnota šířena jako `message`.|
|[Stop](#stop)|Zastaví blok zasílání zpráv `timer`.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[accept_message](#accept_message)|Přijme zprávu, kterou nabídl tento `timer` blok pro zasílání zpráv a přenáší vlastnictví volajícímu.|
|[consume_message](#consume_message)|Spotřebovává zprávu, kterou dřív nabídl `timer` a rezervovala cíl, a přenáší vlastnictví volajícímu.|
|[link_target_notification](#link_target_notification)|Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `timer`m blokem zasílání zpráv.|
|[propagate_to_any_targets](#propagate_to_any_targets)|Se pokusí nabídnout zprávu vytvořenou blokem `timer` do všech propojených cílů.|
|[release_message](#release_message)|Uvolní předchozí rezervaci zprávy. (Potlačení [source_block:: release_message](source-block-class.md#release_message).)|
|[reserve_message](#reserve_message)|Vyhradí zprávu, kterou dřív nabídl tento `timer` blok pro zasílání zpráv. (Potlačení [source_block:: reserve_message](source-block-class.md#reserve_message).)|
|[resume_propagation](#resume_propagation)|Po vydání rezervace pokračuje v šíření. (Potlačení [source_block:: resume_propagation](source-block-class.md#resume_propagation).)|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

[source_block](source-block-class.md)

`timer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept_message"></a>accept_message

Přijme zprávu, kterou nabídl tento `timer` blok pro zasílání zpráv a přenáší vlastnictví volajícímu.

```cpp
virtual message<T>* accept_message(runtime_object_identity _MsgId);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

## <a name="consume_message"></a>consume_message

Spotřebovává zprávu, kterou dřív nabídl `timer` a rezervovala cíl, a přenáší vlastnictví volajícímu.

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

## <a name="link_target_notification"></a>link_target_notification

Zpětné volání upozorňující na to, že nový cíl byl propojen s tímto `timer`m blokem zasílání zpráv.

```cpp
virtual void link_target_notification(_Inout_ ITarget<T>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na nově propojený cíl.

## <a name="pause"></a>chvíli

Zastaví blok zasílání zpráv `timer`. Pokud se jedná o opakující se `timer` blok pro zasílání zpráv, může se restartovat s následným `start()`m voláním. U neopakujících se časovačů má stejný účinek jako volání `stop`.

```cpp
void pause();
```

## <a name="propagate_to_any_targets"></a>propagate_to_any_targets

Se pokusí nabídnout zprávu vytvořenou blokem `timer` do všech propojených cílů.

```cpp
virtual void propagate_to_any_targets(_Inout_opt_ message<T> *);
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

Vyhradí zprávu, kterou dřív nabídl tento `timer` blok pro zasílání zpráv.

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

## <a name="start"></a>Čína

Spustí `timer` blok pro zasílání zpráv. Zadaný počet milisekund po volání bude zadaná hodnota šířena jako `message`.

```cpp
void start();
```

## <a name="stop"></a>Stop

Zastaví blok zasílání zpráv `timer`.

```cpp
void stop();
```

## <a name="ctor"></a>ukládání

Vytvoří `timer` blok pro zasílání zpráv, který po zadaném intervalu spustí danou zprávu.

```cpp
timer(
    unsigned int _Ms,
    T const& value,
    ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    Scheduler& _Scheduler,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);

timer(
    ScheduleGroup& _ScheduleGroup,
    unsigned int _Ms,
    T const& value,
    _Inout_opt_ ITarget<T>* _PTarget = NULL,
    bool _Repeating = false);
```

### <a name="parameters"></a>Parametry

*_Ms*<br/>
Počet milisekund, které musí uplynout po volání metody ke spuštění, aby byla zadaná zpráva šířena jako podřízená.

*value*<br/>
Hodnota, která bude rozšířena na podřízený objekt, když uplyne časová osa.

*_PTarget*<br/>
Cíl, na který bude časovač šířit svou zprávu.

*_Repeating*<br/>
V případě hodnoty true označuje, že se časovač bude pravidelně spouštět každých `_Ms` milisekund.

*_Scheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `timer`

*_ScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `timer` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_Scheduler` nebo `_ScheduleGroup`.

## <a name="dtor"></a>~ Timer

Odstraní blok zasílání zpráv `timer`.

```cpp
~timer();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
