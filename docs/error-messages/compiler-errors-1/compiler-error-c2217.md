---
title: Chyba kompilátoru C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: 7417c651fde6bef781bb6eb2e081cd3ad8ecc3a0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741297"
---
# <a name="compiler-error-c2217"></a>Chyba kompilátoru C2217

' attribute1 ' vyžaduje ' attribute2 '

První atribut Function vyžaduje druhý atribut.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Funkce přerušení (`__interrupt`) je deklarována jako `near`. Funkce přerušení musí být `far`.

1. Funkce přerušení deklarovaná pomocí `__stdcall`nebo `__fastcall`. Funkce přerušení musí používat konvence volání jazyka C.

## <a name="example"></a>Příklad

K C2217 může také dojít, pokud se pokusíte vytvořit vazby delegáta na funkci CLR, která přebírá proměnný počet argumentů. Pokud má funkce také přetížení e-pole, použijte místo toho parametr. Následující ukázka generuje C2217.

```cpp
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```
