---
title: Direktivy a operátory ve vloženém sestavení dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 6aff2f4c5ce5e7f5592aa9ec707d002c57f0eac0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678734"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Direktivy a operátory dat ve vloženém sestavení

**Specifické pro Microsoft**

I když `__asm` bloku může odkazovat na datové typy jazyka C nebo C++ a objekty, ho nelze definovat datové objekty s MASM direktivy a operátory. Konkrétně byste měli nejde použít direktivy definice **DB**, `DW`, **DD**, `DQ`, `DT`, a `DF`, nebo operátory `DUP` nebo  **TO**. Není k dispozici jsou taky MASM struktury a záznamy. Vložený assembler nepřijme direktivy `STRUC`, `RECORD`, **šířka**, nebo **maska**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>