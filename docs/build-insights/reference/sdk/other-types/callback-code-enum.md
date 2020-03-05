---
title: Výčet CALLBACK_CODE
description: Odkaz C++ na výčet CALLBACK_CODE Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 68eaa9aa04d2f0a55ac12fb7dde14a080188a38d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332465"
---
# <a name="callback_code-enum"></a>Výčet CALLBACK_CODE

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

`CALLBACK_CODE` výčet se používá k řízení toku relace analýzy nebo znovu protokolování. Vrácení CALLBACK_CODE hodnoty z funkcí v [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) nebo [RELOG_CALLBACKS](relog-callbacks-struct.md) k určení toho, co by mělo probíhat dále.

## <a name="members"></a>Členové

| Název | Hodnota | Popis |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Aktuální analýza nebo relace znovu se budou normálně pokračovat. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Zruší aktuální analýzu nebo znovu nahlašování a signalizuje chybu. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Zrušte aktuální analýzu nebo znovu protokolovací relaci. |

::: moniker-end
