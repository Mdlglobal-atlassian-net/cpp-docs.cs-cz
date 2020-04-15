---
title: Stack matchevent
description: C++ Build Insights SDK MatchEventStack odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a223d420e8c48667fbd1c6569f02d0486f597b5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323876"
---
# <a name="matcheventstack"></a>Stack matchevent

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEventStack` se používá k porovnání zásobníku událostí s konkrétní hierarchií událostí. Odpovídající hierarchie jsou předány obslužné rutině pro další zpracování. Další informace o událostech, hromádkách událostí a hierarchiích najdete v [tabulce událostí](../event-table.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>Parametry

*Událost*\
Typ nejstarší ho rodiče, který se má shodovat v zásobníku událostí.

*Události*\
Zbývající typy, které chcete porovnat v zásobníku událostí.

*Tcallable*\
Typ, který `operator()`podporuje . Další informace o tom, které argumenty jsou tomuto operátoru předány, naleznete v popisu *volna.*

*TExtraArgs*\
Typy další argumenty předány `MatchEventStack`.

*eventStack*\
Zásobník událostí odpovídá hierarchii typu události popsané *tevent* a *tevents*.

*Callable*\
Po úspěšném porovnání zásobníku událostí s hierarchií typu události `MatchEventStack` popsanou *společnostmi TEvent* a *TEvents*vyvolá *vyvolatelný*soubor . Přejde na *volatelný* jeden argument r-hodnota pro každý typ v hierarchii událostí. Balíček parametrů *extraArgs* je ve zbývajících parametrech *callable*perfektně předán .

*extraArgs*\
Argumenty, které získat perfektní-přepojit *na volatelné* spolu s odpovídající typ události.

### <a name="return-value"></a>Návratová hodnota

**Bool** hodnota, která je **true,** pokud odpovídající byl úspěšný, nebo **false** jinak.

## <a name="remarks"></a>Poznámky

Poslední událost v *eventStack* je vždy porovnána s poslední \[položkou v zřetězené *TEvent*, *TEvents...* \] seznamu typů. Všechny ostatní *položky TEvent* a *TEvents* mohou odpovídat libovolné pozici v *eventStack* s výjimkou poslední, za předpokladu, že jsou ve stejném pořadí.

Typy událostí, které se mají použít pro parametry *TEvent* a *TEvents,* jsou vybrány ze seznamu *tříd zachycení*. Seznam událostí a tříd zachycení, které můžete použít k jejich sladění, naleznete v [tabulce událostí](../event-table.md).

## <a name="example"></a>Příklad

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
