---
title: StopAndAnalyzeTracingSessionA
description: C++ Sestavení Insights SDK StopAndAnalyzeTracingSessionA odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 51a979b68cd87c5e7fd07b28acec80c2d7b81cf6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323724"
---
# <a name="stopandanalyzetracingsessiona"></a>StopAndAnalyzeTracingSessionA

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopAndAnalyzeTracingSessionA` zastaví probíhající relaci trasování a uloží výsledné trasování do dočasného souboru. Relace analýzy je pak okamžitě zahájena pomocí dočasného souboru jako vstupu. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionA(
    const char*                 sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>Parametry

*Název_relace*\
Název relace trasování zastavit. Použijte stejný název relace jako název předané [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*Statistiky*\
Ukazatel na [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) objekt. `StopAndAnalyzeTracingSessionA`zapíše statistiky shromažďování trasování v tomto objektu před vrácením.

*analysisDescriptor*\
Ukazatel na [objekt ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Tento objekt slouží ke konfiguraci relace `StopAndAnalyzeTracingSessionA`analýzy, která je spuštěna aplikací .

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
