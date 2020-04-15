---
title: Třída SimpleEvent
description: C++ Build Insights SDK SimpleEvent odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 414ff5c1af99acc612384c1ae39f6e12ab051275
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324366"
---
# <a name="simpleevent-class"></a>Třída SimpleEvent

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `SimpleEvent` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala jakékoli jednoduché události. Odkazovat na [tabulku událostí](../event-table.md) zobrazíte všechny události, `SimpleEvent` které mohou odpovídat třídy.

## <a name="syntax"></a>Syntaxe

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými [Event](event.md) členy ze `SimpleEvent` základní třídy Event obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[SimpleEvent](#simple-event)

## <a name="simpleevent"></a><a name="simple-event"></a>SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Jakákoliv jednoduchá událost.

::: moniker-end
