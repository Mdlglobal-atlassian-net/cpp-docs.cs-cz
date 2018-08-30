---
title: Výrazy L-Value a R-Value | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8003997d82c59d42813d7852e6c3fadb8f12fb26
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208905"
---
# <a name="l-value-and-r-value-expressions"></a>Výrazy hodnot L-Value a R-Value
Výrazy, které odkazují na umístění v paměti, se nazývají výrazy „l-hodnota“. L hodnota představuje hodnotu oblasti úložiště "lokátoru" nebo "levou" hodnotu, zdání, může se objevit na levé straně znaménka rovnosti (**=**). L-hodnoty jsou často identifikátory.  
  
 Výrazy odkazující na upravitelná umístění se nazývají „upravitelné l-hodnoty“. Upravitelná l hodnota nemůže mít typ pole, neúplný typ nebo typ s **const** atribut. Struktury a sjednocení bude upravitelná l hodnotami, nesmějí obsahovat žádné členy s **const** atribut. Název identifikátoru označuje umístění úložiště, zatímco hodnota proměnné je hodnota uložená v tomto umístění.  
  
 Identifikátor je upravitelná l-hodnota, odkazuje-li na umístění v paměti a je-li její typ aritmetický, struktura, sjednocení nebo ukazatel. Například pokud je `ptr` ukazatel na oblast úložiště, pak je `*ptr` upravitelná l-hodnota, jež určuje oblast úložiště, na které `ptr` ukazuje.  
  
 Jakýkoli z těchto výrazů jazyka C může být výrazem l-hodnoty:  
  
-   Identifikátor celočíselného typu, typu s plovoucí desetinnou čárkou, typu ukazatele, struktury nebo sjednocení  
  
-   Index (**[] č.**) výraz, který není vyhodnocen na pole  
  
-   Výraz výběru členů (**->** nebo **.**)  
  
-   Unární indirection (<strong>\**</strong>) výraz, který není odkaz na pole  
  
-   Výraz l-hodnoty v závorkách  
  
-   A **const** objekt (neupravitelná l hodnota)  
  
 Pojem „r-hodnota“ se někdy používá k popisu hodnoty výrazu a pro jeho odlišení od l-hodnoty. Všechny l-hodnoty jsou r-hodnotami, ale ne všechny r-hodnoty jsou l-hodnotami.  
  
 **Specifické pro Microsoft**  
  
 Jazyk Microsoft C zahrnuje rozšíření standardu ANSI C, které umožňuje přetypovat l-hodnoty pro použití jako l-hodnoty, pokud není velikost objektu zvětšena pomocí přetypování. (Viz [převody přetypování](../c-language/type-cast-conversions.md) Další informace.) Tuto funkci znázorňuje následující příklad:  
  
```  
char *p ;  
short  i;  
long l;  
  
(long *) p = &l ;       /* Legal cast   */  
(long) i = l ;          /* Illegal cast */  
```  
  
 Výchozí nastavení pro Microsoft C je, že jsou povolena rozšíření společnosti Microsoft. Pomocí možnosti kompilátoru /Za pro zákaz těchto rozšíření.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Operandy a výrazy](../c-language/operands-and-expressions.md)