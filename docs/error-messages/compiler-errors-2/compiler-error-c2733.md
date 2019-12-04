---
title: Chyba kompilátoru C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 3ef669a49f4a3ec5a1af1a15a79f2511fa2699dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755782"
---
# <a name="compiler-error-c2733"></a>Chyba kompilátoru C2733

druhé propojení jazyka C přetížené funkce Function není povolené.

Více než jedna přetížená funkce je deklarována s propojením jazyka C. Při použití propojení jazyka C může být pouze jedna forma zadané funkce external. Vzhledem k tomu, že přetížené funkce mají stejný nedekorovaný název, nelze je použít s programy jazyka C.

Následující ukázka generuje C2733:

```cpp
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```
