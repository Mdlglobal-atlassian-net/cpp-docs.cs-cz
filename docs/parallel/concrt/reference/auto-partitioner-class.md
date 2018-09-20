---
title: auto_partitioner – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
dev_langs:
- C++
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2bb62d76733e77c2528a80dfc4e9ef358878895
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425398"
---
# <a name="autopartitioner-class"></a>auto_partitioner – třída

`auto_partitioner` Třída představuje výchozí metodu `parallel_for`, `parallel_for_each` a `parallel_transform` použít při vytváření oddílů rozsah se Iteruje přes. Tato metoda dělení employes rozsahu zcizování pro vyrovnávání zatížení také na iterovat zrušení.

## <a name="syntax"></a>Syntaxe

```
class auto_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[auto_partitioner](#ctor)|Vytvoří `auto_partitioner` objektu.|
|[~auto_partitioner Destructor](#dtor)|Odstraní `auto_partitioner` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`auto_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppl.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~ auto_partitioner –

Odstraní `auto_partitioner` objektu.

```
~auto_partitioner();
```

##  <a name="ctor"></a> auto_partitioner –

Vytvoří `auto_partitioner` objektu.

```
auto_partitioner();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
