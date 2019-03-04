---
title: scheduler_interface – struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: 99a3ea8b6ad1f23b4f3d54b7f2f406a3d115b374
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283368"
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

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
