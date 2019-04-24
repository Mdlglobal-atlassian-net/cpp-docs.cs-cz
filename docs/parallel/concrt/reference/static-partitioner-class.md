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
ms.openlocfilehash: 5120e3c53dc00ba9d5c3a4218efe1dcfb8f92e28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337385"
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
|[static_partitioner](#ctor)|Vytvoří `static_partitioner` objektu.|
|[~static_partitioner Destructor](#dtor)|Odstraní `static_partitioner` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`static_partitioner`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ppl.h

**Namespace:** souběžnosti

##  <a name="dtor"></a> ~static_partitioner

Odstraní `static_partitioner` objektu.

```
~static_partitioner();
```

##  <a name="ctor"></a> static_partitioner –

Vytvoří `static_partitioner` objektu.

```
static_partitioner();
```

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
