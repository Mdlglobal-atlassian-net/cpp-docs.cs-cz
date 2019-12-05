---
title: Méně závažná chyba nástroje ML A2085
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: 3bd89fb2b7f8b755cdb095e63ed89386332ecf9d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74855755"
---
# <a name="ml-nonfatal-error-a2085"></a>Méně závažná chyba nástroje ML A2085

**instrukce nebo registr se v aktuálním režimu procesoru nepřijaly.**

Byl proveden pokus o použití instrukcí, registru nebo klíčového slova, které nebylo pro aktuální režim procesoru platné.

Například 32 bitové Registry vyžadují [. 386](../../assembler/masm/dot-386.md) nebo vyšší. Řídicí Registry jako CR0 vyžadují privilegovaný režim [. 386P](../../assembler/masm/dot-386p.md) nebo vyšší. Tato chyba se taky vygeneruje pro klíčová slova **NEAR32**, **FAR32**a **Flat** , která vyžadují. **386** nebo vyšší.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>