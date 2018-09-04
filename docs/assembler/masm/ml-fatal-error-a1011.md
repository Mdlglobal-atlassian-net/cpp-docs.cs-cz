---
title: Závažná chyba nástroje ML A1011 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32949773b869d189516a381ca7df941760a1e4e4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690805"
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