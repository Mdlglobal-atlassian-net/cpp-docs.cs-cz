---
title: Kompilátoru (úroveň 1) upozornění C4544 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4544
dev_langs:
- C++
helpviewer_keywords:
- C4544
ms.assetid: 11ee04df-41ae-435f-af44-881e801315a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc07340c0b8c9cc513e8b10910ccee21152328f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4544"></a>C4544 kompilátoru upozornění (úroveň 1)
"prohlášení": výchozí šablony argument ignorovat na toto prohlášení šablony  
  
 Výchozí šablony argument byl zadán nesprávný umístění a byla ignorována. Argumentem výchozí šablonu pro třídu šablony lze zadat pouze v deklarace a definice šablony třídy a ne na člena třídy šablony.  
  
 Tato ukázka generuje C4545 a další příklad ukazuje, jak to opravit:  
  
```  
// C4544.cpp  
// compile with: /W1 /LD  
template <class T>   
struct S  
{  
   template <class T1>   
      struct S1;  
   void f();  
};  
  
template <class T=int>  
template <class T1>  
struct S<T>::S1 {};   // C4544  
```  
  
 V tomto příkladu výchozí parametr platí pro šablony třídy `S`:  
  
```  
// C4544b.cpp  
// compile with: /LD  
template <class T = int>   
struct S  
{  
   template <class T1>   
      struct S1;  
   void f();  
};  
  
template <class T>  
template <class T1>  
struct S<T>::S1 {};  
```