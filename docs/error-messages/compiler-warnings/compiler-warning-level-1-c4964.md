---
title: "Kompilátoru (úroveň 1) upozornění C4964 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4964
dev_langs: C++
helpviewer_keywords: C4964
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b1c7483b82c363898bc16ed5fc7d48f9cf0b35c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4964"></a>C4964 kompilátoru upozornění (úroveň 1)
Nebyly zadány žádné možnosti optimalizace; informace o profilu nebudou shromažďovány.  
  
 [/GL](../../build/reference/gl-whole-program-optimization.md) a [/ltgc](../../build/reference/ltcg-link-time-code-generation.md) byly zadány, ale žádné optimalizace se požadovaly, tak, aby žádné .pgc soubory se budou generovat, a proto bude možné žádné optimalizace na základě profilu.  
  
 Pokud chcete generovat při spuštění aplikace .pgc soubory, určete jednu z [/O](../../build/reference/o-options-optimize-code.md) – možnosti kompilátoru.  
  
 Následující ukázka generuje C4964:  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```