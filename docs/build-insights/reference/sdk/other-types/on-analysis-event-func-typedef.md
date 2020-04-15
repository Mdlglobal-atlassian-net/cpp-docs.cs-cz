---
title: Atribut typu OnAnalysisEventFunc
description: C++ Sestavení Insights SDK OnAnalysisEventFunc typedef odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eacd174279caff0db22586d5e40d3a866afc4459
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329118"
---
# <a name="onanalysiseventfunc-typedef"></a>Atribut typu OnAnalysisEventFunc

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Typedef `OnAnalysisEventFunc` je jedním z podpisů funkce používaných ve struktuře [ANALYSIS_CALLBACKS.](analysis-callbacks-struct.md)

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro aktuální událost. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

*callbackContext*\
Hodnota kontextu, která byla nastavena pro toto zpětné volání v [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md) nebo [RELOG_DESCRIPTOR](relog-descriptor-struct.md).

### <a name="return-value"></a>Návratová hodnota

Hodnota [CALLBACK_CODE,](callback-code-enum.md) která určuje, co by se mělo stát dál.

::: moniker-end
