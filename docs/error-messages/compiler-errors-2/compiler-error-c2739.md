---
title: Chyba kompilátoru C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 18cece8d9630aa93e867329acc7cefea30da3286
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759656"
---
# <a name="compiler-error-c2739"></a>Chyba kompilátoru C2739

' Number ': explicitní spravované nebo dimenze pole WinRT musí být v rozmezí od 1 do 32

Dimenze pole nebyla mezi 1 a 32.

Následující ukázka generuje C2739 a ukazuje, jak ji opravit:

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
