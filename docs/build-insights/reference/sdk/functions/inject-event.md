---
title: InjectEvent
description: Reference C++ k funkci InjectEvent sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332843"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `InjectEvent` je volána v rámci přeprotokolovacího nástroje implementující rozhraní [IRelogger](../other-types/irelogger-class.md) . Používá se k zápisu událostí trasování událostí pro Windows (ETW) ve výstupním trasovacím souboru pro relaci přehlašování.

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

*relogSession*\
Ukazatel na relaci přeprotokolování. K dispozici je znovu protokolovací relace, která implementuje rozhraní `IRelogger`. Další informace najdete v tématu [IRelogger](../other-types/irelogger-class.md).

\ *providerId*
Identifikátor GUID zprostředkovatele trasování událostí pro Windows (ETW), pod kterým se událost ETW znovu zaznamená.

*eventDescriptor*\
Popisovač události ETW pro událost trasování událostí pro Windows, která je přeprotokolována.

*id_procesu*\
Identifikátor procesu (PID) pro událost trasování událostí pro Windows, která je přeprotokolována.

*idvlákna*\
Identifikátor vlákna (TID) pro událost trasování událostí pro Windows, která je přeprotokolována.

*processorIndex*\
Index procesoru pro událost trasování událostí pro Windows, která je přeprotokolována.

\ *časového razítka*
Časové razítko události ETW, která je přeprotokolována.

\ *dat*
Ukazatel na data, která by měla být obsažena v přeprotokolovaných událostech ETW.

*byteCount*\
Velikost dat v bajtech odkazujících na *data*.

## <a name="remarks"></a>Poznámky

Další informace o konceptech ETW, například *identifikátor GUID zprostředkovatele* a *popisovači událostí*, najdete v [dokumentaci ETW](/windows/win32/etw/about-event-tracing). Podrobnosti o tom, jak zahájit relaci C++ opětovného protokolování se sadou SDK pro Build Insights, najdete v tématu [relog](relog.md).

::: moniker-end
