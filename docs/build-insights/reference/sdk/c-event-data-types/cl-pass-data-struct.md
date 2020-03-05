---
title: Struktura CL_PASS_DATA
description: Odkaz C++ na strukturu CL_PASS_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- CL_PASS_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3df5b5bc1cddbadc4a4d432ae021dd8b338c532e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333823"
---
# <a name="cl_pass_data-structure"></a>Struktura CL_PASS_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `CL_PASS_DATA` popisuje průchod kompilací.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct CL_PASS_DATA_TAG
{
    int                         TranslationUnitPassCode;
    const wchar_t*              InputSourcePath;
    const wchar_t*              OutputObjectPath;

} CL_PASS_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `TranslationUnitPassCode` | Kód identifikující spuštěný průchod kompilace. Další informace najdete v tématu [TRANSLATION_UNIT_PASS_CODE](translation-unit-pass-code-enum.md). |
| `InputSourcePath` | C++ Zdrojový soubor jazyka C, na kterém je provedena tato kompilace. |
| `OutputObjectPath` | Soubor objektu vytvářený kompilátorem. |

::: moniker-end
