---
title: Třída OptLBR
description: C++ Build Insights SDK OptLBR odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptLBR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4cbd87134741d6fc09521f94bfdfbc099cb426a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324458"
---
# <a name="optlbr-class"></a>Třída OptLBR

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `OptLBR` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události OPT_LBR.](../event-table.md#opt-lbr)

## <a name="syntax"></a>Syntaxe

```cpp
class OptLBR : public Activity
{
public:
    OptLBR(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `OptLBR` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[OptLBR](#opt-lbr)

## <a name="optlbr"></a><a name="opt-lbr"></a>OptLBR

```cpp
OptLBR(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost OPT_LBR.](../event-table.md#opt-lbr)

::: moniker-end
