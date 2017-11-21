---
title: "Kompilátoru (úroveň 4) upozornění C4057 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4057
dev_langs: C++
helpviewer_keywords: C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 553cd9a79755d90dc53f552b7e980f2d5cd9b454
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4057"></a>C4057 kompilátoru upozornění (úroveň 4)
'operátor': 'identifier1' indirection mírně odlišné základních typů z 'identifier2.  
  
 Dva výrazy ukazatel odkazovat na jiné základní typy. Výrazy jsou bez převodu použít.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Typy signed a unsigned kombinací.  
  
2.  Kombinování **krátké** a **dlouho** typy.