---
title: Událost matchevent
description: C++ Build Insights SDK MatchEvent odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0c60653641c676716bcdd60865433773da79325f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323858"
---
# <a name="matchevent"></a>Událost matchevent

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEvent` se používá k porovnání události se seznamem typů událostí. Pokud událost odpovídá typu v seznamu, je předána obslužné rutině k dalšímu zpracování.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>Parametry

*Událost*\
První typ události, který chcete porovnat.

*Události*\
Zbývající typy událostí, které chcete porovnat.

*Tcallable*\
Typ, který `operator()`podporuje . Další informace o tom, které argumenty jsou tomuto operátoru předány, naleznete v popisu *volna.*

*TExtraArgs*\
Typy další argumenty, které byly `MatchEvent`předány .

*Událost*\
Událost, která se bude shodovat s typy událostí popsanými *teventa* a *TEvents*.

*Callable*\
`MatchEvent`vyvolá *volatelné* po úspěšném porovnání události s libovolným typem události popsaným *tevent* a *tevents*. První argument předaný *volatelné* je hodnota r odpovídající typ události. Balíček parametrů *extraArgs* je ve zbývajících parametrech *callable*perfektně předán .  

*extraArgs*\
Argumenty, které získat perfektní-přepojit *na volatelné* spolu s odpovídající typ události.

### <a name="return-value"></a>Návratová hodnota

**Bool** hodnota, která je **true,** pokud odpovídající byl úspěšný, nebo **false** jinak.

## <a name="remarks"></a>Poznámky

Typy událostí, které se mají použít pro parametry *TEvent* a *TEvents,* jsou vybrány ze seznamu *tříd zachycení*. Seznam událostí a tříd zachycení, které můžete použít k jejich sladění, naleznete v [tabulce událostí](../event-table.md).

## <a name="example"></a>Příklad

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
