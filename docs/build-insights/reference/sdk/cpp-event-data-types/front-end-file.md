---
title: Třída FrontEndFile
description: C++ Build Insights SDK FrontEndFile odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFile
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c40137724279ea2fd615729db39f0ac5c907b79e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324762"
---
# <a name="frontendfile-class"></a>Třída FrontEndFile

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `FrontEndFile` se používá s funkcemi [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)a [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Slouží k tomu, aby odpovídala [události FRONT_END_FILE.](../event-table.md#front-end-file)

## <a name="syntax"></a>Syntaxe

```cpp
class FrontEndFile : public Activity
{
public:
    FrontEndFile(const RawEvent& event);

    const char* Path() const;
};
```

## <a name="members"></a>Členové

Spolu s zděděnými členy ze `FrontEndFile` základní třídy [Aktivita](activity.md) obsahuje třída následující členy:

### <a name="constructors"></a>Konstruktory

[Soubor frontendů](#front-end-file)

### <a name="functions"></a>Functions

[Cesta](#path)

## <a name="frontendfile"></a><a name="front-end-file"></a>Soubor frontendů

```cpp
FrontEndFile(const RawEvent& event);
```

### <a name="parameters"></a>Parametry

*Událost*\
[Událost FRONT_END_FILE.](../event-table.md#front-end-file)

## <a name="path"></a><a name="path"></a>Cestu

```cpp
const char* Path() const;
```

### <a name="return-value"></a>Návratová hodnota

Absolutní cesta k souboru, kódovaná v UTF-8.

::: moniker-end
