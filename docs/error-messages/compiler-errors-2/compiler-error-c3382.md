---
title: "C3382 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3382
dev_langs: C++
helpviewer_keywords: C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c58047e409c60fd2b6cb65418131f6aadb1430a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3382"></a>C3382 chyby kompilátoru
'sizeof' není podporován s/clr: safe  
  
 Výstupní soubor **/CLR: safe** kompilace je soubor, který je prokazatelně typově bezpečný a sizeof není podporována, protože návratová hodnota sizeof – operátor je size_t –, jejichž velikost se liší podle operačního systému.  
  
 Další informace najdete v tématu,  
  
-   [sizeof – operátor](../../cpp/sizeof-operator.md)  
  
-   [/ CLR (kompilace common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Obecné problémy migrace v 64bitovém prostředí Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3382.  
  
```  
// C3382.cpp  
// compile with: /clr:safe  
int main() {  
   sizeof( char );   // C3382  
}  
```