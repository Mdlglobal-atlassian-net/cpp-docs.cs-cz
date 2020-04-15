---
title: Třída BackEndPass
description: C++ Build Insights SDK BackEndPass odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BackEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2b4b1a219abdbe418efaab4537f1c6dc9a22afb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325243"
---
# <a name="backendpass-class"></a>Třída BackEndPass

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `BackEndPass` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události BACK_END_PASS.](../event-table.md#back-end-pass)

## <a name="syntax"></a>Syntaxe

```cpp
class BackEndPass : public CompilerPass
{
public:
    BackEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděné členy z jeho `BackEndPass` [CompilerPass](compiler-pass.md) základní třídy, třída obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[Backendpass](#back-end-pass)

## <a name="backendpass"></a><a name="back-end-pass"></a>Backendpass

```cpp
BackEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost BACK_END_PASS.](../event-table.md#back-end-pass)

::: moniker-end
