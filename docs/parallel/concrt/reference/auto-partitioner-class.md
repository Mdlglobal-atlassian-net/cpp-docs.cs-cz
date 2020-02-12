---
title: auto_partitioner – třída
ms.date: 11/04/2016
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
ms.openlocfilehash: 4d1d8f19069412240de8e9d69cdcfb34618f2796
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142869"
---
# <a name="auto_partitioner-class"></a>auto_partitioner – třída

Třída `auto_partitioner` představuje výchozí metodu `parallel_for`, `parallel_for_each` a `parallel_transform` použít k rozdělení rozsahu, na který iterovat. Tato metoda vytváření oddílů využívá krádež rozsahu pro vyrovnávání zatížení a zrušení iterací za sekundu.

## <a name="syntax"></a>Syntaxe

```cpp
class auto_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[auto_partitioner](#ctor)|Vytvoří objekt `auto_partitioner`.|
|[~ auto_partitioner destruktor](#dtor)|Odstraní objekt `auto_partitioner`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`auto_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** PPL. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ auto_partitioner

Odstraní objekt `auto_partitioner`.

```cpp
~auto_partitioner();
```

## <a name="ctor"></a>auto_partitioner

Vytvoří objekt `auto_partitioner`.

```cpp
auto_partitioner();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
