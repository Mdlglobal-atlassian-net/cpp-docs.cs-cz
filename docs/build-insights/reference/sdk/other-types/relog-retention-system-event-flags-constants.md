---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS konstanty
description: Referenční C++ informace k konstantám sady Build Insights SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332318"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS konstanty

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Konstanty `RELOG_RETENTION_SYSTEM_EVENT_FLAGS` slouží k popisu, které systémové události mají být zachovány v přeprotokolovaném trasování. Použijte je k inicializaci `SystemEventsRetentionFlags` pole [RELOG_DESCRIPTOR](relog-descriptor-struct.md) struktury.

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
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | V případě přeprotokolovaných trasování Udržujte systémové události ve vzorovém procesoru. |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | Ponechte všechny systémové události v přeprotokolovaném trasování. |

## <a name="remarks"></a>Poznámky

::: moniker-end
