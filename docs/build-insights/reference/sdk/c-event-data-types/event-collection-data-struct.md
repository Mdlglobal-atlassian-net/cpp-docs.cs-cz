---
title: EVENT_COLLECTION_DATA struktura
description: C++ Build Insights SDK EVENT_COLLECTION_DATA odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_COLLECTION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 88ba39ede8c86f47c2e6458332ae005eddc06fda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325695"
---
# <a name="event_collection_data-structure"></a>EVENT_COLLECTION_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `EVENT_COLLECTION_DATA` popisuje pole [EVENT_DATA](event-data-struct.md) prvků.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct EVENT_COLLECTION_DATA_TAG
{
    unsigned int            Count;
    const EVENT_DATA*       Elements;

} EVENT_COLLECTION_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `Count` | Počet `EVENT_DATA` prvků v poli. |
| `Elements` | Ukazatel na `EVENT_DATA` první prvek v poli. |

::: moniker-end
