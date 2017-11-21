---
title: "Kompilátoru (úroveň 4) upozornění C4238 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4238
dev_langs: C++
helpviewer_keywords: C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 32e8b4b252ed1da4bef785032929e615a6c73bc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4238"></a>C4238 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: použít jako lvalue rvalue – třída  
  
 Pro kompatibilitu s předchozí verzí aplikace Visual C++, rozšíření Microsoft (**/Ze**) vám umožní používat typu třídy jako rvalue v kontextu, který implicitně nebo explicitně bere jeho adresy. V některých případech, například v příkladu níže může být nebezpečný.  
  
## <a name="example"></a>Příklad  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 Toto použití způsobí chybu v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).