---
title: Chyba kompilátoru C3662
ms.date: 11/04/2016
f1_keywords:
- C3662
helpviewer_keywords:
- C3662
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
ms.openlocfilehash: 48fe8bd4a6872ff214d185ac77553debab78ab20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758187"
---
# <a name="compiler-error-c3662"></a>Chyba kompilátoru C3662

' member ': specifikátor override ' specifikátor ' je povolen pouze pro členské funkce spravované nebo třídy WinRT

Pro člena nativního typu se použil specifikátor přepisu, který není povolený.

Další informace najdete v tématu [Explicitní přepsání](../../extensions/explicit-overrides-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3662.

```cpp
// C3662.cpp
// compile with: /clr /c
struct S {
   virtual void f();
};

struct S1 : S {
   virtual void f() new;   // C3662
};

ref struct T {
   virtual void f();
};

ref struct T1 : T {
   virtual void f() new;   // OK
};
```
