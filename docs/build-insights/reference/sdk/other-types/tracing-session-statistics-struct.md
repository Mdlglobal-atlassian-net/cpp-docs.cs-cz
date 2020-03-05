---
title: Struktura TRACING_SESSION_STATISTICS
description: Odkaz C++ na strukturu TRACING_SESSION_OPTIONS Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa7c0a861d80fd3ebff85eb7ecb17dd05ae869e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332199"
---
# <a name="tracing_session_statistics-structure"></a>Struktura TRACING_SESSION_STATISTICS

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACING_SESSION_STATISTICS` popisuje statistiku shromažďovaného trasování. Jeho pole jsou nastavena při zastavování relace trasování.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `MSVCEventsLost` | Počet vyřazených událostí MSVC. |
| `MSVCBuffersLost` | Počet vyřazených vyrovnávacích pamětí událostí MSVC. |
| `SystemEventsLost` | Počet vyřazených systémových událostí. |
| `SystemBuffersLost` | Počet vyřazených vyrovnávacích pamětí systémových událostí. |

## <a name="remarks"></a>Poznámky

Tato struktura je naplněna při volání následujících funkcí:

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
