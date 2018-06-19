---
title: Kompilátoru (úroveň 3) upozornění C4522 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4522
dev_langs:
- C++
helpviewer_keywords:
- C4522
ms.assetid: 7065dc27-0b6c-4e68-a345-c51cdb99a20b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e57f32c715b6e6f0846025d5010631c746589bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298932"
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