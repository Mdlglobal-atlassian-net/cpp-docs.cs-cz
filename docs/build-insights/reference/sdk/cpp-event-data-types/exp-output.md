---
title: ExpOutput – třída
description: Referenční C++ dokumentace třídy ExpOutput sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ExpOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bc108096bf2fffba876231bbf522295d0d0dcc0d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333354"
---
# <a name="expoutput-class"></a>ExpOutput – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ExpOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [EXP_OUTPUT](../event-table.md#exp-output) události.

## <a name="syntax"></a>Syntaxe

```cpp
class ExpOutput : public FileOutput
{
public:
    ExpOutput(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze základní třídy typu " [výstup](file-output.md) " třídy `ExpOutput` obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[ExpOutput](#exp-output)

## <a name="exp-output"></a>ExpOutput

```cpp
ExpOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [EXP_OUTPUT](../event-table.md#exp-output) .

::: moniker-end
