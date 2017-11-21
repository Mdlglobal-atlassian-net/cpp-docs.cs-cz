---
title: "Bajtové indexy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: ec28ce5e577fe4d1e766934095d22a7e64a6a3da
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="byte-indices"></a>Bajtové indexy
Použijte následující tipy:  
  
-   Práce s indexem byjtově orientovaným na řetězec uvede problémy, které jsou podobné těm, které jsou manipulaci s ukazatelem. Tento příklad, který prohledá řetězec pro zpětné lomítko vezměte v úvahu:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     To může být index druhého bajtu, nikoli úvodního bajtu, a nemusí tedy ukazovat `character`.  
  
-   Použití [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) funkce předchozí problém vyřešit:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     Ta správně indexuje úvodní bajt, tedy na `character`. `_mbclen` Funkce určuje velikost znaku (v bajtech 1 nebo 2).  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Poslední znak v řetězci.](../text/last-character-in-a-string.md)