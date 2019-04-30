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
ms.openlocfilehash: 59a0f66a0ba3b10c3307a835ff6ccaa216596538
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339535"
---
# <a name="itarget-class"></a>ITarget – třída

`ITarget` Třídy je rozhraní pro všechny cílové bloky. Cílovým blokům využívat zprávy, nabízí jim `ISource` bloky.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ITarget;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Datový typ datové části v rámci přijal cílový blok zpráv.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`filter_method`|Podpis blokem, který vrátí všechny metody `bool` hodnotu, která určí, zda by měl být přijat nabízené zprávy.|
|`type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[~ITarget Destructor](#dtor)|Odstraní `ITarget` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[propagate](#propagate)|Při přepisu v odvozené třídě, asynchronně předává zprávy z zdrojový blok pro tento cílový blok.|
|[Odeslat](#send)|Při přepisu v odvozené třídě, synchronně předává zprávy na cílový blok.|
|[supports_anonymous_source](#supports_anonymous_source)|Při přepisu v odvozené třídě vrátí hodnotu PRAVDA nebo NEPRAVDA v závislosti na tom, zda blok zpráv přijímá zprávy nabízí zdrojem, který není přidružený k němu. Přepsané metody vrátí-li **true**, cílem nelze odložit nabízené zprávy, jako využití odloženou zprávu později vyžaduje zdroj musí identifikovat jeho sourse odkaz registru.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[link_source](#link_source)|Při přepisu v odvozené třídě, odkazuje na tento blok zadaný zdroj `ITarget` bloku.|
|[unlink_source](#unlink_source)|Při přepisu v odvozené třídě, nebude odpojen blok zadaný zdroj z tohoto `ITarget` bloku.|
|[unlink_sources](#unlink_sources)|Při přepisu v odvozené třídě, nebude odpojen všechny zdrojové bloky z tohoto `ITarget` bloku.|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ITarget`

## <a name="requirements"></a>Požadavky

**Záhlaví:** agents.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~ Itarget –

Odstraní `ITarget` objektu.

```
virtual ~ITarget();
```

##  <a name="link_source"></a> link_source –

Při přepisu v odvozené třídě, odkazuje na tento blok zadaný zdroj `ITarget` bloku.

```
virtual void link_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
`ISource` Blokovat, na které se odkazuje na tuto `ITarget` bloku.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána přímo na `ITarget` bloku. Bloky by měly být propojeny pomocí `link_target` metoda `ISource` bloků, které se vyvolá `link_source` metodu na odpovídající cíle.

##  <a name="propagate"></a> rozšíření

Při přepisu v odvozené třídě, asynchronně předává zprávy z zdrojový blok pro tento cílový blok.

```
virtual message_status propagate(
    _Inout_opt_ message<T>* _PMessage,
    _Inout_opt_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimku, pokud buď `_PMessage` nebo `_PSource` parametr je `NULL`.

##  <a name="send"></a> Odeslat

Při přepisu v odvozené třídě, synchronně předává zprávy na cílový blok.

```
virtual message_status send(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PMessage*<br/>
Ukazatel `message` objektu.

*_PSource*<br/>
Ukazatele na blok zdroje nabídky zprávy.

### <a name="return-value"></a>Návratová hodnota

A [message_status –](concurrency-namespace-enums.md) označení cíl rozhodla se zprávy.

### <a name="remarks"></a>Poznámky

Metoda vyvolá [invalid_argument](../../../standard-library/invalid-argument-class.md) výjimku, pokud buď `_PMessage` nebo `_PSource` parametr je `NULL`.

Použití `send` metoda mimo zahájení zprávu a šíření zpráv v rámci sítě je nebezpečné a může vést k zablokování.

Když `send` vrátí zprávy buď již byla přijata a přenést na cílový blok, nebo byla zamítnuta v cíli.

##  <a name="supports_anonymous_source"></a> supports_anonymous_source –

Při přepisu v odvozené třídě vrátí hodnotu PRAVDA nebo NEPRAVDA v závislosti na tom, zda blok zpráv přijímá zprávy nabízí zdrojem, který není přidružený k němu. Přepsané metody vrátí-li **true**, cílem nelze odložit nabízené zprávy, jako využití odloženou zprávu později vyžaduje zdroj musí identifikovat jeho sourse odkaz registru.

```
virtual bool supports_anonymous_source();
```

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud bloku může přijmout zprávy ze zdroje, který není přidružený k němu **false** jinak.

##  <a name="unlink_source"></a> unlink_source –

Při přepisu v odvozené třídě, nebude odpojen blok zadaný zdroj z tohoto `ITarget` bloku.

```
virtual void unlink_source(_Inout_ ISource<T>* _PSource) = 0;
```

### <a name="parameters"></a>Parametry

*_PSource*<br/>
`ISource` Bloku je byl odpojen od to `ITarget` bloku.

### <a name="remarks"></a>Poznámky

Tato funkce by neměla být volána přímo na `ITarget` bloku. Bloky by měl odpojení pomocí `unlink_target` nebo `unlink_targets` metody `ISource` bloků, které se vyvolá `unlink_source` metodu na odpovídající cíle.

##  <a name="unlink_sources"></a> unlink_sources –

Při přepisu v odvozené třídě, nebude odpojen všechny zdrojové bloky z tohoto `ITarget` bloku.

```
virtual void unlink_sources() = 0;
```

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[ISource – třída](isource-class.md)
