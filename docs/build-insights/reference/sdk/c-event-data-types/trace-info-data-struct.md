---
title: TRACE_INFO_DATA struktura
description: C++ Build Insights SDK TRACE_INFO_DATA odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 70ae17a376f79cad7a669d81e482f551afd0ec62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325281"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACE_INFO_DATA` popisuje trasování analyzovány nebo relogged.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `LogicalProcessorCount` | Počet logických procesorů v počítači, kde byla trasování shromážděna. |
| `TickFrequency` | Počet klíšťat za sekundu, které se mají použít při hodnocení doby trvání měřené v klíšťacích. |
| `StartTimestamp` | Toto pole je nastaveno na hodnotu značky zachycenou v době spuštění trasování. |
| `StopTimestamp` | Toto pole je nastaveno na hodnotu značky zachycenou v době, kdy bylo trasování zastaveno. |

## <a name="remarks"></a>Poznámky

Odečíst `StartTimestamp` `StopTimestamp` od získat počet klíšťat uplynulběhem celé trasování. Slouží `TickFrequency` k převodu výsledné hodnoty na časovou jednotku. Příklad, který převádí značky na časové jednotky, naleznete [v tématu EVENT_DATA](event-data-struct.md).

::: moniker-end
