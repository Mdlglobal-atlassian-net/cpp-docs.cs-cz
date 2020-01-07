---
title: Méně závažná chyba nástroje ML A2133
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 1ffdf5fb6577dbd4e24312b3c57a4186173ddcf6
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312635"
---
# <a name="ml-nonfatal-error-a2133"></a>Méně závažná chyba nástroje ML A2133

**Hodnota registru, která je přepsána voláním**

Registr byl předán jako argument procedury, ale kód vygenerovaný voláním [Invoke](invoke.md) pro předání jiných argumentů zničil obsah registru.

Registry AX, AL, AH, EAX vrátí, DX, DL, DH a EDX může použít Assembler k provedení převodu dat.

Použijte jiný registr.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
