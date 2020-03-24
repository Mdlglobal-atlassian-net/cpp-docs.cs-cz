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
ms.openlocfilehash: 916dce0346bebfc5ff65ca558ae75317a187660a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169536"
---
# <a name="data-directives-and-operators-in-inline-assembly"></a>Direktivy a operátory dat ve vloženém sestavení

**Specifické pro společnost Microsoft**

I když `__asm` blok může odkazovat na C++ datové typy a objekty jazyka C, nemůže definovat datové objekty pomocí direktiv MASM nebo operátorů. Konkrétně nemůžete použít direktivy definice **DB**, `DW`, **DD**, `DQ`, `DT`a `DF`nebo `DUP` ani **to**. Struktury a záznamy MASM jsou také nedostupné. Vložený Assembler nepřijímá direktivy `STRUC`, `RECORD`, **Width**nebo **Mask**.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
