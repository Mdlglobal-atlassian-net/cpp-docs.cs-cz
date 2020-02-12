---
title: message – třída
ms.date: 11/04/2016
f1_keywords:
- message
- AGENTS/concurrency::message
- AGENTS/concurrency::message::message
- AGENTS/concurrency::message::add_ref
- AGENTS/concurrency::message::msg_id
- AGENTS/concurrency::message::remove_ref
- AGENTS/concurrency::message::payload
helpviewer_keywords:
- message class
ms.assetid: 3e1f3505-6c0c-486c-8191-666d0880ec62
ms.openlocfilehash: 700d052b6f22c970387a3ab45d299538a5b74e1b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139532"
---
# <a name="message-class"></a>message – třída

Základní obálka zprávy obsahující datovou část dat, která se předává mezi bloky pro zasílání zpráv.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ datové části v rámci zprávy.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[message](#ctor)|Přetíženo. Vytvoří objekt `message`.|
|[~ Message – destruktor](#dtor)|Odstraní objekt `message`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add_ref](#add_ref)|Přidá do počtu odkazů pro objekt `message`. Používá se pro bloky zpráv, které vyžadují počítání odkazů, aby bylo možné určit dobu života zprávy.|
|[msg_id](#msg_id)|Vrátí ID objektu `message`.|
|[remove_ref](#remove_ref)|Odečte od počtu odkazů pro objekt `message`. Používá se pro bloky zpráv, které vyžadují počítání odkazů, aby bylo možné určit dobu života zprávy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[Délka](#payload)|Datová část objektu `message`.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`message`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="add_ref"></a>add_ref

Přidá do počtu odkazů pro objekt `message`. Používá se pro bloky zpráv, které vyžadují počítání odkazů, aby bylo možné určit dobu života zprávy.

```cpp
long add_ref();
```

### <a name="return-value"></a>Návratová hodnota

Nová hodnota počtu odkazů

## <a name="ctor"></a>Zpráva

Vytvoří objekt `message`.

```cpp
message(
    T const& _P);

message(
    T const& _P,
    runtime_object_identity _Id);

message(
    message const& _Msg);

message(
    _In_ message const* _Msg);
```

### <a name="parameters"></a>Parametry

*_P*<br/>
Datová část této zprávy

*_Id*<br/>
Jedinečné ID této zprávy

*_Msg*<br/>
Odkaz nebo ukazatel na objekt `message`.

### <a name="remarks"></a>Poznámky

Konstruktor, který přebírá ukazatel na objekt `message` jako argument vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud je parametr `_Msg` `NULL`.

## <a name="dtor"></a>~ Zpráva

Odstraní objekt `message`.

```cpp
virtual ~message();
```

## <a name="msg_id"></a>msg_id

Vrátí ID objektu `message`.

```cpp
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Návratová hodnota

`runtime_object_identity` objektu `message`

## <a name="payload"></a>Délka

Datová část objektu `message`.

```cpp
T const payload;
```

## <a name="remove_ref"></a>remove_ref

Odečte od počtu odkazů pro objekt `message`. Používá se pro bloky zpráv, které vyžadují počítání odkazů, aby bylo možné určit dobu života zprávy.

```cpp
long remove_ref();
```

### <a name="return-value"></a>Návratová hodnota

Nová hodnota počtu odkazů

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
