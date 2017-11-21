---
title: "C3483 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3483
dev_langs: C++
helpviewer_keywords: C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 145e0162c47b360b9d37cf95b108446f919435de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3483"></a>C3483 chyby kompilátoru
'var' je již součástí seznamu zachycení lambda  
  
 Stejnou proměnnou byl předán zachycení seznam výrazu lambda více než jednou.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Odeberte všechny další instance proměnné ze seznamu zachycení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3483, protože proměnná `n` se zobrazí v seznamu zachycení výrazu lambda více než jednou:  
  
```  
// C3483.cpp  
  
int main()  
{  
   int m = 6, n = 5;  
   [m,n,n] { return n + m; }(); // C3483  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)