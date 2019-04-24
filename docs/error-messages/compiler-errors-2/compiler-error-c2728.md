---
title: Chyba kompilátoru C2728
ms.date: 11/04/2016
f1_keywords:
- C2728
helpviewer_keywords:
- C2728
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
ms.openlocfilehash: 1fbbc3d63386ebe98a447de8b7166a5263d2168f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208412"
---
# <a name="compiler-error-c2728"></a>Chyba kompilátoru C2728

'type': nativní pole nemůže obsahovat tento typ.

Syntaxe vytváření pole byla použita k vytvoření pole spravované nebo objekty WinRT. Nelze vytvořit pole spravované nebo objekty WinRT pomocí syntaxe nativní pole.

Další informace najdete v tématu [pole](../../extensions/arrays-cpp-component-extensions.md).

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
