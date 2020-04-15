---
title: StopTracingSessionW
description: C++ Build Insights SDK StopTracingSessionW odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6582e477ac6b13319ab5ab0f77295517548f7068
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323540"
---
# <a name="stoptracingsessionw"></a>StopTracingSessionW

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopTracingSessionW` zastaví probíhající relaci trasování a vytvoří nezpracovaný soubor trasování. Nezpracované trasovací soubory mohou být předány funkci [Analyzovat](analyze.md), [AnalzeA](analyze-a.md)a [AnalyzeW](analyze-w.md) a spustit relaci analýzy. Nezpracované trasovací soubory lze také předat funkci [Relog](relog.md), [RelogA](relog-a.md)a [RelogW](relog-w.md) a zahájit relaci opětovného přihlášení. Volání `StopTracingSessionW` spustitelných souborů musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE StopTracingSessionW(
    const wchar_t*              sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parametry

*Název_relace*\
Název relace trasování zastavit. Použijte stejný název relace jako název předané [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Cesta ke konečnému výstupnímu souboru protokolu, kde by mělo být nezpracovaná trasování uložena.

*Statistiky*\
Ukazatel na [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) objekt. `StopTracingSessionW`zapíše statistiky shromažďování trasování v tomto objektu před vrácením.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
