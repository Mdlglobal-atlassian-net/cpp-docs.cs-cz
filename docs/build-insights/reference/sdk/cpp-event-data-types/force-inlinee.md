---
title: Třída ForceInlinee
description: C++ Build Insights SDK ForceInlinee odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c6a1af0384197a0a3b6062ad9ef30537c348190d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324784"
---
# <a name="forceinlinee-class"></a>Třída ForceInlinee

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `ForceInlinee` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události FORCE_INLINEE.](../event-table.md#force-inlinee)

## <a name="syntax"></a>Syntaxe

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `ForceInlinee` třídy [SimpleEvent](simple-event.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[SílaInlinee](#force-inlinee)

### <a name="functions"></a>Functions

[Velikost názvu](#name)
[Size](#size)

## <a name="forceinlinee"></a><a name="force-inlinee"></a>SílaInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost FORCE_INLINEE.](../event-table.md#force-inlinee)

## <a name="name"></a><a name="name"></a>Jméno

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název funkce vložené silou, kódované v UTF-8.

## <a name="size"></a><a name="size"></a>Velikost

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost funkce vložené silou jako počet zprostředkující instrukce.

::: moniker-end
