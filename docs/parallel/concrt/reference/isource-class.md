---
title: ISource – třída
ms.date: 11/04/2016
f1_keywords:
- ISource
- AGENTS/concurrency::ISource
- AGENTS/concurrency::ISource::accept
- AGENTS/concurrency::ISource::acquire_ref
- AGENTS/concurrency::ISource::consume
- AGENTS/concurrency::ISource::link_target
- AGENTS/concurrency::ISource::release
- AGENTS/concurrency::ISource::release_ref
- AGENTS/concurrency::ISource::reserve
- AGENTS/concurrency::ISource::unlink_target
- AGENTS/concurrency::ISource::unlink_targets
helpviewer_keywords:
- ISource class
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
ms.openlocfilehash: 4e96dc11455015a83af9be545ba15c96b5e2f779
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620516"
---
# <a name="isource-class"></a>ISource – třída

`ISource` Třídy je rozhraní pro všechny zdrojové bloky. Zdrojové bloky šíření zpráv `ITarget` bloky.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ISource;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ datové části v rámci zprávy vytvářené zdrojovým blokem.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`source_type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ ISource – destruktor](#dtor)|Odstraní `ISource` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Přijmout](#accept)|Při přepisu v odvozené třídě, přijímá zprávy, které byly nabízeny situace `ISource` bloku, přenos vlastnictví volajícímu.|
|[acquire_ref](#acquire_ref)|Při přepisu v odvozené třídě, získá počet odkazů na tomto `ISource` bloku, abyste zabránili odstranění.|
|[využívání](#consume)|Při přepisu v odvozené třídě, využívá zprávu nabízely dříve v tomto `ISource` blokovat a úspěšně vyhrazená v cíli, přenos vlastnictví volajícímu.|
|[link_target](#link_target)|Při přepisu v odvozené třídě, odkazuje na tento cílový blok `ISource` bloku.|
|[Vydání verze](#release)|Při přepisu v odvozené třídě, uvolní předchozí vyhrazení úspěšné zprávy.|
|[release_ref](#release_ref)|Při přepisu v odvozené třídě, uvolní počet odkazů na tomto `ISource` bloku.|
|[Rezervovat](#reserve)|Při přepisu v odvozené třídě, vyhradí zprávu nabízely dříve v tomto `ISource` bloku.|
|[unlink_target](#unlink_target)|Při přepisu v odvozené třídě, nebude odpojen cílový blok z tohoto `ISource` blokovat, pokud nalezen dříve propojení.|
|[unlink_targets](#unlink_targets)|Při přepisu v odvozené třídě, nebude odpojen všem cílovým blokům z tohoto `ISource` bloku.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="accept"></a> Přijmout

Při přepisu v odvozené třídě, přijímá zprávy, které byly nabízeny situace `ISource` bloku, přenos vlastnictví volajícímu.

```
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.

*_PTarget*<br/>
Ukazatel na cílový blok, který volá `accept` metody.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zprávu, která má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

`accept` Metoda je volána metodou cíl, zatímco zpráva nabízí situace `ISource` bloku. Vrácený ukazatel zpráva může být jiný než ten, předán `propagate` metodu `ITarget` blokovat, pokud se tento zdroj rozhodne vytvořit kopii zprávy.

##  <a name="acquire_ref"></a> acquire_ref –

Při přepisu v odvozené třídě, získá počet odkazů na tomto `ISource` bloku, abyste zabránili odstranění.

```
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který je volání této metody.

### <a name="remarks"></a>Poznámky

Tato metoda je volána `ITarget` objekt, který se odkazuje tento zdroj během `link_target` metody.

##  <a name="consume"></a> využívání

Při přepisu v odvozené třídě, využívá zprávu nabízely dříve v tomto `ISource` blokovat a úspěšně vyhrazená v cíli, přenos vlastnictví volajícímu.

```
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z vyhrazených `message` objektu.

*_PTarget*<br/>
Ukazatel na cílový blok, který volá `consume` metody.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `message` volající má teď vlastnictví objektu.

### <a name="remarks"></a>Poznámky

`consume` Metoda je podobná `accept`, ale musí vždy předcházet volání `reserve` vrácená **true**.

##  <a name="dtor"></a> ~ Isource –

Odstraní `ISource` objektu.

```
virtual ~ISource();
```

##  <a name="link_target"></a> link_target –

Při přepisu v odvozené třídě, odkazuje na tento cílový blok `ISource` bloku.

```
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, na které se odkazuje na tuto `ISource` bloku.

##  <a name="release"></a> Vydání verze

Při přepisu v odvozené třídě, uvolní předchozí vyhrazení úspěšné zprávy.

```
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` z vyhrazených `message` objektu.

*_PTarget*<br/>
Ukazatel na cílový blok, který volá `release` metody.

##  <a name="release_ref"></a> release_ref –

Při přepisu v odvozené třídě, uvolní počet odkazů na tomto `ISource` bloku.

```
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který je volání této metody.

### <a name="remarks"></a>Poznámky

Tato metoda je volána `ITarget` objekt, který je právě byl odpojen od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky, které jsou vyhrazené pro cílový blok.

##  <a name="reserve"></a> Rezervovat

Při přepisu v odvozené třídě, vyhradí zprávu nabízely dříve v tomto `ISource` bloku.

```
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` Nabízených `message` objektu.

*_PTarget*<br/>
Ukazatel na cílový blok, který volá `reserve` metody.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud zpráva byla úspěšně vyhrazené, **false** jinak. Rezervace může selhat z mnoha důvodů včetně: byla zpráva již vyhrazena nebo přijatý jiný cíl, zdroj může zamítnout rezervace a tak dále.

### <a name="remarks"></a>Poznámky

Po zavolání `reserve`, pokud je úspěšná, musí buď volat `consume` nebo `release` aby bylo možné provést nebo vzdát vlastnictví zprávy, v uvedeném pořadí.

##  <a name="unlink_target"></a> unlink_target –

Při přepisu v odvozené třídě, nebude odpojen cílový blok z tohoto `ISource` blokovat, pokud nalezen dříve propojení.

```
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok se byl odpojen od to `ISource` bloku.

##  <a name="unlink_targets"></a> unlink_targets –

Při přepisu v odvozené třídě, nebude odpojen všem cílovým blokům z tohoto `ISource` bloku.

```
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ITarget – třída](itarget-class.md)
