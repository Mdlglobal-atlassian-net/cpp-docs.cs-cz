---
title: _emit – pseudoinstrukce
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: f2a7c9c4dab97bc1aba3147b5d75f6abbdac951f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167163"
---
# <a name="emit-pseudoinstruction"></a>_emit – pseudoinstrukce

**Microsoft Specific**

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