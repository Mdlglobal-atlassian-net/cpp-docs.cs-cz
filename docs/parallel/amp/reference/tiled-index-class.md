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
ms.openlocfilehash: 46a6b3548526f0917c4e022a12bf859242e70b20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375473"
---
# <a name="tiled_index-class"></a>tiled_index – třída

Poskytuje index do [tiled_extent](tiled-extent-class.md) objektu. Tato třída má vlastnosti pro přístup k prvkům vzhledem k místní dlaždice původu a vzhledem ke globálnímu původu. Další informace o dlaždicových prostorech naleznete [v tématu Using Tiles](../../../parallel/amp/using-tiles.md).

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
Délka nejvýznamnější dimenze.

*_Dim1*<br/>
Délka následující ho nejdůležitějšího rozměru.

*_Dim2*<br/>
Délka nejméně významné dimenze.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Konstruktor tiled_index](#ctor)|Inicializuje novou instanci třídy. `tile_index`|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Vrátí objekt [rozsahu,](extent-class.md) který obsahuje `tiled_index` hodnoty `_Dim0`argumentů šablony , `_Dim1`a `_Dim2`.|

### <a name="public-constants"></a>Veřejné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[bariéra Konstanta](#tiled_index__barrier)|Ukládá [tile_barrier](tile-barrier-class.md) objekt, který představuje bariéru v aktuální dlaždici podprocesů.|
|||
|[globální konstanta](#tiled_index__global)|Ukládá objekt [indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje globální index v objektu mřížky.|
|[místní konstanta](#tiled_index__local)|Ukládá `index` objekt pořadí 1, 2 nebo 3, který představuje relativní index v aktuální dlaždici [tiled_extent](tiled-extent-class.md) objektu.|
|[pořadí konstanta](#tiled_index__rank)|Ukládá pořadí objektu. `tiled_index`|
|[konstanta dlaždice](#tiled_index__tile)|Ukládá `index` objekt hodnosti 1, 2 nebo 3, který představuje souřadnice aktuální dlaždice objektu. `tiled_extent`|
|[tile_dim0 konstanta](#tiled_index__tile_dim0)|Ukládá délku nejvýznamnější dimenze.|
|[tile_dim1 konstanta](#tiled_index__tile_dim1)|Ukládá délku další nejvýznamnější dimenze.|
|[tile_dim2 konstanta](#tiled_index__tile_dim2)|Ukládá délku nejméně významné dimenze.|
|[tile_origin konstanta](#tiled_index__tile_origin)|Ukládá `index` objekt pořadí 1, 2 nebo 3, který představuje globální souřadnice `tiled_extent` původu aktuální dlaždice v objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Získá objekt [rozsahu,](extent-class.md) který má `tiled_index` hodnoty `tiled_index` argumentů `_Dim0`šablony `_Dim1`argumentů šablony šablony , a `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Obor názvů:** Souběžnost

## <a name="tiled_index-constructor"></a><a name="ctor"></a>Konstruktor tiled_index

Inicializuje novou instanci třídy. `tiled_index`

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
Globální [index](index-class.md) vyrobeno `tiled_index`.

*_Local*<br/>
Místní [index](index-class.md) konstruovaných`tiled_index`

*_Tile*<br/>
[Index](index-class.md) dlaždic konstruované`tiled_index`

*_Tile_origin*<br/>
[Index](index-class.md) původu dlaždice konstruované`tiled_index`

*_Barrier*<br/>
[Tile_barrier](tile-barrier-class.md) objekt vyrobeno `tiled_index`.

*_Other*<br/>
Objekt, `tile_index` který má být zkopírován do vyrobeno `tiled_index`.

### <a name="overloads"></a>Přetížení

|||
|-|-|
|Name (Název)|Popis|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializuje novou instanci `tile_index` třídy z indexu dlaždice v globálních souřadnicích a relativní pozici v dlaždici v místních souřadnicích. A `_Global` `_Tile_origin` parametry jsou vypočítány.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializuje novou instanci `tile_index` třídy zkopírováním zadaného `tiled_index` objektu.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent

Vrátí objekt [rozsahu,](extent-class.md) který obsahuje `tiled_index` hodnoty `_Dim0`argumentů šablony , `_Dim1`a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `extent` který má hodnoty `tiled_index` argumentů `_Dim0` `_Dim1`šablony `_Dim2`, a .

## <a name="barrier"></a><a name="tiled_index__barrier"></a>Bariéra

Ukládá [tile_barrier](tile-barrier-class.md) objekt, který představuje bariéru v aktuální dlaždici podprocesů.

### <a name="syntax"></a>Syntaxe

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a>Globální

Ukládá [objekt indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje globální index objektu.

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a>Místní

Ukládá objekt [indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje relativní index v aktuální dlaždici [tiled_extent](tiled-extent-class.md) objektu.

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a>Hodnost

Ukládá pořadí objektu. `tiled_index`

### <a name="syntax"></a>Syntaxe

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a>Dlaždice

Ukládá [objekt indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje souřadnice aktuální dlaždice [tiled_extent](tiled-extent-class.md) objektu.

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0

Ukládá délku nejvýznamnější dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1

Ukládá délku další nejvýznamnější dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2

Ukládá délku nejméně významné dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a>tile_origin

Ukládá [objekt indexu](index-class.md) pořadí 1, 2 nebo 3, který představuje globální souřadnice původu aktuální dlaždice v [rámci tiled_extent](tiled-extent-class.md) objektu.

### <a name="syntax"></a>Syntaxe

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a>tile_extent

Získá objekt [rozsahu,](extent-class.md) který má `tiled_index` hodnoty `tiled_index` argumentů `_Dim0`šablony `_Dim1`argumentů šablony šablony , a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
