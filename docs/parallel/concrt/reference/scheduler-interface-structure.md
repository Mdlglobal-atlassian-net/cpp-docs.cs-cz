---
title: scheduler_interface – struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 9fa51aa5bd1fdea4eb1c35488654f0b5003e2efe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612768"
---
# <a name="schedulerinterface-structure"></a>scheduler_interface – struktura

Rozhraní plánovače

## <a name="syntax"></a>Syntaxe

```
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[scheduler_interface::schedule](#schedule)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`scheduler_interface`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface.h

**Namespace:** souběžnosti

##  <a name="schedule"></a>  scheduler_interface::Schedule – metoda

```
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
