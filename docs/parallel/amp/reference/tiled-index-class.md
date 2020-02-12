---
title: tiled_index – třída
ms.date: 03/27/2019
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: eda01667a6b239284c682ba6ae3f9b857c713447
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142427"
---
# <a name="tiled_index-class"></a>tiled_index – třída

Poskytuje index do objektu [tiled_extent](tiled-extent-class.md) . Tato třída má vlastnosti pro přístup k prvkům relativním k původnímu zdroji dlaždice a vzhledem k globálnímu původu. Další informace o dlaždicích mezer najdete v tématu [použití dlaždic](../../../parallel/amp/using-tiles.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    int _Dim0,
    int _Dim1 = 0,
    int _Dim2 = 0
>
class tiled_index : public _Tiled_index_base<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;

template <
    int _Dim0
>
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;
```

### <a name="parameters"></a>Parametry

*_Dim0*<br/>
Délka nejvýznamnějšího rozměru.

*_Dim1*<br/>
Délka nejbližšího významného rozměru.

*_Dim2*<br/>
Délka nejméně významného rozměru.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[tiled_index – konstruktor](#ctor)|Inicializuje novou instanci třídy `tile_index`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Vrátí objekt [rozsahu](extent-class.md) , který má hodnoty argumentů šablony `tiled_index` `_Dim0`, `_Dim1`a `_Dim2`.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[Konstanta bariéry](#tiled_index__barrier)|Ukládá objekt [tile_barrier](tile-barrier-class.md) , který představuje bariéru v aktuální dlaždici vláken.|
|||
|[globální konstanta](#tiled_index__global)|Ukládá objekt [indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje globální index v objektu Grid.|
|[lokální konstanta](#tiled_index__local)|Ukládá objekt `index` pořadí 1, 2 nebo 3, který představuje relativní index v aktuální dlaždici objektu [tiled_extent](tiled-extent-class.md) .|
|[Konstanta Rank](#tiled_index__rank)|Ukládá pořadí objektu `tiled_index`.|
|[Konstanta dlaždice](#tiled_index__tile)|Ukládá objekt `index` pořadí 1, 2 nebo 3, který představuje souřadnice aktuální dlaždice objektu `tiled_extent`.|
|[tile_dim0 konstanta](#tiled_index__tile_dim0)|Ukládá délku nejvýznamnějšího rozměru.|
|[tile_dim1 konstanta](#tiled_index__tile_dim1)|Ukládá délku další důležité dimenze.|
|[tile_dim2 konstanta](#tiled_index__tile_dim2)|Ukládá délku nejméně významného rozměru.|
|[tile_origin konstanta](#tiled_index__tile_origin)|Ukládá objekt `index` pořadí 1, 2 nebo 3, který představuje globální souřadnice počátku aktuální dlaždice v objektu `tiled_extent`.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Získá objekt [rozsahu](extent-class.md) , který má hodnoty argumentů šablony `tiled_index` `tiled_index` argumenty šablony `_Dim0`, `_Dim1`a `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="ctor"></a>tiled_index – konstruktor

Inicializuje novou instanci třídy `tiled_index`.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Global*<br/>
Globální [index](index-class.md) vytvořeného `tiled_index`.

*_Local*<br/>
Místní [index](index-class.md) vytvořeného `tiled_index`

*_Tile*<br/>
[Index](index-class.md) dlaždice vytvořeného `tiled_index`

*_Tile_origin*<br/>
[Index](index-class.md) počátku dlaždice vytvořeného `tiled_index`

*_Barrier*<br/>
Objekt [tile_barrier](tile-barrier-class.md) vytvořeného `tiled_index`.

*_Other*<br/>
Objekt `tile_index`, který má být zkopírován do vytvořeného `tiled_index`.

### <a name="overloads"></a>Přetížení

|||
|-|-|
|Název|Popis|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializuje novou instanci třídy `tile_index` z indexu dlaždice v globálních souřadnicích a relativní pozice dlaždice v místních souřadnicích. Parametry `_Global` a `_Tile_origin` jsou vypočítány.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializuje novou instanci třídy `tile_index` zkopírováním zadaného objektu `tiled_index`.|

## <a name="tiled_index__get_tile_extent"></a>get_tile_extent

Vrátí objekt [rozsahu](extent-class.md) , který má hodnoty argumentů šablony `tiled_index` `_Dim0`, `_Dim1`a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Objekt `extent`, který obsahuje hodnoty argumentů šablony `tiled_index` `_Dim0`, `_Dim1`a `_Dim2`.

## <a name="tiled_index__barrier"></a>bariéra

Ukládá objekt [tile_barrier](tile-barrier-class.md) , který představuje bariéru v aktuální dlaždici vláken.

### <a name="syntax"></a>Syntaxe

```cpp
const tile_barrier barrier;
```

## <a name="tiled_index__global"></a>globální

Ukládá objekt [indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje globální index objektu.

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> global;
```

## <a name="tiled_index__local"></a>místní

Ukládá objekt [indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje relativní index v aktuální dlaždici objektu [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> local;
```

## <a name="tiled_index__rank"></a>pořadí

Ukládá pořadí objektu `tiled_index`.

### <a name="syntax"></a>Syntaxe

```cpp
static const int rank = _Rank;
```

## <a name="tiled_index__tile"></a>podobě

Ukládá objekt [indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje souřadnice aktuální dlaždice objektu [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile;
```

## <a name="tiled_index__tile_dim0"></a>tile_dim0

Ukládá délku nejvýznamnějšího rozměru.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tiled_index__tile_dim1"></a>tile_dim1

Ukládá délku další důležité dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tiled_index__tile_dim2"></a>tile_dim2

Ukládá délku nejméně významného rozměru.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tiled_index__tile_origin"></a>tile_origin

Ukládá objekt [indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje globální souřadnice počátku aktuální dlaždice v rámci objektu [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a>tile_extent

Získá objekt [rozsahu](extent-class.md) , který má hodnoty argumentů šablony `tiled_index` `tiled_index` argumenty šablony `_Dim0`, `_Dim1`a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
