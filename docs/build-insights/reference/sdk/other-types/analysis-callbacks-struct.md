---
title: ANALYSIS_CALLBACKS struktura
description: C++ Build Insights SDK ANALYSIS_CALLBACKS odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3c6de999b19657f999f884075ee53e21a4d2f2b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323510"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS struktura

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_CALLBACKS` se používá při inicializaci [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo [RELOG_DESCRIPTOR](relog-descriptor-struct.md) objektu. Určuje, které funkce se mají volat během analýzy nebo opětovného protokolování trasování trasování událostí pro Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `OnStartActivity` | Nazývá se zpracování události zahájení aktivity. |
| `OnStopActivity` | Nazývá se zpracování události zastavení aktivity. |
| `OnSimpleEvent` | Volána ke zpracování jednoduché události. |
| `OnTraceInfo` | Pro relace analýzy, volané na začátku každého průchodu analýzy. Pro opětovné seknutí relací, volané na začátku každého průchodu analýzy a znovu na začátku průchodu opětovným protokolováním. Tato funkce je volána pouze po OnBeginAnalysisPass byla volána. |
| `OnBeginAnalysis` | Pro relace analýzy, volané před zahájením průchodu analýzy. Pro opětovné seknutí relací, volal dvakrát před fáze analýzy začala: jednou oznámit zahájení relace opětovného přihlášení a ještě jednou oznámit začátek fáze analýzy. |
| `OnEndAnalysis` | Pro relace analýzy je tato funkce volána po ukončení všech průchodů analýzy. Pro opětovné seknutí relací je tato funkce volána po ukončení všech průchodů analýzy fáze analýzy. Poté se znovu zavolá po ukončení průchodu pro opětovné přihlášení. |
| `OnBeginAnalysisPass` | Volána při zahájení průchodu analýzy nebo opakování průchodu před zpracováním jakékoli události. |
| `OnEndAnalysisPass` | Volána při ukončení průchodu analýzy nebo opakování průchodu po zpracování všech událostí. |

## <a name="remarks"></a>Poznámky

Fáze analýzy relace opětovného přihlášení je považována za součást relace opětovného sloggingu a může obsahovat více průchodů analýzy. Z tohoto `OnBeginAnalysis` důvodu se volá dvakrát za sebou na začátku relace opětovného přihlášení. `OnEndAnalysis`na konci fáze analýzy, před zahájením fáze opětovného přihlášení a opět na konci fáze opětovného přihlášení. Fáze opětovného přihlášení vždy obsahuje jeden průchod opětovného přihlášení.

Je možné, že analyzátory budou součástí fáze analýzy i opětovného přihlášení relace opětovného přihlášení. Tyto analyzátory můžete určit, která fáze právě probíhá `OnEndAnalysis` udržováním sledování OnBeginAnalysis a dvojice volání. Dva `OnBeginAnalysis` hovory `OnEndAnalysis` bez jakéhokoli volání znamená, že fáze analýzy probíhá. Dva `OnBeginAnalysis` hovory `OnEndAnalysis` a jeden hovor znamená, že fáze opětovného přihlášení probíhá. Dvě OnBeginAnalysis `OnEndAnalysis` a dvě volání znamená, že obě fáze byly ukončeny.

Všichni členové `ANALYSIS_CALLBACKS` struktury musí ukazovat na platnou funkci. Další informace o podpisech přijatých funkcí naleznete v [tématech OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)a [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
