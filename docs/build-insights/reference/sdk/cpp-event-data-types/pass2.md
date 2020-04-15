---
title: Třída Pass2
description: C++ Build Insights SDK Pass2 odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass2
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 89b775c60b1d136c33dbaf2c4e39f247be7bb0bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324406"
---
# <a name="pass2-class"></a>Třída Pass2

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Pass2` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala události [PASS2.](../event-table.md#pass2)

## <a name="syntax"></a>Syntaxe

```cpp
class Pass2 : public LinkerPass
{
public:
    Pass2(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy z jeho `Pass2` [LinkerPass](linker-pass.md) základní třídy, třída obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[Průchod2](#pass2)

## <a name="pass2"></a><a name="pass2"></a>Průchod2

```cpp
Pass2(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Událost [PASS2.](../event-table.md#pass2)

::: moniker-end
