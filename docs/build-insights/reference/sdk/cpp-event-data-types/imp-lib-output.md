---
title: ImpLibOutput – třída
description: Referenční C++ dokumentace třídy ImpLibOutput sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ImpLibOutput
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 068415250f2981724ad4efd14de9eaf67c546c96
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333249"
---
# <a name="impliboutput-class"></a>ImpLibOutput – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ImpLibOutput` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output) události.

## <a name="syntax"></a>Syntaxe

```cpp
class ImpLibOutput : public FileOutput
{
public:
    ImpLibOutput(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze základní třídy typu " [výstup](file-output.md) " třídy `ImpLibOutput` obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[ImpLibOutput](#imp-lib-output)

## <a name="imp-lib-output"></a>ImpLibOutput

```cpp
ImpLibOutput(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [IMP_LIB_OUTPUT](../event-table.md#imp-lib-output) .

::: moniker-end
