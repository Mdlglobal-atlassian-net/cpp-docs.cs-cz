---
title: C2754 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2754
dev_langs:
- C++
helpviewer_keywords:
- C2754
ms.assetid: 1cab66c5-da9d-4b81-b7fb-9cdc48ff1ccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d1b12eb7b091c2566235239f5c9b929e4e881ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33233912"
---
# <a name="compiler-error-c2754"></a>C2754 chyby kompilátoru
'specializace': částečná specializace nemůže mít parametr závislé bez typu šablony  
  
 Došlo pokusu o částečně specialize třídy šablony, která má parametr závislé šablony bez typu. Toto není povoleno.  
  
 Následující ukázka generuje C2754:  
  
```  
// C2754.cpp  
// compile with: /c  
  
template<class T, T t>  
struct A {};  
  
template<class T, int N>  
struct B {};  
  
template<class T> struct A<T,5> {};   // C2754  
template<> struct A<int,5> {};   // OK  
template<class T> struct B<T,5> {};   // OK  
```