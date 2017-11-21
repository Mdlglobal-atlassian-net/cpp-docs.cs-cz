---
title: "C3642 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3642
dev_langs: C++
helpviewer_keywords: C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4b5d73344b99a42dfc4caf2b9f6b8cf7c9dc18bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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