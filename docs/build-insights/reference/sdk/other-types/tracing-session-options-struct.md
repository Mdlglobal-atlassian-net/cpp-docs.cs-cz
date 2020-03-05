---
title: Struktura TRACING_SESSION_OPTIONS
description: Odkaz C++ na strukturu TRACING_SESSION_OPTIONS Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332206"
---
# <a name="tracing_session_options-structure"></a>Struktura TRACING_SESSION_OPTIONS

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACING_SESSION_OPTIONS` se používá při inicializaci [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo struktury [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Popisuje, které události mají být zachyceny během shromažďování trasování.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `SystemEventFlags` | Bitová maska popisující systémové události, které se mají zachytit Další informace najdete v tématu [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md). |
| `MsvcEventFlags` | Bitová maska popisující MSVC události, které se mají zachytit Další informace najdete v tématu [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md). |

::: moniker-end
