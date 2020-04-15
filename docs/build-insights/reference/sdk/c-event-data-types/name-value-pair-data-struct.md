---
title: NAME_VALUE_PAIR_DATA struktura
description: C++ Build Insights SDK NAME_VALUE_PAIR_DATA odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- NAME_VALUE_PAIR_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4a0bf8e8ba32d94d30a56d0ef26ca4ed0c9b0711
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325358"
---
# <a name="name_value_pair_data-structure"></a>NAME_VALUE_PAIR_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `NAME_VALUE_PAIR_DATA` popisuje dvojici názvů a hodnot.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct NAME_VALUE_PAIR_DATA_TAG
{
    const wchar_t*      Name;
    const wchar_t*      Value;
} NAME_VALUE_PAIR_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `Name` | Název |
| `Value` | Hodnota |

::: moniker-end
