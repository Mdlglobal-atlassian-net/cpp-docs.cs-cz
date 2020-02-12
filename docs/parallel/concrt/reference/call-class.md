---
title: Třída call
ms.date: 11/04/2016
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
helpviewer_keywords:
- call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
ms.openlocfilehash: 445e368ced9d9c8faf30351ecaeecc4e1b8a59f2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142839"
---
# <a name="call-class"></a>Třída call

`call` blok pro zasílání zpráv je více zdrojů seřazená `target_block`, která při přijímání zprávy vyvolá zadanou funkci.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ datové části zpráv šířených do tohoto bloku

*_FunctorType*<br/>
Podpis funkcí, které tento blok může přijmout.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[volání](#ctor)|Přetíženo. Vytvoří blok pro zasílání zpráv `call`.|
|[~ volání destruktoru](#dtor)|Odstraní blok zasílání zpráv `call`.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[process_input_messages](#process_input_messages)|Spustí funkci volání na vstupních zprávách.|
|[process_message](#process_message)|Zpracuje zprávu, kterou přijal tento `call` blok pro zasílání zpráv.|
|[propagate_message](#propagate_message)|Asynchronně předává zprávu z `ISource` bloku do tohoto `call` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.|
|[send_message](#send_message)|Synchronně předává zprávu z `ISource` bloku do tohoto `call` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.|
|[supports_anonymous_source](#supports_anonymous_source)|Přepíše metodu `supports_anonymous_source`, aby označovala, že tento blok může přijímat zprávy, které mu byly nabídnuty zdrojem, který není propojen. (Overrides [ITarget:: supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ITarget](itarget-class.md)

[target_block](target-block-class.md)

`call`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>volání

Vytvoří blok pro zasílání zpráv `call`.

```cpp
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```

### <a name="parameters"></a>Parametry

*_Func*<br/>
Funkce, která bude vyvolána pro každou přijatou zprávu.

*_Filter*<br/>
Funkce filtru, která určuje, zda mají být přijaty nabízené zprávy.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `call`

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `call` Použitý objekt `Scheduler` je odvozen skupinou plánu.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PScheduleGroup`.

Typ `_Call_method` je funktor s podpisovým `void (T const &)`, který je vyvolán pomocí tohoto `call` bloku zpráv pro zpracování zprávy.

Typ `filter_method` je funktor s podpisovým `bool (T const &)`, který je vyvolán pomocí tohoto `call` bloku zpráv k určení, zda by měla přijmout nabízenou zprávu.

## <a name="dtor"></a>~ volání

Odstraní blok zasílání zpráv `call`.

```cpp
~call();
```

## <a name="process_input_messages"></a>process_input_messages

Spustí funkci volání na vstupních zprávách.

```cpp
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

## <a name="process_message"></a>process_message

Zpracuje zprávu, kterou přijal tento `call` blok pro zasílání zpráv.

```cpp
virtual void process_message(_Inout_ message<T>* _PMessage);
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na zprávu, která má být zpracována.

## <a name="propagate_message"></a>propagate_message

Asynchronně předává zprávu z `ISource` bloku do tohoto `call` bloku zpráv. Je vyvolána metodou `propagate`, když je volána pomocí zdrojového bloku.

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

## <a name="send_message"></a>send_message

Synchronně předává zprávu z `ISource` bloku do tohoto `call` bloku zpráv. Je vyvolána metodou `send`, když je volána pomocí zdrojového bloku.

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

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[transformer – třída](transformer-class.md)
