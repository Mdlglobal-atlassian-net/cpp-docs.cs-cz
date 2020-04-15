---
title: InjectEvent
description: C++ Build Insights SDK injectEvent odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c82aad5923eff60e5c72ceccaa39aa136f942665
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324042"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `InjectEvent` je volána v rámci relogger uprovádění [rozhraní IRelogger.](../other-types/irelogger-class.md) Používá se k zápisu události trasování událostí pro Windows (ETW) ve výstupním souboru trasování relace opětovného přihlášení.

## <a name="syntax"></a>Syntaxe

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>Parametry

*relogsession*\
Ukazatel na relaci opětovného přihlášení. Reloggery, které implementují `IRelogger` rozhraní, je k dispozici relogging. Další informace naleznete v tématu [IRelogger](../other-types/irelogger-class.md).

*providerId*\
Identifikátor GUID zprostředkovatele trasování událostí pro Windows (ETW), pod kterým se událost ETW znovu zahltí.

*událostDeskriptor*\
Popisovač události ETW pro událost ETW, která je relogged.

*Processid*\
Identifikátor procesu (PID) pro událost ETW, která je relogged.

*threadId*\
Identifikátor vlákna (TID) pro událost ETW, která je relogged.

*procesorIndex*\
Index procesoru pro událost ETW, která je relogged.

*Časové razítko*\
Časové razítko pro událost ETW, která je relogged.

*Dat*\
Ukazatel na data, která by měla být zahrnuta do události relogged ETW.

*Bytecount*\
Velikost dat v bajtech, na *která*se data zmizují .

## <a name="remarks"></a>Poznámky

Další informace o konceptech ETW, jako je například *identifikátor GUID zprostředkovatele* a *popisovač událostí*, naleznete v [dokumentaci k ETW](/windows/win32/etw/about-event-tracing). Podrobnosti o tom, jak spustit relaci opětovného sloggingu pomocí sady C++ Build Insights SDK, naleznete v [tématu Relog](relog.md).

::: moniker-end
