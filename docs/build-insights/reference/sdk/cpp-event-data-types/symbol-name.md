---
title: Třída SymbolName
description: C++ Build Insights SDK SymbolName odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SymbolName
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1306fb43d6c2140a75b36c5f142532916cf26ae4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324359"
---
# <a name="symbolname-class"></a>Třída SymbolName

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `SymbolName` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události SYMBOL_NAME.](../event-table.md#symbol-name)

## <a name="syntax"></a>Syntaxe

```cpp
class SymbolName : public SimpleEvent
{
public:
    SymbolName(const RawEvent& event);

    const unsigned long long&  Key() const;
    const char*                Name() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `SymbolName` třídy [SimpleEvent](simple-event.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Název_symbolu](#symbol-name)

### <a name="functions"></a>Functions

[Název klíče](#key)
[Name](#name)

## <a name="key"></a><a name="key"></a>Klíč

```cpp
const unsigned long long& Key() const;
```

### <a name="return-value"></a>Návratová hodnota

Číselný identifikátor pro typ reprezentované tímto symbolem. Tento identifikátor je jedinečný v rámci front-endového průchodu kompilátoru.

## <a name="name"></a><a name="name"></a>Jméno

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název typu reprezentovaného symbolem, kódovaný v UTF-8.

## <a name="symbolname"></a><a name="symbol-name"></a>Název_symbolu

```cpp
SymbolName(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[SYMBOL_NAME](../event-table.md#symbol-name) událost.

::: moniker-end
