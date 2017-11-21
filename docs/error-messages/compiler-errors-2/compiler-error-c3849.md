---
title: "C3849 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3849
dev_langs: C++
helpviewer_keywords: C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7fbe46ee4f83dc5477eeb67e0debf14fe4f9fad5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3849"></a>C3849 chyby kompilátoru
volání funkce stylu výrazu typu "typ" by dojít ke ztrátě const nebo volatile kvalifikátory pro všechny číslo přetížení operátoru k dispozici  
  
 Proměnná s zadaného typu const volatile může volat pouze člen funkcí definovaných s kvalifikací const volatile stejné nebo větší.  
  
 Pokud chcete vyřešit tuto chybu, zadejte odpovídající – členská funkce. Převodu z na const nebo volatile kvalifikovaný objektu nelze provést, když převod způsobí ztrátu kvalifikaci. Můžete získat kvalifikátory, ale nemůže dojít ke ztrátě kvalifikátory v převodu z.  
  
 Následující ukázky generovat C3849:  
  
```  
// C3849.cpp  
void glbFunc3(int i, char c)  
{  
   i;  
}  
typedef void (* pFunc3)(int, char);  
  
void glbFunc2(int i)  
{  
   i;  
}  
  
typedef void (* pFunc2)(int);  
  
void glbFunc1()  
{  
}  
typedef void (* pFunc1)();  
  
struct S4  
{  
   operator ()(int i)  
   {  
      i;  
   }  
  
   operator pFunc1() const  
   {  
      return &glbFunc1;  
   }  
  
   operator pFunc2() volatile  
   {  
      return &glbFunc2;  
   }  
  
   operator pFunc3()  
   {  
      return &glbFunc3;  
   }  
  
   // operator pFunc1() const volatile  
   // {  
   //    return &glbFunc1;  
   // }  
};  
  
int main()  
{  
   // Cannot call any of the 4 overloads of "operator ()(.....)" and   
   // "operator pFunc()" because none is declared as "const volatile"  
   const volatile S4 s4;  // can only call cv member functions of S4  
   s4();   // C3849 to resolve, uncomment member function  
}  
```