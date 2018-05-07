---
title: Kompilátoru (úroveň 1) upozornění C4716 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4716
dev_langs:
- C++
helpviewer_keywords:
- C4716
ms.assetid: d95ecfe5-870f-461f-a746-7913af98414b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be620264c315fc9c2ff3cd4cb91bd9d77c8a4d07
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4716"></a>C4716 kompilátoru upozornění (úroveň 1)
'function' musí vrátit hodnotu  
  
 Danou funkci nevrátil hodnotu.  
  
 Pouze funkce s návratovým typem void může použít příkaz return bez doprovodné návratovou hodnotu.  
  
 Když tato funkce je volána, bude vrácen nedefinovanou hodnotu.  
  
 Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md).  
  
 Následující ukázka generuje C4716:  
  
```  
// C4716.cpp  
// compile with: /c /W1  
// C4716 expected  
#pragma warning(default:4716)  
int test() {  
   // uncomment the following line to resolve  
   // return 0;  
}  
```