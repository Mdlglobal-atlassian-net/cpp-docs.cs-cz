---
title: static_partitioner – třída
ms.date: 11/04/2016
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
ms.openlocfilehash: 7a58daa27bc7a2f51f78a3068a2f152979ffdd72
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142682"
---
# <a name="static_partitioner-class"></a>static_partitioner – třída

Třída `static_partitioner` představuje statický segmentování rozsahu, na které prochází `parallel_for`. Dělicí metoda rozdělí rozsah do tolika bloků dat, kolik jsou zaměstnanci k dispozici pro základní Plánovač.

## <a name="syntax"></a>Syntaxe

```cpp
class static_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[static_partitioner](#ctor)|Vytvoří objekt `static_partitioner`.|
|[~ static_partitioner destruktor](#dtor)|Odstraní objekt `static_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`static_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ static_partitioner

Odstraní objekt `static_partitioner`.

```cpp
~static_partitioner();
```

## <a name="ctor"></a>static_partitioner

Vytvoří objekt `static_partitioner`.

```cpp
static_partitioner();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
