---
title: Struktura ANALYSIS_DESCRIPTOR
description: Odkaz C++ na strukturu ANALYSIS_DESCRIPTOR Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fc11ce11e1faaae02edb36aac447c18ea8107e35
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332479"
---
# <a name="analysis_descriptor-structure"></a>Struktura ANALYSIS_DESCRIPTOR

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_DESCRIPTOR` se používá s funkcemi [analyze](../functions/analyze-a.md) a [AnalyzeW](../functions/analyze-w.md) . Popisuje, jak by mělo být analyzováno trasování událostí pro Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct ANALYSIS_DESCRIPTOR_TAG
{
    unsigned                NumberOfPasses;
    ANALYSIS_CALLBACKS      Callbacks;
    void*                   Context;
} ANALYSIS_DESCRIPTOR;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `NumberOfPasses` | Počet průchodů analýzy, které by se měly provést v trasování ETW. |
| `Callbacks` | Objekt [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) , který určuje funkce, které mají být volány během relace analýzy. |
| `Context` | Uživatelem zadaný kontext, který se předává jako argument všem funkcím zpětného volání určených v `Callbacks` |

## <a name="remarks"></a>Poznámky

Struktura `Callbacks` akceptuje pouze ukazatele na nečlenské funkce. Toto omezení můžete obejít nastavením `Context` na ukazatel objektu. Tento ukazatel objektu se předává jako argument všem funkcím zpětného volání, které nepatří do členů. Tento ukazatel použijte k volání členských funkcí v rámci funkcí zpětného volání, které nepatří do členů.

::: moniker-end
