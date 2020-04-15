---
title: Relog
description: C++ Build Insights SDK Relog odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28b290d2bf2880ce2f534fa1cd91750890e2fead
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323778"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `Relog` se používá ke čtení událostí MSVC z trasování trasování trasování událostí pro Windows (ETW) a zapsat je do nového, upraveného trasování ETW.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>Parametry

*Členové skupiny TAnalyzerGroup*\
Tento parametr je vždy odvodit.

*TReloggerČlenové skupiny*\
Tento parametr je vždy odvodit.

*inputLogFile*\
Vstupní trasování ETW, ze kterého chcete číst události.

*outputLogFile*\
Soubor, ve kterém chcete napsat nové události.

*numberOfAnalysisPasses*\
Počet analýzy předá ke spuštění na vstupní trasování. Trasování získá průchod za předpokladu, analyzer skupiny jednou za průchod analýzy.

*systemEventsRetentionFlags*\
Bitová maska, která určuje, které systémové události ETW zachovat v relogged trasování. Další informace naleznete v [tématu RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

*skupina analyzátorů*\
Skupina analyzátoru použitá pro fázi analýzy relace opětovného přihlášení. Volání [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) vytvořit skupinu analyzátoru. Chcete-li použít skupinu dynamických analyzátorů získanou ze [skupiny MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), nejprve ji zapouzdřte do skupiny statických analyzátorů předáním její adresy společnosti `MakeStaticAnalyzerGroup`.

*skupina relogger*\
Skupina relogger, která reloguje události do trasovacího souboru zadaného v *outputLogFile*. Volání [MakeStaticReloggerGroup](make-static-relogger-group.md) vytvořit skupinu relogger. Chcete-li použít dynamickou skupinu reloggerzí z [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), nejprve zapouzdřete uvnitř statické skupiny relogger předáním jeho adresu `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

### <a name="remark"></a>Poznámka

Vstupní trasování je předána prostřednictvím analyzátoru skupiny *numberOfAnalysisPasses* časy. Neexistuje žádná podobná možnost pro opětovné přihlášení průchodů. Trasování je předánka koryto skupiny relogger pouze jednou, po dokončení všech průchodů analýzy.

Opětovné uhlazení systémových událostí, jako jsou ukázky procesoru z třídy reloggeru, není podporováno. Pomocí parametru *systemEventsRetentionFlags* můžete rozhodnout, které systémové události mají být ve výstupním trasování uchovány.

::: moniker-end
