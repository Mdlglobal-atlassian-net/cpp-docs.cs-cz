---
title: Chyba kompilátoru C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 3e3584d5e9166bb57e3be56e33f0198cacace7c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615173"
---
# <a name="compiler-error-c2728"></a>Chyba kompilátoru C2728

'type': nativní pole nemůže obsahovat tento typ.

Syntaxe vytváření pole byla použita k vytvoření pole spravované nebo objekty WinRT. Nelze vytvořit pole spravované nebo objekty WinRT pomocí syntaxe nativní pole.

Další informace najdete v tématu [pole](../../windows/arrays-cpp-component-extensions.md).

Následující ukázka generuje C2728 a ukazuje, jak ho opravit:

```
// C2728.cpp
// compile with: /clr

int main() {
   int^ arr[5];   // C2728

   // try the following line instead
   array<int>^arr2;
}
```
