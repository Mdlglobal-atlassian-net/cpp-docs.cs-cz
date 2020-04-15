---
title: Třída linkeru
description: C++ Build Insights SDK Linker odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e5d4c0c3841377fc2e029c23d5cbbd076c8029cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324603"
---
# <a name="linker-class"></a>Třída linkeru

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Linker` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala události [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Syntaxe

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy z základní `Linker` třídy [Vyvolání](invocation.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Linker](#linker)

## <a name="linker"></a><a name="linker"></a>Linker

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Událost [LINKER.](../event-table.md#linker)

::: moniker-end
