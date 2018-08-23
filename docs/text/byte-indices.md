---
title: Bajtové indexy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5beb69ef7d9d3356eddef40c6bce6483079d934a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590797"
---
# <a name="byte-indices"></a>Bajtové indexy
Použijte následující tipy:  
  
-   Práce s byjtově orientovaným index do řetězce přináší problémy, které jsou podobné těm, manipulaci s ukazatelem. Vezměte v úvahu tento příklad, který vyhledá v řetězci zpětné lomítko:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     To může být index bajt, není vedoucí bajt, a proto nemusí přejděte `character`.  
  
-   Použití [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) funkce předchozí problém vyřešit:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     To správně indexuje vedoucí bajt, proto k `character`. `_mbclen` Funkce určuje velikost znaku (1 nebo 2 bajtů).  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Poslední znak v řetězci](../text/last-character-in-a-string.md)