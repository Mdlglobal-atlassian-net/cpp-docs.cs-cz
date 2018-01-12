---
title: "C3149 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3149
dev_langs: C++
helpviewer_keywords: C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 154ae99c5e47438f6fca3b85ac8318c1b14f7a30
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3149"></a>C3149 chyby kompilátoru
'type': nemůžete použít tento typ zde bez nejvyšší úrovně "char"  
  
 Deklaraci nebyl zadán správně.  
  
 Například můžete mít definovaný typ CLR v globálním oboru a pokusu o vytvoření proměnné typu jako součást definice. Protože globální proměnné typy CLR nejsou povoleny, vygeneruje kompilátor C3149.  
  
 Pokud chcete tuto chybu vyřešit, deklarujte proměnné typů CLR v definici funkce nebo typu.  
  
 Následující ukázka generuje C3149:  
  
```  
// C3149.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   // declare an array of value types   
   array< Int32 ^> IntArray;   // C3149  
   array< Int32>^ IntArray2;   // OK  
}  
```  
  
 Následující ukázka generuje C3149:  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
