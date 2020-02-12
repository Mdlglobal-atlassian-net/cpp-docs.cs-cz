---
title: ITarget – třída
ms.date: 11/04/2016
f1_keywords:
- ITarget
- AGENTS/concurrency::ITarget
- AGENTS/concurrency::ITarget::propagate
- AGENTS/concurrency::ITarget::send
- AGENTS/concurrency::ITarget::supports_anonymous_source
- AGENTS/concurrency::ITarget::link_source
- AGENTS/concurrency::ITarget::unlink_source
- AGENTS/concurrency::ITarget::unlink_sources
helpviewer_keywords:
- ITarget class
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
ms.openlocfilehash: dc9eacad744536e640417a4ebf51b975bd05bcc7
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142033"
---
# <a name="itarget-class"></a>ITarget – třída

Třída `ITarget` je rozhraní pro všechny cílové bloky. Cílové bloky využívají pro `ISource` bloků zprávy, které jim nabízí.

## <a name="syntax"></a>Syntaxe

```cpp
template<class T>
class ITarget;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Datový typ datové části v rámci zpráv přijatých cílovým blokem.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`filter_method`|Signatura jakékoli metody používané blokem, která vrací `bool` hodnotu k určení, zda má být nabídnutá zpráva přijata.|
|`type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ ITarget destruktor](#dtor)|Odstraní objekt `ITarget`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[šířit](#propagate)|Při přepsání v odvozené třídě asynchronně předává zprávu ze zdrojového bloku do tohoto cílového bloku.|
|[posílají](#send)|Při přepsání v odvozené třídě synchronně předává zprávu cílovému bloku.|
|[supports_anonymous_source](#supports_anonymous_source)|Při přepsání v odvozené třídě vrátí hodnotu true nebo false v závislosti na tom, zda blok zprávy akceptuje zprávy nabízené zdrojem, který není propojen s ním. Pokud přepsaná metoda vrátí **hodnotu true**, nemůže cíl odložit nabízenou zprávu, protože spotřeba odložené zprávy v pozdější době vyžaduje, aby byl zdroj identifikován v registru zdrojového odkazu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[link_source](#link_source)|Při přepsání v odvozené třídě propojí zadaný zdrojový blok s tímto `ITarget`m blokem.|
|[unlink_source](#unlink_source)|Při přepsání v odvozené třídě odpojí zadaný zdrojový blok od tohoto bloku `ITarget`.|
|[unlink_sources](#unlink_sources)|Při přepsání v odvozené třídě odpojí všechny zdrojové bloky z tohoto bloku `ITarget`.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ ITarget

Odstraní objekt `ITarget`.

```cpp
virtual ~ITarget();
```

## <a name="link_source"></a>link_source

Při přepsání v odvozené třídě propojí zadaný zdrojový blok s tímto `ITarget`m blokem.

```cpp
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
`ISource` blok, který je propojen s tímto blokem `ITarget`.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána přímo v bloku `ITarget`. Bloky by měly být propojeny společně pomocí metody `link_target` v blocích `ISource`, která vyvolá metodu `link_source` na odpovídajícím cíli.

## <a name="propagate"></a>šířit

Při přepsání v odvozené třídě asynchronně předává zprávu ze zdrojového bloku do tohoto cílového bloku.

```cpp
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud je `NULL`parametr `_PMessage` nebo `_PSource`.

## <a name="send"></a>posílají

Při přepsání v odvozené třídě synchronně předává zprávu cílovému bloku.

```cpp
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel na objekt `message`.

*_PSource*<br/>
Ukazatel na zdrojový blok, který nabízí zprávu.

### <a name="return-value"></a>Návratová hodnota

[Message_status](concurrency-namespace-enums.md) údaj o tom, co se cíli rozhodl s touto zprávou.

### <a name="remarks"></a>Poznámky

Metoda vyvolá výjimku [invalid_argument](../../../standard-library/invalid-argument-class.md) , pokud je `NULL`parametr `_PMessage` nebo `_PSource`.

Použití metody `send` mimo zahájení zprávy a šíření zpráv v síti je nebezpečné a může vést k zablokování.

Když `send` vrátí, zpráva buď již byla přijata, a převedena do cílového bloku, nebo byla odmítnuta cílem.

## <a name="supports_anonymous_source"></a>supports_anonymous_source

Při přepsání v odvozené třídě vrátí hodnotu true nebo false v závislosti na tom, zda blok zprávy akceptuje zprávy nabízené zdrojem, který není propojen s ním. Pokud přepsaná metoda vrátí **hodnotu true**, nemůže cíl odložit nabízenou zprávu, protože spotřeba odložené zprávy bude v pozdější době vyžadovat identifikaci zdroje v registru odkazů sourse.

```cpp
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud blok může přijmout zprávu ze zdroje, který je neodkazuje na **NEPRAVDA** , jinak.

## <a name="unlink_source"></a>unlink_source

Při přepsání v odvozené třídě odpojí zadaný zdrojový blok od tohoto bloku `ITarget`.

```cpp
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
Odpojování `ISource`ho bloku z tohoto bloku `ITarget`.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána přímo v bloku `ITarget`. Bloky by měly být odpojeny pomocí `unlink_target` nebo `unlink_targets` metody v `ISource` blocích, což vyvolá metodu `unlink_source` na odpovídajícím cíli.

## <a name="unlink_sources"></a>unlink_sources

Při přepsání v odvozené třídě odpojí všechny zdrojové bloky z tohoto bloku `ITarget`.

```cpp
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ISource – třída](isource-class.md)
