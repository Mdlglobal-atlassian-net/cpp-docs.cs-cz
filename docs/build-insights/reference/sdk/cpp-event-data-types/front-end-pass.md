---
title: FrontEndPass – třída
description: Referenční C++ dokumentace třídy FrontEndPass sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cc0bf38c46b51d4a49da46be88e23afa64c12cc8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333270"
---
# <a name="frontendpass-class"></a>FrontEndPass – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FrontEndPass` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [FRONT_END_PASS](../event-table.md#front-end-pass) události.

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndPass : public CompilerPass
{
public:
    FrontEndPass(const RawEvent& event);
};
```

## <a name="members"></a>Členové

Společně s děděnými členy ze své základní třídy [CompilerPass](compiler-pass.md) obsahuje Třída `FrontEndPass` následující členy:

### <a name="constructors"></a>Konstruktory

[FrontEndPass](#front-end-pass)

## <a name="front-end-pass"></a>FrontEndPass

```cpp
FrontEndPass(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [FRONT_END_PASS](../event-table.md#front-end-pass) .

::: moniker-end
