---
title: Compiler – třída
description: Referenční C++ dokumentace třídy kompilátoru Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Compiler
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a63a0bad1ab6063d5986fec77b5135f500ded1ce
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333459"
---
# <a name="compiler-class"></a>Compiler – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Compiler` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho pro spárování události [kompilátoru](../event-table.md#compiler) .

## <a name="syntax"></a>Syntaxe

```cpp
class Compiler : public Invocation
{
public:
    Compiler(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze základní třídy [vyvolání](invocation.md) , třída `Compiler` obsahuje následující členy:

### <a name="constructors"></a>Konstruktory

[Přepínač](#compiler)

## <a name="compiler"></a>Přepínač

```cpp
Compiler(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [kompilátoru](../event-table.md#compiler) .

::: moniker-end
