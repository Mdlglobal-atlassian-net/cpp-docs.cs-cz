---
title: "Kompilátoru (úroveň 1) upozornění C4835 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4835
dev_langs: C++
helpviewer_keywords: C4835
ms.assetid: d2e44c62-7b0e-4a45-943d-97903e27ed9d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c1b01a84313d2d04e927420d1462dd8d5c2c495b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4835"></a>C4835 kompilátoru upozornění (úroveň 1)
"proměnné": inicializátoru pro exportovaná data se nespustí, dokud spravovaný kód je nejdřív provést v sestavení hostitele  
  
 Při přístupu k datům mezi spravované součásti, doporučujeme vám není použijte nativní C++ import a export mechanismy. Místo toho deklarovat datových členů uvnitř spravovaného typu a odkazovat na metadata s `#using` v klientovi. Další informace najdete v tématu [#using – direktiva](../../preprocessor/hash-using-directive-cpp.md).  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4835.  
  
```  
// C4835.cpp  
// compile with: /W1 /clr /LD  
int f() { return 1; }  
int n = 9;  
  
__declspec(dllexport) int m = f();   // C4835  
__declspec(dllexport) int *p = &n;   // C4835  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka spotřebuje komponentu vytvořené v předchozí ukázce zobrazující, že je hodnota proměnné není podle očekávání.  
  
```  
// C4835_b.cpp  
// compile with: /clr C4835.lib  
#include <stdio.h>  
__declspec(dllimport) int m;  
__declspec(dllimport) int *p;  
  
int main() {  
   printf("%d\n", m);  
   printf("%d\n", p);  
}  
```  
  
```Output  
0  
268456008  
```