---
title: Chyba linkerů LNK1120
description: Popisuje chybu linkeru LINKERŮ LNK1120, která hlásí počet nevyřešených chyb externích symbolů v odkazu.
ms.date: 10/31/2019
f1_keywords:
- LNK1120
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
ms.openlocfilehash: 21a1ede07a69cdc065dd897715e243115529600d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626585"
---
# <a name="linker-tools-error-lnk1120"></a>Chyba linkerů LNK1120

> *počet* nerozpoznaných externích typů

Chyba LINKERŮ LNK1120 hlásí počet [nevyřešených chyb externích symbolů](linker-tools-error-lnk2001.md#what-is-an-unresolved-external-symbol) v aktuálním propojení.

Každý nevyřešený externí symbol nejprve získá zprávu [linkerů LNK2001](linker-tools-error-lnk2001.md) nebo [linkerů LNK2019](linker-tools-error-lnk2019.md) . Zpráva LINKERŮ LNK1120 se objeví jako poslední a zobrazuje počet chyb nevyřešených symbolů.

> [!IMPORTANT]
> **Tuto chybu nemusíte opravovat.** Tato chyba se neukončí, když opravíte všechny chyby linkeru LINKERŮ LNK2001 a LINKERŮ LNK2019 předtím, než je ve výstupu sestavení. Vždy opravovat problémy počínaje první nahlášenou chybou. Pozdější chyby můžou být způsobené předchozími chybami a v případě, že jsou vyřešené předchozí chyby, zmizí.
