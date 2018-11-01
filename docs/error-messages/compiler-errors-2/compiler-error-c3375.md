---
title: Chyba kompilátoru C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: b3dfc17f9df495fe6907b816bace0dac1eff08cc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545272"
---
# <a name="compiler-error-c3375"></a>Chyba kompilátoru C3375

'function': nejednoznačná funkce delegate

Vytvoření instance delegáta mohlo být statickou členskou funkci nebo jako delegáta bez vazby na instance funkce, proto kompilátor vydané k této chybě.

Další informace najdete v tématu [delegate (rozšíření komponent C++)](../../windows/delegate-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3375.

```
// C3375.cpp
// compile with: /clr
ref struct R {
   static void f(R^) {}
   void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::f);   // C3375
}
```