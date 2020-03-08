---
title: StopTracingSession
description: Reference C++ k funkci StopTracingSession sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a4be229dcfddef0624869b789ee35e51336ac78e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332549"
---
# <a name="stoptracingsession"></a>StopTracingSession

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopTracingSession` zastaví probíhající relaci trasování a vytvoří nezpracovaný trasovací soubor. Nezpracované trasovací soubory se dají předat funkcím [analyze](analyze.md), [AnalzeA](analyze-a.md)a [AnalyzeW](analyze-w.md) , aby se spustila relace analýzy. Nezpracované trasovací soubory lze také předat funkcím [relog](relog.md), [relog](relog-a.md)a [RelogW](relog-w.md) , aby bylo možné spustit znovu protokolování relace. Spustitelné soubory, které volají `StopTracingSession`, musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
inline RESULT_CODE StopTracingSession(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);

inline RESULT_CODE StopTracingSession(
    const wchar_t*              sessionName
    const wchar_t*              outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>Parametry

*název_relace*\
Název relace trasování, která se má zastavit. Použijte stejný název relace jako ten předaný do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Cesta k konečnému výstupnímu souboru protokolu, ve kterém by se mělo Uložit nezpracovaná trasování

\ *statistiky*
Ukazatel na objekt [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . před vrácením `StopTracingSession` zapisuje statistiky shromažďování trasování v tomto objektu.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end