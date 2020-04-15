---
title: INVOCATION_DATA struktura
description: C++ Build Insights SDK INVOCATION_DATA odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4e1f428facac413d7a4a5c059452dd8cdb07be4c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325485"
---
# <a name="invocation_data-structure"></a>INVOCATION_DATA struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `INVOCATION_DATA` popisuje vyvolání kompilátoru nebo propojovacího serveru.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct INVOCATION_DATA_TAG
{
    int                         MSVCToolCode;

    INVOCATION_VERSION_DATA     ToolVersion;

    const char*                 ToolVersionString;
    const wchar_t*              WorkingDirectory;
    const wchar_t*              ToolPath;

} INVOCATION_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `MSVCToolCode` | Kód, který identifikuje typ vyvolání. Další informace naleznete [v tématu MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Objekt, který ukládá verzi vyvolaného nástroje jako skupinu integrálních hodnot. |
| `ToolVersionString` | Popisuje verzi vyvolaný nástroj v textové podobě. |
| `WorkingDirectory` | Adresář, ze kterého byla vyvolání provedena. |
| `ToolPath` | Absolutní cesta vyvolaný nástroj. |

::: moniker-end
