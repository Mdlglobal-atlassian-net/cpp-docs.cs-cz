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
ms.openlocfilehash: a0d06326b2ecbf3c427ae24b45751f7053778a0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500890"
---
# <a name="staticpartitioner-class"></a>static_partitioner – třída

`static_partitioner` Třída reprezentuje statické dělení provést iteraci přes podle rozsahu `parallel_for`. Dělicí rozdělí rozsah tolik bloky dat jsou k dispozici Plánovač inteligentním pracovních procesů.

## <a name="syntax"></a>Syntaxe

```
class static_partitioner;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[static_partitioner –](#ctor)|Vytvoří `static_partitioner` objektu.|
|[~ static_partitioner – destruktor](#dtor)|Odstraní `static_partitioner` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`static_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppl.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~ static_partitioner –

Odstraní `static_partitioner` objektu.

```
~static_partitioner();
```

##  <a name="ctor"></a> static_partitioner –

Vytvoří `static_partitioner` objektu.

```
static_partitioner();
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
