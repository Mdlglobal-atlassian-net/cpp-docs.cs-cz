---
title: Kompilátoru (úroveň 3) upozornění C4686 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4686
dev_langs:
- C++
helpviewer_keywords:
- C4686
ms.assetid: 767c83c2-9e4b-4f9e-88c8-02128ba563f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1edbf438951644f63aae637a68f69d173ab7e1b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4686"></a>C4686 kompilátoru upozornění (úroveň 3)
**'**   
 ***uživatelem definovaný typ* ': vrátit změnu v hodnotě UDT možné změnu v chování konvence volání**  
  
 Specializace šablony třída nebyla je definována předtím, než byl použit v návratovým typem. Všechno, co vytvoří instanci třídy bude vyřešen C4686; deklarování instance nebo přístupu k nim člena (C\<int >:: NIC) jsou taky možnosti.  
  
 Toto upozornění je ve výchozím nastavení vypnutý. V tématu [kompilátoru upozornění, že jsou vypnout ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Další informace.  
  
 Místo toho zkuste následující  
  
```  
// C4686.cpp  
// compile with: /W3  
#pragma warning (default : 4686)  
template <class T>  
class C;  
  
template <class T>  
C<T> f(T);  
  
template <class T>  
class C {};  
  
int main() {  
   f(1);   // C4686  
}  
  
template <class T>  
C<T> f(T) {  
   return C<int>();  
}  
```