---
title: Chyba kompilátoru C2969
ms.date: 11/04/2016
f1_keywords:
- C2969
helpviewer_keywords:
- C2969
ms.assetid: e4ea3d66-b937-4b2c-b42a-96e03fb11579
ms.openlocfilehash: 045ba4930e985d90f755ac44d482a55f04a3e6a3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759435"
---
# <a name="compiler-error-c2969"></a>Chyba kompilátoru C2969

Chyba syntaxe: symbol: očekávaná definice členské funkce má končit znakem '} '.

Definice členské funkce šablony má neshodnou uzavírací složenou závorku.

Následující ukázka generuje C2969:

```cpp
// C2969.cpp
// compile with: /c
class A {
   int i;
public:
   A(int i) {}
};

A anA(1);

class B {
   A a;
   B() : a(anA);   // C2969
   // try the following line instead
   // B() : a(anA) {}
};
```
