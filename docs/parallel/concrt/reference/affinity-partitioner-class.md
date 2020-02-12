---
title: affinity_partitioner – třída
ms.date: 11/04/2016
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
ms.openlocfilehash: 0ae6bbee49d1b8873190a7054e55f65b40b31b13
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142879"
---
# <a name="affinity_partitioner-class"></a>affinity_partitioner – třída

Třída `affinity_partitioner` je podobná `static_partitioner` třídě, ale vylepšuje spřažení mezipaměti podle výběru mapování dílčích rozsahů na pracovní vlákna. Může výrazně zvýšit výkon, když se smyčka znovu spustí přes stejnou datovou sadu a data se vejdou do mezipaměti. Všimněte si, že stejný objekt `affinity_partitioner` musí být použit s následnými iteracemi paralelní smyčky spouštěné přes konkrétní datovou sadu, aby bylo možné využít data z místního prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
class affinity_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Vytvoří objekt `affinity_partitioner`.|
|[~ affinity_partitioner destruktor](#dtor)|Odstraní objekt `affinity_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`affinity_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ affinity_partitioner

Odstraní objekt `affinity_partitioner`.

```cpp
~affinity_partitioner();
```

## <a name="ctor"></a>affinity_partitioner

Vytvoří objekt `affinity_partitioner`.

```cpp
affinity_partitioner();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
