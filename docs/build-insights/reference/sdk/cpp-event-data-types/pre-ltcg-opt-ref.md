---
title: Třída PreLTCGOptRef
description: C++ Build Insights SDK PreLTCGOptRef odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- PreLTCGOptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a48dc2db0345333da3ec66ccb3a345323b4f10c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324387"
---
# <a name="preltcgoptref-class"></a>Třída PreLTCGOptRef

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `PreLTCGOptRef` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události PRE_LTCG_OPT_REF.](../event-table.md#pre-ltcg-opt-ref)

## <a name="syntax"></a>Syntaxe

```cpp
class PreLTCGOptRef : public Activity
{
public:
    PreLTCGOptRef(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `PreLTCGOptRef` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Program PreLTCGOptRef](#pre-ltcg-opt-ref)

## <a name="preltcgoptref"></a><a name="pre-ltcg-opt-ref"></a>Program PreLTCGOptRef

```cpp
PreLTCGOptRef(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost PRE_LTCG_OPT_REF.](../event-table.md#pre-ltcg-opt-ref)

::: moniker-end
