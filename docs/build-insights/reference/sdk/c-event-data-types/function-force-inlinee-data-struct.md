---
title: Struktura FUNCTION_FORCE_INLINEE_DATA
description: Odkaz C++ na strukturu FUNCTION_FORCE_INLINEE_DATA Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FUNCTION_FORCE_INLINEE_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3d6929f2f16e9b1bd79b7fb8b383b40e031268bf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333697"
---
# <a name="function_force_inlinee_data-structure"></a>Struktura FUNCTION_FORCE_INLINEE_DATA

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `FUNCTION_FORCE_INLINEE_DATA` popisuje vynuceně vloženou funkci.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct FUNCTION_FORCE_INLINEE_DATA_TAG
{
    const char*         Name;
    unsigned short      Size;

} FUNCTION_FORCE_INLINEE_DATA;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `Name` | Název funkce kódovaný v kódování UTF-8. |
| `Size` | Velikost funkce, jako počet zprostředkujících instrukcí. |

::: moniker-end
