---
title: "CXX0019 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0019
dev_langs: C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 67fbd43280ad6ffcecdf0532819cd80a0d44b479
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0019"></a>Chyba při vyhodnocování výrazu CXX0019
Chybný typ přetypování  
  
 Vyhodnocovací filtr výrazů C nelze provést typ přetypování jako zapsána.  
  
 Tato chyba je stejný jako CAN0019.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Zadaný typ neznámý.  
  
2.  Nebyly k dispozici příliš mnoho úrovní typů ukazatele. Například typ přetypování  
  
    ```  
    (char **)h_message  
    ```  
  
     Nelze vyhodnotit ve vyhodnocovací filtr výrazů C.