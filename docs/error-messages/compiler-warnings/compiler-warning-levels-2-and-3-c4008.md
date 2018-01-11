---
title: "C4008 kompilátoru upozornění (úrovně 2 a 3) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4008
dev_langs: C++
helpviewer_keywords: C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: afd45078ac75ec9da8343baa2c203e75b324fb6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>C4008 kompilátoru upozornění (úrovně 2 a 3)
"identifikátor": atribut ' attribute ' ignorovat  
  
 Kompilátor ignoruje `__fastcall`, **statické**, nebo **vložené** atribut pro funkci (úroveň 3 upozornění) nebo dat (úroveň 2 upozornění).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  `__fastcall`atribut s daty.  
  
2.  **statické** nebo **vložené** atribut s **hlavní** funkce.