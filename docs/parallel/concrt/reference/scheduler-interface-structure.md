---
title: scheduler_interface – struktura
ms.date: 11/04/2016
f1_keywords:
- scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface
- PPLINTERFACE/concurrency::scheduler_interface::scheduler_interface::schedule
ms.assetid: 4de61c78-a2c6-4698-bd47-964baf7fa287
ms.openlocfilehash: da2ebc2f9c2878baefcfa792bac08f420dbbb281
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358790"
---
# <a name="scheduler_interface-structure"></a>scheduler_interface – struktura

Rozhraní plánovače

## <a name="syntax"></a>Syntaxe

```cpp
struct __declspec(novtable) scheduler_interface;
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[scheduler_interface::plán](#schedule)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`scheduler_interface`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplinterface.h

**Obor názvů:** souběžnost

## <a name="scheduler_interfaceschedule-method"></a><a name="schedule"></a>scheduler_interface::metoda plánu

```cpp
virtual void schedule(
    TaskProc_t,
void*) = 0;
```

## <a name="see-also"></a>Viz také

[obor názvů souběžnosti](concurrency-namespace.md)
