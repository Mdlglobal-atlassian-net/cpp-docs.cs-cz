---
title: tiled_extent – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8370dbd381fa7005ea619ddb63b21bd227f68153
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="tiledextent-class"></a>tiled_extent – třída
A `tiled_extent` objekt `extent` objekt jednu až tři dimenzí, který rozděluje prostor rozsah do jeden, dva nebo trojrozměrné dlaždice.  
  
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
|[tiled_extent – konstruktor](#ctor)|Inicializuje novou instanci třídy `tiled_extent` třídy.|  

  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[get_tile_extent](#get_tile_extent)|Vrátí `extent` objekt, který zachycuje hodnoty `tiled_extent` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.|  
|[pad](#pad)|Vrátí novou `tiled_extent` objekt s rozsahy upraví, až se dělitelná dimenze dlaždice.|  
|[zkrácení](#truncate)|Vrátí novou `tiled_extent` objekt s rozsahy upraveno dolů, aby dělitelná dimenze dlaždice.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Zkopíruje obsah zadaného `tiled_index` objekt s touto.|  

  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[tile_dim0 Constant](#tile_dim0)|Ukládá délka nejvýznamnějších dimenze.|  
|[tile_dim1 Constant](#tile_dim1)|Ukládá délka další většinu významné dimenze.|  
|[tile_dim2 Constant](#tile_dim2)|Ukládá délku nejméně významný dimenze.|  

  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[tile_extent](#tile_extent)|Získá `extent` objekt, který zachycuje hodnoty `tiled_extent` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `extent`  
  
 `tiled_extent`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  

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
 `_Other`  
 `extent` Nebo `tiled_extent` objekt, který chcete kopírovat.  
  

  

## <a name="get_tile_extent"> </a>  get_tile_extent   
Vrátí `extent` objekt, který zachycuje hodnoty `tiled_extent` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `extent` Objekt, který zachycuje dimenze tohoto `tiled_extent` instance.  
  

## <a name="pad"> </a>  pad   
Vrátí novou `tiled_extent` objekt s rozsahy upraví, až se dělitelná dimenze dlaždice.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
tiled_extent pad() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové `tiled_extent` objektu podle hodnoty. 
## <a name="truncate"> </a>  zkrácení   
Vrátí novou `tiled_extent` objekt s rozsahy upraveno dolů, aby dělitelná dimenze dlaždice.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
tiled_extent truncate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí novou `tiled_extent` objekt s rozsahy upraveno dolů, aby dělitelná dimenze dlaždice.  

## <a name="operator_eq"> </a>  operátor =   
Zkopíruje obsah zadaného `tiled_index` objekt s touto.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
tiled_extent&  operator= (  
    const tiled_extent& _Other ) restrict (amp, cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `tiled_index` Objekt, který chcete zkopírovat z.  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na toto `tiled_index` instance.  

## <a name="tile_dim0"> </a>  tile_dim0   
Ukládá délka nejvýznamnějších dimenze.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim0 = _Dim0;  
```  
  
## <a name="tile_dim1"> </a>  tile_dim1   
Ukládá délka další většinu významné dimenze.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim1 = _Dim1;  
```  
## <a name="tile_dim2"> </a>  tile_dim2   
Ukládá délku nejméně významný dimenze.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static const int tile_dim2 = _Dim2;  
```  
## <a name="tile_extent"> </a>  tile_extent –   
  Získá `extent` objekt, který zachycuje hodnoty `tiled_extent` šablony argumenty `_Dim0`, `_Dim1`, a `_Dim2`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;  
```  
  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
