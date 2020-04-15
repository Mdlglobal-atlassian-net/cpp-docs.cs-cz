---
title: OnTraceInfoFunc typedef
description: C++ Sestavení Insights SDK OnTraceInfoFunc typedef odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b987d4db9852c2e52c148bb91015ad414c04d41b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329025"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Typedef `OnTraceInfoFunc` je jedním z podpisů funkce používaných v [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) a [RELOG_CALLBACKS](relog-callbacks-struct.md) struktury.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*traceInfo*\
Objekt [TRACE_INFO_DATA,](../c-event-data-types/trace-info-data-struct.md) který obsahuje informace o trasování aktuálně analyzovány nebo relogged.

*callbackContext*\
Hodnota kontextu, která byla nastavena pro toto zpětné volání v [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Návratová hodnota

Hodnota [CALLBACK_CODE,](callback-code-enum.md) která určuje, co by se mělo stát dál.

::: moniker-end
