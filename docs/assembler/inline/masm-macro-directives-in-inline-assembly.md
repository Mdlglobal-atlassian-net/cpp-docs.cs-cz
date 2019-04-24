---
title: Direktivy makra MASM ve vloženém sestavení
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 7e1bed782d28a5bf7c934c3f57f50aae70038578
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167254"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Direktivy makra MASM ve vloženém sestavení

**Microsoft Specific**

Vložený assembler není assembleru maker. Nelze použít direktivy makra MASM (**– makro**, `REPT`, **IRC**, `IRP`, a `ENDM`) nebo makro operátory (**<>**, **!** , **&**, `%`, a `.TYPE`). `__asm` Bloku lze pomocí direktivy preprocesoru jazyka C, ale. Zobrazit [pomocí jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Další informace.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>