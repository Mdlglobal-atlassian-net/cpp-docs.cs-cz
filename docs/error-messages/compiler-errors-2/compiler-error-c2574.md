---
title: Chyba kompilátoru C2574
ms.date: 11/04/2016
f1_keywords:
- C2574
helpviewer_keywords:
- C2574
ms.assetid: 3e1c5c18-ee8b-4dbb-bfc0-d3b8991af71b
ms.openlocfilehash: e0959d875065f7548706b07b032798a68bb4639b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755470"
---
# <a name="compiler-error-c2574"></a>Chyba kompilátoru C2574

destruktor: nejde deklarovat jako static.

Nelze deklarovat `static`ani destruktory ani konstruktory.

Následující ukázka generuje C2574:

```cpp
// C2574.cpp
// compile with: /c
class A {
   virtual static ~A();   // C2574
   //  try the following line instead
   // virtual ~A();
};
```
