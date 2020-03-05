---
title: Třída vyvolání
description: Referenční C++ dokumentace třídy pro vyvolání sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333235"
---
# <a name="invocationgroup-class"></a>Třída vyvolání

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `InvocationGroup` se používá s funkcemi [MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ji pro spárování skupin, které obsahují kombinaci událostí [kompilátoru](../event-table.md#compiler) a [linkeru](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své třídy [event\<vyvolání\>](event-group.md) základní třídy třída `InvocationGroup` obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[Nevolání](#invocation-group)

## <a name="invocation-group"></a>Nevolání

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>Parametry

\ *skupiny*
Skupina obsahující kombinaci událostí [kompilátoru](../event-table.md#compiler) a [linkeru](../event-table.md#linker) .

::: moniker-end
