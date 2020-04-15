---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS konstanty
description: C++ Build Insights SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS konstanty odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 264d697cc905eb6b44c8ec7de835a552976f0eb8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323276"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS konstanty

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Konstanty `TRACING_SESSION_SYSTEM_EVENT_FLAGS` se používají k popisu, které systémové události shromažďovat během trasování. Použijte je k inicializaci `SystemEventFlags` pole [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) struktury.

## <a name="syntax"></a>Syntaxe

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>Členové

| Name (Název) | Události zapnuté tímto příznakem |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Tento příznak je ve výchozím nastavení aktivován sadou C++ Build Insights SDK, i když není zadán explicitně. Umožňuje základní systémové události, které jsou vyžadovány C++ Sestavení Insights správně fungovat. Události povolené tímto příznakem poskytují informace o procesech, vláknech a načítání bitové kopie. Tyto události nelze zakázat. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Ukázky procesoru |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Tento příznak zapne všechny systémové události. |

::: moniker-end
