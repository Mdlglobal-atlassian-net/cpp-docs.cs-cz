---
title: Chyba kompilátoru C3656
ms.date: 11/04/2016
f1_keywords:
- C3656
helpviewer_keywords:
- C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
ms.openlocfilehash: 312fc4311120819fe6621d03e5ab6f7cab13cac9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758278"
---
# <a name="compiler-error-c3656"></a>Chyba kompilátoru C3656

override: specifikátor override se nemůže opakovat.

Explicitní klíčové slovo override lze zadat pouze jednou. Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

Následující ukázka generuje C3656:

```cpp
// C3656.cpp
// compile with: /clr /c
public interface struct O {
   int f();
};

public ref struct V : O {
   int f() override override { return 0; }   // C3656
   // try the following line instead
   // int f() override { return 0; }
};
```
