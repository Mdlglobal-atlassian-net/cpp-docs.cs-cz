---
title: Méně závažná chyba nástroje ML A2085
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 729f6f38761171c6ddc4cccfc2443c6a2b597bf3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444353"
---
# <a name="ml-nonfatal-error-a2085"></a>Méně závažná chyba nástroje ML A2085

**instrukce nebo register není přijatá v aktuálním režimu procesoru**

Došlo pokusu o použít instrukce, registr nebo klíčové slovo, které není platný pro aktuální režim procesoru.

Například 32-bit registrů vyžaduje [.386](../../assembler/masm/dot-386.md) nebo vyšší. Registruje ovládací prvek, jako je CR0 vyžadují privilegovaném režimu [.386P](../../assembler/masm/dot-386p.md) nebo vyšší. K této chybě také se vygeneruje pro **NEAR32**, **FAR32**, a **PLOCHÝ** klíčová slova, které vyžadují. **386** nebo vyšší.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>