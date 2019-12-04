---
title: Chyba kompilátoru C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: 7c3f9f05bf04c9a1c20fff7910836e7b50468a8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742454"
---
# <a name="compiler-error-c3642"></a>Chyba kompilátoru C3642

return_type/args: nejde volat funkci s __clrcall konvencí volání z nativního kódu.

Funkce, která je označena pomocí [__clrcall](../../cpp/clrcall.md) konvence volání, nemůže být volána z nativního (nespravovaného) kódu.

*return_type/args* je buď název funkce, nebo typ `__clrcall` funkce, kterou se pokoušíte volat.  Typ se používá při volání prostřednictvím ukazatele na funkci.

Chcete-li volat spravovanou funkci z nativního kontextu, můžete přidat funkci "Obálka", která bude volat funkci `__clrcall`. Nebo můžete použít mechanismus zařazování CLR; Další informace najdete v tématu [Postupy: zařazování ukazatelů na funkce pomocí PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) .

Následující ukázka generuje C3642:

```cpp
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```
