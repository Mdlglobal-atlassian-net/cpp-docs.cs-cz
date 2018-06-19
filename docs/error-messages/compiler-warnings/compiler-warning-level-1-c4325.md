---
title: Kompilátoru (úroveň 1) upozornění C4325 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936433987f823ae7d5d22cfd075f188dd5d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277641"
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
  
-   .text  
  
-   .const –  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 Další části lze přidat později.  
  
## <a name="see-also"></a>Viz také  
 [section](../../preprocessor/section.md)