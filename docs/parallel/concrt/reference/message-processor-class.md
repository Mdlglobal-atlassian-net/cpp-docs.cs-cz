---
title: message_processor – třída
ms.date: 11/04/2016
f1_keywords:
- message_processor
- AGENTS/concurrency::message_processor
- AGENTS/concurrency::message_processor::async_send
- AGENTS/concurrency::message_processor::sync_send
- AGENTS/concurrency::message_processor::wait
- AGENTS/concurrency::message_processor::process_incoming_message
helpviewer_keywords:
- message_processor class
ms.assetid: 23afb052-daa7-44ed-bf24-d2513db748da
ms.openlocfilehash: 88944b2d935eebd0e031be1431c2a0f4efa3d760
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139472"
---
# <a name="message_processor-class"></a>message_processor – třída

Třída `message_processor` je abstraktní základní třída pro zpracování objektů `message`. Na řazení zpráv není nijak zaručeno.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class message_processor;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ datové části v rámci zpráv zpracovávaných tímto objektem `message_processor`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`type`|Alias typu pro `T`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[async_send](#async_send)|Při přepsání v odvozené třídě umístí zprávy do bloku asynchronně.|
|[sync_send](#sync_send)|Při přepsání v odvozené třídě umístí zprávy do bloku synchronně.|
|[Počkej](#wait)|Při přepsání v odvozené třídě čeká na dokončení všech asynchronních operací.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Při přepsání v odvozené třídě provede zpracování zpráv do bloku. Volá se jednou při každém přidání nové zprávy a ta se najde jako prázdná.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`message_processor`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="async_send"></a>async_send

Při přepsání v odvozené třídě umístí zprávy do bloku asynchronně.

```cpp
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Objekt `message`, který se má odeslat asynchronně.

### <a name="remarks"></a>Poznámky

Implementace procesoru by měla přepsat tuto metodu.

## <a name="process_incoming_message"></a>process_incoming_message

Při přepsání v odvozené třídě provede zpracování zpráv do bloku. Volá se jednou při každém přidání nové zprávy a ta se najde jako prázdná.

```cpp
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Poznámky

Implementace bloku zprávy by měly přepsat tuto metodu.

## <a name="sync_send"></a>sync_send

Při přepsání v odvozené třídě umístí zprávy do bloku synchronně.

```cpp
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
Objekt `message`, který se má synchronně odeslat.

### <a name="remarks"></a>Poznámky

Implementace procesoru by měla přepsat tuto metodu.

## <a name="wait"></a>Počkej

Při přepsání v odvozené třídě čeká na dokončení všech asynchronních operací.

```cpp
virtual void wait() = 0;
```

### <a name="remarks"></a>Poznámky

Implementace procesoru by měla přepsat tuto metodu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ordered_message_processor – třída](ordered-message-processor-class.md)
