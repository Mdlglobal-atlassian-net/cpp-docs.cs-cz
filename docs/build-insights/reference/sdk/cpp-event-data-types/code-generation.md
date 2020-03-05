---
title: Strategii – třída
description: Referenční C++ dokumentace třídy strategii sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CodeGeneration
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1bc56794a197b9ae7bf116757581fb5a49699462
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333480"
---
# <a name="codegeneration-class"></a>Strategii – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `CodeGeneration` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [CODE_GENERATION](../event-table.md#code-generation) události.

## <a name="syntax"></a>Syntaxe

```cpp
class CodeGeneration : public Activity
{
public:
    CodeGeneration(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `CodeGeneration` následující členy:

### <a name="constructors"></a>Konstruktory

[Strategii](#code-generation)

## <a name="code-generation"></a>Strategii

```cpp
CodeGeneration(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [CODE_GENERATION](../event-table.md#code-generation) .

::: moniker-end
