---
title: StopAndRelogTracingSession
description: C++ Build Insights SDK StopAndRelogTracingSession odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1f6f5af63d25504226707d977791430463374328
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323658"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopAndRelogTracingSession` zastaví probíhající relaci trasování a uloží výsledné trasování do dočasného souboru. Relace opětovného přihlášení je pak okamžitě začít používat dočasný soubor jako vstup. Konečné relogged trasování vytvořené relogging relace je uložen v souboru určeném volajícím. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parametry

*Název_relace*\
Název relace trasování zastavit. Použijte stejný název relace jako název předané [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Soubor, ve kterém chcete zapsat relogged trasování vytvořené relogging relace.

*Statistiky*\
Ukazatel na [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) objekt. `StopAndRelogTracingSession`zapíše statistiky shromažďování trasování v tomto objektu před vrácením.

*numberOfAnalysisPasses*\
Počet analýzy předá ke spuštění na trasování. Trasování získá průchod za předpokladu, analyzer skupiny jednou za průchod analýzy.

*systemEventsRetentionFlags*\
Bitová maska [RELOG_RETENTION_SYSTEM_EVENT_FLAGS,](../other-types/relog-retention-system-event-flags-constants.md) která určuje, které systémové události ETW mají být v relogged trace.

*skupina analyzátorů*\
Skupina analyzátoru použitá pro fázi analýzy relace opětovného přihlášení. Volání [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) vytvořit skupinu analyzátoru. Pokud chcete použít skupinu dynamických analyzátorů získanou z [makedynamicanalyzerGroup](make-dynamic-analyzer-group.md), nejprve `MakeStaticAnalyzerGroup`ji zapouzdřte do skupiny statických analyzátorů předáním její adresy společnosti .

*skupina relogger*\
Skupina relogger, která reloguje události do trasovacího souboru zadaného v *outputLogFile*. Volání [MakeStaticReloggerGroup](make-static-relogger-group.md) vytvořit skupinu relogger. Pokud chcete použít dynamickou skupinu reloggeru získanou z [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), nejprve `MakeStaticReloggerGroup`jej zapouzdřte do statické skupiny reloggeru předáním jeho adresy na adresu .

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

### <a name="remarks"></a>Poznámky

Vstupní trasování je předána prostřednictvím analyzátoru skupiny *numberOfAnalysisPasses* časy. Neexistuje žádná podobná možnost pro opětovné přihlášení průchodů. Trasování je předánka koryto skupiny relogger pouze jednou, po dokončení všech průchodů analýzy.

Opětovné uhlazení systémových událostí, jako jsou ukázky procesoru z třídy reloggeru, není podporováno. Pomocí parametru *systemEventsRetentionFlags* můžete rozhodnout, které systémové události mají být ve výstupním trasování uchovány.

::: moniker-end
