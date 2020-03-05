---
title: Linker – třída
description: Referenční C++ příručka třídy linkeru Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Linker
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: bb8948d7772046e18d5db5002deed48d0dd88375
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333186"
---
# <a name="linker-class"></a>Linker – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Linker` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování události [linkeru](../event-table.md#linker) .

## <a name="syntax"></a>Syntaxe

```cpp
class Linker : public Invocation
{
public:
    Linker(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze základní třídy [vyvolání](invocation.md) , třída `Linker` obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[Linker](#linker)

## <a name="linker"></a>Linkeru

```cpp
Linker(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [linkeru](../event-table.md#linker) .

::: moniker-end
