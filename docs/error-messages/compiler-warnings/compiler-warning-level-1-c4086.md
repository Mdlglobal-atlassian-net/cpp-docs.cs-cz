---
title: "Kompilátoru (úroveň 1) upozornění C4086 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4086
dev_langs: C++
helpviewer_keywords: C4086
ms.assetid: 9248831b-22bf-47af-8684-bfadb17e94fc
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d34694f2f991e31ee7a896e128881ff6f09c54d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4086"></a>C4086 kompilátoru upozornění (úroveň 1)
Parametr očekávané – Direktiva pragma, 1, "2", "4", "8" nebo se 16.  
  
 Parametr – Direktiva pragma nemá požadovaná hodnota (1, 2, 4, 8 nebo 16).  
  
## <a name="example"></a>Příklad  
  
```  
// C4086.cpp  
// compile with: /W1 /LD  
#pragma pack( 3 ) // C4086  
```