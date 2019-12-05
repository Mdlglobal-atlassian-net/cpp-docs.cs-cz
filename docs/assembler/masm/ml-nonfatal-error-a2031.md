---
title: Méně závažná chyba nástroje ML A2031
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: f964c67ba7bf399e9a3761e4e201662a6a712a1b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856698"
---
# <a name="ml-nonfatal-error-a2031"></a>Méně závažná chyba nástroje ML A2031

**musí se jednat o index nebo základní registr.**

Došlo k pokusu o použití registru, který nebyl základním nebo indexovým registrem ve výrazu paměti.

Následující výrazy například způsobují tuto chybu:

```asm
[ax]
[bl]
```

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>