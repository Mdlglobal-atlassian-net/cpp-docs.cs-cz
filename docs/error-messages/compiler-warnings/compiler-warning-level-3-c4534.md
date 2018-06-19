---
title: Kompilátoru (úroveň 3) upozornění C4534 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- c4534
dev_langs:
- C++
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b765f5f654c8d533b0ae22d874e7657cd10d667
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293030"
---
# <a name="compiler-warning-level-3-c4534"></a>C4534 kompilátoru upozornění (úroveň 3)
'konstruktor, nebude výchozí konstruktor pro třídu 'class' z důvodu argument výchozí  
  
 Nespravované třídy může obsahovat konstruktor s parametry, které mají výchozí hodnoty a kompilátor se použít jako výchozí konstruktor. Třída označené jako `value` – klíčové slovo nebude použijte konstruktor s výchozími hodnotami jeho parametrů jako výchozí konstruktor.  
  
 Další informace najdete v tématu [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
 Následující ukázka generuje C4534:  
  
```  
// C4534.cpp  
// compile with: /W3 /clr /WX  
value class MyClass {  
public:  
   int ii;  
   MyClass(int i = 9) {   // C4534, will not be the default constructor  
      i++;  
   }  
};  
  
int main() {  
   MyClass ^ xx = gcnew MyClass;  
   xx->ii = 0;  
}  
```