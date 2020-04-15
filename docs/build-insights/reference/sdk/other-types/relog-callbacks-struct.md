---
title: struktura RELOG_CALLBACKS
description: C++ Build Insights SDK RELOG_CALLBACKS odkaz na strukturu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 60e7db81a48731090a23b82332704a79a51e97df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328962"
---
# <a name="relog_callbacks-structure"></a>struktura RELOG_CALLBACKS

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_CALLBACKS` se používá při inicializaci [RELOG_DESCRIPTOR](relog-descriptor-struct.md) objektu. Určuje, které funkce se mají volat během opětovného přihlášení trasování trasování událostí pro Windows (ETW).

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>Členové

|  |  |
|--|--|
| `OnStartActivity` | Nazývá se zpracování události zahájení aktivity. |
| `OnStopActivity` | Nazývá se zpracování události zastavení aktivity. |
| `OnSimpleEvent` | Volána ke zpracování jednoduché události. |
| `OnTraceInfo` | Volána jednou na začátku relogging `OnBeginReloggingPass` průchodu, poté, co byl volán. |
| `OnBeginRelogging` | Volána při zahájení relace opětovného přihlášení před zahájením opakování průchodu. |
| `OnEndRelogging` | Volána při ukončení relace opětovného přihlášení po ukončení opakování průchodu. |
| `OnBeginReloggingPass` | Volána při zahájení opakování průchodu, před zpracováním jakékoli události. |
| `OnEndReloggingPass` | Volána při ukončení opakování průchodu, po zpracování všech událostí. |

## <a name="remarks"></a>Poznámky

Všichni členové `RELOG_CALLBACKS` struktury musí ukazovat na platnou funkci. Další informace o podpisech přijatých funkcí naleznete v [tématech OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)a [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
