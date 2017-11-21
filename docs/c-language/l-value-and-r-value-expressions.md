---
title: "L-Value a R-Value výrazy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c2d37d95a20ac2a71c50d468a7793ae4ab8956f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="l-value-and-r-value-expressions"></a>Výrazy hodnot L-Value a R-Value
Výrazy, které odkazují na umístění v paměti, se nazývají výrazy „l-hodnota“. Hodnotu l reprezentuje hodnotu "Lokátor" v oblasti úložiště, nebo hodnotu "left" zdání, může se objevit na levé straně znaménkem rovnosti (**=**). L-hodnoty jsou často identifikátory.  
  
 Výrazy odkazující na upravitelná umístění se nazývají „upravitelné l-hodnoty“. Upravitelnými l hodnota nemůže mít typ pole, neúplné typ nebo typ s **const** atribut. Struktury a sjednocení jako upravitelnými hodnoty l, nesmí mít žádné členy s **const** atribut. Název identifikátoru označuje umístění úložiště, zatímco hodnota proměnné je hodnota uložená v tomto umístění.  
  
 Identifikátor je upravitelná l-hodnota, odkazuje-li na umístění v paměti a je-li její typ aritmetický, struktura, sjednocení nebo ukazatel. Například pokud je `ptr` ukazatel na oblast úložiště, pak je `*ptr` upravitelná l-hodnota, jež určuje oblast úložiště, na které `ptr` ukazuje.  
  
 Jakýkoli z těchto výrazů jazyka C může být výrazem l-hodnoty:  
  
-   Identifikátor celočíselného typu, typu s plovoucí desetinnou čárkou, typu ukazatele, struktury nebo sjednocení  
  
-   Dolní index (**[]**) výraz, který není vyhodnocen pole  
  
-   Výraz výběru členů ( **->**  nebo **.**)  
  
-   Unární indirection (**\***) výraz, který není odkaz na pole  
  
-   Výraz l-hodnoty v závorkách  
  
-   A **const** objektu (neupravitelnými l hodnota)  
  
 Pojem „r-hodnota“ se někdy používá k popisu hodnoty výrazu a pro jeho odlišení od l-hodnoty. Všechny l-hodnoty jsou r-hodnotami, ale ne všechny r-hodnoty jsou l-hodnotami.  
  
 **Konkrétní Microsoft**  
  
 Jazyk Microsoft C zahrnuje rozšíření standardu ANSI C, které umožňuje přetypovat l-hodnoty pro použití jako l-hodnoty, pokud není velikost objektu zvětšena pomocí přetypování. (Viz [převody přetypování](../c-language/type-cast-conversions.md) Další informace.) Tuto funkci znázorňuje následující příklad:  
  
```  
char *p ;  
short  i;  
long l;  
  
(long *) p = &l ;       /* Legal cast   */  
(long) i = l ;          /* Illegal cast */  
```  
  
 Výchozí nastavení pro Microsoft C je, že jsou povolené rozšíření Microsoft. Použijte /Za – možnost kompilátoru zakázání tyto rozšíření.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Operandy a výrazy](../c-language/operands-and-expressions.md)