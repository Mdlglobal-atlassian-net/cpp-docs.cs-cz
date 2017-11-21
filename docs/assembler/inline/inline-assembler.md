---
title: "Vložený Assembler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 22f428a21af037b86e063261003baf9849357c9e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="inline-assembler"></a>Vložený assembler
**Konkrétní Microsoft**  
  
 Jazyk sestavení slouží různým účelům, například zvýšení rychlosti programu, snížení požadavků na paměť a ovládání hardwaru. Inline assembler můžete použít pro vložení instrukcí sestavení jazyka přímo do zdrojových programů v jazyce C a C++ bez nutnosti dodatečných kroků sestavení a propojení. Inline assembler je integrován v kompilátoru, takže nepotřebujete používat samostatný kompilátor, jako například Microsoft Macro Assembler (MASM).  
  
> [!NOTE]
>  Programy s kódem inline assembleru nejsou plně přenosné na jiné hardwarové platformy. Pokud navrhujete s ohledem na přenositelnost, vyhněte se použití inline assembleru.  
  
 Vnořené sestavení nepodporuje ARM a [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] procesory.  Následující témata popisují způsob použití inline assembleru Visual C/C++ u procesorů x86:  
  
-   [Přehled inline assembleru](../../assembler/inline/inline-assembler-overview.md)  
  
-   [Výhody vloženého sestavení](../../assembler/inline/advantages-of-inline-assembly.md)  
  
-   [__asm](../../assembler/inline/asm.md)  
  
-   [Použití jazyka sestavení v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)  
  
-   [Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)  
  
-   [Použití a zachování registrů ve vloženém sestavení](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)  
  
-   [Přechod na popisky ve vloženém sestavení](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)  
  
-   [Volání funkcí jazyka C ve vloženém sestavení](../../assembler/inline/calling-c-functions-in-inline-assembly.md)  
  
-   [Volání funkcí jazyka C++ ve vloženém sestavení](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)  
  
-   [Definování bloků __asm jako maker jazyka C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)  
  
-   [Optimalizace vloženého sestavení](../../assembler/inline/optimizing-inline-assembly.md)  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru a jazyk sestavení](../../intrinsics/compiler-intrinsics-and-assembly-language.md)   
 [Referenční příručka jazyka C++](../../cpp/cpp-language-reference.md)