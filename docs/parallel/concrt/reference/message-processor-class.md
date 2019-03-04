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
ms.openlocfilehash: be6cb1c614a41919663a4cc063da66679556e498
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295237"
---
# <a name="messageprocessor-class"></a>message_processor – třída

`message_processor` Třída je abstraktní základní třída pro zpracování `message` objekty. Neexistuje žádná záruka na pořadí zpráv.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class message_processor;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ datové části v rámci zprávy zpracovává situace `message_processor` objektu.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`type`|Alias typu pro `T`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[async_send](#async_send)|Při přepisu v odvozené třídě, umístí zprávy asynchronně do bloku.|
|[sync_send](#sync_send)|Při přepisu v odvozené třídě, umístí zprávy synchronně do bloku.|
|[Počkej](#wait)|Při přepisu v odvozené třídě, čeká na dokončení všech asynchronních operací.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[process_incoming_message](#process_incoming_message)|Při přepisu v odvozené třídě, provádí dopředu zpracování zpráv do bloku. Volá se jednou pokaždé, když se přidá nová zpráva a fronta je nalezena prázdný.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`message_processor`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="async_send"></a> async_send –

Při přepisu v odvozené třídě, umístí zprávy asynchronně do bloku.

```
virtual void async_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
A `message` objektu k odesílání asynchronně.

### <a name="remarks"></a>Poznámky

Implementace by měly přepsat tuto metodu.

##  <a name="process_incoming_message"></a> process_incoming_message –

Při přepisu v odvozené třídě, provádí dopředu zpracování zpráv do bloku. Volá se jednou pokaždé, když se přidá nová zpráva a fronta je nalezena prázdný.

```
virtual void process_incoming_message() = 0;
```

### <a name="remarks"></a>Poznámky

Implementace bloku zpráv by měly přepsat tuto metodu.

##  <a name="sync_send"></a> sync_send –

Při přepisu v odvozené třídě, umístí zprávy synchronně do bloku.

```
virtual void sync_send(_Inout_opt_ message<T>* _Msg) = 0;
```

### <a name="parameters"></a>Parametry

*_Msg*<br/>
A `message` objekt se má poslat synchronně.

### <a name="remarks"></a>Poznámky

Implementace by měly přepsat tuto metodu.

##  <a name="wait"></a> Počkej

Při přepisu v odvozené třídě, čeká na dokončení všech asynchronních operací.

```
virtual void wait() = 0;
```

### <a name="remarks"></a>Poznámky

Implementace by měly přepsat tuto metodu.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ordered_message_processor – třída](ordered-message-processor-class.md)
