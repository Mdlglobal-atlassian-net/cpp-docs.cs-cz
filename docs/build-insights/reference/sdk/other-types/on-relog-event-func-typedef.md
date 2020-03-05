---
title: OnRelogEventFunc – typedef
description: Referenční C++ materiály k OnRelogEventFunc sestavení sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnRelogEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 619f9a142ad19a7809b867eda93f2db634825a8f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332388"
---
# <a name="onrelogeventfunc-typedef"></a>OnRelogEventFunc – typedef

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

`OnRelogEventFunc` typedef je jedním z signatur funkcí použitých ve struktuře [RELOG_CALLBACKS](relog-callbacks-struct.md) .

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnRelogEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    const void*                     relogSession,
    void*                           callbackContext);
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro aktuální událost. Další informace o zásobníkech událostí najdete v tématu [události](../event-table.md).

*relogSession*\
Ukazatel relace opakovaného protokolování, který se má použít při volání [InjectEvent](../functions/inject-event.md).

*callbackContext*\
Hodnota kontextu, která byla nastavena pro toto zpětné volání v [RELOG_DESCRIPTOR](analysis-descriptor-struct.md).

### <a name="return-value"></a>Návratová hodnota

[CALLBACK_CODE](callback-code-enum.md) hodnota, která určuje, co by mělo proběhnout příště.

::: moniker-end
