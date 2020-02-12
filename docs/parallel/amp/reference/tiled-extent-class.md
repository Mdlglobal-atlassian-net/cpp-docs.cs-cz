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
ms.openlocfilehash: e2248c770c7eedde59d1cb592f7d5d7c1bfbde9a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126419"
---
# <a name="tiled_extent-class"></a>tiled_extent – třída

Objekt `tiled_extent` je objekt `extent` jednoho až tří rozměrů, který rozděluje rozsah prostoru na jednu, dvě nebo tři dvojrozměrné dlaždice.

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
Délka nejvýznamnějšího rozměru.

*_Dim1*<br/>
Délka nejbližšího významného rozměru.

*_Dim2*<br/>
Délka nejméně významného rozměru.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[tiled_extent – konstruktor](#ctor)|Inicializuje novou instanci třídy `tiled_extent`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Vrátí objekt `extent`, který zachycuje hodnoty argumentů šablony `tiled_extent` `_Dim0`, `_Dim1`a `_Dim2`.|
|[čísel](#pad)|Vrátí nový objekt `tiled_extent` s rozsahy upravenými tak, aby byly rovnoměrně oddělitelné Rozměry dlaždice.|
|[zkrátit](#truncate)|Vrátí nový objekt `tiled_extent` s rozsahy, které jsou upraveny tak, aby byly rovnoměrně oddělitelné Rozměry dlaždice.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operátor =](#operator_eq)|Zkopíruje obsah zadaného objektu `tiled_index` do tohoto objektu.|

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[tile_dim0 konstanta](#tile_dim0)|Ukládá délku nejvýznamnějšího rozměru.|
|[tile_dim1 konstanta](#tile_dim1)|Ukládá délku další důležité dimenze.|
|[tile_dim2 konstanta](#tile_dim2)|Ukládá délku nejméně významného rozměru.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[tile_extent](#tile_extent)|Získá objekt `extent`, který zachycuje hodnoty argumentů šablony `tiled_extent` `_Dim0`, `_Dim1`a `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`extent`

`tiled_extent`

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="ctor"></a> Tiled_extent – konstruktor

Inicializuje novou instanci třídy `tiled_extent`.

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
Objekt `extent` nebo `tiled_extent` ke zkopírování.

## <a name="get_tile_extent"></a> get_tile_extent

Vrátí objekt `extent`, který zachycuje hodnoty argumentů šablony `tiled_extent` `_Dim0`, `_Dim1`a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Návratová hodnota

Objekt `extent`, který zachycuje Rozměry této `tiled_extent` instance.

## <a name="pad"></a> panel

Vrátí nový objekt `tiled_extent` s rozsahy upravenými tak, aby byly rovnoměrně oddělitelné Rozměry dlaždice.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Návratová hodnota

Nový objekt `tiled_extent` podle hodnoty.
## <a name="truncate"></a> zkrátit

Vrátí nový objekt `tiled_extent` s rozsahy, které jsou upraveny tak, aby byly rovnoměrně oddělitelné Rozměry dlaždice.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí nový objekt `tiled_extent` s rozsahy, které jsou upraveny tak, aby byly rovnoměrně oddělitelné Rozměry dlaždice.

## <a name="operator_eq"></a> operátor =

Zkopíruje obsah zadaného objektu `tiled_index` do tohoto objektu.

### <a name="syntax"></a>Syntaxe

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `tiled_index`, ze kterého se má kopírovat.

### <a name="return-value"></a>Návratová hodnota

Odkaz na tuto instanci `tiled_index`.

## <a name="tile_dim0"></a> tile_dim0

Ukládá délku nejvýznamnějšího rozměru.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a> tile_dim1

Ukládá délku další důležité dimenze.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a> tile_dim2

Ukládá délku nejméně významného rozměru.

### <a name="syntax"></a>Syntaxe

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a> tile_extent
  Získá objekt `extent`, který zachycuje hodnoty argumentů šablony `tiled_extent` `_Dim0`, `_Dim1`a `_Dim2`.

### <a name="syntax"></a>Syntaxe

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
