---
title: StopAndAnalyzeTracingSession
description: C++ Build Insights SDK StopAndAnalyzeTracingSession odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c9bd4a092c22dfcdfb6d463b74207ec11ee6d64
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323702"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopAndAnalyzeTracingSession` zastaví probíhající relaci trasování a uloží výsledné trasování do dočasného souboru. Relace analýzy je pak okamžitě zahájena pomocí dočasného souboru jako vstupu. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parametry

*Název_relace*\
Název relace trasování zastavit. Použijte stejný název relace jako název předané [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*numberOfAnalysisPasses*\
Počet analýzy předá ke spuštění na trasování. Trasování získá průchod za předpokladu, analyzer skupiny jednou za průchod analýzy.

*Statistiky*\
Ukazatel na [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) objekt. `StopAndAnalyzeTracingSession`zapíše statistiky shromažďování trasování v tomto objektu před vrácením.

*skupina analyzátorů*\
Skupina analyzátorů použitá pro analýzu. Volání [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) vytvořit skupinu analyzátoru. Pokud chcete použít skupinu dynamických analyzátorů získanou z [makedynamicanalyzerGroup](make-dynamic-analyzer-group.md), nejprve `MakeStaticAnalyzerGroup`ji zapouzdřte do skupiny statických analyzátorů předáním její adresy společnosti .

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
