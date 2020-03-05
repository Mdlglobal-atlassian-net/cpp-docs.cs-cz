---
title: Třída výčtu AnalysisControl
description: Odkaz C++ na výčet AnalysisControl sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cf162c11e0a7109b8d733dab79df80782398e14d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332500"
---
# <a name="analysiscontrol-enum-class"></a>Třída výčtu AnalysisControl

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída výčtu `AnalysisControl` slouží k řízení toku relace analýzy nebo znovu protokolování. Vraťte kód `AnalysisControl` z členské funkce [IAnalyzer](ianalyzer-class.md) nebo [IRelogger](irelogger-class.md) , abyste mohli řídit, co by mělo probíhat dále.

## <a name="members"></a>Členové

|  |  |
|--|--|
| `BLOCK` | Zabrání dalšímu rozšiřování aktuální události ve skupině Analyzer nebo reprotokolovacího nástroje. |
| `CANCEL` | Zrušte aktuální analýzu nebo znovu protokolovací relaci. |
| `CONTINUE` | Aktuální analýza nebo relace znovu se budou normálně pokračovat. Rozšíří aktuální událost na další analyzátor nebo člena skupiny reprotokolovacího nástroje. |
| `FAILURE` | Zruší aktuální analýzu nebo znovu nahlašování a signalizuje chybu. |

::: moniker-end
