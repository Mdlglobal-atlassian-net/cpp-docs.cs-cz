---
title: Chyba kompilátoru C2555
description: Reference pro chybu kompilátoru visual studio C++ C2555.
ms.date: 03/30/2020
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: fe0e6379e783387506e6098c9b14a047baa8e6c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374177"
---
# <a name="compiler-error-c2555"></a>Chyba kompilátoru C2555

> '*class1*::*function1*': přepsání typu návratu virtuální funkce se liší a není kovariantní od '*class2*::*function2*'

Virtuální funkce a odvozené přepsání funkce mají identické seznamy parametrů, ale různé návratové typy.

## <a name="remarks"></a>Poznámky

V jazyce C++ se přepsání funkce v odvozené třídě nemůže lišit pouze podle návratového typu z virtuální funkce v základní třídě.

Existuje výjimka z tohoto pravidla pro určité typy vrácení. Když odvozená třída přepíše třídu veřejné základní, může vrátit ukazatel nebo odkaz na odvozenou třídu namísto ukazatele základní třídy nebo odkazu. Tyto návratové typy se nazývají *kovariantní*, protože se liší společně s typem. Tato výjimka pravidla neumožňuje kovariantní typy odkazů na ukazatel nebo ukazatel na ukazatel.

Jedním ze způsobů, jak chybu vyřešit, je vrátit stejný typ jako základní třída. Potom přetypování vrácená hodnota po virtuální funkce byla volána. Dalším je také změnit seznam parametrů, aby se odvozená funkce člena třídy přetížení namísto přepsání.

## <a name="examples"></a>Příklady

Tato chyba se může zobrazit, pokud kompilujete s **`/clr`**. Například C++ ekvivalentní následující deklaraci Jazyka C#:

```csharp
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```cpp
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Následující vzorek generuje C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```

Chcete-li jej opravit, `Y::func` změňte návratový typ na `void`.
