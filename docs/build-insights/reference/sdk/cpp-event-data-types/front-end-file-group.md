---
title: FrontEndFileGroup – třída
description: Referenční C++ dokumentace třídy FrontEndFileGroup sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 343a5a0d798d6c719088bd49668e70b10fba6d1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333326"
---
# <a name="frontendfilegroup-class"></a>FrontEndFileGroup – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FrontEndFileGroup` se používá s funkcemi [MatchEventStack](../functions/match-event-stack.md) a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ji pro spárování skupin [FRONT_END_FILEch](../event-table.md#front-end-file) událostí.

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své třídy [event\<FrontEndFile\>](event-group.md) základní třídy obsahuje Třída `FrontEndFileGroup` následující členy:

### <a name="constructors"></a>Konstruktory

[FrontEndFileGroup](#front-end-file-group)

## <a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>Parametry

\ *skupiny*
Skupina [FRONT_END_FILEch](../event-table.md#front-end-file) událostí.

::: moniker-end
