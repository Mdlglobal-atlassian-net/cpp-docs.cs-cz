---
title: unorm – třída
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 7c9ec967be8be618e5f8ab3bad1bfd940bfeaef4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126302"
---
# <a name="unorm-class"></a>unorm – třída

Představuje unorm číslo. Každý prvek je číslo s plovoucí desetinnou čárkou v rozsahu [0,0 f, 1,0 f].

## <a name="syntax"></a>Syntaxe

```cpp
class unorm;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Konstruktor unorm](#ctor)|Přetíženo. Výchozí konstruktor Inicializovat na 0,0 f.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|unorm:: operator--||
|unorm:: operator float|Operátor převodu Převeďte unorm číslo na hodnotu s plovoucí desetinnou čárkou.|
|unorm:: operator * =||
|unorm:: operator/=||
|unorm:: operator + +||
|unorm:: operator + =||
|unorm:: operator =||
|unorm:: operator-=||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`unorm`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp_short_vectors. h

**Obor názvů:** Concurrency:: Graphics

## <a name="ctor"></a>unorm

Výchozí konstruktor Inicializovat na 0,0 f.

```cpp
unorm(
    void) restrict(amp,
    cpu);

explicit unorm(
    float _V) restrict(amp,
    cpu);

explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

explicit unorm(
    int _V) restrict(amp,
    cpu);

explicit unorm(
    double _V) restrict(amp,
    cpu);

unorm(
    const unorm& _Other) restrict(amp,
    cpu);

inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parametry

*_V*<br/>
Hodnota, která se má použít k inicializaci.

*_Other*<br/>
Objekt "norma" použitý k inicializaci.

## <a name="see-also"></a>Viz také

[Concurrency::graphics – obor názvů](concurrency-graphics-namespace.md)
