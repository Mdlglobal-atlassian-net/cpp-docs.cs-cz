---
title: Struktura INVOCATION_VERSION_DATA
description: Odkaz C++ na strukturu INVOCATION_VERSION_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_VERSION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 040b0f90b14133ec2b25f7a12d35b88d382c4f7a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333676"
---
# <a name="invocation_version_data-structure"></a>Struktura INVOCATION_VERSION_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

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
| `VersionMajor` | Hlavní číslo verze |
| `VersionMinor` | Vedlejší číslo verze |
| `BuildNumberMajor` | Hlavní číslo buildu. |
| `BuildNumberMinor` | Vedlejší číslo buildu. |

::: moniker-end
