---
title: tiled_extent – třída
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: ce2710da1a745efedcd6e9e524355eda41e26de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374715"
---
# <a name="tiled_extent-class"></a>tiled_extent – třída

Objekt `tiled_extent` je `extent` objekt jedné až tří dimenzí, který rozděluje prostor rozsahu na jednorozměrné, dvourozměrné nebo trojrozměrné dlaždice.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
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
|[Konstruktor tiled_extent](#ctor)|Inicializuje novou instanci třídy. `tiled_extent`|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Vrátí `extent` objekt, který zachycuje hodnoty `tiled_extent` argumentů `_Dim0` `_Dim1`šablony `_Dim2`, a .|
|[Pad](#pad)|Vrátí nový `tiled_extent` objekt s rozsahy upravenými tak, aby byly rovnoměrně dělitelné rozměry dlaždic.|
|[Zkrátit](#truncate)|Vrátí nový `tiled_extent` objekt s rozsahy upravenými dolů tak, aby byl rovnoměrně dělitelný rozměry dlaždice.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `tiled_index` objektu do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Name (Název)|Popis|
|----------|-----------------|
|[tile_dim0 konstanta](#tile_dim0)|Ukládá délku nejvýznamnější dimenze.|
|[tile_dim1 konstanta](#tile_dim1)|Ukládá délku další nejvýznamnější dimenze.|
|[tile_dim2 konstanta](#tile_dim2)|Ukládá délku nejméně významné dimenze.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Získá `extent` objekt, který zachycuje hodnoty `tiled_extent` argumentů `_Dim0` `_Dim1`šablony `_Dim2`, a .|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`extent`

`tiled_extent`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Obor názvů:** Souběžnost

## <a name="tiled_extent-constructor"></a><a name="ctor"> </a> Konstruktor tiled_extent

Inicializuje novou instanci třídy. `tiled_extent`

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Nebo `extent` `tiled_extent` objekt, který chcete zkopírovat.

## <a name="get_tile_extent"></a><a name="get_tile_extent"> </a> get_tile_extent

Vrátí `extent` objekt, který zachycuje hodnoty `tiled_extent` argumentů `_Dim0` `_Dim1`šablony `_Dim2`, a .

### <a name="syntax"></a>Syntaxe

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `extent` který zachycuje dimenze této `tiled_extent` instance.

## <a name="pad"></a><a name="pad"> </a> podložka

Vrátí nový `tiled_extent` objekt s rozsahy upravenými tak, aby byly rovnoměrně dělitelné rozměry dlaždic.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Návratová hodnota

Nový `tiled_extent` objekt podle hodnoty.

## <a name="truncate"></a><a name="truncate"> </a> zkrácení

Vrátí nový `tiled_extent` objekt s rozsahy upravenými dolů tak, aby byl rovnoměrně dělitelný rozměry dlaždice.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nový `tiled_extent` objekt s rozsahy upravenými dolů tak, aby byl rovnoměrně dělitelný rozměry dlaždice.

## <a name="operator"></a><a name="operator_eq"> </a> operátor =

Zkopíruje obsah zadaného `tiled_index` objektu do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt, `tiled_index` ze který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na `tiled_index` tuto instanci.

## <a name="tile_dim0"></a><a name="tile_dim0"> </a> tile_dim0

Ukládá délku nejvýznamnější dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"> </a> tile_dim1

Ukládá délku další nejvýznamnější dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"> </a> tile_dim2

Ukládá délku nejméně významné dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"> </a> tile_extent

Získá `extent` objekt, který zachycuje hodnoty `tiled_extent` argumentů `_Dim0` `_Dim1`šablony `_Dim2`, a .

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
