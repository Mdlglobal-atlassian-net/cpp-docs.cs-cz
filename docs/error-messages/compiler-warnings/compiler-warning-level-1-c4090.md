---
title: Upozornění kompilátoru (úroveň 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 88ed48e9bf7057c55ee4004ca1bb1eb18cd4be51
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626169"
---
# <a name="compiler-warning-level-1-c4090"></a>Upozornění kompilátoru (úroveň 1) C4090

' operation ': odlišné kvalifikátory modifikátoru

Proměnná použitá v operaci je definována se zadaným modifikátorem, která brání jeho úpravám bez detekce kompilátorem. Výraz je zkompilován beze změny.

Toto upozornění může být způsobeno tím, že ukazatel na typ **const** nebo `volatile` je přiřazen k ukazateli, který není deklarován jako typ ukazatele na typ **const** nebo `volatile`.

Toto upozornění je vydáno pro programy C. V C++ programu vyvolá kompilátor chybu: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).

Následující ukázka generuje C4090:

```c
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