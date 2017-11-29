---
title: "float_3 – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_3::get_zyx
- amp_short_vectors/Concurrency::graphics::float_3::set_y
- amp_short_vectors/Concurrency::graphics::float_3::b
- amp_short_vectors/Concurrency::graphics::float_3::operator-=
- amp_short_vectors/Concurrency::graphics::float_3::get_y
- amp_short_vectors/Concurrency::graphics::float_3::set_zy
- amp_short_vectors/Concurrency::graphics::float_3::get_yzx
- amp_short_vectors/Concurrency::graphics::float_3::xz
- amp_short_vectors/Concurrency::graphics::float_3::xyz
- amp_short_vectors/Concurrency::graphics::float_3::operator+=
- amp_short_vectors/Concurrency::graphics::float_3::brg
- amp_short_vectors/Concurrency::graphics::float_3::get_x
- amp_short_vectors/Concurrency::graphics::float_3::get_zx
- amp_short_vectors/Concurrency::graphics::float_3::y
- amp_short_vectors/Concurrency::graphics::float_3::rbg
- amp_short_vectors/Concurrency::graphics::float_3::operator-
- amp_short_vectors/Concurrency::graphics::float_3::get_yz
- amp_short_vectors/Concurrency::graphics::float_3::set_xz
- amp_short_vectors/Concurrency::graphics::float_3::operator/=
- amp_short_vectors/Concurrency::graphics::float_3::zxy
- amp_short_vectors/Concurrency::graphics::float_3::yx
- amp_short_vectors/Concurrency::graphics::float_3::g
- amp_short_vectors/Concurrency::graphics::float_3::r
- amp_short_vectors/Concurrency::graphics::float_3::zy
- amp_short_vectors/Concurrency::graphics::float_3::set_zxy
- amp_short_vectors/Concurrency::graphics::float_3::set_zyx
- amp_short_vectors/Concurrency::graphics::float_3::get_yx
- amp_short_vectors/Concurrency::graphics::float_3
- amp_short_vectors/Concurrency::graphics::float_3::get_xz
- amp_short_vectors/Concurrency::graphics::float_3::get_yxz
- amp_short_vectors/Concurrency::graphics::float_3::set_xy
- amp_short_vectors/Concurrency::graphics::float_3::get_xzy
- amp_short_vectors/Concurrency::graphics::float_3::bgr
- amp_short_vectors/Concurrency::graphics::float_3::zx
- amp_short_vectors/Concurrency::graphics::float_3::gr
- amp_short_vectors/Concurrency::graphics::float_3::set_z
- amp_short_vectors/Concurrency::graphics::float_3::get_zy
- amp_short_vectors/Concurrency::graphics::float_3::gb
- amp_short_vectors/Concurrency::graphics::float_3::set_xzy
- amp_short_vectors/Concurrency::graphics::float_3::set_zx
- amp_short_vectors/Concurrency::graphics::float_3::set_yzx
- amp_short_vectors/Concurrency::graphics::float_3::operator=
- amp_short_vectors/Concurrency::graphics::float_3::x
- amp_short_vectors/Concurrency::graphics::float_3::grb
- amp_short_vectors/Concurrency::graphics::float_3::zyx
- amp_short_vectors/Concurrency::graphics::float_3::set_yxz
- amp_short_vectors/Concurrency::graphics::float_3::get_zxy
- amp_short_vectors/Concurrency::graphics::float_3::set_yz
- amp_short_vectors/Concurrency::graphics::float_3::operator--
- amp_short_vectors/Concurrency::graphics::float_3::set_xyz
- amp_short_vectors/Concurrency::graphics::float_3::operator++
- amp_short_vectors/Concurrency::graphics::float_3::z
- amp_short_vectors/Concurrency::graphics::float_3::xy
- amp_short_vectors/Concurrency::graphics::float_3::rgb
- amp_short_vectors/Concurrency::graphics::float_3::rg
- amp_short_vectors/Concurrency::graphics::float_3::yzx
- amp_short_vectors/Concurrency::graphics::float_3::set_yx
- amp_short_vectors/Concurrency::graphics::float_3::xzy
- amp_short_vectors/Concurrency::graphics::float_3::rb
- amp_short_vectors/Concurrency::graphics::float_3::get_z
- amp_short_vectors/Concurrency::graphics::float_3::br
- amp_short_vectors/Concurrency::graphics::float_3::bg
- amp_short_vectors/Concurrency::graphics::float_3::get_xyz
- amp_short_vectors/Concurrency::graphics::float_3::set_x
- amp_short_vectors/Concurrency::graphics::float_3::yxz
- amp_short_vectors/Concurrency::graphics::float_3::yz
- amp_short_vectors/Concurrency::graphics::float_3::gbr
- amp_short_vectors/Concurrency::graphics::float_3::operator*=
- amp_short_vectors/Concurrency::graphics::float_3::get_xy
dev_langs: C++
helpviewer_keywords: amp_short_vectors/Concurrency::graphics::float_3
ms.assetid: 209df7a5-08d7-48b4-8ba5-77603642cdd8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 713f3545ea2604db1313abab729ec726cce3cd75
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="float3-class"></a>float_3 – třída
Představuje krátký vektor tři obtékaných objektů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class float_3;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|`value_type`||  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[float_3 – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor, inicializuje všechny prvky s 0.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|float_3::get_x||  
|float_3::get_xy||  
|float_3::get_xyz||  
|float_3::get_xz||  
|float_3::get_xzy||  
|float_3::get_y||  
|float_3::get_yx||  
|float_3::get_yxz||  
|float_3::get_yz||  
|float_3::get_yzx||  
|float_3::get_z||  
|float_3::get_zx||  
|float_3::get_zxy||  
|float_3::get_zy||  
|float_3::get_zyx||  
|float_3::ref_b||  
|float_3::ref_g||  
|float_3::ref_r||  
|float_3::ref_x||  
|float_3::ref_y||  
|float_3::ref_z||  
|float_3::set_x||  
|float_3::set_xy||  
|float_3::set_xyz||  
|float_3::set_xz||  
|float_3::set_xzy||  
|float_3::set_y||  
|float_3::set_yx||  
|float_3::set_yxz||  
|float_3::set_yz||  
|float_3::set_yzx||  
|float_3::set_z||  
|float_3::set_zx||  
|float_3::set_zxy||  
|float_3::set_zy||  
|float_3::set_zyx||  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|float_3::Operator-||  
|float_3::Operator--||  
|float_3::Operator * =||  
|/ float_3::Operator = – operátor||  
|float_3::Operator ++||  
|float_3::Operator +=||  
|float_3::Operator =||  
|float_3::Operator-=||  
  
### <a name="public-constants"></a>Veřejné konstanty  
  
|Název|Popis|  
|----------|-----------------|  
|[Size – konstanta](#float_3__size)||  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|float_3::b||  
|float_3::BG||  
|float_3::BGR||  
|float_3::br||  
|float_3::brg||  
|float_3::g||  
|float_3::GB||  
|float_3::GBR||  
|float_3::GR||  
|float_3::grb||  
|float_3::r||  
|float_3::RB||  
|float_3::rbg||  
|float_3::rg||  
|float_3::RGB||  
|float_3::x||  
|float_3::XY||  
|float_3::xyz||  
|float_3::xz||  
|float_3::xzy||  
|float_3::y||  
|float_3::yx||  
|float_3::yxz||  
|float_3::YZ||  
|float_3::yzx||  
|float_3::z||  
|float_3::ZX||  
|float_3::zxy||  
|float_3::Zy||  
|float_3::Zyx||  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `float_3`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a>float_3 

 Výchozí konstruktor, inicializuje všechny prvky s 0.  
  
```  
float_3() restrict(amp,
    cpu);

 
float_3(
    float _V0,  
    float _V1,  
    float _V2) restrict(amp,
    cpu);

 
float_3(
    float _V) restrict(amp,
    cpu);

 
float_3(
    const float_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const uint_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const int_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const unorm_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const norm_3& _Other) restrict(amp,
    cpu);

 
explicit inline float_3(
    const double_3& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parametry  
 `_V0`  
 Hodnota k chybě při inicializaci element 0.  
  
 `_V1`  
 Hodnota k chybě při inicializaci prvek 1.  
  
 `_V2`  
 Hodnota k chybě při inicializaci element 2.  
  
 `_V`  
 Hodnota pro inicializaci.  
  
 `_Other`  
 Objekt použitý k chybě při inicializaci.  
  
##  <a name="float_3__size"></a>velikost 

```  
static const int size = 3;  
```  
  
## <a name="see-also"></a>Viz také  
 [Concurrency::Graphics Namespace](concurrency-graphics-namespace.md)