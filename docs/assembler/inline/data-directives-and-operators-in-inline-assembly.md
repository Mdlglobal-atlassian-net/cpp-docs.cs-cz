---
title: "Direktivy a operátory ve vloženém sestavení dat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data directives [C++]
- __asm keyword [C++], referencing limitations
- MASM (Microsoft Macro Assembler), directives
- directives [C++], MASM
- MASM (Microsoft Macro Assembler), structures
- operators [MASM]
- inline assembly, operators
- inline assembly, data directives
- MASM (Microsoft Macro Assembler), operators
- structures [C++], MASM
ms.assetid: fb7410c7-156a-4131-bcfc-211aa70533e3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9875a6d4ee0b061db609f45d574a80a7ee5424ab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Direktivy a operátory dat ve vloženém sestavení
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 I když `__asm` bloku odkazovat jazyka C nebo C++ datové typy a objekty, ho nelze definovat datové objekty s direktivy MASM nebo operátory. Konkrétně, nemůžete použít direktivy definice **DB**, `DW`, **DD**, `DQ`, `DT`, a `DF`, nebo operátory `DUP` nebo  **TO**. MASM struktury a záznamy jsou také k dispozici. Vložený assembler nepřijímá direktivy `STRUC`, `RECORD`, **šířka**, nebo **maska**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití jazyka sestavení v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)