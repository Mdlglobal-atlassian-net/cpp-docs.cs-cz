---
title: Závažná méně závažná chyba nástroje ML A2031 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2031
dev_langs:
- C++
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf6744224847e114e76df6e7ad6470696d3e8387
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682655"
---
# <a name="ml-nonfatal-error-a2031"></a>Méně závažná chyba nástroje ML A2031

**musí být registr indexu nebo base**

Byl proveden pokus o použití registru, která nebyla registru base nebo indexu ve výrazu paměti.

Například následující výrazy způsobit následující chybu:

```asm
[ax]
[bl]
```

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>