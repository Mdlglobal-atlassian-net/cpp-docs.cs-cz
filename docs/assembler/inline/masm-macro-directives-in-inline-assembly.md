---
title: Direktivy makra MASM ve vloženém sestavení
ms.date: 08/30/2018
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
ms.openlocfilehash: 38b73346fc52f6b5efe478f8eb960ad049fae924
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169276"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Direktivy makra MASM ve vloženém sestavení

**Specifické pro společnost Microsoft**

Inline assembler není Assembler makra. Nemůžete použít direktivy maker MASM (**makro**, `REPT`, **IRC**, `IRP`a `ENDM`) nebo operátory makra ( **<>** , **!** , **&** , `%`a `.TYPE`). Blok `__asm` může ale používat direktivy preprocesoru jazyka C. Další informace naleznete [v C++ tématu using C nebo in __asm Blocks](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
