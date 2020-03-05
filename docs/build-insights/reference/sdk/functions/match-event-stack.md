---
title: MatchEventStack
description: Reference C++ k funkci MatchEventStack sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 445c2d00c24da10754d32256de0c691e82b557e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332780"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEventStack` se používá pro porovnání zásobníku událostí s konkrétní hierarchií událostí. Odpovídající hierarchie jsou předávány obslužné rutině pro další zpracování. Další informace o událostech, zásobníkech událostí a hierarchiích najdete v tématu [tabulka událostí](../event-table.md).

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

*TEvent*\
Typ nadřazeného prvku Eldest, který se má shodovat s zásobníkem událostí.

*TEvents*\
Zbývající typy, které chcete v zásobníku událostí porovnat.

*TCallable*\
Typ, který podporuje `operator()`. Další informace o tom, které argumenty jsou předány tomuto operátorovi, *naleznete v popisu parametru s* parametrem.

*TExtraArgs*\
Typy dalších argumentů předaných `MatchEventStack`.

*eventStack*\
Zásobník událostí, který se má shodovat s hierarchií typu události popsanou v *TEvent* a *TEvents*.

*volat*\
Po úspěšném porovnání zásobníku událostí s hierarchií typu události popsanou v *TEvent* a *TEvents*`MatchEventStack` vyvolá volání metody *Invoke.* Předá k navýšení jednoho argumentu r-value pro každý typ v hierarchii událostí. Sada parametrů *extraArgs* je ve zbývajících parametrech *pro vyžádání dokonalé.*

*extraArgs*\
Argumenty, které získají *dokonalý a předávané k vyžádání* , spolu s odpovídajícím typem události.

### <a name="return-value"></a>Návratová hodnota

Hodnota **bool** , která má **hodnotu true** , pokud bylo spárování úspěšné, nebo v opačném případě **false** .

## <a name="remarks"></a>Poznámky

Poslední událost v *eventStack* se vždycky spáruje s poslední položkou v seznamu typů zřetězených \[*TEvent*, *TEvents...* \]. Všechny ostatní položky *TEvent* a *TEvents* se můžou shodovat s libovolnou pozicí v *eventStack* s výjimkou posledního, pokud jsou ve stejném pořadí.

Typy událostí, které se mají použít pro parametry *TEvent* a *TEvents* , se vyberou ze seznamu *tříd zachycení*. Seznam událostí a třídy zachycení, které můžete použít k přiřazení, najdete v tématu [tabulka událostí](../event-table.md).

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
