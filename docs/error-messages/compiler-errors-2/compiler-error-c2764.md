---
title: "C2764 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2764
dev_langs: C++
helpviewer_keywords: C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 18e32646c3930dfae79ffd1ed13dfa014da4ce1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2764"></a>C2764 chyby kompilátoru
'param': parametr šablony není používá nebo deducible v částečná specializace 'specializace.  
  
 Částečná specializace nepoužívá parametr šablony. Díky tomu částečná specializace nepoužitelný, protože nelze odvodit parametr šablony.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2764:  
  
```  
// C2764.cpp  
#include <stdio.h>  
template <class T1, class T2>  
struct S  {  
   int m_i;  
};  
  
template <class T1, class T2>  
struct S<int, T2*> {   // C2764  
// try the following line instead  
// struct S<T1(*)(T2), T2*> {  
   char m_c;  
};  
  
int main() {  
   S<int, char> s1;  
   S<void (*)(short), short *> s2;  
   s2.m_c = 10;  
   s1.m_i = s2.m_c;  
   printf_s("%d\n", s1.m_i);  
}  
```