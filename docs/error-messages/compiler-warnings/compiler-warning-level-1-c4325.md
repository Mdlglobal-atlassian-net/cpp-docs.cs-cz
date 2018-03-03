---
title: "Kompilátoru (úroveň 1) upozornění C4325 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab31150efc02601d7392470198e162e979ac4917
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [section](../../preprocessor/section.md)