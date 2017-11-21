---
title: "Kompilátoru (úroveň 1) upozornění C4041 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4041
dev_langs: C++
helpviewer_keywords: C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2ae98391c3c5bfb603afae684027a86c39c840b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4041"></a>C4041 kompilátoru upozornění (úroveň 1)
omezení kompilátoru: ukončení prohlížeče výstup  
  
 Informace o prohlížeči překročil limit kompilátoru.  
  
 Toto upozornění může být způsobeno kompilujete s [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informace o prohlížeči včetně lokální proměnné).  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Kompilace s /Fr (informace o prohlížeči bez místní proměnné).  
  
2.  Zakážete prohlížeče výstup (Kompilovat bez /FR nebo /Fr).