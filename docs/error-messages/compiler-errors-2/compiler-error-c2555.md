---
title: Chyba kompilátoru C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: cc6c3a3a29665ccf65b77a3d9866986cb0a46b9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353196"
---
# <a name="compiler-error-c2555"></a>Chyba kompilátoru C2555

'class1::function1': přepisující virtuální funkce návratový typ se liší a není kovariantem z: "class2::function2.

Virtuální funkce a odvozené přepisující funkce mají stejné parametr seznamy ale různé typy vrácené hodnoty. Přepsání funkce v odvozené třídě se nemůže lišit od virtuální funkce v základní třídě pouze podle jejího návratového typu.

Chcete-li vyřešit tuto chybu, přetypujte návratovou hodnotu po volání virtuální funkce.

Tato chyba může také zobrazit, pokud kompilujete s možnostmi/CLR.   Například Visual C++ ekvivalentní následující deklarace jazyka C#:

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