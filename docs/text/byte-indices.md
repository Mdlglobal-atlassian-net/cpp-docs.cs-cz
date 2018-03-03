---
title: "Bajtové indexy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 594acadeedad06e9720180c38bd0bcd657391879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [Poslední znak v řetězci](../text/last-character-in-a-string.md)