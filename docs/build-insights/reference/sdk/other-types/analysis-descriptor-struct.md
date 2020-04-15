---
title: ANALYSIS_DESCRIPTOR struktura
description: C++ Build Insights SDK ANALYSIS_DESCRIPTOR odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1de7f2a5bc3f02a327daaecf8c2cebc44687ba43
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323616"
---
# <a name="analysis_descriptor-structure"></a>ANALYSIS_DESCRIPTOR struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_DESCRIPTOR` se používá s [funkcemi AnalyzeA](../functions/analyze-a.md) a [AnalyzeW.](../functions/analyze-w.md) Popisuje, jak trasování událostí pro Windows (ETW) trasování by měly být analyzovány.

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
| `NumberOfPasses` | Počet průchodů analýzy, které by měly být provedeny přes trasování ETW. |
| `Callbacks` | Objekt [ANALYSIS_CALLBACKS,](analysis-callbacks-struct.md) který určuje, které funkce se mají volat během relace analýzy. |
| `Context` | Kontext poskytnutý uživatelem, který je předán jako argument všem funkcím zpětného volání určeným v`Callbacks` |

## <a name="remarks"></a>Poznámky

Struktura `Callbacks` přijímá pouze ukazatele na nečlenné funkce. Toto omezení můžete obejít nastavením `Context` ukazatele objektu. Tento ukazatel objektu bude předán jako argument všem funkcím zpětného volání bez členů. Pomocí tohoto ukazatele můžete volat členské funkce z nečlenských funkcí zpětného volání.

::: moniker-end
