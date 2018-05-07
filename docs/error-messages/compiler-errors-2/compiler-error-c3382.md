---
title: C3382 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3382
dev_langs:
- C++
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8bcca58aecc3d5a5e7b621f45e102690c9f138c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3382"></a>C3382 chyby kompilátoru
'sizeof' není podporován s/clr: safe  
  
 Výstupní soubor **/CLR: safe** kompilace je soubor, který je prokazatelně typově bezpečný a sizeof není podporována, protože návratová hodnota sizeof – operátor je size_t –, jejichž velikost se liší podle operačního systému.  
  
 Další informace najdete v tématu,  
  
-   [sizeof – operátor](../../cpp/sizeof-operator.md)  
  
-   [/clr (kompilace modulu Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
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