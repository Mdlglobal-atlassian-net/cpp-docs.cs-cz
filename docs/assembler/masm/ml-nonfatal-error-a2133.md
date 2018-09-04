---
title: Závažná méně závažná chyba nástroje ML A2133 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2133
dev_langs:
- C++
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0df094f5e7135ffb3b9a5f09383e03e411755de3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678063"
---
# <a name="ml-nonfatal-error-a2133"></a>Méně závažná chyba nástroje ML A2133

**Přepsat INVOKE hodnoty registru**

Registru byl předán jako argument procedury, ale kód generovaných [INVOKE](../../assembler/masm/invoke.md) předání dalších argumentů zničen obsah do registru.

AX, AL, AH, EAX, DX, bude používat, Diffie-Hellman a EDX registrů lze assembler k provedení převodu data.

Použijte jiný registr.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>