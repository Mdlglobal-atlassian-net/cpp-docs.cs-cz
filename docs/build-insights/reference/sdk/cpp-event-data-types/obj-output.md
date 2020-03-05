---
title: ObjOutput – třída
description: Referenční C++ dokumentace třídy ObjOutput sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ObjOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 26cf110bcd086ab051174ebf0017a73370c0aa5e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333130"
---
# <a name="objoutput-class"></a>ObjOutput – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ObjOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [OBJ_OUTPUT](../event-table.md#obj-output) události.

## <a name="syntax"></a>Syntaxe

```cpp
class ObjOutput : public FileOutput
{
public:
    ObjOutput(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze základní třídy typu " [výstup](file-output.md) " třídy `ObjOutput` obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[ObjOutput](#obj-output)

## <a name="obj-output"></a>ObjOutput

```cpp
ObjOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [OBJ_OUTPUT](../event-table.md#obj-output) .

::: moniker-end
