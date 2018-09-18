---
title: Chyba kompilátoru C3644 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3644
dev_langs:
- C++
helpviewer_keywords:
- C3644
ms.assetid: 2e3f6c41-3ec5-4a01-82bc-f11b61ebe68e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63e48b944bd5b828ece1110240c462584703ba73
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099483"
---
# <a name="compiler-error-c3644"></a>Chyba kompilátoru C3644

'function': Nelze zkompilovat funkci vygenerovat spravovaný kód

Přítomnost některých klíčových slov ve funkci způsobí, že funkce, který má být zkompilována pro nativní.

Následující ukázka generuje C3644:

```
// C3644.cpp
// compile with: /clr
// processor: x86

void __clrcall Func2(int i) {
   __asm {}   // C3644
}
```