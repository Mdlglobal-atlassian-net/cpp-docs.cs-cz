---
title: Závažná méně závažná chyba nástroje ML A2085 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd5ec9f36a4f956b8eeb097b6a8f8eaed89ba2b2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681433"
---
# <a name="ml-nonfatal-error-a2085"></a>Méně závažná chyba nástroje ML A2085

**instrukce nebo register není přijatá v aktuálním režimu procesoru**

Došlo pokusu o použít instrukce, registr nebo klíčové slovo, které není platný pro aktuální režim procesoru.

Například 32-bit registrů vyžaduje [.386](../../assembler/masm/dot-386.md) nebo vyšší. Registruje ovládací prvek, jako je CR0 vyžadují privilegovaném režimu [.386P](../../assembler/masm/dot-386p.md) nebo vyšší. K této chybě také se vygeneruje pro **NEAR32**, **FAR32**, a **PLOCHÝ** klíčová slova, které vyžadují. **386** nebo vyšší.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>