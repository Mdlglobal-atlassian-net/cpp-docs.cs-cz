---
title: OnTraceInfoFunc – typedef
description: Referenční C++ materiály k OnTraceInfoFunc sestavení sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332346"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc – typedef

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

`OnTraceInfoFunc` typedef je jedním z signatur funkcí použitých ve strukturách [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) a [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*traceInfo*\
Objekt [TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md) , který obsahuje informace o aktuálně analyzovaném nebo přeprotokolovaných trasováních.

*callbackContext*\
Hodnota kontextu, která byla nastavena pro toto zpětné volání v [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Návratová hodnota

[CALLBACK_CODE](callback-code-enum.md) hodnota, která určuje, co by mělo proběhnout příště.

::: moniker-end
