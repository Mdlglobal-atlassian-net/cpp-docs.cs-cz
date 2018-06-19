---
title: Kompilátoru (úroveň 4) upozornění C4238 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06dbec01da8d1b47cb7b93c90a22ae5266e9b4c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292434"
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