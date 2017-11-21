---
title: "C3231 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3231
dev_langs: C++
helpviewer_keywords: C3231
ms.assetid: fe5dc352-e634-45fa-9534-3da176294c98
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5d3cf8747f25fdccda1467e894f95d8bcfb3525c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3231"></a>C3231 chyby kompilátoru
'arg': argument typu šablonu nelze použít parametr obecného typu  
  
 Jsou šablony vytvořeny v době kompilace, ale instance obecné typy v době běhu. Proto není možné vygenerovat obecný kód, který můžete volat šablony, protože šablona nelze vytvořit instanci za běhu, když se nakonec označuje obecného typu.  
  
 Následující ukázka generuje C3231:  
  
```  
// C3231.cpp  
// compile with: /clr /LD  
template <class T> class A;  
  
generic <class T>  
ref class C {  
   void f() {  
      A<T> a;   // C3231  
   }  
};  
```