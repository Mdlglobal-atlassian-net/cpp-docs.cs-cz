---
title: "Kompilátoru (úroveň 1) upozornění C4325 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4325
dev_langs: C++
helpviewer_keywords: C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5b5ce2e90705a1f3a899ef31313d1a402d2ecc04
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4325"></a>C4325 kompilátoru upozornění (úroveň 1)
**atributy pro standardní oddíl.**   
 ***část* ' ignorovat**  
  
 Atributy standardní oddílu nesmí změnit. Příklad:  
  
```  
#pragma section(".sdata", long)  
```  
  
 To by přepsala `.sdata` standardní oddíl, který používá **krátké** datový typ s **dlouho** datový typ.  
  
 Standardní oddíly, jejichž atributy nesmí změnit zahrnout,  
  
-   .data –  
  
-   .sdata  
  
-   .BSS  
  
-   .sbss  
  
-   text  
  
-   .const –  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 Další části lze přidat později.  
  
## <a name="see-also"></a>Viz také  
 [část](../../preprocessor/section.md)