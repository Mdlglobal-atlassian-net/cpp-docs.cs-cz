---
title: Pass1 – třída
description: Referenční C++ dokumentace třídy Pass1 sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass1
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d81a933e21f6976624808be358230305459e4992
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333088"
---
# <a name="pass1-class"></a>Pass1 – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Pass1` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování s událostí [PASS1](../event-table.md#pass1) .

## <a name="syntax"></a>Syntaxe

```cpp
class Pass1 : public LinkerPass
{
public:
    Pass1(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své základní třídy [LinkerPass](linker-pass.md) obsahuje Třída `Pass1` následující členy:

### <a name="constructors"></a>Konstruktory

[Pass1](#pass1)

## <a name="pass1"></a>Pass1

```cpp
Pass1(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [PASS1](../event-table.md#pass1)

::: moniker-end
