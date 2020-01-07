---
title: Méně závažná chyba nástroje ML A2085
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2085
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
ms.openlocfilehash: f8fdedfc1bc8bff63124d18fe1410d9f144cb926
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316834"
---
# <a name="ml-nonfatal-error-a2085"></a>Méně závažná chyba nástroje ML A2085

**instrukce nebo registr se v aktuálním režimu procesoru nepřijaly.**

Byl proveden pokus o použití instrukcí, registru nebo klíčového slova, které nebylo pro aktuální režim procesoru platné.

Například 32 bitové Registry vyžadují [. 386](dot-386.md) nebo vyšší. Řídicí Registry jako CR0 vyžadují privilegovaný režim [. 386P](dot-386p.md) nebo vyšší. Tato chyba se taky vygeneruje pro klíčová slova **NEAR32**, **FAR32**a **Flat** , která vyžadují. **386** nebo vyšší.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
