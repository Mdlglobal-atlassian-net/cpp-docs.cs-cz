---
title: "Inkrementace a dekrementace ukazatelů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 7c63b900b389edb2c62b69296f709619072f4511
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="incrementing-and-decrementing-pointers"></a>Inkrementace a dekrementace ukazatelů
Použijte následující tipy:  
  
-   Přejděte na úvodní bajty, ne na poslední bajt. Je obvykle bezpečné mít ukazatel na poslední bajt. Obvykle je bezpečnější dál spíše než v zpětného vyhledávání řetězec.  
  
-   Existují ukazatele přírůstek nebo snížení funkce a makra, které se přesouvají přes celou znak:  
  
    ```  
    sz1++;  
    ```  
  
     Změní na:  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc` a `_mbsdec` funkce správně zvýší a sníží v `character` jednotek, bez ohledu na velikost znaku.  
  
-   Pro snížení hodnoty je třeba ukazatel na začátek řetězce, a to následovně:  
  
    ```  
    sz2--;  
    ```  
  
     Změní na:  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     Alternativně může být hlavní ukazatel neplatný znak v řetězci, tak, aby:  
  
    ```  
    sz2Head < sz2  
    ```  
  
     Musíte mít ukazatel na známý platný úvodní bajt.  
  
-   Můžete chtít zachovat ukazatel na předchozí znak pro rychlejší volání `_mbsdec`.  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Bajtové indexy](../text/byte-indices.md)