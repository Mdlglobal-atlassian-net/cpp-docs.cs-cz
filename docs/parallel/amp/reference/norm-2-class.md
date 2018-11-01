---
title: norm_2 – třída
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm_2::set_x
- amp_short_vectors/Concurrency::graphics::norm_2::set_xy
- amp_short_vectors/Concurrency::graphics::norm_2::g
- amp_short_vectors/Concurrency::graphics::norm_2::get_yx
- amp_short_vectors/Concurrency::graphics::norm_2::set_yx
- amp_short_vectors/Concurrency::graphics::norm_2::operator-=
- amp_short_vectors/Concurrency::graphics::norm_2::operator/=
- amp_short_vectors/Concurrency::graphics::norm_2::operator*=
- amp_short_vectors/Concurrency::graphics::norm_2::yx
- amp_short_vectors/Concurrency::graphics::norm_2::y
- amp_short_vectors/Concurrency::graphics::norm_2::xy
- amp_short_vectors/Concurrency::graphics::norm_2::operator++
- amp_short_vectors/Concurrency::graphics::norm_2::operator-
- amp_short_vectors/Concurrency::graphics::norm_2::rg
- amp_short_vectors/Concurrency::graphics::norm_2::operator=
- amp_short_vectors/Concurrency::graphics::norm_2::get_y
- amp_short_vectors/Concurrency::graphics::norm_2::r
- amp_short_vectors/Concurrency::graphics::norm_2::get_x
- amp_short_vectors/Concurrency::graphics::norm_2::get_xy
- amp_short_vectors/Concurrency::graphics::norm_2::gr
- amp_short_vectors/Concurrency::graphics::norm_2::set_y
- amp_short_vectors/Concurrency::graphics::norm_2::x
- amp_short_vectors/Concurrency::graphics::norm_2::operator+=
- amp_short_vectors/Concurrency::graphics::norm_2
- amp_short_vectors/Concurrency::graphics::norm_2::operator--
ms.assetid: 80703f9b-61f4-414a-93fd-bc774f7d3393
ms.openlocfilehash: ebf1a80a695f1d25652f239f66d8d40c0e1099ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542213"
---
# <a name="norm2-class"></a>norm_2 – třída

Představuje krátký vektor dvou normálních čísel.

## <a name="syntax"></a>Syntaxe

```
class norm_2;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[norm_2 – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor, inicializuje všechny prvky na 0.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|norm_2::get_x||
|norm_2::get_xy||
|norm_2::get_y||
|norm_2::get_yx||
|norm_2::ref_g||
|norm_2::ref_r||
|norm_2::ref_x||
|norm_2::ref_y||
|norm_2::set_x||
|norm_2::set_xy||
|norm_2::set_y||
|norm_2::set_yx||

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|norm_2::Operator-||
|norm_2::operator--||
|norm_2::Operator * =||
|norm_2::Operator / =||
|norm_2::Operator ++||
|norm_2::Operator +=||
|norm_2::Operator =||
|operátor norm_2::Operator-=||

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[velikost – konstanta](#norm_2__size)||

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|norm_2::g||
|norm_2::GR||
|norm_2::r||
|norm_2::rg||
|norm_2::x||
|norm_2::XY||
|norm_2::y||
|norm_2::yx||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`norm_2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors.h

**Namespace:** Concurrency::graphics

##  <a name="ctor"></a> norm_2 –

Výchozí konstruktor, inicializuje všechny prvky na 0.

```
norm_2() restrict(amp,
    cpu);

norm_2(
    norm _V0,
    norm _V1) restrict(amp,
    cpu);

norm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

norm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

norm_2(
    norm _V) restrict(amp,
    cpu);

explicit norm_2(
    float _V) restrict(amp,
    cpu);

norm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline norm_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V0*<br/>
Hodnota inicializace prvek 0.

*_V1*<br/>
Hodnota inicializace element 1.

*_V*<br/>
Hodnota inicializace.

*Ji_né*<br/>
Objekt použitý k inicializaci.

##  <a name="norm_2__size"></a> Velikost

```
static const int size = 2;
```

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
