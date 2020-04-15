---
title: Třída kompilátoru
description: C++ Build Insights SDK odkaz na třídu kompilátoru.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9b0a2622c4bc0bc19d7222977fe24c060ee8709e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325028"
---
# <a name="compiler-class"></a>Třída kompilátoru

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Compiler` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte jej tak, aby odpovídaludálosti [KOMPILÁTORu.](../event-table.md#compiler)

## <a name="syntax"></a>Syntaxe

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy z základní `Compiler` třídy [Vyvolání](invocation.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Kompilátoru](#compiler)

## <a name="compiler"></a><a name="compiler"></a>Kompilátoru

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Událost [KOMPILÁTORU.](../event-table.md#compiler)

::: moniker-end
