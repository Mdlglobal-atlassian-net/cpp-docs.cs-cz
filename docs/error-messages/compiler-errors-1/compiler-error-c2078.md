---
title: "C2078 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2078
dev_langs: C++
helpviewer_keywords: C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a6ae181d68f0487f663febfbe38fa42af8670b28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2078"></a>C2078 chyby kompilátoru
příliš mnoho inicializátory  
  
 Počet inicializátory překračuje počet objektů, které chcete být inicializován.  
  
 Kompilátor můžete odvodit správné přiřazení inicializátory objektů a vnitřních objektů, když jsou v seznamu inicializátoru elided vnitřní složené závorky. Dokončení výztuhy také eliminuje nejednoznačnosti a výsledkem správné přiřazení. Částečné výztuhy může způsobit C2078 z důvodu nejednoznačnosti v přiřazení inicializátory objektů.  
  
 Následující ukázka generuje C2078 a ukazuje, jak to opravit:  
  
```  
// C2078.cpp  
// Compile by using: cl /c /W4 C2078.cpp  
struct S {  
   struct {  
      int x, y;  
   } z[2];  
};  
  
int main() {  
   int d[2] = {1, 2, 3};   // C2078  
   int e[2] = {1, 2};      // OK  
  
   char a[] = {"a", "b"};  // C2078  
   char *b[] = {"a", "b"}; // OK  
   char c[] = {'a', 'b'};  // OK  
  
   S s1{1, 2, 3, 4};       // OK  
   S s2{{1, 2}, {3, 4}};   // C2078  
   S s3{{1, 2, 3, 4}};     // OK  
   S s4{{{1, 2}, {3, 4}}}; // OK  
}  
  
```