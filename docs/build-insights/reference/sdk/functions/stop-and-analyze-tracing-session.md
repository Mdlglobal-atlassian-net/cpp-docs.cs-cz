---
title: StopAndAnalyzeTracingSession
description: Reference C++ k funkci StopAndAnalyzeTracingSession sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b1c605bb63ac093f90128a03c37b186226130912
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332612"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopAndAnalyzeTracingSession` zastaví probíhající relaci trasování a uloží výsledné trasování do dočasného souboru. Relace analýzy pak ihned začne používat dočasný soubor jako vstup. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

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

*název_relace*\
Název relace trasování, která se má zastavit. Použijte stejný název relace jako ten předaný do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*numberOfAnalysisPasses*\
Počet průchodů analýzy, které mají být spuštěny na daném trasování. Trasování se předává na základě zadané skupiny analyzátoru jednou za analýzu.

\ *statistiky*
Ukazatel na objekt [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . před vrácením `StopAndAnalyzeTracingSession` zapisuje statistiky shromažďování trasování v tomto objektu.

\a *analyzátoru*
Skupina analyzátoru použitá pro analýzu. Zavolejte [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) a vytvořte skupinu analyzátoru. Pokud chcete použít dynamickou skupinu analýz získanou z [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), nejdřív ji zapouzdřete do statické skupiny analyzátoru předáním adresy do `MakeStaticAnalyzerGroup`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
