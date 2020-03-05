---
title: Struktura RELOG_DESCRIPTOR
description: Odkaz C++ na strukturu RELOG_DESCRIPTOR Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332325"
---
# <a name="relog_descriptor-structure"></a>Struktura RELOG_DESCRIPTOR

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_DESCRIPTOR` se používá s funkcemi [relog](../functions/relog-a.md) a [RelogW](../functions/relog-w.md) . Popisuje, jak by se mělo přeprotokolovat trasování událostí pro Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | Počet průchodů analýz, které by se měly provést v trasování ETW během fáze analýzy relace pro přeprotokolování. |
| `AnalysisCallbacks` | Objekt [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md) , který určuje, které funkce se mají volat během fáze analýzy v rámci přehlašování. |
| `RelogCallbacks` | Objekt [RELOG_CALLBACKS](relog-callbacks-struct.md) , který určuje, které funkce se mají volat během fáze rehlašování relace znovu. |
| `SystemEventsRetentionFlags` | [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md) Bitová maska, která určuje, které systémové události ETW budou v přeprotokolovaných trasováních zachovány. |
| `AnalysisContext` | Uživatelem zadaný kontext, který se předává jako argument všem funkcím zpětného volání určených v `AnalysisCallbacks` |
| `RelogContext` | Uživatelem zadaný kontext, který se předává jako argument všem funkcím zpětného volání určených v `RelogCallbacks` |

## <a name="remarks"></a>Poznámky

Po přeprotokolování událostí ETW během relace znovu protokolování je uživatel řízen funkcemi zpětného volání zadaných v `RelogCallbacks`. Systémové události ETW, jako jsou například ukázkové PROCESORy, nejsou předávány těmto funkcím zpětného volání. Pomocí pole `SystemEventsRetentionFlags` můžete řídit, jak se znovu přihlašuje systémové události ETW.

Struktury `AnalysisCallbacks` a `RelogCallbacks` akceptují pouze ukazatele na funkce, které nejsou členské. Toto omezení můžete obejít tak, že je nastavíte na ukazatel objektu. Tento ukazatel objektu se předává jako argument všem funkcím zpětného volání, které nepatří do členů. Tento ukazatel použijte k volání členských funkcí v rámci funkcí zpětného volání, které nepatří do členů.

Fáze analýzy relace přeprotokolování je vždy prováděna před fází znovu protokolování.

::: moniker-end
