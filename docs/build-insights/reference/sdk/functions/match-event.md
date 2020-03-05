---
title: MatchEvent
description: Reference C++ k funkci MatchEvent sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f8022953e2f56f7c8917f161b094c50e0c5ecbdf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332773"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEvent` slouží k porovnání události se seznamem typů událostí. Pokud událost odpovídá typu v seznamu, je předána obslužné rutině pro další zpracování.

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

*TEvent*\
První typ události, který chcete porovnat.

*TEvents*\
Zbývající typy událostí, které si přejete porovnat.

*TCallable*\
Typ, který podporuje `operator()`. Další informace o tom, které argumenty jsou předány tomuto operátorovi, *naleznete v popisu parametru s* parametrem.

*TExtraArgs*\
Typy dalších argumentů, které byly předány `MatchEvent`.

\ *události*
Událost, která se má shodovat s typy událostí popsanými v *TEvent* a *TEvents*.

*volat*\
`MatchEvent` vyvolá volání metody *Invoke po* úspěšném porovnání události s jakýmkoli typem události popsaným v *TEvent* a *TEvents*. První argument předaný metodě *pro vyžádání* je hodnota r, která odpovídá typu události. Sada parametrů *extraArgs* je ve zbývajících parametrech *pro vyžádání dokonalé.*  

*extraArgs*\
Argumenty, které získají *dokonalý a předávané k vyžádání* , spolu s odpovídajícím typem události.

### <a name="return-value"></a>Návratová hodnota

**Logická** hodnota **true** , pokud bylo spárování úspěšné, nebo jinak **false** .

## <a name="remarks"></a>Poznámky

Typy událostí, které se mají použít pro parametry *TEvent* a *TEvents* , se vyberou ze seznamu *tříd zachycení*. Seznam událostí a třídy zachycení, které můžete použít k přiřazení, najdete v tématu [tabulka událostí](../event-table.md).

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
