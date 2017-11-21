---
title: "C2472 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2472
dev_langs: C++
helpviewer_keywords: C2472
ms.assetid: 3b36bcdc-2ba5-4357-ab88-7545ba0551cd
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ed41a3d78ab9652d1e88ceefe29011eb5b2225a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2472"></a>C2472 chyby kompilátoru
ve spravovaném kódu nemůže být generována 'function': 'zprávy'; kompilace s volbou/CLR ke generování smíšený bitové kopie  
  
 Tato chyba nastane, když typy nejsou podporované ve spravovaném kódu se používají v rámci čistý společné prostředí runtime (CLR) jazyk. Kompilovat s **/CLR** vyřešit chyby.  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2472.  
  
```  
// C2472.cpp  
// compile with: /clr:pure  
// C2472 expected  
  
#include <cstdlib>  
  
int main()  
{  
   int * __ptr32 p32;  
   int * __ptr64 p64;  
  
   p32 = (int * __ptr32)malloc(4);  
   p64 = p32;  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [/ CLR (kompilace common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)