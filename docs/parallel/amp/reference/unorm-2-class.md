---
title: unorm_2 – třída
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator+=
- amp_short_vectors/Concurrency::graphics::unnorm_2::y
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::x
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator--
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator*=
- amp_short_vectors/Concurrency::graphics::unnorm_2::xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_y
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator=
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::rg
- amp_short_vectors/Concurrency::graphics::unorm_2
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-=
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator/=
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_xy
- amp_short_vectors/Concurrency::graphics::unnorm_2::set_yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::yx
- amp_short_vectors/Concurrency::graphics::unnorm_2::gr
- amp_short_vectors/Concurrency::graphics::unnorm_2::r
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator-
- amp_short_vectors/Concurrency::graphics::unnorm_2::get_x
- amp_short_vectors/Concurrency::graphics::unnorm_2::g
- amp_short_vectors/Concurrency::graphics::unnorm_2::operator++
ms.assetid: 62e88ea7-e29f-4f62-95ce-61a1f39f5e34
ms.openlocfilehash: 33411511809fc9798f6fdf65f5331e2e587990ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405492"
---
# <a name="unorm2-class"></a>unorm_2 – třída

Představuje krátký vektor dvou normálních čísel bez znaménka.

## <a name="syntax"></a>Syntaxe

```
class unorm_2;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[unorm_2 – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor, inicializuje všechny prvky na 0.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|unorm_2::get_x||
|unorm_2::get_xy||
|unorm_2::get_y||
|unorm_2::get_yx||
|unorm_2::ref_g||
|unorm_2::ref_r||
|unorm_2::ref_x||
|unorm_2::ref_y||
|unorm_2::set_x||
|unorm_2::set_xy||
|unorm_2::set_y||
|unorm_2::set_yx||

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|unorm_2::Operator--||
|unorm_2::Operator * =||
|unorm_2::Operator / =||
|unorm_2::Operator ++||
|unorm_2::Operator +=||
|unorm_2::Operator =||
|operátor unorm_2::Operator-=||

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|unorm_2::size – konstanta||

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|unorm_2::g||
|unorm_2::GR||
|unorm_2::r||
|unorm_2::rg||
|unorm_2::x||
|unorm_2::XY||
|unorm_2::y||
|unorm_2::yx||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`unorm_2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors.h

**Namespace:** Concurrency::Graphics

##  <a name="ctor"></a> unorm_2 –

Výchozí konstruktor, inicializuje všechny prvky na 0.

```
unorm_2() restrict(amp,
    cpu);

unorm_2(
    unorm _V0,
    unorm _V1) restrict(amp,
    cpu);

unorm_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

unorm_2(
    unorm _V) restrict(amp,
    cpu);

explicit unorm_2(
    float _V) restrict(amp,
    cpu);

unorm_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline unorm_2(
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

##  <a name="unorm_2__size"></a> Velikost

```
static const int size = 2;
```

## <a name="see-also"></a>Viz také:

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
