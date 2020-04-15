---
title: Třída FrontEndFileGroup
description: C++ Build Insights SDK FrontEndFileGroup odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d2eebb650e59e750e5ebde74914dca5f0ef4779d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324761"
---
# <a name="frontendfilegroup-class"></a>Třída FrontEndFileGroup

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FrontEndFileGroup` se používá s [funkcemi MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k přizpůsobení skupin [FRONT_END_FILE](../event-table.md#front-end-file) událostí.

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní třídy `FrontEndFileGroup` [EventGroup\<\> FrontEndFile](event-group.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[FrontendFileGroup](#front-end-file-group)

## <a name="frontendfilegroup"></a><a name="front-end-file-group"></a>FrontendFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parametry

*Skupiny*\
Skupina [FRONT_END_FILE](../event-table.md#front-end-file) událostí.

::: moniker-end
