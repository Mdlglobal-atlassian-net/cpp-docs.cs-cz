---
title: Souhrn doby platnosti a viditelnosti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8e8c676a950979906bbc741679735ba452baec18
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="summary-of-lifetime-and-visibility"></a>Souhrn doby platnosti a viditelnosti
V následující tabulce je uveden seznam doby platnosti a viditelnosti charakteristiky pro většinu identifikátory. První tři sloupce zadejte atributy, které definují doby platnosti a viditelnosti. Identifikátor s atributy poskytují první tři sloupce má doby platnosti a viditelnosti, které jsou ve sloupci čtvrté a páté. V tabulce nepopisuje všechny možné případy. Odkazovat na [třídy úložiště](../c-language/c-storage-classes.md) Další informace.  
  
### <a name="summary-of-lifetime-and-visibility"></a>Souhrn doby platnosti a viditelnosti  
  
|Atributy:<br /><br /> úroveň|Položka|Třídy úložiště<br /><br /> Specifikátor|Výsledek:<br /><br /> Doba platnosti|Viditelnost|  
|---------------------------|----------|----------------------------------|--------------------------|----------------|  
|Rozsah souboru|Definicí proměnné|**statické**|Globální|Zbývající část zdrojový soubor, ve kterém byly provedeny|  
||Deklarace proměnné|`extern`|Globální|Zbývající část zdrojový soubor, ve kterém byly provedeny|  
||Prototyp funkce a definice|**statické**|Globální|Jeden zdrojový soubor|  
||Prototyp funkce|`extern`|Globální|Zbývající část zdrojový soubor|  
|Rozsah bloku|Deklarace proměnné|`extern`|Globální|Blok|  
||Definicí proměnné|**statické**|Globální|Blok|  
||Definicí proměnné|**Automatické** nebo **zaregistrovat**|místní|Blok|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad ilustruje bloky, vnoření a viditelnost proměnných:  
  
### <a name="code"></a>Kód  
  
```  
// Lifetime_and_Visibility.c  
  
#include <stdio.h>  
  
int i = 1;  // i defined at external level  
  
int main()  // main function defined at external level  
{  
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)  
    {                                 // Begin first nested block  
        int i = 2, j = 3;          // i and j defined at internal level  
        printf_s( "%d %d\n", i, j );  // Prints 2, 3  
        {                             // Begin second nested block  
            int i = 0;                // i is redefined  
            printf_s( "%d %d\n", i, j ); // Prints 0, 3  
        }                             // End of second nested block  
        printf_s( "%d\n", i );        // Prints 2 (outer definition  
                                      //  restored)  
    }                                 // End of first nested block  
    printf_s( "%d\n", i );            // Prints 1 (external level  
                                      // definition restored)  
    return 0;  
}   
```  
  
### <a name="comments"></a>Komentáře  
 V tomto příkladu jsou čtyři úrovně viditelnosti: externí úrovni a úrovně tři bloku. Hodnoty jsou vytištěny na obrazovku, jak je uvedeno v komentářích následující každý příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Doba platnosti, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md)