---
title: "Deklarátor a deklarace proměnné | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d9b7ce4895d51c50185c5262664dc478af62cfa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="declarators-and-variable-declarations"></a>Deklarátor a deklarace proměnné
Zbývající část tohoto oddílu popisuje formuláře a význam deklarace pro typy proměnných souhrnu v tomto seznamu. Konkrétně zbývající části popisují, jak deklarovat následující:  
  
|Typ proměnné|Popis|  
|----------------------|-----------------|  
|[Jednoduché proměnné](../c-language/simple-variable-declarations.md)|Jednou hodnotou proměnné s typem integrální nebo s plovoucí desetinnou čárkou|  
|[Pole](../c-language/array-declarations.md)|Proměnné se skládá z kolekci elementů stejného typu|  
|[Ukazatele](../c-language/pointer-declarations.md)|Proměnné, které bod na jiné proměnné a obsahovat proměnné umístění (ve formě adresy) namísto hodnoty|  
|[Proměnné – výčet](../c-language/c-enumeration-declarations.md)|Jednoduché proměnné s integrální zadejte tuto hodnotu uchování jeden ze sady s názvem celočíselné konstanty|  
|[Struktury](../c-language/structure-declarations.md)|Proměnné se skládá z kolekce hodnot, které může mít různé typy|  
|[Sjednocení](../c-language/union-declarations.md)|Proměnné se skládá z několika hodnoty různých typů, které zabírají stejnému adresnímu prostoru úložiště|  
  
 Deklarátor je součástí deklaraci, která určuje název, který je potřeba zavést do programu. Modifikátory může zahrnovat například  **\***  (ukazatel-k) a všechny klíčová slova konvence volání Microsoft.  
  
 **Konkrétní Microsoft**  
  
 V deklarátor  
  
```  
__declspec(thread) char *var;  
```  
  
 `char`je specifikátor typu `__declspec(thread)` a `*` jsou modifikátory, a `var` je název identifikátoru.  
  
 **Konkrétní Microsoft END**  
  
 Deklarátory použijete deklarovat pole hodnot ukazatelé na hodnoty a funkce, které vracejí hodnoty zadaného typu. Deklarátory se zobrazí v poli a ukazatel deklarace, které jsou popsané dál v této části.  
  
## <a name="syntax"></a>Syntaxe  
 *deklarátor*:  
 &nbsp;&nbsp;*ukazatel*<sub>opt</sub> *přímo deklarátor*  
  
 *deklarátor přímo*:  
 &nbsp;&nbsp;*identifikátor*  
 &nbsp;&nbsp;**(***deklarátor***)**   
 &nbsp;&nbsp;*deklarátor přímo***[***konstantní výraz*<sub>opt</sub> **]**   
 &nbsp;&nbsp;*deklarátor přímo***(***seznam parametrů typu***)**   
 &nbsp;&nbsp;*deklarátor přímo***(***seznam identifikátorů*<sub>opt</sub> **)**   
  
 *ukazatel*:  
 &nbsp;&nbsp;**\****seznam typů kvalifikátor*<sub>opt</sub>  
 &nbsp;&nbsp;**\****seznam typů kvalifikátor*<sub>opt</sub> *ukazatele*  
  
 *seznam typů kvalifikátor*:  
 &nbsp;&nbsp;*Kvalifikátor typu*  
 &nbsp;&nbsp;*seznam typů kvalifikátor kvalifikátor typu*  
  
> [!NOTE]
>  Další informace o syntaxi *deklarace* v [přehled deklarace](../c-language/overview-of-declarations.md) nebo [souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md) pro syntaxi, která odkazuje *deklarátor*.  
  
 Když deklarátor se skládá z identifikátorem beze změny, položka je deklarovaná má základní typ. Pokud se hvězdička (**\***) se zobrazí vlevo identifikátoru, typ je upravit tak, aby ukazatel typu. Pokud je identifikátor následovaný hranatými závorkami (**[]**), typ je upravit tak, aby typ pole. Pokud identifikátor následuje závorky, typ je upravit tak, aby typ funkce. Další informace o interpretaci Priorita v rámci deklarace najdete v tématu [interpretace další složité Deklarátory](../c-language/interpreting-more-complex-declarators.md).  
  
 Každý deklarátor deklaruje alespoň jeden identifikátor. Deklarátor musí obsahovat specifikátor typu jako úplné deklarace. Specifikátor typu dává typ elementů typu pole, typ objektu používala ukazatel typu nebo návratový typ funkce.  
  
 [Pole](../c-language/array-declarations.md) a [ukazatel](../c-language/pointer-declarations.md) deklarace jsou podrobněji popsána dále v této části. Následující příklady uvádějí pár jednoduchých formulářů deklarátorů:  
  
```  
int list[20]; // Declares an array of 20 int values named list  
char *cp;     // Declares a pointer to a char value  
double func( void ); // Declares a function named func, with no   
                     // arguments, that returns a double value  
int *aptr[10] // Declares an array of 10 pointers  
```  
  
 **Konkrétní Microsoft**  
  
 Kompilátor Microsoft C neomezuje počet deklarátory, které můžete upravit aritmetické, struktura nebo typu union. Číslo je omezena pouze dostupné paměti.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)