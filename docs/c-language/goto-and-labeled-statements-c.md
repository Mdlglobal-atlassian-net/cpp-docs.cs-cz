---
title: "příkaz goto a Labeled Statements (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: goto
dev_langs: C++
helpviewer_keywords:
- labeled statement
- statements, labeled
- goto keyword [C]
ms.assetid: 3d0473dc-4b18-4fcc-9616-31a38499d7d7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea0543a13d16850be4259d2d93f763dd0edcbda3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="goto-and-labeled-statements-c"></a>Příkaz goto a příkazy s popiskem (C)
`goto` Příkaz převede ovládací prvek popisek. Daný popisek se musí nacházet ve stejné funkce a může vyskytovat před pouze jeden příkaz ve stejné funkci.  
  
## <a name="syntax"></a>Syntaxe  
 *příkaz*:  
 *příkaz s popiskem*  
  
 *jump – příkaz*  
  
 *příkaz přechod*:  
 **Goto***identifikátor***;**   
  
 *příkaz s popiskem*:  
 *identifikátor***:***– příkaz*   
  
 Má smysl pouze pro příkaz štítek `goto` příkaz; v jiné kontextu, je proveden příkaz s popiskem bez ohledu na popisku.  
  
 A *přechod příkaz* se musí nacházet ve stejné funkce a může se objevit před pouze jeden příkaz ve stejné funkci. Sada *identifikátor* následující názvy `goto` má svou vlastní obor názvů, takže názvy nezpůsobují konflikt s další identifikátory. Popisky nelze deklarovat. V tématu [obory názvů](../c-language/name-spaces.md) Další informace.  
  
 Je vhodné programování styl použitý **zalomení**, **pokračovat**, a `return` příkaz preference a `goto` kdykoli je to možné. Vzhledem k tomu **zalomení** příkaz ukončí pouze z jedné úrovně smyčky, `goto` může být nutné pro ukončení smyčky z v rámci hluboko vložené smyčky.  
  
 Tento příklad ukazuje `goto` příkaz:  
  
```  
// goto.c  
#include <stdio.h>  
  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 3; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 5 )  
                goto stop;  
        }  
    }  
  
    /* This message does not print: */  
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop: printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
 V tomto příkladu `goto` příkaz předá řízení bod s názvem bez přípony `stop` při `i` rovná 5.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../c-language/statements-c.md)