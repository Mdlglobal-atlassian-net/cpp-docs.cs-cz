---
title: "Zadejte kvalifikátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- volatile keyword [C], type qualifier
- type qualifiers
- volatile keyword [C]
- qualifiers for types
- const keyword [C]
- memory, access using volatile
- volatile keyword [C], type specifier
ms.assetid: bb4c6744-1dd7-40a8-b4eb-f5585be30908
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c4fad93505a5778c23171b413654624a32e825b2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="type-qualifiers"></a>Kvalifikátory typu
Kvalifikátory typu jednu ze dvou vlastností předáte identifikátor. **Const** kvalifikátor typu deklaruje objekt tak, aby se neupravitelnými. `volatile` Kvalifikátor typu deklaruje položku, jehož hodnota může být změněna legálně cokoli, co je nad rámec tohoto programu, ve kterém se zobrazí, jako je například souběžně spuštěných vláken ovládacího prvku.  
  
 Kvalifikátory, zadejte dva **const** a `volatile`, může vyskytovat pouze jednou v deklaraci. Kvalifikátory typu mohou objevit všechny specifikace typu; však nemůže být použit po první čárkou v deklaraci více položek. Například následující deklarace jsou právní:  
  
```  
typedef volatile int VI;  
const int ci;  
```  
  
 Tyto deklarace nejsou právní:  
  
```  
typedef int *i, volatile *vi;  
float f, const cf;     
```  
  
 Kvalifikátory typu jsou relevantní jenom v případě, že přístup k identifikátory jako hodnoty l ve výrazech. V tématu [L-Value a R-Value výrazy](../c-language/l-value-and-r-value-expressions.md) informace o hodnoty l a výrazy.  
  
## <a name="syntax"></a>Syntaxe  
 *Kvalifikátor typu*:  
 **constvolatile**  
  
 Toto jsou právní **const** a `volatile` deklarace:  
  
```  
int const *p_ci;       /* Pointer to constant int */  
int const (*p_ci);     /* Pointer to constant int */  
int *const cp_i;       /* Constant pointer to int */  
int (*const cp_i);     /* Constant pointer to int */  
int volatile vint;     /* Volatile integer        */  
```  
  
 Obsahuje-li specifikace typu pole kvalifikátory typu, je kvalifikovaný elementu, nikoli typ pole. Obsahuje-li specifikace typu funkce kvalifikátory, chování nedefinovaný. Ani `volatile` ani **const** ovlivňuje aritmetické vlastnosti objektu nebo rozsah hodnot.  
  
 Tento seznam popisuje, jak používat **const** a `volatile`.  
  
-   **Const** – klíčové slovo lze použít k úpravě libovolného typu základní nebo agregační nebo ukazatel na objekt jakéhokoli typu nebo `typedef`. Pokud položku je deklarovaný s pouze **const** kvalifikátor typu, jako je provedena její typ **const int**. A **const** proměnná může být inicializována nebo mohou být umístěny v oblasti úložiště jen pro čtení. **Const** – klíčové slovo je užitečné pro deklarování ukazatele na **const** vzhledem k tomu, že to vyžaduje funkci nechcete změnit ukazatel žádným způsobem.  
  
-   Kompilátor předpokládá, že, v libovolném bodě v programu, `volatile` proměnné je přístupná neznámé procesem, který používá nebo upraví jeho hodnotu. Proto bez ohledu na zadaný v příkazu optimalizace řádek kódu pro každé přiřazení nebo odkazovat z `volatile` proměnná musí být generovány i v případě, že se zdá, že nemají žádný vliv.  
  
     Pokud `volatile` použitý samostatně, `int` se předpokládá. `volatile` Specifikátor typu je možné poskytnout spolehlivý přístup k umístění speciální paměti. Použití `volatile` s datových objektů, které může získat přístup nebo změnit signál obslužné rutiny, souběžně prováděných programů nebo speciální hardware, jako například mapované paměti zaregistruje řízení vstupně-výstupní operace. Je možné deklarovat proměnnou jako `volatile` pro své životnosti, nebo může odevzdat jeden odkaz na být `volatile`.  
  
-   Položka může být obě **const** a `volatile`, v takovém případě položky nelze je změnit legálně vlastní program, ale je možné upravovat asynchronní proces.  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)