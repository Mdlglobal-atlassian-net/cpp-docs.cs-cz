---
title: Třída IAnalyzer
description: C++ Build Insights SDK IAnalyzer odkaz na třídu.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: be9d80bb94450458c73fd6ce8d908985ba6f293d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329176"
---
# <a name="ianalyzer-class"></a>Třída IAnalyzer

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `IAnalyzer` poskytuje rozhraní pro analýzu trasování trasování událostí pro Windows (ETW). Používá se s funkcemi [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)a [MakeStaticReloggerGroup.](../functions/make-static-analyzer-group.md) Použijte `IAnalyzer` jako základní třídu k vytvoření vlastního analyzátoru, který může být součástí analyzátoru nebo skupiny reloggerů.

## <a name="syntax"></a>Syntaxe

```cpp
class IAnalyzer : public IRelogger
{
public:
    virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
    virtual AnalysisControl OnStopActivity(const EventStack& eventStack)
    virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
    virtual AnalysisControl OnBeginAnalysis();
    virtual AnalysisControl OnEndAnalysis();
    virtual AnalysisControl OnBeginAnalysisPass();
    virtual AnalysisControl OnEndAnalysisPass();

    AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;

    AnalysisControl OnBeginRelogging() final;
    AnalysisControl OnEndRelogging() final;
    AnalysisControl OnBeginReloggingPass() final;
    AnalysisControl OnEndReloggingPass() final;

    virtual ~IAnalyzer();
};
```

## <a name="remarks"></a>Poznámky

Třídy, `IAnalyzer` které jsou odvozeny z lze použít jako analyzátory a reloggery. Při použití jako reloggery, funkce specifické pro relogger přesměrovat na jejich ekvivalent analyzátoru. Opak není pravdou: třídu, která `IRelogger` je odvozena z nelze použít jako analyzátor. Použití analyzátoru ve skupině relogger je běžný vzor. Při umístění do rané pozice skupiny relogger, analyzátor může pre-vypočítat informace a zpřístupnit je pro reloggery v pozdějších pozicích.

Výchozí vrácená hodnota pro všechny funkce, `AnalysisControl::CONTINUE`které nejsou přepsány, je . Další informace naleznete v tématu [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Členové

Kromě [ontraceinfo](irelogger-class.md#on-trace-info) člen z `IRelogger` `IAnalyzer` rozhraní, třída obsahuje následující členy:

### <a name="destructor"></a>Destruktor

[~IAnalyzátor](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[Onendanalýza](#on-end-analysis)\
[OnendAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[Událost OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer"></a><a name="ianalyzer-destructor"></a>~IAnalyzátor

Zničí třídu IAnalyzer.

```cpp
virtual ~IAnalyzer();
```

## <a name="onbeginanalysis"></a><a name="on-begin-analysis"></a>OnBeginAnalysis

Pro analyzátory, které jsou součástí skupiny analyzátorů, je tato funkce volána před zahájením prvního průchodu analýzy. Pro analyzátory část relogger skupiny, tato funkce je volána před zahájením relogging pass. Pro analyzátory část analyzátoru a relogger skupiny stejné relace opětovného přihlášení, tato funkce je volána dvakrát před zahájením první analýzy průchodu.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onbeginanalysispass"></a><a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

Pro analyzátory, které jsou součástí skupiny analyzátorů, je tato funkce volána na začátku každého průchodu analýzy. Pro analyzátory součástí skupiny relogger, tato funkce se nazývá na začátku průchodu relogger. Pro analyzátory část analyzátoru a relogger skupiny stejné relace relogging, tato funkce se nazývá na začátku každé analýzy průchodu, a na začátku relogger projít.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onbeginrelogging"></a><a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Tuto funkci nelze přepsat. Je volána c++ sestavení insights SDK při analyzátor je součástí skupiny relogger. Tato funkce přesměruje volání [na OnBeginAnalysis](#on-begin-analysis).

### <a name="return-value"></a>Návratová hodnota

Výsledek [OnBeginAnalysis](#on-begin-analysis) volání.

## <a name="onbeginreloggingpass"></a><a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Tuto funkci nelze přepsat. Je volána c++ sestavení insights SDK při analyzátor je součástí skupiny relogger. Tato funkce přesměruje volání [OnBeginAnalysisPass](#on-begin-analysis-pass).

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek [onbeginAnalysisPass](#on-begin-analysis-pass) volání.

## <a name="onendanalysis"></a><a name="on-end-analysis"></a>Onendanalýza

Pro analyzátory, které jsou součástí skupiny analyzátoru, je tato funkce volána po ukončení posledního průchodu analýzy. Pro analyzátory, které jsou součástí skupiny relogger, tato funkce je volána po ukončení opětovného přihlášení průchodu. Pro analyzátory, které jsou součástí analyzátoru a relogger skupiny stejné relace opětovného přihlášení, tato funkce se nazývá dvakrát:

1. po ukončení všech analytických průchodů a před zahájením opakování a
1. po ukončení průchodu pro opětovné přihlášení.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onendanalysispass"></a><a name="on-end-analysis-pass"></a>OnendAnalysisPass

Pro analyzátory, které jsou součástí skupiny analyzátorů, je tato funkce volána na konci každého průchodu analýzy. Pro analyzátory součástí skupiny relogger, tato funkce je volána na konci průchodu relogger. Pro analyzátory část analyzátoru a relogger skupiny stejné relace relogging, tato funkce se nazývá na konci každé analýzy průchodu a na konci průchodu relogger.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onendrelogging"></a><a name="on-end-relogging"></a>OnEndRelogging

Tuto funkci nelze přepsat. Je volána c++ sestavení insights SDK při analyzátor je součástí skupiny relogger. Tato funkce přesměruje volání [na OnEndAnalysis](#on-end-analysis).

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek [OnEndAnalysis](#on-end-analysis) volání.

## <a name="onendreloggingpass"></a><a name="on-end-relogging-pass"></a>OnEndReloggingPass

Tuto funkci nelze přepsat. Je volána c++ sestavení insights SDK při analyzátor je součástí skupiny relogger. Tato funkce přesměruje volání [na OnEndAnalysisPass](#on-end-analysis-pass).

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek [onendanalysispass](#on-end-analysis-pass) volání.

## <a name="onsimpleevent"></a><a name="on-simple-event"></a>Událost OnSimpleEvent

Tato funkce je volána při zpracování jednoduché události. Druhou verzi této funkce nelze přepsat. Je volána c++ sestavení insights SDK při analyzátor je součástí skupiny relogger. Všechna volání na verzi 2 jsou přesměrována na verzi 1.

### <a name="version-1"></a>Verze 1

```cpp
virtual AnalysisControl OnSimpleEvent(const EventStack& eventStack);
```

### <a name="version-2"></a>Verze 2

```cpp
AnalysisControl OnSimpleEvent(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto jednoduchou událost. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

*relogsession*\
Tento parametr není použit.

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onstartactivity"></a><a name="on-start-activity"></a>OnStartActivity

Tato funkce je volána při zpracování události zahájení aktivity. Druhou verzi této funkce nelze přepsat. Je volána c++ sestavení insights SDK při analyzátor je součástí skupiny relogger. Všechna volání na verzi 2 jsou přesměrována na verzi 1.

### <a name="version-1"></a>Verze 1

```cpp
virtual AnalysisControl OnStartActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Verze 2

```cpp
AnalysisControl OnStartActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto událost zahájení aktivity. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

*relogsession*\
Tento parametr není použit.

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

## <a name="onstopactivity"></a><a name="on-stop-activity"></a>OnStopActivity

Tato funkce je volána při zpracování události zastavení aktivity. Druhou verzi této funkce nelze přepsat. Je volána c++ sestavení insights SDK při analyzátor je součástí skupiny relogger. Všechna volání na verzi 2 jsou přesměrována na verzi 1.

### <a name="version-1"></a>Verze 1

```cpp
virtual AnalysisControl OnStopActivity(const EventStack& eventStack);
```

### <a name="version-2"></a>Verze 2

```cpp
AnalysisControl OnStopActivity(const EventStack& eventStack,
        const void* relogSession) final;
```

### <a name="parameters"></a>Parametry

*eventStack*\
Zásobník událostí pro tuto událost zastavení aktivity. Další informace o hromádkách událostí naleznete v [tématu Události](../event-table.md).

*relogsession*\
Tento parametr není použit.

### <a name="return-value"></a>Návratová hodnota

Kód [AnalysisControl,](analysis-control-enum-class.md) který popisuje, co by se mělo stát dál.

::: moniker-end
