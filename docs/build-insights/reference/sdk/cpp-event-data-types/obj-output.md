---
title: Třída ObjOutput
description: C++ Sestavení Insights SDK ObjOutput odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 194253e8995401114e2529b868b36c9823510a4f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324496"
---
# <a name="objoutput-class"></a>Třída ObjOutput

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ObjOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události OBJ_OUTPUT.](../event-table.md#obj-output)

## <a name="syntax"></a>Syntaxe

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `ObjOutput` třídy [FileOutput](file-output.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[ObjVýstup](#obj-output)

## <a name="objoutput"></a><a name="obj-output"></a>ObjVýstup

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost OBJ_OUTPUT.](../event-table.md#obj-output)

::: moniker-end
