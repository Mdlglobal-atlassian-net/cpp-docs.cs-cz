---
title: simple_partitioner – třída
ms.date: 11/04/2016
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
ms.openlocfilehash: 503f36b90c5eb3319f9aa2d56528172ffa95bb11
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142501"
---
# <a name="simple_partitioner-class"></a>simple_partitioner – třída

Třída `simple_partitioner` představuje statický segmentování rozsahu, na které prochází `parallel_for`. Dělicí metoda rozdělí rozsah na bloky dat tak, aby měl každý blok alespoň počet iterací určených velikostí bloku dat.

## <a name="syntax"></a>Syntaxe

```cpp
class simple_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[simple_partitioner](#ctor)|Vytvoří objekt `simple_partitioner`.|
|[~ simple_partitioner destruktor](#dtor)|Odstraní objekt `simple_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`simple_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ simple_partitioner

Odstraní objekt `simple_partitioner`.

```cpp
~simple_partitioner();
```

## <a name="ctor"></a>simple_partitioner

Vytvoří objekt `simple_partitioner`.

```cpp
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Parametry

*_Chunk_size*<br/>
Minimální velikost oddílu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
