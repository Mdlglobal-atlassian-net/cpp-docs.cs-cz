---
title: Chyba kompilátoru C2179
ms.date: 11/04/2016
f1_keywords:
- C2179
helpviewer_keywords:
- C2179
ms.assetid: f929bfc6-3964-4e54-87d6-7529b9b6c0b9
ms.openlocfilehash: 5b9b5382ab934f8d870e58189a447775a1e9a415
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737163"
---
# <a name="compiler-error-c2179"></a>Chyba kompilátoru C2179

' type ': argument atributu nemůže používat parametry typu

Parametr obecného typu se vyřeší za běhu. Nicméně parametr atributu musí být vyřešen v době kompilace. Proto nemůžete použít parametr obecného typu jako argument pro atribut.

## <a name="example"></a>Příklad

Následující ukázka generuje C2179.

```cpp
// C2179.cpp
// compile with: /clr
using namespace System;

public ref struct Attr : Attribute {
   Attr(Type ^ a) {
      x = a;
   }

   Type ^ x;
};

ref struct G {};

generic<typename T>
public ref class Z {
public:
   Type ^ d;
   [Attr(T::typeid)]   // C2179
   // try the following line instead
   // [Attr(G::typeid)]
   T t;
};
```
