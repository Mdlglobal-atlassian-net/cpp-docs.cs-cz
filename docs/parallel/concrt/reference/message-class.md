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
ms.openlocfilehash: 83cfdb5807581f7092709691a1839052abdd657c
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343854"
---
# <a name="message-class"></a>message – třída

Obálky základní zprávy obsahující datovou část předávaný mezi bloky zasílání zpráv.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class message : public ::Concurrency::details::_Runtime_object;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ datové části v rámci zprávy.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[message](#ctor)|Přetíženo. Vytvoří `message` objektu.|
|[~ message – destruktor](#dtor)|Odstraní `message` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[add_ref](#add_ref)|Přidá počet odkazů `message` objektu. Používá se pro bloky zpráv, které potřebují k určení doby života zprávy pro počítání odkazů.|
|[msg_id](#msg_id)|Vrátí ID `message` objektu.|
|[remove_ref](#remove_ref)|Odečte od počet odkazů `message` objektu. Používá se pro bloky zpráv, které potřebují k určení doby života zprávy pro počítání odkazů.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[datová část](#payload)|Datová část `message` objektu.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`message`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="add_ref"></a> add_ref –

Přidá počet odkazů `message` objektu. Používá se pro bloky zpráv, které potřebují k určení doby života zprávy pro počítání odkazů.

```
long add_ref();
```

### <a name="return-value"></a>Návratová hodnota

Nová hodnota počet odkazů.

##  <a name="ctor"></a> Zpráva

Vytvoří `message` objektu.

```
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
Datová část této zprávy.

*ID _ovládacího*<br/>
Jedinečné ID této zprávy.

*_Msg*<br/>
Odkaz nebo ukazatel `message` objektu.

### <a name="remarks"></a>Poznámky

Konstruktor, který bere ukazatel na `message` jak argument vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimka Pokud parametr `_Msg` je `NULL`.

##  <a name="dtor"></a> ~ zprávy

Odstraní `message` objektu.

```
virtual ~message();
```

##  <a name="msg_id"></a> msg_id

Vrátí ID `message` objektu.

```
runtime_object_identity msg_id() const;
```

### <a name="return-value"></a>Návratová hodnota

`runtime_object_identity` z `message` objektu.

##  <a name="payload"></a> datová část

Datová část `message` objektu.

```
T const payload;
```

##  <a name="remove_ref"></a> remove_ref –

Odečte od počet odkazů `message` objektu. Používá se pro bloky zpráv, které potřebují k určení doby života zprávy pro počítání odkazů.

```
long remove_ref();
```

### <a name="return-value"></a>Návratová hodnota

Nová hodnota počet odkazů.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
