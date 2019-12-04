---
title: Chyba kompilátoru C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 6b6f08ac52eff355f0857968817a681818e3c3dc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756770"
---
# <a name="compiler-error-c2556"></a>Chyba kompilátoru C2556

' identifier ': přetížené funkce se liší pouze v návratovém typu

Přetížené funkce mají rozdílné návratové typy, ale stejný seznam parametrů. Každá přetížená funkce musí mít samostatný seznam formálních parametrů.

Následující ukázka generuje C2556:

```cpp
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```
