---
title: Třída LinkerGroup
description: C++ Build Insights SDK LinkerGroup odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c59d62938e5bd7b839ad12a321a03510e708e0fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324648"
---
# <a name="linkergroup-class"></a>Třída LinkerGroup

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `LinkerGroup` se používá s [funkcemi MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k přizpůsobení skupin událostí [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Syntaxe

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní třídy [EventGroup\<Linker\> ](event-group.md) obsahuje `LinkerGroup` třída následující členy:

### <a name="constructors"></a>Konstruktory

[Skupina linkerů](#linker-group)

## <a name="linkergroup"></a><a name="linker-group"></a>Skupina linkerů

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parametry

*Skupiny*\
Skupina událostí [LINKER.](../event-table.md#linker)

::: moniker-end
