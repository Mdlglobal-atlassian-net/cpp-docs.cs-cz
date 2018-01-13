---
title: "C relační operátory a operátory rovnosti | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- relational operators, syntax
- equality operator
- operators [C], equality
- equality operator, syntax
- operators [C], relational
ms.assetid: c89a3815-a65e-4e0d-8333-0e8dc7fdb30b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6860198b9acce372b710e819a17f534e793f1ead
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="c-relational-and-equality-operators"></a>Relační operátory a operátory rovnosti jazyka C
Binární relační operátory a operátory rovnosti porovnat jejich první operand jejich Druhý operand k testování platnosti zadané relaci. Výsledek relační výrazu je 1, pokud je otestované vztah true a 0, pokud je hodnota false. Typ výsledku je `int`.  
  
 **Syntaxe**  
  
 *relační výraz*:  
 *SHIFT – výraz*  
  
 *relační výraz***\<***posunutí – výraz*   
  
 *relační výraz***>***posunutí – výraz*   
  
 *relační výraz***\<=***posunutí – výraz*   
  
 *relační výraz***>=***posunutí – výraz*   
  
 *výraz rovnosti*:  
 *relační výraz*  
  
 *výraz rovnosti***==***relační výraz*   
  
 *výraz rovnosti***! =***relační výraz*   
  
 Operátory rovnosti a relační test následující vztahů:  
  
|Operátor|Vztah testována|  
|--------------|-------------------------|  
|**\<**|První operand menší než druhý operand|  
|**>**|První operand větší než druhý operand|  
|**\<=**|První operand menší než nebo rovna Druhý operand|  
|**>=**|První operand větší než nebo rovna hodnotě Druhý operand|  
|`==`|První operand rovna Druhý operand|  
|`!=`|První operand není rovno Druhý operand|  
  
 První čtyři operátory v seznamu výš mít vyšší prioritu než operátory rovnosti (`==` a `!=`). Přečtěte si informace přednost v tabulce [přednost a operátory jazyka C Asociativnost](../c-language/precedence-and-order-of-evaluation.md).  
  
 Operandy může mít typ celé číslo, číslo s plovoucí čárkou nebo ukazatel. Typy operandy může lišit. Relační operátory provádět obvyklé aritmetické převody na typ plovoucí a integrální operandy. Kromě toho můžete použít následující kombinace typů operand s relační operátory a operátory rovnosti:  
  
-   Ukazatelé na stejný typ může být operandy všechny relační nebo operátor rovnosti. Pro rovnosti (`==`) a nerovnosti (`!=`) operátory, výsledkem porovnání označuje, zda dva odkazy adres stejné místo v paměti. Pro relační operátory (**\<**,  **>** ,  **\<** =, a  **>** =), výsledkem porovnání označuje relativní pozici adres dvě paměti objektů na odkazuje. Relační operátory porovnání pouze posun.  
  
     Porovnání ukazatelů je určená jenom pro součástí stejného objektu. Pokud následující ukazatele odkazovat na členy pole, je ekvivalentní k porovnání odpovídající dolní indexy porovnání. Je adresa první prvek pole "menší než" na adresu posledním elementem. V případě struktury jsou ukazatelé na členy struktura deklarovaný později "větší než" ukazatelé na členy deklarovaný dříve ve struktuře. Ukazatelé na členy stejné unie jsou stejné.  
  
-   Hodnota ukazatele je možné porovnávat konstantní hodnotu 0 pro rovnosti (`==`) nebo nerovnosti (`!=`). Ukazatel s hodnotou 0 se označuje jako "null" ukazatel; To znamená ho neodkazuje na platný paměti umístění.  
  
-   Operátory rovnosti stejným pravidlům jako relační operátory, ale povolit další možnosti: ukazatel je možné porovnávat celočíselné konstantní výraz s hodnotou 0, nebo ukazatel na `void`. Pokud jsou dva ukazatele obou ukazatelé s hodnotou null, porovnejte jako rovnocenné. Operátory rovnosti porovnat segmentu a posun.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ilustrují relační operátory a operátory rovnosti.  
  
```  
int x = 0, y = 0;  
if ( x < y )  
```  
  
 Protože `x` a `y` jsou stejné, výsledkem je hodnota 0, výraz v tomto příkladu.  
  
```  
char array[10];  
char *p;  
  
for ( p = array; p < &array[10]; p++ )  
    *p = '\0';  
```  
  
 Fragment v tomto příkladu nastaví každý element `array` konstantu znak hodnoty null.  
  
```  
enum color { red, white, green } col;  
   .  
   .  
   .  
   if ( col == red )  
   .  
   .  
   .  
```  
  
 Tyto příkazy deklarovat proměnnou výčtu s názvem `col` ke značce `color`. V každém okamžiku může obsahovat proměnné celočíselnou hodnotu 0, 1 nebo 2, který představuje jeden z elementů – výčet sady `color`: červená barva, prázdný nebo zelená, v uvedeném pořadí. Pokud `col` obsahuje 0 při **Pokud** spustit příkaz, všechny příkazy v závislosti na **Pokud** bude proveden.  
  
## <a name="see-also"></a>Viz také  
 [Relační operátory: \<, >, \<=, a > =](../cpp/relational-operators-equal-and-equal.md)   
 [Operátory rovnosti: == a !=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)