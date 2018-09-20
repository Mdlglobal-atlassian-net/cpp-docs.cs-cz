---
title: affinity_partitioner – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1254b316a52bd3e61b3cafd81ba2e89ee88b62
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444642"
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner – třída

`affinity_partitioner` Třída je podobně jako `static_partitioner` třídy, ale zvyšuje přidružení mezipaměti podle svého výběru mapování podrozsahů na pracovních vláken. To výrazně zvýšit výkon při smyčku znovu provést prostřednictvím stejné datové sady, a data vejde se do mezipaměti. Všimněte si, že stejné `affinity_partitioner` objekt musí být použit s dalších iteracích paralelní smyčky, který se spouští nad konkrétní datové sady, abyste využili výhod data lokality.

## <a name="syntax"></a>Syntaxe

```
class affinity_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[affinity_partitioner](#ctor)|Vytvoří `affinity_partitioner` objektu.|
|[~ affinity_partitioner – destruktor](#dtor)|Zničí `affinity_partitioner` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`affinity_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppl.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~ affinity_partitioner –

Zničí `affinity_partitioner` objektu.

```
~affinity_partitioner();
```

##  <a name="ctor"></a> affinity_partitioner –

Vytvoří `affinity_partitioner` objektu.

```
affinity_partitioner();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
