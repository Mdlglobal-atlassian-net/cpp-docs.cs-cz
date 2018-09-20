---
title: scheduler_interface – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
dev_langs:
- C++
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2178eddef2dcf7c2f48a5667930bc639781628fb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425356"
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
