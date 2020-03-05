---
title: Linker – třída
description: Referenční C++ dokumentace třídy linkeru Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333207"
---
# <a name="linkergroup-class"></a>Linker – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `LinkerGroup` se používá s funkcemi [MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ji pro spárování skupin událostí [linkeru](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>Členové

Společně se zděděnými členy ze své třídy [event\<\>základní třídy linkeru](event-group.md) obsahuje Třída `LinkerGroup` následující členy:

### <a name="constructors"></a>Konstruktory

[Propojovacího programu](#linker-group)

## <a name="linker-group"></a>Propojovacího programu

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>Parametry

\ *skupiny*
Skupina událostí [linkeru](../event-table.md#linker) .

::: moniker-end
