---
title: MatcheventInMemberFunction
description: C++ Build Insights SDK MatchEventInMemberFunction odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 522630da16e3f4a1294316d88140f4bc25dca2c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323903"
---
# <a name="matcheventinmemberfunction"></a>MatcheventInMemberFunction

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEventInMemberFunction` se používá k porovnání události s typem popsaným prvním parametrem členské funkce. Odpovídající událost je předána členské funkci k dalšímu zpracování.

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>Parametry

*Rozhraní T*\
Typ, který obsahuje členská funkce.

*TNávrat*\
Návratový typ členské funkce.

*Událost*\
Typ události, která má odpovídat.

*TExtraParams*\
Typy dalšíparametry přijaté členské funkce spolu s typem události tak, aby odpovídaly.

*TExtraArgs*\
Typy další argumenty, které byly `MatchEventInMemberFunction`předány .

*Událost*\
Událost, která se shoduje s typem události popsaným *tevent*.

*objectPtr*\
Ukazatel na objekt, na kterém *memberFunc* získá volání.

*členFunc*\
Členská funkce, která popisuje typ události tak, aby odpovídal.

*extraArgs*\
Argumenty, které získat perfektní *předány memberFunc* spolu s parametrem typu události.

### <a name="return-value"></a>Návratová hodnota

**Bool** hodnota, která je **true,** pokud odpovídající byl úspěšný, nebo **false** jinak.

## <a name="remarks"></a>Poznámky

Typ události, který se má použít pro parametr *TEvent,* lze vybrat ze seznamu *tříd zachycení*. Seznam událostí a tříd zachycení, které můžete použít k jejich sladění, naleznete v [tabulce událostí](../event-table.md).

## <a name="example"></a>Příklad

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
