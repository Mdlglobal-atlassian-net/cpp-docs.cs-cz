---
title: MatchEventStackInMemberFunction
description: Reference C++ k funkci MatchEventStackInMemberFunction sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a966ea5209a25a62c08cb0873d0565299a15d27
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332787"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEventStackInMemberFunction` se používá ke spárování zásobníku událostí proti konkrétní hierarchii událostí, která je popsána v seznamu parametrů členské funkce. Odpovídající hierarchie jsou předávány členské funkci pro další zpracování. Další informace o událostech, zásobníkech událostí a hierarchiích najdete v tématu [tabulka událostí](../event-table.md).

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

*TInterface*\
Typ, který obsahuje členskou funkci.

*TReturn*\
Návratový typ členské funkce

*T1*,..., *T10*\
Typy popisující hierarchii události, které se mají porovnat.

*TExtraParams*\
Typy dodatečných parametrů přijímaných členskou funkcí a typy hierarchie událostí.

*TExtraArgs*\
Typy dalších argumentů, které byly předány `MatchEventStackInMemberFunction`.

*eventStack*\
Zásobník událostí, který se má shodovat s hierarchií typu události popsanou *T1* prostřednictvím *T10*.

*objectPtr*\
Ukazatel na objekt, na kterém je volána metoda *memberFunc* .

*memberFunc*\
Členská funkce, která popisuje hierarchii typu události, aby odpovídala.

*extraArgs*\
Argumenty, které se dodávají dokonalému přeposílány na *memberFunc* spolu s parametry hierarchie typu události.

### <a name="return-value"></a>Návratová hodnota

Hodnota **bool** , která má **hodnotu true** , pokud bylo spárování úspěšné, nebo v opačném případě **false** .

## <a name="remarks"></a>Poznámky

Poslední událost v *eventStack* se vždycky spáruje s poslední položkou v hierarchii typu události, aby se shodovala. Všechny ostatní typy v hierarchii typu události se můžou shodovat s libovolným umístěním v *eventStack* s výjimkou posledního, pokud se nachází ve stejném pořadí.

Typy událostí, které se mají použít pro parametry *T1* až *T10* , se vyberou ze seznamu *tříd zachycení*. Seznam událostí a třídy zachycení, které můžete použít k přiřazení, najdete v tématu [tabulka událostí](../event-table.md).

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
