---
title: int_2 – třída
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_2::y
- amp_short_vectors/Concurrency::graphics::int_2::set_x
- amp_short_vectors/Concurrency::graphics::int_2::set_y
- amp_short_vectors/Concurrency::graphics::int_2::get_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator++
- amp_short_vectors/Concurrency::graphics::int_2::x
- amp_short_vectors/Concurrency::graphics::int_2::set_yx
- amp_short_vectors/Concurrency::graphics::int_2::operator/=
- amp_short_vectors/Concurrency::graphics::int_2::get_y
- amp_short_vectors/Concurrency::graphics::int_2::gr
- amp_short_vectors/Concurrency::graphics::int_2::operator*=
- amp_short_vectors/Concurrency::graphics::int_2::r
- amp_short_vectors/Concurrency::graphics::int_2::get_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator=
- amp_short_vectors/Concurrency::graphics::int_2::g
- amp_short_vectors/Concurrency::graphics::int_2::rg
- amp_short_vectors/Concurrency::graphics::int_2::xy
- amp_short_vectors/Concurrency::graphics::int_2::operator-=
- amp_short_vectors/Concurrency::graphics::int_2::get_x
- amp_short_vectors/Concurrency::graphics::int_2::yx
- amp_short_vectors/Concurrency::graphics::int_2
- amp_short_vectors/Concurrency::graphics::int_2::operator-
- amp_short_vectors/Concurrency::graphics::int_2::set_xy
- amp_short_vectors/Concurrency::graphics::int_2::operator+=
- amp_short_vectors/Concurrency::graphics::int_2::operator--
ms.assetid: 258b02e9-f1ee-46c2-8edd-dc9f69184846
ms.openlocfilehash: 000bda3a6ecc5b1ebf9be4e07ce8d703b6cd9194
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126640"
---
# <a name="int_2-class"></a>int_2 – třída

Představuje krátký vektor dvou celých čísel.

## <a name="syntax"></a>Syntaxe

```cpp
class int_2;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[int_2 – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor inicializuje všechny prvky s 0.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|int_2::get_x||
|int_2::get_xy||
|int_2:: get_y||
|int_2::get_yx||
|int_2::ref_g||
|int_2::ref_r||
|int_2::ref_x||
|int_2:: ref_y||
|int_2::set_x||
|int_2::set_xy||
|int_2::set_y||
|int_2::set_yx||

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|int_2:: operator-||
|int_2::operator--||
|int_2::operator%=||
|int_2::operator&=||
|int_2::operator*=||
|int_2:: operator/=||
|int_2::operator^=||
|int_2::operator&#124;=||
|int_2::operator~||
|int_2:: operator + +||
|int_2::operator+=||
|int_2:: operator <\<=||
|int_2::operator=||
|int_2::operator-=||
|int_2:: operator > > =||

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|[velikost – konstanta](#int_2__size)||

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|int_2:: g||
|int_2:: gr||
|int_2::r||
|int_2::rg||
|int_2::x||
|int_2::xy||
|int_2:: y||
|int_2::yx||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`int_2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors. h

**Obor názvů:** Concurrency:: Graphics

## <a name="ctor"></a>int_2

Výchozí konstruktor inicializuje všechny prvky s 0.

```cpp
int_2() restrict(amp,
    cpu);

int_2(
    int _V0,
    int _V1) restrict(amp,
    cpu);

int_2(
    int _V) restrict(amp,
    cpu);

int_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline int_2(
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

## <a name="int_2__size"></a>hodnota

```cpp
static const int size = 2;
```

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
