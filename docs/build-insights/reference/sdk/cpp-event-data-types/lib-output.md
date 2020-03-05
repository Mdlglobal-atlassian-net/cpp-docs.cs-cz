---
title: LibOutput – třída
description: Referenční C++ dokumentace třídy LibOutput sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9ec0d8de5302d9893aedd28661b2234150e82e08
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333214"
---
# <a name="liboutput-class"></a>LibOutput – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `LibOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [LIB_OUTPUT](../event-table.md#lib-output) události.

## <a name="syntax"></a>Syntaxe

```cpp
class LibOutput : public FileOutput
{
public:
    LibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze základní třídy typu " [výstup](file-output.md) " třídy `LibOutput` obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[LibOutput](#lib-output)

## <a name="lib-output"></a>LibOutput

```cpp
LibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [LIB_OUTPUT](../event-table.md#lib-output) .

::: moniker-end
