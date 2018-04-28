---
title: Direktivy makra MASM ve vloženém sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cfd8e3ca5fb6bf65a288c17b1754d567b2b081a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Direktivy makra MASM ve vloženém sestavení
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Vložený assembler není Assembler – makro. Nemůžete použít direktivy makra MASM (**makro**, `REPT`, **IRC**, `IRP`, a `ENDM`) nebo makro operátory (**<>**, **!** , **&**, `%`, a `.TYPE`). `__asm` Bloku můžete ale použít C preprocesor – direktivy,. V tématu [pomocí jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Další informace.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)