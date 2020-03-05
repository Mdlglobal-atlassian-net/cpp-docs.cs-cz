---
title: BottomUp – třída
description: Referenční C++ dokumentace třídy BottomUp sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- BottomUp
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fa26acfdf25acc3b78de71fd21b20cbf5a0df66b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333536"
---
# <a name="bottomup-class"></a>BottomUp – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `BottomUp` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [BOTTOM_UP](../event-table.md#bottom-up) události.

## <a name="syntax"></a>Syntaxe

```cpp
class BottomUp : public Activity
{
public:
    BottomUp(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `BottomUp` následující členy:

### <a name="constructors"></a>Konstruktory

[BottomUp](#bottom-up)

## <a name="bottom-up"></a>BottomUp

```cpp
BottomUp(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [BOTTOM_UP](../event-table.md#bottom-up) .

::: moniker-end
