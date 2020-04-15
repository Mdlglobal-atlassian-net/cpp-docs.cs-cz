---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS konstanty
description: C++ Build Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS konstanty odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7110f809a819357b31951c203c1fa6ac9fb9f42e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323472"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS konstanty

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Konstanty `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` se používají k popisu, které systémové události zachovat v relogged trasování. Použijte je k inicializaci `SystemEventsRetentionFlags` pole [RELOG_DESCRIPTOR](relog-descriptor-struct.md) struktury.

## <a name="syntax"></a>Syntaxe

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Udržujte ukázkové systémové události procesoru v relogged trasování. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Uchovávejte všechny systémové události v relogged trasování. |

## <a name="remarks"></a>Poznámky

::: moniker-end
