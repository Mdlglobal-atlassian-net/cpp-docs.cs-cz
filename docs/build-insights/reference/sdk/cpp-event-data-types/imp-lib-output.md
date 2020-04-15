---
title: Třída ImpLibOutput
description: C++ Build Insights SDK ImpLibOutput odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ImpLibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 98905dfe75484e98e14a0fa575e75fe3ab284559
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324705"
---
# <a name="impliboutput-class"></a>Třída ImpLibOutput

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ImpLibOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události IMP_LIB_OUTPUT.](../event-table.md#imp-lib-output)

## <a name="syntax"></a>Syntaxe

```cpp
class ImpLibOutput : public FileOutput
{
public:
    ImpLibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `ImpLibOutput` třídy [FileOutput](file-output.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[ImpLibVýstup](#imp-lib-output)

## <a name="impliboutput"></a><a name="imp-lib-output"></a>ImpLibVýstup

```cpp
ImpLibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost IMP_LIB_OUTPUT.](../event-table.md#imp-lib-output)

::: moniker-end
