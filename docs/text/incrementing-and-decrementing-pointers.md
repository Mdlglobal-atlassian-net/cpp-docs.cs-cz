---
title: Inkrementace a dekrementace ukazatelů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4fff5d7ec20ce052e4d831f1556432186ebc7bb
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603357"
---
# <a name="incrementing-and-decrementing-pointers"></a>Inkrementace a dekrementace ukazatelů
Použijte následující tipy:  
  
-   Přejděte na úvodní bajty, ne na druhý bajt. Je obvykle bezpečné s ukazatelem na druhý bajt. Obvykle je bezpečnější kontrolovat řetězec vpřed spíše než v opačném pořadí.  
  
-   Existuje funkce Inkrementace a dekrementace ukazatelů a makra, které přesouvají přes celý znak:  
  
    ```  
    sz1++;  
    ```  
  
     změní:  
  
    ```  
    sz1 = _mbsinc( sz1 );  
    ```  
  
     `_mbsinc` a `_mbsdec` funkce správně zvýší a sníží v `character` jednotky, bez ohledu na velikost znaků.  
  
-   Sníží musíte ukazatel na začátek řetězce, viz následující příklad:  
  
    ```  
    sz2--;  
    ```  
  
     změní:  
  
    ```  
    sz2 = _mbsdec( sz2Head, sz2 );  
    ```  
  
     Alternativně může být hlavního ukazatele na platný znak v řetězci, tak, aby:  
  
    ```  
    sz2Head < sz2  
    ```  
  
     Musíte mít ukazatel na známé platné vedoucí bajt.  
  
-   Můžete chtít zachovat ukazatel na předchozí znak pro rychlejší volání `_mbsdec`.  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Bajtové indexy](../text/byte-indices.md)