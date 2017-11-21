---
title: Inline Assembler (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5456b9c750a7aba33282f95097826362434e9840
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="inline-assembler-c"></a>Vložený assembler (C)
**Konkrétní Microsoft**  
  
 Vložený assembler umožňuje vložení instrukcí sestavení jazyka přímo do zdrojových programů v jazyce C bez nutnosti dodatečných kroků sestavení a propojení. Vložený assembler je integrován v kompilátoru, takže nepotřebujete používat samostatný kompilátor, jako například Microsoft Macro Assembler (MASM).  
  
 Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Kód vloženého sestavení může použít název proměnné nebo funkce jazyka C, který je v rozsahu, takže jej lze snadno integrovat do kódu jazyka C programu. A protože lze kód sestavení kombinovat s příkazy jazyka C, lze provádět úkoly, které jsou v samostatném jazyce C náročné nebo nemožné.  
  
 Klíčové slovo `__asm` vyvolá vložený assembler a může se objevit všude, kde lze použít příkaz jazyka C. Se nemůže objevit samostatně. Musí být následováno instrukci sestavení skupinu instrukce uzavřené do složených závorek, nebo v každém, prázdný pár složené závorky. Termín "`__asm` bloku" zde označují jakýkoliv pokyn nebo skupiny pokynů, zda v závorkách.  
  
 Kód níže je jednoduchý blok `__asm` uzavřený ve složených závorkách. (Kód je posloupnost vlastní funkce sekvence prologu.)  
  
```  
__asm  
{  
   push ebp  
   mov  ebp, esp  
   sub  esp, __LOCAL_SIZE  
}  
```  
  
 Alternativně můžete umístit `__asm` před každou instrukci sestavení:  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 Protože klíčové slovo `__asm` představuje oddělovač výrazů, lze také umístit pokyny sestavení na stejný řádek:  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE   
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Atributy funkce](../c-language/function-attributes.md)