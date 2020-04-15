---
title: Třída TopDown
description: C++ Build Insights SDK TopDown odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TopDown
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7c0c957fa17daaec34710debeda634192c63d1da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324215"
---
# <a name="topdown-class"></a>Třída TopDown

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TopDown` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události TOP_DOWN.](../event-table.md#top-down)

## <a name="syntax"></a>Syntaxe

```cpp
class TopDown : public Activity
{
public:
    TopDown(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `TopDown` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Shora dolů](#top-down)

## <a name="topdown"></a><a name="top-down"></a>Shora dolů

```cpp
TopDown(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost TOP_DOWN.](../event-table.md#top-down)

::: moniker-end
