---
title: Třída výčtu AnalysisControl
description: C++ Sestavení Insights SDK AnalysisControl odkaz na výčet.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- AnalysisControl
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e9431f878390127f2cefbe8f0ee42ca509e147de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323633"
---
# <a name="analysiscontrol-enum-class"></a>Třída výčtu AnalysisControl

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Výčet `AnalysisControl` třída se používá řídit tok analýzy nebo opětovné hoprotokolování relace. Vrátit `AnalysisControl` kód z [iAnalyzer](ianalyzer-class.md) nebo [IRelogger](irelogger-class.md) členské funkce řídit, co by se mělo stát dál.

## <a name="members"></a>Členové

|  |  |
|--|--|
| `BLOCK` | Zabrání šíření aktuální události v analyzátoru nebo skupině reloggeru. |
| `CANCEL` | Zrušte aktuální analýzu nebo opětovné přihlášení relace. |
| `CONTINUE` | Pokračujte v aktuální analýze nebo opětovném zahlcování relace normálně. Propagujte aktuální událost na dalšího člena analyzátoru nebo reloggerové skupiny. |
| `FAILURE` | Zrušte aktuální analýzu nebo opětovné přihlášení relace a signalizujte chybu. |

::: moniker-end
