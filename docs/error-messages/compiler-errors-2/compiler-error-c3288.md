---
title: Chyba kompilátoru C3288
ms.date: 11/04/2016
f1_keywords:
- C3288
helpviewer_keywords:
- C3288
ms.assetid: ed08a540-9751-46e1-9cbe-c51d6a49ffab
ms.openlocfilehash: a7b87fdbd2e15906ebc0c669f0b9a74ebf97f0b3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760176"
---
# <a name="compiler-error-c3288"></a>Chyba kompilátoru C3288

' type ': neplatný odkaz na typ popisovače

Kompilátor zjistil neplatnou zpětnou referenci typu popisovače. Můžete odkázat na typ popisovače a přiřadit ho k odkazu. Další informace naleznete v tématu [operátor sledování odkazů](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3288.

```cpp
// C3288.cpp
// compile with: /clr
ref class R {};
int main() {
   *(System::Object^) nullptr;   // C3288

// OK
   (System::Object^) nullptr;   // OK
   R^ r;
   R% pr = *r;
}
```
