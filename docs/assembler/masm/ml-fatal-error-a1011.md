---
title: Závažná chyba nástroje ML A1011
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 5607d6d56e0b3889332dcf2624d519529819b1c9
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318072"
---
# <a name="ml-fatal-error-a1011"></a>Závažná chyba nástroje ML A1011

**Direktiva musí být v řídicím bloku.**

Assembler našel direktivu vysoké úrovně, u které se neočekávala žádná z nich. Našla se jedna z následujících direktiv:

- [. JINAK](dot-else.md) bez [. Pokud](dot-if.md)

- [. ENDIF](dot-endif.md) bez [. Pokud](dot-if.md)

- [. ENDW](dot-endw.md) bez [. ZATÍMCO](dot-while.md)

- [. UNTILCXZ](dot-untilcxz.md) bez [. OPAKOVAT](dot-repeat.md)

- [. POKRAČOVAT](dot-continue.md) bez [. WHILe](dot-while.md) nebo [. OPAKOVAT](dot-repeat.md)

- [. Přerušit](dot-break.md) bez [. WHILe](dot-while.md) nebo [. OPAKOVAT](dot-repeat.md)

- [. JINAK](dot-else.md) následující `.ELSE`

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
