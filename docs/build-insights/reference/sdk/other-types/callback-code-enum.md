---
title: CALLBACK_CODE výčtu
description: C++ Build Insights SDK CALLBACK_CODE výčtu odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CALLBACK_CODE
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0d3dcc70040f562cd40755188e545f709a807b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329195"
---
# <a name="callback_code-enum"></a>CALLBACK_CODE výčtu

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Výčet `CALLBACK_CODE` se používá řídit tok analýzy nebo opětovné hoprotokolování relace. Vrátí CALLBACK_CODE hodnotu z funkcí v [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) nebo [RELOG_CALLBACKS](relog-callbacks-struct.md) řídit, co by se mělo stát dál.

## <a name="members"></a>Členové

| Name (Název) | Hodnota | Popis |
|--|--|--|
| `CALLBACK_CODE_ANALYSIS_SUCCESS` | 1 (0x00000001) | Pokračujte v aktuální analýze nebo opětovném zahlcování relace normálně. |
| `CALLBACK_CODE_ANALYSIS_FAILURE` | 2 (0x00000002) | Zrušte aktuální analýzu nebo opětovné přihlášení relace a signalizujte chybu. |
| `CALLBACK_CODE_ANALYSIS_CANCEL` | 4 (0x00000004) | Zrušte aktuální analýzu nebo opětovné přihlášení relace. |

::: moniker-end
