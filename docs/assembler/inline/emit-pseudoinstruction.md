---
title: _emit – pseudoinstrukce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
f1_keywords:
- _emit
dev_langs:
- C++
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8c11165e8b6632488d29e5fe79aa945332c25e9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689359"
---
# <a name="emit-pseudoinstruction"></a>_emit – pseudoinstrukce

**Specifické pro Microsoft**

**_Emit** – pseudoinstrukce definuje jeden bajt na aktuální pozici do aktuálního textového segmentu. **_Emit** – pseudoinstrukce vypadá podobně jako [DB](../../assembler/masm/db.md) direktivu MASM.

Následující fragment bajtů 0x4A 0x43 a 0x4B umístí do kódu:

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
     randasm
     }
```

> [!CAUTION]
> Pokud `_emit` generuje pokyny, které mění registrů a zkompilovat aplikaci s optimalizací, kompilátor nemůže určit, jaké registrů se to týká. Například pokud `_emit` generuje instrukce, která upravuje **rax** registr, kompilátor neví, který **rax** došlo ke změně. Kompilátor poté může být nesprávné předpoklady o hodnotu v tomto registrovat po provedení vloženého kódu assembleru. Vaše aplikace v důsledku toho může vykazovat nepředvídatelné chování při spuštění.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>