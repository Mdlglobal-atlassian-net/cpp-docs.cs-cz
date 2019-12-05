---
title: Méně závažná chyba nástroje ML A2133
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: c2d13aefe02543129340bcc307771a1026776d61
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74854612"
---
# <a name="ml-nonfatal-error-a2133"></a>Méně závažná chyba nástroje ML A2133

**Hodnota registru, která je přepsána voláním**

Registr byl předán jako argument procedury, ale kód vygenerovaný voláním [Invoke](../../assembler/masm/invoke.md) pro předání jiných argumentů zničil obsah registru.

Registry AX, AL, AH, EAX vrátí, DX, DL, DH a EDX může použít Assembler k provedení převodu dat.

Použijte jiný registr.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>