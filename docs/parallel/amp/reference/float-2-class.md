---
title: float_2 – třída
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_2::yx
- amp_short_vectors/Concurrency::graphics::float_2::operator-=
- amp_short_vectors/Concurrency::graphics::float_2::operator++
- amp_short_vectors/Concurrency::graphics::float_2::operator-
- amp_short_vectors/Concurrency::graphics::float_2::r
- amp_short_vectors/Concurrency::graphics::float_2::get_yx
- amp_short_vectors/Concurrency::graphics::float_2::get_xy
- amp_short_vectors/Concurrency::graphics::float_2::operator/=
- amp_short_vectors/Concurrency::graphics::float_2::set_yx
- amp_short_vectors/Concurrency::graphics::float_2::x
- amp_short_vectors/Concurrency::graphics::float_2::get_y
- amp_short_vectors/Concurrency::graphics::float_2::operator+=
- amp_short_vectors/Concurrency::graphics::float_2::gr
- amp_short_vectors/Concurrency::graphics::float_2::operator=
- amp_short_vectors/Concurrency::graphics::float_2::set_x
- amp_short_vectors/Concurrency::graphics::float_2::operator--
- amp_short_vectors/Concurrency::graphics::float_2::get_x
- amp_short_vectors/Concurrency::graphics::float_2::operator*=
- amp_short_vectors/Concurrency::graphics::float_2::rg
- amp_short_vectors/Concurrency::graphics::float_2::set_xy
- amp_short_vectors/Concurrency::graphics::float_2::xy
- amp_short_vectors/Concurrency::graphics::float_2
- amp_short_vectors/Concurrency::graphics::float_2::set_y
- amp_short_vectors/Concurrency::graphics::float_2::y
- amp_short_vectors/Concurrency::graphics::float_2::g
ms.assetid: b3ebd48e-f8c8-4f00-a640-357f702f0cae
ms.openlocfilehash: af5116118c9821f5c1801789bff13f3de8d4026a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126653"
---
# <a name="float_2-class"></a>float_2 – třída

Představuje krátký vektor dvou floatů.

## <a name="syntax"></a>Syntaxe

```cpp
class float_2;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[float_2 – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor inicializuje všechny prvky s 0.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|float_2:: get_x||
|float_2::get_xy||
|float_2:: get_y||
|float_2::get_yx||
|float_2::ref_g||
|float_2::ref_r||
|float_2::ref_x||
|float_2:: ref_y||
|float_2::set_x||
|float_2::set_xy||
|float_2:: set_y||
|float_2::set_yx||

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|float_2:: operator-||
|float_2:: operator--||
|float_2:: operator * =||
|float_2:: operator/=||
|float_2:: operator + +||
|float_2:: operator + =||
|float_2:: operator =||
|float_2:: operator-=||

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[velikost – konstanta](#float_2__size)||

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|float_2:: g||
|float_2:: gr||
|float_2:: r||
|float_2:: RG||
|float_2:: x||
|float_2:: XY||
|float_2:: y||
|float_2::yx||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`float_2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors. h

**Obor názvů:** Concurrency:: Graphics

## <a name="ctor"></a>float_2

Výchozí konstruktor inicializuje všechny prvky s 0.

```cpp
float_2() restrict(amp,
    cpu);

float_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

float_2(
    float _V) restrict(amp,
    cpu);

float_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V0*<br/>
Hodnota pro inicializaci elementu 0.

*_V1*<br/>
Hodnota pro inicializaci elementu 1.

*_V*<br/>
Hodnota pro inicializaci.

*_Other*<br/>
Objekt použitý k inicializaci.

## <a name="float_2__size"></a>hodnota

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
