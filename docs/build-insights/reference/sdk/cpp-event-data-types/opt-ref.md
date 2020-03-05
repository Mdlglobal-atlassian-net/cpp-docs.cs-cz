---
title: OptRef – třída
description: Referenční C++ dokumentace třídy OptRef sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c2abad6489012250862bc0721663572d03261bd4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333102"
---
# <a name="optref-class"></a>OptRef – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `OptRef` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [OPT_REF](../event-table.md#opt-ref) události.

## <a name="syntax"></a>Syntaxe

```cpp
class OptRef : public Activity
{
public:
    OptRef(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `OptRef` následující členy:

### <a name="constructors"></a>Konstruktory

[OptRef](#opt-ref)

## <a name="opt-ref"></a>OptRef

```cpp
OptRef(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [OPT_REF](../event-table.md#opt-ref) .

::: moniker-end
