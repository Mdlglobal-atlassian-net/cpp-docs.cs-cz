---
title: "C3287 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3287
dev_langs: C++
helpviewer_keywords: C3287
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f282b1fd67603b17bd9c2ea1ad267218c7650e40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3287"></a>C3287 chyby kompilátoru
typu "typ" (návratový typ GetEnumerator) musí mít aktuální veřejné vlastnosti a vhodný veřejné MoveNext – členská funkce  
  
 Uživatelem definované kolekci třídy musí obsahovat definice pro `MoveNext` a `Current`.  
  
 V tématu [postupy: Iterate Over a User-Defined kolekce se pro každou](../../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3287.  
  
```  
// C3287.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {  
   bool MoveNext() {  
      return true;  
   }  
   property Object^ Current {  
      Object^ get() {  
         Object ^ o = gcnew Object;  
         return o;  
      }  
   }  
};  
  
ref struct R2 {  
   R ^GetEnumerator() {  
      R^ r = gcnew R;  
      return r;  
   }  
};  
  
ref struct T {};  
  
ref struct T2 {  
   T ^GetEnumerator() {  
      T^ t = gcnew T;  
      return t;  
   }  
};  
  
int main() {  
   for each (int i in gcnew T2) {}   // C3287  
   for each (int i in gcnew R2) {}   // OK  
}  
```