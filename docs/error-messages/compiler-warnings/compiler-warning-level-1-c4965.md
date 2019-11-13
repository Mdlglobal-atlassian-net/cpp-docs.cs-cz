---
title: Upozornění kompilátoru (úroveň 1) C4965
ms.date: 11/04/2016
f1_keywords:
- C4965
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
ms.openlocfilehash: ac1ffc1626a8b72fd7c9026afb6c6a54bace3750
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052237"
---
# <a name="compiler-warning-level-1-c4965"></a>Upozornění kompilátoru (úroveň 1) C4965

implicitní pole typu Integer 0; použít nullptr nebo explicitní přetypování

Vizuální C++ funkce implicitní zabalení hodnotových typů. Instrukce, která vedla k přiřazení null pomocí spravovaných rozšíření, se C++ teď staly přiřazením do zabaleného int.

Další informace naleznete v tématu [zabalení](../../extensions/boxing-cpp-component-extensions.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4965.

```cpp
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