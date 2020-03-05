---
title: Thread – třída
description: Odkaz C++ na třídu vláken sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Thread
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a74eb130bd3f8be949fef0c19d545f61a72f3934
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332962"
---
# <a name="thread-class"></a>Thread – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Thread` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování události [vlákna](../event-table.md#thread) .

## <a name="syntax"></a>Syntaxe

```cpp
class Thread : public Activity
{
public:
    Thread(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `Thread` následující členy:

### <a name="constructors"></a>Konstruktory

[Doporučujeme](#thread)

## <a name="thread"></a>Doporučujeme

```cpp
Thread(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [vlákna](../event-table.md#thread) .

::: moniker-end
