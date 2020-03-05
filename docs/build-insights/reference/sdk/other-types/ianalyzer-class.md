---
title: IAnalyzer – třída
description: Referenční C++ dokumentace třídy IAnalyzer sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- IAnalyzer
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 53f7b36695bb24d96ccfe88afbb56ff717c94dc9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332451"
---
# <a name="ianalyzer-class"></a>IAnalyzer – třída

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Třída `IAnalyzer` poskytuje rozhraní pro analýzu trasování událostí pro Windows (ETW). Používá se u funkcí [MakeDynamicAnalyzerGroup](../functions/make-dynamic-analyzer-group.md), [MakeDynamicReloggerGroup](../functions/make-dynamic-relogger-group.md), [MakeStaticAnalyzerGroup](../functions/make-dynamic-analyzer-group.md)a [MakeStaticReloggerGroup](../functions/make-static-analyzer-group.md) . Použijte `IAnalyzer` jako základní třídu k vytvoření vlastního analyzátoru, který může být součástí skupiny analyzátorů nebo přeprotokolovacích nástrojů.

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

Třídy, které jsou odvozeny od `IAnalyzer`, lze použít jako analyzátory i pro přeprotokolovací nástroje. Při použití jako reprotokolovacích nástrojů se funkce specifické pro přeprotokolovací nástroj přesměrují na jejich ekvivalent analyzátoru. Reverzní není true: třídu, která je odvozena z `IRelogger` nelze použít jako analyzátor. Použití analyzátoru ve skupině reprotokolovacích nástrojů je běžným vzorem. Při umístění do prvotní pozice skupiny přeprotokolovacích souborů může analyzátor předem vypočítat informace a zpřístupnit je pro opětovné protokolování v pozdějších pozicích.

Výchozí návratová hodnota pro všechny funkce, které nejsou přepsány, je `AnalysisControl::CONTINUE`. Další informace najdete v tématu [AnalysisControl](analysis-control-enum-class.md).

## <a name="members"></a>Členové

Kromě členu [OnTraceInfo](irelogger-class.md#on-trace-info) z rozhraní `IRelogger` obsahuje Třída `IAnalyzer` následující členy:

### <a name="destructor"></a>Destruktor

[~ IAnalyzer](#ianalyzer-destructor)

### <a name="functions"></a>Functions

[OnBeginAnalysis](#on-begin-analysis)\
[OnBeginAnalysisPass](#on-begin-analysis-pass)\
[OnBeginRelogging](#on-begin-relogging)\
[OnBeginReloggingPass](#on-begin-relogging-pass)\
[OnEndAnalysis](#on-end-analysis)\
[OnEndAnalysisPass](#on-end-analysis-pass)\
[OnEndRelogging](#on-end-relogging)\
[OnEndReloggingPass](#on-end-relogging-pass)\
[OnSimpleEvent](#on-simple-event)\
[OnStartActivity](#on-start-activity)\
[OnStopActivity](#on-stop-activity)

## <a name="ianalyzer-destructor"></a>~ IAnalyzer

Zničí třídu IAnalyzer.

```cpp
virtual ~IAnalyzer();
```

## <a name="on-begin-analysis"></a>OnBeginAnalysis

V případě analyzátorů, které jsou součástí skupiny analyzátorů, je tato funkce volána před zahájením prvního průchodu analýzy. Pro analyzátory součástí skupiny přeprotokolovacích souborů je tato funkce volána před zahájením opětovného protokolování. Pro analyzátory součást analyzátoru i skupiny přeprotokolovacích souborů stejné relace opětovného protokolování je tato funkce volána dvakrát před zahájením první analýzy.

```cpp
virtual AnalysisControl OnBeginAnalysis();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-begin-analysis-pass"></a>OnBeginAnalysisPass

V případě analyzátorů, které jsou součástí skupiny analyzátorů, je tato funkce volána na začátku každé analytické fáze. Pro analyzátory, které jsou součástí skupiny přeprotokolovacích souborů, je tato funkce volána na začátku průchodu reprotokolovacího nástroje. Pro analyzátory, které jsou součástí skupiny analyzátoru i přeprotokolovacího nástroje stejné relace opětovného protokolování, je tato funkce volána na začátku každé analytické fáze a na začátku průchodu opětovného protokolování.

```cpp
virtual AnalysisControl OnBeginAnalysisPass();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-begin-relogging"></a>OnBeginRelogging

```cpp
AnalysisControl OnBeginRelogging() final;
```

Tuto funkci nelze přepsat. Je volána sadou SDK pro C++ Build Insights, když je analyzátor součástí skupiny přeprotokolovacích souborů. Tato funkce přesměrovává volání na [OnBeginAnalysis](#on-begin-analysis).

### <a name="return-value"></a>Návratová hodnota

Výsledek volání [OnBeginAnalysis](#on-begin-analysis)

## <a name="on-begin-relogging-pass"></a>OnBeginReloggingPass

Tuto funkci nelze přepsat. Je volána sadou SDK pro C++ Build Insights, když je analyzátor součástí skupiny přeprotokolovacích souborů. Tato funkce přesměrovává volání na [OnBeginAnalysisPass](#on-begin-analysis-pass).

```cpp
AnalysisControl OnBeginReloggingPass() final;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek volání [OnBeginAnalysisPass](#on-begin-analysis-pass)

## <a name="on-end-analysis"></a>OnEndAnalysis

Pro analyzátory, které jsou součástí skupiny analyzátorů, je tato funkce volána po ukončení poslední fáze analýzy. Pro analyzátory, které jsou součástí skupiny přeprotokolovacího nástroje, je tato funkce volána po ukončení opětovného přihlášení. Pro analyzátory, které jsou součástí skupiny analyzátoru i přeprotokolovacího nástroje stejné relace opětovného protokolování, je tato funkce volána dvakrát:

1. po ukončení všech průchodů analýz a před zahájením znovu zalogování a
1. Po dokončení přehlašování bylo úspěšně dokončeno.

```cpp
virtual AnalysisControl OnEndAnalysis();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-end-analysis-pass"></a>OnEndAnalysisPass

Pro analyzátory, které jsou součástí skupiny analyzátorů, je tato funkce volána na konci každé analytické fáze. Pro analyzátory součástí skupiny přeprotokolovacích souborů je tato funkce volána na konci přeprotokolovacího nástroje. Pro analyzátory, které jsou součástí skupiny analyzátoru i přeprotokolovacího nástroje stejné relace opětovného protokolování, je tato funkce volána na konci každé analýzy průchodu a na konci přeběhu znovu protokolovacího nástroje.

```cpp
virtual AnalysisControl OnEndAnalysisPass();
```

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-end-relogging"></a>OnEndRelogging

Tuto funkci nelze přepsat. Je volána sadou SDK pro C++ Build Insights, když je analyzátor součástí skupiny přeprotokolovacích souborů. Tato funkce přesměrovává volání na [OnEndAnalysis](#on-end-analysis).

```cpp
AnalysisControl OnEndRelogging() final;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek volání [OnEndAnalysis](#on-end-analysis)

## <a name="on-end-relogging-pass"></a>OnEndReloggingPass

Tuto funkci nelze přepsat. Je volána sadou SDK pro C++ Build Insights, když je analyzátor součástí skupiny přeprotokolovacích souborů. Tato funkce přesměrovává volání na [OnEndAnalysisPass](#on-end-analysis-pass).

```cpp
AnalysisControl OnEndReloggingPass() final;
```

### <a name="return-value"></a>Návratová hodnota

Výsledek volání [OnEndAnalysisPass](#on-end-analysis-pass)

## <a name="on-simple-event"></a>OnSimpleEvent

Tato funkce se volá, když se zpracovává jednoduchá událost. Druhá verze této funkce se nedá přepsat. Je volána sadou SDK pro C++ Build Insights, když je analyzátor součástí skupiny přeprotokolovacích souborů. Všechna volání na verzi 2 jsou přesměrována na verzi 1.

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
Zásobník událostí pro tuto jednoduchou událost. Další informace o zásobníkech událostí najdete v tématu [události](../event-table.md).

*relogSession*\
Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-start-activity"></a>OnStartActivity

Tato funkce se volá, když se zpracovává událost zahájení aktivity. Druhá verze této funkce se nedá přepsat. Je volána sadou SDK pro C++ Build Insights, když je analyzátor součástí skupiny přeprotokolovacích souborů. Všechna volání na verzi 2 jsou přesměrována na verzi 1.

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
Zásobník událostí pro událost spuštění této aktivity. Další informace o zásobníkech událostí najdete v tématu [události](../event-table.md).

*relogSession*\
Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

## <a name="on-stop-activity"></a>OnStopActivity

Tato funkce se volá, když se zpracovává událost zastavení aktivity. Druhá verze této funkce se nedá přepsat. Je volána sadou SDK pro C++ Build Insights, když je analyzátor součástí skupiny přeprotokolovacích souborů. Všechna volání na verzi 2 jsou přesměrována na verzi 1.

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
Zásobník událostí pro tuto událost zastavení aktivity Další informace o zásobníkech událostí najdete v tématu [události](../event-table.md).

*relogSession*\
Tento parametr se nepoužívá.

### <a name="return-value"></a>Návratová hodnota

[AnalysisControl](analysis-control-enum-class.md) kód, který popisuje, co by mělo proběhnout příště.

::: moniker-end
