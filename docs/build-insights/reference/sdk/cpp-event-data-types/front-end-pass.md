---
title: Třída FrontEndPass
description: C++ Build Insights SDK FrontEndPass odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 137f553f1e495b7658ae89e69a48cec6b1988a81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324731"
---
# <a name="frontendpass-class"></a>Třída FrontEndPass

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FrontEndPass` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události FRONT_END_PASS.](../event-table.md#front-end-pass)

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndPass : public CompilerPass
{
public:
    FrontEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděné členy z jeho `FrontEndPass` [CompilerPass](compiler-pass.md) základní třídy, třída obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[Frontendpass](#front-end-pass)

## <a name="frontendpass"></a><a name="front-end-pass"></a>Frontendpass

```cpp
FrontEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost FRONT_END_PASS.](../event-table.md#front-end-pass)

::: moniker-end
