---
title: Chyba kompilátoru C2355
ms.date: 11/04/2016
f1_keywords:
- C2355
helpviewer_keywords:
- C2355
ms.assetid: 0a947881-d61f-4f98-8409-32140f39500b
ms.openlocfilehash: e44501f7df05a8b277cd52107ff35c4c4d30578f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759942"
---
# <a name="compiler-error-c2355"></a>Chyba kompilátoru C2355

' this ': lze odkazovat pouze uvnitř nestatických členských funkcí nebo inicializátorů nestatických datových členů.

Ukazatel `this` je platný pouze v rámci nestatických členských funkcí nebo v inicializátorech nestatických datových členů. Tato chyba může být způsobena tím, že není správně kvalifikován obor třídy definice členské funkce mimo deklaraci třídy. K chybě může dojít také v případě, že se `this` ukazatel používá ve funkci, která není deklarována ve třídě.

Chcete-li tento problém vyřešit, ujistěte se, že definice členské funkce odpovídá deklaraci členské funkce ve třídě a že není deklarována jako statická. Pro Inicializátory datových členů se ujistěte, že datový člen není deklarován jako static.

Následující ukázka generuje C2355 a ukazuje, jak ji opravit:

```cpp
// C2355.cpp
// compile with: /c
class MyClass {};
MyClass *p = this;   // C2355

// OK
class MyClass2 {
public:
   void Test() {
      MyClass2 *p = this;
   }
};
```
