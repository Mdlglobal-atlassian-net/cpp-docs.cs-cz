---
title: Chyba kompilátoru C2109 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2109
dev_langs:
- C++
helpviewer_keywords:
- C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 551c391c67e54c00a26fe6c11fb062adcb9c2f30
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100784"
---
# <a name="compiler-error-c2109"></a>Chyba kompilátoru C2109

Subscript vyžaduje typ pole nebo ukazatel

Dolního indexu byla použita na proměnnou, která není pole.

Následující ukázka generuje C2109:

```
// C2109.cpp
int main() {
   int a, b[10] = {0};
   a[0] = 1;   // C2109
   b[0] = 1;   // OK
}
```