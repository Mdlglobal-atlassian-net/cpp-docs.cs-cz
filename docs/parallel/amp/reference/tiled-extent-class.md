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
ms.openlocfilehash: 51e7696b8103e81d42beec0987a49f26fe041643
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264319"
---
# <a name="tiledextent-class"></a>tiled_extent – třída

A `tiled_extent` je objekt `extent` objekt dimenze jedné do tří, který rozděluje rozsah prostoru do jedno, dvou nebo třírozměrných dlaždic.

### <a name="syntax"></a>Syntaxe

```
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
Délka nejvýznamnějšího rozměru.

*_Dim1*<br/>
Délka druhého nejvýznamnějšího rozměru další úplně.

*_Dim2*<br/>
Velikost nejméně významného rozměru.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[tiled_extent Constructor](#ctor)|Inicializuje novou instanci třídy `tiled_extent` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Vrátí `extent` , který zachycuje hodnoty `tiled_extent` argumenty šablony `_Dim0`, `_Dim1`, a `_Dim2`.|
|[pad](#pad)|Vrátí nový `tiled_extent` objektu s rozsahy upraví, až se rovnoměrně dělitelné podle dimenzí dlaždice.|
|[zkrátit](#truncate)|Vrátí nový `tiled_extent` objektu s rozsahy sníženými tak byly rovnoměrně dělitelné podle dimenzí dlaždice.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného `tiled_index` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[tile_dim0 Constant](#tile_dim0)|Ukládá velikost nejvýznamnějšího rozměru.|
|[tile_dim1 Constant](#tile_dim1)|Ukládá délku druhé nejvýznamnější dimenze další úplně.|
|[tile_dim2 Constant](#tile_dim2)|Ukládá velikost nejméně významného rozměru.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Získá `extent` , který zachycuje hodnoty `tiled_extent` argumenty šablony `_Dim0`, `_Dim1`, a `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`extent`

`tiled_extent`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Namespace:** Souběžnost

## <a name="ctor"> </a>  tiled_extent – konstruktor

Inicializuje novou instanci třídy `tiled_extent` třídy.

### <a name="syntax"></a>Syntaxe

```
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`extent` Nebo `tiled_extent` objektu, který chcete zkopírovat.

## <a name="get_tile_extent"> </a>  get_tile_extent

Vrátí `extent` , který zachycuje hodnoty `tiled_extent` argumenty šablony `_Dim0`, `_Dim1`, a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

`extent` , Který zachycuje rozměry této `tiled_extent` instance.

## <a name="pad"> </a>  pad

Vrátí nový `tiled_extent` objektu s rozsahy upraví, až se rovnoměrně dělitelné podle dimenzí dlaždice.

### <a name="syntax"></a>Syntaxe

```
tiled_extent pad() const;
```

### <a name="return-value"></a>Návratová hodnota

Nové `tiled_extent` objektu podle hodnoty.
## <a name="truncate"> </a>  zkrátit

Vrátí nový `tiled_extent` objektu s rozsahy sníženými tak byly rovnoměrně dělitelné podle dimenzí dlaždice.

### <a name="syntax"></a>Syntaxe

```
tiled_extent truncate() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nový `tiled_extent` objektu s rozsahy sníženými tak byly rovnoměrně dělitelné podle dimenzí dlaždice.

## <a name="operator_eq"> </a>  operátor =

Zkopíruje obsah zadaného `tiled_index` do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`tiled_index` Objektu, který chcete kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tento `tiled_index` instance.

## <a name="tile_dim0"> </a>  tile_dim0

Ukládá velikost nejvýznamnějšího rozměru.

### <a name="syntax"></a>Syntaxe

```
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"> </a>  tile_dim1

Ukládá délku druhé nejvýznamnější dimenze další úplně.

### <a name="syntax"></a>Syntaxe

```
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"> </a>  tile_dim2

Ukládá velikost nejméně významného rozměru.

### <a name="syntax"></a>Syntaxe

```
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"> </a>  tile_extent –
  Získá `extent` , který zachycuje hodnoty `tiled_extent` argumenty šablony `_Dim0`, `_Dim1`, a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
