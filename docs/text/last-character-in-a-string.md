---
title: Poslední znak v řetězci | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88cde1d2eb30103462f7ae8f8c06274a2977fc36
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="last-character-in-a-string"></a>Poslední znak v řetězci
Použijte následující tipy:  
  
-   Rozsahy posledního bajtu přesahují v mnoha případech sadu znaků ASCII. Prohledávání můžete bez obav použít pro žádné řídicí znaky (menší než 32).  
  
-   Vezměte v úvahu následující řádek kódu, který může kontrolovat, zda poslední znak v řetězci je znak zpětného lomítka:  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     Protože `strlen` MBCS neví, vrátí počet bajtů, nikoli počet znaků v řetězci vícebajtové. Také Upozorňujeme, že v některých znakové stránky (například 932) se\\"(0x5c poslední) je platný bajt (`sz` je řetězec C).  
  
     Jedním z možných řešení je přepište kód tímto způsobem:  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     Tento kód používá funkce znakové sady MBCS `_mbsrchr` a `_mbsinc`. Protože tyto funkce jsou podporující rozhraní MBCS, lze rozlišit mezi '\\'znak a druhý bajt'\\'. Kód provede některé akce, pokud jeho poslední znak v řetězci je s hodnotou null ('\0').  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)   
 [Přiřazení znaků](../text/character-assignment.md)