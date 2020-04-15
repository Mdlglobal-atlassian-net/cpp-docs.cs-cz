---
title: Třída InvocationGroup
description: C++ Build Insights SDK InvocationGroup odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff5a73d5304a21c314c0fc5ce442e0ffc23b28fd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324695"
---
# <a name="invocationgroup-class"></a>Třída InvocationGroup

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `InvocationGroup` se používá s [funkcemi MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte jej k přizpůsobení skupin obsahujících kombinaci událostí [KOMPILÁTORU](../event-table.md#compiler) a [LINKER.](../event-table.md#linker)

## <a name="syntax"></a>Syntaxe

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy z základní třídy [Vyvolání eventgroup\<\> ](event-group.md) obsahuje `InvocationGroup` třída následující členy:

### <a name="constructors"></a>Konstruktory

[Skupina vyvolání](#invocation-group)

## <a name="invocationgroup"></a><a name="invocation-group"></a>Skupina vyvolání

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parametry

*Skupiny*\
Skupina obsahující kombinaci [compiler](../event-table.md#compiler) a [LINKER](../event-table.md#linker) události.

::: moniker-end
