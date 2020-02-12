---
title: multitype_join – třída
ms.date: 11/04/2016
f1_keywords:
- multitype_join
- AGENTS/concurrency::multitype_join
- AGENTS/concurrency::multitype_join::multitype_join
- AGENTS/concurrency::multitype_join::accept
- AGENTS/concurrency::multitype_join::acquire_ref
- AGENTS/concurrency::multitype_join::consume
- AGENTS/concurrency::multitype_join::link_target
- AGENTS/concurrency::multitype_join::release
- AGENTS/concurrency::multitype_join::release_ref
- AGENTS/concurrency::multitype_join::reserve
- AGENTS/concurrency::multitype_join::unlink_target
- AGENTS/concurrency::multitype_join::unlink_targets
helpviewer_keywords:
- multitype_join class
ms.assetid: 236e87a0-4867-49fd-869a-bef4010e49a7
ms.openlocfilehash: 4214c43fa0d0ab8fdd29ed54738c19f72a07267a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77138955"
---
# <a name="multitype_join-class"></a>multitype_join – třída

`multitype_join` blok zasílání zpráv je multi-source blok pro zasílání zpráv s jedním cílem, který kombinuje zprávy různých typů od každého ze svých zdrojů a nabízí řazenou kolekci členů kombinovaných zpráv do svých cílů.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename T,
    join_type _Jtype = non_greedy
>
class multitype_join: public ISource<typename _Unwrap<T>::type>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
`tuple` typ datové části zpráv, které byly připojeny a šířeny blokem.

*_Jtype*<br/>
Typ `join` blok je, buď `greedy` nebo `non_greedy`

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[multitype_join](#ctor)|Přetíženo. Vytvoří blok pro zasílání zpráv `multitype_join`.|
|[~ multitype_join destruktor](#dtor)|Odstraní blok zasílání zpráv `multitype_join`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[vyjádřit](#accept)|Přijme zprávu, kterou nabídl tento `multitype_join` blok, a přenáší vlastnictví volajícímu.|
|[acquire_ref](#acquire_ref)|Získá počet odkazů na tomto `multitype_join`ovém bloku pro zasílání zpráv, aby se zabránilo odstranění.|
|[každém](#consume)|Spotřebovává zprávu, kterou dřív nabídl `multitype_join` blok pro zasílání zpráv, a úspěšně ji rezervoval cíl a přenáší vlastnictví volajícímu.|
|[link_target](#link_target)|Propojí cílový blok s tímto `multitype_join`m blokem pro zasílání zpráv.|
|[předběžné](#release)|Uvolní předchozí úspěšnou rezervaci zprávy.|
|[release_ref](#release_ref)|Uvolní počet odkazů v tomto `multiple_join`ovém bloku pro zasílání zpráv.|
|[rezervační](#reserve)|Vyhradí zprávu, kterou dřív nabídl tento `multitype_join` blok pro zasílání zpráv.|
|[unlink_target](#unlink_target)|Odpojí cílový blok od tohoto `multitype_join`ho bloku pro zasílání zpráv.|
|[unlink_targets](#unlink_targets)|Odpojí všechny cíle od tohoto `multitype_join`ho bloku pro zasílání zpráv. (Overrides [ISource:: unlink_targets](isource-class.md#unlink_targets).)|

## <a name="remarks"></a>Poznámky

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

`multitype_join`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept"></a>vyjádřit

Přijme zprávu, kterou nabídl tento `multitype_join` blok, a přenáší vlastnictví volajícímu.

```cpp
virtual message<_Destination_type>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `accept`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zprávu, na kterou má volající nyní vlastnictví.

## <a name="acquire_ref"></a>acquire_ref

Získá počet odkazů na tomto `multitype_join`ovém bloku pro zasílání zpráv, aby se zabránilo odstranění.

```cpp
virtual void acquire_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který volá tuto metodu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je propojen s tímto zdrojem během metody `link_target`.

## <a name="consume"></a>každém

Spotřebovává zprávu, kterou dřív nabídl `multitype_join` blok pro zasílání zpráv, a úspěšně ji rezervoval cíl a přenáší vlastnictví volajícímu.

```cpp
virtual message<_Destination_type>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
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

## <a name="link_target"></a>link_target

Propojí cílový blok s tímto `multitype_join`m blokem pro zasílání zpráv.

```cpp
virtual void link_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na blok `ITarget`, který se má připojit k tomuto `multitype_join` bloku zpráv.

## <a name="ctor"></a>multitype_join

Vytvoří blok pro zasílání zpráv `multitype_join`.

```cpp
explicit multitype_join(
    T _Tuple);

multitype_join(
    Scheduler& _PScheduler,
    T _Tuple);

multitype_join(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

multitype_join(
    multitype_join&& _Join);
```

### <a name="parameters"></a>Parametry

*_Tuple*<br/>
`tuple` zdrojů pro tento blok zasílání zpráv `multitype_join`

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `multitype_join`

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `multitype_join` Použitý objekt `Scheduler` je odvozen skupinou plánu.

*_Join*<br/>
`multitype_join` blok pro zasílání zpráv, ze kterého se má kopírovat. Všimněte si, že původní objekt je osamocený, takže se tento konstruktor přesune.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PScheduleGroup`.

Konstrukce přesunutí se neprovádí za zámkem, což znamená, že je až pro uživatele, aby se zajistilo, že v době přesunutí nejsou v letadle žádné nevýznamové úlohy. Jinak může dojít k mnoha Races, což vede k výjimkám nebo nekonzistentnímu stavu.

## <a name="dtor"></a>~ multitype_join

Odstraní blok zasílání zpráv `multitype_join`.

```cpp
~multitype_join();
```

## <a name="release"></a>předběžné

Uvolní předchozí úspěšnou rezervaci zprávy.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` vydaných `message` objektu.

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `release`.

## <a name="release_ref"></a>release_ref

Uvolní počet odkazů v tomto `multiple_join`ovém bloku pro zasílání zpráv.

```cpp
virtual void release_ref(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který volá tuto metodu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je odpojování od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky rezervované pro cílový blok.

## <a name="reserve"></a>rezervační

Vyhradí zprávu, kterou dřív nabídl tento `multitype_join` blok pro zasílání zpráv.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `reserve`.

### <a name="return-value"></a>Návratová hodnota

`true`, zda byla zpráva úspěšně rezervována, `false` jinak. Rezervace mohou selhat z mnoha důvodů, včetně: zpráva byla již rezervována nebo přijata jiným cílem, zdroj může zamítnout rezervace atd.

### <a name="remarks"></a>Poznámky

Po volání `reserve`, je-li tato operace úspěšná, je nutné volat buď `consume` nebo `release`, aby bylo možné převzít nebo dát k dispozici zprávu, v uvedeném pořadí.

## <a name="unlink_target"></a>unlink_target

Odpojí cílový blok od tohoto `multitype_join`ho bloku pro zasílání zpráv.

```cpp
virtual void unlink_target(_Inout_ ITarget<_Destination_type>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na blok `ITarget`, který se má odpojit od `multitype_join` bloku zpráv.

## <a name="unlink_targets"></a>unlink_targets

Odpojí všechny cíle od tohoto `multitype_join`ho bloku pro zasílání zpráv.

```cpp
virtual void unlink_targets();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[choice – třída](choice-class.md)<br/>
[join – třída](join-class.md)
