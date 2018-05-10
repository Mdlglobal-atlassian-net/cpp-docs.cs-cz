---
title: tiled_index – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd28ab01d0d4180cc518cff230eb7df8261f4940
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="tiledindex-class"></a>tiled_index – třída
Poskytuje index do [tiled_extent](tiled-extent-class.md) objektu. Tato třída obsahuje vlastnosti, které chcete přístup k elementům relativně ke zdroji místní dlaždice a relativně ke zdroji globální. Další informace o vedle sebe prostorech najdete v tématu [pomocí dlaždice](../../../parallel/amp/using-tiles.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `_Dim0`  
 Délka nejvýznamnějších dimenze.  
  
 `_Dim1`  
 Délka další většinu významné dimenze.  
  
 `_Dim2`  
 Délka nejméně významný dimenze.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[tiled_index – konstruktor](#ctor)|Inicializuje novou instanci třídy `tile_index` třídy.|  

  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_tile_extent](#tiled_index__get_tile_extent)|Vrátí [rozsah](extent-class.md) objekt, který obsahuje hodnoty `tiled_index` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.|  


  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[Barrier konstanta](#tiled_index__barrier)|Úložiště [tile_barrier](tile-barrier-class.md) objekt, který reprezentuje bariéry v dlaždici aktuální vláken.|  
|||  
|[globální konstanta](#tiled_index__global)|Úložiště [index](index-class.md) objekt pořadí 1, 2 nebo 3, který představuje na globální indexu v [mřížky](http://msdn.microsoft.com/en-us/f7d1b6a6-586c-4345-b09a-bfc26c492cb0) objektu.|  
|[Local – konstanta](#tiled_index__local)|Úložiště `index` objekt pořadí 1, 2 nebo 3, která představuje relativní indexu v aktuální dlaždici [tiled_extent](tiled-extent-class.md) objektu.|  
|[pořadí konstanta](#tiled_index__rank)|Ukládá pořadí `tiled_index` objektu.|  
|[Tile – konstanta](#tiled_index__tile)|Úložiště `index` objekt pořadí 1, 2 nebo 3, který představuje souřadnice aktuální dlaždici `tiled_extent` objektu.|  
|[tile_dim0 konstanta](#tiled_index__tile_dim0)|Ukládá délka nejvýznamnějších dimenze.|  
|[tile_dim1 konstanta](#tiled_index__tile_dim1)|Ukládá délka další většinu významné dimenze.|  
|[tile_dim2 konstanta](#tiled_index__tile_dim2)|Ukládá délku nejméně významný dimenze.|  
|[tile_origin konstanta](#tiled_index__tile_origin)|Úložiště `index` objekt pořadí 1, 2 nebo 3, který představuje na globální souřadnice počátečního aktuální dlaždice v `tiled_extent` objektu.|  

  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|Získá [rozsah](extent-class.md) objekt, který obsahuje hodnoty `tiled_index` šablony argumenty `tiled_index` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.|  

  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_Tiled_index_base`  
  
 `tiled_index`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  


## <a name="tiled_index__ctor"></a>  tiled_index – konstruktor  
Inicializuje novou instanci třídy `tiled_index` třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
tiled_index(  
    const index<rank>& _Global,  
    const index<rank>& _Local,  
    const index<rank>& _Tile,  
    const index<rank>& _Tile_origin,  
    const tile_barrier& _Barrier ) restrict(amp,cpu);  
  
tiled_index(  
    const tiled_index& _Other ) restrict(amp,cpu);  
```  
  
#### <a name="parameters"></a>Parametry  
 `_Global`  
 Na globální [index](index-class.md) z konstruovaný objekt `tiled_index`.  
  
 `_Local`  
 Místní [index](index-class.md) z konstruovaný objekt `tiled_index`  
  
 `_Tile`  
 Na dlaždici [index](index-class.md) z konstruovaný objekt `tiled_index`  
  
 `_Tile_origin`  
 Na dlaždici počátek [index](index-class.md) z konstruovaný objekt `tiled_index`  
  
 `_Barrier`  
 [Tile_barrier](tile-barrier-class.md) objekt konstruovaný objekt `tiled_index`.  
  
 `_Other`  
 `tile_index` Objekt, který se má zkopírovat na konstruovaný objekt `tiled_index`.  
  
## <a name="overloads"></a>Přetížení  
  
|||  
|-|-|  
|Název|Popis|  
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializuje novou instanci třídy `tile_index` třídu z indexu na dlaždici v souřadnicích globální a relativní pozici v dlaždici v místní souřadnice. `_Global` a `_Tile_origin` se vypočítávají parametry.|  
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializuje novou instanci třídy `tile_index` zkopírováním zadané `tiled_index` objektu.|  


## <a name="tiled_index__get_tile_extent"></a>  get_tile_extent –
Vrátí [rozsah](extent-class.md) objekt, který obsahuje hodnoty `tiled_index` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
extent<rank> get_tile_extent()restrict(amp,cpu);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `extent` Objekt, který obsahuje hodnoty `tiled_index` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.  

## <a name="tiled_index__barrier"></a>  Barrier   
Úložiště [tile_barrier](tile-barrier-class.md) objekt, který reprezentuje bariéry v dlaždici aktuální vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
const tile_barrier barrier;  
```  

## <a name="tiled_index__global"></a>  Globální   
Úložiště [index](index-class.md) objekt pořadí 1, 2 nebo 3, která představuje globální index objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
const index<rank> global;  
```  
  
## <a name="tiled_index__local"></a>  místní   
Úložiště [index](index-class.md) objekt pořadí 1, 2 nebo 3, která představuje relativní indexu v aktuální dlaždici [tiled_extent](tiled-extent-class.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
const index<rank> local;  
```  
  
## <a name="tiled_index__rank"></a>  Pořadí   
Ukládá pořadí `tiled_index` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const int rank = _Rank;  
```  

## <a name="tiled_index__tile"></a>  Dlaždice   
Úložiště [index](index-class.md) objekt pořadí 1, 2 nebo 3, který představuje souřadnice aktuální dlaždici [tiled_extent](tiled-extent-class.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
const index<rank> tile;  
```  
  
## <a name="tiled_index__tile_dim0"></a>  tile_dim0  
Ukládá délka nejvýznamnějších dimenze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim0 = _Dim0;  
```  
   
## <a name="tiled_index__tile_dim1"></a>  tile_dim1   
Ukládá délka další většinu významné dimenze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tiled_index__tile_dim2"></a>  tile_dim2   
Ukládá délku nejméně významný dimenze.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tiled_index__tile_origin"></a>  tile_origin   
Úložiště [index](index-class.md) objekt pořadí 1, 2 nebo 3, který představuje na globální souřadnice počátečního aktuální dlaždice v rámci [tiled_extent](tiled-extent-class.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
const index<rank> tile_origin  
```  
## <a name="tile_extent"></a>  tile_extent –
  Získá [rozsah](extent-class.md) objekt, který obsahuje hodnoty `tiled_index` šablony argumenty `tiled_index` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;  
```  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
