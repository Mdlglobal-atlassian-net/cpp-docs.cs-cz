---
title: Třída choice
ms.date: 11/04/2016
f1_keywords:
- choice
- AGENTS/concurrency::choice
- AGENTS/concurrency::choice::choice
- AGENTS/concurrency::choice::accept
- AGENTS/concurrency::choice::acquire_ref
- AGENTS/concurrency::choice::consume
- AGENTS/concurrency::choice::has_value
- AGENTS/concurrency::choice::index
- AGENTS/concurrency::choice::link_target
- AGENTS/concurrency::choice::release
- AGENTS/concurrency::choice::release_ref
- AGENTS/concurrency::choice::reserve
- AGENTS/concurrency::choice::unlink_target
- AGENTS/concurrency::choice::unlink_targets
- AGENTS/concurrency::choice::value
helpviewer_keywords:
- choice class
ms.assetid: 4157a539-d5c2-4161-b1ab-536ce2888397
ms.openlocfilehash: 3e718d0d34580d3bf2f13937159e431134631218
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142219"
---
# <a name="choice-class"></a>Třída choice

`choice` blok pro zasílání zpráv je vícenásobný zdroj s jedním cílovým blokem, který představuje interakci toku řízení se sadou zdrojů. Blok voleb počká, až jeden z několika zdrojů vytvoří zprávu, a bude rozšiřovat index zdroje, který zprávu vytvořil.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    class T
>
class choice: public ISource<size_t>;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Typ založený `tuple`reprezentující datové části vstupních zdrojů.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`type`|Alias typu pro `T`.|

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[libovolném](#ctor)|Přetíženo. Vytvoří blok pro zasílání zpráv `choice`.|
|[~ Choice – destruktor](#dtor)|Odstraní blok zasílání zpráv `choice`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[vyjádřit](#accept)|Přijme zprávu, kterou nabídl tento `choice` blok, a přenáší vlastnictví volajícímu.|
|[acquire_ref](#acquire_ref)|Získá počet odkazů na tomto `choice`ovém bloku pro zasílání zpráv, aby se zabránilo odstranění.|
|[každém](#consume)|Využívá zprávu, kterou dřív nabídl tento `choice` blok pro zasílání zpráv a který je úspěšně rezervovaný cílem a přenáší vlastnictví volajícímu.|
|[has_value](#has_value)|Kontroluje, zda byl tento blok zasílání zpráv `choice` inicializován s hodnotou.|
|[indexovacím](#index)|Vrátí index do `tuple` představující prvek vybraný v bloku `choice` pro zasílání zpráv.|
|[link_target](#link_target)|Propojí cílový blok s tímto `choice`m blokem pro zasílání zpráv.|
|[předběžné](#release)|Uvolní předchozí úspěšnou rezervaci zprávy.|
|[release_ref](#release_ref)|Uvolní počet odkazů v tomto `choice`ovém bloku pro zasílání zpráv.|
|[rezervační](#reserve)|Vyhradí zprávu, kterou dřív nabídl tento `choice` blok pro zasílání zpráv.|
|[unlink_target](#unlink_target)|Odpojí cílový blok od tohoto `choice`ho bloku pro zasílání zpráv.|
|[unlink_targets](#unlink_targets)|Odpojí všechny cíle od tohoto `choice`ho bloku pro zasílání zpráv. (Overrides [ISource:: unlink_targets](isource-class.md#unlink_targets).)|
|[value](#value)|Získá zprávu, jejíž index byl vybrán v rámci `choice`ho bloku pro zasílání zpráv.|

## <a name="remarks"></a>Poznámky

Blok voleb zajistí, že se bude používat jenom jedna z příchozích zpráv.

Další informace najdete v tématu [asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[ISource](isource-class.md)

`choice`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Agents. h

**Obor názvů:** souběžnost

## <a name="accept"></a>vyjádřit

Přijme zprávu, kterou nabídl tento `choice` blok, a přenáší vlastnictví volajícímu.

```cpp
virtual message<size_t>* accept(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` nabízeného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `accept`.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na zprávu, na kterou má volající nyní vlastnictví.

## <a name="acquire_ref"></a>acquire_ref

Získá počet odkazů na tomto `choice`ovém bloku pro zasílání zpráv, aby se zabránilo odstranění.

```cpp
virtual void acquire_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který volá tuto metodu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je propojen s tímto zdrojem během metody `link_target`.

## <a name="ctor"></a>libovolném

Vytvoří blok pro zasílání zpráv `choice`.

```cpp
explicit choice(
    T _Tuple);

choice(
    Scheduler& _PScheduler,
    T _Tuple);

choice(
    ScheduleGroup& _PScheduleGroup,
    T _Tuple);

choice(
    choice&& _Choice);
```

### <a name="parameters"></a>Parametry

*_Tuple*<br/>
`tuple` zdrojů pro výběr.

*_PScheduler*<br/>
Objekt `Scheduler`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `choice`

*_PScheduleGroup*<br/>
Objekt `ScheduleGroup`, ve kterém je naplánována úloha šíření pro blok zasílání zpráv `choice` Použitý objekt `Scheduler` je odvozen skupinou plánu.

*_Choice*<br/>
`choice` blok pro zasílání zpráv, ze kterého se má kopírovat. Všimněte si, že původní objekt je osamocený, takže se tento konstruktor přesune.

### <a name="remarks"></a>Poznámky

Modul runtime používá výchozí Plánovač, pokud nezadáte parametry `_PScheduler` nebo `_PScheduleGroup`.

Konstrukce přesunutí se neprovádí za zámkem, což znamená, že je až pro uživatele, aby se zajistilo, že v době přesunutí nejsou v letadle žádné nevýznamové úlohy. Jinak může dojít k mnoha Races, což vede k výjimkám nebo nekonzistentnímu stavu.

## <a name="dtor"></a>~ volba

Odstraní blok zasílání zpráv `choice`.

```cpp
~choice();
```

## <a name="consume"></a>každém

Využívá zprávu, kterou dřív nabídl tento `choice` blok pro zasílání zpráv a který je úspěšně rezervovaný cílem a přenáší vlastnictví volajícímu.

```cpp
virtual message<size_t>* consume(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
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

## <a name="has_value"></a>has_value

Kontroluje, zda byl tento blok zasílání zpráv `choice` inicializován s hodnotou.

```cpp
bool has_value() const;
```

### <a name="return-value"></a>Návratová hodnota

**true** , pokud blok obdržel hodnotu, jinak **false** .

## <a name="index"></a>indexovacím

Vrátí index do `tuple` představující prvek vybraný v bloku `choice` pro zasílání zpráv.

```cpp
size_t index();
```

### <a name="return-value"></a>Návratová hodnota

Index zprávy

### <a name="remarks"></a>Poznámky

Datovou část zprávy lze extrahovat pomocí metody `get`.

## <a name="link_target"></a>link_target

Propojí cílový blok s tímto `choice`m blokem pro zasílání zpráv.

```cpp
virtual void link_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na blok `ITarget`, který se má připojit k tomuto `choice` bloku zpráv.

## <a name="release"></a>předběžné

Uvolní předchozí úspěšnou rezervaci zprávy.

```cpp
virtual void release(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` vydaných `message` objektu.

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `release`.

## <a name="release_ref"></a>release_ref

Uvolní počet odkazů v tomto `choice`ovém bloku pro zasílání zpráv.

```cpp
virtual void release_ref(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na cílový blok, který volá tuto metodu.

### <a name="remarks"></a>Poznámky

Tato metoda je volána objektem `ITarget`, který je odpojování od tohoto zdroje. Zdrojový blok může uvolnit všechny prostředky rezervované pro cílový blok.

## <a name="reserve"></a>rezervační

Vyhradí zprávu, kterou dřív nabídl tento `choice` blok pro zasílání zpráv.

```cpp
virtual bool reserve(
    runtime_object_identity _MsgId,
    _Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_MsgId*<br/>
`runtime_object_identity` rezervovaného objektu `message`

*_PTarget*<br/>
Ukazatel na cílový blok, který volá metodu `reserve`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud byla zpráva úspěšně rezervována, jinak **false** . Rezervace mohou selhat z mnoha důvodů, včetně: zpráva byla již rezervována nebo přijata jiným cílem, zdroj může zamítnout rezervace atd.

### <a name="remarks"></a>Poznámky

Po volání `reserve`, je-li tato operace úspěšná, je nutné volat buď `consume` nebo `release`, aby bylo možné převzít nebo dát k dispozici zprávu, v uvedeném pořadí.

## <a name="unlink_target"></a>unlink_target

Odpojí cílový blok od tohoto `choice`ho bloku pro zasílání zpráv.

```cpp
virtual void unlink_target(_Inout_ ITarget<size_t>* _PTarget);
```

### <a name="parameters"></a>Parametry

*_PTarget*<br/>
Ukazatel na blok `ITarget`, který se má odpojit od `choice` bloku zpráv.

## <a name="unlink_targets"></a>unlink_targets

Odpojí všechny cíle od tohoto `choice`ho bloku pro zasílání zpráv.

```cpp
virtual void unlink_targets();
```

### <a name="remarks"></a>Poznámky

Tuto metodu není nutné volat z destruktoru, protože destruktor interního `single_assignment`ho bloku se odpojí správně.

## <a name="value"></a>osa

Získá zprávu, jejíž index byl vybrán v rámci `choice`ho bloku pro zasílání zpráv.

```cpp
template <
    typename _Payload_type
>
_Payload_type const& value();
```

### <a name="parameters"></a>Parametry

*_Payload_type*<br/>
Typ datové části zprávy

### <a name="return-value"></a>Návratová hodnota

Datová část zprávy.

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že blok zasílání zpráv `choice` může přebírat vstupy s různými typy datových částí, je nutné v bodě načtení zadat typ datové části. Můžete určit typ založený na výsledku `index` metody.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[join – třída](join-class.md)<br/>
[single_assignment – třída](single-assignment-class.md)
