---
title: "Kompilátoru (úroveň 3) upozornění C4522 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4522
dev_langs: C++
helpviewer_keywords: C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 564ccedc090d7fb5c3f594f62b21f0afdf094a26
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4522"></a>C4522 kompilátoru upozornění (úroveň 3)
'class': Zadaná více operátory přiřazení  
  
 Třída nemá více operátorů přiřazení jednoho typu. Toto upozornění je informační; konstruktory jsou volány v programu.  
  
 Použití [upozornění](../../preprocessor/warning.md) – Direktiva pragma pro potlačení toto upozornění.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4522.  
  
```  
// C4522.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
  
using namespace std;  
class A {  
public:  
   A& operator=( A & o ) { cout << "A&" << endl; return *this; }  
   A& operator=( const A &co ) { cout << "const A&" << endl; return *this; }   // C4522  
};  
  
int main() {  
   A o1, o2;  
   o2 = o1;  
   const A o3;  
   o1 = o3;  
}  
```