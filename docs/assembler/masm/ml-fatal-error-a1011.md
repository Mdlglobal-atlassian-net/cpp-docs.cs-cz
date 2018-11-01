---
title: Závažná chyba nástroje ML A1011
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 591755a1d7066d8251f61d2a22b9601a9ccb9dcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520195"
---
# <a name="ml-fatal-error-a1011"></a>Závažná chyba nástroje ML A1011

**Direktiva musí být v bloku ovládacího prvku**

Assembler nalezen direktivu vysoké úrovně, kde jedna neočekával. Byl nalezen jeden z následujících direktiv:

- [. OSTATNÍ](../../assembler/masm/dot-else.md) bez [. IF](../../assembler/masm/dot-if.md)

- [. ENDIF](../../assembler/masm/dot-endif.md) bez [. IF](../../assembler/masm/dot-if.md)

- [. ENDW](../../assembler/masm/dot-endw.md) bez [. WHILE](../../assembler/masm/dot-while.md)

- [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) bez [. OPAKUJTE](../../assembler/masm/dot-repeat.md)

- [. Pokračovat](../../assembler/masm/dot-continue.md) bez [. ZATÍMCO](../../assembler/masm/dot-while.md) nebo [. OPAKUJTE](../../assembler/masm/dot-repeat.md)

- [. PŘERUŠIT](../../assembler/masm/dot-break.md) bez [. ZATÍMCO](../../assembler/masm/dot-while.md) nebo [. OPAKUJTE](../../assembler/masm/dot-repeat.md)

- [. OSTATNÍ](../../assembler/masm/dot-else.md) následující `.ELSE`

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>