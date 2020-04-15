---
title: Třída funkce
description: C++ Build Insights SDK odkaz na třídu třídy.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 69acbe4d6630de37120aec89a24a9f33d447009e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324711"
---
# <a name="function-class"></a>Třída funkce

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Function` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k odpovídající [událost FUNCTION.](../event-table.md#function)

## <a name="syntax"></a>Syntaxe

```cpp
class Function : public Activity
{
public:
    Function(const RawEvent& event);

    const char* Name() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `Function` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Funkce](#function)

### <a name="functions"></a>Functions

[Název](#name)

## <a name="function"></a><a name="function"></a>Funkce

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
Událost [FUNCTION.](../event-table.md#function)

## <a name="name"></a><a name="name"></a>Jméno

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název funkce, kódované v UTF-8.

::: moniker-end
