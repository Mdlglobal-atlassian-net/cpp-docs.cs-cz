---
title: AnalyzovatA
description: C++ Build Insights SDK AnalyzeA odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7c7602c49ab5f3ce67693424019e253727563293
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324129"
---
# <a name="analyzea"></a>AnalyzovatA

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `AnalyzeA` se používá k analýze událostí MSVC přečtených ze vstupního trasování událostí pro Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
enum RESULT_CODE AnalyzeA(
    const char*                inputLogFile,
    const ANALYSIS_DESCRIPTOR* analysisDescriptor);
```

### <a name="parameters"></a>Parametry

*inputLogFile*\
Vstupní trasování ETW, ze kterého chcete číst události.

*analysisDescriptor*\
Ukazatel na [objekt ANALYSIS_DESCRIPTOR.](../other-types/analysis-descriptor-struct.md) Tento objekt slouží ke konfiguraci analýzy.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
