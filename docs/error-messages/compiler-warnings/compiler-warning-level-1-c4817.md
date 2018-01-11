---
title: "Kompilátoru (úroveň 1) upozornění C4817 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4817
dev_langs: C++
helpviewer_keywords: C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f11e0c555bdf3a80dcc381ee642d6adb0ecc5c21
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4817"></a>C4817 kompilátoru upozornění (úroveň 1)
"člen": Neplatné použití '.' pro přístup k tomuto členu; nahradí kompilátoru '->.  
  
 Operátor přístupu nesprávný členů byl použit.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4817.  
  
```  
// C4817.cpp  
// compile with: /clr /W1  
using namespace System;  
int main() {  
   array<Int32> ^ a = gcnew array<Int32>(100);  
   Console::WriteLine( a.Length );   // C4817  
   Console::WriteLine( a->Length );   // OK  
}  
```  
