---
title: Chyba kompilátoru C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ebf3e4a3aff48311edd5fb95b01a7b2d23990231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202421"
---
# <a name="compiler-error-c2555"></a>Chyba kompilátoru C2555

' Class1:: Function1 ': návratový typ přepisující virtuální funkce se liší a není kovariantou od ' Class2:: function2 '

Virtuální funkce a odvozená přepisovaná funkce mají stejné seznamy parametrů, ale jiné návratové typy. Přepisování funkce v odvozené třídě se nemůže lišit od virtuální funkce v základní třídě pouze pomocí jejího návratového typu.

Chcete-li tuto chybu vyřešit, přetypování návratové hodnoty poté, co byla volána virtuální funkce.

Tato chyba se může zobrazit i v případě, že kompilujete pomocí parametrem/CLR.   Například vizuální C++ ekvivalent k následující C# deklaraci:

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

Následující ukázka generuje C2555:

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
