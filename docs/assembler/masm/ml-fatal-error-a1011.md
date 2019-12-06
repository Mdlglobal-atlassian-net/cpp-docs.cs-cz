---
title: Závažná chyba nástroje ML A1011
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 0d8d3896f7788aa3f51605651ee1b728b0e1d60a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856849"
---
# <a name="ml-fatal-error-a1011"></a>Závažná chyba nástroje ML A1011

**Direktiva musí být v řídicím bloku.**

Assembler našel direktivu vysoké úrovně, u které se neočekávala žádná z nich. Našla se jedna z následujících direktiv:

- [. JINAK](../../assembler/masm/dot-else.md) bez [. Pokud](../../assembler/masm/dot-if.md)

- [. ENDIF](../../assembler/masm/dot-endif.md) bez [. Pokud](../../assembler/masm/dot-if.md)

- [. ENDW](../../assembler/masm/dot-endw.md) bez [. ZATÍMCO](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) bez [. OPAKOVAT](../../assembler/masm/dot-repeat.md)

- [. POKRAČOVAT](../../assembler/masm/dot-continue.md) bez [. WHILe](../../assembler/masm/dot-while.md) nebo [. OPAKOVAT](../../assembler/masm/dot-repeat.md)

- [. Přerušit](../../assembler/masm/dot-break.md) bez [. WHILe](../../assembler/masm/dot-while.md) nebo [. OPAKOVAT](../../assembler/masm/dot-repeat.md)

- [. JINAK](../../assembler/masm/dot-else.md) následující `.ELSE`

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>