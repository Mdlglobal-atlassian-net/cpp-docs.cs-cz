---
title: norm – třída
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 56f879ef2fc0d3010ab4f64fedaf2570dac565d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272422"
---
# <a name="norm-class"></a>norm – třída

Představují normu číslo. Každý prvek je plovoucí bodu číslo v rozsahu [-1.0f, 1.0f].

## <a name="syntax"></a>Syntaxe

```
class norm;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Norm – konstruktor](#ctor)|Přetíženo. Výchozí konstruktor. Inicializujte na 0,0 f.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|norm::operator-||
|norm::operator--||
|Norm::Operator float|Operátor převodu. Převést norm číslo plovoucí desetinnou čárkou.|
|Norm::Operator * =||
|Norm::Operator / =||
|Norm::Operator ++||
|Norm::Operator +=||
|Norm::Operator =||
|Norm::Operator-=||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`norm`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors.h

**Namespace:** Concurrency::Graphics

##  <a name="ctor"></a> Norm –

Výchozí konstruktor. Inicializujte na 0,0 f.

```
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
Hodnoty použité k inicializaci.

*Ji_né*<br/>
Objekt použitý k inicializaci.

## <a name="see-also"></a>Viz také:

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
