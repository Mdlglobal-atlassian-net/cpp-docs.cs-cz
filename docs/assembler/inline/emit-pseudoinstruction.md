---
title: _emit – pseudoinstrukce
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: 8be250aadf20dc4a7dee6a0b565ece21840339d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169471"
---
# <a name="_emit-pseudoinstruction"></a>_emit – pseudoinstrukce

**Specifické pro společnost Microsoft**

**_Emit** – pseudoinstrukce definuje jeden bajt v aktuálním umístění v aktuálním textovém segmentu. **_Emit** – pseudoinstrukce se podobá [databázové](../../assembler/masm/db.md) direktivě MASM.

Následující fragment umístí do kódu bajty 0x4A, 0x43 a 0x4B:

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
> Pokud `_emit` vygeneruje pokyny, které mění registry a zkompilujete aplikaci s optimalizací, kompilátor nemůže určit, které Registry budou ovlivněny. Například pokud `_emit` vygeneruje instrukci, která upraví registr **RAX** , kompilátor neví, že **RAX** se změnil. Kompilátor pak může vytvořit nesprávný předpoklad o hodnotě v tomto registru po spuštění vloženého kódu assembleru. V důsledku toho může aplikace při spuštění vykazovat nepředvídatelné chování.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Použití assembleru v blocích __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
