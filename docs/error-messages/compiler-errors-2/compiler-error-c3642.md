---
title: Chyba kompilátoru C3642 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3642
dev_langs:
- C++
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: febd6f1a9a3b4bac8bbee59cbf8c5bead93c3fb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047717"
---
# <a name="compiler-error-c3642"></a>Chyba kompilátoru C3642

' typ/args': nelze volat funkci s konvencí volání z nativního kódu __clrcall

Funkce, která je označena [__clrcall](../../cpp/clrcall.md) konvence volání nelze volat z nativního (nespravovaného) kódu.

*Typ/args* je buď název funkce nebo typ `__clrcall` funkce, které se snažíte volat.  Typ se používá, když voláte prostřednictvím ukazatele funkce.

Volání spravované funkce z nativního kontextu, můžete přidat funkci "zabezpečenou obálku", která bude volat `__clrcall` funkce. Nebo můžete použít mechanismus sběrného systému CLR; v tématu [postupy: zařazování funkce ukazatele pomocí PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) Další informace.

Následující ukázka generuje C3642:

```
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