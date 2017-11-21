---
title: "C2784 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2784
dev_langs: C++
helpviewer_keywords: C2784
ms.assetid: 3d761fe2-881c-48bd-afae-e2e714e20473
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c65b03e098b1e0917e554052ee3c8ebfa7181193
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2784"></a>C2784 chyby kompilátoru
"prohlášení": nelze odvodit argument šablony pro "typ" z "typ"  
  
 Kompilátor nelze určit šablonu argumentu z argumentů zadaná funkce.  
  
 Následující ukázka generuje C2784 a ukazuje, jak to opravit:  
  
```  
// C2784.cpp  
template<class T> class X {};  
template<class T> void f(X<T>) {}  
  
int main() {  
   X<int> x;  
   f(1);   // C2784  
  
   // To fix it, try the following line instead  
   f(x);  
}  
```