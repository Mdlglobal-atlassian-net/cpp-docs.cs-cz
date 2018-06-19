---
title: Kompilátoru (úroveň 1) upozornění C4540 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4540
dev_langs:
- C++
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3939ad2bbcba1ab3b492d83bdbb8f7076c2c5f2b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283059"
---
# <a name="compiler-warning-level-1-c4540"></a>C4540 kompilátoru upozornění (úroveň 1)
dynamic_cast použitý k převedení nedostupné nebo je nejednoznačný základní; spuštění testu se nezdaří ('type1' na 'type2')  
  
 Jste použili `dynamic_cast` převést z jednoho typu. Kompilátor určit, že by vždy selže přetypování (vrátit **NULL**) protože základní třída není přístupný (`private`, například) nebo nejednoznačný (vyskytuje více než jednou v hierarchii tříd pro instanci).  
  
 Následující ukazuje příklad toto upozornění. Třída **B** je odvozená od třídy **A**. Program používá `dynamic_cast` přetypovat z třídy **B** (odvozené třídy) do třídy **A**, která vždy selže, protože třída **B** je `private` proto nedostupné. Změna přístup **A** k **veřejné** vyřešit upozornění.  
  
```  
// C4540.cpp  
// compile with: /W1  
  
struct A {   
   virtual void g() {}  
};  
  
struct B : private A {  
   virtual void g() {}  
};  
  
int main() {  
   B b;  
   A * ap = dynamic_cast<A*>(&b);   // C4540  
}  
```