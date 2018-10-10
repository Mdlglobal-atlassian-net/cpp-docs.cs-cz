---
title: Chyba kompilátoru C2555 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2555
dev_langs:
- C++
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0cd401aa1ee3611befb39d630f48f6aed36211c
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48889943"
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