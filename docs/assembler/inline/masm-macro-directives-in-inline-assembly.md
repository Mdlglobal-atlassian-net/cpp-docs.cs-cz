---
title: "Direktivy makra MASM ve vloženém sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- directives, macros
- inline assembly, macro directives
- macros, directives
- MASM (Microsoft Macro Assembler), inline assembly macro directives
ms.assetid: 83643a09-1699-40a8-8ef2-13502bc4ac2c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f789df759729deb3c2b548efb008ae9a27357ab2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Direktivy makra MASM ve vloženém sestavení
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Vložený assembler není Assembler – makro. Nemůžete použít direktivy makra MASM (**makro**, `REPT`, **IRC**, `IRP`, a `ENDM`) nebo makro operátory (**<>**, **!** ,  **&** , `%`, a `.TYPE`). `__asm` Bloku můžete ale použít C preprocesor – direktivy,. V tématu [pomocí jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Další informace.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Použití jazyka sestavení v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)