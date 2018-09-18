---
title: Upozornění (úroveň 1) C4090 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4090
dev_langs:
- C++
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4ae34eeb6c87fdb12b07d25c6b6bbcfdd6b5ee21
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024805"
---
# <a name="compiler-warning-level-1-c4090"></a>Kompilátor upozornění (úroveň 1) C4090

'operation': kvalifikátory různé "modifikátor'

Proměnné použité v operaci je definován pomocí zadaného modifikátor, který brání jeho upravovaného bez zjištění kompilátorem. Výraz je zkompilován beze změn.

Toto upozornění může nastat, když ukazatel **const** nebo `volatile` přiřadí položka na ukazatel není deklarovaná jako odkazující na **const** nebo `volatile`.

Pro programy C se objeví toto upozornění. V programu v jazyce C++, kompilátor vyvolá chybu: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

Následující ukázka generuje C4090:

```
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```