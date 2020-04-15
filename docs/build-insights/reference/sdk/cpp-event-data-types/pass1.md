---
title: Třída Pass1
description: C++ Build Insights SDK Pass1 odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass1
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 039c2cc92b8461009c235baa7e49484eb2a4f49f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324424"
---
# <a name="pass1-class"></a>Třída Pass1

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Pass1` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala události [PASS1.](../event-table.md#pass1)

## <a name="syntax"></a>Syntaxe

```cpp
class Pass1 : public LinkerPass
{
public:
    Pass1(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy z jeho `Pass1` [LinkerPass](linker-pass.md) základní třídy, třída obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[Průchod1](#pass1)

## <a name="pass1"></a><a name="pass1"></a>Průchod1

```cpp
Pass1(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Událost [PASS1.](../event-table.md#pass1)

::: moniker-end
