---
title: IRelogger – třída
description: Referenční C++ dokumentace třídy IRelogger sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IRelogger
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d0796cec3fe4ac6183279e8d8013a9550f18b61c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332444"
---
# <a name="irelogger-class"></a>IRelogger – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `IRelogger` poskytuje rozhraní pro zpětné protokolování trasování událostí pro Windows (ETW). Používá se s funkcemi [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md) a [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Použijte `IRelogger` jako základní třídu k vytvoření vlastního protokolovacího nástroje, který může být součástí skupiny přeprotokolovacích souborů.

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

Výchozí návratová hodnota pro všechny funkce, které nejsou přepsány, je `AnalysisControl::CONTINUE`. Další informace najdete v tématu [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Členové

### <a name="destructor"></a>Destruktor

[~ IRelogger](#irelogger-destructor)

### <a name="functions"></a>Functions

[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)\
[OnTraceInfo](#on-trace-info)

## <a name="irelogger-destructor"></a>~ IRelogger

Zničí třídu IRelogger.

```cpp
virtual ~IRelogger();
```

## <a name="on-begin-relogging"></a>OnBeginRelogging

Tato funkce je volána před zahájením přehlašování.

```cpp
virtual AnalysisControl OnBeginRelogging();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Tato funkce se volá na začátku přehlašování.

```cpp
virtual AnalysisControl OnBeginReloggingPass();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-end-relogging"></a>OnEndRelogging

Tato funkce se volá po skončení průchodu znovu Logging.

```cpp
virtual AnalysisControl OnEndRelogging();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

Tato funkce se volá na konci přelogování Pass.

```cpp
virtual AnalysisControl OnEndReloggingPass();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-simple-event"></a>OnSimpleEvent

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

Tato funkce se volá, když se zpracovává jednoduchá událost.

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto jednoduchou událost. Další informace o zásobníkech událostí najdete v tématu [události](../event-table.md).

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-start-activity"></a>OnStartActivity

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

Tato funkce se volá, když se zpracovává událost zahájení aktivity.

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro událost spuštění této aktivity. Další informace o zásobníkech událostí najdete v tématu [události](../event-table.md).

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-stop-activity"></a>OnStopActivity

Tato funkce se volá, když se zpracovává událost zastavení aktivity.

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto událost zastavení aktivity Další informace o zásobníkech událostí najdete v tématu [události](../event-table.md).

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-trace-info"></a>OnTraceInfo

```cpp
virtual AnalysisControl OnTraceInfo(const TraceInfo& traceInfo);
```

Tato funkce se volá jednou na začátku každé analýzy nebo průchodu znovu.

### <a name="parameters"></a>Parametry

*traceInfo*\
Objekt [TraceInfo](../cpp-event-data-types/trace-info.md) , který obsahuje užitečné vlastnosti pro spotřebované trasování.

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

::: moniker-end
