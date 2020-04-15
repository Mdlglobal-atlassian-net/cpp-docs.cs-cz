---
title: Třída EnvironmentVariable
description: C++ Build Insights SDK EnvironmentVariable odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EnvironmentVariable
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 963c52e0ea9e048448c6f2b3ac62d9938817467e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325022"
---
# <a name="environmentvariable-class"></a>Třída EnvironmentVariable

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `EnvironmentVariable` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Použijte ji tak, aby odpovídala [události ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

## <a name="syntax"></a>Syntaxe

```cpp
class EnvironmentVariable : public SimpleEvent
{
public:
    EnvironmentVariable(const RawEvent& event);

    const wchar_t* Name() const;
    const wchar_t* Value() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `EnvironmentVariable` třídy [SimpleEvent](simple-event.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Proměnná prostředí](#environment-variable)

### <a name="functions"></a>Functions

[Hodnota názvu](#name)
[Value](#value)

## <a name="environmentvariable"></a><a name="environment-variable"></a>Proměnná prostředí

```cpp
EnvironmentVariable(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost ENVIRONMENT_VARIABLE.](../event-table.md#environment-variable)

## <a name="name"></a><a name="name"></a>Jméno

```cpp
const wchar_t Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název proměnné prostředí.

## <a name="value"></a><a name="value"></a>Hodnotu

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota proměnné prostředí.

::: moniker-end
