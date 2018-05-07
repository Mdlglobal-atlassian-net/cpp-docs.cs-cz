---
title: C2477 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2477
dev_langs:
- C++
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca1212a664582f19e91fbf21bde36431ec715946
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2477"></a>C2477 chyby kompilátoru
"člen": člen statických dat nelze inicializovat prostřednictvím odvozené třídy  
  
 Členem třídu šablony statických dat byl nesprávně inicializován. Toto je k narušující změně ve verzích Visual C++ compiler před Visual Studio .NET 2003, aby bylo možné v souladu s ISO C++ standard.  
  
 Následující ukázka generuje C2477:  
  
```  
// C2477.cpp  
// compile with: /Za /c  
template <class T>  
struct S {  
   static int n;  
};  
  
struct X {};  
struct A: S<X> {};  
  
int A::n = 0;   // C2477  
  
template<>  
int S<X>::n = 0;  
```