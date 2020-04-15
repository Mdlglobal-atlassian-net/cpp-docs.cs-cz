---
title: Třída IRelogger
description: C++ Build Insights SDK IRelogger odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 146377b2b44df43ed4b2f749efd9fb614a2a09c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329144"
---
# <a name="irelogger-class"></a>Třída IRelogger

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `IRelogger` poskytuje rozhraní pro opětovné zaprotokolování trasování událostí pro Windows (ETW). Používá se s [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) a [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) funkce. Použijte `IRelogger` jako základní třídu k vytvoření vlastního reloggeru, který může být součástí skupiny relogger.

## <a name="syntax"></a>Syntaxe

```cpp
class IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession);

    virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
    virtual AnalysisControl OnBeginRelogging();
    virtual AnalysisControl OnEndRelogging();
    virtual AnalysisControl OnBeginReloggingPass();
    virtual AnalysisControl OnEndReloggingPass() ;

    virtual ~IRelogger();
};
```

## <a name="remarks"></a>Poznámky

Výchozí vrácená hodnota pro všechny funkce, `AnalysisControl::CONTINUE`které nejsou přepsány, je . Další informace naleznete v tématu [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Členové

### <a name="destructor"></a>Destruktor

[~IRelogger](#irelogger-destructor)

### <a name="functions"></a>Functions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[Událost OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OntraceInfo](#on-trace-info)

## <a name="irelogger"></a><a name="irelogger-destructor"></a>~IRelogger

Zničí třídu IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

Tato funkce je volána před zahájením opakování průchodu.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Tato funkce je volána na začátku průchodu opětovného přihlášení.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Tato funkce je volána po ukončení průchodu opětovného přihlášení.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Tato funkce je volána na konci průchodu opětovného přihlášení.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>Událost OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Tato funkce je volána při zpracování jednoduché události.

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto jednoduchou událost. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Tato funkce je volána při zpracování události zahájení aktivity.

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto událost zahájení aktivity. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity

Tato funkce je volána při zpracování události zastavení aktivity.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto událost zastavení aktivity. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="ontraceinfo"></a><a name="on-trace-info"></a>OntraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Tato funkce je volána jednou na začátku každé analýzy nebo opětovného přihlášení průchodu.

### <a name="parameters"></a>Parametry

*traceInfo*\
[TraceInfo](../cpp-event-data-types/trace-info.md) objekt, který obsahuje užitečné vlastnosti o trasování spotřebovává.

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

::: moniker-end
