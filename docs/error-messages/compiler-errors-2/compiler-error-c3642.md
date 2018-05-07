---
title: C3642 Chyba kompilátoru | Microsoft Docs
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
ms.openlocfilehash: c9e841bcc4fbcb62d6a2d1e6f51f47a73bd2e06a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3642"></a>C3642 chyby kompilátoru
'; typ nebo argumentů': nelze volat funkci s __clrcall konvence volání z nativní kód  
  
 Funkci, která je označena [__clrcall](../../cpp/clrcall.md) konvence volání nelze volat z nativního kódu (nespravovaný).  
  
 *typ nebo argumentů* je buď název funkce nebo typ `__clrcall` funkce, které se pokoušíte volání.  Typ se používá, když voláte prostřednictvím ukazatel na funkci.  
  
 K volání z nativní kontextu spravované funkce, můžete přidat funkci "obálky", která bude volat `__clrcall` funkce. Nebo můžete použít mezipaměti sdružených dat mechanismus CLR; v tématu [postupy: zařazování funkce ukazatelů pomocí PInvoke](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) Další informace.  
  
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