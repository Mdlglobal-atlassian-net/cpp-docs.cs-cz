---
title: MatchEventStackInMemberFunction
description: C++ Build Insights SDK MatchEventStackInMemberFunction odkaz na funkci.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 28842a02e7edc2e00266d8c7941798f4ce714ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323886"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

Sada C++ Build Insights SDK je kompatibilní s Visual Studio 2017 a vyšší. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek pro výběr **verze** sady Visual Studio pro tento článek na Visual Studio 2017 nebo Visual Studio 2019. Nachází se v horní části obsahu na této stránce.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEventStackInMemberFunction` se používá k porovnání zásobníku událostí s konkrétní hierarchií událostí, která je popsána seznamem parametrů členské funkce. Odpovídající hierarchie jsou předány členské funkci pro další zpracování. Další informace o událostech, hromádkách událostí a hierarchiích najdete v [tabulce událostí](../event-table.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>Parametry

*Rozhraní T*\
Typ, který obsahuje členská funkce.

*TNávrat*\
Návratový typ členské funkce.

*T1*, ..., *T10*\
Typy popisující hierarchii událostí tak, aby odpovídala.

*TExtraParams*\
Typy dalšíparametry přijaté členská funkce a typy hierarchie událostí.

*TExtraArgs*\
Typy další argumenty, které byly `MatchEventStackInMemberFunction`předány .

*eventStack*\
Zásobník událostí tak, aby odpovídal hierarchii typů událostí popsaných *T1* až *T10*.

*objectPtr*\
Ukazatel na objekt, na kterém *memberFunc* je volána.

*členFunc*\
Členská funkce, která popisuje hierarchii typu události tak, aby odpovídala.

*extraArgs*\
Argumenty, které získat perfektní *předány memberFunc* spolu s parametry hierarchie typu události.

### <a name="return-value"></a>Návratová hodnota

**Bool** hodnota, která je **true,** pokud odpovídající byl úspěšný, nebo **false** jinak.

## <a name="remarks"></a>Poznámky

Poslední událost v *eventStack* je vždy porovnána s poslední položkou v hierarchii typu události tak, aby odpovídala. Všechny ostatní typy v hierarchii typu události může odpovídat libovolné pozici v *eventStack* s výjimkou poslední, za předpokladu, že jsou ve stejném pořadí.

Typy událostí, které se mají použít pro parametry *T1* až *T10,* jsou vybrány ze seznamu *tříd zachycení*. Seznam událostí a tříd zachycení, které můžete použít k jejich sladění, naleznete v [tabulce událostí](../event-table.md).

## <a name="example"></a>Příklad

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
