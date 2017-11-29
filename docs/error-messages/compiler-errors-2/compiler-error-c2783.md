---
title: "C2783 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2783
dev_langs: C++
helpviewer_keywords: C2783
ms.assetid: 1ce94a11-bb8b-4be3-a222-f1f105da74b3
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1fff9803fa54d1ea18d0ada78c816067731e8c41
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2783"></a>C2783 chyby kompilátoru
"prohlášení": nelze odvodit argument šablony pro "identifikátor"  
  
 Kompilátor nelze určit šablonu argumentu. Výchozí argumenty nelze použít k odvození argumentu šablony.  
  
 Následující ukázka generuje C2783:  
  
```  
// C2783.cpp  
template<typename T1, typename T2>  
T1 f(T2) {  
   return 248;  
}  
  
int main() {  
   f(1);   // C2783  
   // try the following line instead  
   int i = f<int>(1);  
}  
```  
  
 C2783 může dojít také při použití obecných typů:  
  
```  
// C2783b.cpp  
// compile with: /clr  
using namespace System;  
generic<typename T1, typename T2>   
T1 gf(T2) {  
   T1 t1 = safe_cast<T1>( Activator::CreateInstance(T1::typeid));  
   return t1;  
}  
  
ref class MyClass{};  
  
int main() {  
   int i;  
   i = gf(9);   // C2783  
  
   // OK  
   i = gf<int>(9);  
}  
```