---
title: Function – třída
description: Odkaz C++ na třídu funkce Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Function
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3ff66119007ed7172fed7e824287ab8617c70973
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333256"
---
# <a name="function-class"></a>Function – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `Function` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction](../functions/match-event-stack-in-member-function.md) . Použijte ho pro spárování události [funkce](../event-table.md#function) .

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

Spolu se zděděnými členy ze své základní třídy [aktivity](activity.md) obsahuje Třída `Function` následující členy:

### <a name="constructors"></a>Konstruktory

[Slouží](#function)

### <a name="functions"></a>Functions

[Název](#name)

## <a name="function"></a>Slouží

```cpp
Function(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

\ *události*
Událost [funkce](../event-table.md#function) .

## <a name="name"></a>Jméno

```cpp
const char* Name() const;
```

### <a name="return-value"></a>Návratová hodnota

Název funkce kódovaný v kódování UTF-8.

::: moniker-end
