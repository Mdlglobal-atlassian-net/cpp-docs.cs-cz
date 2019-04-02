---
title: Kompilátor upozornění (úroveň 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: 2e93fdeba7f9b5b10340ccd1920807a3fcb345a0
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58771055"
---
# <a name="compiler-warning-level-1-c4965"></a>Kompilátor upozornění (úroveň 1) C4965

implicitní pole celé číslo 0; Použijte nullptr nebo explicitní přetypování.

Visual C++ poskytuje implicitní zabalení typů hodnot. Instrukce, jejímž výsledkem bylo null přiřazení pomocí Správce rozšíření pro C++ teď bude přiřazení na zabalený int

Další informace najdete v tématu [zabalení](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4965.

```
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```