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
ms.openlocfilehash: f3c5792a13d9e63a05ce6710dea77828f2510f0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522444"
---
# <a name="simplepartitioner-class"></a>simple_partitioner – třída

`simple_partitioner` Třída reprezentuje statické dělení provést iteraci přes podle rozsahu `parallel_for`. Dělicí rozsahu rozdělí do bloků dat tak, aby měl každý blok minimální počet iterací určená velikost deduplikačního bloku dat.

## <a name="syntax"></a>Syntaxe

```
class simple_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[simple_partitioner](#ctor)|Vytvoří `simple_partitioner` objektu.|
|[~simple_partitioner Destructor](#dtor)|Odstraní `simple_partitioner` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`simple_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppl.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~ simple_partitioner –

Odstraní `simple_partitioner` objektu.

```
~simple_partitioner();
```

##  <a name="ctor"></a> simple_partitioner –

Vytvoří `simple_partitioner` objektu.

```
explicit simple_partitioner(_Size_type _Chunk_size);
```

### <a name="parameters"></a>Parametry

*_Chunk_size*<br/>
Požadovanou minimální velikost oddílu.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
