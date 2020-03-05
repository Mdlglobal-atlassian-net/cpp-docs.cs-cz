---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS konstanty
description: Referenční C++ informace k konstantám sady Build Insights SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332353"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS konstanty

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Konstanty `TRACING_SESSION_SYSTEM_EVENT_FLAGS` slouží k popisu, které systémové události se mají shromáždit během trasování. Použijte je k inicializaci `SystemEventFlags` pole [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md) struktury.

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

| Název | Události zapnuté tímto příznakem |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | Tento příznak je ve výchozím nastavení aktivován sadou C++ SDK Build Insights, i když není explicitně zadaný. Umožňuje základní systémové události, které jsou požadovány C++ pro správné fungování sestav Build Insights. Události povolené tímto příznakem poskytují informace o procesech, vláknech a načítání obrázků. Tyto události nemůžete zakázat. |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | Ukázky procesoru |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | Tento příznak zapne všechny systémové události. |

::: moniker-end
