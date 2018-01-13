---
title: "Obvyklé aritmetické převody | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- arithmetic conversions [C++]
- type conversion [C++], arithmetic
- operators [C], arithmetic conversions
- data type conversion [C++], arithmetic
- conversions [C++], arithmetic
- arithmetic operators [C++], type conversions
ms.assetid: bfa49803-0efd-45d0-b987-111412a140d7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a73da6d96b0dc03fa3f4c4807d6a2dff4fef2879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="usual-arithmetic-conversions"></a>Obvyklé aritmetické převody
Většina operátory jazyka C provést převody typů a dovést operandy výrazu do stejného typu nebo rozšířit krátké hodnoty použít v operacích počítač velikosti celé číslo. Převody provádí operátory jazyka C závisí na konkrétní operátor a typ operandu nebo operandy. Řada operátorů se ale provést převody podobně jako u operandů plovoucí a integrální typy. Tyto převody se označují jako "aritmetické převody." Převod hodnoty operand na kompatibilní typ. způsobí, že žádná změna na jeho hodnotu.  
  
 Aritmetické převody shrnuté níž se nazývají "obvyklé aritmetické převody." Tyto kroky platí pouze pro binární operátory, které očekávají aritmetické typu. Účelem je yield společný typ, který je i typ výsledku. Pokud chcete zjistit, které převody ve skutečnosti provádět, kompilátor platí následující algoritmus pro binárních operací ve výrazu. Následující postup nejsou pořadí priorit.  
  
1.  Pokud je buď operand typu `long double`, jiné operand je převést na typ `long double`.  
  
2.  Pokud není splněna podmínka výše a je buď operand typu **dvojité**, jiné operand je převést na typ **dvojité**.  
  
3.  Pokud nejsou splněny výše uvedené dvě podmínky a je buď operand typu **float**, jiné operand je převést na typ **float**.  
  
4.  Pokud nejsou splněné výše uvedených tří podmínek (žádná z operandy jsou typy s plovoucí čárkou), pak integrální převody jsou prováděny v operandy následovně:  
  
    -   Pokud je buď operand typu `unsigned long`, jiné operand je převést na typ `unsigned long`.  
  
    -   Pokud není splněna podmínka výše a je buď operand typu **dlouho** a dalších typu `unsigned int`, oba operandy se převedou na typ `unsigned long`.  
  
    -   Pokud výše uvedené dvě podmínky nejsou splněné, a je buď operand typu **dlouho**, jiné operand je převést na typ **dlouho**.  
  
    -   Pokud nejsou splněné výše uvedených tří podmínek, a je buď operand typu `unsigned int`, jiné operand je převést na typ `unsigned int`.  
  
    -   Pokud žádná z výše uvedených podmínek jsou splněny, jsou oba operandy převést na typ `int`.  
  
 Následující kód ukazuje tato pravidla převodu:  
  
```  
float   fVal;  
double  dVal;  
int   iVal;  
unsigned long ulVal;  
  
dVal = iVal * ulVal; /* iVal converted to unsigned long  
                      * Uses step 4.  
                      * Result of multiplication converted to double   
                      */  
dVal = ulVal + fVal; /* ulVal converted to float  
                      * Uses step 3.  
                      * Result of addition converted to double   
                      */   
```  
  
## <a name="see-also"></a>Viz také  
 [Operátory jazyka C](../c-language/c-operators.md)