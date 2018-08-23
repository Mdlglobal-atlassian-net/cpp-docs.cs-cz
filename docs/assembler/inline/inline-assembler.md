---
title: Vložený Assembler | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assembler [C++]
- assembler [C++], inline
- assembly language [C++], inline
- inline assembler [C++]
- inline assembly [C++]
ms.assetid: 7e13f18f-3628-4306-8b81-4a6d09c043fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b45c55fbba37d27aa005480789cb490b891b103
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465009"
---
# <a name="inline-assembler"></a>Vložený assembler
**Specifické pro Microsoft**  
  
 Jazyk sestavení slouží různým účelům, například zvýšení rychlosti programu, snížení požadavků na paměť a ovládání hardwaru. Inline assembler můžete použít pro vložení instrukcí sestavení jazyka přímo do zdrojových programů v jazyce C a C++ bez nutnosti dodatečných kroků sestavení a propojení. Inline assembler je integrován v kompilátoru, takže nepotřebujete používat samostatný kompilátor, jako například Microsoft Macro Assembler (MASM).  
  
> [!NOTE]
>  Programy s kódem inline assembleru nejsou plně přenosné na jiné hardwarové platformy. Pokud navrhujete s ohledem na přenositelnost, vyhněte se použití inline assembleru.  
  
 Vložené sestavení není podporován ARM a x64 procesory.  Následující témata popisují způsob použití inline assembleru Visual C/C++ u procesorů x86:  
  
-   [Přehled inline assembleru](../../assembler/inline/inline-assembler-overview.md)  
  
-   [Výhody inline assembleru](../../assembler/inline/advantages-of-inline-assembly.md)  
  
-   [__asm](../../assembler/inline/asm.md)  
  
-   [Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)  
  
-   [Použití jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)  
  
-   [Použití a zachování registrů ve vloženém sestavení](../../assembler/inline/using-and-preserving-registers-in-inline-assembly.md)  
  
-   [Přechod na popisky ve vloženém sestavení](../../assembler/inline/jumping-to-labels-in-inline-assembly.md)  
  
-   [Volání funkcí jazyka C ve vloženém sestavení](../../assembler/inline/calling-c-functions-in-inline-assembly.md)  
  
-   [Volání funkcí jazyka C++ ve vloženém sestavení](../../assembler/inline/calling-cpp-functions-in-inline-assembly.md)  
  
-   [Definování bloků __asm jako maker v jazyce C](../../assembler/inline/defining-asm-blocks-as-c-macros.md)  
  
-   [Optimalizace vloženého sestavení](../../assembler/inline/optimizing-inline-assembly.md)  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní prvky kompilátoru a jazyk sestavení](../../intrinsics/compiler-intrinsics-and-assembly-language.md)   
 [Referenční dokumentace jazyka C++](../../cpp/cpp-language-reference.md)