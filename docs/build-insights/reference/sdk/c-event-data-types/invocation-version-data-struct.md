---
title: INVOCATION_VERSION_DATA struktura
description: C++ Sestavení Insights SDK INVOCATION_VERSION_DATA odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1211b4eb999fd63767af71c6884d7d20d6920df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325475"
---
# <a name="invocation_version_data-structure"></a>INVOCATION_VERSION_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `INVOCATION_VERSION_DATA` popisuje číslo verze jako skupinu integrálních hodnot.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct INVOCATION_VERSION_DATA_TAG
{
    unsigned short VersionMajor;
    unsigned short VersionMinor;
    unsigned short BuildNumberMajor;
    unsigned short BuildNumberMinor;

} INVOCATION_VERSION_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `VersionMajor` | Hlavní číslo verze. |
| `VersionMinor` | Dílčí číslo verze. |
| `BuildNumberMajor` | Hlavní číslo sestavení. |
| `BuildNumberMinor` | Vedlejší číslo sestavení. |

::: moniker-end
