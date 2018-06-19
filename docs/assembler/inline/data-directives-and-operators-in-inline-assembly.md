---
title: Direktivy a operátory ve vloženém sestavení dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bd3bc686cc8cee1a02e9df936f80f542bec26bd
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051382"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Direktivy a operátory dat ve vloženém sestavení
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 I když `__asm` bloku odkazovat jazyka C nebo C++ datové typy a objekty, ho nelze definovat datové objekty s direktivy MASM nebo operátory. Konkrétně, nemůžete použít direktivy definice **DB**, `DW`, **DD**, `DQ`, `DT`, a `DF`, nebo operátory `DUP` nebo  **TO**. MASM struktury a záznamy jsou také k dispozici. Vložený assembler nepřijímá direktivy `STRUC`, `RECORD`, **šířka**, nebo **maska**.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)