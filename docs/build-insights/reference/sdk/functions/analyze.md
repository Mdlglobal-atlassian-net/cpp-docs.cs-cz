---
title: Analýza
description: Odkaz na funkci SDK Analýzy přehledů sestavení jazyka C++.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 08b3643270cc785b3fbea36720d192b4a1473104
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324109"
---
# <a name="analyze"></a>Analýza

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `Analyze` se používá k analýze trasování událostí pro Windows (ETW) trasování získané z MSVC při trasování sestavení C++. Události v trasování ETW jsou předávány postupně do skupiny analyzátoru poskytované volajícím. Tato funkce podporuje víceprůchodové analýzy, které umožňují předávat datový proud událostí do skupiny analyzátorů vícekrát za sebou.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const char*                                   inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE Analyze(
    const wchar_t*                                inputLogFile,
    unsigned                                      numberOfPasses,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>Parametry

*Členové skupiny TAnalyzerGroup*\
Tento parametr je vždy odvodit.

*inputLogFile*\
Vstupní trasování ETW, ze kterého chcete číst události.

*numberOfPasses*\
Počet analýzy předá ke spuštění na vstupní trasování. Trasování získá průchod za předpokladu, analyzer skupiny jednou za průchod analýzy.

*skupina analyzátorů*\
Skupina analyzátorů použitá pro analýzu. Volání [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) vytvořit skupinu analyzátoru. Chcete-li použít skupinu dynamických analyzátorů získanou ze [skupiny MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), nejprve ji zapouzdřte do skupiny statických analyzátorů předáním její adresy společnosti `MakeStaticAnalyzerGroup`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
