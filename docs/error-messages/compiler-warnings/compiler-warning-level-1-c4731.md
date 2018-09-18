---
title: Upozornění (úroveň 1) C4731 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75117b34e63694cfa6aeec97abf178ff8e61a7da
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086479"
---
# <a name="compiler-warning-level-1-c4731"></a>Kompilátor upozornění (úroveň 1) C4731

"ukazatelů": "zaregistrovat" upravil vložený kód sestavení registr ukazatelů rámců

Registr ukazatelů rámec byl změněn. Musíte uložení a obnovení registru v vaše sestavení bloku nebo rámec proměnná na řádku (místní proměnná nebo parametr, v závislosti na registr upravit) nebo váš kód nemusí fungovat správně.

Následující ukázka generuje C4731:

```
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

Právě upravuje EBP je rámcový ukazatel (FPO je zakázáno). Když `p` je novější odkazuje, se na ni odkazuje vzhledem k `EBP`. Ale `EBP` je přepsaný pomocí kódu, takže program nebude správně fungovat a může dokonce selhání.