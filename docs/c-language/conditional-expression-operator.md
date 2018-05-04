---
title: Operátor podmíněného výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- conditional operators
- operators [C++], conditional
- expressions [C++], conditional
ms.assetid: c4f1a5ca-0844-44a7-a384-eca584d4e3dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f3bead2a40e38698534e433d8e4289eb8da4dc9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="conditional-expression-operator"></a>Operátor podmíněného výrazu
C má jeden Ternární operátor: operátor podmíněného výrazu (**?:**).  
  
## <a name="syntax"></a>Syntaxe  
 *podmíněného výrazu*:  
 *logický výraz OR*  
  
 *výraz logické OR***?**   *výraz***:***podmíněného výrazu*   
  
 *Logický výraz OR* musí být celé číslo, číslo s plovoucí čárkou nebo ukazatel typu. Vyhodnotí z hlediska jeho ekvivalenční na hodnotu 0. Následuje bod sekvence *logický výraz OR*. Vyhodnocení operandy probíhá následujícím způsobem:  
  
-   Pokud *logický výraz OR* není rovno 0, *výraz* vyhodnotí. Výsledek vyhodnocení výrazu je dána nonterminal *výraz*. (To znamená *výraz* vyhodnotí pouze v případě *logický výraz OR* hodnotu true.)  
  
-   Pokud *logický výraz OR* rovná 0, *podmíněného výrazu* vyhodnotí. Výsledkem výrazu je hodnota *podmíněného výrazu*. (To znamená *podmíněného výrazu* vyhodnotí pouze v případě *logický výraz OR* je false.)  
  
 Všimněte si, že buď *výraz* nebo *podmíněného výrazu* vyhodnotí, ale ne pomocí obou.  
  
 Typ výsledku podmíněného operace závisí na typu *výraz* nebo *podmíněného výrazu* operand následujícím způsobem:  
  
-   Pokud *výraz* nebo *podmíněného výrazu* má integrální nebo plovoucí typu (jejich typy může být jiný), operátor provede obvyklé aritmetické převody. Typ výsledku je typ operandy po převodu.  
  
-   Pokud oba *výraz* a *podmíněného výrazu* mít stejnou strukturu, union nebo ukazatel typu, typ výsledek je stejného typu struktury, sjednocení nebo ukazatel.  
  
-   Pokud oba operandy typu `void`, výsledek obsahuje typ `void`.  
  
-   Pokud buď operand je ukazatel na objekt jakéhokoli typu a dalších operand je ukazatel na `void`, má ukazatel na objekt jsou převedeny na ukazatel na `void` a výsledkem je ukazatel na `void`.  
  
-   Pokud má jedna *výraz* nebo *podmíněného výrazu* ukazatel a dalších operand je konstantní výraz s hodnotou 0, typ výsledku je ukazatel typu.  
  
 Typ porovnání pro ukazatele, jakýkoli typ kvalifikátory (**const** nebo `volatile`) v typu, ke kterému jsou body ukazatel zanedbatelné, ale výsledný typ dědí kvalifikátory z obou součástí zásad správy.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ukazují použití podmíněný operátor:  
  
```  
j = ( i < 0 ) ? ( -i ) : ( i );  
```  
  
 Tento příklad přiřadí absolutní hodnotu `i` k `j`. Pokud `i` je menší než 0, `-i` je přiřazena k `j`. Pokud `i` je větší než nebo rovno 0, `i` je přiřazena k `j`.  
  
```  
void f1( void );  
void f2( void );  
int x;  
int y;  
    .  
    .  
    .  
( x == y ) ? ( f1() ) : ( f2() );  
```  
  
 V tomto příkladu dvě funkce `f1` a `f2`a dvě proměnné, `x` a `y`, jsou deklarované. Dále v programu, pokud dvě proměnné, které mají stejnou hodnotu, funkce `f1` je volána. V opačném `f2` je volána.  
  
## <a name="see-also"></a>Viz také  
 [Podmíněný operátor: ?:](../cpp/conditional-operator-q.md)