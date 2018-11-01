---
title: Direktivy a operátory dat ve vloženém sestavení
ms.date: 08/30/2018
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
ms.openlocfilehash: 52e20c37f3066122a062e3fc9c64ced576b6c302
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577970"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Direktivy a operátory dat ve vloženém sestavení

**Specifické pro Microsoft**

I když `__asm` bloku může odkazovat na datové typy jazyka C nebo C++ a objekty, ho nelze definovat datové objekty s MASM direktivy a operátory. Konkrétně byste měli nejde použít direktivy definice **DB**, `DW`, **DD**, `DQ`, `DT`, a `DF`, nebo operátory `DUP` nebo  **TO**. Není k dispozici jsou taky MASM struktury a záznamy. Vložený assembler nepřijme direktivy `STRUC`, `RECORD`, **šířka**, nebo **maska**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>