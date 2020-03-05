---
title: Relog
description: Referenční C++ informace o funkci relog sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1ce09101deebd957de4b9305762dc37f38b53f4e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332689"
---
# <a name="relog"></a>Relog

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `Relog` slouží ke čtení událostí MSVC z trasování událostí pro Windows (ETW) a jejich zápis do nového upraveného trasování ETW.

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

*TAnalyzerGroupMembers*\
Tento parametr je vždy odvozený.

*TReloggerGroupMembers*\
Tento parametr je vždy odvozený.

*inputLogFile*\
Vstupní trasování ETW, ze kterého chcete číst události.

*outputLogFile*\
Soubor, do kterého mají být zapsány nové události.

*numberOfAnalysisPasses*\
Počet průchodů analýzy, které mají být spuštěny na vstupním trasování. Trasování se předává na základě zadané skupiny analyzátoru jednou za analýzu.

*systemEventsRetentionFlags*\
Bitová maska, která určuje, které systémové události ETW mají zůstat v přeprotokolovaném trasování. Další informace najdete v tématu [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md).

\a *analyzátoru*
Skupina analyzátoru, která se používá pro fázi analýzy relace přeprotokolování. Zavolejte [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) a vytvořte skupinu analyzátoru. Chcete-li použít dynamickou skupinu analýz získanou z [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), nejprve ji zapouzdřete do statické skupiny analyzátoru předáním adresy do `MakeStaticAnalyzerGroup`.

\ opětovného *naprotokolovacího* nástroje
Skupina reprotokolovacích nástrojů, která znovu zapisuje události do trasovacího souboru zadaného v *outputLogFile*. Zavolejte [MakeStaticReloggerGroup](make-static-relogger-group.md) k vytvoření skupiny přeprotokolovacích souborů. Chcete-li použít dynamickou skupinu přeprotokolovacích souborů získanou z [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md), nejprve ji zapouzdřete do skupiny statických přeprotokolovacích souborů předáním její adresy do `MakeStaticReloggerGroup`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

### <a name="remark"></a>Přeznačit

Vstupní trasování se předává přes skupinu analyzátoru *numberOfAnalysisPasses* časy. K dispozici není žádná podobná možnost pro přehlašování. Trasování je předáno pouze jednou pro skupinu reprotokolovacích souborů po dokončení všech průchodů analýz.

Opětovné protokolování systémových událostí, jako jsou vzorky procesoru v rámci třídy reprotokolovacího nástroje, není podporováno. Pomocí parametru *systemEventsRetentionFlags* určete, které systémové události se mají zachovat ve výstupním trasování.

::: moniker-end
