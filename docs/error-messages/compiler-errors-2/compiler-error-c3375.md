---
title: Chyba kompilátoru C3375
ms.date: 11/04/2016
f1_keywords:
- C3375
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
ms.openlocfilehash: ba1dbf08fb56364d2ab5b8c40847ab89484dc005
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781390"
---
# <a name="compiler-error-c3375"></a>Chyba kompilátoru C3375

'function': nejednoznačná funkce delegate

Vytvoření instance delegáta mohlo být statickou členskou funkci nebo jako delegáta bez vazby na instance funkce, proto kompilátor vydané k této chybě.

Další informace najdete v tématu [delegate (rozšíření komponent C++)](../../extensions/delegate-cpp-component-extensions.md).

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