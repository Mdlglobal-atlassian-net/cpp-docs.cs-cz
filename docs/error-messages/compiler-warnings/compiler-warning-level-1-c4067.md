---
title: Kompilátoru (úroveň 1) upozornění C4067 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4067
dev_langs:
- C++
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eccec985e6a9e652f18c6513542942351ff6efc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4067"></a>C4067 kompilátoru upozornění (úroveň 1)
neočekávané tokeny následující direktivy preprocesoru - očekává nový řádek  
  
 Kompilátor najít a další znaky následující direktivy preprocesoru ignorovány. Toto upozornění se zobrazí pouze pod kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).  
  
```  
// C4067a.cpp  
// compile with: /DX /Za /W1  
#pragma warning(default:4067)  
#if defined(X)  
#else  
#endif v   // C4067  
int main()  
{  
}  
```  
  
### <a name="to-resolve-this-warning-try-the-following"></a>Chcete-li vyřešit toto upozornění, zkuste následující postup:  
  
1.  Kompilovat s **/Ze**.  
  
2.  Použijte komentář oddělovače:  
  
```  
// C4067b.cpp  
// compile with: /DX /Za /W1  
#if defined(X)  
#else  
#endif  
int main()  
{  
}  
```