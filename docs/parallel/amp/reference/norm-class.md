---
title: norm – třída
ms.date: 11/04/2016
f1_keywords:
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: b5740f33dea6aad79770f77f179803023432248a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447534"
---
# <a name="norm-class"></a>norm – třída

Představuje číslo normy. Každý prvek je číslo s plovoucí desetinnou čárkou v rozsahu [-1.0 f, 1,0 f].

## <a name="syntax"></a>Syntaxe

```cpp
class norm;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Norm – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor Inicializovat na 0,0 f.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|norm::operator-||
|Norm:: operator--||
|Norm:: operator float|Operátor převodu Převede normu číslo na hodnotu s plovoucí desetinnou čárkou.|
|Norm:: operator * =||
|Norm:: operator/=||
|Norm:: operator + +||
|Norm:: operator + =||
|Norm:: operator =||
|Norm:: operator-=||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`norm`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors. h

**Obor názvů:** Concurrency:: Graphics

## <a name="ctor"></a>Norm

Výchozí konstruktor Inicializovat na 0,0 f.

```cpp
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V*<br/>
Hodnota, která se má použít k inicializaci.

*_Other*<br/>
Objekt použitý k inicializaci.

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
