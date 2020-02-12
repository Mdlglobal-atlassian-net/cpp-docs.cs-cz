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
ms.openlocfilehash: a9ef9990db6376536f2f2a15c053b3b1d4ed12cf
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139322"
---
# <a name="isource-class"></a>ISource – třída

Třída `ISource` je rozhraní pro všechny zdrojové bloky. Zdrojové bloky šíří zprávy do bloků `ITarget`.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class ISource;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ datové části v rámci zpráv vyprodukovaných zdrojovým blokem.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`source_type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ ISource destruktor](#dtor)|Odstraní objekt `ISource`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[vyjádřit](#accept)|Při přepsání v odvozené třídě přijímá zprávu, která byla nabídnuta tímto `ISource`m blokem, převádění vlastnictví na volajícího.|
|[acquire_ref](#acquire_ref)|Při přepsání v odvozené třídě získá počet odkazů na tento blok `ISource`, aby se zabránilo odstranění.|
|[každém](#consume)|Při přepsání v odvozené třídě aplikace spotřebovává zprávu, kterou dřív nabídl tento `ISource` blok a úspěšně rezervoval cíl, a přenáší vlastnictví volajícímu.|
|[link_target](#link_target)|Při přepsání v odvozené třídě odkazuje cílový blok na tento `ISource`ový blok.|
|[předběžné](#release)|Při přepsání v odvozené třídě uvolní předchozí úspěšnou rezervaci zprávy.|
|[release_ref](#release_ref)|Při přepsání v odvozené třídě uvolní počet odkazů na tento blok `ISource`.|
|[rezervační](#reserve)|Při přepsání v odvozené třídě si vyhrazuje zprávu, kterou dřív nabídl tento `ISource` blok.|
|[unlink_target](#unlink_target)|Při přepsání v odvozené třídě odpojí cílový blok od tohoto bloku `ISource`, pokud se zjistilo, že byl dříve propojen.|
|[unlink_targets](#unlink_targets)|Při přepsání v odvozené třídě odpojí všechny cílové bloky z tohoto bloku `ISource`.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISource`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept"></a>vyjádřit

Při přepsání v odvozené třídě přijímá zprávu, která byla nabídnuta tímto `ISource`m blokem, převádění vlastnictví na volajícího.

```cpp
virtual message<T>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `accept`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zprávu, na kterou má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Metoda `accept` je volána cílem, zatímco je zpráva nabízena tímto `ISource` bloku. Vrácený ukazatel na zprávu může být jiný než ten, který se předává do metody `propagate` bloku `ITarget`, pokud se tento zdroj rozhodne vytvořit kopii zprávy.

## <a name="acquire_ref"></a>acquire_ref

Při přepsání v odvozené třídě získá počet odkazů na tento blok `ISource`, aby se zabránilo odstranění.

```cpp
virtual void acquire_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který volá tuto metodu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je propojen s tímto zdrojem během metody `link_target`.

## <a name="consume"></a>každém

Při přepsání v odvozené třídě aplikace spotřebovává zprávu, kterou dřív nabídl tento `ISource` blok a úspěšně rezervoval cíl, a přenáší vlastnictví volajícímu.

```cpp
virtual message<T>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `consume`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `message`, u kterého má volající nyní vlastnictví.

### <a name="remarks"></a>Poznámky

Metoda `consume` je podobná `accept`, ale vždy musí předcházet volání `reserve`, které vrátilo **hodnotu true**.

## <a name="dtor"></a>~ ISource

Odstraní objekt `ISource`.

```cpp
virtual ~ISource();
```

## <a name="link_target"></a>link_target

Při přepsání v odvozené třídě odkazuje cílový blok na tento `ISource`ový blok.

```cpp
virtual void link_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok propojený s tímto `ISource`m blokem.

## <a name="release"></a>předběžné

Při přepsání v odvozené třídě uvolní předchozí úspěšnou rezervaci zprávy.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `release`.

## <a name="release_ref"></a>release_ref

Při přepsání v odvozené třídě uvolní počet odkazů na tento blok `ISource`.

```cpp
virtual void release_ref(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který volá tuto metodu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je odpojování od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky rezervované pro cílový blok.

## <a name="reserve"></a>rezervační

Při přepsání v odvozené třídě si vyhrazuje zprávu, kterou dřív nabídl tento `ISource` blok.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `reserve`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva úspěšně rezervována, jinak **false** . Rezervace mohou selhat z mnoha důvodů, včetně: zpráva byla již rezervována nebo přijata jiným cílem, zdroj může zamítnout rezervace atd.

### <a name="remarks"></a>Poznámky

Po volání `reserve`, je-li tato operace úspěšná, je nutné volat buď `consume` nebo `release`, aby bylo možné převzít nebo dát k dispozici zprávu, v uvedeném pořadí.

## <a name="unlink_target"></a>unlink_target

Při přepsání v odvozené třídě odpojí cílový blok od tohoto bloku `ISource`, pokud se zjistilo, že byl dříve propojen.

```cpp
virtual void unlink_target(_Inout_ ITarget<T>* _PTarget) = 0;
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který je odpojování od tohoto `ISource`ho bloku.

## <a name="unlink_targets"></a>unlink_targets

Při přepsání v odvozené třídě odpojí všechny cílové bloky z tohoto bloku `ISource`.

```cpp
virtual void unlink_targets() = 0;
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ITarget – třída](itarget-class.md)
