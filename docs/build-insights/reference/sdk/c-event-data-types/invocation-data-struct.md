---
title: Struktura INVOCATION_DATA
description: Odkaz C++ na strukturu INVOCATION_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- INVOCATION_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b2e8ddcf79201d8bcbbb8eb298b96b5c7680f90e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333690"
---
# <a name="invocation_data-structure"></a>Struktura INVOCATION_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `INVOCATION_DATA` popisuje vyvolání kompilátoru nebo linkeru.

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
| `MSVCToolCode` | Kód, který identifikuje typ volání. Další informace najdete v tématu [MSVC_TOOL_CODE](msvc-tool-code-enum.md). |
| `ToolVersion` | Objekt, který ukládá verzi vyvolaného nástroje jako skupinu integrálních hodnot. |
| `ToolVersionString` | Popisuje verzi vyvolaného nástroje v textovém formátu. |
| `WorkingDirectory` | Adresář, ze kterého bylo provedeno vyvolání. |
| `ToolPath` | Absolutní cesta k vyvolanému nástroji. |

::: moniker-end
