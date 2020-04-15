---
title: Třída C2DLL
description: C++ Build Insights SDK C2DLL odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- C2DLL
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7711acf800999d4e97c3ae56fa2100a632a245b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325079"
---
# <a name="c2dll-class"></a>Třída C2DLL

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `C2DLL` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události C2_DLL.](../event-table.md#c2-dll)

## <a name="syntax"></a>Syntaxe

```cpp
class C2DLL : public Activity
{
public:
    C2DLL(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `C2DLL` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[C2DLL](#c2-dll)

## <a name="c2dll"></a><a name="c2-dll"></a>C2DLL

```cpp
C2DLL(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[C2_DLL](../event-table.md#c2-dll) událost.

::: moniker-end
