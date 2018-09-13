---
title: Direktivy makra MASM ve vloženém sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: 35ad22a9a4b79a31665ab6b156f8174d395bb0ee
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "43687970"
---
# <a name="masm-macro-directives-in-inline-assembly"></a>Direktivy makra MASM ve vloženém sestavení

**Specifické pro Microsoft**

Vložený assembler není assembleru maker. Nelze použít direktivy makra MASM (**– makro**, `REPT`, **IRC**, `IRP`, a `ENDM`) nebo makro operátory (**<>**, **!** , **&**, `%`, a `.TYPE`). `__asm` Bloku lze pomocí direktivy preprocesoru jazyka C, ale. Zobrazit [pomocí jazyka C nebo C++ v blocích __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md) Další informace.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>