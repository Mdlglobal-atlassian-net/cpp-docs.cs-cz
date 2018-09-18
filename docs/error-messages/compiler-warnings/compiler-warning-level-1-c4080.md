---
title: Upozornění (úroveň 1) C4080 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4080
dev_langs:
- C++
helpviewer_keywords:
- C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 08ec1b7c65342ece3a7aebae673fce9a0d19b7a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074705"
---
# <a name="compiler-warning-level-1-c4080"></a>Kompilátor upozornění (úroveň 1) C4080

Očekával se identifikátor pro název segmentu; 'symbol' nalezen

Název segmentu v [#pragma alloc_text](../../preprocessor/alloc-text.md) musí být řetězec nebo identifikátor. Kompilátor ignoruje direktivy pragma, pokud není nalezen platný identifikátor.

Následující ukázka generuje C4080:

```
// C4080.cpp
// compile with: /W1
extern "C" void func(void);

#pragma alloc_text()   // C4080

// try this line to resolve the warning
// #pragma alloc_text("mysection", func)

int main() {
}

void func(void) {
}
```