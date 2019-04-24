---
title: double_2 – třída
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::double_2::set_x
- amp_short_vectors/Concurrency::graphics::double_2::operator+=
- amp_short_vectors/Concurrency::graphics::double_2::operator=
- amp_short_vectors/Concurrency::graphics::double_2::operator/=
- amp_short_vectors/Concurrency::graphics::double_2::operator*=
- amp_short_vectors/Concurrency::graphics::double_2::yx
- amp_short_vectors/Concurrency::graphics::double_2::y
- amp_short_vectors/Concurrency::graphics::double_2::xy
- amp_short_vectors/Concurrency::graphics::double_2::set_xy
- amp_short_vectors/Concurrency::graphics::double_2::get_yx
- amp_short_vectors/Concurrency::graphics::double_2::set_yx
- amp_short_vectors/Concurrency::graphics::double_2::get_xy
- amp_short_vectors/Concurrency::graphics::double_2::operator++
- amp_short_vectors/Concurrency::graphics::double_2::get_x
- amp_short_vectors/Concurrency::graphics::double_2::operator-=
- amp_short_vectors/Concurrency::graphics::double_2::rg
- amp_short_vectors/Concurrency::graphics::double_2::gr
- amp_short_vectors/Concurrency::graphics::double_2::get_y
- amp_short_vectors/Concurrency::graphics::double_2::x
- amp_short_vectors/Concurrency::graphics::double_2::r
- amp_short_vectors/Concurrency::graphics::double_2::operator--
- amp_short_vectors/Concurrency::graphics::double_2
- amp_short_vectors/Concurrency::graphics::double_2::operator-
- amp_short_vectors/Concurrency::graphics::double_2::g
- amp_short_vectors/Concurrency::graphics::double_2::set_y
ms.assetid: c19c2d21-3cbf-4ce5-b460-3b8253688f82
ms.openlocfilehash: 9482c2839c4963d533eb643fa0ef86a5c66636a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182329"
---
# <a name="double2-class"></a>double_2 – třída

Představuje krátký vektor 2 double.

## <a name="syntax"></a>Syntaxe

```
class double_2;
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[double_2 – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor, inicializuje všechny prvky na 0.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|double_2::get_x||
|double_2::get_xy||
|double_2::get_y||
|double_2::get_yx||
|double_2::ref_g||
|double_2::ref_r||
|double_2::ref_x||
|double_2::ref_y||
|double_2::set_x||
|double_2::set_xy||
|double_2::set_y||
|double_2::set_yx||

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|double_2::Operator-||
|double_2::Operator-||
|double_2::Operator * =||
|double_2::Operator / =||
|double_2::Operator ++||
|double_2::Operator +=||
|double_2::Operator =||
|operátor double_2::Operator-=||

### <a name="public-constants"></a>Veřejné konstanty

|Název|Popis|
|----------|-----------------|
|double_2::size – konstanta||

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|double_2::g||
|double_2::GR||
|double_2::r||
|double_2::rg||
|double_2::x||
|double_2::XY||
|double_2::y||
|double_2::yx||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`double_2`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors.h

**Namespace:** Concurrency::Graphics

##  <a name="ctor"></a> double_2 –

Výchozí konstruktor, inicializuje všechny prvky na 0.

```
double_2() restrict(amp,
    cpu);

double_2(
    double _V0,
    double _V1) restrict(amp,
    cpu);

double_2(
    double _V) restrict(amp,
    cpu);

double_2(
    const double_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline double_2(
    const norm_2& _Other) restrict(amp,
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

##  <a name="double_2__size"></a> Velikost

```
static const int size = 2;
```

## <a name="see-also"></a>Viz také:

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
