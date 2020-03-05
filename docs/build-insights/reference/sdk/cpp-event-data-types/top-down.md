---
title: TopDown – třída
description: Referenční C++ dokumentace třídy topdown sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TopDown
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2d4ef1f2f824bca9ab8e45f8fb030727e6e4007b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332948"
---
# <a name="topdown-class"></a>TopDown – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `TopDown` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [TOP_DOWN](../event-table.md#top-down) události.

## <a name="syntax"></a>Syntaxe

```cpp
class TopDown : public Activity
{
public:
    TopDown(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `TopDown` následující členy:

### <a name="constructors"></a>Konstruktory

[TopDown](#top-down)

## <a name="top-down"></a>TopDown

```cpp
TopDown(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [TOP_DOWN](../event-table.md#top-down) .

::: moniker-end
