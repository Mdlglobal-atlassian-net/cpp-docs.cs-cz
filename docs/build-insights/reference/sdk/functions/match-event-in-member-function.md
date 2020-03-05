---
title: MatchEventInMemberFunction
description: Reference C++ k funkci MatchEventInMemberFunction sady SDK pro Build Insights
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eabbb8a91609b1447ebcc19af32df2ffed347c24
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2020
ms.locfileid: "78332801"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

Sada C++ SDK pro Build Insights je kompatibilní se sadou Visual Studio 2017 a novější. Chcete-li zobrazit dokumentaci pro tyto verze, nastavte ovládací prvek selektor verzí sady Visual Studio pro tento článek na sadu Visual Studio 2017 nebo Visual Studio 2019.

::: moniker-end
::: moniker range=">=vs-2017"

Funkce `MatchEventInMemberFunction` slouží k porovnání události s typem, který je popsán prvním parametrem členské funkce. Odpovídající událost je předána členské funkci pro další zpracování.

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

*TInterface*\
Typ, který obsahuje členskou funkci.

*TReturn*\
Návratový typ členské funkce

*TEvent*\
Typ události, která má být shodná.

*TExtraParams*\
Typy dodatečných parametrů přijaté členskou funkcí společně s typem události, který se má shodovat.

*TExtraArgs*\
Typy dalších argumentů, které byly předány `MatchEventInMemberFunction`.

\ *události*
Událost, která se má shodovat s typem události popsanou v *TEvent*.

*objectPtr*\
Ukazatel na objekt, na kterém se *memberFunc* volá.

*memberFunc*\
Členská funkce, která popisuje typ události, která se má shodovat.

*extraArgs*\
Argumenty, které získají dokonalé – předávané *memberFunc* spolu s parametrem typu události.

### <a name="return-value"></a>Návratová hodnota

Hodnota **bool** , která má **hodnotu true** , pokud bylo spárování úspěšné, nebo v opačném případě **false** .

## <a name="remarks"></a>Poznámky

Typ události, který se má použít pro parametr *TEvent* , můžete vybrat ze seznamu *tříd zachycení*. Seznam událostí a třídy zachycení, které můžete použít k přiřazení, najdete v tématu [tabulka událostí](../event-table.md).

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
