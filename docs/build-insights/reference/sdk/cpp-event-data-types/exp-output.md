---
title: Třída ExpOutput
description: C++ Build Insights SDK ExpOutput odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExpOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c8c5f2f260596c444df7841c2a3e0c65f5163f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324822"
---
# <a name="expoutput-class"></a>Třída ExpOutput

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ExpOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události EXP_OUTPUT.](../event-table.md#exp-output)

## <a name="syntax"></a>Syntaxe

```cpp
class ExpOutput : public FileOutput
{
public:
    ExpOutput(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `ExpOutput` třídy [FileOutput](file-output.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[ExpOutput](#exp-output)

## <a name="expoutput"></a><a name="exp-output"></a>ExpOutput

```cpp
ExpOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost EXP_OUTPUT.](../event-table.md#exp-output)

::: moniker-end
