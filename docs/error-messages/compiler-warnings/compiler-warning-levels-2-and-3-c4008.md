---
title: C4008 kompilátoru upozornění (úrovně 2 a 3) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cdc88f222f9e5ce3829a63c131c955ce2abdd7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294255"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>C4008 kompilátoru upozornění (úrovně 2 a 3)
"identifikátor": atribut ' attribute ' ignorovat  
  
 Kompilátor ignoruje `__fastcall`, **statické**, nebo **vložené** atribut pro funkci (úroveň 3 upozornění) nebo dat (úroveň 2 upozornění).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  `__fastcall` atribut s daty.  
  
2.  **statické** nebo **vložené** atribut s **hlavní** funkce.