---
title: "C2910 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2910
dev_langs: C++
helpviewer_keywords: C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: db1c4d7b4533d6bbfb0848c1dc16a7336ad81eb0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2910"></a>C2910 chyby kompilátoru
'function': nelze explicitně specializuje  
  
 Kompilátor zjistil pokus o explicitně specialize funkce dvakrát.  
  
 Následující ukázka generuje C2910:  
  
```  
// C2910.cpp  
// compile with: /c  
template <class T>  
struct S;  
  
template <> struct S<int> { void f() {} };  
template <> void S<int>::f() {}   // C2910 delete this specialization  
```  
  
 C2910 lze vygenerovat také pokud se pokusíte explicitně specialize členem bez šablony. To znamená můžete pouze explicitně specialize šablonu funkce.  
  
 Následující ukázka generuje C2910:  
  
```  
// C2910b.cpp  
// compile with: /c  
template <class T> struct A {  
   A(T* p);  
};  
  
template <> struct A<void> {  
   A(void* p);  
};  
  
template <class T>  
inline A<T>::A(T* p) {}  
  
template <> A<void>::A(void* p){}   // C2910  
// try the following line instead  
// A<void>::A(void* p){}  
```  
  
 Tato chyba bude vygenerována také v důsledku kompilátoru shoda práci, kterou bylo provedeno v sadě Visual Studio .NET 2003:.  
  
 Pro kód bude v verze Visual C++ pro Visual Studio .NET 2003 a sady Visual Studio .NET, odeberte `template <>`.  
  
 Následující ukázka generuje C2910:  
  
```  
// C2910c.cpp  
// compile with: /c  
template <class T> class A {  
   void f();  
};  
  
template <> class A<int> {  
   void f();  
};  
  
template <> void A<int>::f() {}   // C2910  
// try the following line instead  
// void A<int>::f(){}   // OK  
```