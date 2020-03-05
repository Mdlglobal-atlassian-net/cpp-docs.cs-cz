---
title: Struktura RELOG_CALLBACKS
description: Odkaz C++ na strukturu RELOG_CALLBACKS Build Insights SDK
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332339"
---
# <a name="relog_callbacks-structure"></a>Struktura RELOG_CALLBACKS

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Struktura `RELOG_CALLBACKS` se používá při inicializaci objektu [RELOG_DESCRIPTOR](relog-descriptor-struct.md) . Určuje funkce, které mají být volány během přeprotokolování trasování událostí pro Windows (ETW).

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
| `OnStartActivity` | Volá se, aby se zpracovala událost zahájení aktivity. |
| `OnStopActivity` | Volá se, aby se zpracovala událost zastavení aktivity. |
| `OnSimpleEvent` | Volá se, aby se zpracovala jednoduchá událost. |
| `OnTraceInfo` | Volá se jednou na začátku přehlašování po volání `OnBeginReloggingPass`. |
| `OnBeginRelogging` | Volá se při zahájení relace znovu protokolování, než se začne znovu přihlašovat. |
| `OnEndRelogging` | Volá se, když se ukončí relace znovu protokolování, až se úspěšně přehlásilo. |
| `OnBeginReloggingPass` | Volá se, když se před zpracováním jakékoli události znovu projde. |
| `OnEndReloggingPass` | Volá se, když se po zpracování všech událostí ukončí průchod znovu Logging. |

## <a name="remarks"></a>Poznámky

Všichni členové `RELOG_CALLBACKS` struktury musí ukazovat na platnou funkci. Další informace o přijatých podpisech funkcí naleznete v tématech [OnRelogEventFunc](on-relog-event-func-typedef.md), [OnTraceInfoFunc](on-trace-info-func-typedef.md)a [OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md).

::: moniker-end
