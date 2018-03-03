---
title: "Kompilátoru (úroveň 4) upozornění C4238 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e8e52868d97d31243f92307e9bfd158c818c2f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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