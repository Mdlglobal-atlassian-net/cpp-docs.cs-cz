---
title: Analýza
description: Referenční C++ informace k analýze funkcí sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Analyze
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49161641d1cff1c64261d95bb2caace2f802543a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332864"
---
# <a name="analyze"></a>Analýza

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `Analyze` slouží k analýze trasování událostí pro Windows (ETW) získaného z MSVC při trasování C++ buildu. Události v trasování ETW jsou postupně přesměrovány do skupiny analyzátorů poskytované volajícím. Tato funkce podporuje analýzy s více průchody, které umožňují předávat datový proud událostí do skupiny analyzátorů několikrát v řádku.

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

*TAnalyzerGroupMembers*\
Tento parametr je vždy odvozený.

*inputLogFile*\
Vstupní trasování ETW, ze kterého chcete číst události.

*numberOfPasses*\
Počet průchodů analýzy, které mají být spuštěny na vstupním trasování. Trasování se předává na základě zadané skupiny analyzátoru jednou za analýzu.

\a *analyzátoru*
Skupina analyzátoru použitá pro analýzu. Zavolejte [MakeStaticAnalyzerGroup](make-static-analyzer-group.md) a vytvořte skupinu analyzátoru. Chcete-li použít dynamickou skupinu analýz získanou z [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md), nejprve ji zapouzdřete do statické skupiny analyzátoru předáním adresy do `MakeStaticAnalyzerGroup`.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
