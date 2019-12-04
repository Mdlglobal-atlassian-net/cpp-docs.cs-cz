---
title: Chyba kompilátoru C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: ac9efa88fc4ab17a656172c44de2e49e82108108
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755665"
---
# <a name="compiler-error-c2728"></a>Chyba kompilátoru C2728

' type ': nativní pole nemůže obsahovat tento typ

Syntaxe vytvoření pole se použila k vytvoření pole spravovaných objektů nebo objektů WinRT. Nemůžete vytvořit pole spravovaných objektů nebo objektů WinRT pomocí syntaxe nativního pole.

Další informace naleznete v tématu [Array](../../extensions/arrays-cpp-component-extensions.md).

Následující ukázka generuje C2728 a ukazuje, jak ji opravit:

```cpp
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
