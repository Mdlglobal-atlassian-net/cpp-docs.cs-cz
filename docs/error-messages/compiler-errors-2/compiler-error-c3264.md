---
title: Chyba kompilátoru C3264
ms.date: 11/04/2016
f1_keywords:
- C3264
helpviewer_keywords:
- C3264
ms.assetid: 94ece687-2364-4f7a-8ebb-7afd3ae9d63d
ms.openlocfilehash: b7645daf59aea97efaaffac83b751bbe29f1940b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754183"
---
# <a name="compiler-error-c3264"></a>Chyba kompilátoru C3264

Class: konstruktor třídy nemůže mít návratový typ.

Konstruktory třídy nemůžou mít návratové typy.

Následující ukázka generuje C3264:

```cpp
// C3264_2.cpp
// compile with: /clr

ref class X {
   public:
      static int X()   { // C3264
      }

      /* use the code below to resolve the error
      static X() {
      }
      */
};
int main() {
}
```
