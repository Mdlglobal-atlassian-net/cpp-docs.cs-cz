---
title: CommandLine – třída
description: Referenční C++ dokumentace třídy příkazového řádku sady Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CommandLine
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ff16646920fe77f7f3b4cb8a194a38984c3e6c32
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333508"
---
# <a name="commandline-class"></a>CommandLine – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `CommandLine` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho ke spárování [COMMAND_LINE](../event-table.md#command-line) události.

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

Společně s děděnými členy ze své základní třídy [SimpleEvent](simple-event.md) obsahuje Třída `CommandLine` následující členy:

### <a name="constructors"></a>Konstruktory

[Řádek](#command-line)

### <a name="functions"></a>Functions

[Hodnota](#value)

## <a name="command-line"></a>Řádek

```cpp
CommandLine(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [COMMAND_LINE](../event-table.md#command-line) .

## <a name="value"></a>Osa

```cpp
const wchar_t Value() const;
```

### <a name="return-value"></a>Návratová hodnota

Řetězec obsahující příkazový řádek. Hodnota zahrnuje argumenty, které byly získány ze souboru odpovědí a z proměnných prostředí, jako je CL, \_CL\_, odkaz a \_propojení\_.

::: moniker-end
