---
title: Analyzovat
description: Reference C++ k funkci analyzovat Přehled sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalyzeA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9f5a7b91bf0cd6fd45f97880a99e1f56a85d74ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332913"
---
# <a name="analyzea"></a>Analyzovat

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `AnalyzeA` slouží k analýze událostí MSVC čtených z trasování vstupních událostí pro Windows (ETW).

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
Ukazatel na objekt [ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md) . Pomocí tohoto objektu můžete nakonfigurovat analýzu.

### <a name="return-value"></a>Návratová hodnota

Kód výsledku z [RESULT_CODE](../other-types/result-code-enum.md) výčtu.

::: moniker-end
