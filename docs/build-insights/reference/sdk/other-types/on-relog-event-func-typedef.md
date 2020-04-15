---
title: OnRelogEventFunc typedef
description: C++ Sestavení Insights SDK OnRelogEventFunc typedef odkaz.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2df8646d530c089b1239978d716b2b619a5b4b61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329066"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc typedef

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Typedef `OnRelogEventFunc` je jedním z podpisů funkce používaných ve struktuře [RELOG_CALLBACKS.](relog-callbacks-struct.md)

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro aktuální událost. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

*relogsession*\
Ukazatel relace pro opětovné nasávání, který se má použít při volání [události InjectEvent](../functions/inject-event.md).

*callbackContext*\
Hodnota kontextu, která byla nastavena pro toto zpětné volání v [RELOG_DESCRIPTOR](analysis-descriptor-struct.md).

### <a name="return-value"></a>Návratová hodnota

Hodnota [CALLBACK_CODE,](callback-code-enum.md) která určuje, co by se mělo stát dál.

::: moniker-end
