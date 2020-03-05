---
title: Struktura TRACE_INFO_DATA
description: Odkaz C++ na strukturu TRACE_INFO_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333585"
---
# <a name="trace_info_data-structure"></a>Struktura TRACE_INFO_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `TRACE_INFO_DATA` popisuje analýzu nebo přeprotokolování trasování.

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
| `LogicalProcessorCount` | Počet logických procesorů v počítači, kde bylo trasování shromážděno. |
| `TickFrequency` | Počet taktů za sekundu, které se použijí při vyhodnocování doby trvání měřené v taktech. |
| `StartTimestamp` | Toto pole je nastaveno na hodnotu Tick zachycenou v okamžiku spuštění trasování. |
| `StopTimestamp` | Toto pole je nastaveno na hodnotu Tick zachycenou v okamžiku, kdy bylo trasování zastaveno. |

## <a name="remarks"></a>Poznámky

Odečíst `StartTimestamp` z `StopTimestamp` a získejte počet tiků uplynulých během celého trasování. Pomocí `TickFrequency` převeďte výslednou hodnotu na časovou jednotku. Příklad, který převádí takty na časové jednotky, naleznete v tématu [EVENT_DATA](event-data-struct.md).

::: moniker-end
