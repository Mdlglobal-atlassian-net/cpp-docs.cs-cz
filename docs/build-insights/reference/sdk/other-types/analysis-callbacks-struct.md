---
title: Struktura ANALYSIS_CALLBACKS
description: Odkaz C++ na strukturu ANALYSIS_CALLBACKS Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332528"
---
# <a name="analysis_callbacks-structure"></a>Struktura ANALYSIS_CALLBACKS

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `ANALYSIS_CALLBACKS` se používá při inicializaci objektu [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Určuje funkce, které mají být volány během analýzy nebo znovu protokolovány trasování událostí pro Windows (ETW).

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
| `OnStartActivity` | Volá se, aby se zpracovala událost zahájení aktivity. |
| `OnStopActivity` | Volá se, aby se zpracovala událost zastavení aktivity. |
| `OnSimpleEvent` | Volá se, aby se zpracovala jednoduchá událost. |
| `OnTraceInfo` | Pro relace analýzy, které se nazývají na začátku každého analytického průchodu. Pro relace opětovného protokolování, které se nazývají na začátku každé analýzy, a znovu na začátku opakovaného protokolování. Tato funkce se volá jenom po volání OnBeginAnalysisPass. |
| `OnBeginAnalysis` | Pro relace analýzy, které byly volány před zahájením všech analytických průchodů. Pro relace znovu nahlašování, které se před začátkem analýzy vyvolaly dvakrát: jednou pro oznámení začátku relace znovu protokolování a další informace, které oznamuje začátek fáze analýzy. |
| `OnEndAnalysis` | Pro relace analýzy je tato funkce volána po ukončení všech průchodů analýzou. V případě relací znovu protokolovaných funkcí se tato funkce volá, když všechny analýzy projde fází analýzy. Pak se znovu volá po dokončení opětovného přihlášení. |
| `OnBeginAnalysisPass` | Volá se, když se před zpracováním jakékoli události projde nebo znovu přihlásí. |
| `OnEndAnalysisPass` | Volá se, když se dokončí analýza, nebo se po zpracování všech událostí znovu projde. |

## <a name="remarks"></a>Poznámky

Fáze analýzy relace opakovaného protokolování je považována za součást relace opakovaného protokolování a může obsahovat více průchodů analýz. Z tohoto důvodu se `OnBeginAnalysis` volá dvakrát v řádku na začátku relace opětovného protokolování. `OnEndAnalysis` se volá na konci fáze analýzy, než se spustí fáze opětovného protokolování, a teprve potom znovu na konci fáze opětovného protokolování. Fáze reprotokolovacího nástroje vždy obsahuje jedno přeprotokolovací průchod.

Je možné, že analyzátory budou součástí analýzy i fáze znovu protokolovací relace. Tyto analyzátory mohou určit, která fáze aktuálně probíhá, díky udržování přehledu o OnBeginAnalysis a `OnEndAnalysis` páry volání. Dvě `OnBeginAnalysis` volání bez jakéhokoli volání `OnEndAnalysis` znamená, že fáze analýzy pokračuje. Dvě `OnBeginAnalysis` volání a jedno `OnEndAnalysis` volání znamená, že probíhá fáze nového protokolování. Dvě OnBeginAnalysis a dvě volání `OnEndAnalysis` znamená, že obě fáze byly ukončeny.

Všichni členové `ANALYSIS_CALLBACKS` struktury musí ukazovat na platnou funkci. Další informace o přijatých podpisech funkcí naleznete v tématech [OnAnalysisEventFunc](on-analysis-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)a [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
