---
title: Třída WholeProgramAnalysis
description: C++ Build Insights SDK WholeProgramAnalysis odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- WholeProgramAnalysis
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c68441b7da09f9880bbb2f97544b1ad8da2f631f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324118"
---
# <a name="wholeprogramanalysis-class"></a>Třída WholeProgramAnalysis

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `WholeProgramAnalysis` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události WHOLE_PROGRAM_ANALYSIS.](../event-table.md#whole-program-analysis)

## <a name="syntax"></a>Syntaxe

```cpp
class WholeProgramAnalysis : public Activity
{
public:
    WholeProgramAnalysis(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `WholeProgramAnalysis` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Analýza wholeprogram](#whole-program-analysis)

## <a name="wholeprogramanalysis"></a><a name="whole-program-analysis"></a>Analýza wholeprogram

```cpp
WholeProgramAnalysis(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost WHOLE_PROGRAM_ANALYSIS.](../event-table.md#whole-program-analysis)

::: moniker-end
