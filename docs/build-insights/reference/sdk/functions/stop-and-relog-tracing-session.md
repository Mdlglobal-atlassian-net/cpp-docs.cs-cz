---
title: StopAndRelogTracingSession
description: Reference C++ k funkci StopAndRelogTracingSession sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e99568f9b509b89ccd0f0711433dec9d96d904bc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332591"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `StopAndRelogTracingSession` zastaví probíhající relaci trasování a uloží výsledné trasování do dočasného souboru. Relace, která se znovu zaznamená, pak okamžitě začne používat dočasný soubor jako vstup. Konečné přeprotokolované trasování vytvořené relací znovu protokolování je uloženo v souboru určeném volajícím. Spustitelné soubory volající tuto funkci musí mít oprávnění správce.

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

*název_relace*\
Název relace trasování, která se má zastavit. Použijte stejný název relace jako ten předaný do [StartTracingSession](start-tracing-session.md), [StartTracingSessionA](start-tracing-session-a.md)nebo [StartTracingSessionW](start-tracing-session-w.md).

*outputLogFile*\
Soubor, ve kterém se má zapsat přeprotokolované trasování vytvořené relací znovu protokolování.

\ *statistiky*
Ukazatel na objekt [TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md) . před vrácením `StopAndRelogTracingSession` zapisuje statistiky shromažďování trasování v tomto objektu.

*numberOfAnalysisPasses*\
Počet průchodů analýzy, které mají být spuštěny na daném trasování. Trasování se předává na základě zadané skupiny analyzátoru jednou za analýzu.

*systemEventsRetentionFlags*\
[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md) Bitová maska, která určuje, které systémové události ETW budou v přeprotokolovaných trasováních zachovány.

\a *analyzátoru*
Skupina analyzátoru, která se používá pro fázi analýzy relace přeprotokolování. Zavolejte [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) a vytvořte skupinu analyzátoru. Pokud chcete použít dynamickou skupinu analýz získanou z [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), nejdřív ji zapouzdřete do statické skupiny analyzátoru předáním adresy do `MakeStaticAnalyzerGroup`.

\ opětovného *naprotokolovacího* nástroje
Skupina reprotokolovacích nástrojů, která znovu zapisuje události do trasovacího souboru zadaného v *outputLogFile*. Zavolejte [MakeStaticReloggerGroup](make-static-relogger-group.md) k vytvoření skupiny přeprotokolovacích souborů. Pokud chcete použít dynamickou skupinu přeprotokolovacích souborů získanou z [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), nejprve ji zapouzdřete do skupiny statických přeprotokolovacích souborů předáním její adresy do `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

### <a name="remarks"></a>Poznámky

Vstupní trasování se předává přes skupinu analyzátoru *numberOfAnalysisPasses* časy. K dispozici není žádná podobná možnost pro přehlašování. Trasování je předáno pouze jednou pro skupinu reprotokolovacích souborů po dokončení všech průchodů analýz.

Opětovné protokolování systémových událostí, jako jsou vzorky procesoru v rámci třídy reprotokolovacího nástroje, není podporováno. Pomocí parametru *systemEventsRetentionFlags* určete, které systémové události se mají zachovat ve výstupním trasování.

::: moniker-end
