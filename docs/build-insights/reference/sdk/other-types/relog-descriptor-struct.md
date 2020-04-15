---
title: RELOG_DESCRIPTOR struktura
description: C++ Build Insights SDK RELOG_DESCRIPTOR odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c3aee49fe9f609ca37082693ddcfd5e838cc96a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328943"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_DESCRIPTOR` se používá s funkcemi [RelogA](../functions/relog-a.md) a [RelogW.](../functions/relog-w.md) Popisuje, jak trasování událostí pro Windows (ETW) trasování by měla být relogged.

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
| `NumberOfAnalysisPasses` | Počet průchodů analýzy, které by měly být provedeny přes trasování ETW během fáze analýzy relace opětovného přihlášení. |
| `AnalysisCallbacks` | Objekt [ANALYSIS_CALLBACKS,](analysis-callbacks-struct.md) který určuje, které funkce se mají volat během fáze analýzy relace opětovného správě. |
| `RelogCallbacks` | Objekt [RELOG_CALLBACKS,](relog-callbacks-struct.md) který určuje, které funkce se mají volat během fáze opětovného sekání relace. |
| `SystemEventsRetentionFlags` | Bitová maska [RELOG_RETENTION_SYSTEM_EVENT_FLAGS,](relog-retention-system-event-flags-constants.md) která určuje, které systémové události ETW mají být v relogged trace. |
| `AnalysisContext` | Kontext poskytnutý uživatelem, který je předán jako argument všem funkcím zpětného volání určeným v`AnalysisCallbacks` |
| `RelogContext` | Kontext poskytnutý uživatelem, který je předán jako argument všem funkcím zpětného volání určeným v`RelogCallbacks` |

## <a name="remarks"></a>Poznámky

Opětovné protokolování událostí ETW během relace opětovného přihlášení je řízeno `RelogCallbacks`uživatelem prostřednictvím funkcí zpětného volání uvedených v aplikaci . Události systému ETW, jako jsou například vzorky procesoru, však nejsou předávány do těchto funkcí zpětného volání. Toto `SystemEventsRetentionFlags` pole slouží k řízení opětovného přihlášení událostí systému ETW.

Struktury `AnalysisCallbacks` `RelogCallbacks` a přijímají pouze ukazatele na nečlenné funkce. Toto omezení můžete obejít tak, že je nastavíte na ukazatel objektu. Tento ukazatel objektu bude předán jako argument všem funkcím zpětného volání bez členů. Pomocí tohoto ukazatele můžete volat členské funkce z nečlenských funkcí zpětného volání.

Fáze analýzy relace opětovného přihlášení je vždy provedena před fází opětovného přihlášení.

::: moniker-end
