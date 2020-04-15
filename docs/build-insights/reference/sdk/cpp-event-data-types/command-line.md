---
title: Třída CommandLine
description: C++ Build Insights SDK CommandLine odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b35d688acf06579cc27f2fee053ef58032e204e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325051"
---
# <a name="commandline-class"></a>Třída CommandLine

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `CommandLine` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události COMMAND_LINE.](../event-table.md#command-line)

## <a name="syntax"></a>Syntaxe

```cpp
class CommandLine : public SimpleEvent
{
public:
    CommandLine(const RawEvent& event);

    const wchar_t* Value() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze základní `CommandLine` třídy [SimpleEvent](simple-event.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Commandline](#command-line)

### <a name="functions"></a>Functions

[Hodnota](#value)

## <a name="commandline"></a><a name="command-line"></a>Commandline

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost COMMAND_LINE.](../event-table.md#command-line)

## <a name="value"></a><a name="value"></a>Hodnotu

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující příkazový řádek. Hodnota zahrnuje argumenty, které byly získány ze souboru odpovědí \_\_a z \_proměnných prostředí, jako je CL, CL , Link a LINK\_.

::: moniker-end
