---
title: "Přehled vloženého assembleru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7733398f5a444fa5e7461ea52295624d6d16f9a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="inline-assembler-overview"></a>Přehled inline assembleru
**Konkrétní Microsoft**  
  
 Vložený assembler umožňuje vložit pokyny jazyka sestavení do zdrojové programy C a C++ bez dodatečné kroky sestavení a odkaz. Vložený assembler je integrován v kompilátoru, takže nepotřebujete používat samostatný kompilátor, jako například Microsoft Macro Assembler (MASM).  
  
 Protože vložený assembler nevyžaduje samostatné kroky sestavení a propojení, je pohodlnější než samostatný assembler. Kód vnořeného sestavení můžete použít všechny jazyka C nebo C++ proměnné nebo funkce název, který je v oboru, je snadné provést integraci s vaším programem C a C++ kódem. A protože kódu sestavení můžete kombinovat s příkazy jazyka C a C++, ho můžete provést úlohy, které jsou komplikované nebo dokonce znemožňují v jazyka C nebo C++ samostatně.  
  
 [__Asm](../../assembler/inline/asm.md) – klíčové slovo vyvolá vloženého assembleru a může vyskytovat kdekoli je právní příkaz jazyka C nebo C++. Se nemůže objevit samostatně. Musí být následováno instrukci sestavení skupinu instrukce uzavřené do složených závorek, nebo v každém, prázdný pár složené závorky. Termín "`__asm` bloku" zde označují jakýkoliv pokyn nebo skupiny pokynů, zda v závorkách.  
  
 Následující kód je jednoduchý `__asm` bloku uzavřené do složených závorek. (Kód je posloupnost vlastní funkce sekvence prologu.)  
  
```  
// asm_overview.cpp  
// processor: x86  
void __declspec(naked) main()  
{  
    // Naked functions must provide their own prolog...  
    __asm {  
        push ebp  
        mov ebp, esp  
        sub esp, __LOCAL_SIZE  
    }  
  
    // ... and epilog  
    __asm {  
        pop ebp  
        ret  
    }  
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
 [Vložený Assembler](../../assembler/inline/inline-assembler.md)