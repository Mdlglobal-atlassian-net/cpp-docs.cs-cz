---
title: CXX0019 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52e1679374e105ab06ce245ba68cfe92706689e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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