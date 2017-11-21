---
title: "C2512 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2512
dev_langs: C++
helpviewer_keywords: C2512
ms.assetid: 15206da9-1164-451a-b869-280e00711aad
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63090bc7dac08aa87bcd68e77c076185176a7285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2512"></a>C2512 chyby kompilátoru
"identifikátor": žádný odpovídající výchozí konstruktor k dispozici  
  
 Žádný výchozí konstruktor je k dispozici pro zadanou třídu, struktura nebo union. Kompilátor poskytuje výchozí konstruktor pouze v případě, že uživatelská konstruktory nejsou zadány.  
  
 Pokud zadáte konstruktor, který přebírá parametr není void a chcete povolit třídu vytváření bez parametrů – například jako elementy pole – je taky nutné zadat výchozí konstruktor. Výchozí konstruktor může být konstruktor se výchozí hodnoty pro všechny parametry.  
  
 Následující ukázka generuje C2512 a ukazuje, jak to opravit:  
  
```  
// C2512.cpp  
// C2512 expected  
struct B {  
   B (char *);  
   // Uncomment the following line to fix.  
   // B() {};  
};  
  
int main() {  
   B b;   
}  
```  
  
 Následující příklad ukazuje další menší C2512. Chcete-li tuto chybu opravit, změna uspořádání kód, který definuje třídu před jeho konstruktor se odkazuje:  
  
```  
// C2512b.cpp  
// compile with: /c  
struct S {  
   struct X;  
  
   void f() {  
      X *x = new X();   // C2512 X not defined yet  
   }  
  
};  
  
struct S::X {};  
  
struct T {  
   struct X;  
   void f();  
};  
  
struct T::X {};  
  
void T::f() {  
   X *x = new X();  
}  
```  
  
 C2512 může být způsobeno volání výchozí – konstrukce třídu, která obsahuje const nebo odkaz na datový člen. V seznamu inicializátoru konstruktoru, což zabrání kompilátoru generování výchozí konstruktor, musí být inicializován tito členové.  
  
 Následující ukázka generuje C2512 a ukazuje, jak to opravit:  
  
```  
// C2512c.cpp  
// Compile by using: cl /c /W3 C2512c.cpp  
struct S {  
   const int i_;  
   int &r_;   
};   
  
int SumS() {  
   const int ci = 7;  
   int ir = 42;  
  
   S s1; // C2512 - no default constructor available  
   S s2{ci, ir};  // Fix - initialize const and reference members   
   return s2.i_ + s2.r_;  
}  
```